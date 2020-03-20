---
title: Inicializace vytváření instancí
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: 897bb62df0a23073827aeed18b54bf77e8c6d4bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183599"
---
# <a name="instancing-initialization"></a><span data-ttu-id="b2f45-102">Inicializace vytváření instancí</span><span class="sxs-lookup"><span data-stu-id="b2f45-102">Instancing Initialization</span></span>
<span data-ttu-id="b2f45-103">Tato ukázka rozšiřuje [sdružování](../../../../docs/framework/wcf/samples/pooling.md) vzorku `IObjectControl`definováním rozhraní , který přizpůsobí inicializaci objektu aktivací a deaktivací.</span><span class="sxs-lookup"><span data-stu-id="b2f45-103">This sample extends the [Pooling](../../../../docs/framework/wcf/samples/pooling.md) sample by defining an interface, `IObjectControl`, which customizes the initialization of an object by activating and deactivating it.</span></span> <span data-ttu-id="b2f45-104">Klient vyvolá metody, které vrátí objekt do fondu a které nevrátí objekt do fondu.</span><span class="sxs-lookup"><span data-stu-id="b2f45-104">The client invokes methods that return the object to the pool and that do not return the object to the pool.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b2f45-105">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="b2f45-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="extensibility-points"></a><span data-ttu-id="b2f45-106">Body rozšiřitelnosti</span><span class="sxs-lookup"><span data-stu-id="b2f45-106">Extensibility Points</span></span>  
 <span data-ttu-id="b2f45-107">Prvním krokem při vytváření rozšíření Windows Communication Foundation (WCF) je rozhodnout o bodu rozšiřitelnosti použít.</span><span class="sxs-lookup"><span data-stu-id="b2f45-107">The first step in creating a Windows Communication Foundation (WCF) extension is to decide the extensibility point to use.</span></span> <span data-ttu-id="b2f45-108">V WCF termín *EndpointDispatcher* odkazuje na součást za běhu, která je zodpovědná za převod příchozích zpráv na vyvolání metody ve službě uživatele a za převod vrácených hodnot z této metody na odchozí zprávu.</span><span class="sxs-lookup"><span data-stu-id="b2f45-108">In WCF, the term *EndpointDispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="b2f45-109">Služba WCF vytvoří endpointdispatcher pro každý koncový bod.</span><span class="sxs-lookup"><span data-stu-id="b2f45-109">A WCF service creates an EndpointDispatcher for each endpoint.</span></span>  
  
 <span data-ttu-id="b2f45-110">EndpointDispatcher nabízí obor koncového bodu (pro všechny zprávy přijaté nebo odeslané službou) rozšiřitelnost pomocí třídy. <xref:System.ServiceModel.Dispatcher.EndpointDispatcher></span><span class="sxs-lookup"><span data-stu-id="b2f45-110">The EndpointDispatcher offers endpoint scope (for all messages received or sent by the service) extensibility using the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> class.</span></span> <span data-ttu-id="b2f45-111">Tato třída umožňuje přizpůsobit různé vlastnosti, které řídí chování EndpointDispatcher.</span><span class="sxs-lookup"><span data-stu-id="b2f45-111">This class allows you to customize various properties that control the behavior of the EndpointDispatcher.</span></span> <span data-ttu-id="b2f45-112">Tato ukázka se <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> zaměřuje na vlastnost, která odkazuje na objekt, který poskytuje instance třídy služby.</span><span class="sxs-lookup"><span data-stu-id="b2f45-112">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="iinstanceprovider"></a><span data-ttu-id="b2f45-113">Iinstanceprovider</span><span class="sxs-lookup"><span data-stu-id="b2f45-113">IInstanceProvider</span></span>  
 <span data-ttu-id="b2f45-114">V WCF EndpointDispatcher vytvoří instance třídy služby pomocí zprostředkovatele <xref:System.ServiceModel.Dispatcher.IInstanceProvider> instance, který implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b2f45-114">In WCF, the EndpointDispatcher creates instances of a service class by using an instance provider that implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="b2f45-115">Toto rozhraní má pouze dvě metody:</span><span class="sxs-lookup"><span data-stu-id="b2f45-115">This interface has only two methods:</span></span>  
  
