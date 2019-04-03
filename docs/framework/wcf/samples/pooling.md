---
title: Sdružování
ms.date: 03/30/2017
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
ms.openlocfilehash: 91fdb34a82446aab1528835132efd31e2858191c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832434"
---
# <a name="pooling"></a><span data-ttu-id="1fb10-102">Sdružování</span><span class="sxs-lookup"><span data-stu-id="1fb10-102">Pooling</span></span>
<span data-ttu-id="1fb10-103">Tato ukázka předvádí, jak rozšířit Windows Communication Foundation (WCF) pro podporu sdružování objektů.</span><span class="sxs-lookup"><span data-stu-id="1fb10-103">This sample demonstrates how to extend Windows Communication Foundation (WCF) to support object pooling.</span></span> <span data-ttu-id="1fb10-104">Vzorek ukazuje, jak vytvořit atribut, který je syntakticky a sémanticky podobné `ObjectPoolingAttribute` atribut funkce podnikové služby.</span><span class="sxs-lookup"><span data-stu-id="1fb10-104">The sample demonstrates how to create an attribute that is syntactically and semantically similar to the `ObjectPoolingAttribute` attribute functionality of Enterprise Services.</span></span> <span data-ttu-id="1fb10-105">Sdružování objektů umožňují výrazné zvýšení výkonu aplikace.</span><span class="sxs-lookup"><span data-stu-id="1fb10-105">Object pooling can provide a dramatic boost to an application's performance.</span></span> <span data-ttu-id="1fb10-106">Pokud se nepoužívá správně však může mít opačný efekt.</span><span class="sxs-lookup"><span data-stu-id="1fb10-106">However, it can have the opposite effect if it is not used properly.</span></span> <span data-ttu-id="1fb10-107">Sdružování objektů pomáhá snižovat režijní náklady na opětovné vytvoření často používané objekty, které vyžadují rozsáhlé inicializace.</span><span class="sxs-lookup"><span data-stu-id="1fb10-107">Object pooling helps reduce the overhead of recreating frequently used objects that require extensive initialization.</span></span> <span data-ttu-id="1fb10-108">Nicméně pokud volání metody na objektu ve fondu trvá značné množství času k dokončení, sdružování objektů zařadí do fronty dalších žádostí ihned poté, co je dosaženo maximální velikosti fondu.</span><span class="sxs-lookup"><span data-stu-id="1fb10-108">However, if a call to a method on a pooled object takes a considerable amount of time to complete, object pooling queues additional requests as soon as the maximum pool size is reached.</span></span> <span data-ttu-id="1fb10-109">Proto může dojít k selhání obsluhovat požadavky na vytvoření některý objekt vyvoláním výjimka časového limitu.</span><span class="sxs-lookup"><span data-stu-id="1fb10-109">Thus it may fail to serve some object creation requests by throwing a timeout exception.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1fb10-110">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="1fb10-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="1fb10-111">Prvním krokem při vytváření rozšíření WCF je rozhodnout bodu rozšiřitelnosti pro použití.</span><span class="sxs-lookup"><span data-stu-id="1fb10-111">The first step in creating a WCF extension is to decide the extensibility point to use.</span></span>  
  
 <span data-ttu-id="1fb10-112">Ve službě WCF termín *dispečer* odkazuje na komponentu za běhu pro převod příchozích zpráv do volání metod na uživatele služby a pro převod vrácené hodnoty z této metody na odchozí zprávu.</span><span class="sxs-lookup"><span data-stu-id="1fb10-112">In WCF the term *dispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="1fb10-113">Služba WCF vytvoří dispečer pro každý koncový bod.</span><span class="sxs-lookup"><span data-stu-id="1fb10-113">A WCF service creates a dispatcher for each endpoint.</span></span> <span data-ttu-id="1fb10-114">Pokud kontrakt přidružený tento klient je duplexního kontraktu, musíte použít klienta WCF dispečerem.</span><span class="sxs-lookup"><span data-stu-id="1fb10-114">A WCF client must use a dispatcher if the contract associated with that client is a duplex contract.</span></span>  
  
 <span data-ttu-id="1fb10-115">Nabízejí dispečerů kanálu a koncového bodu kanálu – a rozšiřitelnost smlouvy celou zveřejněním různé vlastnosti, které řídí chování dispečer.</span><span class="sxs-lookup"><span data-stu-id="1fb10-115">The channel and endpoint dispatchers offer channel-and contract-wide extensibility by exposing various properties that control the behavior of the dispatcher.</span></span> <span data-ttu-id="1fb10-116"><xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> Vlastnosti můžete také zkontrolovat, upravit nebo přizpůsobit dispatching proces.</span><span class="sxs-lookup"><span data-stu-id="1fb10-116">The <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> property also enables you to inspect, modify, or customize the dispatching process.</span></span> <span data-ttu-id="1fb10-117">Tato ukázka se zaměřuje na <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> vlastnost, která odkazuje na objekt, který poskytuje instance třídy service.</span><span class="sxs-lookup"><span data-stu-id="1fb10-117">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="the-iinstanceprovider"></a><span data-ttu-id="1fb10-118">IInstanceProvider</span><span class="sxs-lookup"><span data-stu-id="1fb10-118">The IInstanceProvider</span></span>  
 <span data-ttu-id="1fb10-119">Ve službě WCF, dispečer vytvoří instance třídy pomocí služeb <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, která implementuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1fb10-119">In WCF, the dispatcher creates instances of the service class using a <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, which implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="1fb10-120">Toto rozhraní obsahuje tři metody:</span><span class="sxs-lookup"><span data-stu-id="1fb10-120">This interface has three methods:</span></span>  
  
