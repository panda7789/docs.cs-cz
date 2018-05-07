---
title: Inspektoři zpráv
ms.date: 03/30/2017
ms.assetid: 9bd1f305-ad03-4dd7-971f-fa1014b97c9b
ms.openlocfilehash: 05dbee820a002feb1f2a1672220be0c4a397f952
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="message-inspectors"></a>Inspektoři zpráv
Tento příklad ukazuje, jak implementovat a nakonfigurovat klienta a služby inspektoři zpráv.  
  
 Zpráva inspector je rozšíření objekt, který lze použít v modelu služby runtime klienta a odesílání runtime prostřednictvím kódu programu, nebo prostřednictvím konfigurace a který můžete zkontrolovat a změnit zprávy po jejich přijetí nebo před jejich odesláním.  
  
 Tato ukázka implementuje základní klienta a služby zpráva ověření mechanismu, který ověří příchozí zprávy oproti sadě konfigurovat dokumentů schématu XML. Všimněte si, že tato ukázka neověřuje zprávy pro každou operaci. To je úmyslné zjednodušení.  
  
## <a name="message-inspector"></a>Zpráva Inspector  
 Implementace inspektoři zpráv klienta <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> rozhraní a služby implementace inspektoři zpráv <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> rozhraní. Implementace zkombinovat do jedné třídy k vytvoření inspector zpráva, která se dá použít na obou stranách. Tato ukázka implementuje takové inspector kombinované zprávy. Kontrolor je vytvořený předávání v sadě schémat, kterými se ověří příchozí a odchozí zprávy a umožňuje vývojáři k určení, jestli se ověřují příchozí nebo odchozí zprávy a zda nástroj inspector je v režimu klienta nebo odeslání, který zpracování chyb ovlivňuje, jak je popsáno dále v tomto tématu.  
  
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
  
 Všechny zprávy inspector služby (odesílatel) musí implementovat dvě <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> metody <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> a <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.  
  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> je volána dispečera při obdržel, zpracovává zásobníku kanál a přiřazené k službě zprávu, ale předtím, než je deserializovat a odeslaných do operace. Pokud příchozí zpráva byla zašifrována, je zpráva již dešifrovat při dosažení inspector zprávy. Získá metodu `request` zpráva předán jako referenční parametr, který umožňuje zpráva, která má být prověřovány, s nimi manipulovat nebo nahradit podle potřeby. Návratová hodnota může být jakýkoli objekt a slouží jako objekt korelace stavu, který je předán <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> při službu vrátí odpověď na aktuální zprávu. V této ukázce <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> deleguje kontroly (ověřování) zprávy metodu privátní, místní `ValidateMessageBody` a vrátí objekt žádné korelace stavu. Tato metoda zajišťuje, že žádné neplatné zprávy předat do služby.  
  
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
  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29> je volána vždy, když je připravena k odeslání zpět na klienta nebo v případě jednosměrného zprávy, když se po zpracování příchozí zprávy odpovědi. To umožňuje rozšíření počítat se volané symetricky, bez ohledu na to MEP. Stejně jako u <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, zpráva se předá jako parametr odkazu a lze prověřovány, změnit nebo nahradit. Ověření zprávy, které se provádí v této ukázce je znovu delegovaný jako `ValidMessageBody` metoda, ale ošetření chyb při ověřování se v takovém případě mírně lišit.  
  
 Pokud dojde k chybě ověření ve službě, `ValidateMessageBody` vyvolá metoda <xref:System.ServiceModel.FaultException>-odvozené výjimky. V <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, tyto výjimky můžou být přepnuté do infrastruktury služby modelu, kde jsou automaticky převede na chyb SOAP a předává do klienta. V <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>, <xref:System.ServiceModel.FaultException> výjimky nesmí být přepnuté do infrastruktury, protože transformace selhání výjimky vydané služby se vyskytuje před zpráva inspector je volána. Proto za následující implementaci zachytí známých `ReplyValidationFault` výjimku a nahradí odpovědi zpráv s explicitní chybovou zprávu. Tato metoda zajišťuje, že žádné neplatné zprávy jsou vráceny implementace služby.  
  
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
  
 Inspector zpráv klienta je velmi podobné. Tyto dvě metody, které musí být implementován z <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> jsou <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> a <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>.  
  
 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> je voláno, když má byla daná zpráva vytvořena, klientská aplikace nebo operaci formátování. Jako s inspektoři dispečera zpráv, můžete zprávu právě prověřovány nebo zcela nahradit. V této ukázce kontrolor deleguje do stejné místní `ValidateMessageBody` Pomocná metoda, která se také používá pro inspektoři odesílání zpráv.  
  
 Chování rozdíl mezi klientem a službou ověření (jako je zadaný v konstruktoru) je, že ověření klienta vyvolá místní výjimky, které jsou vloženy do uživatelského kódu, protože k nim dojde místně a ne z důvodu selhání služby. Pravidlo je obecně platí, že služba dispečera inspektoři throw chyb a že kontroly klienta výjimku výjimky.  
  
 To <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementace zajistí, že žádné neplatné zprávy se odešle do služby.  
  
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
  
 `AfterReceiveReply` Implementace zajistí, že žádné neplatné zprávy přijal od služby jsou přes předávací službu klienta uživatelského kódu.  
  
