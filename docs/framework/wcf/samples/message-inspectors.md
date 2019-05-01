---
title: Inspektoři zpráv
ms.date: 03/30/2017
ms.assetid: 9bd1f305-ad03-4dd7-971f-fa1014b97c9b
ms.openlocfilehash: c9d2c47a816e7fd8c5d219009128ed530564b81b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989810"
---
# <a name="message-inspectors"></a>Inspektoři zpráv
Tento příklad ukazuje, jak implementovat a konfigurovat messageinspectors klienta a služby.  
  
 Zpráva inspector je objekt rozšiřitelnosti, který lze použít v modelu služby klientů runtime a odeslání runtime programově nebo prostřednictvím konfigurace a že můžete zkontrolovat a změnit zpráv po jejich přijetí nebo před jejich odesláním.  
  
 Tato ukázka implementuje základní klient a služba zpráva ověřovací mechanismus, který ověří příchozí zprávy pro sadu konfigurovatelné dokumentů schématu XML. Všimněte si, že tato ukázka neověřuje zpráv pro každou operaci. To je úmyslné zjednodušení.  
  
## <a name="message-inspector"></a>Zpráva inspektoru  
 Implementace inspektoři zpráv klienta <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> rozhraní a službu implementovat kontroly zprávy <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> rozhraní. Implementace zkombinovat do jedné třídy k vytvoření zprávy inspector, který se dá použít pro obě strany. Tato ukázka implementuje takové kombinované zpráva inspector. Inspektor je vytvořen při předávání v sadě schémat, kterými se ověří příchozí a odchozí zprávy a umožňuje vývojářům určit, jestli se ověřují příchozí nebo odchozí zprávy a určuje, zda inspector pracuje v režimu klienta nebo odeslání, který zpracování chyb ovlivní, jak je popsáno dále v tomto tématu.  
  
```  
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
  
 Žádné služby (odesílatel) zpráva inspektoru musí implementovat dvě <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> metody <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> a <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.  
  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> Vyvolá dispečer při přijetí, zpracování kanálu zásobníku a přiřazeno ke službě zprávy, ale předtím, než je deserializovat a odeslaných do operace. Pokud příchozí zpráva byla zašifrována, je zpráva již dešifrovat dosáhne inspektor zprávy. Získá metodu `request` zprávu předá jako parametr odkazu, který umožňuje zpráva, kterou chcete prozkoumat, manipulovat nebo nahradit podle potřeby. Návratová hodnota může být libovolný objekt a slouží jako korelace stav objektu, který je předán <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> Pokud služba vrátí odpověď na aktuální zprávu. V této ukázce <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> deleguje kontroly (ověřování) zprávy, která se metoda privátní, místní `ValidateMessageBody` a vrátí objekt stavu žádná korelace. Tato metoda zajišťuje, že žádné neplatné zprávy předat do služby.  
  
```  
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
  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29> je vyvolána pokaždé, když odpověď je připravená k odeslání zpět do klienta nebo v případě jednosměrného zpráv, po zpracování příchozí zprávy. To umožňuje rozšíření Spolehněte se na volání symetricky, bez ohledu na to MEP. Stejně jako u <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, zprávy se předá jako parametr odkazu a lze ho zkontrolovat, upravit nebo nahradit. Ověření zprávy, která se provádí v této ukázce se znovu deleguje na `ValidMessageBody` metody, ale zpracování chyb při ověřování se v tomto případě mírně liší.  
  
 Pokud dojde k chybě ověření ve službě, `ValidateMessageBody` vyvolá metoda výjimku <xref:System.ServiceModel.FaultException>-odvozené výjimky. V <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, tyto výjimky můžou být přepnuté do infrastruktury služby modelu, ve kterém jsou automaticky transformuje na chyb SOAP a předává do klienta. V <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>, <xref:System.ServiceModel.FaultException> výjimky nesmí možné zařadit do infrastruktury, protože transformace selhání výjimky vyvolané službou vyskytuje před voláním inspektor zprávy. Proto následující implementaci zachytí známých `ReplyValidationFault` výjimky a nahradí zprávu odpovědi s explicitní chybovou zprávu. Tato metoda zajišťuje, že žádné neplatné jsou vraceny v implementaci služby.  
  
