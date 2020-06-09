---
title: Inicializace vytváření instancí
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: 06a8dfe571b652ded236df3097b37861c03a858d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596653"
---
# <a name="instancing-initialization"></a><span data-ttu-id="88313-102">Inicializace vytváření instancí</span><span class="sxs-lookup"><span data-stu-id="88313-102">Instancing Initialization</span></span>
<span data-ttu-id="88313-103">Tato ukázka rozšiřuje ukázku [sdružování](pooling.md) definováním rozhraní, `IObjectControl` , které přizpůsobuje inicializaci objektu aktivací a dezaktivováním.</span><span class="sxs-lookup"><span data-stu-id="88313-103">This sample extends the [Pooling](pooling.md) sample by defining an interface, `IObjectControl`, which customizes the initialization of an object by activating and deactivating it.</span></span> <span data-ttu-id="88313-104">Klient vyvolá metody, které vrátí objekt do fondu a nevrátí objekt do fondu.</span><span class="sxs-lookup"><span data-stu-id="88313-104">The client invokes methods that return the object to the pool and that do not return the object to the pool.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="88313-105">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="88313-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="extensibility-points"></a><span data-ttu-id="88313-106">Body rozšiřitelnosti</span><span class="sxs-lookup"><span data-stu-id="88313-106">Extensibility Points</span></span>  
 <span data-ttu-id="88313-107">Prvním krokem při vytváření rozšíření Windows Communication Foundation (WCF) je určení bodu rozšiřitelnosti, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="88313-107">The first step in creating a Windows Communication Foundation (WCF) extension is to decide the extensibility point to use.</span></span> <span data-ttu-id="88313-108">V rámci WCF pojem *Třída EndpointDispatcher* odkazuje na komponentu za běhu odpovědnou za převod příchozích zpráv do vyvolání metod na službu uživatele a pro převod návratových hodnot z této metody na odchozí zprávu.</span><span class="sxs-lookup"><span data-stu-id="88313-108">In WCF, the term *EndpointDispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="88313-109">Služba WCF vytvoří třída EndpointDispatcher pro každý koncový bod.</span><span class="sxs-lookup"><span data-stu-id="88313-109">A WCF service creates an EndpointDispatcher for each endpoint.</span></span>  
  
 <span data-ttu-id="88313-110">Třída EndpointDispatcher nabízí rozsah koncového bodu (pro všechny zprávy, které přijala nebo odesílá služba) rozšiřitelnost pomocí <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> třídy.</span><span class="sxs-lookup"><span data-stu-id="88313-110">The EndpointDispatcher offers endpoint scope (for all messages received or sent by the service) extensibility using the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> class.</span></span> <span data-ttu-id="88313-111">Tato třída umožňuje přizpůsobit různé vlastnosti, které řídí chování třída EndpointDispatcher.</span><span class="sxs-lookup"><span data-stu-id="88313-111">This class allows you to customize various properties that control the behavior of the EndpointDispatcher.</span></span> <span data-ttu-id="88313-112">Tato ukázka se zaměřuje na <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> vlastnost, která odkazuje na objekt, který poskytuje instance třídy služby.</span><span class="sxs-lookup"><span data-stu-id="88313-112">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="iinstanceprovider"></a><span data-ttu-id="88313-113">IInstanceProvider</span><span class="sxs-lookup"><span data-stu-id="88313-113">IInstanceProvider</span></span>  
 <span data-ttu-id="88313-114">Ve službě WCF vytvoří třída EndpointDispatcher instance třídy služby pomocí zprostředkovatele instancí, který implementuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="88313-114">In WCF, the EndpointDispatcher creates instances of a service class by using an instance provider that implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="88313-115">Toto rozhraní má pouze dvě metody:</span><span class="sxs-lookup"><span data-stu-id="88313-115">This interface has only two methods:</span></span>  
  
- <span data-ttu-id="88313-116"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: Při doručení zprávy Dispečer volá <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> metodu pro vytvoření instance třídy služby pro zpracování zprávy.</span><span class="sxs-lookup"><span data-stu-id="88313-116"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: When a message arrives, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="88313-117">Frekvence volání této metody je určena <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastností.</span><span class="sxs-lookup"><span data-stu-id="88313-117">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="88313-118">Například pokud <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> je vlastnost nastavena na <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType> , je vytvořena nová instance třídy služby pro zpracování každé zprávy, která dorazí, takže <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> je volána při doručení zprávy.</span><span class="sxs-lookup"><span data-stu-id="88313-118">For example if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> is called whenever a message arrives.</span></span>  
  