- <span data-ttu-id="b2f45-116"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: Když přijde zpráva, Dispečer volá metodu <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> k vytvoření instance třídy služby ke zpracování zprávy.</span><span class="sxs-lookup"><span data-stu-id="b2f45-116"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: When a message arrives, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="b2f45-117">Frekvence volání této metody je určena <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastností.</span><span class="sxs-lookup"><span data-stu-id="b2f45-117">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="b2f45-118">Například pokud <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> je vlastnost <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>nastavena na , je vytvořena nová instance třídy služby pro zpracování každé zprávy, která dorazí, tak <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> se nazývá vždy, když přijde zpráva.</span><span class="sxs-lookup"><span data-stu-id="b2f45-118">For example if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> is called whenever a message arrives.</span></span>  
  
- <span data-ttu-id="b2f45-119"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: Když instance služby dokončí zpracování zprávy, EndpointDispatcher volá metodu. <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A></span><span class="sxs-lookup"><span data-stu-id="b2f45-119"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: When the service instance finishes processing the message, the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method.</span></span> <span data-ttu-id="b2f45-120">Stejně <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> jako v metodě je frekvence volání této <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> metody určena vlastností.</span><span class="sxs-lookup"><span data-stu-id="b2f45-120">As in the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="b2f45-121">Fond objektů</span><span class="sxs-lookup"><span data-stu-id="b2f45-121">The Object Pool</span></span>  
 <span data-ttu-id="b2f45-122">Třída `ObjectPoolInstanceProvider` obsahuje implementaci pro fond objektů.</span><span class="sxs-lookup"><span data-stu-id="b2f45-122">The `ObjectPoolInstanceProvider` class contains the implementation for the object pool.</span></span> <span data-ttu-id="b2f45-123">Tato třída implementuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider> rozhraní pro interakci s vrstvou modelu služby.</span><span class="sxs-lookup"><span data-stu-id="b2f45-123">This class implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface to interact with the service model layer.</span></span> <span data-ttu-id="b2f45-124">Když EndpointDispatcher volá <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> metodu namísto vytvoření nové instance, vlastní implementace hledá existující objekt ve fondu v paměti.</span><span class="sxs-lookup"><span data-stu-id="b2f45-124">When the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="b2f45-125">Pokud je k dispozici, je vrácena.</span><span class="sxs-lookup"><span data-stu-id="b2f45-125">If one is available, it is returned.</span></span> <span data-ttu-id="b2f45-126">V `ObjectPoolInstanceProvider` opačném případě `ActiveObjectsCount` zkontroluje, zda vlastnost (počet objektů vrácených z fondu) dosáhla maximální velikost fondu.</span><span class="sxs-lookup"><span data-stu-id="b2f45-126">Otherwise, `ObjectPoolInstanceProvider` checks whether the `ActiveObjectsCount` property (number of objects returned from the pool) has reached the maximum pool size.</span></span> <span data-ttu-id="b2f45-127">Pokud tomu tak není, je vytvořena nová `ActiveObjectsCount` instance a vrácena volajícímu a následně se zpřímí.</span><span class="sxs-lookup"><span data-stu-id="b2f45-127">If not, a new instance is created and returned to the caller and `ActiveObjectsCount` is subsequently incremented.</span></span> <span data-ttu-id="b2f45-128">V opačném případě je požadavek na vytvoření objektu zařazen do fronty po nakonfigurovanou dobu.</span><span class="sxs-lookup"><span data-stu-id="b2f45-128">Otherwise an object creation request is queued for a configured period of time.</span></span> <span data-ttu-id="b2f45-129">Implementace pro `GetObjectFromThePool` je uveden v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="b2f45-129">The implementation for `GetObjectFromThePool` is shown in the following sample code.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="b2f45-130">Vlastní `ReleaseInstance` implementace přidá uvolněnou instanci zpět do `ActiveObjectsCount` fondu a sníží hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b2f45-130">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="b2f45-131">EndpointDispatcher můžete volat tyto metody z různých vláken, a proto je `ObjectPoolInstanceProvider` vyžadován synchronizovaný přístup k členům na úrovni třídy ve třídě.</span><span class="sxs-lookup"><span data-stu-id="b2f45-131">The EndpointDispatcher can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolInstanceProvider` class is required.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="b2f45-132">Metoda `ReleaseInstance` poskytuje funkci *vyčištění inicializace.*</span><span class="sxs-lookup"><span data-stu-id="b2f45-132">The `ReleaseInstance` method provides a *clean up initialization* feature.</span></span> <span data-ttu-id="b2f45-133">Obvykle fond udržuje minimální počet objektů po dobu životnosti fondu.</span><span class="sxs-lookup"><span data-stu-id="b2f45-133">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="b2f45-134">Však může být období nadměrného využití, které vyžadují vytvoření další objekty ve fondu k dosažení maximální limit zadaný v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="b2f45-134">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="b2f45-135">Nakonec při fondu se stane méně aktivní tyto nadbytečné objekty se může stát další režii.</span><span class="sxs-lookup"><span data-stu-id="b2f45-135">Eventually when the pool becomes less active those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="b2f45-136">Proto při `activeObjectsCount` dosažení nuly je spuštěn časovač nečinnosti, který aktivuje a provede cyklus čištění.</span><span class="sxs-lookup"><span data-stu-id="b2f45-136">Therefore when the `activeObjectsCount` reaches zero an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
