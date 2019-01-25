---
title: Inspektoři zpráv
ms.date: 03/30/2017
ms.assetid: 9bd1f305-ad03-4dd7-971f-fa1014b97c9b
ms.openlocfilehash: 99886ef112a74bb86346208c5c24b09349ba4027
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54552850"
---
# <a name="message-inspectors"></a><span data-ttu-id="725b7-102">Inspektoři zpráv</span><span class="sxs-lookup"><span data-stu-id="725b7-102">Message Inspectors</span></span>
<span data-ttu-id="725b7-103">Tento příklad ukazuje, jak implementovat a konfigurovat messageinspectors klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="725b7-103">This sample demonstrates how to implement and configure client and service message inspectors.</span></span>  
  
 <span data-ttu-id="725b7-104">Zpráva inspector je objekt rozšiřitelnosti, který lze použít v modelu služby klientů runtime a odeslání runtime programově nebo prostřednictvím konfigurace a že můžete zkontrolovat a změnit zpráv po jejich přijetí nebo před jejich odesláním.</span><span class="sxs-lookup"><span data-stu-id="725b7-104">A message inspector is an extensibility object that can be used in the service model's client runtime and dispatch runtime programmatically or through configuration and that can inspect and alter messages after they are received or before they are sent.</span></span>  
  
 <span data-ttu-id="725b7-105">Tato ukázka implementuje základní klient a služba zpráva ověřovací mechanismus, který ověří příchozí zprávy pro sadu konfigurovatelné dokumentů schématu XML.</span><span class="sxs-lookup"><span data-stu-id="725b7-105">This sample implements a basic client and service message validation mechanism that validates incoming messages against a set of configurable XML Schema documents.</span></span> <span data-ttu-id="725b7-106">Všimněte si, že tato ukázka neověřuje zpráv pro každou operaci.</span><span class="sxs-lookup"><span data-stu-id="725b7-106">Note that this sample does not validate messages for each operation.</span></span> <span data-ttu-id="725b7-107">To je úmyslné zjednodušení.</span><span class="sxs-lookup"><span data-stu-id="725b7-107">This is an intentional simplification.</span></span>  
  
