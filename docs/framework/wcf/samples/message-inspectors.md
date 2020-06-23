---
title: Inspektoři zpráv
description: Naučte se implementovat a konfigurovat nástroje pro kontrolu zpráv klienta a služeb WCF, které poskytují mechanismus ověřování zpráv.
ms.date: 03/30/2017
ms.assetid: 9bd1f305-ad03-4dd7-971f-fa1014b97c9b
ms.openlocfilehash: 20abb655a58f9dce4a967ade9b51db90eed2375b
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246204"
---
# <a name="message-inspectors"></a>Inspektoři zpráv
Tato ukázka předvádí, jak implementovat a nakonfigurovat kontrolory zpráv klienta a služby.  
  
 Kontrola zprávy je objekt rozšiřitelnosti, který se dá použít v modulu runtime klienta modelu služby a za běhu prostřednictvím kódu programu nebo prostřednictvím konfigurace a který může kontrolovat a měnit zprávy po jejich přijetí nebo před jejich odesláním.  
  
 Tato ukázka implementuje základní mechanismus ověřování zprávy klienta a služby, který ověřuje příchozí zprávy se sadou konfigurovatelných dokumentů XML schématu. Všimněte si, že tato ukázka neověřuje zprávy pro každou operaci. Toto je úmyslné zjednodušení.  
  
## <a name="message-inspector"></a>Kontrola zpráv  
 Nástroje pro kontrolu zpráv klienta implementují rozhraní a nástroje pro <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> zprávy služby implementují <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> rozhraní. Implementace mohou být kombinovány do jedné třídy, aby bylo možné vytvořit kontrolor zprávy, který funguje na obou stranách. Tato ukázka implementuje takový kombinovaný inspektor zpráv. Inspektor se sestaví do sady schémat, u kterých jsou ověřovány příchozí a odchozí zprávy, a umožňuje vývojářům určit, zda jsou příchozí nebo odchozí zprávy ověřeny a zda je kontrolor v režimu odeslání nebo klienta, který má vliv na zpracování chyb, jak je popsáno dále v tomto tématu.  
  
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
  
 Inspektoři zpráv služby (dispečer) musí implementovat tyto dvě <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> metody <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> a <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29> .  
  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>je vyvolána dispečerem, když byla přijata zpráva, zpracována zásobníkem kanálu a přiřazena ke službě, ale před tím, než je deserializována a odeslána na operaci. Pokud byla příchozí zpráva zašifrována, je zpráva při dosažení kontroly zprávy již dešifrována. Metoda obdrží `request` zprávu předanou jako parametr reference, který umožňuje kontrolu a manipulaci se zprávami podle potřeby. Návratová hodnota může být libovolný objekt a používá se jako objekt stavu korelace, který se předává, <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> když služba vrátí odpověď na aktuální zprávu. V této ukázce <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> deleguje kontrolu (ověření) zprávy na soukromou místní metodu `ValidateMessageBody` a nevrátí objekt stavu korelace. Tato metoda zajistí, že do služby přecházejí žádné neplatné zprávy.  
  
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
  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>Vyvolá se vždy, když je odpověď připravena k odeslání zpět klientovi nebo v případě jednosměrné zprávy, když byla příchozí zpráva zpracována. Díky tomu můžou rozšíření počítat symetricky, bez ohledu na MEP. Stejně jako v je <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> zpráva předána jako parametr reference a lze ji zkontrolovat, upravit nebo nahradit. Ověření zprávy, která je provedena v této ukázce, je znovu delegováno na `ValidMessageBody` metodu, ale zpracování chyb ověřování je v tomto případě mírně odlišné.  
  
 Pokud dojde k chybě ověřování ve službě, `ValidateMessageBody` metoda vyvolá <xref:System.ServiceModel.FaultException> odvozenou výjimku. V nástroji je <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> možné tyto výjimky umístit do infrastruktury Service Model, kde jsou automaticky transformované na chyby protokolu SOAP a přeneseny do klienta. V <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> nástroji <xref:System.ServiceModel.FaultException> nesmí být výjimky vloženy do infrastruktury, protože transformace výjimek chyb vyvolaných službou probíhá před zavoláním funkce kontrolor zprávy. Proto následující implementace zachytí známou `ReplyValidationFault` výjimku a nahradí zprávu odpovědi pomocí explicitní zprávy o chybě. Tato metoda zajistí, že implementace služby nevrátí žádné neplatné zprávy.  
  
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
  
 Kontroler zprávy klienta je velmi podobný. Dvě metody, které musí být implementovány z <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> jsou <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> a <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> .  
  
 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>je vyvolána, když je zpráva vytvořena buď klientskou aplikací, nebo formátovacím modulem operace. Stejně jako u kontrolorů zpráv dispečera může být zpráva jen zkontrolována nebo zcela nahrazena. V této ukázce inspektor deleguje na stejnou místní `ValidateMessageBody` pomocnou metodu, která se používá také pro kontrolory odesílání zpráv.  
  
 Rozdíl mezi chováními klienta a služby (jak je uvedeno v konstruktoru) je, že ověřování klienta vyvolá místní výjimky, které jsou vloženy do uživatelského kódu, protože se vyskytují místně, a ne kvůli selhání služby. Obecně platí, že kontrolory dispečerů služeb vyvolávají chyby a že kontroloři klienta vyvolávají výjimky.  
  
 Tato <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementace zajišťuje, že službě nejsou odesílány žádné neplatné zprávy.  
  
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
  
 `AfterReceiveReply`Implementace zajišťuje, aby nepřijaté zprávy ze služby nebyly přenášeny do uživatelského kódu klienta.  
  
