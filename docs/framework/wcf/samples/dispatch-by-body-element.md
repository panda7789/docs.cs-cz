---
title: Přiřazování zpráv metodám podle elementu těla
ms.date: 03/30/2017
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
ms.openlocfilehash: 754151f856dfe09b8fd12912ab06d1d8720be016
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183714"
---
# <a name="dispatch-by-body-element"></a><span data-ttu-id="d6a4d-102">Přiřazování zpráv metodám podle elementu těla</span><span class="sxs-lookup"><span data-stu-id="d6a4d-102">Dispatch by Body Element</span></span>
<span data-ttu-id="d6a4d-103">Tato ukázka ukazuje, jak implementovat alternativní algoritmus pro přiřazování příchozích zpráv k operacím.</span><span class="sxs-lookup"><span data-stu-id="d6a4d-103">This sample demonstrates how to implement an alternate algorithm for assigning incoming messages to operations.</span></span>  
  
 <span data-ttu-id="d6a4d-104">Ve výchozím nastavení dispečer modelu služby vybere vhodnou metodu zpracování pro příchozí zprávu na základě hlavičky "Akce" adresování WS zprávy nebo ekvivalentních informací v požadavku HTTP SOAP.</span><span class="sxs-lookup"><span data-stu-id="d6a4d-104">By default, the service model dispatcher selects the appropriate handling method for an incoming message based on the message's WS-Addressing "Action" header or the equivalent information in the HTTP SOAP request.</span></span>  
  
 <span data-ttu-id="d6a4d-105">Některé zásobníky webových služeb SOAP 1.1, které nedodržují pokyny WS-I Basic Profile 1.1, neodesílají zprávy založené na identifikátoru URI akce, ale spíše na základě kvalifikovaného názvu jazyka XML prvního prvku uvnitř těla SOAP.</span><span class="sxs-lookup"><span data-stu-id="d6a4d-105">Some SOAP 1.1 Web services stacks that do not follow the WS-I Basic Profile 1.1 guidelines do not dispatch messages based on the Action URI, but rather based on the XML qualified name of the first element inside the SOAP body.</span></span> <span data-ttu-id="d6a4d-106">Podobně straně klienta těchto zásobníků může odesílat zprávy s prázdnou nebo libovolnou hlavičkou HTTP SoapAction, která byla povolena specifikací SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="d6a4d-106">Likewise, the client side of these stacks might send messages with an empty or arbitrary HTTP SoapAction header, which was permitted by the SOAP 1.1 specification.</span></span>  
  
 <span data-ttu-id="d6a4d-107">Chcete-li změnit způsob, jakým jsou odesílány <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> zprávy metod, ukázka implementuje rozhraní rozšiřitelnosti `DispatchByBodyElementOperationSelector`na rozhraní .</span><span class="sxs-lookup"><span data-stu-id="d6a4d-107">To change the way messages are dispatched to methods, the sample implements the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> extensibility interface on the `DispatchByBodyElementOperationSelector`.</span></span> <span data-ttu-id="d6a4d-108">Tato třída vybere operace na základě prvního prvku textu zprávy.</span><span class="sxs-lookup"><span data-stu-id="d6a4d-108">This class selects operations based on the first element of the message body.</span></span>  
  
 <span data-ttu-id="d6a4d-109">Konstruktor třídy očekává slovník naplněný dvojicemi `XmlQualifiedName` a řetězce, přičemž kvalifikované názvy označují název prvního podřízeného těla SOAP a řetězce označují odpovídající název operace.</span><span class="sxs-lookup"><span data-stu-id="d6a4d-109">The class constructor expects a dictionary populated with pairs of `XmlQualifiedName` and strings, whereby the qualified names indicate the name of the first child of the SOAP body and the strings indicate the matching operation name.</span></span> <span data-ttu-id="d6a4d-110">Název `defaultOperationName` operace, která přijímá všechny zprávy, které nelze porovnat s tímto slovníkem:</span><span class="sxs-lookup"><span data-stu-id="d6a4d-110">The `defaultOperationName` is the name of the operation that receives all messages that cannot be matched against this dictionary:</span></span>  
  
