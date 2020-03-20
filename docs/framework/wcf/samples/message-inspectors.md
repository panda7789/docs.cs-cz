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
# <a name="message-inspectors"></a><span data-ttu-id="2d462-102">Inspektoři zpráv</span><span class="sxs-lookup"><span data-stu-id="2d462-102">Message Inspectors</span></span>
<span data-ttu-id="2d462-103">Tato ukázka ukazuje, jak implementovat a konfigurovat inspektory zpráv klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="2d462-103">This sample demonstrates how to implement and configure client and service message inspectors.</span></span>  
  
 <span data-ttu-id="2d462-104">Inspektor zprávy je objekt rozšiřitelnosti, který lze použít v době runtime klienta a odeslání runtime klienta a odeslání runmaticky nebo prostřednictvím konfigurace a který může kontrolovat a měnit zprávy po jejich přijetí nebo před jejich odesláním.</span><span class="sxs-lookup"><span data-stu-id="2d462-104">A message inspector is an extensibility object that can be used in the service model's client runtime and dispatch runtime programmatically or through configuration and that can inspect and alter messages after they are received or before they are sent.</span></span>  
  
 <span data-ttu-id="2d462-105">Tato ukázka implementuje základní mechanismus ověřování zpráv klienta a služby, který ověřuje příchozí zprávy proti sadě konfigurovatelných dokumentů schématu XML.</span><span class="sxs-lookup"><span data-stu-id="2d462-105">This sample implements a basic client and service message validation mechanism that validates incoming messages against a set of configurable XML Schema documents.</span></span> <span data-ttu-id="2d462-106">Všimněte si, že tato ukázka neověřuje zprávy pro každou operaci.</span><span class="sxs-lookup"><span data-stu-id="2d462-106">Note that this sample does not validate messages for each operation.</span></span> <span data-ttu-id="2d462-107">Jedná se o záměrné zjednodušení.</span><span class="sxs-lookup"><span data-stu-id="2d462-107">This is an intentional simplification.</span></span>  
  
