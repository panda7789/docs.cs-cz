---
title: Inspektoři zpráv
ms.date: 03/30/2017
ms.assetid: 9bd1f305-ad03-4dd7-971f-fa1014b97c9b
ms.openlocfilehash: 05dbee820a002feb1f2a1672220be0c4a397f952
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33508992"
---
# <a name="message-inspectors"></a><span data-ttu-id="b40ef-102">Inspektoři zpráv</span><span class="sxs-lookup"><span data-stu-id="b40ef-102">Message Inspectors</span></span>
<span data-ttu-id="b40ef-103">Tento příklad ukazuje, jak implementovat a nakonfigurovat klienta a služby inspektoři zpráv.</span><span class="sxs-lookup"><span data-stu-id="b40ef-103">This sample demonstrates how to implement and configure client and service message inspectors.</span></span>  
  
 <span data-ttu-id="b40ef-104">Zpráva inspector je rozšíření objekt, který lze použít v modelu služby runtime klienta a odesílání runtime prostřednictvím kódu programu, nebo prostřednictvím konfigurace a který můžete zkontrolovat a změnit zprávy po jejich přijetí nebo před jejich odesláním.</span><span class="sxs-lookup"><span data-stu-id="b40ef-104">A message inspector is an extensibility object that can be used in the service model's client runtime and dispatch runtime programmatically or through configuration and that can inspect and alter messages after they are received or before they are sent.</span></span>  
  
 <span data-ttu-id="b40ef-105">Tato ukázka implementuje základní klienta a služby zpráva ověření mechanismu, který ověří příchozí zprávy oproti sadě konfigurovat dokumentů schématu XML.</span><span class="sxs-lookup"><span data-stu-id="b40ef-105">This sample implements a basic client and service message validation mechanism that validates incoming messages against a set of configurable XML Schema documents.</span></span> <span data-ttu-id="b40ef-106">Všimněte si, že tato ukázka neověřuje zprávy pro každou operaci.</span><span class="sxs-lookup"><span data-stu-id="b40ef-106">Note that this sample does not validate messages for each operation.</span></span> <span data-ttu-id="b40ef-107">To je úmyslné zjednodušení.</span><span class="sxs-lookup"><span data-stu-id="b40ef-107">This is an intentional simplification.</span></span>  
  
