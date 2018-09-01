---
title: Přiřazování zpráv metodám podle elementu těla
ms.date: 03/30/2017
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
ms.openlocfilehash: 449c153092d80bb457a2059b80158ea665bfc645
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43396375"
---
# <a name="dispatch-by-body-element"></a><span data-ttu-id="35450-102">Přiřazování zpráv metodám podle elementu těla</span><span class="sxs-lookup"><span data-stu-id="35450-102">Dispatch by Body Element</span></span>
<span data-ttu-id="35450-103">Tento příklad ukazuje, jak implementovat alternativní algoritmus pro přiřazení k operacím příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="35450-103">This sample demonstrates how to implement an alternate algorithm for assigning incoming messages to operations.</span></span>  
  
 <span data-ttu-id="35450-104">Ve výchozím nastavení, vybere dispečer modelu služby příslušné zpracování metody pro příchozí zprávy podle zprávy WS-Addressing "Action" záhlaví nebo ekvivalentní informace v požadavku SOAP protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="35450-104">By default, the service model dispatcher selects the appropriate handling method for an incoming message based on the message's WS-Addressing "Action" header or the equivalent information in the HTTP SOAP request.</span></span>  
  
 <span data-ttu-id="35450-105">Některé SOAP 1.1 webových služeb balíčky, které se neřídí WS-I Basic Profile 1.1 pokyny není odeslání zprávy založené na identifikátor URI akce, ale spíše založené na XML kvalifikovaný název prvního prvku uvnitř těla protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="35450-105">Some SOAP 1.1 Web services stacks that do not follow the WS-I Basic Profile 1.1 guidelines do not dispatch messages based on the Action URI, but rather based on the XML qualified name of the first element inside the SOAP body.</span></span> <span data-ttu-id="35450-106">Tyto balíčky na straně klienta, může odesílat zprávy pomocí prázdný nebo libovolné záhlaví HTTP SoapAction, které bylo povoleno ve specifikaci protokolu SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="35450-106">Likewise, the client side of these stacks might send messages with an empty or arbitrary HTTP SoapAction header, which was permitted by the SOAP 1.1 specification.</span></span>  
  
 <span data-ttu-id="35450-107">Chcete-li změnit způsob, jakým jsou zprávy odesílány metodám, ukázka implementuje <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> rozšiřitelnost rozhraní `DispatchByBodyElementOperationSelector`.</span><span class="sxs-lookup"><span data-stu-id="35450-107">To change the way messages are dispatched to methods, the sample implements the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> extensibility interface on the `DispatchByBodyElementOperationSelector`.</span></span> <span data-ttu-id="35450-108">Tato třída vybere operace založené na první prvek těla zprávy.</span><span class="sxs-lookup"><span data-stu-id="35450-108">This class selects operations based on the first element of the message body.</span></span>  
  
 <span data-ttu-id="35450-109">Konstruktor třídy očekává, že vyplní dvojice slovník `XmlQualifiedName` a řetězce, kterým kvalifikované názvy odděluje název prvního podřízeného těla protokolu SOAP a řetězce označují odpovídající název operace.</span><span class="sxs-lookup"><span data-stu-id="35450-109">The class constructor expects a dictionary populated with pairs of `XmlQualifiedName` and strings, whereby the qualified names indicate the name of the first child of the SOAP body and the strings indicate the matching operation name.</span></span> <span data-ttu-id="35450-110">`defaultOperationName` Je název operace, která přijímá všechny zprávy, které nejde spárovat proti tomuto slovníku:</span><span class="sxs-lookup"><span data-stu-id="35450-110">The `defaultOperationName` is the name of the operation that receives all messages that cannot be matched against this dictionary:</span></span>  
  