```csharp  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();
}  
```  
  
 <span data-ttu-id="b2f45-137">Rozšíření vrstev ServiceModel jsou zahnutý nahoru pomocí následujících chování:</span><span class="sxs-lookup"><span data-stu-id="b2f45-137">ServiceModel layer extensions are hooked up using the following behaviors:</span></span>  
  
- <span data-ttu-id="b2f45-138">Chování služby: Umožňují přizpůsobení celého běhu služby.</span><span class="sxs-lookup"><span data-stu-id="b2f45-138">Service Behaviors: These allow for the customization of the entire service runtime.</span></span>  
  
- <span data-ttu-id="b2f45-139">Chování koncového bodu: Umožňují přizpůsobení konkrétního koncového bodu služby, včetně endpointdispatcheru.</span><span class="sxs-lookup"><span data-stu-id="b2f45-139">Endpoint Behaviors: These allow for the customization of a particular service endpoint, including the EndpointDispatcher.</span></span>  
  
- <span data-ttu-id="b2f45-140">Chování smlouvy: Umožňují přizpůsobení buď <xref:System.ServiceModel.Dispatcher.ClientRuntime> nebo <xref:System.ServiceModel.Dispatcher.DispatchRuntime> třídy na straně klienta nebo služby v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="b2f45-140">Contract Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientRuntime> or <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client or the service respectively.</span></span>  
  
- <span data-ttu-id="b2f45-141">Chování operace: Umožňují přizpůsobení buď <xref:System.ServiceModel.Dispatcher.ClientOperation> nebo <xref:System.ServiceModel.Dispatcher.DispatchOperation> třídy na straně klienta nebo služby v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="b2f45-141">Operation Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientOperation> or <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes on the client or the service respectively.</span></span>  
  
 <span data-ttu-id="b2f45-142">Pro účely rozšíření sdružování objektů lze vytvořit chování koncového bodu nebo chování služby.</span><span class="sxs-lookup"><span data-stu-id="b2f45-142">For the purpose of an object pooling extension, either an endpoint behavior or a service behavior can be created.</span></span> <span data-ttu-id="b2f45-143">V tomto příkladu používáme chování služby, které platí schopnost sdružování objektů pro každý koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="b2f45-143">In this example, we use a service behavior, which applies object pooling ability to every endpoint of the service.</span></span> <span data-ttu-id="b2f45-144">Chování služby jsou vytvořeny <xref:System.ServiceModel.Description.IServiceBehavior> implementací rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b2f45-144">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="b2f45-145">Existuje několik způsobů, jak seznámit ServiceModel vlastní chování:</span><span class="sxs-lookup"><span data-stu-id="b2f45-145">There are several ways to make the ServiceModel aware of the custom behaviors:</span></span>  
  
