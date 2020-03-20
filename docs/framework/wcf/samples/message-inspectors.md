---
title: Inspektoři zpráv
ms.date: 03/30/2017
ms.assetid: 9bd1f305-ad03-4dd7-971f-fa1014b97c9b
ms.openlocfilehash: 705401a182d5d816bc2682f5f21ff09ca95f21c7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144445"
---
# <a name="message-inspectors"></a>Inspektoři zpráv
Tato ukázka ukazuje, jak implementovat a konfigurovat inspektory zpráv klienta a služby.  
  
 Inspektor zprávy je objekt rozšiřitelnosti, který lze použít v době runtime klienta a odeslání runtime klienta a odeslání runmaticky nebo prostřednictvím konfigurace a který může kontrolovat a měnit zprávy po jejich přijetí nebo před jejich odesláním.  
  
 Tato ukázka implementuje základní mechanismus ověřování zpráv klienta a služby, který ověřuje příchozí zprávy proti sadě konfigurovatelných dokumentů schématu XML. Všimněte si, že tato ukázka neověřuje zprávy pro každou operaci. Jedná se o záměrné zjednodušení.  
  
## <a name="message-inspector"></a>Inspektor zprávy  
 Inspektoři zpráv klienta implementovat <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> rozhraní a <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> služby zprávy inspektoři implementovat rozhraní. Implementace lze kombinovat do jedné třídy a vytvořit inspektor zpráv, který pracuje pro obě strany. Tento příklad implementuje takové kombinované zprávy inspektor. Inspektor je vytvořen předávání v sadě schémat, proti kterým jsou ověřeny příchozí a odchozí zprávy a umožňuje vývojáři určit, zda jsou ověřeny příchozí nebo odchozí zprávy a zda je inspektor v režimu odeslání nebo klienta, který ovlivňuje zpracování chyb, jak je popsáno dále v tomto tématu.  
  
```csharp
public class SchemaValidationMessageInspector : IClientMessageInspector, IDispatchMessageInspector  
{  
    XmlSchemaSet schemaSet;  
    bool validateRequest;  
    bool validateReply;  
    bool isClientSide;  
    [ThreadStatic]  
    bool isRequest;  
  
    public SchemaValidationMessageInspector(XmlSchemaSet schemaSet,  
         bool validateRequest, bool validateReply, bool isClientSide)  
    {  
        this.schemaSet = schemaSet;  
        this.validateReply = validateReply;  
        this.validateRequest = validateRequest;  
        this.isClientSide = isClientSide;  
    }  
```  
  
 Každý inspektor zpráv služby (dispečera) musí implementovat dvě <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> metody <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> a <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.  
  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>je vyvolána dispečerem, když byla přijata zpráva, zpracována zásobníkem kanálu a přiřazena ke službě, ale před tím, než je deserializována a odeslána do operace. Pokud byla příchozí zpráva zašifrována, je již dešifrována, jakmile se dostane do inspektoru zprávy. Metoda získá `request` zprávu předánjako referenční parametr, který umožňuje zprávu, která má být kontrolována, manipulováno nebo nahrazena podle potřeby. Vrácená hodnota může být libovolný objekt a slouží jako <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> objekt stavu korelace, který je předán, když služba vrátí odpověď na aktuální zprávu. V této <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> ukázce deleguje kontrolu (ověření) `ValidateMessageBody` zprávy na soukromé, místní metody a vrátí žádný objekt stavu korelace. Tato metoda zajišťuje, že žádné neplatné zprávy předat do služby.  
  
```csharp  
object IDispatchMessageInspector.AfterReceiveRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel, System.ServiceModel.InstanceContext instanceContext)  
{  
    if (validateRequest)  
    {  
        // inspect the message. If a validation error occurs,  
        // the thrown fault exception bubbles up.  
        ValidateMessageBody(ref request, true);  
    }  
    return null;  
}  
```  
  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>je vyvolána vždy, když je odpověď připravena k odeslání zpět klientovi nebo v případě jednosměrných zpráv při zpracování příchozí zprávy. To umožňuje rozšíření počítat s tím, že budou volána symetricky, bez ohledu na europoslance. Stejně <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>jako v případě , zpráva je předána jako referenční parametr a může být kontrolována, upravena nebo nahrazena. Ověření zprávy, která je provedena v této ukázce je opět delegována na metodu, `ValidMessageBody` ale zpracování chyb ověření se mírně liší v tomto případě.  
  
 Pokud dojde k chybě ověření ve `ValidateMessageBody` službě, <xref:System.ServiceModel.FaultException>metoda vyvolá odvozené výjimky. V <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>oblasti lze tyto výjimky vložit do infrastruktury modelu služby, kde jsou automaticky transformovány na chyby SOAP a předány klientovi. V <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> <xref:System.ServiceModel.FaultException> , výjimky nesmí být vloženy do infrastruktury, protože transformace výjimky chyby vyvolána službou dochází před upozornění mše. Proto následující implementace zachytí známou `ReplyValidationFault` výjimku a nahradí zprávu odpovědi explicitní chybovou zprávou. Tato metoda zajišťuje, že implementace služby vrací žádné neplatné zprávy.  
  
