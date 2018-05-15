---
title: Inicializace vytváření instancí
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: ae01254760219f2b408ef9d9663c4158e2802be8
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="instancing-initialization"></a><span data-ttu-id="be18b-102">Inicializace vytváření instancí</span><span class="sxs-lookup"><span data-stu-id="be18b-102">Instancing Initialization</span></span>
<span data-ttu-id="be18b-103">Tato ukázka rozšiřuje [Pooling](../../../../docs/framework/wcf/samples/pooling.md) ukázku definováním rozhraní, `IObjectControl`, který přizpůsobí inicializace objektu aktivace a deaktivace ho.</span><span class="sxs-lookup"><span data-stu-id="be18b-103">This sample extends the [Pooling](../../../../docs/framework/wcf/samples/pooling.md) sample by defining an interface, `IObjectControl`, which customizes the initialization of an object by activating and deactivating it.</span></span> <span data-ttu-id="be18b-104">Klient volá metody, které vrací objekt do fondu a která nevrátí objektu do fondu.</span><span class="sxs-lookup"><span data-stu-id="be18b-104">The client invokes methods that return the object to the pool and that do not return the object to the pool.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="be18b-105">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="be18b-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="extensibility-points"></a><span data-ttu-id="be18b-106">Body rozšiřitelnosti</span><span class="sxs-lookup"><span data-stu-id="be18b-106">Extensibility Points</span></span>  
 <span data-ttu-id="be18b-107">Prvním krokem při vytváření rozšíření pro Windows Communication Foundation (WCF) je rozhodnout bodem rozšíření používat.</span><span class="sxs-lookup"><span data-stu-id="be18b-107">The first step in creating a Windows Communication Foundation (WCF) extension is to decide the extensibility point to use.</span></span> <span data-ttu-id="be18b-108">Ve službě WCF termín *EndpointDispatcher* odkazuje na komponentu běhu odpovědný za převodu příchozí zprávy volání metod na uživatele služby a pro převod návratové hodnoty z dané metody na odchozí zprávy .</span><span class="sxs-lookup"><span data-stu-id="be18b-108">In WCF, the term *EndpointDispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="be18b-109">Služby WCF vytvoří EndpointDispatcher pro každý koncový bod.</span><span class="sxs-lookup"><span data-stu-id="be18b-109">A WCF service creates an EndpointDispatcher for each endpoint.</span></span>  
  
 <span data-ttu-id="be18b-110">EndpointDispatcher nabízí koncový bod oboru (pro všechny zprávy přijatých nebo odeslaných službou) rozšiřitelnost pomocí <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> třídy.</span><span class="sxs-lookup"><span data-stu-id="be18b-110">The EndpointDispatcher offers endpoint scope (for all messages received or sent by the service) extensibility using the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> class.</span></span> <span data-ttu-id="be18b-111">Tato třída umožňuje přizpůsobit různé vlastnosti tohoto ovládání chování EndpointDispatcher.</span><span class="sxs-lookup"><span data-stu-id="be18b-111">This class allows you to customize various properties that control the behavior of the EndpointDispatcher.</span></span> <span data-ttu-id="be18b-112">Tato ukázka se zaměřuje na <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> vlastnost, která odkazuje na objekt, který poskytuje instancí třídy služby.</span><span class="sxs-lookup"><span data-stu-id="be18b-112">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="iinstanceprovider"></a><span data-ttu-id="be18b-113">IInstanceProvider</span><span class="sxs-lookup"><span data-stu-id="be18b-113">IInstanceProvider</span></span>  
 <span data-ttu-id="be18b-114">Ve službě WCF, EndpointDispatcher vytváří instance třídy služeb pomocí instance zprostředkovatele, který implementuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="be18b-114">In WCF, the EndpointDispatcher creates instances of a service class by using an instance provider that implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="be18b-115">Toto rozhraní má jenom dvě metody:</span><span class="sxs-lookup"><span data-stu-id="be18b-115">This interface has only two methods:</span></span>  
  
