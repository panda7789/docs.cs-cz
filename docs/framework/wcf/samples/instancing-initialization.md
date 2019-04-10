---
title: Inicializace vytváření instancí
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: 1414908025416f4cdd6e5b51c052799631ab52cd
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322183"
---
# <a name="instancing-initialization"></a><span data-ttu-id="b48e4-102">Inicializace vytváření instancí</span><span class="sxs-lookup"><span data-stu-id="b48e4-102">Instancing Initialization</span></span>
<span data-ttu-id="b48e4-103">Tento příklad rozšiřuje [Sdužování](../../../../docs/framework/wcf/samples/pooling.md) ukázka definováním rozhraní, `IObjectControl`, který přizpůsobí inicializace objektu aktivace a deaktivace.</span><span class="sxs-lookup"><span data-stu-id="b48e4-103">This sample extends the [Pooling](../../../../docs/framework/wcf/samples/pooling.md) sample by defining an interface, `IObjectControl`, which customizes the initialization of an object by activating and deactivating it.</span></span> <span data-ttu-id="b48e4-104">Klient volá metody, které vracejí objekt do fondu a objekt, který nesmí vracet do fondu.</span><span class="sxs-lookup"><span data-stu-id="b48e4-104">The client invokes methods that return the object to the pool and that do not return the object to the pool.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b48e4-105">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="b48e4-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="extensibility-points"></a><span data-ttu-id="b48e4-106">Body rozšiřitelnosti</span><span class="sxs-lookup"><span data-stu-id="b48e4-106">Extensibility Points</span></span>  
 <span data-ttu-id="b48e4-107">Prvním krokem při vytváření rozšíření pro Windows Communication Foundation (WCF) je rozhodnout bodu rozšiřitelnosti pro použití.</span><span class="sxs-lookup"><span data-stu-id="b48e4-107">The first step in creating a Windows Communication Foundation (WCF) extension is to decide the extensibility point to use.</span></span> <span data-ttu-id="b48e4-108">Ve službě WCF termín *EndpointDispatcher* odkazuje na komponentu za běhu pro převod příchozích zpráv do volání metod na uživatele služby a pro převod vrácené hodnoty z této metody na odchozí zprávy .</span><span class="sxs-lookup"><span data-stu-id="b48e4-108">In WCF, the term *EndpointDispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="b48e4-109">Služba WCF vytvoří EndpointDispatcher pro každý koncový bod.</span><span class="sxs-lookup"><span data-stu-id="b48e4-109">A WCF service creates an EndpointDispatcher for each endpoint.</span></span>  
  
 <span data-ttu-id="b48e4-110">Modul nabízí používání rozšíření koncového bodu rozsah (pro všechny zprávy přijatých nebo odeslaných službou) <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> třídy.</span><span class="sxs-lookup"><span data-stu-id="b48e4-110">The EndpointDispatcher offers endpoint scope (for all messages received or sent by the service) extensibility using the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> class.</span></span> <span data-ttu-id="b48e4-111">Tato třída umožňuje přizpůsobit různé vlastnosti ovládacího prvku chování EndpointDispatcher.</span><span class="sxs-lookup"><span data-stu-id="b48e4-111">This class allows you to customize various properties that control the behavior of the EndpointDispatcher.</span></span> <span data-ttu-id="b48e4-112">Tato ukázka se zaměřuje na <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> vlastnost, která odkazuje na objekt, který poskytuje instance třídy service.</span><span class="sxs-lookup"><span data-stu-id="b48e4-112">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="iinstanceprovider"></a><span data-ttu-id="b48e4-113">IInstanceProvider</span><span class="sxs-lookup"><span data-stu-id="b48e4-113">IInstanceProvider</span></span>  
 <span data-ttu-id="b48e4-114">Ve službě WCF, vytvoří modul instancí třídy služby pomocí instance zprostředkovatele, který implementuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b48e4-114">In WCF, the EndpointDispatcher creates instances of a service class by using an instance provider that implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="b48e4-115">Toto rozhraní má jenom dvě metody:</span><span class="sxs-lookup"><span data-stu-id="b48e4-115">This interface has only two methods:</span></span>  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A><span data-ttu-id="b48e4-116">: Při přijetí e-mailu, odesílatel volání <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> metodu pro vytvoření instance třídy službu ke zpracování zprávy.</span><span class="sxs-lookup"><span data-stu-id="b48e4-116">: When a message arrives, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="b48e4-117">Četnost volání této metody se zakládá <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b48e4-117">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="b48e4-118">Například pokud <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> je nastavena na <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, zpracovat každou zprávu, která dorazí, tak se vytvoří novou instanci třídy služby <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> je volána při každém přijetí e-mailu.</span><span class="sxs-lookup"><span data-stu-id="b48e4-118">For example if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> is called whenever a message arrives.</span></span>  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A><span data-ttu-id="b48e4-119">: Pokud instance služby podaří zprávu zpracovat, zavolá modul <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b48e4-119">: When the service instance finishes processing the message, the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method.</span></span> <span data-ttu-id="b48e4-120">Stejně jako v <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> metoda, je určena Četnost volání této metody <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b48e4-120">As in the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="b48e4-121">Fond objektů</span><span class="sxs-lookup"><span data-stu-id="b48e4-121">The Object Pool</span></span>  
 <span data-ttu-id="b48e4-122">`ObjectPoolInstanceProvider` Třída obsahuje implementaci pro fondu objektů.</span><span class="sxs-lookup"><span data-stu-id="b48e4-122">The `ObjectPoolInstanceProvider` class contains the implementation for the object pool.</span></span> <span data-ttu-id="b48e4-123">Tato třída implementuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider> rozhraní pro interakci s vrstva modelu služby.</span><span class="sxs-lookup"><span data-stu-id="b48e4-123">This class implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface to interact with the service model layer.</span></span> <span data-ttu-id="b48e4-124">Když volá modul <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> metody, místo vytvoření nové instance, vlastní implementaci hledá existující objekt ve fondu v paměti.</span><span class="sxs-lookup"><span data-stu-id="b48e4-124">When the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="b48e4-125">Pokud je k dispozici, bude vrácen.</span><span class="sxs-lookup"><span data-stu-id="b48e4-125">If one is available, it is returned.</span></span> <span data-ttu-id="b48e4-126">V opačném případě `ObjectPoolInstanceProvider` kontroluje, zda `ActiveObjectsCount` vlastností (počet objektů vrácených z fondu) dosáhl maximální velikosti fondu.</span><span class="sxs-lookup"><span data-stu-id="b48e4-126">Otherwise, `ObjectPoolInstanceProvider` checks whether the `ActiveObjectsCount` property (number of objects returned from the pool) has reached the maximum pool size.</span></span> <span data-ttu-id="b48e4-127">Pokud ne, novou instanci se vytvoří a vrátit zpět volajícímu a `ActiveObjectsCount` se následně zvýší.</span><span class="sxs-lookup"><span data-stu-id="b48e4-127">If not, a new instance is created and returned to the caller and `ActiveObjectsCount` is subsequently incremented.</span></span> <span data-ttu-id="b48e4-128">Jinak požadavek na vytvoření objektů je zařadí do fronty pro nakonfigurovaného časového období.</span><span class="sxs-lookup"><span data-stu-id="b48e4-128">Otherwise an object creation request is queued for a configured period of time.</span></span> <span data-ttu-id="b48e4-129">Implementace `GetObjectFromThePool` je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="b48e4-129">The implementation for `GetObjectFromThePool` is shown in the following sample code.</span></span>  
  
