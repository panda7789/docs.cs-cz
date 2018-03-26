---
title: Přiřazování zpráv metodám podle elementu těla
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4ab8ddccafa8dbf1ecde8afbb07f0a61faa62be5
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2018
---
# <a name="dispatch-by-body-element"></a><span data-ttu-id="06ba2-102">Přiřazování zpráv metodám podle elementu těla</span><span class="sxs-lookup"><span data-stu-id="06ba2-102">Dispatch by Body Element</span></span>
<span data-ttu-id="06ba2-103">Tento příklad znázorňuje způsob implementace alternativní algoritmus pro přiřazení k operacím příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="06ba2-103">This sample demonstrates how to implement an alternate algorithm for assigning incoming messages to operations.</span></span>  
  
 <span data-ttu-id="06ba2-104">Ve výchozím nastavení vybere dispečera modelu služby příslušné zpracování metodu pro příchozí zprávy založené na protokolu WS-Addressing zprávy "Action" záhlaví nebo ekvivalentní informace v požadavku HTTP SOAP.</span><span class="sxs-lookup"><span data-stu-id="06ba2-104">By default, the service model dispatcher selects the appropriate handling method for an incoming message based on the message's WS-Addressing "Action" header or the equivalent information in the HTTP SOAP request.</span></span>  
  
 <span data-ttu-id="06ba2-105">Některé SOAP 1.1 webových služeb zásobníky, které neodpovídají WS-I Basic Profile 1.1 pokyny není odesílání zpráv na základě v identifikátoru URI akce, ale spíš podle XML kvalifikovaný název první prvek uvnitř těla protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="06ba2-105">Some SOAP 1.1 Web services stacks that do not follow the WS-I Basic Profile 1.1 guidelines do not dispatch messages based on the Action URI, but rather based on the XML qualified name of the first element inside the SOAP body.</span></span> <span data-ttu-id="06ba2-106">Tyto balíčky na straně klienta, může odesílat zprávy s prázdná nebo libovolný HTTP SoapAction hlavičky, která byla povolena specifikací SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="06ba2-106">Likewise, the client side of these stacks might send messages with an empty or arbitrary HTTP SoapAction header, which was permitted by the SOAP 1.1 specification.</span></span>  
  
 <span data-ttu-id="06ba2-107">Chcete-li změnit způsob, jakým se odesílají zprávy do metod, implementuje vzorku <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> rozšiřitelnost rozhraní na `DispatchByBodyElementOperationSelector`.</span><span class="sxs-lookup"><span data-stu-id="06ba2-107">To change the way messages are dispatched to methods, the sample implements the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> extensibility interface on the `DispatchByBodyElementOperationSelector`.</span></span> <span data-ttu-id="06ba2-108">Tato třída vybere operace založené na první prvek textu zprávy.</span><span class="sxs-lookup"><span data-stu-id="06ba2-108">This class selects operations based on the first element of the message body.</span></span>  
  
 <span data-ttu-id="06ba2-109">Konstruktoru třídy očekává slovník naplněný dvojici `XmlQualifiedName` a řetězce, kterým kvalifikované názvy označení názvu prvního podřízeného těla protokolu SOAP a řetězce znamenat odpovídající název operace.</span><span class="sxs-lookup"><span data-stu-id="06ba2-109">The class constructor expects a dictionary populated with pairs of `XmlQualifiedName` and strings, whereby the qualified names indicate the name of the first child of the SOAP body and the strings indicate the matching operation name.</span></span> <span data-ttu-id="06ba2-110">`defaultOperationName` Je název operace, která přijímá všechny zprávy, které nelze porovnání tohoto slovníku:</span><span class="sxs-lookup"><span data-stu-id="06ba2-110">The `defaultOperationName` is the name of the operation that receives all messages that cannot be matched against this dictionary:</span></span>  
  
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
  
 <span data-ttu-id="06ba2-111"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementace jsou velmi jednoduché, jako je pouze jednu metodu na rozhraní pro sestavení: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>.</span><span class="sxs-lookup"><span data-stu-id="06ba2-111"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementations are very straightforward to build as there is only one method on the interface: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>.</span></span> <span data-ttu-id="06ba2-112">Úloha tato metoda je kontrola příchozí zprávy a vrátí řetězec, který se rovná názvu metody na kontrakt služby pro aktuální koncový bod.</span><span class="sxs-lookup"><span data-stu-id="06ba2-112">The job of this method is to inspect an incoming message and to return a string that equals the name of a method on the service contract for the current endpoint.</span></span>  
  
 <span data-ttu-id="06ba2-113">V této ukázce získá selektor operace <xref:System.Xml.XmlDictionaryReader> pro příchozí zprávy je text použití <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>.</span><span class="sxs-lookup"><span data-stu-id="06ba2-113">In this sample, the operation selector acquires an <xref:System.Xml.XmlDictionaryReader> for the incoming message's body using <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>.</span></span> <span data-ttu-id="06ba2-114">Tato metoda již umisťuje čtečky na prvním podřízeným objektem těla zprávy, tak, aby se pro získání aktuálního elementu název a identifikátor URI oboru názvů a zkombinovat do dostatečná `XmlQualifiedName` , pak se používá pro vyhledávání odpovídající operaci provést z slovník držené selektor operace.</span><span class="sxs-lookup"><span data-stu-id="06ba2-114">This method already positions the reader on the first child of the message's body so that it is sufficient to get the current element's name and namespace URI and combine them into an `XmlQualifiedName` that is then used for looking up the corresponding operation from the dictionary held by the operation selector.</span></span>  
  
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
  
 <span data-ttu-id="06ba2-115">Přístup k tělo zprávy s <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> nebo některou z metod, které poskytují přístup k obsahu tělo zprávy způsobí, že zpráva byla označena jako "číst", což znamená, že zprávy je neplatný pro další zpracování.</span><span class="sxs-lookup"><span data-stu-id="06ba2-115">Accessing the message body with <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> or any of the other methods that provide access to the message's body content causes the message to be marked as "read", which means that the message is invalid for any further processing.</span></span> <span data-ttu-id="06ba2-116">Proto selektor operace vytvoří kopii příchozí zprávy s metodou vidět v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="06ba2-116">Therefore, the operation selector creates a copy of the incoming message with the method shown in the following code.</span></span> <span data-ttu-id="06ba2-117">Protože pozice čtenáře nebylo změněno při kontrole, může být odkazován nově vytvořenou zprávu do které vlastnosti zprávy a záhlaví zprávy jsou také zkopírovali, což vede přesný klon na původní zprávu o:</span><span class="sxs-lookup"><span data-stu-id="06ba2-117">Because the reader's position has not been changed during the inspection, it can be referenced by the newly created message to which the message properties and the message headers are also copied, which results in an exact clone of the original message:</span></span>  
  
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
  