## <a name="message-inspector"></a><span data-ttu-id="725b7-108">Zpráva inspektoru</span><span class="sxs-lookup"><span data-stu-id="725b7-108">Message Inspector</span></span>  
 <span data-ttu-id="725b7-109">Implementace inspektoři zpráv klienta <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> rozhraní a službu implementovat kontroly zprávy <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="725b7-109">Client message inspectors implement the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> interface and service message inspectors implement the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> interface.</span></span> <span data-ttu-id="725b7-110">Implementace zkombinovat do jedné třídy k vytvoření zprávy inspector, který se dá použít pro obě strany.</span><span class="sxs-lookup"><span data-stu-id="725b7-110">The implementations can be combined into a single class to form a message inspector that works for both sides.</span></span> <span data-ttu-id="725b7-111">Tato ukázka implementuje takové kombinované zpráva inspector.</span><span class="sxs-lookup"><span data-stu-id="725b7-111">This sample implements such a combined message inspector.</span></span> <span data-ttu-id="725b7-112">Inspektor je vytvořen při předávání v sadě schémat, kterými se ověří příchozí a odchozí zprávy a umožňuje vývojářům určit, jestli se ověřují příchozí nebo odchozí zprávy a určuje, zda inspector pracuje v režimu klienta nebo odeslání, který zpracování chyb ovlivní, jak je popsáno dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="725b7-112">The inspector is constructed passing in a set of schemas against which incoming and outgoing messages are validated and allows the developer to specify whether incoming or outgoing messages are validated and whether the inspector is in dispatch or client mode, which affects the error handling as discussed later in this topic.</span></span>  
  
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
  
 <span data-ttu-id="725b7-113">Žádné služby (odesílatel) zpráva inspektoru musí implementovat dvě <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> metody <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> a <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.</span><span class="sxs-lookup"><span data-stu-id="725b7-113">Any service (dispatcher) message inspector must implement the two <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> methods <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> and <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.</span></span>  
  
 <span data-ttu-id="725b7-114"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> Vyvolá dispečer při přijetí, zpracování kanálu zásobníku a přiřazeno ke službě zprávy, ale předtím, než je deserializovat a odeslaných do operace.</span><span class="sxs-lookup"><span data-stu-id="725b7-114"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> is invoked by the dispatcher when a message has been received, processed by the channel stack and assigned to a service, but before it is deserialized and dispatched to an operation.</span></span> <span data-ttu-id="725b7-115">Pokud příchozí zpráva byla zašifrována, je zpráva již dešifrovat dosáhne inspektor zprávy.</span><span class="sxs-lookup"><span data-stu-id="725b7-115">If the incoming message was encrypted, the message is already decrypted when it reaches the message inspector.</span></span> <span data-ttu-id="725b7-116">Získá metodu `request` zprávu předá jako parametr odkazu, který umožňuje zpráva, kterou chcete prozkoumat, manipulovat nebo nahradit podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="725b7-116">The method gets the `request` message passed as a reference parameter, which allows the message to be inspected, manipulated or replaced as required.</span></span> <span data-ttu-id="725b7-117">Návratová hodnota může být libovolný objekt a slouží jako korelace stav objektu, který je předán <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> Pokud služba vrátí odpověď na aktuální zprávu.</span><span class="sxs-lookup"><span data-stu-id="725b7-117">The return value can be any object and is used as a correlation state object that is passed to <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> when the service returns a reply to the current message.</span></span> <span data-ttu-id="725b7-118">V této ukázce <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> deleguje kontroly (ověřování) zprávy, která se metoda privátní, místní `ValidateMessageBody` a vrátí objekt stavu žádná korelace.</span><span class="sxs-lookup"><span data-stu-id="725b7-118">In this sample, <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> delegates the inspection (validation) of the message to the private, local method `ValidateMessageBody` and returns no correlation state object.</span></span> <span data-ttu-id="725b7-119">Tato metoda zajišťuje, že žádné neplatné zprávy předat do služby.</span><span class="sxs-lookup"><span data-stu-id="725b7-119">This method ensures that no invalid messages pass into the service.</span></span>  
  
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
  
 <span data-ttu-id="725b7-120"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29> je vyvolána pokaždé, když odpověď je připravená k odeslání zpět do klienta nebo v případě jednosměrného zpráv, po zpracování příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="725b7-120"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29> is invoked whenever a reply is ready to be sent back to a client, or in the case of one-way messages, when the incoming message has been processed.</span></span> <span data-ttu-id="725b7-121">To umožňuje rozšíření Spolehněte se na volání symetricky, bez ohledu na to MEP.</span><span class="sxs-lookup"><span data-stu-id="725b7-121">This allows extensions to count on being called symmetrically, regardless of MEP.</span></span> <span data-ttu-id="725b7-122">Stejně jako u <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, zprávy se předá jako parametr odkazu a lze ho zkontrolovat, upravit nebo nahradit.</span><span class="sxs-lookup"><span data-stu-id="725b7-122">As with <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, the message is passed as a reference parameter and can be inspected, modified or replaced.</span></span> <span data-ttu-id="725b7-123">Ověření zprávy, která se provádí v této ukázce se znovu deleguje na `ValidMessageBody` metody, ale zpracování chyb při ověřování se v tomto případě mírně liší.</span><span class="sxs-lookup"><span data-stu-id="725b7-123">The validation of the message that is performed in this sample is again delegated to the `ValidMessageBody` method, but the handling of validation errors is slightly different in this case.</span></span>  
  
 <span data-ttu-id="725b7-124">Pokud dojde k chybě ověření ve službě, `ValidateMessageBody` vyvolá metoda výjimku <xref:System.ServiceModel.FaultException>-odvozené výjimky.</span><span class="sxs-lookup"><span data-stu-id="725b7-124">If a validation error occurs on the service, the `ValidateMessageBody` method throws <xref:System.ServiceModel.FaultException>-derived exceptions.</span></span> <span data-ttu-id="725b7-125">V <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, tyto výjimky můžou být přepnuté do infrastruktury služby modelu, ve kterém jsou automaticky transformuje na chyb SOAP a předává do klienta.</span><span class="sxs-lookup"><span data-stu-id="725b7-125">In <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, these exceptions can be put into the service model infrastructure where they are automatically transformed into SOAP faults and relayed to the client.</span></span> <span data-ttu-id="725b7-126">V <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>, <xref:System.ServiceModel.FaultException> výjimky nesmí možné zařadit do infrastruktury, protože transformace selhání výjimky vyvolané službou vyskytuje před voláním inspektor zprávy.</span><span class="sxs-lookup"><span data-stu-id="725b7-126">In <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>, <xref:System.ServiceModel.FaultException> exceptions must not be put into the infrastructure, because the transformation of fault exceptions thrown by the service occurs before the message inspector is called.</span></span> <span data-ttu-id="725b7-127">Proto následující implementaci zachytí známých `ReplyValidationFault` výjimky a nahradí zprávu odpovědi s explicitní chybovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="725b7-127">Therefore the following implementation catches the known `ReplyValidationFault` exception and replaces the reply message with an explicit fault message.</span></span> <span data-ttu-id="725b7-128">Tato metoda zajišťuje, že žádné neplatné jsou vraceny v implementaci služby.</span><span class="sxs-lookup"><span data-stu-id="725b7-128">This method ensures that no invalid messages are returned by the service implementation.</span></span>  
  
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
  
 <span data-ttu-id="725b7-129">Inspektor zprávy klienta je velmi podobné.</span><span class="sxs-lookup"><span data-stu-id="725b7-129">The client message inspector is very similar.</span></span> <span data-ttu-id="725b7-130">Tyto dvě metody, které je třeba implementovat z <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> jsou <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> a <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>.</span><span class="sxs-lookup"><span data-stu-id="725b7-130">The two methods that must be implemented from <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> are <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> and <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>.</span></span>  
  
 <span data-ttu-id="725b7-131"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> je voláno, když má byla zpráva skládá klientská aplikace nebo formátovací modul operace.</span><span class="sxs-lookup"><span data-stu-id="725b7-131"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> is invoked when the message has been composed either by the client application or by the operation formatter.</span></span> <span data-ttu-id="725b7-132">Jak s dispečerem inspektoři zpráv, zprávy stačí, když ho zkontrolovat nebo zcela nahrazena.</span><span class="sxs-lookup"><span data-stu-id="725b7-132">As with the dispatcher message inspectors, the message can just be inspected or entirely replaced.</span></span> <span data-ttu-id="725b7-133">V této ukázce inspektor deleguje na stejnou místní `ValidateMessageBody` Pomocná metoda, která se používá také pro odeslání inspektoři zpráv.</span><span class="sxs-lookup"><span data-stu-id="725b7-133">In this sample, the inspector delegates to the same local `ValidateMessageBody` helper method that is also used for the dispatch message inspectors.</span></span>  
  
 <span data-ttu-id="725b7-134">Chování rozdíl mezi klientem a službou ověření (jak je uvedeno v konstruktoru) je, že ověřování na straně klienta vyvolá místní výjimky, které jsou vloženy do uživatelského kódu vzhledem k tomu, že k nim dojde místně a ne kvůli selhání služby.</span><span class="sxs-lookup"><span data-stu-id="725b7-134">The behavioral difference between the client and service validation (as specified in the constructor) is that the client validation throws local exceptions that are put into the user code because they occur locally and not because of a service failure.</span></span> <span data-ttu-id="725b7-135">Obecně platí je pravidlo, že služba dispečer kontroly vyvolat chyby a zda kontroly klienta vyvolávat výjimky.</span><span class="sxs-lookup"><span data-stu-id="725b7-135">Generally, the rule is that service dispatcher inspectors throw faults and that client inspectors throw exceptions.</span></span>  
  
 <span data-ttu-id="725b7-136">To <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementace zajistí, že žádné neplatné zprávy se odesílají do služby.</span><span class="sxs-lookup"><span data-stu-id="725b7-136">This <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementation ensures that no invalid messages are sent to the service.</span></span>  
  
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
  
 <span data-ttu-id="725b7-137">`AfterReceiveReply` Implementace zajistí, že žádné neplatné zprávy přijaté ze služby se předává do uživatelského kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="725b7-137">The `AfterReceiveReply` implementation ensures that no invalid messages received from the service are relayed to the client user code.</span></span>  
  
