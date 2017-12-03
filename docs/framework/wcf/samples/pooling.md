---
title: "Sdružování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fb45a08e9f21578b69dedbe504cfb8bbd21193bb
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="pooling"></a><span data-ttu-id="baa15-102">Sdružování</span><span class="sxs-lookup"><span data-stu-id="baa15-102">Pooling</span></span>
<span data-ttu-id="baa15-103">Tento příklad ukazuje, jak rozšířit [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pro podporu sdružování objektů.</span><span class="sxs-lookup"><span data-stu-id="baa15-103">This sample demonstrates how to extend [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to support object pooling.</span></span> <span data-ttu-id="baa15-104">Ukázka ukazuje, jak vytvořit atribut, který je syntakticky a sémanticky podobná `ObjectPoolingAttribute` atribut funkce služby Enterprise.</span><span class="sxs-lookup"><span data-stu-id="baa15-104">The sample demonstrates how to create an attribute that is syntactically and semantically similar to the `ObjectPoolingAttribute` attribute functionality of Enterprise Services.</span></span> <span data-ttu-id="baa15-105">Sdružování objektů zajistí výrazné zvýšení výkonu aplikace na výkon.</span><span class="sxs-lookup"><span data-stu-id="baa15-105">Object pooling can provide a dramatic boost to an application's performance.</span></span> <span data-ttu-id="baa15-106">Pokud se nepoužívá správně však může mít opačný efekt.</span><span class="sxs-lookup"><span data-stu-id="baa15-106">However, it can have the opposite effect if it is not used properly.</span></span> <span data-ttu-id="baa15-107">Sdružování objektů pomáhá snížit režii znovu vytvořit často používaných objektů, které vyžadují rozsáhlé inicializace.</span><span class="sxs-lookup"><span data-stu-id="baa15-107">Object pooling helps reduce the overhead of recreating frequently used objects that require extensive initialization.</span></span> <span data-ttu-id="baa15-108">Však sdružování objekt fronty Pokud volání metody na objekt ve fondu používá značné množství času na dokončení, další požadavky při dosažení k maximální velikosti fondu.</span><span class="sxs-lookup"><span data-stu-id="baa15-108">However, if a call to a method on a pooled object takes a considerable amount of time to complete, object pooling queues additional requests as soon as the maximum pool size is reached.</span></span> <span data-ttu-id="baa15-109">Proto může dojít k selhání obsluze některé objekt požadavky na vytvoření byla vrácena výjimka časového limitu.</span><span class="sxs-lookup"><span data-stu-id="baa15-109">Thus it may fail to serve some object creation requests by throwing a timeout exception.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="baa15-110">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="baa15-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="baa15-111">Prvním krokem při vytváření [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] rozšíření je rozhodnutí o bodem rozšíření používat.</span><span class="sxs-lookup"><span data-stu-id="baa15-111">The first step in creating a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] extension is to decide the extensibility point to use.</span></span>  
  
 <span data-ttu-id="baa15-112">V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] termín *dispečera* odkazuje na komponentu běhu odpovědný za převodu příchozí zprávy volání metod na uživatele služby a pro převod návratové hodnoty z dané metody na odchozí zpráva.</span><span class="sxs-lookup"><span data-stu-id="baa15-112">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] the term *dispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="baa15-113">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služba vytvoří dispečera pro každý koncový bod.</span><span class="sxs-lookup"><span data-stu-id="baa15-113">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service creates a dispatcher for each endpoint.</span></span> <span data-ttu-id="baa15-114">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, pokud smlouvy přidružené tohoto klienta je duplexního kontraktu, musíte používat dispečera.</span><span class="sxs-lookup"><span data-stu-id="baa15-114">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client must use a dispatcher if the contract associated with that client is a duplex contract.</span></span>  
  
 <span data-ttu-id="baa15-115">Kanál a koncový bod dispečerů nabízejí kanál- a rozšiřitelnost v rámci smlouvy díky zpřístupnění různé vlastnosti, které řídí chování dispečera.</span><span class="sxs-lookup"><span data-stu-id="baa15-115">The channel and endpoint dispatchers offer channel-and contract-wide extensibility by exposing various properties that control the behavior of the dispatcher.</span></span> <span data-ttu-id="baa15-116"><xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> Vlastnost můžete také zkontrolovat, upravit nebo přizpůsobit odesílající proces.</span><span class="sxs-lookup"><span data-stu-id="baa15-116">The <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> property also enables you to inspect, modify, or customize the dispatching process.</span></span> <span data-ttu-id="baa15-117">Tato ukázka se zaměřuje na <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> vlastnost, která odkazuje na objekt, který poskytuje instancí třídy služby.</span><span class="sxs-lookup"><span data-stu-id="baa15-117">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="the-iinstanceprovider"></a><span data-ttu-id="baa15-118">IInstanceProvider</span><span class="sxs-lookup"><span data-stu-id="baa15-118">The IInstanceProvider</span></span>  
 <span data-ttu-id="baa15-119">V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], dispečera vytváří instance třídy pomocí služby <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, který implementuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="baa15-119">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], the dispatcher creates instances of the service class using a <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, which implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="baa15-120">Toto rozhraní obsahuje tři metody:</span><span class="sxs-lookup"><span data-stu-id="baa15-120">This interface has three methods:</span></span>  
  
