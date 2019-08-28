---
title: Inspektoři zpráv
ms.date: 03/30/2017
ms.assetid: 9bd1f305-ad03-4dd7-971f-fa1014b97c9b
ms.openlocfilehash: e7846b8710fa52a5b13de245b8b7147e217533db
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039404"
---
# <a name="message-inspectors"></a><span data-ttu-id="a5eee-102">Inspektoři zpráv</span><span class="sxs-lookup"><span data-stu-id="a5eee-102">Message Inspectors</span></span>
<span data-ttu-id="a5eee-103">Tato ukázka předvádí, jak implementovat a nakonfigurovat kontrolory zpráv klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="a5eee-103">This sample demonstrates how to implement and configure client and service message inspectors.</span></span>  
  
 <span data-ttu-id="a5eee-104">Kontrola zprávy je objekt rozšiřitelnosti, který se dá použít v modulu runtime klienta modelu služby a za běhu prostřednictvím kódu programu nebo prostřednictvím konfigurace a který může kontrolovat a měnit zprávy po jejich přijetí nebo před jejich odesláním.</span><span class="sxs-lookup"><span data-stu-id="a5eee-104">A message inspector is an extensibility object that can be used in the service model's client runtime and dispatch runtime programmatically or through configuration and that can inspect and alter messages after they are received or before they are sent.</span></span>  
  
 <span data-ttu-id="a5eee-105">Tato ukázka implementuje základní mechanismus ověřování zprávy klienta a služby, který ověřuje příchozí zprávy se sadou konfigurovatelných dokumentů XML schématu.</span><span class="sxs-lookup"><span data-stu-id="a5eee-105">This sample implements a basic client and service message validation mechanism that validates incoming messages against a set of configurable XML Schema documents.</span></span> <span data-ttu-id="a5eee-106">Všimněte si, že tato ukázka neověřuje zprávy pro každou operaci.</span><span class="sxs-lookup"><span data-stu-id="a5eee-106">Note that this sample does not validate messages for each operation.</span></span> <span data-ttu-id="a5eee-107">Toto je úmyslné zjednodušení.</span><span class="sxs-lookup"><span data-stu-id="a5eee-107">This is an intentional simplification.</span></span>  
  