- <span data-ttu-id="b2f45-146">Použití vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="b2f45-146">Using a custom attribute.</span></span>  
  
- <span data-ttu-id="b2f45-147">Imperativně přidání do kolekce chování popis služby.</span><span class="sxs-lookup"><span data-stu-id="b2f45-147">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
- <span data-ttu-id="b2f45-148">Rozšíření konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="b2f45-148">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="b2f45-149">Tato ukázka používá vlastní atribut.</span><span class="sxs-lookup"><span data-stu-id="b2f45-149">This sample uses a custom attribute.</span></span> <span data-ttu-id="b2f45-150">Když <xref:System.ServiceModel.ServiceHost> je vytvořen, zkontroluje atributy použité v definici typu služby a přidá dostupné chování do kolekce chování popis služby.</span><span class="sxs-lookup"><span data-stu-id="b2f45-150">When the <xref:System.ServiceModel.ServiceHost> is constructed, it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="b2f45-151">Rozhraní <xref:System.ServiceModel.Description.IServiceBehavior> má tři <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> `,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> `,` metody: a <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span><span class="sxs-lookup"><span data-stu-id="b2f45-151">The <xref:System.ServiceModel.Description.IServiceBehavior> interface has three methods: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>`,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>`,` and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="b2f45-152">Tyto metody jsou volány <xref:System.ServiceModel.ServiceHost> WCF při inicializování.</span><span class="sxs-lookup"><span data-stu-id="b2f45-152">These methods are called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="b2f45-153"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType>nazývá jako první; umožňuje, aby služba byla zkontrolována na nekonzistenci.</span><span class="sxs-lookup"><span data-stu-id="b2f45-153"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> is called first; it allows the service to be inspected for inconsistencies.</span></span> <span data-ttu-id="b2f45-154"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType>nazývá další; Tato metoda je vyžadována pouze ve velmi pokročilých scénářích.</span><span class="sxs-lookup"><span data-stu-id="b2f45-154"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> is called next; this method is only required in very advanced scenarios.</span></span> <span data-ttu-id="b2f45-155"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>je volána jako poslední a je zodpovědná za konfiguraci běhu.</span><span class="sxs-lookup"><span data-stu-id="b2f45-155"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> is called last and is responsible for configuring the runtime.</span></span> <span data-ttu-id="b2f45-156">Následující parametry jsou <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>předány do :</span><span class="sxs-lookup"><span data-stu-id="b2f45-156">The following parameters are passed into <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:</span></span>  
  
- <span data-ttu-id="b2f45-157">`Description`: Tento parametr poskytuje popis služby pro celou službu.</span><span class="sxs-lookup"><span data-stu-id="b2f45-157">`Description`: This parameter provides the service description for the entire service.</span></span> <span data-ttu-id="b2f45-158">To lze použít ke kontrole popisdat o koncových bodech služby, smlouvy, vazby a další data spojená se službou.</span><span class="sxs-lookup"><span data-stu-id="b2f45-158">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data associated with the service.</span></span>  
  