```  
void IClientMessageInspector.AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        ValidateMessageBody(ref reply, false);  
    }  
}  
```  
  
 <span data-ttu-id="725b7-138">Je srdcem tato kontrola konkrétní zprávy `ValidateMessageBody` metody.</span><span class="sxs-lookup"><span data-stu-id="725b7-138">The heart of this particular message inspector is the `ValidateMessageBody` method.</span></span> <span data-ttu-id="725b7-139">K provedení své práce, zabalí ověřování <xref:System.Xml.XmlReader> kolem textu dílčí stromu obsahu předané zprávy.</span><span class="sxs-lookup"><span data-stu-id="725b7-139">To perform its work, it wraps a validating <xref:System.Xml.XmlReader> around the body content sub-tree of the passed message.</span></span> <span data-ttu-id="725b7-140">Čtecí modul se vyplní sadu schémat, které obsahuje inspektor zprávy a zpětné volání pro ověření je nastavená na delegáta odkazující na `InspectionValidationHandler` , která je definována vedle této metody.</span><span class="sxs-lookup"><span data-stu-id="725b7-140">The reader is populated with the set of schemas that the message inspector holds and the validation callback is set to a delegate referring to the `InspectionValidationHandler` that is defined alongside this method.</span></span> <span data-ttu-id="725b7-141">K provedení ověření zprávy je přečtení a zařazení do paměti datového proudu zajišťuje <xref:System.Xml.XmlDictionaryWriter>.</span><span class="sxs-lookup"><span data-stu-id="725b7-141">To perform the validation, the message is then read and spooled into a memory stream-backed <xref:System.Xml.XmlDictionaryWriter>.</span></span> <span data-ttu-id="725b7-142">Pokud v procesu dojde k chybě nebo upozornění, je vyvolána metoda zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="725b7-142">If a validation error or warning occurs in the process, the callback method is invoked.</span></span>  
  
 <span data-ttu-id="725b7-143">Pokud nenastane žádná chyba novou zprávu je vytvořený, který kopíruje vlastnosti a záhlaví z původní zprávy a informační sadu ověřit nyní používá v datovém proudu paměti, která je zabalena <xref:System.Xml.XmlDictionaryReader> a přidávat do zprávy nahrazení.</span><span class="sxs-lookup"><span data-stu-id="725b7-143">If no error occurs, a new message is constructed that copies the properties and headers from the original message and uses the now-validated infoset in the memory stream, which is wrapped by an <xref:System.Xml.XmlDictionaryReader> and added to the replacement message.</span></span>  
  
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
  
 <span data-ttu-id="725b7-144">`InspectionValidationHandler` Metoda je volána ověřování <xref:System.Xml.XmlReader> vždy, když dojde k chybě ověření schématu nebo upozornění.</span><span class="sxs-lookup"><span data-stu-id="725b7-144">The `InspectionValidationHandler` method is called by the validating <xref:System.Xml.XmlReader> whenever a schema validation error or warning occurs.</span></span> <span data-ttu-id="725b7-145">Následující implementaci funguje jenom s chybami a bude ignorovat všechna upozornění.</span><span class="sxs-lookup"><span data-stu-id="725b7-145">The following implementation only works with errors and ignores all warnings.</span></span>  
  
 <span data-ttu-id="725b7-146">Na první úvahy může zdát dát vložit ověřování <xref:System.Xml.XmlReader> do zprávy s inspektoru zprávu a umožňují ověření dochází při zpracování zprávy a bez ukládání do vyrovnávací paměti zprávy.</span><span class="sxs-lookup"><span data-stu-id="725b7-146">On first consideration, it might seem possible to inject a validating <xref:System.Xml.XmlReader> into the message with the message inspector and let the validation happen as the message is processed and without buffering the message.</span></span> <span data-ttu-id="725b7-147">Ale znamená, že tato zpětné volání vyvolá výjimky ověření někde ve službě model infrastruktury nebo z uživatelského kódu jako zjistí neplatné z uzlů XML v důsledku nepředvídatelného chování.</span><span class="sxs-lookup"><span data-stu-id="725b7-147">That, however, means that this callback throws the validation exceptions somewhere into the service model infrastructure or the user code as invalid XML nodes are detected, resulting in unpredictable behavior.</span></span> <span data-ttu-id="725b7-148">Vyrovnávací paměti přístup chrání zcela uživatelský kód z neplatné zprávy.</span><span class="sxs-lookup"><span data-stu-id="725b7-148">The buffering approach shields the user code from invalid messages, entirely.</span></span>  
  
 <span data-ttu-id="725b7-149">Jak bylo uvedeno výše ověřte výjimky vyvolané obslužnou rutinou lišit mezi klientem a službou.</span><span class="sxs-lookup"><span data-stu-id="725b7-149">As previously discussed, the exceptions thrown by the handler differ between the client and the service.</span></span> <span data-ttu-id="725b7-150">Ve službě, výjimky jsou odvozeny z <xref:System.ServiceModel.FaultException>, výjimky na straně klienta jsou pravidelné vlastní výjimky.</span><span class="sxs-lookup"><span data-stu-id="725b7-150">On the service, the exceptions are derived from <xref:System.ServiceModel.FaultException>, on the client the exceptions are regular custom exceptions.</span></span>  
  
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
  