```csharp  
void IClientMessageInspector.AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        ValidateMessageBody(ref reply, false);  
    }  
}  
```  
  
 Srdcem tohoto konkrétního inspektoru zprávy je `ValidateMessageBody` metoda. Chcete-li provést svou práci, zabalí ověřování <xref:System.Xml.XmlReader> kolem podstromu obsahu předané zprávy. Čtecí modul se naplní sadou schémat, které obsahuje inspektor zprávy a zpětné volání ověřování je nastaveno na delegáta odkazující na objekt `InspectionValidationHandler` , který je definován společně s touto metodou. K provedení ověření se zpráva načte a zařadí do paměťového streamu, která se bude zálohovat <xref:System.Xml.XmlDictionaryWriter> . Pokud dojde k chybě nebo varování ověřování v procesu, je vyvolána metoda zpětného volání.  
  
 Pokud nedojde k žádné chybě, vytvoří se nová zpráva, která zkopíruje vlastnosti a hlavičky z původní zprávy a použije aktuálně ověřenou informační sadu v paměťovém streamu, která je zabalena <xref:System.Xml.XmlDictionaryReader> a přidána do nahrazující zprávy.  
  
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
  
 `InspectionValidationHandler`Metoda je volána při ověřování <xref:System.Xml.XmlReader> při každém výskytu chyby nebo varování ověřování schématu. Následující implementace funguje jenom s chybami a ignoruje všechna upozornění.  
  
 Při prvním zvážení se může zdát, že je možné do <xref:System.Xml.XmlReader> zprávy s nástrojem pro kontrolu zpráv vložit ověřování a umožnit tak ověření, když se zpráva zpracovává, a bez uložení zprávy do vyrovnávací paměti. To však znamená, že toto zpětné volání vyvolá výjimky ověřování někam do infrastruktury modelu služby nebo kód uživatele jako neplatné uzly XML, což vede k nepředvídatelnému chování. Přístup do vyrovnávací paměti chrání uživatelský kód z neplatných zpráv, a to zcela.  
  
 Jak už bylo popsáno, výjimky vyvolané obslužnou rutinou se liší mezi klientem a službou. U služby jsou výjimky odvozeny z <xref:System.ServiceModel.FaultException> , v klientovi jsou výjimky běžnými vlastními výjimkami.  
  
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
 Nástroje pro kontrolu zpráv jsou rozšířeními modulu runtime klienta nebo odeslání. Taková rozšíření se konfigurují pomocí *chování*. Chování je třída, která mění chování modulu runtime modelu služby změnou výchozí konfigurace nebo přidáním rozšíření (například kontrolorů zpráv) do této třídy.  
  
 Následující `SchemaValidationBehavior` Třída je chování, které se používá k přidání tohoto ukázkového inspektoru zprávy do klienta nebo modulu runtime odeslání. V obou případech je implementace spíše základní. V <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> a <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A> je kontrolor zprávy vytvořen a přidán do <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> kolekce příslušného modulu runtime.  
  
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
> Toto konkrétní chování se nezdvojnásobuje jako atribut, a proto jej nelze přidat deklarativně na typ kontraktu typu služba. Toto je rozhodnutí podle návrhu, protože kolekci schématu nelze načíst v deklaraci atributu a odkazování na další umístění konfigurace (například na nastavení aplikace) v tomto atributu znamená vytvoření konfiguračního prvku, který není konzistentní se zbytkem konfigurace modelu služby. Proto lze toto chování přidat pouze imperativně prostřednictvím kódu a prostřednictvím rozšíření konfigurace modelu služby.  
  