- <span data-ttu-id="b2f45-159">`ServiceHostBase`: Tento parametr <xref:System.ServiceModel.ServiceHostBase> poskytuje aktuálně inicializován.</span><span class="sxs-lookup"><span data-stu-id="b2f45-159">`ServiceHostBase`: This parameter provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="b2f45-160">Ve vlastní <xref:System.ServiceModel.Description.IServiceBehavior> `ObjectPoolInstanceProvider` implementaci je vytvořena instance instance a přiřazena <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> k <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> vlastnosti v každé, která je připojena k <xref:System.ServiceModel.ServiceHostBase>.</span><span class="sxs-lookup"><span data-stu-id="b2f45-160">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation, a new instance of `ObjectPoolInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> that is attached to the <xref:System.ServiceModel.ServiceHostBase>.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="b2f45-161">Kromě <xref:System.ServiceModel.Description.IServiceBehavior> implementace má `ObjectPoolingAttribute` třída několik členů pro přizpůsobení fondu objektů pomocí argumentů atributu.</span><span class="sxs-lookup"><span data-stu-id="b2f45-161">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the `ObjectPoolingAttribute` class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="b2f45-162">Mezi tyto `MaxSize` `MinSize`členy `Enabled` `CreationTimeout`patří , , a , aby odpovídaly sadě funkcí sdružování objektů poskytované službou .NET Enterprise Services.</span><span class="sxs-lookup"><span data-stu-id="b2f45-162">These members include `MaxSize`, `MinSize`, `Enabled` and `CreationTimeout`, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="b2f45-163">Chování sdružování objektů lze nyní přidat do služby WCF anotací `ObjectPooling` implementace služby s nově vytvořeným vlastním atributem.</span><span class="sxs-lookup"><span data-stu-id="b2f45-163">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```csharp  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a><span data-ttu-id="b2f45-164">Aktivace a deaktivace hákování</span><span class="sxs-lookup"><span data-stu-id="b2f45-164">Hooking Activation and Deactivation</span></span>  
 <span data-ttu-id="b2f45-165">Primárním cílem sdružování objektů je optimalizace krátkodobých objektů s relativně nákladným vytvářením a inicializací.</span><span class="sxs-lookup"><span data-stu-id="b2f45-165">The primary objective of object pooling is to optimize short-lived objects with relatively expensive creation and initialization.</span></span> <span data-ttu-id="b2f45-166">Proto může poskytnout dramatický výkon zvýšení aplikace, pokud správně používá.</span><span class="sxs-lookup"><span data-stu-id="b2f45-166">Therefore it can give a dramatic performance boost to an application if properly used.</span></span> <span data-ttu-id="b2f45-167">Vzhledem k tomu, že objekt je vrácena z fondu, konstruktor se nazývá pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="b2f45-167">Because the object is returned from the pool, the constructor is called only once.</span></span> <span data-ttu-id="b2f45-168">Některé aplikace však vyžadují určitou úroveň řízení, aby mohly inicializovat a vyčistit prostředky používané během jednoho kontextu.</span><span class="sxs-lookup"><span data-stu-id="b2f45-168">However, some applications require some level of control so that they can initialize and clean-up the resources used during a single context.</span></span> <span data-ttu-id="b2f45-169">Například objekt používaný pro sadu výpočtů může obnovit svá soukromá pole před zpracováním dalšího výpočtu.</span><span class="sxs-lookup"><span data-stu-id="b2f45-169">For example, an object being used for a set of calculations can reset its private fields before processing the next calculation.</span></span> <span data-ttu-id="b2f45-170">Enterprise Services povolila tento druh inicializace specifické `Activate` pro `Deactivate` kontext <xref:System.EnterpriseServices.ServicedComponent> tím, že umožňuje vývojářobjektu přepsat a metody ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="b2f45-170">Enterprise Services enabled this kind of context-specific initialization by letting the object developer override `Activate` and `Deactivate` methods from the <xref:System.EnterpriseServices.ServicedComponent> base class.</span></span>  
  
 <span data-ttu-id="b2f45-171">Fond objektů volá `Activate` metodu těsně před vrácením objektu z fondu.</span><span class="sxs-lookup"><span data-stu-id="b2f45-171">The object pool calls the `Activate` method just before returning the object from the pool.</span></span> <span data-ttu-id="b2f45-172">`Deactivate`je volána, když se objekt vrátí zpět do fondu.</span><span class="sxs-lookup"><span data-stu-id="b2f45-172">`Deactivate` is called when the object returns back to the pool.</span></span> <span data-ttu-id="b2f45-173">Základní <xref:System.EnterpriseServices.ServicedComponent> třída má `boolean` také `CanBePooled`vlastnost s názvem , která slouží k upozornění fondu, zda objekt může být dále sdružený.</span><span class="sxs-lookup"><span data-stu-id="b2f45-173">The <xref:System.EnterpriseServices.ServicedComponent> base class also has a `boolean` property called `CanBePooled`, which can be used to notify the pool whether the object can be pooled further.</span></span>  
  
 <span data-ttu-id="b2f45-174">Chcete-li napodobení této funkce,`IObjectControl`ukázka deklaruje veřejné rozhraní ( ), který má výše uvedené členy.</span><span class="sxs-lookup"><span data-stu-id="b2f45-174">To mimic this functionality, the sample declares a public interface (`IObjectControl`) that has the aforementioned members.</span></span> <span data-ttu-id="b2f45-175">Toto rozhraní je pak implementováno třídami služeb určenými k poskytování inicializace specifické pro kontext.</span><span class="sxs-lookup"><span data-stu-id="b2f45-175">This interface is then implemented by service classes intended to provide context specific initialization.</span></span> <span data-ttu-id="b2f45-176">Implementace <xref:System.ServiceModel.Dispatcher.IInstanceProvider> musí být upravena tak, aby splňovala tyto požadavky.</span><span class="sxs-lookup"><span data-stu-id="b2f45-176">The <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation must be modified to meet these requirements.</span></span> <span data-ttu-id="b2f45-177">Nyní pokaždé, když získáte objekt `GetInstance` voláním metody, je nutné `IObjectControl.` zkontrolovat, zda objekt implementuje Pokud ano, musíte správně volat metodu. `Activate`</span><span class="sxs-lookup"><span data-stu-id="b2f45-177">Now, each time you get an object by calling the `GetInstance` method, you must check whether the object implements `IObjectControl.` If it does, you must call the `Activate` method appropriately.</span></span>  
  