-   <span data-ttu-id="baa15-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: Při doručení zprávy dispečera volání <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metodu pro vytvoření instance třídy služeb, ke zpracování zprávy.</span><span class="sxs-lookup"><span data-stu-id="baa15-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: When a message arrives the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="baa15-122">Četnost volání této metody je dáno <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="baa15-122">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="baa15-123">Například pokud <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> je nastavena na <xref:System.ServiceModel.InstanceContextMode.PerCall> pro zpracování jednotlivých zpráv, které dorazí, tak se vytvoří novou instanci třídy služby <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> je volána, když doručení zprávy.</span><span class="sxs-lookup"><span data-stu-id="baa15-123">For example, if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall> a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> is called whenever a message arrives.</span></span>  
  
-   <span data-ttu-id="baa15-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: Toto je stejný jako předchozí metoda, s výjimkou to je volána, když je argument žádné zprávy.</span><span class="sxs-lookup"><span data-stu-id="baa15-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: This is identical to the previous method, except this is invoked when there is no Message argument.</span></span>  
  
-   <span data-ttu-id="baa15-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: Pokud dojde k uplynutí doby platnosti instance služby, volání dispečera <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> metoda.</span><span class="sxs-lookup"><span data-stu-id="baa15-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: When a service instance's lifetime has elapsed, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> method.</span></span> <span data-ttu-id="baa15-126">Stejně jako pro <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metody Četnost volání této metody je dáno <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="baa15-126">Just like for the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="baa15-127">Fond objektů</span><span class="sxs-lookup"><span data-stu-id="baa15-127">The Object Pool</span></span>  
 <span data-ttu-id="baa15-128">Vlastní <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementace poskytuje požadovaný objekt sdružování sémantiku pro službu.</span><span class="sxs-lookup"><span data-stu-id="baa15-128">A custom <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation provides the required object pooling semantics for a service.</span></span> <span data-ttu-id="baa15-129">Proto tato ukázka má `ObjectPoolingInstanceProvider` typ, který poskytuje vlastní implementaci <xref:System.ServiceModel.Dispatcher.IInstanceProvider> pro sdružování.</span><span class="sxs-lookup"><span data-stu-id="baa15-129">Therefore, this sample has an `ObjectPoolingInstanceProvider` type that provides custom implementation of <xref:System.ServiceModel.Dispatcher.IInstanceProvider> for pooling.</span></span> <span data-ttu-id="baa15-130">Když `Dispatcher` volání <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metody, místo vytvoření nové instance, vlastní implementaci vypadá pro existující objekt ve fondu v paměti.</span><span class="sxs-lookup"><span data-stu-id="baa15-130">When the `Dispatcher` calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="baa15-131">Pokud je k dispozici, je vrácena.</span><span class="sxs-lookup"><span data-stu-id="baa15-131">If one is available, it is returned.</span></span> <span data-ttu-id="baa15-132">Jinak se vytvoří nový objekt.</span><span class="sxs-lookup"><span data-stu-id="baa15-132">Otherwise, a new object is created.</span></span> <span data-ttu-id="baa15-133">Implementace pro `GetInstance` je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="baa15-133">The implementation for `GetInstance` is shown in the following sample code.</span></span>  
  