```csharp
class DispatchByBodyElementOperationSelector : IDispatchOperationSelector  
{  
    Dictionary<XmlQualifiedName, string> dispatchDictionary;  
    string defaultOperationName;  
  
    public DispatchByBodyElementOperationSelector(Dictionary<XmlQualifiedName,string> dispatchDictionary, string defaultOperationName)  
    {  
        this.dispatchDictionary = dispatchDictionary;  
        this.defaultOperationName = defaultOperationName;  
    }  
}
```  
  
 <span data-ttu-id="d6a4d-111"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector>implementace jsou velmi jednoduché stavět, protože existuje pouze <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>jedna metoda na rozhraní: .</span><span class="sxs-lookup"><span data-stu-id="d6a4d-111"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementations are very straightforward to build as there is only one method on the interface: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>.</span></span> <span data-ttu-id="d6a4d-112">Úlohou této metody je zkontrolovat příchozí zprávu a vrátit řetězec, který se rovná názvu metody na servisní smlouvě pro aktuální koncový bod.</span><span class="sxs-lookup"><span data-stu-id="d6a4d-112">The job of this method is to inspect an incoming message and to return a string that equals the name of a method on the service contract for the current endpoint.</span></span>  
  
 <span data-ttu-id="d6a4d-113">V této ukázce volič <xref:System.Xml.XmlDictionaryReader> operace získá pro text příchozí <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>zprávy pomocí .</span><span class="sxs-lookup"><span data-stu-id="d6a4d-113">In this sample, the operation selector acquires an <xref:System.Xml.XmlDictionaryReader> for the incoming message's body using <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>.</span></span> <span data-ttu-id="d6a4d-114">Tato metoda již umístí čtenáře na první podřízené tělo zprávy tak, aby bylo dostačující získat název aktuálního prvku a identifikátor URI oboru názvů a kombinovat je `XmlQualifiedName` do, který se pak používá pro vyhledání odpovídající operace ze slovníku drženého volič operace.</span><span class="sxs-lookup"><span data-stu-id="d6a4d-114">This method already positions the reader on the first child of the message's body so that it is sufficient to get the current element's name and namespace URI and combine them into an `XmlQualifiedName` that is then used for looking up the corresponding operation from the dictionary held by the operation selector.</span></span>  
  
```csharp
public string SelectOperation(ref System.ServiceModel.Channels.Message message)  
{  
    XmlDictionaryReader bodyReader = message.GetReaderAtBodyContents();  
    XmlQualifiedName lookupQName = new  
       XmlQualifiedName(bodyReader.LocalName, bodyReader.NamespaceURI);  
    message = CreateMessageCopy(message,bodyReader);  
    if (dispatchDictionary.ContainsKey(lookupQName))  
    {  
         return dispatchDictionary[lookupQName];  
    }  
    else  
    {  
        return defaultOperationName;  
    }  
}  
```  
  
 <span data-ttu-id="d6a4d-115">Přístup k textu <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> zprávy s nebo některou z dalších metod, které poskytují přístup k obsahu textu zprávy způsobí, že zpráva bude označena jako "číst", což znamená, že zpráva je neplatná pro jakékoli další zpracování.</span><span class="sxs-lookup"><span data-stu-id="d6a4d-115">Accessing the message body with <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> or any of the other methods that provide access to the message's body content causes the message to be marked as "read", which means that the message is invalid for any further processing.</span></span> <span data-ttu-id="d6a4d-116">Proto selekto operace vytvoří kopii příchozí zprávy s metodou uvedenou v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="d6a4d-116">Therefore, the operation selector creates a copy of the incoming message with the method shown in the following code.</span></span> <span data-ttu-id="d6a4d-117">Vzhledem k tomu, že pozice čtenáře nebyla během kontroly změněna, může být odkazována nově vytvořenou zprávou, do které jsou také zkopírovány vlastnosti zprávy a záhlaví zprávy, což má za následek přesný klon původní zprávy:</span><span class="sxs-lookup"><span data-stu-id="d6a4d-117">Because the reader's position has not been changed during the inspection, it can be referenced by the newly created message to which the message properties and the message headers are also copied, which results in an exact clone of the original message:</span></span>  
  