```  
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
  
 Inspektor zprávy klienta je velmi podobné. Tyto dvě metody, které je třeba implementovat z <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> jsou <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> a <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>.  
  
 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> je voláno, když má byla zpráva skládá klientská aplikace nebo formátovací modul operace. Jak s dispečerem inspektoři zpráv, zprávy stačí, když ho zkontrolovat nebo zcela nahrazena. V této ukázce inspektor deleguje na stejnou místní `ValidateMessageBody` Pomocná metoda, která se používá také pro odeslání inspektoři zpráv.  
  
 Chování rozdíl mezi klientem a službou ověření (jak je uvedeno v konstruktoru) je, že ověřování na straně klienta vyvolá místní výjimky, které jsou vloženy do uživatelského kódu vzhledem k tomu, že k nim dojde místně a ne kvůli selhání služby. Obecně platí je pravidlo, že služba dispečer kontroly vyvolat chyby a zda kontroly klienta vyvolávat výjimky.  
  
 To <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementace zajistí, že žádné neplatné zprávy se odesílají do služby.  
  
```  
object IClientMessageInspector.BeforeSendRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel)  
{  
    if (validateRequest)  
    {  
        ValidateMessageBody(ref request, true);  
    }  
    return null;  
}  
```  
  
 `AfterReceiveReply` Implementace zajistí, že žádné neplatné zprávy přijaté ze služby se předává do uživatelského kódu klienta.  
  
```  
void IClientMessageInspector.AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        ValidateMessageBody(ref reply, false);  
    }  
}  
```  
  
 Je srdcem tato kontrola konkrétní zprávy `ValidateMessageBody` metody. K provedení své práce, zabalí ověřování <xref:System.Xml.XmlReader> kolem textu dílčí stromu obsahu předané zprávy. Čtecí modul se vyplní sadu schémat, které obsahuje inspektor zprávy a zpětné volání pro ověření je nastavená na delegáta odkazující na `InspectionValidationHandler` , která je definována vedle této metody. K provedení ověření zprávy je přečtení a zařazení do paměti datového proudu zajišťuje <xref:System.Xml.XmlDictionaryWriter>. Pokud v procesu dojde k chybě nebo upozornění, je vyvolána metoda zpětného volání.  
  
 Pokud nenastane žádná chyba novou zprávu je vytvořený, který kopíruje vlastnosti a záhlaví z původní zprávy a informační sadu ověřit nyní používá v datovém proudu paměti, která je zabalena <xref:System.Xml.XmlDictionaryReader> a přidávat do zprávy nahrazení.  
  
```  
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
  
 `InspectionValidationHandler` Metoda je volána ověřování <xref:System.Xml.XmlReader> vždy, když dojde k chybě ověření schématu nebo upozornění. Následující implementaci funguje jenom s chybami a bude ignorovat všechna upozornění.  
  
 Na první úvahy může zdát dát vložit ověřování <xref:System.Xml.XmlReader> do zprávy s inspektoru zprávu a umožňují ověření dochází při zpracování zprávy a bez ukládání do vyrovnávací paměti zprávy. Ale znamená, že tato zpětné volání vyvolá výjimky ověření někde ve službě model infrastruktury nebo z uživatelského kódu jako zjistí neplatné z uzlů XML v důsledku nepředvídatelného chování. Vyrovnávací paměti přístup chrání zcela uživatelský kód z neplatné zprávy.  
  
 Jak bylo uvedeno výše ověřte výjimky vyvolané obslužnou rutinou lišit mezi klientem a službou. Ve službě, výjimky jsou odvozeny z <xref:System.ServiceModel.FaultException>, výjimky na straně klienta jsou pravidelné vlastní výjimky.  
  