```  
private object GetObjectFromThePool()  
{  
    bool didNotTimeout =   
       availableCount.WaitOne(creationTimeout, true);  
    if(didNotTimeout)  
    {  
         object obj = null;  
         lock (poolLock)  
        {  
             if (pool.Count != 0)  
             {  
                   obj = pool.Pop();  
                   activeObjectsCount++;  
             }  
             else if (pool.Count == 0)  
             {  
                   if (activeObjectsCount < maxPoolSize)  
                   {  
                        obj = CreateNewPoolObject();  
                        activeObjectsCount++;  
  
                        #if (DEBUG)  
                        WritePoolMessage(  
                             ResourceHelper.GetString("MsgNewObject"));  
                       #endif  
                   }                          
            }  
           idleTimer.Stop();  
      }  
     // Call the Activate method if possible.  
    if (obj is IObjectControl)  
   {  
         ((IObjectControl)obj).Activate();  
   }  
   return obj;  
}  
throw new TimeoutException(  
ResourceHelper.GetString("ExObjectCreationTimeout"));  
}  
```  
  
 <span data-ttu-id="b48e4-130">Vlastní `ReleaseInstance` implementace přidá vydané instanci zpět do fondu a sníží `ActiveObjectsCount` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b48e4-130">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="b48e4-131">Modul může tyto metody volat z různých vláken a proto synchronizaci přístupu k členům třídy úrovni v `ObjectPoolInstanceProvider` třída je povinné.</span><span class="sxs-lookup"><span data-stu-id="b48e4-131">The EndpointDispatcher can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolInstanceProvider` class is required.</span></span>  
  