## <a name="message-inspector"></a><span data-ttu-id="2d462-108">Inspektor zprávy</span><span class="sxs-lookup"><span data-stu-id="2d462-108">Message Inspector</span></span>  
 <span data-ttu-id="2d462-109">Inspektoři zpráv klienta implementovat <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> rozhraní a <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> služby zprávy inspektoři implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2d462-109">Client message inspectors implement the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> interface and service message inspectors implement the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> interface.</span></span> <span data-ttu-id="2d462-110">Implementace lze kombinovat do jedné třídy a vytvořit inspektor zpráv, který pracuje pro obě strany.</span><span class="sxs-lookup"><span data-stu-id="2d462-110">The implementations can be combined into a single class to form a message inspector that works for both sides.</span></span> <span data-ttu-id="2d462-111">Tento příklad implementuje takové kombinované zprávy inspektor.</span><span class="sxs-lookup"><span data-stu-id="2d462-111">This sample implements such a combined message inspector.</span></span> <span data-ttu-id="2d462-112">Inspektor je vytvořen předávání v sadě schémat, proti kterým jsou ověřeny příchozí a odchozí zprávy a umožňuje vývojáři určit, zda jsou ověřeny příchozí nebo odchozí zprávy a zda je inspektor v režimu odeslání nebo klienta, který ovlivňuje zpracování chyb, jak je popsáno dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="2d462-112">The inspector is constructed passing in a set of schemas against which incoming and outgoing messages are validated and allows the developer to specify whether incoming or outgoing messages are validated and whether the inspector is in dispatch or client mode, which affects the error handling as discussed later in this topic.</span></span>  
  
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
  
 <span data-ttu-id="2d462-113">Každý inspektor zpráv služby (dispečera) musí implementovat dvě <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> metody <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> a <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.</span><span class="sxs-lookup"><span data-stu-id="2d462-113">Any service (dispatcher) message inspector must implement the two <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> methods <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> and <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.</span></span>  
  
 <span data-ttu-id="2d462-114"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>je vyvolána dispečerem, když byla přijata zpráva, zpracována zásobníkem kanálu a přiřazena ke službě, ale před tím, než je deserializována a odeslána do operace.</span><span class="sxs-lookup"><span data-stu-id="2d462-114"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> is invoked by the dispatcher when a message has been received, processed by the channel stack and assigned to a service, but before it is deserialized and dispatched to an operation.</span></span> <span data-ttu-id="2d462-115">Pokud byla příchozí zpráva zašifrována, je již dešifrována, jakmile se dostane do inspektoru zprávy.</span><span class="sxs-lookup"><span data-stu-id="2d462-115">If the incoming message was encrypted, the message is already decrypted when it reaches the message inspector.</span></span> <span data-ttu-id="2d462-116">Metoda získá `request` zprávu předánjako referenční parametr, který umožňuje zprávu, která má být kontrolována, manipulováno nebo nahrazena podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="2d462-116">The method gets the `request` message passed as a reference parameter, which allows the message to be inspected, manipulated or replaced as required.</span></span> <span data-ttu-id="2d462-117">Vrácená hodnota může být libovolný objekt a slouží jako <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> objekt stavu korelace, který je předán, když služba vrátí odpověď na aktuální zprávu.</span><span class="sxs-lookup"><span data-stu-id="2d462-117">The return value can be any object and is used as a correlation state object that is passed to <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> when the service returns a reply to the current message.</span></span> <span data-ttu-id="2d462-118">V této <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> ukázce deleguje kontrolu (ověření) `ValidateMessageBody` zprávy na soukromé, místní metody a vrátí žádný objekt stavu korelace.</span><span class="sxs-lookup"><span data-stu-id="2d462-118">In this sample, <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> delegates the inspection (validation) of the message to the private, local method `ValidateMessageBody` and returns no correlation state object.</span></span> <span data-ttu-id="2d462-119">Tato metoda zajišťuje, že žádné neplatné zprávy předat do služby.</span><span class="sxs-lookup"><span data-stu-id="2d462-119">This method ensures that no invalid messages pass into the service.</span></span>  
  
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
  
 <span data-ttu-id="2d462-120"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>je vyvolána vždy, když je odpověď připravena k odeslání zpět klientovi nebo v případě jednosměrných zpráv při zpracování příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="2d462-120"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29> is invoked whenever a reply is ready to be sent back to a client, or in the case of one-way messages, when the incoming message has been processed.</span></span> <span data-ttu-id="2d462-121">To umožňuje rozšíření počítat s tím, že budou volána symetricky, bez ohledu na europoslance.</span><span class="sxs-lookup"><span data-stu-id="2d462-121">This allows extensions to count on being called symmetrically, regardless of MEP.</span></span> <span data-ttu-id="2d462-122">Stejně <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>jako v případě , zpráva je předána jako referenční parametr a může být kontrolována, upravena nebo nahrazena.</span><span class="sxs-lookup"><span data-stu-id="2d462-122">As with <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, the message is passed as a reference parameter and can be inspected, modified or replaced.</span></span> <span data-ttu-id="2d462-123">Ověření zprávy, která je provedena v této ukázce je opět delegována na metodu, `ValidMessageBody` ale zpracování chyb ověření se mírně liší v tomto případě.</span><span class="sxs-lookup"><span data-stu-id="2d462-123">The validation of the message that is performed in this sample is again delegated to the `ValidMessageBody` method, but the handling of validation errors is slightly different in this case.</span></span>  
  
 <span data-ttu-id="2d462-124">Pokud dojde k chybě ověření ve `ValidateMessageBody` službě, <xref:System.ServiceModel.FaultException>metoda vyvolá odvozené výjimky.</span><span class="sxs-lookup"><span data-stu-id="2d462-124">If a validation error occurs on the service, the `ValidateMessageBody` method throws <xref:System.ServiceModel.FaultException>-derived exceptions.</span></span> <span data-ttu-id="2d462-125">V <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>oblasti lze tyto výjimky vložit do infrastruktury modelu služby, kde jsou automaticky transformovány na chyby SOAP a předány klientovi.</span><span class="sxs-lookup"><span data-stu-id="2d462-125">In <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, these exceptions can be put into the service model infrastructure where they are automatically transformed into SOAP faults and relayed to the client.</span></span> <span data-ttu-id="2d462-126">V <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> <xref:System.ServiceModel.FaultException> , výjimky nesmí být vloženy do infrastruktury, protože transformace výjimky chyby vyvolána službou dochází před upozornění mše.</span><span class="sxs-lookup"><span data-stu-id="2d462-126">In <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>, <xref:System.ServiceModel.FaultException> exceptions must not be put into the infrastructure, because the transformation of fault exceptions thrown by the service occurs before the message inspector is called.</span></span> <span data-ttu-id="2d462-127">Proto následující implementace zachytí známou `ReplyValidationFault` výjimku a nahradí zprávu odpovědi explicitní chybovou zprávou.</span><span class="sxs-lookup"><span data-stu-id="2d462-127">Therefore the following implementation catches the known `ReplyValidationFault` exception and replaces the reply message with an explicit fault message.</span></span> <span data-ttu-id="2d462-128">Tato metoda zajišťuje, že implementace služby vrací žádné neplatné zprávy.</span><span class="sxs-lookup"><span data-stu-id="2d462-128">This method ensures that no invalid messages are returned by the service implementation.</span></span>  
  
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
  
 <span data-ttu-id="2d462-129">Inspektor zpráv klienta je velmi podobný.</span><span class="sxs-lookup"><span data-stu-id="2d462-129">The client message inspector is very similar.</span></span> <span data-ttu-id="2d462-130">Dvě metody, které musí <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> být <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>implementovány z jsou a .</span><span class="sxs-lookup"><span data-stu-id="2d462-130">The two methods that must be implemented from <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> are <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> and <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>.</span></span>  
  
 <span data-ttu-id="2d462-131"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>je vyvolána, pokud byla zpráva složena klientskou aplikací nebo formátovacím formátovacím formátem operace.</span><span class="sxs-lookup"><span data-stu-id="2d462-131"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> is invoked when the message has been composed either by the client application or by the operation formatter.</span></span> <span data-ttu-id="2d462-132">Stejně jako u dispečerů může být zpráva pouze zkontrolována nebo zcela nahrazena.</span><span class="sxs-lookup"><span data-stu-id="2d462-132">As with the dispatcher message inspectors, the message can just be inspected or entirely replaced.</span></span> <span data-ttu-id="2d462-133">V této ukázce inspektor `ValidateMessageBody` deleguje stejnou místní pomocnou metodu, která se používá také pro inspektory odesílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="2d462-133">In this sample, the inspector delegates to the same local `ValidateMessageBody` helper method that is also used for the dispatch message inspectors.</span></span>  
  
 <span data-ttu-id="2d462-134">Behaviorální rozdíl mezi ověřením klienta a služby (jak je uvedeno v konstruktoru) je, že ověření klienta vyvolá místní výjimky, které jsou vloženy do uživatelského kódu, protože k nim dochází místně a ne z důvodu selhání služby.</span><span class="sxs-lookup"><span data-stu-id="2d462-134">The behavioral difference between the client and service validation (as specified in the constructor) is that the client validation throws local exceptions that are put into the user code because they occur locally and not because of a service failure.</span></span> <span data-ttu-id="2d462-135">Obecně platí pravidlo je, že inspektoři dispečera služby vyvolat chyby a že inspektoři klienta vyvolat výjimky.</span><span class="sxs-lookup"><span data-stu-id="2d462-135">Generally, the rule is that service dispatcher inspectors throw faults and that client inspectors throw exceptions.</span></span>  
  
 <span data-ttu-id="2d462-136">Tato <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementace zajišťuje, že do služby nejsou odesílány žádné neplatné zprávy.</span><span class="sxs-lookup"><span data-stu-id="2d462-136">This <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementation ensures that no invalid messages are sent to the service.</span></span>  
  
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
  
 <span data-ttu-id="2d462-137">Implementace `AfterReceiveReply` zajišťuje, že žádné neplatné zprávy přijaté ze služby jsou přenášeny do kódu uživatele klienta.</span><span class="sxs-lookup"><span data-stu-id="2d462-137">The `AfterReceiveReply` implementation ensures that no invalid messages received from the service are relayed to the client user code.</span></span>  
  