```  
class DispatchByBodyElementOperationSelector : IDispatchOperationSelector  
{  
    Dictionary<XmlQualifiedName, string> dispatchDictionary;  
    string defaultOperationName;  
  
    public DispatchByBodyElementOperationSelector(Dictionary<XmlQualifiedName,string> dispatchDictionary, string defaultOperationName)  
    {  
        this.dispatchDictionary = dispatchDictionary;  
        this.defaultOperationName = defaultOperationName;  
    }  
```  
  
 <span data-ttu-id="35450-111"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementace jsou velmi jednoduché k sestavení, protože existuje jenom jedna metoda v rozhraní: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>.</span><span class="sxs-lookup"><span data-stu-id="35450-111"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementations are very straightforward to build as there is only one method on the interface: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>.</span></span> <span data-ttu-id="35450-112">Úloha této metody je ke kontrole příchozích zpráv a vrátí řetězec, který se rovná název metody u kontraktu služby pro aktuální koncový bod.</span><span class="sxs-lookup"><span data-stu-id="35450-112">The job of this method is to inspect an incoming message and to return a string that equals the name of a method on the service contract for the current endpoint.</span></span>  
  
 <span data-ttu-id="35450-113">V tomto příkladu získá selektor operace <xref:System.Xml.XmlDictionaryReader> pro příchozí zprávy textu v nástrojích <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>.</span><span class="sxs-lookup"><span data-stu-id="35450-113">In this sample, the operation selector acquires an <xref:System.Xml.XmlDictionaryReader> for the incoming message's body using <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>.</span></span> <span data-ttu-id="35450-114">Tato metoda čtecí modul již umístí na prvním podřízeným těla zprávy tak, aby je dostatečné pro získání názvu a oboru názvů identifikátoru URI aktuálního elementu a zkombinujte je do `XmlQualifiedName` , která se pak použije pro vyhledávání odpovídající operace slovník drží selektor operace.</span><span class="sxs-lookup"><span data-stu-id="35450-114">This method already positions the reader on the first child of the message's body so that it is sufficient to get the current element's name and namespace URI and combine them into an `XmlQualifiedName` that is then used for looking up the corresponding operation from the dictionary held by the operation selector.</span></span>  
  