```  
public void ReleaseInstance(InstanceContext instanceContext, object instance)  
{  
    lock (poolLock)  
    {  
        // Check whether the object can be pooled.   
        // Call the Deactivate method if possible.  
        if (instance is IObjectControl)  
        {  
            IObjectControl objectControl = (IObjectControl)instance;  
            objectControl.Deactivate();  
  
            if (objectControl.CanBePooled)  
            {  
                pool.Push(instance);  
  
                #if(DEBUG)  
                WritePoolMessage(  
                    ResourceHelper.GetString("MsgObjectPooled"));  
                #endif                          
            }  
            else  
            {  
                #if(DEBUG)  
                WritePoolMessage(  
                    ResourceHelper.GetString("MsgObjectWasNotPooled"));  
                #endif  
            }  
        }  
        else  
        {  
            pool.Push(instance);  
  
            #if(DEBUG)  
            WritePoolMessage(  
                ResourceHelper.GetString("MsgObjectPooled"));  
            #endif   
        }  
  
        activeObjectsCount--;  
  
        if (activeObjectsCount == 0)  
        {  
            idleTimer.Start();                       
        }  
    }  
  
    availableCount.Release(1);  
}  
```  
  
 <span data-ttu-id="b48e4-132">`ReleaseInstance` Poskytuje metody *vyčistit inicializace* funkce.</span><span class="sxs-lookup"><span data-stu-id="b48e4-132">The `ReleaseInstance` method provides a *clean up initialization* feature.</span></span> <span data-ttu-id="b48e4-133">Fondu obvykle udržuje minimální počet objektů, které po dobu životnosti fondu.</span><span class="sxs-lookup"><span data-stu-id="b48e4-133">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="b48e4-134">Může však být období nadměrnému využití, které vyžadují vytvoření další objekty ve fondu k dosažení maximální limit zadaný v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="b48e4-134">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="b48e4-135">Nakonec po fond bude méně aktivní těchto nadbytečné objektů se může stát další režii.</span><span class="sxs-lookup"><span data-stu-id="b48e4-135">Eventually when the pool becomes less active those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="b48e4-136">Proto když `activeObjectsCount` dosáhne nuly, je spuštěn nečinný časovače, který se aktivuje a provede vyčištění cyklu.</span><span class="sxs-lookup"><span data-stu-id="b48e4-136">Therefore when the `activeObjectsCount` reaches zero an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