```  
void IClientMessageInspector.AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        ValidateMessageBody(ref reply, false);  
    }  
}  
```  
  
 Jádrem této konkrétní zprávu inspector je `ValidateMessageBody` metoda. Ke své práci, zabalí ověřování <xref:System.Xml.XmlReader> kolem textu obsahu dílčí stromu předaný zprávy. Čtečka je naplněna sadu schémat, které obsahuje nástroj inspector zpráv a zpětné volání pro ověření je nastaven s delegátem, která odkazuje na `InspectionValidationHandler` definovaný společně se tato metoda. K provedení ověření, zpráva se pak číst a zařazených do paměti, zálohovaná datový proud <xref:System.Xml.XmlDictionaryWriter>. Pokud v procesu dojde k ověření chyby nebo upozornění, je vyvolána metoda zpětného volání.  
  
 Pokud nedojde k žádné chybě novou zprávu vytvořená, zkopíruje vlastnosti a hlavičky z původní zprávy a informační sadu ověřit nyní používá v datovém proudu paměti, která je zabalené službou <xref:System.Xml.XmlDictionaryReader> a přidávat do zprávy nahrazení.  
  
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
  
 `InspectionValidationHandler` Metoda je volána ověřování <xref:System.Xml.XmlReader> vždy, když dojde k chybě ověření schématu nebo upozornění. Za následující implementaci lze použít pouze se chyby a varování.  
  
 Na první úvahy, mohou vám možné vložit, ověřování <xref:System.Xml.XmlReader> do zprávy s zpráva inspector a umožňují ověření dojít při zpracování zprávy se a bez ukládání do vyrovnávací paměti zprávy. Že však znamená, že tento zpětného volání vyvolá výjimek ověření někde ve službě model infrastrukturu nebo uživatelský kód jako neplatný z uzlů XML detekovány, což vede k nepředvídatelné chování. Vyrovnávací paměti přístup chrání zcela uživatelského kódu z neplatné zprávy.  
  
 Jak bylo popsáno dříve výjimky vyvolané obslužná rutina se liší mezi klientem a služby. Ve službě, výjimky jsou odvozeny od <xref:System.ServiceModel.FaultException>, na straně klienta jsou výjimky regulární vlastní výjimky.  
  
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
 Inspektoři zpráv jsou rozšíření modulu runtime klienta nebo odeslání runtime. Taková rozšíření jsou konfigurováni pomocí *chování*. Chování je třída, která mění chování modulu runtime service model změnu výchozí konfigurace nebo přidání přípony (například inspektoři zpráv) k němu.  
  
 Následující `SchemaValidationBehavior` třída je použít k přidání této ukázce zpráva inspector do klienta nebo odeslání runtime chování. Implementace je spíš základní v obou případech. V <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> a <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>, nástroj inspector zprávy je vytvořen a přidán do <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> kolekce příslušných modulu runtime.  
  
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
>  Toto konkrétní chování není dvakrát jako atribut a nelze ji proto přidat deklarativně na typ smlouvy typu služby. Jedná se o záměrných rozhodnutí provést, protože kolekce schémat nelze načíst v deklarace atributu a odkazy na další konfigurace umístění (například na nastavení aplikací) v tomto atributu znamená vytvoření konfigurační prvek, který není konzistentní se zbytkem konfiguraci modelu služby. Proto toto chování lze přidat pouze imperativní prostřednictvím kódu a prostřednictvím rozšíření pro konfiguraci modelu služby.  
  