- <span data-ttu-id="88313-119"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: Když instance služby dokončí zpracování zprávy, třída EndpointDispatcher volá <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="88313-119"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: When the service instance finishes processing the message, the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method.</span></span> <span data-ttu-id="88313-120">Stejně jako v <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> metodě je frekvence volání této metody určena <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastností.</span><span class="sxs-lookup"><span data-stu-id="88313-120">As in the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="88313-121">Fond objektů</span><span class="sxs-lookup"><span data-stu-id="88313-121">The Object Pool</span></span>  
 <span data-ttu-id="88313-122">`ObjectPoolInstanceProvider`Třída obsahuje implementaci fondu objektů.</span><span class="sxs-lookup"><span data-stu-id="88313-122">The `ObjectPoolInstanceProvider` class contains the implementation for the object pool.</span></span> <span data-ttu-id="88313-123">Tato třída implementuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider> rozhraní pro interakci s vrstvou modelu služby.</span><span class="sxs-lookup"><span data-stu-id="88313-123">This class implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface to interact with the service model layer.</span></span> <span data-ttu-id="88313-124">Pokud třída EndpointDispatcher volá <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> metodu namísto vytvoření nové instance, vlastní implementace vyhledá existující objekt ve fondu v paměti.</span><span class="sxs-lookup"><span data-stu-id="88313-124">When the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="88313-125">Pokud je k dispozici, je vrácena.</span><span class="sxs-lookup"><span data-stu-id="88313-125">If one is available, it is returned.</span></span> <span data-ttu-id="88313-126">V opačném případě `ObjectPoolInstanceProvider` ověří, zda `ActiveObjectsCount` vlastnost (počet objektů vrácených z fondu) dosáhla maximální velikosti fondu.</span><span class="sxs-lookup"><span data-stu-id="88313-126">Otherwise, `ObjectPoolInstanceProvider` checks whether the `ActiveObjectsCount` property (number of objects returned from the pool) has reached the maximum pool size.</span></span> <span data-ttu-id="88313-127">V takovém případě se vytvoří nová instance, která se vrátí volajícímu a `ActiveObjectsCount` následně se zvýší.</span><span class="sxs-lookup"><span data-stu-id="88313-127">If not, a new instance is created and returned to the caller and `ActiveObjectsCount` is subsequently incremented.</span></span> <span data-ttu-id="88313-128">V opačném případě je požadavek na vytvoření objektu zařazen do fronty po nastavenou dobu.</span><span class="sxs-lookup"><span data-stu-id="88313-128">Otherwise an object creation request is queued for a configured period of time.</span></span> <span data-ttu-id="88313-129">Implementace pro `GetObjectFromThePool` je uvedena v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="88313-129">The implementation for `GetObjectFromThePool` is shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="88313-130">Vlastní `ReleaseInstance` implementace přidá uvolněnou instanci zpátky do fondu a sníží `ActiveObjectsCount` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="88313-130">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="88313-131">Třída EndpointDispatcher může volat tyto metody z různých vláken, a proto je vyžadován synchronizovaný přístup ke členům úrovně třídy ve `ObjectPoolInstanceProvider` třídě.</span><span class="sxs-lookup"><span data-stu-id="88313-131">The EndpointDispatcher can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolInstanceProvider` class is required.</span></span>  
  
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
  
 <span data-ttu-id="88313-132">`ReleaseInstance`Metoda poskytuje *inicializační* funkci pro vyčištění.</span><span class="sxs-lookup"><span data-stu-id="88313-132">The `ReleaseInstance` method provides a *clean up initialization* feature.</span></span> <span data-ttu-id="88313-133">Fond běžně udržuje minimální počet objektů za dobu života fondu.</span><span class="sxs-lookup"><span data-stu-id="88313-133">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="88313-134">Nicméně můžou existovat období nadměrného využití, které vyžaduje vytvoření dalších objektů ve fondu, aby dosáhly maximálního limitu určeného v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="88313-134">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="88313-135">Pokud se ale fond stane méně aktivním, může se stát, že nadbytečné objekty budou dodatečně režijní.</span><span class="sxs-lookup"><span data-stu-id="88313-135">Eventually when the pool becomes less active those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="88313-136">Proto když dojde k `activeObjectsCount` nulovému nečinnému časovači, spustí se Trigger a provede se čisticí cyklus.</span><span class="sxs-lookup"><span data-stu-id="88313-136">Therefore when the `activeObjectsCount` reaches zero an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
```csharp  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();
}  
```  
  
 <span data-ttu-id="88313-137">Rozšíření vrstvy ServiceModel jsou zapojená pomocí následujícího chování:</span><span class="sxs-lookup"><span data-stu-id="88313-137">ServiceModel layer extensions are hooked up using the following behaviors:</span></span>  
  
- <span data-ttu-id="88313-138">Chování služby: tyto možnosti umožňují přizpůsobení celého modulu runtime služby.</span><span class="sxs-lookup"><span data-stu-id="88313-138">Service Behaviors: These allow for the customization of the entire service runtime.</span></span>  
  
- <span data-ttu-id="88313-139">Chování koncového bodu: tyto možnosti umožňují přizpůsobení konkrétního koncového bodu služby, včetně třída EndpointDispatcher.</span><span class="sxs-lookup"><span data-stu-id="88313-139">Endpoint Behaviors: These allow for the customization of a particular service endpoint, including the EndpointDispatcher.</span></span>  
  
- <span data-ttu-id="88313-140">Chování kontraktu: tyto možnosti umožňují přizpůsobení buď <xref:System.ServiceModel.Dispatcher.ClientRuntime> nebo <xref:System.ServiceModel.Dispatcher.DispatchRuntime> tříd v klientovi nebo službě.</span><span class="sxs-lookup"><span data-stu-id="88313-140">Contract Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientRuntime> or <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client or the service respectively.</span></span>  
  
- <span data-ttu-id="88313-141">Chování operace: tyto možnosti umožňují přizpůsobení buď <xref:System.ServiceModel.Dispatcher.ClientOperation> nebo <xref:System.ServiceModel.Dispatcher.DispatchOperation> tříd v klientovi nebo službě.</span><span class="sxs-lookup"><span data-stu-id="88313-141">Operation Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientOperation> or <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes on the client or the service respectively.</span></span>  
  
 <span data-ttu-id="88313-142">Pro účely rozšíření sdružování objektů je možné vytvořit buď chování koncového bodu, nebo chování služby.</span><span class="sxs-lookup"><span data-stu-id="88313-142">For the purpose of an object pooling extension, either an endpoint behavior or a service behavior can be created.</span></span> <span data-ttu-id="88313-143">V tomto příkladu používáme chování služby, které aplikuje sdružování objektů do každého koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="88313-143">In this example, we use a service behavior, which applies object pooling ability to every endpoint of the service.</span></span> <span data-ttu-id="88313-144">Chování služby je vytvořeno implementací <xref:System.ServiceModel.Description.IServiceBehavior> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="88313-144">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="88313-145">Existuje několik způsobů, jak zajistit, aby měl ServiceModel v potaz vlastní chování:</span><span class="sxs-lookup"><span data-stu-id="88313-145">There are several ways to make the ServiceModel aware of the custom behaviors:</span></span>  
  
- <span data-ttu-id="88313-146">Použití vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="88313-146">Using a custom attribute.</span></span>  
  
- <span data-ttu-id="88313-147">Imperativně přidejte do kolekce chování popisu služby.</span><span class="sxs-lookup"><span data-stu-id="88313-147">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
- <span data-ttu-id="88313-148">Rozšíření konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="88313-148">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="88313-149">Tato ukázka používá vlastní atribut.</span><span class="sxs-lookup"><span data-stu-id="88313-149">This sample uses a custom attribute.</span></span> <span data-ttu-id="88313-150">Když <xref:System.ServiceModel.ServiceHost> je vytvořen, prověřuje atributy používané v definici typu služby a přidá k němu dostupné chování do kolekce chování popisu služby.</span><span class="sxs-lookup"><span data-stu-id="88313-150">When the <xref:System.ServiceModel.ServiceHost> is constructed, it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="88313-151"><xref:System.ServiceModel.Description.IServiceBehavior>Rozhraní má tři metody: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> `,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> `,` a <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> .</span><span class="sxs-lookup"><span data-stu-id="88313-151">The <xref:System.ServiceModel.Description.IServiceBehavior> interface has three methods: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>`,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>`,` and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="88313-152">Tyto metody jsou volány službou WCF při <xref:System.ServiceModel.ServiceHost> inicializaci.</span><span class="sxs-lookup"><span data-stu-id="88313-152">These methods are called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="88313-153"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType>je volána jako první; umožňuje kontrolu nekonzistencí služby.</span><span class="sxs-lookup"><span data-stu-id="88313-153"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> is called first; it allows the service to be inspected for inconsistencies.</span></span> <span data-ttu-id="88313-154"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType>se nazývá Next; Tato metoda je vyžadována pouze ve velmi pokročilých scénářích.</span><span class="sxs-lookup"><span data-stu-id="88313-154"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> is called next; this method is only required in very advanced scenarios.</span></span> <span data-ttu-id="88313-155"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>je volána jako poslední a zodpovídá za konfiguraci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="88313-155"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> is called last and is responsible for configuring the runtime.</span></span> <span data-ttu-id="88313-156">Následující parametry jsou předány do <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="88313-156">The following parameters are passed into <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:</span></span>  
  
- <span data-ttu-id="88313-157">`Description`: Tento parametr poskytuje popis služby pro celou službu.</span><span class="sxs-lookup"><span data-stu-id="88313-157">`Description`: This parameter provides the service description for the entire service.</span></span> <span data-ttu-id="88313-158">Dá se použít ke kontrole popisných dat o koncových bodech služby, kontraktech, vazbách a dalších datech přidružených k této službě.</span><span class="sxs-lookup"><span data-stu-id="88313-158">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data associated with the service.</span></span>  
  
- <span data-ttu-id="88313-159">`ServiceHostBase`: Tento parametr poskytuje <xref:System.ServiceModel.ServiceHostBase> aktuálně inicializovaný.</span><span class="sxs-lookup"><span data-stu-id="88313-159">`ServiceHostBase`: This parameter provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="88313-160">V vlastní <xref:System.ServiceModel.Description.IServiceBehavior> implementaci `ObjectPoolInstanceProvider` je vytvořena instance nové instance a přiřazena <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> vlastnosti v každé z nich <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> , která je připojena k <xref:System.ServiceModel.ServiceHostBase> .</span><span class="sxs-lookup"><span data-stu-id="88313-160">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation, a new instance of `ObjectPoolInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> that is attached to the <xref:System.ServiceModel.ServiceHostBase>.</span></span>  
  
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
  
 <span data-ttu-id="88313-161">Kromě <xref:System.ServiceModel.Description.IServiceBehavior> implementace má `ObjectPoolingAttribute` Třída více členů k přizpůsobení fondu objektů pomocí argumentů atributu.</span><span class="sxs-lookup"><span data-stu-id="88313-161">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the `ObjectPoolingAttribute` class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="88313-162">Mezi tyto členy patří `MaxSize` , `MinSize` , `Enabled` a `CreationTimeout` , aby odpovídaly sadě funkcí sdružování objektů poskytované službami .NET Enterprise Services.</span><span class="sxs-lookup"><span data-stu-id="88313-162">These members include `MaxSize`, `MinSize`, `Enabled` and `CreationTimeout`, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="88313-163">Chování sdružování objektů se teď dá přidat ke službě WCF tím, že se pokládá na implementaci služby s nově vytvořeným vlastním `ObjectPooling` atributem.</span><span class="sxs-lookup"><span data-stu-id="88313-163">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```csharp  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a><span data-ttu-id="88313-164">Zapojování aktivace a deaktivace</span><span class="sxs-lookup"><span data-stu-id="88313-164">Hooking Activation and Deactivation</span></span>  
 <span data-ttu-id="88313-165">Hlavním cílem sdružování objektů je optimalizovat krátkodobé objekty s poměrně nákladným vytvořením a inicializací.</span><span class="sxs-lookup"><span data-stu-id="88313-165">The primary objective of object pooling is to optimize short-lived objects with relatively expensive creation and initialization.</span></span> <span data-ttu-id="88313-166">Proto může aplikace výrazně zvýšit výkon při správném použití.</span><span class="sxs-lookup"><span data-stu-id="88313-166">Therefore it can give a dramatic performance boost to an application if properly used.</span></span> <span data-ttu-id="88313-167">Vzhledem k tomu, že objekt je vrácen z fondu, konstruktor je volán pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="88313-167">Because the object is returned from the pool, the constructor is called only once.</span></span> <span data-ttu-id="88313-168">Některé aplikace však vyžadují určitou úroveň řízení, aby bylo možné inicializovat a vyčistit prostředky používané během jednoho kontextu.</span><span class="sxs-lookup"><span data-stu-id="88313-168">However, some applications require some level of control so that they can initialize and clean-up the resources used during a single context.</span></span> <span data-ttu-id="88313-169">Například objekt, který se používá pro sadu výpočtů, může obnovit svá soukromá pole před zpracováním dalšího výpočtu.</span><span class="sxs-lookup"><span data-stu-id="88313-169">For example, an object being used for a set of calculations can reset its private fields before processing the next calculation.</span></span> <span data-ttu-id="88313-170">Podnikové služby povolily tento druh inicializace specifického kontextu tím, že umožňují vývojáři objektu přepsat `Activate` a `Deactivate` metody ze <xref:System.EnterpriseServices.ServicedComponent> základní třídy.</span><span class="sxs-lookup"><span data-stu-id="88313-170">Enterprise Services enabled this kind of context-specific initialization by letting the object developer override `Activate` and `Deactivate` methods from the <xref:System.EnterpriseServices.ServicedComponent> base class.</span></span>  
  
 <span data-ttu-id="88313-171">Fond objektů volá `Activate` metodu těsně před vrácením objektu z fondu.</span><span class="sxs-lookup"><span data-stu-id="88313-171">The object pool calls the `Activate` method just before returning the object from the pool.</span></span> <span data-ttu-id="88313-172">`Deactivate`se volá, když se objekt vrátí zpátky do fondu.</span><span class="sxs-lookup"><span data-stu-id="88313-172">`Deactivate` is called when the object returns back to the pool.</span></span> <span data-ttu-id="88313-173"><xref:System.EnterpriseServices.ServicedComponent>Základní třída také obsahuje vlastnost s `boolean` názvem `CanBePooled` , která může být použita pro upozorňování fondu, zda lze objekt dále vyřadit do fondu.</span><span class="sxs-lookup"><span data-stu-id="88313-173">The <xref:System.EnterpriseServices.ServicedComponent> base class also has a `boolean` property called `CanBePooled`, which can be used to notify the pool whether the object can be pooled further.</span></span>  
  
 <span data-ttu-id="88313-174">Pro napodobení této funkci ukázka deklaruje veřejné rozhraní ( `IObjectControl` ), které má výše uvedené členy.</span><span class="sxs-lookup"><span data-stu-id="88313-174">To mimic this functionality, the sample declares a public interface (`IObjectControl`) that has the aforementioned members.</span></span> <span data-ttu-id="88313-175">Toto rozhraní je pak implementováno pomocí tříd služeb určených k poskytnutí inicializace specifického kontextu.</span><span class="sxs-lookup"><span data-stu-id="88313-175">This interface is then implemented by service classes intended to provide context specific initialization.</span></span> <span data-ttu-id="88313-176"><xref:System.ServiceModel.Dispatcher.IInstanceProvider>Implementaci je třeba upravit tak, aby splňovala tyto požadavky.</span><span class="sxs-lookup"><span data-stu-id="88313-176">The <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation must be modified to meet these requirements.</span></span> <span data-ttu-id="88313-177">Nyní, při každém získání objektu voláním `GetInstance` metody, je nutné zkontrolovat, zda objekt implementuje `IObjectControl.` , pokud je, nutné zavolat `Activate` metodu odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="88313-177">Now, each time you get an object by calling the `GetInstance` method, you must check whether the object implements `IObjectControl.` If it does, you must call the `Activate` method appropriately.</span></span>  
  
```csharp  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 <span data-ttu-id="88313-178">Při vrácení objektu do fondu je `CanBePooled` před přidáním objektu zpět do fondu vyžadováno ověření vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="88313-178">When returning an object to the pool, a check is required for the `CanBePooled` property before adding the object back to the pool.</span></span>  
  
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
  
 <span data-ttu-id="88313-179">Vzhledem k tomu, že se vývojář služby může rozhodnout, zda lze objekt vytvořit do fondu, může počet objektů ve fondu v daném čase přecházet pod minimální velikostí.</span><span class="sxs-lookup"><span data-stu-id="88313-179">Because the service developer can decide whether an object can be pooled, the object count in the pool at a given time can go below the minimum size.</span></span> <span data-ttu-id="88313-180">Proto je nutné ověřit, zda počet objektů předržíte pod minimální úrovní a provést nezbytnou inicializaci v postupu vyčištění.</span><span class="sxs-lookup"><span data-stu-id="88313-180">Therefore you must check whether the object count has gone below the minimum level and perform the necessary initialization in the clean-up procedure.</span></span>  
  
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
  
 <span data-ttu-id="88313-181">Při spuštění ukázky se požadavky na operace a odpovědi zobrazí v oknech služba i klientská konzola.</span><span class="sxs-lookup"><span data-stu-id="88313-181">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="88313-182">V každém okně konzoly stiskněte klávesu ENTER a ukončete službu a klienta.</span><span class="sxs-lookup"><span data-stu-id="88313-182">Press Enter in each console window to shut down the service and client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="88313-183">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="88313-183">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="88313-184">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="88313-184">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="88313-185">Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="88313-185">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="88313-186">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="88313-186">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="88313-187">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="88313-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="88313-188">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="88313-188">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="88313-189">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="88313-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="88313-190">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="88313-190">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