```csharp  
void IClientMessageInspector.AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        ValidateMessageBody(ref reply, false);  
    }  
}  
```  
  
 <span data-ttu-id="2d462-138">Srdcem tohoto konkrétního inspektora `ValidateMessageBody` zprávy je metoda.</span><span class="sxs-lookup"><span data-stu-id="2d462-138">The heart of this particular message inspector is the `ValidateMessageBody` method.</span></span> <span data-ttu-id="2d462-139">Chcete-li provést svou práci, <xref:System.Xml.XmlReader> obtéká ověřování kolem podstromu obsahu těla předané zprávy.</span><span class="sxs-lookup"><span data-stu-id="2d462-139">To perform its work, it wraps a validating <xref:System.Xml.XmlReader> around the body content sub-tree of the passed message.</span></span> <span data-ttu-id="2d462-140">Čtenář je naplněn sadou schémat, která inspektor zprávy obsahuje a zpětné volání ověření je nastaveno `InspectionValidationHandler` na delegáta, který odkazuje na který je definován vedle této metody.</span><span class="sxs-lookup"><span data-stu-id="2d462-140">The reader is populated with the set of schemas that the message inspector holds and the validation callback is set to a delegate referring to the `InspectionValidationHandler` that is defined alongside this method.</span></span> <span data-ttu-id="2d462-141">Chcete-li provést ověření, zpráva je pak číst a zařazování do paměti zpětný <xref:System.Xml.XmlDictionaryWriter>proud zpět .</span><span class="sxs-lookup"><span data-stu-id="2d462-141">To perform the validation, the message is then read and spooled into a memory stream-backed <xref:System.Xml.XmlDictionaryWriter>.</span></span> <span data-ttu-id="2d462-142">Pokud dojde k chybě ověření nebo upozornění v procesu, je vyvolána metoda zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="2d462-142">If a validation error or warning occurs in the process, the callback method is invoked.</span></span>  
  
 <span data-ttu-id="2d462-143">Pokud nedojde k žádné chybě, je vytvořena nová zpráva, která zkopíruje vlastnosti a záhlaví z původní zprávy a používá nyní <xref:System.Xml.XmlDictionaryReader> ověřenou informační sadu v paměťovém proudu, která je zabalena a přidána do náhradní zprávy.</span><span class="sxs-lookup"><span data-stu-id="2d462-143">If no error occurs, a new message is constructed that copies the properties and headers from the original message and uses the now-validated infoset in the memory stream, which is wrapped by an <xref:System.Xml.XmlDictionaryReader> and added to the replacement message.</span></span>  
  
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
  
 <span data-ttu-id="2d462-144">Metoda `InspectionValidationHandler` je volána ověřování <xref:System.Xml.XmlReader> vždy, když dojde k chybě ověření schématu nebo upozornění.</span><span class="sxs-lookup"><span data-stu-id="2d462-144">The `InspectionValidationHandler` method is called by the validating <xref:System.Xml.XmlReader> whenever a schema validation error or warning occurs.</span></span> <span data-ttu-id="2d462-145">Následující implementace funguje pouze s chybami a ignoruje všechna upozornění.</span><span class="sxs-lookup"><span data-stu-id="2d462-145">The following implementation only works with errors and ignores all warnings.</span></span>  
  
 <span data-ttu-id="2d462-146">Na první úvahu se může zdát možné <xref:System.Xml.XmlReader> vložit ověření do zprávy s inspektorem zprávy a nechat ověření dojít jako zpráva je zpracována a bez ukládání do vyrovnávací paměti zprávy.</span><span class="sxs-lookup"><span data-stu-id="2d462-146">On first consideration, it might seem possible to inject a validating <xref:System.Xml.XmlReader> into the message with the message inspector and let the validation happen as the message is processed and without buffering the message.</span></span> <span data-ttu-id="2d462-147">To však znamená, že toto zpětné volání vyvolá výjimky ověření někde do infrastruktury modelu služby nebo uživatelského kódu jako neplatné uzly XML jsou zjištěny, výsledkem je nepředvídatelné chování.</span><span class="sxs-lookup"><span data-stu-id="2d462-147">That, however, means that this callback throws the validation exceptions somewhere into the service model infrastructure or the user code as invalid XML nodes are detected, resulting in unpredictable behavior.</span></span> <span data-ttu-id="2d462-148">Do vyrovnávací paměti přístup chrání kód uživatele z neplatných zpráv, úplně.</span><span class="sxs-lookup"><span data-stu-id="2d462-148">The buffering approach shields the user code from invalid messages, entirely.</span></span>  
  
 <span data-ttu-id="2d462-149">Jak již bylo popsáno, výjimky vyzdvižené obslužnou rutinou se liší mezi klientem a službou.</span><span class="sxs-lookup"><span data-stu-id="2d462-149">As previously discussed, the exceptions thrown by the handler differ between the client and the service.</span></span> <span data-ttu-id="2d462-150">Ve službě jsou výjimky odvozeny <xref:System.ServiceModel.FaultException>od , na straně klienta výjimky jsou pravidelné vlastní výjimky.</span><span class="sxs-lookup"><span data-stu-id="2d462-150">On the service, the exceptions are derived from <xref:System.ServiceModel.FaultException>, on the client the exceptions are regular custom exceptions.</span></span>  
  
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
  