## <a name="message-inspector"></a><span data-ttu-id="b40ef-108">Zpráva Inspector</span><span class="sxs-lookup"><span data-stu-id="b40ef-108">Message Inspector</span></span>  
 <span data-ttu-id="b40ef-109">Implementace inspektoři zpráv klienta <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> rozhraní a služby implementace inspektoři zpráv <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b40ef-109">Client message inspectors implement the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> interface and service message inspectors implement the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> interface.</span></span> <span data-ttu-id="b40ef-110">Implementace zkombinovat do jedné třídy k vytvoření inspector zpráva, která se dá použít na obou stranách.</span><span class="sxs-lookup"><span data-stu-id="b40ef-110">The implementations can be combined into a single class to form a message inspector that works for both sides.</span></span> <span data-ttu-id="b40ef-111">Tato ukázka implementuje takové inspector kombinované zprávy.</span><span class="sxs-lookup"><span data-stu-id="b40ef-111">This sample implements such a combined message inspector.</span></span> <span data-ttu-id="b40ef-112">Kontrolor je vytvořený předávání v sadě schémat, kterými se ověří příchozí a odchozí zprávy a umožňuje vývojáři k určení, jestli se ověřují příchozí nebo odchozí zprávy a zda nástroj inspector je v režimu klienta nebo odeslání, který zpracování chyb ovlivňuje, jak je popsáno dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="b40ef-112">The inspector is constructed passing in a set of schemas against which incoming and outgoing messages are validated and allows the developer to specify whether incoming or outgoing messages are validated and whether the inspector is in dispatch or client mode, which affects the error handling as discussed later in this topic.</span></span>  
  
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
  
 <span data-ttu-id="b40ef-113">Všechny zprávy inspector služby (odesílatel) musí implementovat dvě <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> metody <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> a <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.</span><span class="sxs-lookup"><span data-stu-id="b40ef-113">Any service (dispatcher) message inspector must implement the two <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> methods <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> and <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.</span></span>  
  
 <span data-ttu-id="b40ef-114"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> je volána dispečera při obdržel, zpracovává zásobníku kanál a přiřazené k službě zprávu, ale předtím, než je deserializovat a odeslaných do operace.</span><span class="sxs-lookup"><span data-stu-id="b40ef-114"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> is invoked by the dispatcher when a message has been received, processed by the channel stack and assigned to a service, but before it is deserialized and dispatched to an operation.</span></span> <span data-ttu-id="b40ef-115">Pokud příchozí zpráva byla zašifrována, je zpráva již dešifrovat při dosažení inspector zprávy.</span><span class="sxs-lookup"><span data-stu-id="b40ef-115">If the incoming message was encrypted, the message is already decrypted when it reaches the message inspector.</span></span> <span data-ttu-id="b40ef-116">Získá metodu `request` zpráva předán jako referenční parametr, který umožňuje zpráva, která má být prověřovány, s nimi manipulovat nebo nahradit podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="b40ef-116">The method gets the `request` message passed as a reference parameter, which allows the message to be inspected, manipulated or replaced as required.</span></span> <span data-ttu-id="b40ef-117">Návratová hodnota může být jakýkoli objekt a slouží jako objekt korelace stavu, který je předán <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> při službu vrátí odpověď na aktuální zprávu.</span><span class="sxs-lookup"><span data-stu-id="b40ef-117">The return value can be any object and is used as a correlation state object that is passed to <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> when the service returns a reply to the current message.</span></span> <span data-ttu-id="b40ef-118">V této ukázce <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> deleguje kontroly (ověřování) zprávy metodu privátní, místní `ValidateMessageBody` a vrátí objekt žádné korelace stavu.</span><span class="sxs-lookup"><span data-stu-id="b40ef-118">In this sample, <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> delegates the inspection (validation) of the message to the private, local method `ValidateMessageBody` and returns no correlation state object.</span></span> <span data-ttu-id="b40ef-119">Tato metoda zajišťuje, že žádné neplatné zprávy předat do služby.</span><span class="sxs-lookup"><span data-stu-id="b40ef-119">This method ensures that no invalid messages pass into the service.</span></span>  
  
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
  
 <span data-ttu-id="b40ef-120"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29> je volána vždy, když je připravena k odeslání zpět na klienta nebo v případě jednosměrného zprávy, když se po zpracování příchozí zprávy odpovědi.</span><span class="sxs-lookup"><span data-stu-id="b40ef-120"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29> is invoked whenever a reply is ready to be sent back to a client, or in the case of one-way messages, when the incoming message has been processed.</span></span> <span data-ttu-id="b40ef-121">To umožňuje rozšíření počítat se volané symetricky, bez ohledu na to MEP.</span><span class="sxs-lookup"><span data-stu-id="b40ef-121">This allows extensions to count on being called symmetrically, regardless of MEP.</span></span> <span data-ttu-id="b40ef-122">Stejně jako u <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, zpráva se předá jako parametr odkazu a lze prověřovány, změnit nebo nahradit.</span><span class="sxs-lookup"><span data-stu-id="b40ef-122">As with <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, the message is passed as a reference parameter and can be inspected, modified or replaced.</span></span> <span data-ttu-id="b40ef-123">Ověření zprávy, které se provádí v této ukázce je znovu delegovaný jako `ValidMessageBody` metoda, ale ošetření chyb při ověřování se v takovém případě mírně lišit.</span><span class="sxs-lookup"><span data-stu-id="b40ef-123">The validation of the message that is performed in this sample is again delegated to the `ValidMessageBody` method, but the handling of validation errors is slightly different in this case.</span></span>  
  
 <span data-ttu-id="b40ef-124">Pokud dojde k chybě ověření ve službě, `ValidateMessageBody` vyvolá metoda <xref:System.ServiceModel.FaultException>-odvozené výjimky.</span><span class="sxs-lookup"><span data-stu-id="b40ef-124">If a validation error occurs on the service, the `ValidateMessageBody` method throws <xref:System.ServiceModel.FaultException>-derived exceptions.</span></span> <span data-ttu-id="b40ef-125">V <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, tyto výjimky můžou být přepnuté do infrastruktury služby modelu, kde jsou automaticky převede na chyb SOAP a předává do klienta.</span><span class="sxs-lookup"><span data-stu-id="b40ef-125">In <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, these exceptions can be put into the service model infrastructure where they are automatically transformed into SOAP faults and relayed to the client.</span></span> <span data-ttu-id="b40ef-126">V <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>, <xref:System.ServiceModel.FaultException> výjimky nesmí být přepnuté do infrastruktury, protože transformace selhání výjimky vydané služby se vyskytuje před zpráva inspector je volána.</span><span class="sxs-lookup"><span data-stu-id="b40ef-126">In <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>, <xref:System.ServiceModel.FaultException> exceptions must not be put into the infrastructure, because the transformation of fault exceptions thrown by the service occurs before the message inspector is called.</span></span> <span data-ttu-id="b40ef-127">Proto za následující implementaci zachytí známých `ReplyValidationFault` výjimku a nahradí odpovědi zpráv s explicitní chybovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="b40ef-127">Therefore the following implementation catches the known `ReplyValidationFault` exception and replaces the reply message with an explicit fault message.</span></span> <span data-ttu-id="b40ef-128">Tato metoda zajišťuje, že žádné neplatné zprávy jsou vráceny implementace služby.</span><span class="sxs-lookup"><span data-stu-id="b40ef-128">This method ensures that no invalid messages are returned by the service implementation.</span></span>  
  
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
  
 <span data-ttu-id="b40ef-129">Inspector zpráv klienta je velmi podobné.</span><span class="sxs-lookup"><span data-stu-id="b40ef-129">The client message inspector is very similar.</span></span> <span data-ttu-id="b40ef-130">Tyto dvě metody, které musí být implementován z <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> jsou <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> a <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>.</span><span class="sxs-lookup"><span data-stu-id="b40ef-130">The two methods that must be implemented from <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> are <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> and <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>.</span></span>  
  
 <span data-ttu-id="b40ef-131"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> je voláno, když má byla daná zpráva vytvořena, klientská aplikace nebo operaci formátování.</span><span class="sxs-lookup"><span data-stu-id="b40ef-131"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> is invoked when the message has been composed either by the client application or by the operation formatter.</span></span> <span data-ttu-id="b40ef-132">Jako s inspektoři dispečera zpráv, můžete zprávu právě prověřovány nebo zcela nahradit.</span><span class="sxs-lookup"><span data-stu-id="b40ef-132">As with the dispatcher message inspectors, the message can just be inspected or entirely replaced.</span></span> <span data-ttu-id="b40ef-133">V této ukázce kontrolor deleguje do stejné místní `ValidateMessageBody` Pomocná metoda, která se také používá pro inspektoři odesílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="b40ef-133">In this sample, the inspector delegates to the same local `ValidateMessageBody` helper method that is also used for the dispatch message inspectors.</span></span>  
  
 <span data-ttu-id="b40ef-134">Chování rozdíl mezi klientem a službou ověření (jako je zadaný v konstruktoru) je, že ověření klienta vyvolá místní výjimky, které jsou vloženy do uživatelského kódu, protože k nim dojde místně a ne z důvodu selhání služby.</span><span class="sxs-lookup"><span data-stu-id="b40ef-134">The behavioral difference between the client and service validation (as specified in the constructor) is that the client validation throws local exceptions that are put into the user code because they occur locally and not because of a service failure.</span></span> <span data-ttu-id="b40ef-135">Pravidlo je obecně platí, že služba dispečera inspektoři throw chyb a že kontroly klienta výjimku výjimky.</span><span class="sxs-lookup"><span data-stu-id="b40ef-135">Generally, the rule is that service dispatcher inspectors throw faults and that client inspectors throw exceptions.</span></span>  
  
 <span data-ttu-id="b40ef-136">To <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementace zajistí, že žádné neplatné zprávy se odešle do služby.</span><span class="sxs-lookup"><span data-stu-id="b40ef-136">This <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementation ensures that no invalid messages are sent to the service.</span></span>  
  
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
  
 <span data-ttu-id="b40ef-137">`AfterReceiveReply` Implementace zajistí, že žádné neplatné zprávy přijal od služby jsou přes předávací službu klienta uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="b40ef-137">The `AfterReceiveReply` implementation ensures that no invalid messages received from the service are relayed to the client user code.</span></span>  
  