```  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();   
}  
```  
  
 <span data-ttu-id="b48e4-137">Rozšíření modelu vrstvy se připojili pomocí následujícího chování:</span><span class="sxs-lookup"><span data-stu-id="b48e4-137">ServiceModel layer extensions are hooked up using the following behaviors:</span></span>  
  
-   <span data-ttu-id="b48e4-138">Chování služby: Tyto rutiny umožňují pro přizpůsobení celé služby modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="b48e4-138">Service Behaviors: These allow for the customization of the entire service runtime.</span></span>  
  
-   <span data-ttu-id="b48e4-139">Chování koncového bodu: Tyto rutiny umožňují pro přizpůsobení koncového bodu konkrétní služby, včetně EndpointDispatcher.</span><span class="sxs-lookup"><span data-stu-id="b48e4-139">Endpoint Behaviors: These allow for the customization of a particular service endpoint, including the EndpointDispatcher.</span></span>  
  
-   <span data-ttu-id="b48e4-140">Chování smlouvy: Tyto rutiny umožňují pro přizpůsobení buď <xref:System.ServiceModel.Dispatcher.ClientRuntime> nebo <xref:System.ServiceModel.Dispatcher.DispatchRuntime> třídy u klienta nebo služby v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="b48e4-140">Contract Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientRuntime> or <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client or the service respectively.</span></span>  
  
-   <span data-ttu-id="b48e4-141">Chování operace: Tyto rutiny umožňují pro přizpůsobení buď <xref:System.ServiceModel.Dispatcher.ClientOperation> nebo <xref:System.ServiceModel.Dispatcher.DispatchOperation> třídy u klienta nebo služby v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="b48e4-141">Operation Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientOperation> or <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes on the client or the service respectively.</span></span>  
  
 <span data-ttu-id="b48e4-142">Pro účely objekt sdružování rozšíření je možné vytvořit chování koncového bodu nebo chování služby.</span><span class="sxs-lookup"><span data-stu-id="b48e4-142">For the purpose of an object pooling extension, either an endpoint behavior or a service behavior can be created.</span></span> <span data-ttu-id="b48e4-143">V tomto příkladu používáme chování služby, která se vztahuje objekt sdružování schopnost každý koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="b48e4-143">In this example, we use a service behavior, which applies object pooling ability to every endpoint of the service.</span></span> <span data-ttu-id="b48e4-144">Chování služby jsou vytvořeny pomocí implementace <xref:System.ServiceModel.Description.IServiceBehavior> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b48e4-144">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="b48e4-145">Ujistěte se, ServiceModel používající vlastní chování několika způsoby:</span><span class="sxs-lookup"><span data-stu-id="b48e4-145">There are several ways to make the ServiceModel aware of the custom behaviors:</span></span>  
  
-   <span data-ttu-id="b48e4-146">Pomocí vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="b48e4-146">Using a custom attribute.</span></span>  
  