## <a name="behavior"></a><span data-ttu-id="2d462-151">Chování</span><span class="sxs-lookup"><span data-stu-id="2d462-151">Behavior</span></span>  
 <span data-ttu-id="2d462-152">Inspektoři zpráv jsou rozšíření na prostředí runtime klienta nebo spuštění odeslání.</span><span class="sxs-lookup"><span data-stu-id="2d462-152">Message inspectors are extensions to the client runtime or the dispatch runtime.</span></span> <span data-ttu-id="2d462-153">Tato rozšíření jsou konfigurována pomocí *chování*.</span><span class="sxs-lookup"><span data-stu-id="2d462-153">Such extensions are configured using *behaviors*.</span></span> <span data-ttu-id="2d462-154">Chování je třída, která mění chování za běhu modelu služby změnou výchozí konfigurace nebo přidáním rozšíření (například inspektorů zpráv).</span><span class="sxs-lookup"><span data-stu-id="2d462-154">A behavior is a class that changes the behavior of the service model runtime by changing the default configuration or adding extensions (such as message inspectors) to it.</span></span>  
  
 <span data-ttu-id="2d462-155">Následující `SchemaValidationBehavior` třída je chování, které se používá k přidání tohoto ukázkového inspektoru zpráv do klienta nebo expedičního běhu.</span><span class="sxs-lookup"><span data-stu-id="2d462-155">The following `SchemaValidationBehavior` class is the behavior used to add this sample's message inspector to the client or dispatch runtime.</span></span> <span data-ttu-id="2d462-156">Implementace je v obou případech spíše základní.</span><span class="sxs-lookup"><span data-stu-id="2d462-156">The implementation is rather basic in both cases.</span></span> <span data-ttu-id="2d462-157">V <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>aplikaci a , inspektor zprávy <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> je vytvořen a přidán do kolekce příslušného běhu.</span><span class="sxs-lookup"><span data-stu-id="2d462-157">In <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> and <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>, the message inspector is created and added to the <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> collection of the respective runtime.</span></span>  
  
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
> <span data-ttu-id="2d462-158">Toto konkrétní chování není double jako atribut a proto nelze přidat deklarativně na typ smlouvy typu služby.</span><span class="sxs-lookup"><span data-stu-id="2d462-158">This particular behavior does not double as an attribute and therefore cannot be added declaratively onto a contract type of a service type.</span></span> <span data-ttu-id="2d462-159">Toto je rozhodnutí podle návrhu, protože kolekci schématu nelze načíst v deklaraci atributu a odkazující na další umístění konfigurace (například nastavení aplikace) v tomto atributu znamená vytvoření konfiguračního prvku, který není konzistentní se zbytkem konfigurace modelu služby.</span><span class="sxs-lookup"><span data-stu-id="2d462-159">This is a by-design decision made because the schema collection cannot be loaded in an attribute declaration and referring to an extra configuration location (for instance to the application settings) in this attribute means creating a configuration element that is not consistent with the rest of the service model configuration.</span></span> <span data-ttu-id="2d462-160">Proto toto chování lze přidat pouze imperativně prostřednictvím kódu a prostřednictvím rozšíření konfigurace modelu služby.</span><span class="sxs-lookup"><span data-stu-id="2d462-160">Therefore, this behavior can only be added imperatively through code and through a service model configuration extension.</span></span>  
  