```csharp  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 <span data-ttu-id="b2f45-178">Při vrácení objektu do fondu je vyžadována `CanBePooled` kontrola pro vlastnost před přidáním objektu zpět do fondu.</span><span class="sxs-lookup"><span data-stu-id="b2f45-178">When returning an object to the pool, a check is required for the `CanBePooled` property before adding the object back to the pool.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="b2f45-179">Vzhledem k tomu, že vývojář služby může rozhodnout, zda objekt může být sdružený, počet objektů ve fondu v daném čase může přejít pod minimální velikost.</span><span class="sxs-lookup"><span data-stu-id="b2f45-179">Because the service developer can decide whether an object can be pooled, the object count in the pool at a given time can go below the minimum size.</span></span> <span data-ttu-id="b2f45-180">Proto je nutné zkontrolovat, zda počet objektů klesla pod minimální úroveň a provést potřebnou inicializaci v procesu čištění.</span><span class="sxs-lookup"><span data-stu-id="b2f45-180">Therefore you must check whether the object count has gone below the minimum level and perform the necessary initialization in the clean-up procedure.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="b2f45-181">Při spuštění ukázky jsou požadavky na operaci a odpovědi zobrazeny v systému Windows služby i klientské konzole.</span><span class="sxs-lookup"><span data-stu-id="b2f45-181">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="b2f45-182">Stisknutím klávesy Enter v každém okně konzoly vypněte službu a klienta.</span><span class="sxs-lookup"><span data-stu-id="b2f45-182">Press Enter in each console window to shut down the service and client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b2f45-183">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="b2f45-183">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b2f45-184">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b2f45-184">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b2f45-185">Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b2f45-185">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="b2f45-186">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b2f45-186">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b2f45-187">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="b2f45-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b2f45-188">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="b2f45-188">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b2f45-189">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="b2f45-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b2f45-190">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="b2f45-190">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