-   <span data-ttu-id="b48e4-147">Imperativně přidáním do kolekce chování popisu služby.</span><span class="sxs-lookup"><span data-stu-id="b48e4-147">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
-   <span data-ttu-id="b48e4-148">Rozšíření konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="b48e4-148">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="b48e4-149">Tato ukázka používá vlastní atribut.</span><span class="sxs-lookup"><span data-stu-id="b48e4-149">This sample uses a custom attribute.</span></span> <span data-ttu-id="b48e4-150">Když <xref:System.ServiceModel.ServiceHost> je vytvořen, zkontroluje atributy použité v definici služby typu a přidá do kolekce chování popis služby k dispozici chování.</span><span class="sxs-lookup"><span data-stu-id="b48e4-150">When the <xref:System.ServiceModel.ServiceHost> is constructed, it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="b48e4-151"><xref:System.ServiceModel.Description.IServiceBehavior> Rozhraní obsahuje tři metody: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>`,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>`,` a <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span><span class="sxs-lookup"><span data-stu-id="b48e4-151">The <xref:System.ServiceModel.Description.IServiceBehavior> interface has three methods: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>`,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>`,` and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="b48e4-152">Tyto metody jsou volány aplikací WCF při <xref:System.ServiceModel.ServiceHost> je inicializována.</span><span class="sxs-lookup"><span data-stu-id="b48e4-152">These methods are called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> <span data-ttu-id="b48e4-153">je volána. To umožňuje službě zkontroloval za účelem nalezení nekonzistencí.</span><span class="sxs-lookup"><span data-stu-id="b48e4-153">is called first; it allows the service to be inspected for inconsistencies.</span></span> <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> <span data-ttu-id="b48e4-154">je volána vedle; Tato metoda je potřeba jenom velmi pokročilých scénářů.</span><span class="sxs-lookup"><span data-stu-id="b48e4-154">is called next; this method is only required in very advanced scenarios.</span></span> <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> <span data-ttu-id="b48e4-155">je volána poslední a je zodpovědná za konfiguraci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="b48e4-155">is called last and is responsible for configuring the runtime.</span></span> <span data-ttu-id="b48e4-156">Následující parametry jsou předány do <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="b48e4-156">The following parameters are passed into <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:</span></span>  
  
-   `Description`<span data-ttu-id="b48e4-157">: Tento parametr obsahuje popis služby pro celou službu.</span><span class="sxs-lookup"><span data-stu-id="b48e4-157">: This parameter provides the service description for the entire service.</span></span> <span data-ttu-id="b48e4-158">To lze použít ke kontrole popis data o koncové body služby, kontrakty, vazby a další data související se službou.</span><span class="sxs-lookup"><span data-stu-id="b48e4-158">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data associated with the service.</span></span>  
  