## <a name="behavior"></a><span data-ttu-id="725b7-151">Chování</span><span class="sxs-lookup"><span data-stu-id="725b7-151">Behavior</span></span>  
 <span data-ttu-id="725b7-152">Inspektoři zpráv jsou rozšíření pro modul runtime klienta nebo odeslání za běhu.</span><span class="sxs-lookup"><span data-stu-id="725b7-152">Message inspectors are extensions to the client runtime or the dispatch runtime.</span></span> <span data-ttu-id="725b7-153">Taková rozšíření se konfiguruje pomocí *chování*.</span><span class="sxs-lookup"><span data-stu-id="725b7-153">Such extensions are configured using *behaviors*.</span></span> <span data-ttu-id="725b7-154">Chování je třída, která mění chování modulu service model runtime změnu výchozí konfigurace nebo přidáním přípony (například messageinspectors) k němu.</span><span class="sxs-lookup"><span data-stu-id="725b7-154">A behavior is a class that changes the behavior of the service model runtime by changing the default configuration or adding extensions (such as message inspectors) to it.</span></span>  
  
 <span data-ttu-id="725b7-155">Následující `SchemaValidationBehavior` třídy se používá k přidání inspektoru zprávy této ukázky do klienta nebo odeslání modul runtime chování.</span><span class="sxs-lookup"><span data-stu-id="725b7-155">The following `SchemaValidationBehavior` class is the behavior used to add this sample's message inspector to the client or dispatch runtime.</span></span> <span data-ttu-id="725b7-156">Implementace je spíše základních v obou případech.</span><span class="sxs-lookup"><span data-stu-id="725b7-156">The implementation is rather basic in both cases.</span></span> <span data-ttu-id="725b7-157">V <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> a <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>, nástroj inspector zprávy je vytvořen a přidán do <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> sadu odpovídajících modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="725b7-157">In <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> and <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>, the message inspector is created and added to the <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> collection of the respective runtime.</span></span>  
  
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
>  <span data-ttu-id="725b7-158">Tento konkrétní chování není dvakrát jako atribut, proto nelze přidat deklarativně na typ kontraktu typu služby.</span><span class="sxs-lookup"><span data-stu-id="725b7-158">This particular behavior does not double as an attribute and therefore cannot be added declaratively onto a contract type of a service type.</span></span> <span data-ttu-id="725b7-159">Jde o výchozí rozhodnutí provést, protože kolekce schématu nelze načíst v deklaraci atributu a odkazující na umístění další konfiguraci (například do nastavení aplikace) v tomto atributu znamená vytvoření konfigurace element, který není konzistentní se zbytkem konfiguraci modelu služby.</span><span class="sxs-lookup"><span data-stu-id="725b7-159">This is a by-design decision made because the schema collection cannot be loaded in an attribute declaration and referring to an extra configuration location (for instance to the application settings) in this attribute means creating a configuration element that is not consistent with the rest of the service model configuration.</span></span> <span data-ttu-id="725b7-160">Proto se toto chování lze přidat pouze imperativně prostřednictvím kódu a konfigurace rozšíření modelu služby.</span><span class="sxs-lookup"><span data-stu-id="725b7-160">Therefore, this behavior can only be added imperatively through code and through a service model configuration extension.</span></span>  
  