```csharp
private Message CreateMessageCopy(Message message,
                                     XmlDictionaryReader body)  
{  
    Message copy = Message.CreateMessage(message.Version,message.Headers.Action,body);  
    copy.Headers.CopyHeaderFrom(message,0);  
    copy.Properties.CopyProperties(message.Properties);  
    return copy;  
}  
```  
  
## <a name="adding-an-operation-selector-to-a-service"></a><span data-ttu-id="d6a4d-118">Přidání voliče operace do služby</span><span class="sxs-lookup"><span data-stu-id="d6a4d-118">Adding an Operation Selector to a Service</span></span>  
 <span data-ttu-id="d6a4d-119">Selektory operací odeslání služby jsou rozšíření dispečera WCF (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="d6a4d-119">Service dispatch operation selectors are extensions to the Windows Communication Foundation (WCF) dispatcher.</span></span> <span data-ttu-id="d6a4d-120">Pro výběr metod na kanálu zpětného volání duplexních smluv existují také voliči operací klienta, které fungují velmi podobně jako voliči operace odeslání popsané zde, ale které nejsou explicitně zahrnuty v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="d6a4d-120">For selecting methods on the callback channel of duplex contracts, there are also client operation selectors, which work very much like the dispatch operation selectors described here, but which are not explicitly covered in this sample.</span></span>  
  
 <span data-ttu-id="d6a4d-121">Stejně jako většina rozšíření modelu služby, selektory operace odeslání jsou přidány do dispečera pomocí chování.</span><span class="sxs-lookup"><span data-stu-id="d6a4d-121">Like most service model extensions, dispatch operation selectors are added to the dispatcher using behaviors.</span></span> <span data-ttu-id="d6a4d-122">*Chování* je konfigurační objekt, který přidá jedno nebo více rozšíření do časového času odeslání (nebo do klientského runtime) nebo jinak změní jeho nastavení.</span><span class="sxs-lookup"><span data-stu-id="d6a4d-122">A *behavior* is a configuration object, which either adds one or more extensions to the dispatch runtime (or to the client runtime) or otherwise changes its settings.</span></span>  
  
 <span data-ttu-id="d6a4d-123">Vzhledem k tomu, že selektory operací mají <xref:System.ServiceModel.Description.IContractBehavior>rozsah smlouvy, vhodné chování k implementaci zde je .</span><span class="sxs-lookup"><span data-stu-id="d6a4d-123">Because operation selectors have contract scope, the appropriate behavior to implement here is the <xref:System.ServiceModel.Description.IContractBehavior>.</span></span> <span data-ttu-id="d6a4d-124">Vzhledem k tomu, <xref:System.Attribute> že rozhraní je implementováno na odvozené třídy, jak je znázorněno v následujícím kódu, chování může být deklarativně přidándo jakékoli smlouvy o poskytování služeb.</span><span class="sxs-lookup"><span data-stu-id="d6a4d-124">Because the interface is implemented on a <xref:System.Attribute> derived class as shown in the following code, the behavior can be declaratively added to any service contract.</span></span> <span data-ttu-id="d6a4d-125"><xref:System.ServiceModel.ServiceHost> Při každém otevření a spuštění runtime odeslání jsou všechna chování nalezena buď jako atributy na smlouvy, operace a implementace služby nebo jako prvek v konfiguraci služby jsou automaticky přidány a následně požádáni, aby přispěly rozšíření nebo upravit výchozí konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="d6a4d-125">Whenever a <xref:System.ServiceModel.ServiceHost> is opened and the dispatch runtime is built, all behaviors found either as attributes on contracts, operations, and service implementations or as element in the service configuration are automatically added and subsequently asked to contribute extensions or modify the default configuration.</span></span>  
  
 <span data-ttu-id="d6a4d-126">Pro stručnost následující kód výňatek zobrazuje pouze implementaci <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>metody , která má vliv na změny konfigurace pro dispečera v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="d6a4d-126">For brevity, the following code excerpt only shows the implementation of the method <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, which effects the configuration changes for the dispatcher in this sample.</span></span> <span data-ttu-id="d6a4d-127">Ostatní metody nejsou zobrazeny, protože se vrátí volajícímu bez provedení jakékoli práce.</span><span class="sxs-lookup"><span data-stu-id="d6a4d-127">The other methods are not shown because they return to the caller without doing any work.</span></span>  
  
```csharp
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 <span data-ttu-id="d6a4d-128">Nejprve <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementace nastaví vyhledávací slovník pro volič operací iteracepřes <xref:System.ServiceModel.Description.OperationDescription> prvky v <xref:System.ServiceModel.Description.ContractDescription>koncovém bodě služby .</span><span class="sxs-lookup"><span data-stu-id="d6a4d-128">First, the <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementation sets up the lookup dictionary for the operation selector by iterating over the <xref:System.ServiceModel.Description.OperationDescription> elements in the service endpoint's <xref:System.ServiceModel.Description.ContractDescription>.</span></span> <span data-ttu-id="d6a4d-129">Potom každý popis operace je zkontrolovánna `DispatchBodyElementAttribute` přítomnost chování, <xref:System.ServiceModel.Description.IOperationBehavior> implementace, která je také definována v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="d6a4d-129">Then, each operation description is inspected for the presence of the `DispatchBodyElementAttribute` behavior, an implementation of <xref:System.ServiceModel.Description.IOperationBehavior> that is also defined in this sample.</span></span> <span data-ttu-id="d6a4d-130">Zatímco tato třída je také chování, je pasivní a nepřispívá aktivně žádné změny konfigurace spuštění odeslání.</span><span class="sxs-lookup"><span data-stu-id="d6a4d-130">While this class is also a behavior, it is passive and does not actively contribute any configuration changes to the dispatch runtime.</span></span> <span data-ttu-id="d6a4d-131">Všechny jeho metody vrátit volajícímu bez nutnosti jakékoli akce.</span><span class="sxs-lookup"><span data-stu-id="d6a4d-131">All of its methods return to the caller without taking any actions.</span></span> <span data-ttu-id="d6a4d-132">Chování operace existuje pouze proto, aby metadata požadovaná pro nový mechanismus odeslání, konkrétně kvalifikovaný název prvku těla, na jehož výskytu je operace vybrána, mohou být přidružena k příslušným operacím.</span><span class="sxs-lookup"><span data-stu-id="d6a4d-132">The operation behavior only exists so that the metadata required for the new dispatch mechanism, namely the qualified name of the body element on whose occurrence an operation is selected, can be associated with the respective operations.</span></span>  
  
 <span data-ttu-id="d6a4d-133">Pokud je takové chování nalezeno, je do slovníku`QName` přidán pár hodnot`Name` vytvořený z kvalifikovaného názvu XML (vlastnost) a název operace ( vlastnost).</span><span class="sxs-lookup"><span data-stu-id="d6a4d-133">If such a behavior is found, a value pair created from the XML qualified name (`QName` property) and the operation name (`Name` property) is added to the dictionary.</span></span>  
  
 <span data-ttu-id="d6a4d-134">Po naplnění slovníku je `DispatchByBodyElementOperationSelector` vytvořen nový s těmito informacemi a nastaven jako volič operace dispečera runtime:</span><span class="sxs-lookup"><span data-stu-id="d6a4d-134">Once the dictionary is populated, a new `DispatchByBodyElementOperationSelector` is constructed with this information and set as the operation selector of the dispatch runtime:</span></span>  
  
```csharp
public void ApplyDispatchBehavior(ContractDescription contractDescription, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.DispatchRuntime dispatchRuntime)  
{  
    Dictionary<XmlQualifiedName,string> dispatchDictionary =
                     new Dictionary<XmlQualifiedName,string>();  
    foreach( OperationDescription operationDescription in
                              contractDescription.Operations )  
    {  
        DispatchBodyElementAttribute dispatchBodyElement =
   operationDescription.Behaviors.Find<DispatchBodyElementAttribute>();  
        if ( dispatchBodyElement != null )  
        {  
             dispatchDictionary.Add(dispatchBodyElement.QName,
                              operationDescription.Name);  
        }  
    }  
    dispatchRuntime.OperationSelector =
            new DispatchByBodyElementOperationSelector(  
               dispatchDictionary,
               dispatchRuntime.UnhandledDispatchOperation.Name);  
    }  
}  
```  
  
## <a name="implementing-the-service"></a><span data-ttu-id="d6a4d-135">Implementace služby</span><span class="sxs-lookup"><span data-stu-id="d6a4d-135">Implementing the Service</span></span>  
 <span data-ttu-id="d6a4d-136">Chování implementované v této ukázce přímo ovlivňuje způsob interpretace a odeslání zpráv z drátu, což je funkce smlouvy o poskytování služeb.</span><span class="sxs-lookup"><span data-stu-id="d6a4d-136">The behavior implemented in this sample directly affects how messages from the wire are interpreted and dispatched, which is a function of the service contract.</span></span> <span data-ttu-id="d6a4d-137">V důsledku toho by mělo být chování deklarováno na úrovni servisní smlouvy v jakékoli implementaci služby, která se rozhodne ji použít.</span><span class="sxs-lookup"><span data-stu-id="d6a4d-137">Consequently, the behavior should be declared on the service contract level in any service implementation that chooses to use it.</span></span>  
  
 <span data-ttu-id="d6a4d-138">Ukázková projektová služba `DispatchByBodyElementBehaviorAttribute` použije chování `IDispatchedByBody` smlouvy na servisní smlouvu `OperationForBodyA()` `OperationForBodyB()` a `DispatchBodyElementAttribute` označí každou ze dvou operací a chování operace.</span><span class="sxs-lookup"><span data-stu-id="d6a4d-138">The sample project service applies the `DispatchByBodyElementBehaviorAttribute` contract behavior to the `IDispatchedByBody` service contract and labels each of the two operations `OperationForBodyA()` and `OperationForBodyB()` with a `DispatchBodyElementAttribute` operation behavior.</span></span> <span data-ttu-id="d6a4d-139">Při otevření hostitele služby pro službu, která implementuje tuto smlouvu, tato metadata je vyzvednuta tvůrcem dispečera, jak bylo popsáno dříve.</span><span class="sxs-lookup"><span data-stu-id="d6a4d-139">When a service host for a service that implements this contract is opened, this metadata is picked up by the dispatcher builder as previously described.</span></span>  
  
 <span data-ttu-id="d6a4d-140">Vzhledem k tomu, že se volič operace odesílá výhradně na základě elementu textu zprávy a ignoruje "Akce", je nutné sdělit, aby ovládací prvek `ReplyAction` runtime <xref:System.ServiceModel.OperationContractAttribute>nekontroloval záhlaví "Akce" na vrácených odpovědích přiřazením zástupného znaku "\*" vlastnosti .</span><span class="sxs-lookup"><span data-stu-id="d6a4d-140">Because the operation selector dispatches solely based on the message body element and ignores the "Action", it is required to tell the runtime not to check the "Action" header on the returned replies by assigning the wildcard "\*" to the `ReplyAction` property of <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="d6a4d-141">Kromě toho je nutné mít výchozí operaci, která má vlastnost "Akce"\*nastavena na zástupný znak " ".</span><span class="sxs-lookup"><span data-stu-id="d6a4d-141">Furthermore, it is required to have a default operation that has the "Action" property set to the wildcard "\*".</span></span> <span data-ttu-id="d6a4d-142">Výchozí operace přijímá všechny zprávy, které nelze odeslat `DispatchBodyElementAttribute`a nemá :</span><span class="sxs-lookup"><span data-stu-id="d6a4d-142">The default operation receives all messages which cannot be dispatched and does not have a `DispatchBodyElementAttribute`:</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"),  
                            DispatchByBodyElementBehavior]  
public interface IDispatchedByBody  
{  
    [OperationContract(ReplyAction="*"),
     DispatchBodyElement("bodyA","http://tempuri.org")]  
    Message OperationForBodyA(Message msg);  
    [OperationContract(ReplyAction = "*"),
     DispatchBodyElement("bodyB", "http://tempuri.org")]  
    Message OperationForBodyB(Message msg);  
    [OperationContract(Action="*", ReplyAction="*")]  
    Message DefaultOperation(Message msg);  
}  
```  
  
 <span data-ttu-id="d6a4d-143">Ukázková implementace služby je jednoduchá.</span><span class="sxs-lookup"><span data-stu-id="d6a4d-143">The sample service implementation is straightforward.</span></span> <span data-ttu-id="d6a4d-144">Každá metoda zalomí přijatou zprávu do zprávy s odpovědí a vrátí ji zpět klientovi.</span><span class="sxs-lookup"><span data-stu-id="d6a4d-144">Every method wraps the received message into a reply message and echoes it back to the client.</span></span>  
  
