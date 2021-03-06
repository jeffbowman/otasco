* Allows testing class under test without creating useless setters for dependencies.
* Makes the test class more readable.

        public class InvoiceManagerTest { 
            @ClassUnderTest private InvoiceManager manager;
            
            @Dependency private InvoiceCalculator invoiceCalculator;
           
            @Dependency private InvoiceDao invoiceDao;
            
            @Before public void setup() {
                invoiceCalculator = new InvoiceCalculator();
                invoiceDao = new InvoiceDao();
                manager = new InvoiceManager();
                Otasco.init(this);
            }
        }

---

* Possibly using Mockito (or your favorite mocking library)

        public class InvoiceManagerTest {
            @ClassUnderTest private InvoiceManager manager;
                        
            @Dependency
            @Mock
            private InvoiceCalculator invoiceCalculator;
                        
            @Dependency
            @Mock
            private InvoiceDao invoiceDao;
                        
            @Before public void setup() {
                MockitoAnnotations.init(this); 
                manager = new InvoiceManager();
                Otasco.init(this);
            }
        }
    