-   <span data-ttu-id="1fb10-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: Při přijetí e-mailu dispečer volání <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metodu pro vytvoření instance třídy službu ke zpracování zprávy.</span><span class="sxs-lookup"><span data-stu-id="1fb10-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: When a message arrives the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="1fb10-122">Četnost volání této metody se zakládá <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1fb10-122">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="1fb10-123">Například pokud <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> je nastavena na <xref:System.ServiceModel.InstanceContextMode.PerCall> zpracovat každou zprávu, která dorazí, tak se vytvoří novou instanci třídy služby <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> je volána při každém přijetí e-mailu.</span><span class="sxs-lookup"><span data-stu-id="1fb10-123">For example, if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall> a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> is called whenever a message arrives.</span></span>  
  
-   <span data-ttu-id="1fb10-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: Toto je stejný jako předchozí metoda, s výjimkou toto se vyvolá, pokud neexistuje žádný argument zprávy.</span><span class="sxs-lookup"><span data-stu-id="1fb10-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: This is identical to the previous method, except this is invoked when there is no Message argument.</span></span>  
  
-   <span data-ttu-id="1fb10-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: Po uplynutí doby života instance služby, dispečer volání <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> metody.</span><span class="sxs-lookup"><span data-stu-id="1fb10-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: When a service instance's lifetime has elapsed, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> method.</span></span> <span data-ttu-id="1fb10-126">Stejně jako u <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metoda, je určena Četnost volání této metody <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1fb10-126">Just like for the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="1fb10-127">Fond objektů</span><span class="sxs-lookup"><span data-stu-id="1fb10-127">The Object Pool</span></span>  
 <span data-ttu-id="1fb10-128">Vlastní <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementace poskytuje požadovaný objekt sdružování sémantiky pro službu.</span><span class="sxs-lookup"><span data-stu-id="1fb10-128">A custom <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation provides the required object pooling semantics for a service.</span></span> <span data-ttu-id="1fb10-129">Proto tato ukázka má `ObjectPoolingInstanceProvider` typ, který poskytuje vlastní implementaci <xref:System.ServiceModel.Dispatcher.IInstanceProvider> pro sdružování.</span><span class="sxs-lookup"><span data-stu-id="1fb10-129">Therefore, this sample has an `ObjectPoolingInstanceProvider` type that provides custom implementation of <xref:System.ServiceModel.Dispatcher.IInstanceProvider> for pooling.</span></span> <span data-ttu-id="1fb10-130">Když `Dispatcher` volání <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metody, místo vytvoření nové instance, vlastní implementaci hledá existující objekt ve fondu v paměti.</span><span class="sxs-lookup"><span data-stu-id="1fb10-130">When the `Dispatcher` calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="1fb10-131">Pokud je k dispozici, bude vrácen.</span><span class="sxs-lookup"><span data-stu-id="1fb10-131">If one is available, it is returned.</span></span> <span data-ttu-id="1fb10-132">V opačném případě se vytvoří nový objekt.</span><span class="sxs-lookup"><span data-stu-id="1fb10-132">Otherwise, a new object is created.</span></span> <span data-ttu-id="1fb10-133">Implementace `GetInstance` je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="1fb10-133">The implementation for `GetInstance` is shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="1fb10-134">Vlastní `ReleaseInstance` implementace přidá vydané instanci zpět do fondu a sníží `ActiveObjectsCount` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1fb10-134">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="1fb10-135">`Dispatcher` Tyto metody lze volat z různých vláken a proto synchronizaci přístupu k členům třídy úrovni v `ObjectPoolingInstanceProvider` třída je povinné.</span><span class="sxs-lookup"><span data-stu-id="1fb10-135">The `Dispatcher` can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolingInstanceProvider` class is required.</span></span>  
  
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
  
 <span data-ttu-id="1fb10-136">`ReleaseInstance` Metoda obsahuje funkci "vyčistit inicializace".</span><span class="sxs-lookup"><span data-stu-id="1fb10-136">The `ReleaseInstance` method provides a "clean up initialization" feature.</span></span> <span data-ttu-id="1fb10-137">Fondu obvykle udržuje minimální počet objektů, které po dobu životnosti fondu.</span><span class="sxs-lookup"><span data-stu-id="1fb10-137">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="1fb10-138">Může však být období nadměrnému využití, které vyžadují vytvoření další objekty ve fondu k dosažení maximální limit zadaný v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="1fb10-138">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="1fb10-139">Nakonec Jakmile fondu je méně aktivní, tyto objekty nadbytečné se může stát další režii.</span><span class="sxs-lookup"><span data-stu-id="1fb10-139">Eventually, when the pool becomes less active, those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="1fb10-140">Proto, když `activeObjectsCount` dosáhne nulu, nečinnosti časovače, který se aktivuje a provede vyčištění cyklus spuštění.</span><span class="sxs-lookup"><span data-stu-id="1fb10-140">Therefore, when the `activeObjectsCount` reaches zero, an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
