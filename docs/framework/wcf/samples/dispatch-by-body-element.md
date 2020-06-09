---
title: Přiřazování zpráv metodám podle elementu těla
ms.date: 03/30/2017
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
ms.openlocfilehash: 19913cdaa47d766f62a313e216a653ac69633a99
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594696"
---
# <a name="dispatch-by-body-element"></a><span data-ttu-id="58374-102">Přiřazování zpráv metodám podle elementu těla</span><span class="sxs-lookup"><span data-stu-id="58374-102">Dispatch by Body Element</span></span>
<span data-ttu-id="58374-103">Tato ukázka předvádí, jak implementovat alternativní algoritmus pro přiřazování příchozích zpráv do operací.</span><span class="sxs-lookup"><span data-stu-id="58374-103">This sample demonstrates how to implement an alternate algorithm for assigning incoming messages to operations.</span></span>  
  
 <span data-ttu-id="58374-104">Ve výchozím nastavení vybírá dispečer Service Model vhodnou metodu zpracování pro příchozí zprávu na základě hlavičky akce WS-Addressing zprávy nebo ekvivalentní informace v žádosti HTTP SOAP.</span><span class="sxs-lookup"><span data-stu-id="58374-104">By default, the service model dispatcher selects the appropriate handling method for an incoming message based on the message's WS-Addressing "Action" header or the equivalent information in the HTTP SOAP request.</span></span>  
  
 <span data-ttu-id="58374-105">Některé zásobníky webových služeb SOAP 1,1, které nedodržují pokyny pro základní 1,1 Profil WS-I, neodesílají zprávy na základě identifikátoru URI akce, ale na základě XML kvalifikovaného názvu prvního prvku uvnitř těla protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="58374-105">Some SOAP 1.1 Web services stacks that do not follow the WS-I Basic Profile 1.1 guidelines do not dispatch messages based on the Action URI, but rather based on the XML qualified name of the first element inside the SOAP body.</span></span> <span data-ttu-id="58374-106">Podobně může Klientská strana těchto zásobníků odesílat zprávy s prázdnou hlavičkou HTTP SoapAction, která byla povolena specifikací protokolu SOAP 1,1.</span><span class="sxs-lookup"><span data-stu-id="58374-106">Likewise, the client side of these stacks might send messages with an empty or arbitrary HTTP SoapAction header, which was permitted by the SOAP 1.1 specification.</span></span>  
  
 <span data-ttu-id="58374-107">Chcete-li změnit způsob, jakým jsou odesílány zprávy do metod, ukázka implementuje <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> rozhraní rozšiřitelnosti na `DispatchByBodyElementOperationSelector` .</span><span class="sxs-lookup"><span data-stu-id="58374-107">To change the way messages are dispatched to methods, the sample implements the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> extensibility interface on the `DispatchByBodyElementOperationSelector`.</span></span> <span data-ttu-id="58374-108">Tato třída vybere operace na základě prvního prvku textu zprávy.</span><span class="sxs-lookup"><span data-stu-id="58374-108">This class selects operations based on the first element of the message body.</span></span>  
  
 <span data-ttu-id="58374-109">Konstruktor třídy očekává slovník naplněný páry `XmlQualifiedName` a řetězce, přičemž kvalifikované názvy označují název prvního podřízeného textu protokolu SOAP a řetězce indikují název vyhovující operace.</span><span class="sxs-lookup"><span data-stu-id="58374-109">The class constructor expects a dictionary populated with pairs of `XmlQualifiedName` and strings, whereby the qualified names indicate the name of the first child of the SOAP body and the strings indicate the matching operation name.</span></span> <span data-ttu-id="58374-110">`defaultOperationName`Je název operace, která přijímá všechny zprávy, které nelze spárovat s tímto slovníkem:</span><span class="sxs-lookup"><span data-stu-id="58374-110">The `defaultOperationName` is the name of the operation that receives all messages that cannot be matched against this dictionary:</span></span>  
  
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
  
 <span data-ttu-id="58374-111"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector>implementace jsou velmi jednoduché k sestavení, protože rozhraní obsahuje pouze jednu metodu: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> .</span><span class="sxs-lookup"><span data-stu-id="58374-111"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementations are very straightforward to build as there is only one method on the interface: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>.</span></span> <span data-ttu-id="58374-112">Úkolem této metody je zkontrolovat příchozí zprávu a vrátit řetězec, který se rovná názvu metody kontraktu služby pro aktuální koncový bod.</span><span class="sxs-lookup"><span data-stu-id="58374-112">The job of this method is to inspect an incoming message and to return a string that equals the name of a method on the service contract for the current endpoint.</span></span>  
  
 <span data-ttu-id="58374-113">V této ukázce selektor operace získá <xref:System.Xml.XmlDictionaryReader> text pro tělo příchozí zprávy pomocí <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> .</span><span class="sxs-lookup"><span data-stu-id="58374-113">In this sample, the operation selector acquires an <xref:System.Xml.XmlDictionaryReader> for the incoming message's body using <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>.</span></span> <span data-ttu-id="58374-114">Tato metoda již umisťuje čtecí modul na první podřízený text zprávy tak, aby bylo možné získat název aktuálního prvku a identifikátor URI oboru názvů a zkombinovat je do objektu `XmlQualifiedName` , který je pak použit pro vyhledání odpovídající operace ze slovníku uloženého selektor operace.</span><span class="sxs-lookup"><span data-stu-id="58374-114">This method already positions the reader on the first child of the message's body so that it is sufficient to get the current element's name and namespace URI and combine them into an `XmlQualifiedName` that is then used for looking up the corresponding operation from the dictionary held by the operation selector.</span></span>  
  
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
  
 <span data-ttu-id="58374-115">Přístup k tělo zprávy pomocí <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> nebo libovolné jiné metody, která poskytuje přístup k obsahu obsahu zprávy způsobí, že zpráva bude označena jako "přečtená", což znamená, že zpráva není pro jakékoli další zpracování platná.</span><span class="sxs-lookup"><span data-stu-id="58374-115">Accessing the message body with <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> or any of the other methods that provide access to the message's body content causes the message to be marked as "read", which means that the message is invalid for any further processing.</span></span> <span data-ttu-id="58374-116">Proto selektor operací vytvoří kopii příchozí zprávy s metodou zobrazenou v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="58374-116">Therefore, the operation selector creates a copy of the incoming message with the method shown in the following code.</span></span> <span data-ttu-id="58374-117">Vzhledem k tomu, že se pozice čtecího zařízení během kontroly nezměnila, může být odkazováno nově vytvořenou zprávou, na kterou jsou také zkopírovány vlastnosti zprávy a záhlaví zpráv, což má za následek přesný klon původní zprávy:</span><span class="sxs-lookup"><span data-stu-id="58374-117">Because the reader's position has not been changed during the inspection, it can be referenced by the newly created message to which the message properties and the message headers are also copied, which results in an exact clone of the original message:</span></span>  
  
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
  