## <a name="message-inspector"></a><span data-ttu-id="a5eee-108">Kontrola zpráv</span><span class="sxs-lookup"><span data-stu-id="a5eee-108">Message Inspector</span></span>  
 <span data-ttu-id="a5eee-109">Nástroje pro kontrolu zpráv klienta implementují rozhraní a nástroje pro <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> zprávy služby <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> implementují rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a5eee-109">Client message inspectors implement the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> interface and service message inspectors implement the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> interface.</span></span> <span data-ttu-id="a5eee-110">Implementace mohou být kombinovány do jedné třídy, aby bylo možné vytvořit kontrolor zprávy, který funguje na obou stranách.</span><span class="sxs-lookup"><span data-stu-id="a5eee-110">The implementations can be combined into a single class to form a message inspector that works for both sides.</span></span> <span data-ttu-id="a5eee-111">Tato ukázka implementuje takový kombinovaný inspektor zpráv.</span><span class="sxs-lookup"><span data-stu-id="a5eee-111">This sample implements such a combined message inspector.</span></span> <span data-ttu-id="a5eee-112">Inspektor se sestaví tak, že se předává do sady schémat, na které se ověřují příchozí a odchozí zprávy, a umožňuje vývojářům určit, jestli se mají ověřit příchozí nebo odchozí zprávy a jestli je kontrolor v režimu odeslání nebo klienta. má vliv na zpracování chyb, jak je popsáno dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="a5eee-112">The inspector is constructed passing in a set of schemas against which incoming and outgoing messages are validated and allows the developer to specify whether incoming or outgoing messages are validated and whether the inspector is in dispatch or client mode, which affects the error handling as discussed later in this topic.</span></span>  
  
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
  
 <span data-ttu-id="a5eee-113">Inspektoři zpráv služby (dispečer) musí implementovat tyto dvě <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> metody <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> a <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.</span><span class="sxs-lookup"><span data-stu-id="a5eee-113">Any service (dispatcher) message inspector must implement the two <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> methods <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> and <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.</span></span>  
  
 <span data-ttu-id="a5eee-114"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>je vyvolána dispečerem, když byla přijata zpráva, zpracována zásobníkem kanálu a přiřazena ke službě, ale před tím, než je deserializována a odeslána na operaci.</span><span class="sxs-lookup"><span data-stu-id="a5eee-114"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> is invoked by the dispatcher when a message has been received, processed by the channel stack and assigned to a service, but before it is deserialized and dispatched to an operation.</span></span> <span data-ttu-id="a5eee-115">Pokud byla příchozí zpráva zašifrována, je zpráva při dosažení kontroly zprávy již dešifrována.</span><span class="sxs-lookup"><span data-stu-id="a5eee-115">If the incoming message was encrypted, the message is already decrypted when it reaches the message inspector.</span></span> <span data-ttu-id="a5eee-116">Metoda obdrží `request` zprávu předanou jako parametr reference, který umožňuje kontrolu a manipulaci se zprávami podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="a5eee-116">The method gets the `request` message passed as a reference parameter, which allows the message to be inspected, manipulated or replaced as required.</span></span> <span data-ttu-id="a5eee-117">Návratová hodnota může být libovolný objekt a používá se jako objekt stavu korelace, který se předává <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> , když služba vrátí odpověď na aktuální zprávu.</span><span class="sxs-lookup"><span data-stu-id="a5eee-117">The return value can be any object and is used as a correlation state object that is passed to <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> when the service returns a reply to the current message.</span></span> <span data-ttu-id="a5eee-118">V této ukázce <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> deleguje kontrolu (ověření) zprávy na soukromou místní metodu `ValidateMessageBody` a nevrátí objekt stavu korelace.</span><span class="sxs-lookup"><span data-stu-id="a5eee-118">In this sample, <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> delegates the inspection (validation) of the message to the private, local method `ValidateMessageBody` and returns no correlation state object.</span></span> <span data-ttu-id="a5eee-119">Tato metoda zajistí, že do služby přecházejí žádné neplatné zprávy.</span><span class="sxs-lookup"><span data-stu-id="a5eee-119">This method ensures that no invalid messages pass into the service.</span></span>  
  
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
  
 <span data-ttu-id="a5eee-120"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>Vyvolá se vždy, když je odpověď připravena k odeslání zpět klientovi nebo v případě jednosměrné zprávy, když byla příchozí zpráva zpracována.</span><span class="sxs-lookup"><span data-stu-id="a5eee-120"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29> is invoked whenever a reply is ready to be sent back to a client, or in the case of one-way messages, when the incoming message has been processed.</span></span> <span data-ttu-id="a5eee-121">Díky tomu můžou rozšíření počítat symetricky, bez ohledu na MEP.</span><span class="sxs-lookup"><span data-stu-id="a5eee-121">This allows extensions to count on being called symmetrically, regardless of MEP.</span></span> <span data-ttu-id="a5eee-122"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>Stejně jako v je zpráva předána jako parametr reference a lze ji zkontrolovat, upravit nebo nahradit.</span><span class="sxs-lookup"><span data-stu-id="a5eee-122">As with <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, the message is passed as a reference parameter and can be inspected, modified or replaced.</span></span> <span data-ttu-id="a5eee-123">Ověření zprávy, která je provedena v této ukázce, je znovu delegováno na `ValidMessageBody` metodu, ale zpracování chyb ověřování je v tomto případě mírně odlišné.</span><span class="sxs-lookup"><span data-stu-id="a5eee-123">The validation of the message that is performed in this sample is again delegated to the `ValidMessageBody` method, but the handling of validation errors is slightly different in this case.</span></span>  
  
 <span data-ttu-id="a5eee-124">Pokud dojde k chybě ověřování ve službě, `ValidateMessageBody` metoda vyvolá <xref:System.ServiceModel.FaultException>odvozenou výjimku.</span><span class="sxs-lookup"><span data-stu-id="a5eee-124">If a validation error occurs on the service, the `ValidateMessageBody` method throws <xref:System.ServiceModel.FaultException>-derived exceptions.</span></span> <span data-ttu-id="a5eee-125">V <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>nástroji je možné tyto výjimky umístit do infrastruktury Service Model, kde jsou automaticky transformované na chyby protokolu SOAP a přeneseny do klienta.</span><span class="sxs-lookup"><span data-stu-id="a5eee-125">In <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, these exceptions can be put into the service model infrastructure where they are automatically transformed into SOAP faults and relayed to the client.</span></span> <span data-ttu-id="a5eee-126">V <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>nástrojinesmí být výjimkyvloženydoinfrastruktury,protožetransformacevýjimekchybvyvolanýchslužbouprobíhápředzavolánímfunkcekontrolorzprávy.<xref:System.ServiceModel.FaultException></span><span class="sxs-lookup"><span data-stu-id="a5eee-126">In <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>, <xref:System.ServiceModel.FaultException> exceptions must not be put into the infrastructure, because the transformation of fault exceptions thrown by the service occurs before the message inspector is called.</span></span> <span data-ttu-id="a5eee-127">Proto následující implementace zachytí známou `ReplyValidationFault` výjimku a nahradí zprávu odpovědi pomocí explicitní zprávy o chybě.</span><span class="sxs-lookup"><span data-stu-id="a5eee-127">Therefore the following implementation catches the known `ReplyValidationFault` exception and replaces the reply message with an explicit fault message.</span></span> <span data-ttu-id="a5eee-128">Tato metoda zajistí, že implementace služby nevrátí žádné neplatné zprávy.</span><span class="sxs-lookup"><span data-stu-id="a5eee-128">This method ensures that no invalid messages are returned by the service implementation.</span></span>  
  
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
  
 <span data-ttu-id="a5eee-129">Kontroler zprávy klienta je velmi podobný.</span><span class="sxs-lookup"><span data-stu-id="a5eee-129">The client message inspector is very similar.</span></span> <span data-ttu-id="a5eee-130">Dvě metody, které musí být implementovány <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> z <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> jsou <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>a.</span><span class="sxs-lookup"><span data-stu-id="a5eee-130">The two methods that must be implemented from <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> are <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> and <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>.</span></span>  
  
 <span data-ttu-id="a5eee-131"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>je vyvolána, když je zpráva vytvořena buď klientskou aplikací, nebo formátovacím modulem operace.</span><span class="sxs-lookup"><span data-stu-id="a5eee-131"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> is invoked when the message has been composed either by the client application or by the operation formatter.</span></span> <span data-ttu-id="a5eee-132">Stejně jako u kontrolorů zpráv dispečera může být zpráva jen zkontrolována nebo zcela nahrazena.</span><span class="sxs-lookup"><span data-stu-id="a5eee-132">As with the dispatcher message inspectors, the message can just be inspected or entirely replaced.</span></span> <span data-ttu-id="a5eee-133">V této ukázce inspektor deleguje na stejnou místní `ValidateMessageBody` pomocnou metodu, která se používá také pro kontrolory odesílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="a5eee-133">In this sample, the inspector delegates to the same local `ValidateMessageBody` helper method that is also used for the dispatch message inspectors.</span></span>  
  
 <span data-ttu-id="a5eee-134">Rozdíl mezi chováními klienta a služby (jak je uvedeno v konstruktoru) je, že ověřování klienta vyvolá místní výjimky, které jsou vloženy do uživatelského kódu, protože se vyskytují místně, a ne kvůli selhání služby.</span><span class="sxs-lookup"><span data-stu-id="a5eee-134">The behavioral difference between the client and service validation (as specified in the constructor) is that the client validation throws local exceptions that are put into the user code because they occur locally and not because of a service failure.</span></span> <span data-ttu-id="a5eee-135">Obecně platí, že kontrolory dispečerů služeb vyvolávají chyby a že kontroloři klienta vyvolávají výjimky.</span><span class="sxs-lookup"><span data-stu-id="a5eee-135">Generally, the rule is that service dispatcher inspectors throw faults and that client inspectors throw exceptions.</span></span>  
  
 <span data-ttu-id="a5eee-136">Tato <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementace zajišťuje, že službě nejsou odesílány žádné neplatné zprávy.</span><span class="sxs-lookup"><span data-stu-id="a5eee-136">This <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementation ensures that no invalid messages are sent to the service.</span></span>  
  
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
  
 <span data-ttu-id="a5eee-137">`AfterReceiveReply` Implementace zajišťuje, aby nepřijaté zprávy ze služby nebyly přenášeny do uživatelského kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="a5eee-137">The `AfterReceiveReply` implementation ensures that no invalid messages received from the service are relayed to the client user code.</span></span>  
  