```  
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
 Inspektoři zpráv jsou rozšíření pro modul runtime klienta nebo odeslání za běhu. Taková rozšíření se konfiguruje pomocí *chování*. Chování je třída, která mění chování modulu service model runtime změnu výchozí konfigurace nebo přidáním přípony (například messageinspectors) k němu.  
  
 Následující `SchemaValidationBehavior` třídy se používá k přidání inspektoru zprávy této ukázky do klienta nebo odeslání modul runtime chování. Implementace je spíše základních v obou případech. V <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> a <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>, nástroj inspector zprávy je vytvořen a přidán do <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> sadu odpovídajících modulu runtime.  
  
```  
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
>  Tento konkrétní chování není dvakrát jako atribut, proto nelze přidat deklarativně na typ kontraktu typu služby. Jde o výchozí rozhodnutí provést, protože kolekce schématu nelze načíst v deklaraci atributu a odkazující na umístění další konfiguraci (například do nastavení aplikace) v tomto atributu znamená vytvoření konfigurace element, který není konzistentní se zbytkem konfiguraci modelu služby. Proto se toto chování lze přidat pouze imperativně prostřednictvím kódu a konfigurace rozšíření modelu služby.  
  
## <a name="adding-the-message-inspector-through-configuration"></a>Přidání zprávy inspektoru prostřednictvím konfigurace  
 Konfigurace vlastního chování pro koncový bod v konfiguračním souboru aplikace, model služby vyžaduje implementátory pro vytvoření konfigurace *element rozšíření* reprezentovaný třídou odvozenou z <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>. Toto rozšíření musí pak přidá do modelu služby konfiguračního oddílu pro rozšíření, jak je ukázáno pro následující rozšíření popsaných v této části.  
  
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
  
 Rozšíření můžete přidat v aplikaci nebo v konfiguračním souboru ASP.NET, což je nejběžnější možnost, nebo v konfiguračním souboru počítače.  
  
 Při přidání rozšíření do konfigurace oboru, chování lze přidat do konfigurace chování, jak je znázorněno v následujícím kódu. Konfigurace chování jsou opakovaně použitelné prvky, které můžete použít pro více koncových bodů podle potřeby. Vzhledem k tomu, že konkrétní chování být nakonfigurované zde implementuje <xref:System.ServiceModel.Description.IEndpointBehavior>, je platný jenom v příslušných konfiguračním oddílu v konfiguračním souboru.  
  
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
  
 `<schemaValidator>` Element, který konfiguruje inspektor zpráva tímto modulem stojí `SchemaValidationBehaviorExtensionElement` třídy. Třída poskytuje dvě logické veřejné vlastnosti s názvem `ValidateRequest` a `ValidateReply`. Obě tyto jsou označené <xref:System.Configuration.ConfigurationPropertyAttribute>. Tento atribut se považuje za propojení mezi vlastností kódu a atributů XML, které můžete zobrazit na předchozí prvek XML konfigurace. Třída také obsahuje vlastnost `Schemas` , který je také označena <xref:System.Configuration.ConfigurationCollectionAttribute> a je typu `SchemaCollection`, což je také součástí této ukázce, ale není uveden v tomto dokumentu pro zkrácení. Tato vlastnost spolu s kolekci a třída prvku kolekce `SchemaConfigElement` zálohuje `<schemas>` element v předchozím fragmentu kódu konfigurace a umožňuje přidání kolekce schémat do sady ověřování.  
  
 Přepsané `CreateBehavior` metoda spustí konfigurační data do objektu chování při modul runtime vyhodnocuje konfigurační data jako sestavení klienta nebo koncový bod.  
  
```  
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
  
## <a name="adding-message-inspectors-imperatively"></a>Přidání imperativně inspektoři zpráv  
 S výjimkou prostřednictvím atributy (které není podporována z důvodu uvedené dříve v této ukázce) a konfigurace, chování lze snadno přidat do klienta a služby modulu runtime pomocí imperativního kódu. V této ukázce se provádí v klientské aplikaci otestovat inspektoru zprávy klienta. `GenericClient` Je třída odvozena z <xref:System.ServiceModel.ClientBase%601>, která zveřejní konfigurace koncového bodu do uživatelského kódu. Předtím, než klient je implicitně otevřen konfigurace koncového bodu můžete změnit, například přidáním chování, jak je znázorněno v následujícím kódu. Přidání chování služby je do značné míry odpovídá techniku klienta je vidět tady a musí být provedena před otevřením hostitele služby.  
  
```  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageInspectors`  