## <a name="adding-an-operation-selector-to-a-service"></a><span data-ttu-id="58374-118">Přidání voliče operace do služby</span><span class="sxs-lookup"><span data-stu-id="58374-118">Adding an Operation Selector to a Service</span></span>  
 <span data-ttu-id="58374-119">Selektory operací odeslání služby jsou rozšířením dispečera Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="58374-119">Service dispatch operation selectors are extensions to the Windows Communication Foundation (WCF) dispatcher.</span></span> <span data-ttu-id="58374-120">Pro výběr metod na kanálu zpětného volání u kontraktů s překrytím jsou k dispozici také selektory operací klienta, které fungují velmi podobně jako selektory operací odeslání popsané zde, ale nejsou výslovně popsány v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="58374-120">For selecting methods on the callback channel of duplex contracts, there are also client operation selectors, which work very much like the dispatch operation selectors described here, but which are not explicitly covered in this sample.</span></span>  
  
 <span data-ttu-id="58374-121">Podobně jako u většiny rozšíření modelu služeb jsou selektory operací odeslání přidány do dispečera pomocí chování.</span><span class="sxs-lookup"><span data-stu-id="58374-121">Like most service model extensions, dispatch operation selectors are added to the dispatcher using behaviors.</span></span> <span data-ttu-id="58374-122">*Chování* je objekt konfigurace, který buď přidá jednu nebo více rozšíření do modulu runtime odeslání (nebo do modulu runtime klienta), nebo jinak změní jeho nastavení.</span><span class="sxs-lookup"><span data-stu-id="58374-122">A *behavior* is a configuration object, which either adds one or more extensions to the dispatch runtime (or to the client runtime) or otherwise changes its settings.</span></span>  
  
 <span data-ttu-id="58374-123">Vzhledem k tomu, že selektory operací mají obor kontraktu, příslušné chování, které se má implementovat, je <xref:System.ServiceModel.Description.IContractBehavior> .</span><span class="sxs-lookup"><span data-stu-id="58374-123">Because operation selectors have contract scope, the appropriate behavior to implement here is the <xref:System.ServiceModel.Description.IContractBehavior>.</span></span> <span data-ttu-id="58374-124">Protože rozhraní je implementováno pro <xref:System.Attribute> odvozenou třídu, jak je znázorněno v následujícím kódu, může být chování deklarativně přidáno do jakékoli kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="58374-124">Because the interface is implemented on a <xref:System.Attribute> derived class as shown in the following code, the behavior can be declaratively added to any service contract.</span></span> <span data-ttu-id="58374-125">Pokaždé <xref:System.ServiceModel.ServiceHost> , když se otevře a spustí se modul runtime Dispatch, všechna chování zjištěná buď jako atributy kontraktů, operací a implementací služby, nebo jako element v konfiguraci služby jsou automaticky přidány a následně vyzvány k rozšířením aplikace Contribute nebo úpravám výchozí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="58374-125">Whenever a <xref:System.ServiceModel.ServiceHost> is opened and the dispatch runtime is built, all behaviors found either as attributes on contracts, operations, and service implementations or as element in the service configuration are automatically added and subsequently asked to contribute extensions or modify the default configuration.</span></span>  
  
 <span data-ttu-id="58374-126">V případě zkrácení následující úryvek kódu zobrazuje pouze implementaci metody <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> , která ovlivňuje změny konfigurace dispečera v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="58374-126">For brevity, the following code excerpt only shows the implementation of the method <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, which effects the configuration changes for the dispatcher in this sample.</span></span> <span data-ttu-id="58374-127">Jiné metody nejsou zobrazeny, protože se vrací volajícímu bez provedení jakékoli práce.</span><span class="sxs-lookup"><span data-stu-id="58374-127">The other methods are not shown because they return to the caller without doing any work.</span></span>  
  