## <a name="adding-the-message-inspector-through-configuration"></a><span data-ttu-id="725b7-161">Přidání zprávy inspektoru prostřednictvím konfigurace</span><span class="sxs-lookup"><span data-stu-id="725b7-161">Adding the Message Inspector through Configuration</span></span>  
 <span data-ttu-id="725b7-162">Konfigurace vlastního chování pro koncový bod v konfiguračním souboru aplikace, model služby vyžaduje implementátory pro vytvoření konfigurace *element rozšíření* reprezentovaný třídou odvozenou z <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>.</span><span class="sxs-lookup"><span data-stu-id="725b7-162">For configuring a custom behavior on an endpoint in the application configuration file, the service model requires implementers to create a configuration *extension element* represented by a class derived from <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>.</span></span> <span data-ttu-id="725b7-163">Toto rozšíření musí pak přidá do modelu služby konfiguračního oddílu pro rozšíření, jak je ukázáno pro následující rozšíření popsaných v této části.</span><span class="sxs-lookup"><span data-stu-id="725b7-163">This extension must then be added to the service model's configuration section for extensions as shown for the following extension discussed in this section.</span></span>  
  
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
  
 <span data-ttu-id="725b7-164">Rozšíření můžete přidat v aplikaci nebo v konfiguračním souboru ASP.NET, což je nejběžnější možnost, nebo v konfiguračním souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="725b7-164">Extensions can be added in the application or ASP.NET configuration file, which is the most common choice, or in the machine configuration file.</span></span>  
  
 <span data-ttu-id="725b7-165">Při přidání rozšíření do konfigurace oboru, chování lze přidat do konfigurace chování, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="725b7-165">When the extension is added to a configuration scope, the behavior can be added to a behavior configuration as it is shown in the following code.</span></span> <span data-ttu-id="725b7-166">Konfigurace chování jsou opakovaně použitelné prvky, které můžete použít pro více koncových bodů podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="725b7-166">Behavior configurations are reusable elements that can be applied to multiple endpoints as required.</span></span> <span data-ttu-id="725b7-167">Vzhledem k tomu, že konkrétní chování být nakonfigurované zde implementuje <xref:System.ServiceModel.Description.IEndpointBehavior>, je platný jenom v příslušných konfiguračním oddílu v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="725b7-167">Because the particular behavior to be configured here implements <xref:System.ServiceModel.Description.IEndpointBehavior>, it is only valid in the respective configuration section in the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="725b7-168">`<schemaValidator>` Element, který konfiguruje inspektor zpráva tímto modulem stojí `SchemaValidationBehaviorExtensionElement` třídy.</span><span class="sxs-lookup"><span data-stu-id="725b7-168">The `<schemaValidator>` element that configures the message inspector is backed by the `SchemaValidationBehaviorExtensionElement` class.</span></span> <span data-ttu-id="725b7-169">Třída poskytuje dvě logické veřejné vlastnosti s názvem `ValidateRequest` a `ValidateReply`.</span><span class="sxs-lookup"><span data-stu-id="725b7-169">The class exposes two Boolean public properties named `ValidateRequest` and `ValidateReply`.</span></span> <span data-ttu-id="725b7-170">Obě tyto jsou označené <xref:System.Configuration.ConfigurationPropertyAttribute>.</span><span class="sxs-lookup"><span data-stu-id="725b7-170">Both of these are marked with a <xref:System.Configuration.ConfigurationPropertyAttribute>.</span></span> <span data-ttu-id="725b7-171">Tento atribut se považuje za propojení mezi vlastností kódu a atributů XML, které můžete zobrazit na předchozí prvek XML konfigurace.</span><span class="sxs-lookup"><span data-stu-id="725b7-171">This attribute constitutes the link between the code properties and the XML attributes that can be seen on the preceding XML configuration element.</span></span> <span data-ttu-id="725b7-172">Třída také obsahuje vlastnost `Schemas` , který je také označena <xref:System.Configuration.ConfigurationCollectionAttribute> a je typu `SchemaCollection`, což je také součástí této ukázce, ale není uveden v tomto dokumentu pro zkrácení.</span><span class="sxs-lookup"><span data-stu-id="725b7-172">The class also has a property `Schemas` that is additionally marked with the <xref:System.Configuration.ConfigurationCollectionAttribute> and is of the type `SchemaCollection`, which is also part of this sample but omitted from this document for brevity.</span></span> <span data-ttu-id="725b7-173">Tato vlastnost spolu s kolekci a třída prvku kolekce `SchemaConfigElement` zálohuje `<schemas>` element v předchozím fragmentu kódu konfigurace a umožňuje přidání kolekce schémat do sady ověřování.</span><span class="sxs-lookup"><span data-stu-id="725b7-173">This property along with the collection and the collection element class `SchemaConfigElement` backs the `<schemas>` element in the preceding configuration snippet and allows adding a collection of schemas to the validation set.</span></span>  
  
 <span data-ttu-id="725b7-174">Přepsané `CreateBehavior` metoda spustí konfigurační data do objektu chování při modul runtime vyhodnocuje konfigurační data jako sestavení klienta nebo koncový bod.</span><span class="sxs-lookup"><span data-stu-id="725b7-174">The overridden `CreateBehavior` method turns the configuration data into a behavior object when the runtime evaluates the configuration data as it builds a client or an endpoint.</span></span>  
  
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
  