```  
void IClientMessageInspector.AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        ValidateMessageBody(ref reply, false);  
    }  
}  
```  
  
 <span data-ttu-id="a5eee-138">Srdcem tohoto konkrétního inspektoru zprávy je `ValidateMessageBody` metoda.</span><span class="sxs-lookup"><span data-stu-id="a5eee-138">The heart of this particular message inspector is the `ValidateMessageBody` method.</span></span> <span data-ttu-id="a5eee-139">Chcete-li provést svou práci, zabalí ověřování <xref:System.Xml.XmlReader> kolem podstromu obsahu předané zprávy.</span><span class="sxs-lookup"><span data-stu-id="a5eee-139">To perform its work, it wraps a validating <xref:System.Xml.XmlReader> around the body content sub-tree of the passed message.</span></span> <span data-ttu-id="a5eee-140">Čtecí modul se naplní sadou schémat, které obsahuje inspektor zprávy a zpětné volání ověřování je nastaveno na delegáta odkazující na `InspectionValidationHandler` objekt, který je definován společně s touto metodou.</span><span class="sxs-lookup"><span data-stu-id="a5eee-140">The reader is populated with the set of schemas that the message inspector holds and the validation callback is set to a delegate referring to the `InspectionValidationHandler` that is defined alongside this method.</span></span> <span data-ttu-id="a5eee-141">K provedení ověření se zpráva načte a zařadí do paměťového streamu, která se bude zálohovat <xref:System.Xml.XmlDictionaryWriter>.</span><span class="sxs-lookup"><span data-stu-id="a5eee-141">To perform the validation, the message is then read and spooled into a memory stream-backed <xref:System.Xml.XmlDictionaryWriter>.</span></span> <span data-ttu-id="a5eee-142">Pokud dojde k chybě nebo varování ověřování v procesu, je vyvolána metoda zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="a5eee-142">If a validation error or warning occurs in the process, the callback method is invoked.</span></span>  
  
 <span data-ttu-id="a5eee-143">Pokud nedojde k žádné chybě, vytvoří se nová zpráva, která zkopíruje vlastnosti a hlavičky z původní zprávy a použije aktuálně ověřenou informační sadu v paměťovém streamu, která je zabalena <xref:System.Xml.XmlDictionaryReader> a přidána do nahrazující zprávy.</span><span class="sxs-lookup"><span data-stu-id="a5eee-143">If no error occurs, a new message is constructed that copies the properties and headers from the original message and uses the now-validated infoset in the memory stream, which is wrapped by an <xref:System.Xml.XmlDictionaryReader> and added to the replacement message.</span></span>  
  
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
  
 <span data-ttu-id="a5eee-144">Metoda je volána při ověřování <xref:System.Xml.XmlReader> při každém výskytu chyby nebo varování ověřování schématu. `InspectionValidationHandler`</span><span class="sxs-lookup"><span data-stu-id="a5eee-144">The `InspectionValidationHandler` method is called by the validating <xref:System.Xml.XmlReader> whenever a schema validation error or warning occurs.</span></span> <span data-ttu-id="a5eee-145">Následující implementace funguje jenom s chybami a ignoruje všechna upozornění.</span><span class="sxs-lookup"><span data-stu-id="a5eee-145">The following implementation only works with errors and ignores all warnings.</span></span>  
  
 <span data-ttu-id="a5eee-146">Při prvním zvážení se může zdát, že je možné do <xref:System.Xml.XmlReader> zprávy s nástrojem pro kontrolu zpráv vložit ověřování a umožnit tak ověření, když se zpráva zpracovává, a bez uložení zprávy do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="a5eee-146">On first consideration, it might seem possible to inject a validating <xref:System.Xml.XmlReader> into the message with the message inspector and let the validation happen as the message is processed and without buffering the message.</span></span> <span data-ttu-id="a5eee-147">To však znamená, že toto zpětné volání vyvolá výjimky ověřování někam do infrastruktury modelu služby nebo kód uživatele jako neplatné uzly XML, což vede k nepředvídatelnému chování.</span><span class="sxs-lookup"><span data-stu-id="a5eee-147">That, however, means that this callback throws the validation exceptions somewhere into the service model infrastructure or the user code as invalid XML nodes are detected, resulting in unpredictable behavior.</span></span> <span data-ttu-id="a5eee-148">Přístup do vyrovnávací paměti chrání uživatelský kód z neplatných zpráv, a to zcela.</span><span class="sxs-lookup"><span data-stu-id="a5eee-148">The buffering approach shields the user code from invalid messages, entirely.</span></span>  
  
 <span data-ttu-id="a5eee-149">Jak už bylo popsáno, výjimky vyvolané obslužnou rutinou se liší mezi klientem a službou.</span><span class="sxs-lookup"><span data-stu-id="a5eee-149">As previously discussed, the exceptions thrown by the handler differ between the client and the service.</span></span> <span data-ttu-id="a5eee-150">U služby jsou výjimky odvozeny z <xref:System.ServiceModel.FaultException>, v klientovi jsou výjimky běžnými vlastními výjimkami.</span><span class="sxs-lookup"><span data-stu-id="a5eee-150">On the service, the exceptions are derived from <xref:System.ServiceModel.FaultException>, on the client the exceptions are regular custom exceptions.</span></span>  
  
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
  