```csharp  
void IDispatchMessageInspector.BeforeSendReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        // Inspect the reply, catch a possible validation error
        try  
        {  
            ValidateMessageBody(ref reply, false);  
        }  
        catch (ReplyValidationFault fault)  
        {  
            // if a validation error occurred, the message is replaced  
            // with the validation fault.  
            reply = Message.CreateMessage(reply.Version,
                    fault.CreateMessageFault(), reply.Headers.Action);  
        }  
    }  
```  
  
 Inspektor zpráv klienta je velmi podobný. Dvě metody, které musí <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> být <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>implementovány z jsou a .  
  
 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>je vyvolána, pokud byla zpráva složena klientskou aplikací nebo formátovacím formátovacím formátem operace. Stejně jako u dispečerů může být zpráva pouze zkontrolována nebo zcela nahrazena. V této ukázce inspektor `ValidateMessageBody` deleguje stejnou místní pomocnou metodu, která se používá také pro inspektory odesílání zpráv.  
  
 Behaviorální rozdíl mezi ověřením klienta a služby (jak je uvedeno v konstruktoru) je, že ověření klienta vyvolá místní výjimky, které jsou vloženy do uživatelského kódu, protože k nim dochází místně a ne z důvodu selhání služby. Obecně platí pravidlo je, že inspektoři dispečera služby vyvolat chyby a že inspektoři klienta vyvolat výjimky.  
  
 Tato <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementace zajišťuje, že do služby nejsou odesílány žádné neplatné zprávy.  
  
```csharp  
object IClientMessageInspector.BeforeSendRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel)  
{  
    if (validateRequest)  
    {  
        ValidateMessageBody(ref request, true);  
    }  
    return null;  
}  
```  
  
 Implementace `AfterReceiveReply` zajišťuje, že žádné neplatné zprávy přijaté ze služby jsou přenášeny do kódu uživatele klienta.  
  
```csharp  
void IClientMessageInspector.AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        ValidateMessageBody(ref reply, false);  
    }  
}  
```  
  
 Srdcem tohoto konkrétního inspektora `ValidateMessageBody` zprávy je metoda. Chcete-li provést svou práci, <xref:System.Xml.XmlReader> obtéká ověřování kolem podstromu obsahu těla předané zprávy. Čtenář je naplněn sadou schémat, která inspektor zprávy obsahuje a zpětné volání ověření je nastaveno `InspectionValidationHandler` na delegáta, který odkazuje na který je definován vedle této metody. Chcete-li provést ověření, zpráva je pak číst a zařazování do paměti zpětný <xref:System.Xml.XmlDictionaryWriter>proud zpět . Pokud dojde k chybě ověření nebo upozornění v procesu, je vyvolána metoda zpětného volání.  
  
 Pokud nedojde k žádné chybě, je vytvořena nová zpráva, která zkopíruje vlastnosti a záhlaví z původní zprávy a používá nyní <xref:System.Xml.XmlDictionaryReader> ověřenou informační sadu v paměťovém proudu, která je zabalena a přidána do náhradní zprávy.  
  