## <a name="adding-the-message-inspector-through-configuration"></a><span data-ttu-id="2d462-161">Přidání inspektoru zprávy prostřednictvím konfigurace</span><span class="sxs-lookup"><span data-stu-id="2d462-161">Adding the Message Inspector through Configuration</span></span>  
 <span data-ttu-id="2d462-162">Pro konfiguraci vlastního chování v koncovém bodě v konfiguračním souboru aplikace vyžaduje model služby, aby implementátoři vytvořili *prvek rozšíření* konfigurace reprezentovaný třídou odvozenou z aplikace <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>.</span><span class="sxs-lookup"><span data-stu-id="2d462-162">For configuring a custom behavior on an endpoint in the application configuration file, the service model requires implementers to create a configuration *extension element* represented by a class derived from <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>.</span></span> <span data-ttu-id="2d462-163">Toto rozšíření pak musí být přidándo oddílu konfigurace modelu služby pro rozšíření, jak je znázorněno na následující rozšíření popsané v této části.</span><span class="sxs-lookup"><span data-stu-id="2d462-163">This extension must then be added to the service model's configuration section for extensions as shown for the following extension discussed in this section.</span></span>  
  
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
  
 <span data-ttu-id="2d462-164">Přípony lze přidat do konfiguračního souboru aplikace nebo ASP.NET, což je nejběžnější volba, nebo do konfiguračního souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="2d462-164">Extensions can be added in the application or ASP.NET configuration file, which is the most common choice, or in the machine configuration file.</span></span>  
  
 <span data-ttu-id="2d462-165">Při přidání rozšíření do oboru konfigurace chování lze přidat do konfigurace chování, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="2d462-165">When the extension is added to a configuration scope, the behavior can be added to a behavior configuration as it is shown in the following code.</span></span> <span data-ttu-id="2d462-166">Konfigurace chování jsou opakovaně použitelné prvky, které lze použít pro více koncových bodů podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="2d462-166">Behavior configurations are reusable elements that can be applied to multiple endpoints as required.</span></span> <span data-ttu-id="2d462-167">Vzhledem k tomu, že <xref:System.ServiceModel.Description.IEndpointBehavior>konkrétní chování, které má být zde nakonfigurováno, implementuje , je platné pouze v příslušné části konfigurace v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="2d462-167">Because the particular behavior to be configured here implements <xref:System.ServiceModel.Description.IEndpointBehavior>, it is only valid in the respective configuration section in the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="2d462-168">Prvek, `<schemaValidator>` který konfiguruje inspektor `SchemaValidationBehaviorExtensionElement` zprávy je zálohována třídy.</span><span class="sxs-lookup"><span data-stu-id="2d462-168">The `<schemaValidator>` element that configures the message inspector is backed by the `SchemaValidationBehaviorExtensionElement` class.</span></span> <span data-ttu-id="2d462-169">Třída zpřístupňuje dvě logické `ValidateRequest` veřejné `ValidateReply`vlastnosti s názvem a .</span><span class="sxs-lookup"><span data-stu-id="2d462-169">The class exposes two Boolean public properties named `ValidateRequest` and `ValidateReply`.</span></span> <span data-ttu-id="2d462-170">Oba tyto jsou označeny <xref:System.Configuration.ConfigurationPropertyAttribute>.</span><span class="sxs-lookup"><span data-stu-id="2d462-170">Both of these are marked with a <xref:System.Configuration.ConfigurationPropertyAttribute>.</span></span> <span data-ttu-id="2d462-171">Tento atribut představuje propojení mezi vlastnostmi kódu a atributy XML, které lze vidět na předchozím konfiguračním elementu XML.</span><span class="sxs-lookup"><span data-stu-id="2d462-171">This attribute constitutes the link between the code properties and the XML attributes that can be seen on the preceding XML configuration element.</span></span> <span data-ttu-id="2d462-172">Třída má také `Schemas` vlastnost, která je <xref:System.Configuration.ConfigurationCollectionAttribute> navíc označena `SchemaCollection`a je typu , který je také součástí tohoto vzorku, ale vynechán z tohoto dokumentu pro stručnost.</span><span class="sxs-lookup"><span data-stu-id="2d462-172">The class also has a property `Schemas` that is additionally marked with the <xref:System.Configuration.ConfigurationCollectionAttribute> and is of the type `SchemaCollection`, which is also part of this sample but omitted from this document for brevity.</span></span> <span data-ttu-id="2d462-173">Tato vlastnost spolu s kolekce a `SchemaConfigElement` třída `<schemas>` elementkolekce podporuje prvek v předchozí fragment konfigurace a umožňuje přidání kolekce schémat do sady ověření.</span><span class="sxs-lookup"><span data-stu-id="2d462-173">This property along with the collection and the collection element class `SchemaConfigElement` backs the `<schemas>` element in the preceding configuration snippet and allows adding a collection of schemas to the validation set.</span></span>  
  
 <span data-ttu-id="2d462-174">Potlačená `CreateBehavior` metoda změní konfigurační data na objekt chování, když runtime vyhodnotí konfigurační data při vytváření klienta nebo koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="2d462-174">The overridden `CreateBehavior` method turns the configuration data into a behavior object when the runtime evaluates the configuration data as it builds a client or an endpoint.</span></span>  
  
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
  