```  
object IInstanceProvider.GetInstance(InstanceContext instanceContext, Message message)  
{  
    object obj = null;  
  
    lock (poolLock)  
    {  
        if (pool.Count > 0)  
        {  
            obj = pool.Pop();  
        }  
        else  
        {  
            obj = CreateNewPoolObject();  
        }  
        activeObjectsCount++;  
    }  
  
    WritePoolMessage(ResourceHelper.GetString("MsgNewObject"));  
  
    idleTimer.Stop();  
  
    return obj;            
}  
```  
  
 <span data-ttu-id="baa15-134">Vlastní `ReleaseInstance` implementace přidá vydaná instance zpět do fondu a snižují se vždy `ActiveObjectsCount` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="baa15-134">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="baa15-135">`Dispatcher` Tyto metody můžete volat z různých vláknech a proto synchronizované přístupu na úrovni členy třídy v `ObjectPoolingInstanceProvider` je vyžadován.</span><span class="sxs-lookup"><span data-stu-id="baa15-135">The `Dispatcher` can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolingInstanceProvider` class is required.</span></span>  
  
```  
void IInstanceProvider.ReleaseInstance(InstanceContext instanceContext, object instance)  
{  
    lock (poolLock)  
    {  
        pool.Push(instance);  
        activeObjectsCount--;  
  
        WritePoolMessage(  
        ResourceHelper.GetString("MsgObjectPooled"));  
  
        // When the service goes completely idle (no requests   
        // are being processed), the idle timer is started  
        if (activeObjectsCount == 0)  
            idleTimer.Start();                       
    }  
}  
```  
  
 <span data-ttu-id="baa15-136">`ReleaseInstance` Metoda nabízí funkci "Vyčištění inicializace".</span><span class="sxs-lookup"><span data-stu-id="baa15-136">The `ReleaseInstance` method provides a "clean up initialization" feature.</span></span> <span data-ttu-id="baa15-137">Za normálních okolností fond udržuje minimální počet objektů po dobu jeho existence fondu.</span><span class="sxs-lookup"><span data-stu-id="baa15-137">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="baa15-138">Však může být období nadměrné využití, které vyžadují vytváření další objekty ve fondu k dosažení maximální limit zadaný v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="baa15-138">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="baa15-139">Nakonec když se stane fondu míň aktivní, tyto nadbytečné objekty se může stát zvýšené režii.</span><span class="sxs-lookup"><span data-stu-id="baa15-139">Eventually, when the pool becomes less active, those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="baa15-140">Proto když `activeObjectsCount` dosáhnou nula, nečinnosti časovače je spuštěno, který aktivuje vyčištění cyklus.</span><span class="sxs-lookup"><span data-stu-id="baa15-140">Therefore, when the `activeObjectsCount` reaches zero, an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
## <a name="adding-the-behavior"></a><span data-ttu-id="baa15-141">Přidání chování</span><span class="sxs-lookup"><span data-stu-id="baa15-141">Adding the Behavior</span></span>  
 <span data-ttu-id="baa15-142">Rozšíření dispečerů vrstvy se připojili pomocí následující chování:</span><span class="sxs-lookup"><span data-stu-id="baa15-142">Dispatcher-layer extensions are hooked up using the following behaviors:</span></span>  
  
-   <span data-ttu-id="baa15-143">Chování služby.</span><span class="sxs-lookup"><span data-stu-id="baa15-143">Service Behaviors.</span></span> <span data-ttu-id="baa15-144">Tyto rutiny umožňují k přizpůsobení modulu runtime celé služby.</span><span class="sxs-lookup"><span data-stu-id="baa15-144">These allow for the customization of the entire service runtime.</span></span>  
  
-   <span data-ttu-id="baa15-145">Koncový bod chování.</span><span class="sxs-lookup"><span data-stu-id="baa15-145">Endpoint Behaviors.</span></span> <span data-ttu-id="baa15-146">Tyto rutiny umožňují pro vlastní nastavení koncových bodů služby, konkrétně kanál a koncový bod dispečera.</span><span class="sxs-lookup"><span data-stu-id="baa15-146">These allow for the customization of service endpoints, specifically a Channel and Endpoint Dispatcher.</span></span>  
  
-   <span data-ttu-id="baa15-147">Kontrakt chování.</span><span class="sxs-lookup"><span data-stu-id="baa15-147">Contract Behaviors.</span></span> <span data-ttu-id="baa15-148">Tyto rutiny umožňují pro přizpůsobení obou <xref:System.ServiceModel.Dispatcher.ClientRuntime> a <xref:System.ServiceModel.Dispatcher.DispatchRuntime> třídy na klienta a služby v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="baa15-148">These allow for the customization of both <xref:System.ServiceModel.Dispatcher.ClientRuntime> and <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client and the service respectively.</span></span>  
  
 <span data-ttu-id="baa15-149">Pro účely objekt sdružování rozšíření musí být vytvořeny chování služby.</span><span class="sxs-lookup"><span data-stu-id="baa15-149">For the purpose of an object pooling extension a service behavior must be created.</span></span> <span data-ttu-id="baa15-150">Chování služby jsou vytvořené pomocí implementace <xref:System.ServiceModel.Description.IServiceBehavior> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="baa15-150">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="baa15-151">Chcete-li vědět, že vlastní chování modelu služby několika způsoby:</span><span class="sxs-lookup"><span data-stu-id="baa15-151">There are several ways to make the service model aware of the custom behaviors:</span></span>  
  
-   <span data-ttu-id="baa15-152">Pomocí vlastních atributů.</span><span class="sxs-lookup"><span data-stu-id="baa15-152">Using a custom attribute.</span></span>  
  
-   <span data-ttu-id="baa15-153">Imperativní přidáním do kolekce chování popis služby.</span><span class="sxs-lookup"><span data-stu-id="baa15-153">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
-   <span data-ttu-id="baa15-154">Rozšíření konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="baa15-154">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="baa15-155">Tato ukázka používá vlastní atribut.</span><span class="sxs-lookup"><span data-stu-id="baa15-155">This sample uses a custom attribute.</span></span> <span data-ttu-id="baa15-156">Když <xref:System.ServiceModel.ServiceHost> sestavený prověří atributy používané v definici služby typu a přidá do kolekce chování popis služby k dispozici chování.</span><span class="sxs-lookup"><span data-stu-id="baa15-156">When the <xref:System.ServiceModel.ServiceHost> is constructed it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="baa15-157">Rozhraní <xref:System.ServiceModel.Description.IServiceBehavior> má tři metody v ní – <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, a <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span><span class="sxs-lookup"><span data-stu-id="baa15-157">The interface <xref:System.ServiceModel.Description.IServiceBehavior> has three methods in it -- <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="baa15-158"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> Metoda se používá k zajištění, že chování může být použitá ke službě.</span><span class="sxs-lookup"><span data-stu-id="baa15-158">The <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> method is used to ensure that the behavior can be applied to the service.</span></span> <span data-ttu-id="baa15-159">V této ukázce implementace zajistí, že služba není nakonfigurována s <xref:System.ServiceModel.InstanceContextMode.Single>.</span><span class="sxs-lookup"><span data-stu-id="baa15-159">In this sample, the implementation ensures that the service is not configured with <xref:System.ServiceModel.InstanceContextMode.Single>.</span></span> <span data-ttu-id="baa15-160"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> Metoda slouží ke konfiguraci vazby služby.</span><span class="sxs-lookup"><span data-stu-id="baa15-160">The <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> method is used to configure the service's bindings.</span></span> <span data-ttu-id="baa15-161">V tomto scénáři není potřeba.</span><span class="sxs-lookup"><span data-stu-id="baa15-161">It is not required in this scenario.</span></span> <span data-ttu-id="baa15-162"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> Slouží ke konfiguraci služby dispečerů.</span><span class="sxs-lookup"><span data-stu-id="baa15-162">The <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> is used to configure the service's dispatchers.</span></span> <span data-ttu-id="baa15-163">Tato metoda je volána [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] při <xref:System.ServiceModel.ServiceHost> inicializace.</span><span class="sxs-lookup"><span data-stu-id="baa15-163">This method is called by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="baa15-164">Tyto parametry se předávají do této metody:</span><span class="sxs-lookup"><span data-stu-id="baa15-164">The following parameters are passed into this method:</span></span>  
  
-   <span data-ttu-id="baa15-165">`Description`: Tento argument obsahuje popis služby pro celé služby.</span><span class="sxs-lookup"><span data-stu-id="baa15-165">`Description`: This argument provides the service description for the entire service.</span></span> <span data-ttu-id="baa15-166">To slouží ke kontrole popis data o koncové body služby, kontrakty, vazby a další data.</span><span class="sxs-lookup"><span data-stu-id="baa15-166">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data.</span></span>  
  
-   <span data-ttu-id="baa15-167">`ServiceHostBase`: Poskytuje tento argument <xref:System.ServiceModel.ServiceHostBase> která aktuálně probíhá inicializace.</span><span class="sxs-lookup"><span data-stu-id="baa15-167">`ServiceHostBase`: This argument provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="baa15-168">Ve vlastní <xref:System.ServiceModel.Description.IServiceBehavior> implementace novou instanci služby `ObjectPoolingInstanceProvider` se vytvořit instanci a přiřadí do <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> vlastnost v každé <xref:System.ServiceModel.Dispatcher.DispatchRuntime> v ServiceHostBase.</span><span class="sxs-lookup"><span data-stu-id="baa15-168">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation a new instance of `ObjectPoolingInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.DispatchRuntime> in the ServiceHostBase.</span></span>  
  