## <a name="adding-the-behavior"></a><span data-ttu-id="1fb10-141">Přidání chování</span><span class="sxs-lookup"><span data-stu-id="1fb10-141">Adding the Behavior</span></span>  
 <span data-ttu-id="1fb10-142">Rozšíření vrstvě dispečera se připojili pomocí následujícího chování:</span><span class="sxs-lookup"><span data-stu-id="1fb10-142">Dispatcher-layer extensions are hooked up using the following behaviors:</span></span>  
  
-   <span data-ttu-id="1fb10-143">Chování služby.</span><span class="sxs-lookup"><span data-stu-id="1fb10-143">Service Behaviors.</span></span> <span data-ttu-id="1fb10-144">Tyto rutiny umožňují pro přizpůsobení celé služby modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="1fb10-144">These allow for the customization of the entire service runtime.</span></span>  
  
-   <span data-ttu-id="1fb10-145">Chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="1fb10-145">Endpoint Behaviors.</span></span> <span data-ttu-id="1fb10-146">Tyto rutiny umožňují pro přizpůsobení koncových bodů služby, konkrétně kanálu a Dispečer koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="1fb10-146">These allow for the customization of service endpoints, specifically a Channel and Endpoint Dispatcher.</span></span>  
  
-   <span data-ttu-id="1fb10-147">Chování kontraktu.</span><span class="sxs-lookup"><span data-stu-id="1fb10-147">Contract Behaviors.</span></span> <span data-ttu-id="1fb10-148">Tyto rutiny umožňují pro přizpůsobení obou <xref:System.ServiceModel.Dispatcher.ClientRuntime> a <xref:System.ServiceModel.Dispatcher.DispatchRuntime> třídy na klienta a služby v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="1fb10-148">These allow for the customization of both <xref:System.ServiceModel.Dispatcher.ClientRuntime> and <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client and the service respectively.</span></span>  
  
 <span data-ttu-id="1fb10-149">Pro účely objekt sdružování rozšíření musí být vytvořeny chování služby.</span><span class="sxs-lookup"><span data-stu-id="1fb10-149">For the purpose of an object pooling extension a service behavior must be created.</span></span> <span data-ttu-id="1fb10-150">Chování služby jsou vytvořeny pomocí implementace <xref:System.ServiceModel.Description.IServiceBehavior> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1fb10-150">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="1fb10-151">Existuje několik způsobů, jak vytvořit model služby používající vlastní chování:</span><span class="sxs-lookup"><span data-stu-id="1fb10-151">There are several ways to make the service model aware of the custom behaviors:</span></span>  
  