```  
void IClientMessageInspector.AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        ValidateMessageBody(ref reply, false);  
    }  
}  
```  
  
 <span data-ttu-id="b40ef-138">Jádrem této konkrétní zprávu inspector je `ValidateMessageBody` metoda.</span><span class="sxs-lookup"><span data-stu-id="b40ef-138">The heart of this particular message inspector is the `ValidateMessageBody` method.</span></span> <span data-ttu-id="b40ef-139">Ke své práci, zabalí ověřování <xref:System.Xml.XmlReader> kolem textu obsahu dílčí stromu předaný zprávy.</span><span class="sxs-lookup"><span data-stu-id="b40ef-139">To perform its work, it wraps a validating <xref:System.Xml.XmlReader> around the body content sub-tree of the passed message.</span></span> <span data-ttu-id="b40ef-140">Čtečka je naplněna sadu schémat, které obsahuje nástroj inspector zpráv a zpětné volání pro ověření je nastaven s delegátem, která odkazuje na `InspectionValidationHandler` definovaný společně se tato metoda.</span><span class="sxs-lookup"><span data-stu-id="b40ef-140">The reader is populated with the set of schemas that the message inspector holds and the validation callback is set to a delegate referring to the `InspectionValidationHandler` that is defined alongside this method.</span></span> <span data-ttu-id="b40ef-141">K provedení ověření, zpráva se pak číst a zařazených do paměti, zálohovaná datový proud <xref:System.Xml.XmlDictionaryWriter>.</span><span class="sxs-lookup"><span data-stu-id="b40ef-141">To perform the validation, the message is then read and spooled into a memory stream-backed <xref:System.Xml.XmlDictionaryWriter>.</span></span> <span data-ttu-id="b40ef-142">Pokud v procesu dojde k ověření chyby nebo upozornění, je vyvolána metoda zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="b40ef-142">If a validation error or warning occurs in the process, the callback method is invoked.</span></span>  
  
 <span data-ttu-id="b40ef-143">Pokud nedojde k žádné chybě novou zprávu vytvořená, zkopíruje vlastnosti a hlavičky z původní zprávy a informační sadu ověřit nyní používá v datovém proudu paměti, která je zabalené službou <xref:System.Xml.XmlDictionaryReader> a přidávat do zprávy nahrazení.</span><span class="sxs-lookup"><span data-stu-id="b40ef-143">If no error occurs, a new message is constructed that copies the properties and headers from the original message and uses the now-validated infoset in the memory stream, which is wrapped by an <xref:System.Xml.XmlDictionaryReader> and added to the replacement message.</span></span>  
  
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
  
 <span data-ttu-id="b40ef-144">`InspectionValidationHandler` Metoda je volána ověřování <xref:System.Xml.XmlReader> vždy, když dojde k chybě ověření schématu nebo upozornění.</span><span class="sxs-lookup"><span data-stu-id="b40ef-144">The `InspectionValidationHandler` method is called by the validating <xref:System.Xml.XmlReader> whenever a schema validation error or warning occurs.</span></span> <span data-ttu-id="b40ef-145">Za následující implementaci lze použít pouze se chyby a varování.</span><span class="sxs-lookup"><span data-stu-id="b40ef-145">The following implementation only works with errors and ignores all warnings.</span></span>  
  
 <span data-ttu-id="b40ef-146">Na první úvahy, mohou vám možné vložit, ověřování <xref:System.Xml.XmlReader> do zprávy s zpráva inspector a umožňují ověření dojít při zpracování zprávy se a bez ukládání do vyrovnávací paměti zprávy.</span><span class="sxs-lookup"><span data-stu-id="b40ef-146">On first consideration, it might seem possible to inject a validating <xref:System.Xml.XmlReader> into the message with the message inspector and let the validation happen as the message is processed and without buffering the message.</span></span> <span data-ttu-id="b40ef-147">Že však znamená, že tento zpětného volání vyvolá výjimek ověření někde ve službě model infrastrukturu nebo uživatelský kód jako neplatný z uzlů XML detekovány, což vede k nepředvídatelné chování.</span><span class="sxs-lookup"><span data-stu-id="b40ef-147">That, however, means that this callback throws the validation exceptions somewhere into the service model infrastructure or the user code as invalid XML nodes are detected, resulting in unpredictable behavior.</span></span> <span data-ttu-id="b40ef-148">Vyrovnávací paměti přístup chrání zcela uživatelského kódu z neplatné zprávy.</span><span class="sxs-lookup"><span data-stu-id="b40ef-148">The buffering approach shields the user code from invalid messages, entirely.</span></span>  
  
 <span data-ttu-id="b40ef-149">Jak bylo popsáno dříve výjimky vyvolané obslužná rutina se liší mezi klientem a služby.</span><span class="sxs-lookup"><span data-stu-id="b40ef-149">As previously discussed, the exceptions thrown by the handler differ between the client and the service.</span></span> <span data-ttu-id="b40ef-150">Ve službě, výjimky jsou odvozeny od <xref:System.ServiceModel.FaultException>, na straně klienta jsou výjimky regulární vlastní výjimky.</span><span class="sxs-lookup"><span data-stu-id="b40ef-150">On the service, the exceptions are derived from <xref:System.ServiceModel.FaultException>, on the client the exceptions are regular custom exceptions.</span></span>  
  
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
  