```  
void IServiceBehavior.ApplyDispatchBehavior(ServiceDescription description, ServiceHostBase serviceHostBase)  
{  
    // Create an instance of the ObjectPoolInstanceProvider.  
    ObjectPoolingInstanceProvider instanceProvider = new  
           ObjectPoolingInstanceProvider(description.ServiceType,   
                                                    minPoolSize);  
  
    // Forward the call if we created a ServiceThrottlingBehavior.  
    if (this.throttlingBehavior != null)  
    {  
        ((IServiceBehavior)this.throttlingBehavior).ApplyDispatchBehavior(description, serviceHostBase);  
    }  
  
    // In case there was already a ServiceThrottlingBehavior   
    // (this.throttlingBehavior==null), it should have initialized   
    // a single ServiceThrottle on all ChannelDispatchers.    
    // As we loop through the ChannelDispatchers, we verify that   
    // and modify the ServiceThrottle to guard MaxPoolSize.  
    ServiceThrottle throttle = null;  
  
    foreach (ChannelDispatcherBase cdb in   
            serviceHostBase.ChannelDispatchers)  
    {  
        ChannelDispatcher cd = cdb as ChannelDispatcher;  
        if (cd != null)  
        {  
            // Make sure there is exactly one throttle used by all   
            // endpoints. If there were others, we could not enforce   
            // MaxPoolSize.  
            if ((this.throttlingBehavior == null) &&   
                        (this.maxPoolSize != Int32.MaxValue))  
            {  
                if (throttle == null)  
                {  
                    throttle = cd.ServiceThrottle;  
                }  
                if (cd.ServiceThrottle == null)  
                {  
                    throw new   
InvalidOperationException(ResourceHelper.GetString("ExNullThrottle"));  
                }  
                if (throttle != cd.ServiceThrottle)  
                {  
                    throw new InvalidOperationException(ResourceHelper.GetString("ExDifferentThrottle"));  
                }  
             }  
  
             foreach (EndpointDispatcher ed in cd.Endpoints)  
             {  
                 // Assign it to DispatchBehavior in each endpoint.  
                 ed.DispatchRuntime.InstanceProvider =   
                                      instanceProvider;  
             }  
         }  
     }  
  
     // Set the MaxConcurrentInstances to limit the number of items   
     // that will ever be requested from the pool.  
     if ((throttle != null) && (throttle.MaxConcurrentInstances >   
                                      this.maxPoolSize))  
     {  
         throttle.MaxConcurrentInstances = this.maxPoolSize;  
     }  
}  
```  
  
 <span data-ttu-id="baa15-169">Kromě <xref:System.ServiceModel.Description.IServiceBehavior> implementace <xref:System.EnterpriseServices.ObjectPoolingAttribute> třída obsahuje několik členů k přizpůsobení fondu objektů pomocí argumenty atributu.</span><span class="sxs-lookup"><span data-stu-id="baa15-169">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the <xref:System.EnterpriseServices.ObjectPoolingAttribute> class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="baa15-170">Zahrnout tito členové <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, a <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, tak, aby odpovídaly objekt sdružování sada funkcí poskytovaných služeb .NET Enterprise.</span><span class="sxs-lookup"><span data-stu-id="baa15-170">These members include <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, and <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="baa15-171">Objekt sdružování chování teď jde přidat do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby podle zadávání poznámek k implementaci služby s nově vytvořené vlastní `ObjectPooling` atribut.</span><span class="sxs-lookup"><span data-stu-id="baa15-171">The object pooling behavior can now be added to a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="baa15-172">Spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="baa15-172">Running the Sample</span></span>  
 <span data-ttu-id="baa15-173">Ukázka ukazuje výkon výhody, které můžete získaných pomocí sdružování objektů v některých scénářích.</span><span class="sxs-lookup"><span data-stu-id="baa15-173">The sample demonstrates the performance benefits that can be gained by using object pooling in certain scenarios.</span></span>  
  
 <span data-ttu-id="baa15-174">Aplikace služby implementuje dvou služeb – `WorkService` a `ObjectPooledWorkService`.</span><span class="sxs-lookup"><span data-stu-id="baa15-174">The service application implements two services -- `WorkService` and `ObjectPooledWorkService`.</span></span> <span data-ttu-id="baa15-175">Jak služby sdílet stejnou implementaci – jejich jak vyžadovat nákladný inicializace a následně je zpřístupněte `DoWork()` metoda, která je relativně levný.</span><span class="sxs-lookup"><span data-stu-id="baa15-175">Both services share the same implementation -- they both require expensive initialization and then expose a `DoWork()` method that is relatively cheap.</span></span> <span data-ttu-id="baa15-176">Jediným rozdílem je, že `ObjectPooledWorkService` má nakonfigurované sdružování objektů:</span><span class="sxs-lookup"><span data-stu-id="baa15-176">The only difference is that the `ObjectPooledWorkService` has object pooling configured:</span></span>  
  