```  
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
  
 <span data-ttu-id="35450-115">Přístup k textu zprávy s <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> nebo některou z metod, které poskytují přístup k obsahu těla zprávy způsobí, že zpráva, která má být označený jako "čtení", což znamená, že zpráva není platná pro další zpracování.</span><span class="sxs-lookup"><span data-stu-id="35450-115">Accessing the message body with <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> or any of the other methods that provide access to the message's body content causes the message to be marked as "read", which means that the message is invalid for any further processing.</span></span> <span data-ttu-id="35450-116">Selektor operace proto vytvoří kopii příchozí zprávy s metodou je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="35450-116">Therefore, the operation selector creates a copy of the incoming message with the method shown in the following code.</span></span> <span data-ttu-id="35450-117">Protože při kontrole nedošlo ke změně pozice čtenáře, lze odkazovat pomocí nově vytvořeného zpráv ke kterému vlastnosti zprávy a záhlaví zpráv jsou zkopírovány také, což vede k přesné klon původní zprávy:</span><span class="sxs-lookup"><span data-stu-id="35450-117">Because the reader's position has not been changed during the inspection, it can be referenced by the newly created message to which the message properties and the message headers are also copied, which results in an exact clone of the original message:</span></span>  
  
```  
private Message CreateMessageCopy(Message message,   
                                     XmlDictionaryReader body)  
{  
    Message copy = Message.CreateMessage(message.Version,message.Headers.Action,body);  
    copy.Headers.CopyHeaderFrom(message,0);  
    copy.Properties.CopyProperties(message.Properties);  
    return copy;  
}  
```  
  
## <a name="adding-an-operation-selector-to-a-service"></a><span data-ttu-id="35450-118">Přidání selektor operace služby</span><span class="sxs-lookup"><span data-stu-id="35450-118">Adding an Operation Selector to a Service</span></span>  
 <span data-ttu-id="35450-119">Selektory operaci odeslání služby jsou rozšíření pro dispečera Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="35450-119">Service dispatch operation selectors are extensions to the Windows Communication Foundation (WCF) dispatcher.</span></span> <span data-ttu-id="35450-120">Pro výběr metody zpětného volání kanál duplexní kontrakty, existují také selektory provozu klienta, které fungují velmi podobně jako selektory operaci odeslání je zde popsáno, ale která nejsou výslovně uvedena v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="35450-120">For selecting methods on the callback channel of duplex contracts, there are also client operation selectors, which work very much like the dispatch operation selectors described here, but which are not explicitly covered in this sample.</span></span>  
  
 <span data-ttu-id="35450-121">Jako většina rozšíření modelů služeb se přidají selektory operaci odeslání do dispečera pomocí chování.</span><span class="sxs-lookup"><span data-stu-id="35450-121">Like most service model extensions, dispatch operation selectors are added to the dispatcher using behaviors.</span></span> <span data-ttu-id="35450-122">A *chování* je objekt konfigurace, která přidá jeden nebo více rozšíření modulu runtime odeslání (nebo modul runtime klienta) nebo v opačném případě se změní jeho nastavení.</span><span class="sxs-lookup"><span data-stu-id="35450-122">A *behavior* is a configuration object, which either adds one or more extensions to the dispatch runtime (or to the client runtime) or otherwise changes its settings.</span></span>  
  
 <span data-ttu-id="35450-123">Vzhledem k tomu, že selektory operace kontraktu oboru, je odpovídající chování k implementaci tady <xref:System.ServiceModel.Description.IContractBehavior>.</span><span class="sxs-lookup"><span data-stu-id="35450-123">Because operation selectors have contract scope, the appropriate behavior to implement here is the <xref:System.ServiceModel.Description.IContractBehavior>.</span></span> <span data-ttu-id="35450-124">Protože rozhraní je implementováno v <xref:System.Attribute> odvozené třídy jak je znázorněno v následujícím kódu, chování lze deklarativně přidat do jakékoli kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="35450-124">Because the interface is implemented on a <xref:System.Attribute> derived class as shown in the following code, the behavior can be declaratively added to any service contract.</span></span> <span data-ttu-id="35450-125">Pokaždé, když se <xref:System.ServiceModel.ServiceHost> je otevřený a sestaven modul runtime odeslání, najít všechny chování jako atributy u kontraktů, operace a implementací služby nebo jako prvek v konfiguraci služby se automaticky přidá a následně vyzve k přispívat rozšíření nebo změnit výchozí konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="35450-125">Whenever a <xref:System.ServiceModel.ServiceHost> is opened and the dispatch runtime is built, all behaviors found either as attributes on contracts, operations, and service implementations or as element in the service configuration are automatically added and subsequently asked to contribute extensions or modify the default configuration.</span></span>  
  
 <span data-ttu-id="35450-126">Pro zkrácení, následující úryvek kódu se zobrazují jenom implementaci metody <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, což ovlivňuje změny konfigurace pro dispečera v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="35450-126">For brevity, the following code excerpt only shows the implementation of the method <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, which effects the configuration changes for the dispatcher in this sample.</span></span> <span data-ttu-id="35450-127">Jiné metody se nezobrazují, vzhledem k tomu, aniž by každé dílo vrácení volajícímu.</span><span class="sxs-lookup"><span data-stu-id="35450-127">The other methods are not shown because they return to the caller without doing any work.</span></span>  
  
```  
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)   
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 <span data-ttu-id="35450-128">Nejprve je potřeba <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementace vyhledávacího slovníku za selektor operace nastaví pomocí provádí iterace <xref:System.ServiceModel.Description.OperationDescription> prvky v koncovém bodě služby <xref:System.ServiceModel.Description.ContractDescription>.</span><span class="sxs-lookup"><span data-stu-id="35450-128">First, the <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementation sets up the lookup dictionary for the operation selector by iterating over the <xref:System.ServiceModel.Description.OperationDescription> elements in the service endpoint's <xref:System.ServiceModel.Description.ContractDescription>.</span></span> <span data-ttu-id="35450-129">Potom se každý popis operace prozkoumá přítomnost `DispatchBodyElementAttribute` chování, implementace <xref:System.ServiceModel.Description.IOperationBehavior> , který je také definováno v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="35450-129">Then, each operation description is inspected for the presence of the `DispatchBodyElementAttribute` behavior, an implementation of <xref:System.ServiceModel.Description.IOperationBehavior> that is also defined in this sample.</span></span> <span data-ttu-id="35450-130">Tato třída je také chování, je pasivní činnost a není aktivně přispět změny konfigurace modulu runtime odeslání.</span><span class="sxs-lookup"><span data-stu-id="35450-130">While this class is also a behavior, it is passive and does not actively contribute any configuration changes to the dispatch runtime.</span></span> <span data-ttu-id="35450-131">Všechny jeho metody vracet volajícímu bez jakékoli akce.</span><span class="sxs-lookup"><span data-stu-id="35450-131">All of its methods return to the caller without taking any actions.</span></span> <span data-ttu-id="35450-132">Chování operace existuje pouze tak, aby byla metadata potřebná pro nové odeslání mechanismus, konkrétně kvalifikovaný název prvku textu na jehož výskyt operace zaškrtnuto, mohou být spojeny s příslušné operace.</span><span class="sxs-lookup"><span data-stu-id="35450-132">The operation behavior only exists so that the metadata required for the new dispatch mechanism, namely the qualified name of the body element on whose occurrence an operation is selected, can be associated with the respective operations.</span></span>  
  
 <span data-ttu-id="35450-133">Pokud takové chování není nalezen, hodnota pár vytvořené z XML kvalifikovaný název (`QName` vlastnost) a název operace (`Name` vlastnost) se přidá do slovníku.</span><span class="sxs-lookup"><span data-stu-id="35450-133">If such a behavior is found, a value pair created from the XML qualified name (`QName` property) and the operation name (`Name` property) is added to the dictionary.</span></span>  
  
 <span data-ttu-id="35450-134">Po naplnění slovníku nový `DispatchByBodyElementOperationSelector` je vytvořen pomocí těchto informací a nastavit jako selektor operace odeslání Runtime:</span><span class="sxs-lookup"><span data-stu-id="35450-134">Once the dictionary is populated, a new `DispatchByBodyElementOperationSelector` is constructed with this information and set as the operation selector of the dispatch runtime:</span></span>  
  