```csharp  
void ValidateMessageBody(ref System.ServiceModel.Channels.Message message, bool isRequest)  
{  
    if (!message.IsFault)  
    {  
        XmlDictionaryReaderQuotas quotas =
                new XmlDictionaryReaderQuotas();  
        XmlReader bodyReader =
            message.GetReaderAtBodyContents().ReadSubtree();  
        XmlReaderSettings wrapperSettings =
                              new XmlReaderSettings();  
        wrapperSettings.CloseInput = true;  
        wrapperSettings.Schemas = schemaSet;  
        wrapperSettings.ValidationFlags =
                                XmlSchemaValidationFlags.None;  
        wrapperSettings.ValidationType = ValidationType.Schema;  
        wrapperSettings.ValidationEventHandler += new
           ValidationEventHandler(InspectionValidationHandler);  
        XmlReader wrappedReader = XmlReader.Create(bodyReader,
                                            wrapperSettings);  
  
        // pull body into a memory backed writer to validate  
        this.isRequest = isRequest;  
        MemoryStream memStream = new MemoryStream();  
        XmlDictionaryWriter xdw =  
              XmlDictionaryWriter.CreateBinaryWriter(memStream);  
        xdw.WriteNode(wrappedReader, false);  
        xdw.Flush(); memStream.Position = 0;  
        XmlDictionaryReader xdr =
        XmlDictionaryReader.CreateBinaryReader(memStream, quotas);  
  
        // reconstruct the message with the validated body  
        Message replacedMessage =
            Message.CreateMessage(message.Version, null, xdr);  
        replacedMessage.Headers.CopyHeadersFrom(message.Headers);  
        replacedMessage.Properties.CopyProperties(message.Properties);  
        message = replacedMessage;  
    }  
}  
```  
  
 Metoda `InspectionValidationHandler` je volána ověřování <xref:System.Xml.XmlReader> vždy, když dojde k chybě ověření schématu nebo upozornění. Následující implementace funguje pouze s chybami a ignoruje všechna upozornění.  
  
 Na první úvahu se může zdát možné <xref:System.Xml.XmlReader> vložit ověření do zprávy s inspektorem zprávy a nechat ověření dojít jako zpráva je zpracována a bez ukládání do vyrovnávací paměti zprávy. To však znamená, že toto zpětné volání vyvolá výjimky ověření někde do infrastruktury modelu služby nebo uživatelského kódu jako neplatné uzly XML jsou zjištěny, výsledkem je nepředvídatelné chování. Do vyrovnávací paměti přístup chrání kód uživatele z neplatných zpráv, úplně.  
  
 Jak již bylo popsáno, výjimky vyzdvižené obslužnou rutinou se liší mezi klientem a službou. Ve službě jsou výjimky odvozeny <xref:System.ServiceModel.FaultException>od , na straně klienta výjimky jsou pravidelné vlastní výjimky.  
  
```csharp  
        void InspectionValidationHandler(object sender, ValidationEventArgs e)  
{  
    if (e.Severity == XmlSeverityType.Error)  
    {  
        // We are treating client and service side validation errors  
        // differently here. Client side errors cause exceptions  
        // and are thrown straight up to the user code. Service side  
        // validations cause faults.  
        if (isClientSide)  
        {  
            if (isRequest)  
            {  
                throw new RequestClientValidationException(e.Message);  
            }  
            else  
            {  
                throw new ReplyClientValidationException(e.Message);  
            }  
        }  
        else  
        {  
            if (isRequest)  
            {  
                // this fault is caught by the ServiceModel
                // infrastructure and turned into a fault reply.  
                throw new RequestValidationFault(e.Message);  
             }  
             else  
             {  
                // this fault is caught and turned into a fault message  
                // in BeforeSendReply in this class  
                throw new ReplyValidationFault(e.Message);  
              }  
          }  
      }  
    }  
```  
  
## <a name="behavior"></a>Chování  
 Inspektoři zpráv jsou rozšíření na prostředí runtime klienta nebo spuštění odeslání. Tato rozšíření jsou konfigurována pomocí *chování*. Chování je třída, která mění chování za běhu modelu služby změnou výchozí konfigurace nebo přidáním rozšíření (například inspektorů zpráv).  
  
 Následující `SchemaValidationBehavior` třída je chování, které se používá k přidání tohoto ukázkového inspektoru zpráv do klienta nebo expedičního běhu. Implementace je v obou případech spíše základní. V <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>aplikaci a , inspektor zprávy <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> je vytvořen a přidán do kolekce příslušného běhu.  
  