```  
[ObjectPooling(MinPoolSize = 0, MaxPoolSize = 5)]  
public class ObjectPooledWorkService : IDoWork  
{  
    public ObjectPooledWorkService()  
    {  
        Thread.Sleep(5000);  
        ColorConsole.WriteLine(ConsoleColor.Blue, "ObjectPooledWorkService instance created.");  
    }  
  
    public void DoWork()  
    {  
        ColorConsole.WriteLine(ConsoleColor.Blue, "ObjectPooledWorkService.GetData() completed.");  
    }          
}  
```  
  
 <span data-ttu-id="baa15-177">Při spuštění klienta uplyne časový volání `WorkService` 5krát.</span><span class="sxs-lookup"><span data-stu-id="baa15-177">When you run the client, it times calling the `WorkService` 5 times.</span></span> <span data-ttu-id="baa15-178">Pak uplyne časový volání `ObjectPooledWorkService` 5krát.</span><span class="sxs-lookup"><span data-stu-id="baa15-178">It then times calling the `ObjectPooledWorkService` 5 times.</span></span> <span data-ttu-id="baa15-179">Rozdíl v čase se následně zobrazí:</span><span class="sxs-lookup"><span data-stu-id="baa15-179">The difference in time is then displayed:</span></span>  
  
```  
Press <ENTER> to start the client.  
  
Calling WorkService:  
1 - DoWork() Done  
2 - DoWork() Done  
3 - DoWork() Done  
4 - DoWork() Done  
5 - DoWork() Done  
Calling WorkService took: 26722 ms.  
Calling ObjectPooledWorkService:  
1 - DoWork() Done  
2 - DoWork() Done  
3 - DoWork() Done  
4 - DoWork() Done  
5 - DoWork() Done  
Calling ObjectPooledWorkService took: 5323 ms.  
Press <ENTER> to exit.  
```  
  
> [!NOTE]
>  <span data-ttu-id="baa15-180">Při prvním spuštění klienta obě služby jsou trvat o stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="baa15-180">The first time the client is run both services appear to take about the same amount of time.</span></span> <span data-ttu-id="baa15-181">Pokud znovu spustíte ukázku, můžete uvidíte, že `ObjectPooledWorkService` vrátí mnohem rychlejší, protože instance tohoto objektu již existuje ve fondu.</span><span class="sxs-lookup"><span data-stu-id="baa15-181">If you re-run the sample, you can see that the `ObjectPooledWorkService` returns much quicker because an instance of that object already exists in the pool.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="baa15-182">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="baa15-182">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="baa15-183">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="baa15-183">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="baa15-184">Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="baa15-184">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="baa15-185">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="baa15-185">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="baa15-186">Pokud používáte Svcutil.exe znovu vygenerovat konfigurace pro tuto ukázku, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídaly kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="baa15-186">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="baa15-187">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="baa15-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="baa15-188">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="baa15-188">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="baa15-189">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="baa15-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="baa15-190">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="baa15-190">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
  
## <a name="see-also"></a><span data-ttu-id="baa15-191">Viz také</span><span class="sxs-lookup"><span data-stu-id="baa15-191">See Also</span></span>