## <a name="running-and-building-the-sample"></a><span data-ttu-id="d6a4d-145">Běh a vytváření ukázky</span><span class="sxs-lookup"><span data-stu-id="d6a4d-145">Running and Building the Sample</span></span>  
 <span data-ttu-id="d6a4d-146">Při spuštění ukázky, obsah těla operace odpovědi jsou zobrazeny v okně klientské konzole podobné následující (formátovaný) výstup.</span><span class="sxs-lookup"><span data-stu-id="d6a4d-146">When you run the sample, the body content of the operation responses are displayed in the client console window similar to the following (formatted) output.</span></span>  
  
 <span data-ttu-id="d6a4d-147">Klient odešle službě tři zprávy, jejichž `bodyA`element `bodyB`obsahu `bodyX`těla je pojmenován , a , v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="d6a4d-147">The client sends three messages to the service whose body content element is named `bodyA`, `bodyB`, and `bodyX`, respectively.</span></span> <span data-ttu-id="d6a4d-148">Jak může být odloženo z předchozího popisu a zobrazené `bodyA` servisní smlouvy, příchozí `OperationForBodyA()` zpráva s elementem je odeslána do metody.</span><span class="sxs-lookup"><span data-stu-id="d6a4d-148">As can be deferred from the previous description and the service contract shown, the incoming message with the `bodyA` element is dispatched to the `OperationForBodyA()` method.</span></span> <span data-ttu-id="d6a4d-149">Vzhledem k tomu, že neexistuje `bodyX` žádný cíl explicitní odeslání zprávy `DefaultOperation()`s elementem body, je zpráva odeslána do .</span><span class="sxs-lookup"><span data-stu-id="d6a4d-149">Because there is no explicit dispatch target for the message with the `bodyX` body element, the message is dispatched to the `DefaultOperation()`.</span></span> <span data-ttu-id="d6a4d-150">Každá operace služby zabalí text přijaté zprávy do prvku specifického pro metodu a vrátí jej, což se provádí korelovat vstupní a výstupní zprávy jasně pro tuto ukázku:</span><span class="sxs-lookup"><span data-stu-id="d6a4d-150">Each of the service operations wraps the received message body into an element specific to the method and returns it, which is done to correlate input and output messages clearly for this sample:</span></span>  
  
```xml  
<?xml version="1.0" encoding="IBM437"?>  
<replyBodyA xmlns="http://tempuri.org">  
   <q:bodyA xmlns:q="http://tempuri.org">test</q:bodyA>  
</replyBodyA>  
<?xml version="1.0" encoding="IBM437"?>  
<replyBodyB xmlns="http://tempuri.org">  
  <q:bodyB xmlns:q="http://tempuri.org">test</q:bodyB>  
</replyBodyB>  
<?xml version="1.0" encoding="IBM437"?>  
<replyDefault xmlns="http://tempuri.org">  
   <q:bodyX xmlns:q="http://tempuri.org">test</q:bodyX>  
</replyDefault>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d6a4d-151">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="d6a4d-151">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d6a4d-152">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d6a4d-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="d6a4d-153">Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d6a4d-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="d6a4d-154">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d6a4d-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d6a4d-155">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="d6a4d-155">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d6a4d-156">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="d6a4d-156">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d6a4d-157">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="d6a4d-157">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d6a4d-158">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="d6a4d-158">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