-   `ServiceHostBase`<span data-ttu-id="b48e4-159">: Tento parametr obsahuje <xref:System.ServiceModel.ServiceHostBase> , který je aktuálně inicializována.</span><span class="sxs-lookup"><span data-stu-id="b48e4-159">: This parameter provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="b48e4-160">Ve vlastní <xref:System.ServiceModel.Description.IServiceBehavior> implementace, novou instanci třídy `ObjectPoolInstanceProvider` vytvořena a přiřazená <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> vlastnost v každém <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> , který je připojen k <xref:System.ServiceModel.ServiceHostBase>.</span><span class="sxs-lookup"><span data-stu-id="b48e4-160">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation, a new instance of `ObjectPoolInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> that is attached to the <xref:System.ServiceModel.ServiceHostBase>.</span></span>  
  
```  
public void ApplyDispatchBehavior(ServiceDescription description, ServiceHostBase serviceHostBase)  
{  
    if (enabled)  
    {  
        // Create an instance of the ObjectPoolInstanceProvider.  
        instanceProvider = new ObjectPoolInstanceProvider(description.ServiceType,  
        maxPoolSize, minPoolSize, creationTimeout);  
  
        // Assign our instance provider to Dispatch behavior in each   
        // endpoint.  
        foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)  
        {  
             ChannelDispatcher cd = cdb as ChannelDispatcher;  
             if (cd != null)  
             {  
                 foreach (EndpointDispatcher ed in cd.Endpoints)  
                 {  
                        ed.DispatchRuntime.InstanceProvider = instanceProvider;  
                 }  
             }  
         }  
     }  
}   
```  
  
 <span data-ttu-id="b48e4-161">Kromě <xref:System.ServiceModel.Description.IServiceBehavior> implementace `ObjectPoolingAttribute` třída má několik členů k přizpůsobení fondu objektů pomocí argumentů atributu.</span><span class="sxs-lookup"><span data-stu-id="b48e4-161">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the `ObjectPoolingAttribute` class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="b48e4-162">Zahrnout tyto členy `MaxSize`, `MinSize`, `Enabled` a `CreationTimeout`, tak, aby odpovídaly objekt sdružování sadu funkcí poskytovanou služeb .NET Enterprise.</span><span class="sxs-lookup"><span data-stu-id="b48e4-162">These members include `MaxSize`, `MinSize`, `Enabled` and `CreationTimeout`, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="b48e4-163">Objekt sdružování chování lze nyní přidat ke službě WCF anotací implementace služby nově vytvořené vlastním `ObjectPooling` atribut.</span><span class="sxs-lookup"><span data-stu-id="b48e4-163">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a><span data-ttu-id="b48e4-164">Zapojení aktivace a deaktivace</span><span class="sxs-lookup"><span data-stu-id="b48e4-164">Hooking Activation and Deactivation</span></span>  
 <span data-ttu-id="b48e4-165">Primární cílem sdružování objektů je k optimalizaci krátkodobé objekty s poměrně nákladné vytváření a inicializace.</span><span class="sxs-lookup"><span data-stu-id="b48e4-165">The primary objective of object pooling is to optimize short-lived objects with relatively expensive creation and initialization.</span></span> <span data-ttu-id="b48e4-166">Proto ho nakopnout výrazné výkonu přidělit aplikaci pokud správně použili.</span><span class="sxs-lookup"><span data-stu-id="b48e4-166">Therefore it can give a dramatic performance boost to an application if properly used.</span></span> <span data-ttu-id="b48e4-167">Protože je objekt vrácen z fondu, je konstruktor volán pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="b48e4-167">Because the object is returned from the pool, the constructor is called only once.</span></span> <span data-ttu-id="b48e4-168">Ale některé aplikace vyžadují určité úrovně ovládacího prvku tak, aby se můžou inicializovat a vyčistit prostředky využívané během jednotlivý kontext.</span><span class="sxs-lookup"><span data-stu-id="b48e4-168">However, some applications require some level of control so that they can initialize and clean-up the resources used during a single context.</span></span> <span data-ttu-id="b48e4-169">Například objekt se používají pro sadu výpočty můžou resetovat jeho privátní pole před zpracováním další výpočtu.</span><span class="sxs-lookup"><span data-stu-id="b48e4-169">For example, an object being used for a set of calculations can reset its private fields before processing the next calculation.</span></span> <span data-ttu-id="b48e4-170">Enterprise Services povolit tento typ inicializace specifickým pro kontext tím, že objekt developer přepsat `Activate` a `Deactivate` metody ze <xref:System.EnterpriseServices.ServicedComponent> základní třídy.</span><span class="sxs-lookup"><span data-stu-id="b48e4-170">Enterprise Services enabled this kind of context-specific initialization by letting the object developer override `Activate` and `Deactivate` methods from the <xref:System.EnterpriseServices.ServicedComponent> base class.</span></span>  
  
 <span data-ttu-id="b48e4-171">Volání objektu fondu `Activate` metoda těsně před vrácením objekt z fondu.</span><span class="sxs-lookup"><span data-stu-id="b48e4-171">The object pool calls the `Activate` method just before returning the object from the pool.</span></span> `Deactivate` <span data-ttu-id="b48e4-172">je volána, když objekt vrátí zpět do fondu.</span><span class="sxs-lookup"><span data-stu-id="b48e4-172">is called when the object returns back to the pool.</span></span> <span data-ttu-id="b48e4-173"><xref:System.EnterpriseServices.ServicedComponent> Má také základní třídu `boolean` vlastnost s názvem `CanBePooled`, které je možné oznámit fondu, jestli objekt může dále fondu.</span><span class="sxs-lookup"><span data-stu-id="b48e4-173">The <xref:System.EnterpriseServices.ServicedComponent> base class also has a `boolean` property called `CanBePooled`, which can be used to notify the pool whether the object can be pooled further.</span></span>  
  
 <span data-ttu-id="b48e4-174">Tak, aby napodoboval tuto funkci, ukázka deklaruje veřejné rozhraní (`IObjectControl`), který má výše uvedené členy.</span><span class="sxs-lookup"><span data-stu-id="b48e4-174">To mimic this functionality, the sample declares a public interface (`IObjectControl`) that has the aforementioned members.</span></span> <span data-ttu-id="b48e4-175">Toto rozhraní následně implementované třídy určená k zajištění určité Inicializace kontextu služby.</span><span class="sxs-lookup"><span data-stu-id="b48e4-175">This interface is then implemented by service classes intended to provide context specific initialization.</span></span> <span data-ttu-id="b48e4-176"><xref:System.ServiceModel.Dispatcher.IInstanceProvider> Implementace musí upravit tak, aby tyto požadavky splňují.</span><span class="sxs-lookup"><span data-stu-id="b48e4-176">The <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation must be modified to meet these requirements.</span></span> <span data-ttu-id="b48e4-177">Nyní pokaždé, když získáte objektu voláním `GetInstance` metodu, musíte zkontrolovat, zda daný objekt implementuje `IObjectControl.` Pokud ano, musíte zavolat `Activate` metoda odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="b48e4-177">Now, each time you get an object by calling the `GetInstance` method, you must check whether the object implements `IObjectControl.` If it does, you must call the `Activate` method appropriately.</span></span>  
  
```  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 <span data-ttu-id="b48e4-178">Při vrácení objektu do fondu, je třeba použít kontrolu `CanBePooled` vlastnost před přidáním objektu zpět do fondu.</span><span class="sxs-lookup"><span data-stu-id="b48e4-178">When returning an object to the pool, a check is required for the `CanBePooled` property before adding the object back to the pool.</span></span>  
  