-   <span data-ttu-id="1fb10-152">Pomocí vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="1fb10-152">Using a custom attribute.</span></span>  
  
-   <span data-ttu-id="1fb10-153">Imperativně přidáním do kolekce chování popisu služby.</span><span class="sxs-lookup"><span data-stu-id="1fb10-153">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
-   <span data-ttu-id="1fb10-154">Rozšíření konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="1fb10-154">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="1fb10-155">Tato ukázka používá vlastní atribut.</span><span class="sxs-lookup"><span data-stu-id="1fb10-155">This sample uses a custom attribute.</span></span> <span data-ttu-id="1fb10-156">Když <xref:System.ServiceModel.ServiceHost> je vytvořená prozkoumá atributy použité v definici služby typu a přidá do kolekce chování popis služby k dispozici chování.</span><span class="sxs-lookup"><span data-stu-id="1fb10-156">When the <xref:System.ServiceModel.ServiceHost> is constructed it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="1fb10-157">Rozhraní <xref:System.ServiceModel.Description.IServiceBehavior> má tři metody v ní <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, a <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span><span class="sxs-lookup"><span data-stu-id="1fb10-157">The interface <xref:System.ServiceModel.Description.IServiceBehavior> has three methods in it -- <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="1fb10-158"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> Metoda se používá k zajištění, že chování lze použít ke službě.</span><span class="sxs-lookup"><span data-stu-id="1fb10-158">The <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> method is used to ensure that the behavior can be applied to the service.</span></span> <span data-ttu-id="1fb10-159">V této ukázce se implementace zajistí, že služba není nakonfigurována s <xref:System.ServiceModel.InstanceContextMode.Single>.</span><span class="sxs-lookup"><span data-stu-id="1fb10-159">In this sample, the implementation ensures that the service is not configured with <xref:System.ServiceModel.InstanceContextMode.Single>.</span></span> <span data-ttu-id="1fb10-160"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> Metoda se používá ke konfiguraci vazby služby.</span><span class="sxs-lookup"><span data-stu-id="1fb10-160">The <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> method is used to configure the service's bindings.</span></span> <span data-ttu-id="1fb10-161">V tomto scénáři není potřeba.</span><span class="sxs-lookup"><span data-stu-id="1fb10-161">It is not required in this scenario.</span></span> <span data-ttu-id="1fb10-162"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> Slouží ke konfiguraci služby dispečerů.</span><span class="sxs-lookup"><span data-stu-id="1fb10-162">The <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> is used to configure the service's dispatchers.</span></span> <span data-ttu-id="1fb10-163">Tato metoda je volána službou WCF při <xref:System.ServiceModel.ServiceHost> je inicializována.</span><span class="sxs-lookup"><span data-stu-id="1fb10-163">This method is called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="1fb10-164">Následující parametry jsou předány do této metody:</span><span class="sxs-lookup"><span data-stu-id="1fb10-164">The following parameters are passed into this method:</span></span>  
  
-   <span data-ttu-id="1fb10-165">`Description`: Tento argument obsahuje popis služby pro celou službu.</span><span class="sxs-lookup"><span data-stu-id="1fb10-165">`Description`: This argument provides the service description for the entire service.</span></span> <span data-ttu-id="1fb10-166">To lze použít ke kontrole popis data o koncové body služby, kontrakty, vazby a další data.</span><span class="sxs-lookup"><span data-stu-id="1fb10-166">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data.</span></span>  
  