```csharp
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 <span data-ttu-id="58374-128">Nejprve <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementace nastaví slovník vyhledávání pro selektor operací tak, že provede iteraci <xref:System.ServiceModel.Description.OperationDescription> prvků v rámci koncového bodu služby <xref:System.ServiceModel.Description.ContractDescription> .</span><span class="sxs-lookup"><span data-stu-id="58374-128">First, the <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementation sets up the lookup dictionary for the operation selector by iterating over the <xref:System.ServiceModel.Description.OperationDescription> elements in the service endpoint's <xref:System.ServiceModel.Description.ContractDescription>.</span></span> <span data-ttu-id="58374-129">Pak je u každého popisu operace prověřena přítomnost `DispatchBodyElementAttribute` chování, implementace <xref:System.ServiceModel.Description.IOperationBehavior> , která je také definována v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="58374-129">Then, each operation description is inspected for the presence of the `DispatchBodyElementAttribute` behavior, an implementation of <xref:System.ServiceModel.Description.IOperationBehavior> that is also defined in this sample.</span></span> <span data-ttu-id="58374-130">I když je tato třída také chování, je pasivní a neaktivně nepřispívá ke změnám konfigurace modulu runtime odeslání.</span><span class="sxs-lookup"><span data-stu-id="58374-130">While this class is also a behavior, it is passive and does not actively contribute any configuration changes to the dispatch runtime.</span></span> <span data-ttu-id="58374-131">Všechny jeho metody se vrátí volajícímu bez provedení jakýchkoli akcí.</span><span class="sxs-lookup"><span data-stu-id="58374-131">All of its methods return to the caller without taking any actions.</span></span> <span data-ttu-id="58374-132">Chování operace existuje pouze proto, že metadata požadovaná pro nový mechanismus odeslání, Jmenovitý název prvku tělo, u jehož výskytu operace je vybrána, lze přidružit k příslušným operacím.</span><span class="sxs-lookup"><span data-stu-id="58374-132">The operation behavior only exists so that the metadata required for the new dispatch mechanism, namely the qualified name of the body element on whose occurrence an operation is selected, can be associated with the respective operations.</span></span>  
  
 <span data-ttu-id="58374-133">Pokud je takové chování nalezeno, je do slovníku přidána dvojice hodnot vytvořená z kvalifikovaného názvu XML ( `QName` vlastnost) a název operace ( `Name` vlastnost).</span><span class="sxs-lookup"><span data-stu-id="58374-133">If such a behavior is found, a value pair created from the XML qualified name (`QName` property) and the operation name (`Name` property) is added to the dictionary.</span></span>  
  
 <span data-ttu-id="58374-134">Po naplnění slovníku se nový vytvoří `DispatchByBodyElementOperationSelector` s těmito informacemi a nastaví se jako selektor operace modulu runtime pro odesílání:</span><span class="sxs-lookup"><span data-stu-id="58374-134">Once the dictionary is populated, a new `DispatchByBodyElementOperationSelector` is constructed with this information and set as the operation selector of the dispatch runtime:</span></span>  
  
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
  
## <a name="implementing-the-service"></a><span data-ttu-id="58374-135">Implementace služby</span><span class="sxs-lookup"><span data-stu-id="58374-135">Implementing the Service</span></span>  
 <span data-ttu-id="58374-136">Chování implementované v této ukázce přímo ovlivňuje způsob interpretace a odeslání zpráv z tohoto drátu, což je funkce kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="58374-136">The behavior implemented in this sample directly affects how messages from the wire are interpreted and dispatched, which is a function of the service contract.</span></span> <span data-ttu-id="58374-137">V důsledku toho by mělo být chování deklarováno na úrovni kontraktu služby v jakékoli implementaci služby, kterou se rozhodnete použít.</span><span class="sxs-lookup"><span data-stu-id="58374-137">Consequently, the behavior should be declared on the service contract level in any service implementation that chooses to use it.</span></span>  
  
 <span data-ttu-id="58374-138">Ukázková služba projektu používá `DispatchByBodyElementBehaviorAttribute` chování kontraktu pro `IDispatchedByBody` kontrakt služby a popisky každé z těchto dvou operací `OperationForBodyA()` a `OperationForBodyB()` s `DispatchBodyElementAttribute` chováním operace.</span><span class="sxs-lookup"><span data-stu-id="58374-138">The sample project service applies the `DispatchByBodyElementBehaviorAttribute` contract behavior to the `IDispatchedByBody` service contract and labels each of the two operations `OperationForBodyA()` and `OperationForBodyB()` with a `DispatchBodyElementAttribute` operation behavior.</span></span> <span data-ttu-id="58374-139">Po otevření hostitele služby pro službu, která implementuje tuto smlouvu, je tato metadata převzata tvůrcem dispečera, jak je popsáno výše.</span><span class="sxs-lookup"><span data-stu-id="58374-139">When a service host for a service that implements this contract is opened, this metadata is picked up by the dispatcher builder as previously described.</span></span>  
  
 <span data-ttu-id="58374-140">Vzhledem k tomu, že se selektor operace odesílá výhradně na základě prvku těla zprávy a ignoruje "Action", je nutné sdělit modulu runtime, aby nekontroloval hlavičku "Action" na vrácených odpovědí přiřazením zástupného znaku "\*" k `ReplyAction` vlastnosti <xref:System.ServiceModel.OperationContractAttribute> .</span><span class="sxs-lookup"><span data-stu-id="58374-140">Because the operation selector dispatches solely based on the message body element and ignores the "Action", it is required to tell the runtime not to check the "Action" header on the returned replies by assigning the wildcard "\*" to the `ReplyAction` property of <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="58374-141">Kromě toho je nutné mít výchozí operaci, která má vlastnost "Action" nastavenou na zástupný znak " \* ".</span><span class="sxs-lookup"><span data-stu-id="58374-141">Furthermore, it is required to have a default operation that has the "Action" property set to the wildcard "\*".</span></span> <span data-ttu-id="58374-142">Výchozí operace přijímá všechny zprávy, které nelze odeslat a nemá `DispatchBodyElementAttribute` :</span><span class="sxs-lookup"><span data-stu-id="58374-142">The default operation receives all messages which cannot be dispatched and does not have a `DispatchBodyElementAttribute`:</span></span>  
  
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
  
 <span data-ttu-id="58374-143">Implementace ukázkové služby je jednoduchá.</span><span class="sxs-lookup"><span data-stu-id="58374-143">The sample service implementation is straightforward.</span></span> <span data-ttu-id="58374-144">Každá metoda zabalí přijatou zprávu do zprávy s odpovědí a vrátí ji zpět klientovi.</span><span class="sxs-lookup"><span data-stu-id="58374-144">Every method wraps the received message into a reply message and echoes it back to the client.</span></span>  
  
## <a name="running-and-building-the-sample"></a><span data-ttu-id="58374-145">Spuštění a sestavování ukázky</span><span class="sxs-lookup"><span data-stu-id="58374-145">Running and Building the Sample</span></span>  
 <span data-ttu-id="58374-146">Když spustíte ukázku, v okně konzoly klienta se zobrazí obsah textu odpovědí operace, který bude podobný následujícímu (formátovanému) výstupu.</span><span class="sxs-lookup"><span data-stu-id="58374-146">When you run the sample, the body content of the operation responses are displayed in the client console window similar to the following (formatted) output.</span></span>  
  
 <span data-ttu-id="58374-147">Klient pošle službě tři zprávy, jejichž tělo elementu obsahu se jmenuje `bodyA` , `bodyB` a v `bodyX` uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="58374-147">The client sends three messages to the service whose body content element is named `bodyA`, `bodyB`, and `bodyX`, respectively.</span></span> <span data-ttu-id="58374-148">Jak je možné odvodit z předchozího popisu a uvedeného kontraktu služby, příchozí zpráva s `bodyA` prvkem je odeslána do `OperationForBodyA()` metody.</span><span class="sxs-lookup"><span data-stu-id="58374-148">As can be deferred from the previous description and the service contract shown, the incoming message with the `bodyA` element is dispatched to the `OperationForBodyA()` method.</span></span> <span data-ttu-id="58374-149">Vzhledem k tomu, že není k dispozici žádný explicitní cíl odeslání zprávy s `bodyX` elementem body, zpráva je odeslána na `DefaultOperation()` .</span><span class="sxs-lookup"><span data-stu-id="58374-149">Because there is no explicit dispatch target for the message with the `bodyX` body element, the message is dispatched to the `DefaultOperation()`.</span></span> <span data-ttu-id="58374-150">Každá operace služby zabalí přijatý text zprávy do prvku specifického pro metodu a vrátí jej, který je pro účely této ukázky možné jednoznačně sladit vstupní a výstupní zprávy:</span><span class="sxs-lookup"><span data-stu-id="58374-150">Each of the service operations wraps the received message body into an element specific to the method and returns it, which is done to correlate input and output messages clearly for this sample:</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="58374-151">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="58374-151">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="58374-152">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="58374-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="58374-153">Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="58374-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="58374-154">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="58374-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="58374-155">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="58374-155">The samples may already be installed on your machine.</span></span> <span data-ttu-id="58374-156">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="58374-156">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="58374-157">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="58374-157">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="58374-158">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="58374-158">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