## <a name="behavior"></a><span data-ttu-id="b40ef-151">Chování</span><span class="sxs-lookup"><span data-stu-id="b40ef-151">Behavior</span></span>  
 <span data-ttu-id="b40ef-152">Inspektoři zpráv jsou rozšíření modulu runtime klienta nebo odeslání runtime.</span><span class="sxs-lookup"><span data-stu-id="b40ef-152">Message inspectors are extensions to the client runtime or the dispatch runtime.</span></span> <span data-ttu-id="b40ef-153">Taková rozšíření jsou konfigurováni pomocí *chování*.</span><span class="sxs-lookup"><span data-stu-id="b40ef-153">Such extensions are configured using *behaviors*.</span></span> <span data-ttu-id="b40ef-154">Chování je třída, která mění chování modulu runtime service model změnu výchozí konfigurace nebo přidání přípony (například inspektoři zpráv) k němu.</span><span class="sxs-lookup"><span data-stu-id="b40ef-154">A behavior is a class that changes the behavior of the service model runtime by changing the default configuration or adding extensions (such as message inspectors) to it.</span></span>  
  
 <span data-ttu-id="b40ef-155">Následující `SchemaValidationBehavior` třída je použít k přidání této ukázce zpráva inspector do klienta nebo odeslání runtime chování.</span><span class="sxs-lookup"><span data-stu-id="b40ef-155">The following `SchemaValidationBehavior` class is the behavior used to add this sample's message inspector to the client or dispatch runtime.</span></span> <span data-ttu-id="b40ef-156">Implementace je spíš základní v obou případech.</span><span class="sxs-lookup"><span data-stu-id="b40ef-156">The implementation is rather basic in both cases.</span></span> <span data-ttu-id="b40ef-157">V <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> a <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>, nástroj inspector zprávy je vytvořen a přidán do <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> kolekce příslušných modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="b40ef-157">In <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> and <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>, the message inspector is created and added to the <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> collection of the respective runtime.</span></span>  
  
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
>  <span data-ttu-id="b40ef-158">Toto konkrétní chování není dvakrát jako atribut a nelze ji proto přidat deklarativně na typ smlouvy typu služby.</span><span class="sxs-lookup"><span data-stu-id="b40ef-158">This particular behavior does not double as an attribute and therefore cannot be added declaratively onto a contract type of a service type.</span></span> <span data-ttu-id="b40ef-159">Jedná se o záměrných rozhodnutí provést, protože kolekce schémat nelze načíst v deklarace atributu a odkazy na další konfigurace umístění (například na nastavení aplikací) v tomto atributu znamená vytvoření konfigurační prvek, který není konzistentní se zbytkem konfiguraci modelu služby.</span><span class="sxs-lookup"><span data-stu-id="b40ef-159">This is a by-design decision made because the schema collection cannot be loaded in an attribute declaration and referring to an extra configuration location (for instance to the application settings) in this attribute means creating a configuration element that is not consistent with the rest of the service model configuration.</span></span> <span data-ttu-id="b40ef-160">Proto toto chování lze přidat pouze imperativní prostřednictvím kódu a prostřednictvím rozšíření pro konfiguraci modelu služby.</span><span class="sxs-lookup"><span data-stu-id="b40ef-160">Therefore, this behavior can only be added imperatively through code and through a service model configuration extension.</span></span>  
  