## <a name="adding-the-message-inspector-through-configuration"></a>Přidání Inspector zprávy prostřednictvím konfigurace  
 Konfigurace vlastní chování pro koncový bod v konfiguračním souboru aplikace, modelu služby vyžaduje implementátory pro vytvoření konfigurace *elementu rozšíření* reprezentována třídy odvozené od <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>. Toto rozšíření musí pak přidá do modelu služby konfigurační oddíl pro rozšíření, jak je uvedeno pro následující rozšíření popsaných v této části.  
  
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
  
 Rozšíření mohou být přidány, v aplikaci nebo konfigurační soubor technologie ASP.NET, což je nejběžnější volbou, nebo v konfiguračním souboru počítače.  
  
 Když rozšíření se přidá do konfigurace oboru, chování lze přidat do konfigurace chování znázorněné v následujícím kódu. Konfigurace chování jsou opakovaně použitelné prvky, které lze použít pro několik koncových bodů podle potřeby. Protože konkrétní chování být nakonfigurované zde implementuje <xref:System.ServiceModel.Description.IEndpointBehavior>, je platný pouze v příslušných konfiguračního oddílu v konfiguračním souboru.  
  
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
  
 `<schemaValidator>` Element, který nakonfiguruje zpráva inspector je zálohovaný díky `SchemaValidationBehaviorExtensionElement` třídy. Třída zpřístupní dvě Boolean veřejné vlastnosti s názvem `ValidateRequest` a `ValidateReply`. Obě tyto jsou označené <xref:System.Configuration.ConfigurationPropertyAttribute>. Tento atribut se považuje za propojení mezi vlastnosti kódu a atributy XML, které můžete zobrazit na předchozí elementu XML konfigurace. Třída také obsahuje vlastnost `Schemas` , kromě označena <xref:System.Configuration.ConfigurationCollectionAttribute> a je typu `SchemaCollection`, což je také součástí této ukázky ale vynechání z tohoto dokumentu jako stručný výtah. Tato vlastnost spolu s kolekce a třída prvku kolekce `SchemaConfigElement` zálohuje `<schemas>` element v předchozím fragmentu kódu konfigurace a umožňuje přidání kolekci schémat sady ověření.  
  
 Přepsané `CreateBehavior` metoda změní konfigurační data do objektu chování, když modul runtime vyhodnocuje konfigurační data, protože sestavuje klienta nebo koncový bod.  
  
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
  
## <a name="adding-message-inspectors-imperatively"></a>Imperativní přidání inspektoři zpráv  
 S výjimkou prostřednictvím atributy (které není podporováno v této ukázce z důvodu citovalo dříve) a konfigurace chování lze velmi snadno přidat do klienta a služby modulu runtime použijte imperativní kódu. V této ukázce se provádí v aplikaci klienta k testování inspector zpráv klienta. `GenericClient` Je třída odvozená z <xref:System.ServiceModel.ClientBase%601>, který zpřístupňuje konfigurace koncového bodu do uživatelského kódu. Klient je implicitně otevřít konfiguraci koncového bodu lze změnit, například přidáním chování, jak je znázorněno v následujícím kódu. Přidání chování služby je z velké části ekvivalentní technika klienta tady uvedené a musí být provedeny před otevření hostitele služby.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageInspectors`  
  
## <a name="see-also"></a>Viz také