```  
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
  
## <a name="implementing-the-service"></a><span data-ttu-id="35450-135">Implementace této služby</span><span class="sxs-lookup"><span data-stu-id="35450-135">Implementing the Service</span></span>  
 <span data-ttu-id="35450-136">Chování, které jsou implementovány v této ukázce přímo ovlivní jak přenosu interpretován a zpráv odeslaných, což je funkce kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="35450-136">The behavior implemented in this sample directly affects how messages from the wire are interpreted and dispatched, which is a function of the service contract.</span></span> <span data-ttu-id="35450-137">V důsledku toho by měly být deklarovány chování na úrovni kontraktu služby v jakékoli implementaci služby, který vybírá jeho použití.</span><span class="sxs-lookup"><span data-stu-id="35450-137">Consequently, the behavior should be declared on the service contract level in any service implementation that chooses to use it.</span></span>  
  
 <span data-ttu-id="35450-138">Služba projektu vzorku se vztahuje `DispatchByBodyElementBehaviorAttribute` smlouvy chování `IDispatchedByBody` smlouvy a popisky z těchto dvou operací služby `OperationForBodyA()` a `OperationForBodyB()` s `DispatchBodyElementAttribute` chování operace.</span><span class="sxs-lookup"><span data-stu-id="35450-138">The sample project service applies the `DispatchByBodyElementBehaviorAttribute` contract behavior to the `IDispatchedByBody` service contract and labels each of the two operations `OperationForBodyA()` and `OperationForBodyB()` with a `DispatchBodyElementAttribute` operation behavior.</span></span> <span data-ttu-id="35450-139">Při otevření hostitele služby pro službu, která implementuje tento kontrakt tato metadata je převzata tvůrcem dispečer jak bylo popsáno dříve.</span><span class="sxs-lookup"><span data-stu-id="35450-139">When a service host for a service that implements this contract is opened, this metadata is picked up by the dispatcher builder as previously described.</span></span>  
  
 <span data-ttu-id="35450-140">Protože modulu pro výběr operace odešle výhradně podle elementu těla zprávy a ignoruje "Action", je potřeba zjistit, modul runtime není ke kontrole "Action" záhlaví odpovědi vrácené přiřazením zástupný znak "\*" na `ReplyAction` vlastnost <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="35450-140">Because the operation selector dispatches solely based on the message body element and ignores the "Action", it is required to tell the runtime not to check the "Action" header on the returned replies by assigning the wildcard "\*" to the `ReplyAction` property of <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="35450-141">Kromě toho je potřeba mít výchozí operaci, která má vlastnost "Action" nastavenou na zástupný znak "\*".</span><span class="sxs-lookup"><span data-stu-id="35450-141">Furthermore, it is required to have a default operation that has the "Action" property set to the wildcard "\*".</span></span> <span data-ttu-id="35450-142">Výchozí operaci přijímá všechny zprávy, které se nedají odbavovat a nemá `DispatchBodyElementAttribute`:</span><span class="sxs-lookup"><span data-stu-id="35450-142">The default operation receives all messages which cannot be dispatched and does not have a `DispatchBodyElementAttribute`:</span></span>  
  
```  
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
  
 <span data-ttu-id="35450-143">Ukázková implementace služby je jednoduché.</span><span class="sxs-lookup"><span data-stu-id="35450-143">The sample service implementation is straightforward.</span></span> <span data-ttu-id="35450-144">EVERY – metoda zabalí do zprávy s odpovědí přijatou zprávu a vrátí ji zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="35450-144">Every method wraps the received message into a reply message and echoes it back to the client.</span></span>  
  