## <a name="behavior"></a><span data-ttu-id="a5eee-151">Chování</span><span class="sxs-lookup"><span data-stu-id="a5eee-151">Behavior</span></span>  
 <span data-ttu-id="a5eee-152">Nástroje pro kontrolu zpráv jsou rozšířeními modulu runtime klienta nebo odeslání.</span><span class="sxs-lookup"><span data-stu-id="a5eee-152">Message inspectors are extensions to the client runtime or the dispatch runtime.</span></span> <span data-ttu-id="a5eee-153">Taková rozšíření se konfigurují pomocí *chování*.</span><span class="sxs-lookup"><span data-stu-id="a5eee-153">Such extensions are configured using *behaviors*.</span></span> <span data-ttu-id="a5eee-154">Chování je třída, která mění chování modulu runtime modelu služby změnou výchozí konfigurace nebo přidáním rozšíření (například kontrolorů zpráv) do této třídy.</span><span class="sxs-lookup"><span data-stu-id="a5eee-154">A behavior is a class that changes the behavior of the service model runtime by changing the default configuration or adding extensions (such as message inspectors) to it.</span></span>  
  
 <span data-ttu-id="a5eee-155">Následující `SchemaValidationBehavior` třída je chování, které se používá k přidání tohoto ukázkového inspektoru zprávy do klienta nebo modulu runtime odeslání.</span><span class="sxs-lookup"><span data-stu-id="a5eee-155">The following `SchemaValidationBehavior` class is the behavior used to add this sample's message inspector to the client or dispatch runtime.</span></span> <span data-ttu-id="a5eee-156">V obou případech je implementace spíše základní.</span><span class="sxs-lookup"><span data-stu-id="a5eee-156">The implementation is rather basic in both cases.</span></span> <span data-ttu-id="a5eee-157">V <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> a <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>je kontrolor zprávy vytvořen a přidán do kolekce příslušného modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="a5eee-157">In <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> and <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>, the message inspector is created and added to the <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> collection of the respective runtime.</span></span>  
  
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
> <span data-ttu-id="a5eee-158">Toto konkrétní chování se nezdvojnásobuje jako atribut, a proto jej nelze přidat deklarativně na typ kontraktu typu služba.</span><span class="sxs-lookup"><span data-stu-id="a5eee-158">This particular behavior does not double as an attribute and therefore cannot be added declaratively onto a contract type of a service type.</span></span> <span data-ttu-id="a5eee-159">Toto je rozhodnutí podle návrhu, protože kolekci schémat nelze načíst v deklaraci atributu a odkazování na další umístění konfigurace (například na nastavení aplikace) v tomto atributu znamená vytvoření konfiguračního prvku, který není konzistentní se zbytkem konfigurace modelu služby.</span><span class="sxs-lookup"><span data-stu-id="a5eee-159">This is a by-design decision made because the schema collection cannot be loaded in an attribute declaration and referring to an extra configuration location (for instance to the application settings) in this attribute means creating a configuration element that is not consistent with the rest of the service model configuration.</span></span> <span data-ttu-id="a5eee-160">Proto lze toto chování přidat pouze imperativně prostřednictvím kódu a prostřednictvím rozšíření konfigurace modelu služby.</span><span class="sxs-lookup"><span data-stu-id="a5eee-160">Therefore, this behavior can only be added imperatively through code and through a service model configuration extension.</span></span>  
  