## <a name="adding-message-inspectors-imperatively"></a><span data-ttu-id="725b7-175">Přidání imperativně inspektoři zpráv</span><span class="sxs-lookup"><span data-stu-id="725b7-175">Adding Message Inspectors Imperatively</span></span>  
 <span data-ttu-id="725b7-176">S výjimkou prostřednictvím atributy (které není podporována z důvodu uvedené dříve v této ukázce) a konfigurace, chování lze snadno přidat do klienta a služby modulu runtime pomocí imperativního kódu.</span><span class="sxs-lookup"><span data-stu-id="725b7-176">Except through attributes (which is not supported in this sample for the reason cited previously) and configuration, behaviors can quite easily be added to a client and service runtime using imperative code.</span></span> <span data-ttu-id="725b7-177">V této ukázce se provádí v klientské aplikaci otestovat inspektoru zprávy klienta.</span><span class="sxs-lookup"><span data-stu-id="725b7-177">In this sample, this is done in the client application to test the client message inspector.</span></span> <span data-ttu-id="725b7-178">`GenericClient` Je třída odvozena z <xref:System.ServiceModel.ClientBase%601>, která zveřejní konfigurace koncového bodu do uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="725b7-178">The `GenericClient` class is derived from <xref:System.ServiceModel.ClientBase%601>, which exposes the endpoint configuration to the user code.</span></span> <span data-ttu-id="725b7-179">Předtím, než klient je implicitně otevřen konfigurace koncového bodu můžete změnit, například přidáním chování, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="725b7-179">Before the client is implicitly opened the endpoint configuration can be changed, for instance by adding behaviors as shown in the following code.</span></span> <span data-ttu-id="725b7-180">Přidání chování služby je do značné míry odpovídá techniku klienta je vidět tady a musí být provedena před otevřením hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="725b7-180">Adding the behavior on the service is largely equivalent to the client technique shown here and must be performed before the service host is opened.</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="725b7-181">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="725b7-181">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="725b7-182">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="725b7-182">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="725b7-183">Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="725b7-183">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="725b7-184">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="725b7-184">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="725b7-185">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="725b7-185">The samples may already be installed on your machine.</span></span> <span data-ttu-id="725b7-186">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="725b7-186">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="725b7-187">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="725b7-187">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="725b7-188">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="725b7-188">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageInspectors`  
  
## <a name="see-also"></a><span data-ttu-id="725b7-189">Viz také:</span><span class="sxs-lookup"><span data-stu-id="725b7-189">See also</span></span>