-   <span data-ttu-id="be18b-116"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: Při doručení zprávy, volání dispečera <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> metodu pro vytvoření instance třídy služeb, ke zpracování zprávy.</span><span class="sxs-lookup"><span data-stu-id="be18b-116"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: When a message arrives, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="be18b-117">Četnost volání této metody je dáno <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="be18b-117">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="be18b-118">Například pokud <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> je nastavena na <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, je vytvořit novou instanci třídy služeb pro zpracování jednotlivých zpráv, které dorazí, tak <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> je volána, když doručení zprávy.</span><span class="sxs-lookup"><span data-stu-id="be18b-118">For example if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> is called whenever a message arrives.</span></span>  
  
-   <span data-ttu-id="be18b-119"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: Pokud je instance služby dokončí zpracování zprávy, EndpointDispatcher volá <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="be18b-119"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: When the service instance finishes processing the message, the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method.</span></span> <span data-ttu-id="be18b-120">Jako v <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> metody Četnost volání této metody je dáno <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="be18b-120">As in the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="be18b-121">Fond objektů</span><span class="sxs-lookup"><span data-stu-id="be18b-121">The Object Pool</span></span>  
 <span data-ttu-id="be18b-122">`ObjectPoolInstanceProvider` Třída obsahuje implementaci pro fond objektů.</span><span class="sxs-lookup"><span data-stu-id="be18b-122">The `ObjectPoolInstanceProvider` class contains the implementation for the object pool.</span></span> <span data-ttu-id="be18b-123">Tato třída implementuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider> rozhraní pro interakci s vrstva modelu služby.</span><span class="sxs-lookup"><span data-stu-id="be18b-123">This class implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface to interact with the service model layer.</span></span> <span data-ttu-id="be18b-124">Při volání EndpointDispatcher <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> metody, místo vytvoření nové instance, vlastní implementaci vypadá pro existující objekt ve fondu v paměti.</span><span class="sxs-lookup"><span data-stu-id="be18b-124">When the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="be18b-125">Pokud je k dispozici, je vrácena.</span><span class="sxs-lookup"><span data-stu-id="be18b-125">If one is available, it is returned.</span></span> <span data-ttu-id="be18b-126">V opačném `ObjectPoolInstanceProvider` kontroluje, zda `ActiveObjectsCount` vlastnost (počet objektů vrácených z fondu) byl dosažen maximální počet.</span><span class="sxs-lookup"><span data-stu-id="be18b-126">Otherwise, `ObjectPoolInstanceProvider` checks whether the `ActiveObjectsCount` property (number of objects returned from the pool) has reached the maximum pool size.</span></span> <span data-ttu-id="be18b-127">Pokud ne, novou instanci se vytvoří a vrácen volajícímu a `ActiveObjectsCount` se následně zvýší.</span><span class="sxs-lookup"><span data-stu-id="be18b-127">If not, a new instance is created and returned to the caller and `ActiveObjectsCount` is subsequently incremented.</span></span> <span data-ttu-id="be18b-128">V opačném případě požadavek na vytvoření objektů je zařadit do fronty pro určenou dobu.</span><span class="sxs-lookup"><span data-stu-id="be18b-128">Otherwise an object creation request is queued for a configured period of time.</span></span> <span data-ttu-id="be18b-129">Implementace pro `GetObjectFromThePool` je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="be18b-129">The implementation for `GetObjectFromThePool` is shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="be18b-130">Vlastní `ReleaseInstance` implementace přidá vydaná instance zpět do fondu a snižují se vždy `ActiveObjectsCount` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="be18b-130">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="be18b-131">EndpointDispatcher tyto metody můžete volat z různých vláknech a proto synchronizované přístupu na úrovni členy třídy v `ObjectPoolInstanceProvider` je vyžadován.</span><span class="sxs-lookup"><span data-stu-id="be18b-131">The EndpointDispatcher can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolInstanceProvider` class is required.</span></span>  
  
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
  
 <span data-ttu-id="be18b-132">`ReleaseInstance` Poskytuje metody *vyčištění inicializace* funkce.</span><span class="sxs-lookup"><span data-stu-id="be18b-132">The `ReleaseInstance` method provides a *clean up initialization* feature.</span></span> <span data-ttu-id="be18b-133">Za normálních okolností fond udržuje minimální počet objektů po dobu jeho existence fondu.</span><span class="sxs-lookup"><span data-stu-id="be18b-133">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="be18b-134">Však může být období nadměrné využití, které vyžadují vytváření další objekty ve fondu k dosažení maximální limit zadaný v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="be18b-134">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="be18b-135">Když se změní na míň aktivní fondu tyto nadbytečné objekty může přestat zvýšené režii.</span><span class="sxs-lookup"><span data-stu-id="be18b-135">Eventually when the pool becomes less active those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="be18b-136">Proto když `activeObjectsCount` hodnota nula nečinnosti časovače spuštění, který aktivuje vyčištění cyklus.</span><span class="sxs-lookup"><span data-stu-id="be18b-136">Therefore when the `activeObjectsCount` reaches zero an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
```  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();   
}  
```  
  
 <span data-ttu-id="be18b-137">Rozšíření vrstvy ServiceModel se připojili pomocí následující chování:</span><span class="sxs-lookup"><span data-stu-id="be18b-137">ServiceModel layer extensions are hooked up using the following behaviors:</span></span>  
  
-   <span data-ttu-id="be18b-138">Chování služby:, Tyto rutiny umožňují k přizpůsobení modulu runtime celé služby.</span><span class="sxs-lookup"><span data-stu-id="be18b-138">Service Behaviors: These allow for the customization of the entire service runtime.</span></span>  
  
-   <span data-ttu-id="be18b-139">Chování koncový bod:, Tyto rutiny umožňují pro přizpůsobení koncový bod konkrétní službu, včetně EndpointDispatcher.</span><span class="sxs-lookup"><span data-stu-id="be18b-139">Endpoint Behaviors: These allow for the customization of a particular service endpoint, including the EndpointDispatcher.</span></span>  
  
-   <span data-ttu-id="be18b-140">Chování kontraktu: Tyto rutiny umožňují pro přizpůsobení buď <xref:System.ServiceModel.Dispatcher.ClientRuntime> nebo <xref:System.ServiceModel.Dispatcher.DispatchRuntime> třídy na klienta nebo služby v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="be18b-140">Contract Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientRuntime> or <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client or the service respectively.</span></span>  
  
-   <span data-ttu-id="be18b-141">Operace chování: Tyto rutiny umožňují pro přizpůsobení buď <xref:System.ServiceModel.Dispatcher.ClientOperation> nebo <xref:System.ServiceModel.Dispatcher.DispatchOperation> třídy na klienta nebo služby v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="be18b-141">Operation Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientOperation> or <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes on the client or the service respectively.</span></span>  
  
 <span data-ttu-id="be18b-142">Pro účely objekt sdružování rozšíření mohou být vytvořeny chování koncového bodu nebo chování služby.</span><span class="sxs-lookup"><span data-stu-id="be18b-142">For the purpose of an object pooling extension, either an endpoint behavior or a service behavior can be created.</span></span> <span data-ttu-id="be18b-143">V tomto příkladu používáme chování služby, která se vztahuje objekt sdružování schopnost každý koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="be18b-143">In this example, we use a service behavior, which applies object pooling ability to every endpoint of the service.</span></span> <span data-ttu-id="be18b-144">Chování služby jsou vytvořené pomocí implementace <xref:System.ServiceModel.Description.IServiceBehavior> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="be18b-144">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="be18b-145">Chcete-li vědět, že vlastní chování ServiceModel několika způsoby:</span><span class="sxs-lookup"><span data-stu-id="be18b-145">There are several ways to make the ServiceModel aware of the custom behaviors:</span></span>  
  
-   <span data-ttu-id="be18b-146">Pomocí vlastních atributů.</span><span class="sxs-lookup"><span data-stu-id="be18b-146">Using a custom attribute.</span></span>  
  
-   <span data-ttu-id="be18b-147">Imperativní přidáním do kolekce chování popis služby.</span><span class="sxs-lookup"><span data-stu-id="be18b-147">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
-   <span data-ttu-id="be18b-148">Rozšíření konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="be18b-148">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="be18b-149">Tato ukázka používá vlastní atribut.</span><span class="sxs-lookup"><span data-stu-id="be18b-149">This sample uses a custom attribute.</span></span> <span data-ttu-id="be18b-150">Když <xref:System.ServiceModel.ServiceHost> je vytvořená, prozkoumá atributy používané v definici služby typu a přidá do kolekce chování popis služby k dispozici chování.</span><span class="sxs-lookup"><span data-stu-id="be18b-150">When the <xref:System.ServiceModel.ServiceHost> is constructed, it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="be18b-151"><xref:System.ServiceModel.Description.IServiceBehavior> Rozhraní má tři metody: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> `,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> `,` a <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span><span class="sxs-lookup"><span data-stu-id="be18b-151">The <xref:System.ServiceModel.Description.IServiceBehavior> interface has three methods: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>`,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>`,` and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="be18b-152">Tyto metody jsou volány WCF při <xref:System.ServiceModel.ServiceHost> inicializace.</span><span class="sxs-lookup"><span data-stu-id="be18b-152">These methods are called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="be18b-153"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> jako první; To umožňuje službu, kterou chcete být prověřovány za účelem nalezení nekonzistencí.</span><span class="sxs-lookup"><span data-stu-id="be18b-153"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> is called first; it allows the service to be inspected for inconsistencies.</span></span> <span data-ttu-id="be18b-154"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> je volána vedle; Tato metoda je potřeba jenom v velmi pokročilých scénářích.</span><span class="sxs-lookup"><span data-stu-id="be18b-154"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> is called next; this method is only required in very advanced scenarios.</span></span> <span data-ttu-id="be18b-155"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> Označuje se poslední a je zodpovědná za konfiguraci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="be18b-155"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> is called last and is responsible for configuring the runtime.</span></span> <span data-ttu-id="be18b-156">Tyto parametry se předávají do <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="be18b-156">The following parameters are passed into <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:</span></span>  
  
-   <span data-ttu-id="be18b-157">`Description`: Tento parametr obsahuje popis služby pro celé služby.</span><span class="sxs-lookup"><span data-stu-id="be18b-157">`Description`: This parameter provides the service description for the entire service.</span></span> <span data-ttu-id="be18b-158">To slouží ke kontrole popis data o koncové body služby, kontrakty, vazby a další data spojené s touto službou.</span><span class="sxs-lookup"><span data-stu-id="be18b-158">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data associated with the service.</span></span>  
  
-   <span data-ttu-id="be18b-159">`ServiceHostBase`: Poskytuje tento parametr <xref:System.ServiceModel.ServiceHostBase> která aktuálně probíhá inicializace.</span><span class="sxs-lookup"><span data-stu-id="be18b-159">`ServiceHostBase`: This parameter provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="be18b-160">Ve vlastní <xref:System.ServiceModel.Description.IServiceBehavior> implementace, novou instanci třídy `ObjectPoolInstanceProvider` se vytvořit instanci a přiřadí do <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> vlastnost v každé <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> připojená k <xref:System.ServiceModel.ServiceHostBase>.</span><span class="sxs-lookup"><span data-stu-id="be18b-160">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation, a new instance of `ObjectPoolInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> that is attached to the <xref:System.ServiceModel.ServiceHostBase>.</span></span>  
  
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
  
 <span data-ttu-id="be18b-161">Kromě <xref:System.ServiceModel.Description.IServiceBehavior> implementace `ObjectPoolingAttribute` třída obsahuje několik členů k přizpůsobení fondu objektů pomocí argumenty atributu.</span><span class="sxs-lookup"><span data-stu-id="be18b-161">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the `ObjectPoolingAttribute` class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="be18b-162">Zahrnout tito členové `MaxSize`, `MinSize`, `Enabled` a `CreationTimeout`, tak, aby odpovídaly objekt sdružování sada funkcí poskytovaných služeb .NET Enterprise.</span><span class="sxs-lookup"><span data-stu-id="be18b-162">These members include `MaxSize`, `MinSize`, `Enabled` and `CreationTimeout`, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="be18b-163">Objekt sdružování chování nyní přidáte do služby WCF tak, že zadávání poznámek k implementaci služby s nově vytvořené vlastní `ObjectPooling` atribut.</span><span class="sxs-lookup"><span data-stu-id="be18b-163">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a><span data-ttu-id="be18b-164">Zapojování aktivace a deaktivace</span><span class="sxs-lookup"><span data-stu-id="be18b-164">Hooking Activation and Deactivation</span></span>  
 <span data-ttu-id="be18b-165">Primární cílem sdružování objektů je za účelem optimalizace krátkodobou objekty s relativně nákladné vytváření a inicializace.</span><span class="sxs-lookup"><span data-stu-id="be18b-165">The primary objective of object pooling is to optimize short-lived objects with relatively expensive creation and initialization.</span></span> <span data-ttu-id="be18b-166">Proto je zvýšení výrazné výkonu přidělit aplikaci pokud správně používá.</span><span class="sxs-lookup"><span data-stu-id="be18b-166">Therefore it can give a dramatic performance boost to an application if properly used.</span></span> <span data-ttu-id="be18b-167">Vzhledem k tomu, že objekt se vrátí z fondu, je konstruktoru volat pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="be18b-167">Because the object is returned from the pool, the constructor is called only once.</span></span> <span data-ttu-id="be18b-168">Ale některé aplikace vyžadují některé úroveň kontroly tak, aby můžou inicializaci a čištění prostředky využívané během jednotlivý kontext.</span><span class="sxs-lookup"><span data-stu-id="be18b-168">However, some applications require some level of control so that they can initialize and clean-up the resources used during a single context.</span></span> <span data-ttu-id="be18b-169">Například objekt používá pro sadu výpočty můžete resetovat jeho privátním polím před zpracováním další výpočtu.</span><span class="sxs-lookup"><span data-stu-id="be18b-169">For example, an object being used for a set of calculations can reset its private fields before processing the next calculation.</span></span> <span data-ttu-id="be18b-170">Tento druh inicializace konkrétní povolit služby Enterprise tím, že vývojář objekt přepsat `Activate` a `Deactivate` metody z <xref:System.EnterpriseServices.ServicedComponent> základní třídy.</span><span class="sxs-lookup"><span data-stu-id="be18b-170">Enterprise Services enabled this kind of context-specific initialization by letting the object developer override `Activate` and `Deactivate` methods from the <xref:System.EnterpriseServices.ServicedComponent> base class.</span></span>  
  
 <span data-ttu-id="be18b-171">Volání objektu fondu `Activate` metoda těsně před vrácením objekt z fondu.</span><span class="sxs-lookup"><span data-stu-id="be18b-171">The object pool calls the `Activate` method just before returning the object from the pool.</span></span> <span data-ttu-id="be18b-172">`Deactivate` je volána, když objekt vrátí zpět do fondu.</span><span class="sxs-lookup"><span data-stu-id="be18b-172">`Deactivate` is called when the object returns back to the pool.</span></span> <span data-ttu-id="be18b-173"><xref:System.EnterpriseServices.ServicedComponent> Základní třída má také `boolean` vlastnost s názvem `CanBePooled`, který slouží k upozornění fondu, zda objekt může být ve fondu další.</span><span class="sxs-lookup"><span data-stu-id="be18b-173">The <xref:System.EnterpriseServices.ServicedComponent> base class also has a `boolean` property called `CanBePooled`, which can be used to notify the pool whether the object can be pooled further.</span></span>  
  
 <span data-ttu-id="be18b-174">Tak, aby napodoboval tuto funkci, ukázky deklaruje veřejné rozhraní (`IObjectControl`) s zmíněnými členy.</span><span class="sxs-lookup"><span data-stu-id="be18b-174">To mimic this functionality, the sample declares a public interface (`IObjectControl`) that has the aforementioned members.</span></span> <span data-ttu-id="be18b-175">Toto rozhraní je implementováno pak službou třídy určené k poskytnutí konkrétní Inicializace kontextu.</span><span class="sxs-lookup"><span data-stu-id="be18b-175">This interface is then implemented by service classes intended to provide context specific initialization.</span></span> <span data-ttu-id="be18b-176"><xref:System.ServiceModel.Dispatcher.IInstanceProvider> Implementace musí upravit, aby tyto požadavky splňují.</span><span class="sxs-lookup"><span data-stu-id="be18b-176">The <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation must be modified to meet these requirements.</span></span> <span data-ttu-id="be18b-177">Nyní, pokaždé, když jste získat objekt voláním `GetInstance` metoda, je nutné zkontrolovat, zda objekt implementuje `IObjectControl.` Pokud ano, musí volat `Activate` metoda správně.</span><span class="sxs-lookup"><span data-stu-id="be18b-177">Now, each time you get an object by calling the `GetInstance` method, you must check whether the object implements `IObjectControl.` If it does, you must call the `Activate` method appropriately.</span></span>  
  