## <a name="adding-the-message-inspector-through-configuration"></a><span data-ttu-id="a5eee-161">Přidání nástroje Message Inspector prostřednictvím konfigurace</span><span class="sxs-lookup"><span data-stu-id="a5eee-161">Adding the Message Inspector through Configuration</span></span>  
 <span data-ttu-id="a5eee-162">Pro konfiguraci vlastního chování na koncovém bodu v konfiguračním souboru aplikace vyžaduje model služby implementátory, aby vytvořil *element rozšíření* konfigurace reprezentovaný třídou odvozenou z <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>.</span><span class="sxs-lookup"><span data-stu-id="a5eee-162">For configuring a custom behavior on an endpoint in the application configuration file, the service model requires implementers to create a configuration *extension element* represented by a class derived from <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>.</span></span> <span data-ttu-id="a5eee-163">Toto rozšíření je pak nutné přidat do konfiguračního oddílu modelu služby pro rozšíření, jak je znázorněno na následujícím rozšíření popsaném v této části.</span><span class="sxs-lookup"><span data-stu-id="a5eee-163">This extension must then be added to the service model's configuration section for extensions as shown for the following extension discussed in this section.</span></span>  
  
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
  
 <span data-ttu-id="a5eee-164">Rozšíření lze přidat do konfiguračního souboru aplikace nebo ASP.NET, což je nejběžnější volba, nebo v konfiguračním souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="a5eee-164">Extensions can be added in the application or ASP.NET configuration file, which is the most common choice, or in the machine configuration file.</span></span>  
  
 <span data-ttu-id="a5eee-165">Když je rozšíření přidáno do oboru konfigurace, může být chování přidáno do konfigurace chování, jak je uvedeno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="a5eee-165">When the extension is added to a configuration scope, the behavior can be added to a behavior configuration as it is shown in the following code.</span></span> <span data-ttu-id="a5eee-166">Konfigurace chování jsou opakovaně použitelné prvky, které lze použít na více koncových bodů podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="a5eee-166">Behavior configurations are reusable elements that can be applied to multiple endpoints as required.</span></span> <span data-ttu-id="a5eee-167">Vzhledem k tomu, že konkrétní chování, které <xref:System.ServiceModel.Description.IEndpointBehavior>má být nakonfigurováno, implementuje, je platné pouze v příslušném konfiguračním oddílu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="a5eee-167">Because the particular behavior to be configured here implements <xref:System.ServiceModel.Description.IEndpointBehavior>, it is only valid in the respective configuration section in the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="a5eee-168">Prvek, který konfiguruje inspektor zprávy, je `SchemaValidationBehaviorExtensionElement` zajištěn třídou. `<schemaValidator>`</span><span class="sxs-lookup"><span data-stu-id="a5eee-168">The `<schemaValidator>` element that configures the message inspector is backed by the `SchemaValidationBehaviorExtensionElement` class.</span></span> <span data-ttu-id="a5eee-169">Třída zpřístupňuje dvě logické veřejné vlastnosti s `ValidateRequest` názvem `ValidateReply`a.</span><span class="sxs-lookup"><span data-stu-id="a5eee-169">The class exposes two Boolean public properties named `ValidateRequest` and `ValidateReply`.</span></span> <span data-ttu-id="a5eee-170">Oba z nich jsou označeny pomocí <xref:System.Configuration.ConfigurationPropertyAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a5eee-170">Both of these are marked with a <xref:System.Configuration.ConfigurationPropertyAttribute>.</span></span> <span data-ttu-id="a5eee-171">Tento atribut představuje propojení mezi vlastnostmi kódu a atributy XML, které lze zobrazit v předchozím elementu konfigurace XML.</span><span class="sxs-lookup"><span data-stu-id="a5eee-171">This attribute constitutes the link between the code properties and the XML attributes that can be seen on the preceding XML configuration element.</span></span> <span data-ttu-id="a5eee-172">Třída má také vlastnost `Schemas` , která je dále označena <xref:System.Configuration.ConfigurationCollectionAttribute> atributem a je typu `SchemaCollection`, který je také součástí této ukázky, ale je vynechán z tohoto dokumentu pro zkrácení.</span><span class="sxs-lookup"><span data-stu-id="a5eee-172">The class also has a property `Schemas` that is additionally marked with the <xref:System.Configuration.ConfigurationCollectionAttribute> and is of the type `SchemaCollection`, which is also part of this sample but omitted from this document for brevity.</span></span> <span data-ttu-id="a5eee-173">Tato vlastnost spolu s kolekcí a třídou `SchemaConfigElement` prvků kolekce vrací `<schemas>` prvek v předchozím fragmentu konfigurace a umožňuje přidat kolekci schémat do sady ověření.</span><span class="sxs-lookup"><span data-stu-id="a5eee-173">This property along with the collection and the collection element class `SchemaConfigElement` backs the `<schemas>` element in the preceding configuration snippet and allows adding a collection of schemas to the validation set.</span></span>  
  
 <span data-ttu-id="a5eee-174">Přepsaná `CreateBehavior` metoda změní konfigurační data na objekt chování, když modul runtime vyhodnotí konfigurační data při sestavení klienta nebo koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="a5eee-174">The overridden `CreateBehavior` method turns the configuration data into a behavior object when the runtime evaluates the configuration data as it builds a client or an endpoint.</span></span>  
  
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
  