## <a name="running-and-building-the-sample"></a><span data-ttu-id="35450-145">Spuštění a sestavování vzorku</span><span class="sxs-lookup"><span data-stu-id="35450-145">Running and Building the Sample</span></span>  
 <span data-ttu-id="35450-146">Při spuštění ukázky obsah textu odpovědi operace se zobrazují v okně konzoly klienta, podobně jako následující výstup (formátovaný).</span><span class="sxs-lookup"><span data-stu-id="35450-146">When you run the sample, the body content of the operation responses are displayed in the client console window similar to the following (formatted) output.</span></span>  
  
 <span data-ttu-id="35450-147">Klient odešle tři zprávy do služby jehož obsahu je s názvem elementu těla `bodyA`, `bodyB`, a `bodyX`v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="35450-147">The client sends three messages to the service whose body content element is named `bodyA`, `bodyB`, and `bodyX`, respectively.</span></span> <span data-ttu-id="35450-148">Jako může být odložena z předchozí popis a kontrakt služby uvedené, příchozí zprávy s `bodyA` element je odeslána `OperationForBodyA()` metoda.</span><span class="sxs-lookup"><span data-stu-id="35450-148">As can be deferred from the previous description and the service contract shown, the incoming message with the `bodyA` element is dispatched to the `OperationForBodyA()` method.</span></span> <span data-ttu-id="35450-149">Protože neexistuje žádný explicitní odeslání cíl pro zprávu s `bodyX` body element, je odeslána zpráva `DefaultOperation()`.</span><span class="sxs-lookup"><span data-stu-id="35450-149">Because there is no explicit dispatch target for the message with the `bodyX` body element, the message is dispatched to the `DefaultOperation()`.</span></span> <span data-ttu-id="35450-150">Každá z operací služby zalomí text zprávy přijaté do elementu specifické pro metodu a vrátí jej, která se provádí korelaci vstupní a výstupní zprávy jasně pro tuto ukázku:</span><span class="sxs-lookup"><span data-stu-id="35450-150">Each of the service operations wraps the received message body into an element specific to the method and returns it, which is done to correlate input and output messages clearly for this sample:</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="35450-151">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="35450-151">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="35450-152">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="35450-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="35450-153">Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="35450-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="35450-154">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="35450-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="35450-155">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="35450-155">The samples may already be installed on your machine.</span></span> <span data-ttu-id="35450-156">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="35450-156">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="35450-157">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="35450-157">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="35450-158">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="35450-158">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
  
## <a name="see-also"></a><span data-ttu-id="35450-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="35450-159">See Also</span></span>