## <a name="adding-an-operation-selector-to-a-service"></a><span data-ttu-id="06ba2-118">Přidání selektor operace služby</span><span class="sxs-lookup"><span data-stu-id="06ba2-118">Adding an Operation Selector to a Service</span></span>  
 <span data-ttu-id="06ba2-119">Selektory operace odesílání služby jsou rozšíření pro [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dispečera.</span><span class="sxs-lookup"><span data-stu-id="06ba2-119">Service dispatch operation selectors are extensions to the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dispatcher.</span></span> <span data-ttu-id="06ba2-120">Pro výběr metody zpětného volání kanál duplexní kontrakty, existují také selektory operace klienta, které fungují velmi podobně, jako jsou zde popsané selektory operace odesílání, ale které nejsou výslovně zahrnuty v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="06ba2-120">For selecting methods on the callback channel of duplex contracts, there are also client operation selectors, which work very much like the dispatch operation selectors described here, but which are not explicitly covered in this sample.</span></span>  
  
 <span data-ttu-id="06ba2-121">Jako většina rozšíření model služeb jsou selektory operace odesílání přidány do dispečera pomocí chování.</span><span class="sxs-lookup"><span data-stu-id="06ba2-121">Like most service model extensions, dispatch operation selectors are added to the dispatcher using behaviors.</span></span> <span data-ttu-id="06ba2-122">A *chování* je objekt konfigurace, která přidá jeden nebo více rozšíření odesílání runtime (nebo modul runtime klienta) nebo v opačném případě se změní jeho nastavení.</span><span class="sxs-lookup"><span data-stu-id="06ba2-122">A *behavior* is a configuration object, which either adds one or more extensions to the dispatch runtime (or to the client runtime) or otherwise changes its settings.</span></span>  
  
 <span data-ttu-id="06ba2-123">Vzhledem k tomu, že selektory operace oboru kontrakt, příslušné chování k implementaci tady je <xref:System.ServiceModel.Description.IContractBehavior>.</span><span class="sxs-lookup"><span data-stu-id="06ba2-123">Because operation selectors have contract scope, the appropriate behavior to implement here is the <xref:System.ServiceModel.Description.IContractBehavior>.</span></span> <span data-ttu-id="06ba2-124">Protože rozhraní je implementováno na <xref:System.Attribute> odvozené třídy jak je znázorněno v následujícím kódu, chování deklarativně přidáním jakékoli servisní smlouvou.</span><span class="sxs-lookup"><span data-stu-id="06ba2-124">Because the interface is implemented on a <xref:System.Attribute> derived class as shown in the following code, the behavior can be declaratively added to any service contract.</span></span> <span data-ttu-id="06ba2-125">Vždy, když <xref:System.ServiceModel.ServiceHost> je otevřen a odesílání runtime vychází, všechny chování nalezena jako atributy na smlouvy, operace a implementací služby nebo jako element v konfiguraci služby se automaticky přidá a následně se zobrazí výzva k přispívat rozšíření nebo změnit výchozí konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="06ba2-125">Whenever a <xref:System.ServiceModel.ServiceHost> is opened and the dispatch runtime is built, all behaviors found either as attributes on contracts, operations, and service implementations or as element in the service configuration are automatically added and subsequently asked to contribute extensions or modify the default configuration.</span></span>  
  
 <span data-ttu-id="06ba2-126">Jako stručný výtah následující výpis kódu se zobrazí pouze implementace metody <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, který ovlivňuje změny konfigurace pro dispečera v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="06ba2-126">For brevity, the following code excerpt only shows the implementation of the method <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, which effects the configuration changes for the dispatcher in this sample.</span></span> <span data-ttu-id="06ba2-127">Jiné metody nezobrazují, protože vracejí volajícímu bez jakékoli pracuje.</span><span class="sxs-lookup"><span data-stu-id="06ba2-127">The other methods are not shown because they return to the caller without doing any work.</span></span>  
  
```  
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)   
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 <span data-ttu-id="06ba2-128">Nejdřív <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementace nastaví slovník vyhledávání pro selektor operace podle iterování přes <xref:System.ServiceModel.Description.OperationDescription> elementů v koncový bod služby <xref:System.ServiceModel.Description.ContractDescription>.</span><span class="sxs-lookup"><span data-stu-id="06ba2-128">First, the <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementation sets up the lookup dictionary for the operation selector by iterating over the <xref:System.ServiceModel.Description.OperationDescription> elements in the service endpoint's <xref:System.ServiceModel.Description.ContractDescription>.</span></span> <span data-ttu-id="06ba2-129">Potom se každý popis operace prozkoumá přítomnost `DispatchBodyElementAttribute` chování, provádění <xref:System.ServiceModel.Description.IOperationBehavior> , je také definován v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="06ba2-129">Then, each operation description is inspected for the presence of the `DispatchBodyElementAttribute` behavior, an implementation of <xref:System.ServiceModel.Description.IOperationBehavior> that is also defined in this sample.</span></span> <span data-ttu-id="06ba2-130">Když je tato třída také chování, je pasivní a není aktivně přispívat změny konfigurace modulu runtime odesílání.</span><span class="sxs-lookup"><span data-stu-id="06ba2-130">While this class is also a behavior, it is passive and does not actively contribute any configuration changes to the dispatch runtime.</span></span> <span data-ttu-id="06ba2-131">Všechny její metody vrátí volajícímu bez nutnosti převádět všechny akce.</span><span class="sxs-lookup"><span data-stu-id="06ba2-131">All of its methods return to the caller without taking any actions.</span></span> <span data-ttu-id="06ba2-132">Operace chování existuje pouze tak, aby byla metadata potřebná pro nové odesílání mechanismus, konkrétně kvalifikovaný název prvku body na jejichž výskyt operace je vybrána, může být spojen s příslušnými operacemi.</span><span class="sxs-lookup"><span data-stu-id="06ba2-132">The operation behavior only exists so that the metadata required for the new dispatch mechanism, namely the qualified name of the body element on whose occurrence an operation is selected, can be associated with the respective operations.</span></span>  
  
 <span data-ttu-id="06ba2-133">Pokud je nalezen takové chování, dvojici hodnota vytvořené z XML úplný název (`QName` vlastnosti) a název operace (`Name` vlastnost) se přidá do slovníku.</span><span class="sxs-lookup"><span data-stu-id="06ba2-133">If such a behavior is found, a value pair created from the XML qualified name (`QName` property) and the operation name (`Name` property) is added to the dictionary.</span></span>  
  
 <span data-ttu-id="06ba2-134">Po zaplnění slovníku, a nové `DispatchByBodyElementOperationSelector` je vytvořená pomocí těchto informací a nastavena jako selektor operace odesílání modulu runtime:</span><span class="sxs-lookup"><span data-stu-id="06ba2-134">Once the dictionary is populated, a new `DispatchByBodyElementOperationSelector` is constructed with this information and set as the operation selector of the dispatch runtime:</span></span>  
  
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
  
## <a name="implementing-the-service"></a><span data-ttu-id="06ba2-135">Implementace služby</span><span class="sxs-lookup"><span data-stu-id="06ba2-135">Implementing the Service</span></span>  
 <span data-ttu-id="06ba2-136">Chování implementována v této ukázce přímo ovlivňuje jak přenosu interpretovat a zpráv odeslaných, což je funkce kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="06ba2-136">The behavior implemented in this sample directly affects how messages from the wire are interpreted and dispatched, which is a function of the service contract.</span></span> <span data-ttu-id="06ba2-137">Chování v důsledku toho musí deklarovat na úrovni kontraktu služby v implementaci žádné služby, který se tedy rozhodne použít ho.</span><span class="sxs-lookup"><span data-stu-id="06ba2-137">Consequently, the behavior should be declared on the service contract level in any service implementation that chooses to use it.</span></span>  
  
 <span data-ttu-id="06ba2-138">Službu ukázkový projekt se vztahuje `DispatchByBodyElementBehaviorAttribute` smlouvy chování `IDispatchedByBody` služby kontrakt a štítky z těchto dvou operací `OperationForBodyA()` a `OperationForBodyB()` s `DispatchBodyElementAttribute` operaci chování.</span><span class="sxs-lookup"><span data-stu-id="06ba2-138">The sample project service applies the `DispatchByBodyElementBehaviorAttribute` contract behavior to the `IDispatchedByBody` service contract and labels each of the two operations `OperationForBodyA()` and `OperationForBodyB()` with a `DispatchBodyElementAttribute` operation behavior.</span></span> <span data-ttu-id="06ba2-139">Po otevření hostitele služby pro službu, která implementuje tento kontrakt tato metadata převzata Tvůrce dispečera jak bylo popsáno dříve.</span><span class="sxs-lookup"><span data-stu-id="06ba2-139">When a service host for a service that implements this contract is opened, this metadata is picked up by the dispatcher builder as previously described.</span></span>  
  
 <span data-ttu-id="06ba2-140">Protože selektor operace odešle zprávu výhradně podle elementu těla zprávy a ignoruje "Action", je třeba, aby říct modul runtime není zkontroluje hlavičky "Action" na vrácený odpovědi přiřazením zástupný znak "\*" k `ReplyAction` vlastnost <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="06ba2-140">Because the operation selector dispatches solely based on the message body element and ignores the "Action", it is required to tell the runtime not to check the "Action" header on the returned replies by assigning the wildcard "\*" to the `ReplyAction` property of <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="06ba2-141">Kromě toho je potřeba mít výchozí operaci, která má vlastnost "Action" nastavená na zástupný znak "\*".</span><span class="sxs-lookup"><span data-stu-id="06ba2-141">Furthermore, it is required to have a default operation that has the "Action" property set to the wildcard "\*".</span></span> <span data-ttu-id="06ba2-142">Výchozí operaci přijímá všechny zprávy, které nelze odeslat a nemá `DispatchBodyElementAttribute`:</span><span class="sxs-lookup"><span data-stu-id="06ba2-142">The default operation receives all messages which cannot be dispatched and does not have a `DispatchBodyElementAttribute`:</span></span>  
  
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
  
 <span data-ttu-id="06ba2-143">Implementace služby ukázka je jednoduchá.</span><span class="sxs-lookup"><span data-stu-id="06ba2-143">The sample service implementation is straightforward.</span></span> <span data-ttu-id="06ba2-144">EVERY – metoda zabalí přijatou zprávu do zprávu odpovědi a vrátí ji zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="06ba2-144">Every method wraps the received message into a reply message and echoes it back to the client.</span></span>  
  
## <a name="running-and-building-the-sample"></a><span data-ttu-id="06ba2-145">Spuštění a sestavování vzorku</span><span class="sxs-lookup"><span data-stu-id="06ba2-145">Running and Building the Sample</span></span>  
 <span data-ttu-id="06ba2-146">Při spuštění vzorového obsah textu odpovědi operace se zobrazují v okně konzoly klienta podobné výstupu v následujícím (formátovaný).</span><span class="sxs-lookup"><span data-stu-id="06ba2-146">When you run the sample, the body content of the operation responses are displayed in the client console window similar to the following (formatted) output.</span></span>  
  
 <span data-ttu-id="06ba2-147">Klient odešle tři zprávy do služby jehož obsahu je s názvem elementu těla `bodyA`, `bodyB`, a `bodyX`, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="06ba2-147">The client sends three messages to the service whose body content element is named `bodyA`, `bodyB`, and `bodyX`, respectively.</span></span> <span data-ttu-id="06ba2-148">Jak může být odložen z předchozí popis a kontrakt služby zobrazí, příchozích zpráv s `bodyA` element odeslaných `OperationForBodyA()` metoda.</span><span class="sxs-lookup"><span data-stu-id="06ba2-148">As can be deferred from the previous description and the service contract shown, the incoming message with the `bodyA` element is dispatched to the `OperationForBodyA()` method.</span></span> <span data-ttu-id="06ba2-149">Vzhledem k tomu, že neexistuje žádné explicitní odesílání cíl pro zprávu s `bodyX` body element je zpráva odeslána na `DefaultOperation()`.</span><span class="sxs-lookup"><span data-stu-id="06ba2-149">Because there is no explicit dispatch target for the message with the `bodyX` body element, the message is dispatched to the `DefaultOperation()`.</span></span> <span data-ttu-id="06ba2-150">Každý operací služby zabalí obsah přijaté zprávy do elementu specifické pro metodu a vrátí, která se provádí korelaci vstup a výstup zprávy jasně pro tuto ukázku:</span><span class="sxs-lookup"><span data-stu-id="06ba2-150">Each of the service operations wraps the received message body into an element specific to the method and returns it, which is done to correlate input and output messages clearly for this sample:</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="06ba2-151">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="06ba2-151">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="06ba2-152">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="06ba2-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="06ba2-153">Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="06ba2-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="06ba2-154">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="06ba2-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="06ba2-155">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="06ba2-155">The samples may already be installed on your machine.</span></span> <span data-ttu-id="06ba2-156">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="06ba2-156">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="06ba2-157">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="06ba2-157">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="06ba2-158">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="06ba2-158">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
  
## <a name="see-also"></a><span data-ttu-id="06ba2-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="06ba2-159">See Also</span></span>