```csharp
public class SchemaValidationBehavior : IEndpointBehavior  
{  
    XmlSchemaSet schemaSet;
    bool validateRequest;
    bool validateReply;  
  
    public SchemaValidationBehavior(XmlSchemaSet schemaSet, bool
                           inspectRequest, bool inspectReply)  
    {  
        this.schemaSet = schemaSet;  
        this.validateReply = inspectReply;  
        this.validateRequest = inspectRequest;  
    }  
    #region IEndpointBehavior Members  
  
    public void AddBindingParameters(ServiceEndpoint endpoint,
       System.ServiceModel.Channels.BindingParameterCollection
                                            bindingParameters)  
    {  
    }  
  
    public void ApplyClientBehavior(ServiceEndpoint endpoint,
            System.ServiceModel.Dispatcher.ClientRuntime clientRuntime)  
    {  
        SchemaValidationMessageInspector inspector =
           new SchemaValidationMessageInspector(schemaSet,
                      validateRequest, validateReply, true);  
            clientRuntime.MessageInspectors.Add(inspector);  
    }  
  
    public void ApplyDispatchBehavior(ServiceEndpoint endpoint,
         System.ServiceModel.Dispatcher.EndpointDispatcher
                                          endpointDispatcher)  
    {  
        SchemaValidationMessageInspector inspector =
           new SchemaValidationMessageInspector(schemaSet,
                        validateRequest, validateReply, false);  
   endpointDispatcher.DispatchRuntime.MessageInspectors.Add(inspector);  
    }  
  
   public void Validate(ServiceEndpoint endpoint)  
   {  
   }  
  
    #endregion  
}  
```  
  
> [!NOTE]
> Toto konkrétní chování není double jako atribut a proto nelze přidat deklarativně na typ smlouvy typu služby. Toto je rozhodnutí podle návrhu, protože kolekci schématu nelze načíst v deklaraci atributu a odkazující na další umístění konfigurace (například nastavení aplikace) v tomto atributu znamená vytvoření konfiguračního prvku, který není konzistentní se zbytkem konfigurace modelu služby. Proto toto chování lze přidat pouze imperativně prostřednictvím kódu a prostřednictvím rozšíření konfigurace modelu služby.  
  
## <a name="adding-the-message-inspector-through-configuration"></a>Přidání inspektoru zprávy prostřednictvím konfigurace  
 Pro konfiguraci vlastního chování v koncovém bodě v konfiguračním souboru aplikace vyžaduje model služby, aby implementátoři vytvořili *prvek rozšíření* konfigurace reprezentovaný třídou odvozenou z aplikace <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>. Toto rozšíření pak musí být přidándo oddílu konfigurace modelu služby pro rozšíření, jak je znázorněno na následující rozšíření popsané v této části.  
  
```xml  
<system.serviceModel>  
…  
   <extensions>  
      <behaviorExtensions>  
        <add name="schemaValidator" type="Microsoft.ServiceModel.Samples.SchemaValidationBehaviorExtensionElement, MessageInspectors, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
      </behaviorExtensions>  
    </extensions>  
…  
</system.serviceModel>  
```  
  
 Přípony lze přidat do konfiguračního souboru aplikace nebo ASP.NET, což je nejběžnější volba, nebo do konfiguračního souboru počítače.  
  
 Při přidání rozšíření do oboru konfigurace chování lze přidat do konfigurace chování, jak je znázorněno v následujícím kódu. Konfigurace chování jsou opakovaně použitelné prvky, které lze použít pro více koncových bodů podle potřeby. Vzhledem k tomu, že <xref:System.ServiceModel.Description.IEndpointBehavior>konkrétní chování, které má být zde nakonfigurováno, implementuje , je platné pouze v příslušné části konfigurace v konfiguračním souboru.  
  
```xml  
<system.serviceModel>  
   <behaviors>  
      …  
     <endpointBehaviors>  
        <behavior name="HelloServiceEndpointBehavior">  
          <schemaValidator validateRequest="True" validateReply="True">  
            <schemas>  
              <add location="messages.xsd" />
            </schemas>  
          </schemaValidator>  
        </behavior>  
      </endpointBehaviors>  
      …  
    </behaviors>  
</system.serviceModel>  
```  
  
 Prvek, `<schemaValidator>` který konfiguruje inspektor `SchemaValidationBehaviorExtensionElement` zprávy je zálohována třídy. Třída zpřístupňuje dvě logické `ValidateRequest` veřejné `ValidateReply`vlastnosti s názvem a . Oba tyto jsou označeny <xref:System.Configuration.ConfigurationPropertyAttribute>. Tento atribut představuje propojení mezi vlastnostmi kódu a atributy XML, které lze vidět na předchozím konfiguračním elementu XML. Třída má také `Schemas` vlastnost, která je <xref:System.Configuration.ConfigurationCollectionAttribute> navíc označena `SchemaCollection`a je typu , který je také součástí tohoto vzorku, ale vynechán z tohoto dokumentu pro stručnost. Tato vlastnost spolu s kolekce a `SchemaConfigElement` třída `<schemas>` elementkolekce podporuje prvek v předchozí fragment konfigurace a umožňuje přidání kolekce schémat do sady ověření.  
  
 Potlačená `CreateBehavior` metoda změní konfigurační data na objekt chování, když runtime vyhodnotí konfigurační data při vytváření klienta nebo koncového bodu.  
  