## <a name="adding-message-inspectors-imperatively"></a><span data-ttu-id="a5eee-175">Naléhavé přidávání inspektoři zpráv</span><span class="sxs-lookup"><span data-stu-id="a5eee-175">Adding Message Inspectors Imperatively</span></span>  
 <span data-ttu-id="a5eee-176">S výjimkou atributů (které nejsou v této ukázce podporovány pro důvod citované dříve) a konfiguraci, lze chování poměrně snadno přidat do klienta a modulu runtime služby pomocí imperativního kódu.</span><span class="sxs-lookup"><span data-stu-id="a5eee-176">Except through attributes (which is not supported in this sample for the reason cited previously) and configuration, behaviors can quite easily be added to a client and service runtime using imperative code.</span></span> <span data-ttu-id="a5eee-177">V této ukázce se to provádí v klientské aplikaci, aby se otestovala kontrola klientských zpráv.</span><span class="sxs-lookup"><span data-stu-id="a5eee-177">In this sample, this is done in the client application to test the client message inspector.</span></span> <span data-ttu-id="a5eee-178">Třída je odvozena z <xref:System.ServiceModel.ClientBase%601>, která zpřístupňuje konfiguraci koncového bodu s uživatelským kódem. `GenericClient`</span><span class="sxs-lookup"><span data-stu-id="a5eee-178">The `GenericClient` class is derived from <xref:System.ServiceModel.ClientBase%601>, which exposes the endpoint configuration to the user code.</span></span> <span data-ttu-id="a5eee-179">Předtím, než bude klient implicitně otevřen, může být konfigurace koncového bodu změněna, například přidáním chování, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="a5eee-179">Before the client is implicitly opened the endpoint configuration can be changed, for instance by adding behaviors as shown in the following code.</span></span> <span data-ttu-id="a5eee-180">Přidání chování v rámci služby je v podstatě ekvivalentní s níže uvedenou technikou klienta, kterou je třeba provést před otevřením hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="a5eee-180">Adding the behavior on the service is largely equivalent to the client technique shown here and must be performed before the service host is opened.</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a5eee-181">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="a5eee-181">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a5eee-182">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a5eee-182">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a5eee-183">Při sestavování řešení postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a5eee-183">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="a5eee-184">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a5eee-184">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a5eee-185">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="a5eee-185">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a5eee-186">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="a5eee-186">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="a5eee-187">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="a5eee-187">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a5eee-188">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="a5eee-188">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageInspectors`  