## <a name="adding-the-message-inspector-through-configuration"></a><span data-ttu-id="b40ef-161">Přidání Inspector zprávy prostřednictvím konfigurace</span><span class="sxs-lookup"><span data-stu-id="b40ef-161">Adding the Message Inspector through Configuration</span></span>  
 <span data-ttu-id="b40ef-162">Konfigurace vlastní chování pro koncový bod v konfiguračním souboru aplikace, modelu služby vyžaduje implementátory pro vytvoření konfigurace *elementu rozšíření* reprezentována třídy odvozené od <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>.</span><span class="sxs-lookup"><span data-stu-id="b40ef-162">For configuring a custom behavior on an endpoint in the application configuration file, the service model requires implementers to create a configuration *extension element* represented by a class derived from <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>.</span></span> <span data-ttu-id="b40ef-163">Toto rozšíření musí pak přidá do modelu služby konfigurační oddíl pro rozšíření, jak je uvedeno pro následující rozšíření popsaných v této části.</span><span class="sxs-lookup"><span data-stu-id="b40ef-163">This extension must then be added to the service model's configuration section for extensions as shown for the following extension discussed in this section.</span></span>  
  
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
  
 <span data-ttu-id="b40ef-164">Rozšíření mohou být přidány, v aplikaci nebo konfigurační soubor technologie ASP.NET, což je nejběžnější volbou, nebo v konfiguračním souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="b40ef-164">Extensions can be added in the application or ASP.NET configuration file, which is the most common choice, or in the machine configuration file.</span></span>  
  
 <span data-ttu-id="b40ef-165">Když rozšíření se přidá do konfigurace oboru, chování lze přidat do konfigurace chování znázorněné v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="b40ef-165">When the extension is added to a configuration scope, the behavior can be added to a behavior configuration as it is shown in the following code.</span></span> <span data-ttu-id="b40ef-166">Konfigurace chování jsou opakovaně použitelné prvky, které lze použít pro několik koncových bodů podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="b40ef-166">Behavior configurations are reusable elements that can be applied to multiple endpoints as required.</span></span> <span data-ttu-id="b40ef-167">Protože konkrétní chování být nakonfigurované zde implementuje <xref:System.ServiceModel.Description.IEndpointBehavior>, je platný pouze v příslušných konfiguračního oddílu v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="b40ef-167">Because the particular behavior to be configured here implements <xref:System.ServiceModel.Description.IEndpointBehavior>, it is only valid in the respective configuration section in the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="b40ef-168">`<schemaValidator>` Element, který nakonfiguruje zpráva inspector je zálohovaný díky `SchemaValidationBehaviorExtensionElement` třídy.</span><span class="sxs-lookup"><span data-stu-id="b40ef-168">The `<schemaValidator>` element that configures the message inspector is backed by the `SchemaValidationBehaviorExtensionElement` class.</span></span> <span data-ttu-id="b40ef-169">Třída zpřístupní dvě Boolean veřejné vlastnosti s názvem `ValidateRequest` a `ValidateReply`.</span><span class="sxs-lookup"><span data-stu-id="b40ef-169">The class exposes two Boolean public properties named `ValidateRequest` and `ValidateReply`.</span></span> <span data-ttu-id="b40ef-170">Obě tyto jsou označené <xref:System.Configuration.ConfigurationPropertyAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b40ef-170">Both of these are marked with a <xref:System.Configuration.ConfigurationPropertyAttribute>.</span></span> <span data-ttu-id="b40ef-171">Tento atribut se považuje za propojení mezi vlastnosti kódu a atributy XML, které můžete zobrazit na předchozí elementu XML konfigurace.</span><span class="sxs-lookup"><span data-stu-id="b40ef-171">This attribute constitutes the link between the code properties and the XML attributes that can be seen on the preceding XML configuration element.</span></span> <span data-ttu-id="b40ef-172">Třída také obsahuje vlastnost `Schemas` , kromě označena <xref:System.Configuration.ConfigurationCollectionAttribute> a je typu `SchemaCollection`, což je také součástí této ukázky ale vynechání z tohoto dokumentu jako stručný výtah.</span><span class="sxs-lookup"><span data-stu-id="b40ef-172">The class also has a property `Schemas` that is additionally marked with the <xref:System.Configuration.ConfigurationCollectionAttribute> and is of the type `SchemaCollection`, which is also part of this sample but omitted from this document for brevity.</span></span> <span data-ttu-id="b40ef-173">Tato vlastnost spolu s kolekce a třída prvku kolekce `SchemaConfigElement` zálohuje `<schemas>` element v předchozím fragmentu kódu konfigurace a umožňuje přidání kolekci schémat sady ověření.</span><span class="sxs-lookup"><span data-stu-id="b40ef-173">This property along with the collection and the collection element class `SchemaConfigElement` backs the `<schemas>` element in the preceding configuration snippet and allows adding a collection of schemas to the validation set.</span></span>  
  
 <span data-ttu-id="b40ef-174">Přepsané `CreateBehavior` metoda změní konfigurační data do objektu chování, když modul runtime vyhodnocuje konfigurační data, protože sestavuje klienta nebo koncový bod.</span><span class="sxs-lookup"><span data-stu-id="b40ef-174">The overridden `CreateBehavior` method turns the configuration data into a behavior object when the runtime evaluates the configuration data as it builds a client or an endpoint.</span></span>  
  
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
  