## <a name="adding-the-message-inspector-through-configuration"></a>Přidání nástroje Message Inspector prostřednictvím konfigurace  
 Pro konfiguraci vlastního chování na koncovém bodu v konfiguračním souboru aplikace vyžaduje model služby implementátory, aby vytvořil *element rozšíření* konfigurace reprezentovaný třídou odvozenou z <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> . Toto rozšíření je pak nutné přidat do konfiguračního oddílu modelu služby pro rozšíření, jak je znázorněno na následujícím rozšíření popsaném v této části.  
  
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
  
 Rozšíření lze přidat do konfiguračního souboru aplikace nebo ASP.NET, což je nejběžnější volba, nebo v konfiguračním souboru počítače.  
  
 Když je rozšíření přidáno do oboru konfigurace, může být chování přidáno do konfigurace chování, jak je uvedeno v následujícím kódu. Konfigurace chování jsou opakovaně použitelné prvky, které lze použít na více koncových bodů podle potřeby. Vzhledem k tomu, že konkrétní chování, které má být nakonfigurováno <xref:System.ServiceModel.Description.IEndpointBehavior> , implementuje, je platné pouze v příslušném konfiguračním oddílu konfiguračního souboru.  
  
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
  
 `<schemaValidator>`Prvek, který konfiguruje inspektor zprávy, je zajištěn `SchemaValidationBehaviorExtensionElement` třídou. Třída zpřístupňuje dvě logické veřejné vlastnosti s názvem `ValidateRequest` a `ValidateReply` . Oba z nich jsou označeny pomocí <xref:System.Configuration.ConfigurationPropertyAttribute> . Tento atribut představuje propojení mezi vlastnostmi kódu a atributy XML, které lze zobrazit v předchozím elementu konfigurace XML. Třída má také vlastnost `Schemas` , která je dále označena atributem <xref:System.Configuration.ConfigurationCollectionAttribute> a je typu `SchemaCollection` , který je také součástí této ukázky, ale je vynechán z tohoto dokumentu pro zkrácení. Tato vlastnost spolu s kolekcí a třídou prvků kolekce `SchemaConfigElement` vrací `<schemas>` prvek v předchozím fragmentu konfigurace a umožňuje přidat kolekci schémat do sady ověření.  
  
 Přepsaná `CreateBehavior` metoda změní konfigurační data na objekt chování, když modul runtime vyhodnotí konfigurační data při sestavení klienta nebo koncového bodu.  
  
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
  
## <a name="adding-message-inspectors-imperatively"></a>Naléhavé přidávání inspektoři zpráv  
 S výjimkou atributů (které nejsou v této ukázce podporovány pro důvod citované dříve) a konfiguraci, lze chování poměrně snadno přidat do klienta a modulu runtime služby pomocí imperativního kódu. V této ukázce se to provádí v klientské aplikaci, aby se otestovala kontrola klientských zpráv. `GenericClient`Třída je odvozena z <xref:System.ServiceModel.ClientBase%601> , která zpřístupňuje konfiguraci koncového bodu s uživatelským kódem. Předtím, než bude klient implicitně otevřen, může být konfigurace koncového bodu změněna, například přidáním chování, jak je znázorněno v následujícím kódu. Přidání chování v rámci služby je v podstatě ekvivalentní s níže uvedenou technikou klienta, kterou je třeba provést před otevřením hostitele služby.  
  
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
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageInspectors`  