-   <span data-ttu-id="1fb10-167">`ServiceHostBase`: Poskytuje tento argument <xref:System.ServiceModel.ServiceHostBase> , který je aktuálně inicializována.</span><span class="sxs-lookup"><span data-stu-id="1fb10-167">`ServiceHostBase`: This argument provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="1fb10-168">Ve vlastní <xref:System.ServiceModel.Description.IServiceBehavior> implementace novou instanci sady `ObjectPoolingInstanceProvider` vytvořena a přiřazená <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> vlastnost v každém <xref:System.ServiceModel.Dispatcher.DispatchRuntime> v objektu ServiceHostBase.</span><span class="sxs-lookup"><span data-stu-id="1fb10-168">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation a new instance of `ObjectPoolingInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.DispatchRuntime> in the ServiceHostBase.</span></span>  
  
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
  
 <span data-ttu-id="1fb10-169">Kromě <xref:System.ServiceModel.Description.IServiceBehavior> implementace <xref:System.EnterpriseServices.ObjectPoolingAttribute> třída má několik členů k přizpůsobení fondu objektů pomocí argumentů atributu.</span><span class="sxs-lookup"><span data-stu-id="1fb10-169">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the <xref:System.EnterpriseServices.ObjectPoolingAttribute> class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="1fb10-170">Zahrnout tyto členy <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, a <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, tak, aby odpovídaly objekt sdružování sadu funkcí poskytovanou služeb .NET Enterprise.</span><span class="sxs-lookup"><span data-stu-id="1fb10-170">These members include <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, and <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="1fb10-171">Objekt sdružování chování lze nyní přidat ke službě WCF anotací implementace služby nově vytvořené vlastním `ObjectPooling` atribut.</span><span class="sxs-lookup"><span data-stu-id="1fb10-171">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="1fb10-172">Spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="1fb10-172">Running the Sample</span></span>  
 <span data-ttu-id="1fb10-173">Ukázce přinese zlepšení výkonu, které může být získaná použitím sdružování objektů v některých scénářích.</span><span class="sxs-lookup"><span data-stu-id="1fb10-173">The sample demonstrates the performance benefits that can be gained by using object pooling in certain scenarios.</span></span>  
  
 <span data-ttu-id="1fb10-174">Aplikace služby implementuje dvou služeb – `WorkService` a `ObjectPooledWorkService`.</span><span class="sxs-lookup"><span data-stu-id="1fb10-174">The service application implements two services -- `WorkService` and `ObjectPooledWorkService`.</span></span> <span data-ttu-id="1fb10-175">Obě služby sdílet stejnou implementaci – jejich vyžadovat nákladná inicializace i pak vystavit `DoWork()` metod, které jsou relativně levné.</span><span class="sxs-lookup"><span data-stu-id="1fb10-175">Both services share the same implementation -- they both require expensive initialization and then expose a `DoWork()` method that is relatively cheap.</span></span> <span data-ttu-id="1fb10-176">Jediným rozdílem je, že `ObjectPooledWorkService` má nakonfigurované sdružování objektů:</span><span class="sxs-lookup"><span data-stu-id="1fb10-176">The only difference is that the `ObjectPooledWorkService` has object pooling configured:</span></span>  
  
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
  
 <span data-ttu-id="1fb10-177">Když spustíte klienta, dojde k jejímu volání `WorkService` 5krát.</span><span class="sxs-lookup"><span data-stu-id="1fb10-177">When you run the client, it times calling the `WorkService` 5 times.</span></span> <span data-ttu-id="1fb10-178">Uplyne volání `ObjectPooledWorkService` 5krát.</span><span class="sxs-lookup"><span data-stu-id="1fb10-178">It then times calling the `ObjectPooledWorkService` 5 times.</span></span> <span data-ttu-id="1fb10-179">Rozdíl v čase se následně zobrazí:</span><span class="sxs-lookup"><span data-stu-id="1fb10-179">The difference in time is then displayed:</span></span>  
  
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
>  <span data-ttu-id="1fb10-180">Při prvním spuštění klienta obě služby se to trvat přibližně stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="1fb10-180">The first time the client is run both services appear to take about the same amount of time.</span></span> <span data-ttu-id="1fb10-181">Pokud znovu spustíte ukázku, vidíte, že `ObjectPooledWorkService` vrátí mnohem rychlejší, protože instance tohoto objektu již existuje ve fondu.</span><span class="sxs-lookup"><span data-stu-id="1fb10-181">If you re-run the sample, you can see that the `ObjectPooledWorkService` returns much quicker because an instance of that object already exists in the pool.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1fb10-182">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="1fb10-182">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="1fb10-183">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1fb10-183">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="1fb10-184">Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1fb10-184">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="1fb10-185">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1fb10-185">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1fb10-186">Pokud používáte Svcutil.exe k opětovnému vytvoření konfigurace pro tuto ukázku, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídaly klientský kód.</span><span class="sxs-lookup"><span data-stu-id="1fb10-186">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1fb10-187">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="1fb10-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1fb10-188">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="1fb10-188">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1fb10-189">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="1fb10-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1fb10-190">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="1fb10-190">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
  