```  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 <span data-ttu-id="be18b-178">Když se vrátí objekt do fondu, je vyžadována pro kontrolu `CanBePooled` vlastnost před přidáním objektu zpět do fondu.</span><span class="sxs-lookup"><span data-stu-id="be18b-178">When returning an object to the pool, a check is required for the `CanBePooled` property before adding the object back to the pool.</span></span>  
  
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
  
 <span data-ttu-id="be18b-179">Protože vývojáři služby můžete rozhodnout, zda objekt můžete ve fondu, můžete přejít počet objektů ve fondu v daném okamžiku nižší než minimální velikost.</span><span class="sxs-lookup"><span data-stu-id="be18b-179">Because the service developer can decide whether an object can be pooled, the object count in the pool at a given time can go below the minimum size.</span></span> <span data-ttu-id="be18b-180">Proto musíte zkontrolovat, zda počet objektů přešel nižší než minimální úroveň a provést potřebné inicializaci v postupu čištění.</span><span class="sxs-lookup"><span data-stu-id="be18b-180">Therefore you must check whether the object count has gone below the minimum level and perform the necessary initialization in the clean-up procedure.</span></span>  
  
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
  
 <span data-ttu-id="be18b-181">Při spuštění vzorového operaci požadavky a odpovědi se zobrazují v oknech konzoly služby a klienta.</span><span class="sxs-lookup"><span data-stu-id="be18b-181">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="be18b-182">Stisknutím klávesy Enter v každé okna konzoly vypnout klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="be18b-182">Press Enter in each console window to shut down the service and client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="be18b-183">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="be18b-183">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="be18b-184">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="be18b-184">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="be18b-185">Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="be18b-185">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="be18b-186">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="be18b-186">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="be18b-187">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="be18b-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="be18b-188">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="be18b-188">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="be18b-189">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="be18b-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="be18b-190">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="be18b-190">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
  
## <a name="see-also"></a><span data-ttu-id="be18b-191">Viz také</span><span class="sxs-lookup"><span data-stu-id="be18b-191">See Also</span></span>