## <a name="adding-message-inspectors-imperatively"></a><span data-ttu-id="b40ef-175">Imperativní přidání inspektoři zpráv</span><span class="sxs-lookup"><span data-stu-id="b40ef-175">Adding Message Inspectors Imperatively</span></span>  
 <span data-ttu-id="b40ef-176">S výjimkou prostřednictvím atributy (které není podporováno v této ukázce z důvodu citovalo dříve) a konfigurace chování lze velmi snadno přidat do klienta a služby modulu runtime použijte imperativní kódu.</span><span class="sxs-lookup"><span data-stu-id="b40ef-176">Except through attributes (which is not supported in this sample for the reason cited previously) and configuration, behaviors can quite easily be added to a client and service runtime using imperative code.</span></span> <span data-ttu-id="b40ef-177">V této ukázce se provádí v aplikaci klienta k testování inspector zpráv klienta.</span><span class="sxs-lookup"><span data-stu-id="b40ef-177">In this sample, this is done in the client application to test the client message inspector.</span></span> <span data-ttu-id="b40ef-178">`GenericClient` Je třída odvozená z <xref:System.ServiceModel.ClientBase%601>, který zpřístupňuje konfigurace koncového bodu do uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="b40ef-178">The `GenericClient` class is derived from <xref:System.ServiceModel.ClientBase%601>, which exposes the endpoint configuration to the user code.</span></span> <span data-ttu-id="b40ef-179">Klient je implicitně otevřít konfiguraci koncového bodu lze změnit, například přidáním chování, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="b40ef-179">Before the client is implicitly opened the endpoint configuration can be changed, for instance by adding behaviors as shown in the following code.</span></span> <span data-ttu-id="b40ef-180">Přidání chování služby je z velké části ekvivalentní technika klienta tady uvedené a musí být provedeny před otevření hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="b40ef-180">Adding the behavior on the service is largely equivalent to the client technique shown here and must be performed before the service host is opened.</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b40ef-181">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="b40ef-181">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b40ef-182">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b40ef-182">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="b40ef-183">Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b40ef-183">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="b40ef-184">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b40ef-184">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b40ef-185">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="b40ef-185">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b40ef-186">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="b40ef-186">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b40ef-187">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="b40ef-187">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b40ef-188">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="b40ef-188">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageInspectors`  
  
## <a name="see-also"></a><span data-ttu-id="b40ef-189">Viz také</span><span class="sxs-lookup"><span data-stu-id="b40ef-189">See Also</span></span>