```  
if (instance is IObjectControl)  
{  
    IObjectControl objectControl = (IObjectControl)instance;  
    objectControl.Deactivate();  
    if (objectControl.CanBePooled)  
    {  
       pool.Push(instance);  
    }  
}  
```  
  
 <span data-ttu-id="b48e4-179">Protože vývojářem služeb se můžete rozhodnout, jestli objekt může být ve fondu, můžete počet objektů ve fondu v daném okamžiku přejít menší než minimální velikost.</span><span class="sxs-lookup"><span data-stu-id="b48e4-179">Because the service developer can decide whether an object can be pooled, the object count in the pool at a given time can go below the minimum size.</span></span> <span data-ttu-id="b48e4-180">Musíte proto zkontrolujte, zda počet objektů pod minimální úroveň a provést nezbytné inicializace v postupu čištění.</span><span class="sxs-lookup"><span data-stu-id="b48e4-180">Therefore you must check whether the object count has gone below the minimum level and perform the necessary initialization in the clean-up procedure.</span></span>  
  
```  
// Remove the surplus objects.  
if (pool.Count > minPoolSize)  
{  
  // Clean the surplus objects.  
}                      
else if (pool.Count < minPoolSize)  
{  
  // Reinitialize the missing objects.  
  while(pool.Count != minPoolSize)  
  {  
    pool.Push(CreateNewPoolObject());  
  }  
}  
```  
  
 <span data-ttu-id="b48e4-181">Při spuštění ukázky operace žádosti a odpovědi se zobrazují v oknech konzoly služby a klienta.</span><span class="sxs-lookup"><span data-stu-id="b48e4-181">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="b48e4-182">Stisknutím klávesy Enter v každé okno konzoly pro vypnutí klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="b48e4-182">Press Enter in each console window to shut down the service and client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b48e4-183">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="b48e4-183">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b48e4-184">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b48e4-184">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b48e4-185">Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b48e4-185">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="b48e4-186">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b48e4-186">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b48e4-187">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="b48e4-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b48e4-188">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="b48e4-188">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b48e4-189">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="b48e4-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b48e4-190">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="b48e4-190">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