## <a name="adding-message-inspectors-imperatively"></a><span data-ttu-id="2d462-175">Přidání inspektorů zpráv imperativně</span><span class="sxs-lookup"><span data-stu-id="2d462-175">Adding Message Inspectors Imperatively</span></span>  
 <span data-ttu-id="2d462-176">S výjimkou prostřednictvím atributů (které nejsou podporovány v této ukázce z důvodu citované dříve) a konfigurace, chování lze poměrně snadno přidat do klienta a za běhu služby pomocí imperativní kód.</span><span class="sxs-lookup"><span data-stu-id="2d462-176">Except through attributes (which is not supported in this sample for the reason cited previously) and configuration, behaviors can quite easily be added to a client and service runtime using imperative code.</span></span> <span data-ttu-id="2d462-177">V této ukázce se provádí v klientské aplikaci otestovat inspektor zpráv klienta.</span><span class="sxs-lookup"><span data-stu-id="2d462-177">In this sample, this is done in the client application to test the client message inspector.</span></span> <span data-ttu-id="2d462-178">Třída `GenericClient` je odvozena <xref:System.ServiceModel.ClientBase%601>od , který zpřístupňuje konfiguraci koncového bodu do uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="2d462-178">The `GenericClient` class is derived from <xref:System.ServiceModel.ClientBase%601>, which exposes the endpoint configuration to the user code.</span></span> <span data-ttu-id="2d462-179">Před klientem je implicitně otevřen konfiguraci koncového bodu lze změnit, například přidáním chování, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="2d462-179">Before the client is implicitly opened the endpoint configuration can be changed, for instance by adding behaviors as shown in the following code.</span></span> <span data-ttu-id="2d462-180">Přidání chování ve službě je do značné míry ekvivalentní techniku klienta zde uvedené a musí být provedena před otevřením hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="2d462-180">Adding the behavior on the service is largely equivalent to the client technique shown here and must be performed before the service host is opened.</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2d462-181">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="2d462-181">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="2d462-182">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2d462-182">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="2d462-183">Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2d462-183">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="2d462-184">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2d462-184">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2d462-185">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="2d462-185">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2d462-186">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="2d462-186">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="2d462-187">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="2d462-187">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2d462-188">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="2d462-188">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageInspectors`  