```csharp
public class SchemaValidationBehaviorExtensionElement : BehaviorExtensionElement  
{  
    public SchemaValidationBehaviorExtensionElement()  
    {  
    }  
  
    public override Type BehaviorType
    {
        get  
        {  
            return typeof(SchemaValidationBehavior);  
        }
    }  
  
    protected override object CreateBehavior()  
    {  
        XmlSchemaSet schemaSet = new XmlSchemaSet();  
        foreach (SchemaConfigElement schemaCfg in this.Schemas)  
        {  
            Uri baseSchema = new
                Uri(AppDomain.CurrentDomain.BaseDirectory);  
            string location = new
                Uri(baseSchema,schemaCfg.Location).ToString();  
            XmlSchema schema =
                XmlSchema.Read(new XmlTextReader(location), null);  
            schemaSet.Add(schema);  
        }  
     return new
     SchemaValidationBehavior(schemaSet,ValidateRequest,ValidateReply);  
    }  
  
[ConfigurationProperty("validateRequest",DefaultValue=false,IsRequired=false)]  
public bool ValidateRequest  
{  
    get { return (bool)base["validateRequest"]; }  
    set { base["validateRequest"] = value; }  
}  
  
[ConfigurationProperty("validateReply", DefaultValue = false, IsRequired = false)]  
        public bool ValidateReply  
        {  
            get { return (bool)base["validateReply"]; }  
            set { base["validateReply"] = value; }  
        }  
  
     //Declare the Schema collection property.  
     //Note: the "IsDefaultCollection = false" instructs
     //.NET Framework to build a nested section of
     //the kind <Schema> ...</Schema>.  
    [ConfigurationProperty("schemas", IsDefaultCollection = true)]  
    [ConfigurationCollection(typeof(SchemasCollection),  
        AddItemName = "add",  
        ClearItemsName = "clear",  
        RemoveItemName = "remove")]  
    public SchemasCollection Schemas  
    {  
        get  
        {  
            SchemasCollection SchemasCollection =  
            (SchemasCollection)base["schemas"];  
            return SchemasCollection;  
        }  
    }  
}  
```  
  
## <a name="adding-message-inspectors-imperatively"></a>Přidání inspektorů zpráv imperativně  
 S výjimkou prostřednictvím atributů (které nejsou podporovány v této ukázce z důvodu citované dříve) a konfigurace, chování lze poměrně snadno přidat do klienta a za běhu služby pomocí imperativní kód. V této ukázce se provádí v klientské aplikaci otestovat inspektor zpráv klienta. Třída `GenericClient` je odvozena <xref:System.ServiceModel.ClientBase%601>od , který zpřístupňuje konfiguraci koncového bodu do uživatelského kódu. Před klientem je implicitně otevřen konfiguraci koncového bodu lze změnit, například přidáním chování, jak je znázorněno v následujícím kódu. Přidání chování ve službě je do značné míry ekvivalentní techniku klienta zde uvedené a musí být provedena před otevřením hostitele služby.  
  
```csharp  
try  
{  
    Console.WriteLine("*** Call 'Hello' with generic client, with client behavior");  
    GenericClient client = new GenericClient();  
  
    // Configure client programmatically, adding behavior  
    XmlSchema schema = XmlSchema.Read(new StreamReader("messages.xsd"),
                                                          null);  
    XmlSchemaSet schemaSet = new XmlSchemaSet();  
    schemaSet.Add(schema);  
    client.Endpoint.Behaviors.Add(new
                SchemaValidationBehavior(schemaSet, true, true));  
  
    Console.WriteLine("--- Sending valid client request:");  
    GenericCallValid(client, helloAction);  
    Console.WriteLine("--- Sending invalid client request:");  
    GenericCallInvalid(client, helloAction);  
  
    client.Close();  
}  
catch (Exception e)  
{  
    DumpException(e);  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageInspectors`  
