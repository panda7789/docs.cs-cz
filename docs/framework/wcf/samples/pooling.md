---
title: Sdružování
ms.date: 03/30/2017
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
ms.openlocfilehash: 717dafb6ba9467590201511cbc0ac17690c931ae
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424272"
---
# <a name="pooling"></a><span data-ttu-id="28a5d-102">Sdružování</span><span class="sxs-lookup"><span data-stu-id="28a5d-102">Pooling</span></span>
<span data-ttu-id="28a5d-103">Tato ukázka předvádí, jak můžete Windows Communication Foundation (WCF) pro podporu sdružování objektů.</span><span class="sxs-lookup"><span data-stu-id="28a5d-103">This sample demonstrates how to extend Windows Communication Foundation (WCF) to support object pooling.</span></span> <span data-ttu-id="28a5d-104">Ukázka ukazuje, jak vytvořit atribut, který je syntakticky a sémanticky podobný funkci `ObjectPoolingAttribute` atributů podnikových služeb.</span><span class="sxs-lookup"><span data-stu-id="28a5d-104">The sample demonstrates how to create an attribute that is syntactically and semantically similar to the `ObjectPoolingAttribute` attribute functionality of Enterprise Services.</span></span> <span data-ttu-id="28a5d-105">Sdružování objektů může poskytovat výrazné zvýšení výkonu aplikace.</span><span class="sxs-lookup"><span data-stu-id="28a5d-105">Object pooling can provide a dramatic boost to an application's performance.</span></span> <span data-ttu-id="28a5d-106">Může ale mít opačný efekt, pokud se nepoužívá správně.</span><span class="sxs-lookup"><span data-stu-id="28a5d-106">However, it can have the opposite effect if it is not used properly.</span></span> <span data-ttu-id="28a5d-107">Sdružování objektů pomáhá snižovat režijní náklady na opětovné vytváření často používaných objektů, které vyžadují rozsáhlou inicializaci.</span><span class="sxs-lookup"><span data-stu-id="28a5d-107">Object pooling helps reduce the overhead of recreating frequently used objects that require extensive initialization.</span></span> <span data-ttu-id="28a5d-108">Nicméně pokud volání metody u objektu ve fondu trvá značnou dobu, sdružování objektů zařadí do fronty další požadavky hned po dosažení maximální velikosti fondu.</span><span class="sxs-lookup"><span data-stu-id="28a5d-108">However, if a call to a method on a pooled object takes a considerable amount of time to complete, object pooling queues additional requests as soon as the maximum pool size is reached.</span></span> <span data-ttu-id="28a5d-109">Proto může neúspěšné obsluhovat některé žádosti o vytvoření objektu vyvoláním výjimky časového limitu.</span><span class="sxs-lookup"><span data-stu-id="28a5d-109">Thus it may fail to serve some object creation requests by throwing a timeout exception.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="28a5d-110">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="28a5d-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="28a5d-111">Prvním krokem při vytváření rozšíření WCF je určení bodu rozšiřitelnosti, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="28a5d-111">The first step in creating a WCF extension is to decide the extensibility point to use.</span></span>  
  
 <span data-ttu-id="28a5d-112">V rámci WCF pojem *Dispatcher* označuje komponentu za běhu odpovědnou za převod příchozích zpráv do vyvolání metod v rámci služby uživatele a pro převod návratových hodnot z této metody na odchozí zprávu.</span><span class="sxs-lookup"><span data-stu-id="28a5d-112">In WCF the term *dispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="28a5d-113">Služba WCF vytvoří dispečera pro každý koncový bod.</span><span class="sxs-lookup"><span data-stu-id="28a5d-113">A WCF service creates a dispatcher for each endpoint.</span></span> <span data-ttu-id="28a5d-114">Klient WCF musí použít dispečera, pokud je kontrakt přidružený k tomuto klientovi duplexní smlouvou.</span><span class="sxs-lookup"><span data-stu-id="28a5d-114">A WCF client must use a dispatcher if the contract associated with that client is a duplex contract.</span></span>  
  
 <span data-ttu-id="28a5d-115">Odesílatelé kanálu a koncových bodů nabízejí rozšiřitelnost kanálu a smlouvy tím, že zveřejňují různé vlastnosti, které řídí chování dispečera.</span><span class="sxs-lookup"><span data-stu-id="28a5d-115">The channel and endpoint dispatchers offer channel-and contract-wide extensibility by exposing various properties that control the behavior of the dispatcher.</span></span> <span data-ttu-id="28a5d-116">Vlastnost <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> také umožňuje kontrolu, úpravu nebo přizpůsobení procesu odesílání.</span><span class="sxs-lookup"><span data-stu-id="28a5d-116">The <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> property also enables you to inspect, modify, or customize the dispatching process.</span></span> <span data-ttu-id="28a5d-117">Tato ukázka se zaměřuje na vlastnost <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, která odkazuje na objekt, který poskytuje instance třídy služby.</span><span class="sxs-lookup"><span data-stu-id="28a5d-117">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="the-iinstanceprovider"></a><span data-ttu-id="28a5d-118">IInstanceProvider</span><span class="sxs-lookup"><span data-stu-id="28a5d-118">The IInstanceProvider</span></span>  
 <span data-ttu-id="28a5d-119">Ve službě WCF vytvoří dispečer instance třídy služby pomocí <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, který implementuje rozhraní <xref:System.ServiceModel.Dispatcher.IInstanceProvider>.</span><span class="sxs-lookup"><span data-stu-id="28a5d-119">In WCF, the dispatcher creates instances of the service class using a <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, which implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="28a5d-120">Toto rozhraní má tři metody:</span><span class="sxs-lookup"><span data-stu-id="28a5d-120">This interface has three methods:</span></span>  
  
- <span data-ttu-id="28a5d-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: po doručení zprávy Dispečer volá metodu <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> k vytvoření instance třídy služby pro zpracování zprávy.</span><span class="sxs-lookup"><span data-stu-id="28a5d-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: When a message arrives the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="28a5d-122">Frekvence volání této metody je určena vlastností <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="28a5d-122">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="28a5d-123">Pokud je například vlastnost <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> nastavena na hodnotu <xref:System.ServiceModel.InstanceContextMode.PerCall> je vytvořena nová instance třídy služby pro zpracování každé zprávy, která dorazí, takže <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> je volána při doručení zprávy.</span><span class="sxs-lookup"><span data-stu-id="28a5d-123">For example, if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall> a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> is called whenever a message arrives.</span></span>  
  
- <span data-ttu-id="28a5d-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: Jedná se o shodu s předchozí metodou, s výjimkou toho, že je vyvolána, pokud neexistuje žádný argument zprávy.</span><span class="sxs-lookup"><span data-stu-id="28a5d-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: This is identical to the previous method, except this is invoked when there is no Message argument.</span></span>  
  
- <span data-ttu-id="28a5d-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: když uplyne doba života instance služby, Dispečer volá metodu <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>.</span><span class="sxs-lookup"><span data-stu-id="28a5d-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: When a service instance's lifetime has elapsed, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> method.</span></span> <span data-ttu-id="28a5d-126">Stejně jako u metody <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> je frekvence volání této metody určena vlastností <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="28a5d-126">Just like for the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="28a5d-127">Fond objektů</span><span class="sxs-lookup"><span data-stu-id="28a5d-127">The Object Pool</span></span>  
 <span data-ttu-id="28a5d-128">Vlastní implementace <xref:System.ServiceModel.Dispatcher.IInstanceProvider> poskytuje pro službu nezbytnou sémantiku sdružování objektů.</span><span class="sxs-lookup"><span data-stu-id="28a5d-128">A custom <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation provides the required object pooling semantics for a service.</span></span> <span data-ttu-id="28a5d-129">Proto má tato ukázka typ `ObjectPoolingInstanceProvider`, který poskytuje vlastní implementaci <xref:System.ServiceModel.Dispatcher.IInstanceProvider> pro sdružování.</span><span class="sxs-lookup"><span data-stu-id="28a5d-129">Therefore, this sample has an `ObjectPoolingInstanceProvider` type that provides custom implementation of <xref:System.ServiceModel.Dispatcher.IInstanceProvider> for pooling.</span></span> <span data-ttu-id="28a5d-130">Pokud `Dispatcher` volá metodu <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> namísto vytvoření nové instance, vlastní implementace vyhledá existující objekt ve fondu v paměti.</span><span class="sxs-lookup"><span data-stu-id="28a5d-130">When the `Dispatcher` calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="28a5d-131">Pokud je k dispozici, je vrácena.</span><span class="sxs-lookup"><span data-stu-id="28a5d-131">If one is available, it is returned.</span></span> <span data-ttu-id="28a5d-132">V opačném případě se vytvoří nový objekt.</span><span class="sxs-lookup"><span data-stu-id="28a5d-132">Otherwise, a new object is created.</span></span> <span data-ttu-id="28a5d-133">Implementace pro `GetInstance` je uvedena v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="28a5d-133">The implementation for `GetInstance` is shown in the following sample code.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="28a5d-134">Vlastní implementace `ReleaseInstance` přidá uvolněnou instanci zpátky do fondu a sníží hodnotu `ActiveObjectsCount`.</span><span class="sxs-lookup"><span data-stu-id="28a5d-134">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="28a5d-135">`Dispatcher` mohou volat tyto metody z různých vláken, a proto je vyžadován synchronizovaný přístup ke členům úrovně třídy ve třídě `ObjectPoolingInstanceProvider`.</span><span class="sxs-lookup"><span data-stu-id="28a5d-135">The `Dispatcher` can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolingInstanceProvider` class is required.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="28a5d-136">Metoda `ReleaseInstance` poskytuje funkci vyčištění při inicializaci.</span><span class="sxs-lookup"><span data-stu-id="28a5d-136">The `ReleaseInstance` method provides a "clean up initialization" feature.</span></span> <span data-ttu-id="28a5d-137">Fond běžně udržuje minimální počet objektů za dobu života fondu.</span><span class="sxs-lookup"><span data-stu-id="28a5d-137">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="28a5d-138">Nicméně můžou existovat období nadměrného využití, které vyžaduje vytvoření dalších objektů ve fondu, aby dosáhly maximálního limitu určeného v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="28a5d-138">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="28a5d-139">Pokud se ale fond stane méně aktivním, může se stát, že tyto nadbytečné objekty budou dodatečně režijní.</span><span class="sxs-lookup"><span data-stu-id="28a5d-139">Eventually, when the pool becomes less active, those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="28a5d-140">Proto když `activeObjectsCount` dosáhne nuly, spustí se časovač nečinnosti, který spustí a provede čisticí cyklus.</span><span class="sxs-lookup"><span data-stu-id="28a5d-140">Therefore, when the `activeObjectsCount` reaches zero, an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
## <a name="adding-the-behavior"></a><span data-ttu-id="28a5d-141">Přidání chování</span><span class="sxs-lookup"><span data-stu-id="28a5d-141">Adding the Behavior</span></span>  
 <span data-ttu-id="28a5d-142">Rozšíření dispečera vrstev jsou zapojená pomocí následujícího chování:</span><span class="sxs-lookup"><span data-stu-id="28a5d-142">Dispatcher-layer extensions are hooked up using the following behaviors:</span></span>  
  
- <span data-ttu-id="28a5d-143">Chování služby.</span><span class="sxs-lookup"><span data-stu-id="28a5d-143">Service Behaviors.</span></span> <span data-ttu-id="28a5d-144">Tyto možnosti umožňují přizpůsobení celého modulu runtime služby.</span><span class="sxs-lookup"><span data-stu-id="28a5d-144">These allow for the customization of the entire service runtime.</span></span>  
  
- <span data-ttu-id="28a5d-145">Chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="28a5d-145">Endpoint Behaviors.</span></span> <span data-ttu-id="28a5d-146">To umožňuje přizpůsobení koncových bodů služby, konkrétně kanálu a dispečera koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="28a5d-146">These allow for the customization of service endpoints, specifically a Channel and Endpoint Dispatcher.</span></span>  
  
- <span data-ttu-id="28a5d-147">Chování kontraktu.</span><span class="sxs-lookup"><span data-stu-id="28a5d-147">Contract Behaviors.</span></span> <span data-ttu-id="28a5d-148">Tato možnost umožňuje přizpůsobení <xref:System.ServiceModel.Dispatcher.ClientRuntime> a <xref:System.ServiceModel.Dispatcher.DispatchRuntime> třídy v klientovi i v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="28a5d-148">These allow for the customization of both <xref:System.ServiceModel.Dispatcher.ClientRuntime> and <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client and the service respectively.</span></span>  
  
 <span data-ttu-id="28a5d-149">Pro účely rozšíření sdružování objektů musí být vytvořeno chování služby.</span><span class="sxs-lookup"><span data-stu-id="28a5d-149">For the purpose of an object pooling extension a service behavior must be created.</span></span> <span data-ttu-id="28a5d-150">Chování služby se vytváří implementací rozhraní <xref:System.ServiceModel.Description.IServiceBehavior>.</span><span class="sxs-lookup"><span data-stu-id="28a5d-150">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="28a5d-151">Existuje několik způsobů, jak zajistit, aby Service Model věděli o vlastním chování:</span><span class="sxs-lookup"><span data-stu-id="28a5d-151">There are several ways to make the service model aware of the custom behaviors:</span></span>  
  
- <span data-ttu-id="28a5d-152">Použití vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="28a5d-152">Using a custom attribute.</span></span>  
  
- <span data-ttu-id="28a5d-153">Imperativně přidejte do kolekce chování popisu služby.</span><span class="sxs-lookup"><span data-stu-id="28a5d-153">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
- <span data-ttu-id="28a5d-154">Rozšíření konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="28a5d-154">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="28a5d-155">Tato ukázka používá vlastní atribut.</span><span class="sxs-lookup"><span data-stu-id="28a5d-155">This sample uses a custom attribute.</span></span> <span data-ttu-id="28a5d-156">Když je vytvořen <xref:System.ServiceModel.ServiceHost>, prověřuje atributy používané v definici typu služby a přidá k němu dostupné chování do kolekce chování popisu služby.</span><span class="sxs-lookup"><span data-stu-id="28a5d-156">When the <xref:System.ServiceModel.ServiceHost> is constructed it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="28a5d-157">Rozhraní <xref:System.ServiceModel.Description.IServiceBehavior> má v něm tři metody--<xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>a <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span><span class="sxs-lookup"><span data-stu-id="28a5d-157">The interface <xref:System.ServiceModel.Description.IServiceBehavior> has three methods in it -- <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="28a5d-158">Metoda <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> slouží k zajištění toho, aby bylo možné chování použít na službu.</span><span class="sxs-lookup"><span data-stu-id="28a5d-158">The <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> method is used to ensure that the behavior can be applied to the service.</span></span> <span data-ttu-id="28a5d-159">V této ukázce implementace zajišťuje, že služba není nakonfigurovaná s <xref:System.ServiceModel.InstanceContextMode.Single>.</span><span class="sxs-lookup"><span data-stu-id="28a5d-159">In this sample, the implementation ensures that the service is not configured with <xref:System.ServiceModel.InstanceContextMode.Single>.</span></span> <span data-ttu-id="28a5d-160">Metoda <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> slouží ke konfiguraci vazeb služby.</span><span class="sxs-lookup"><span data-stu-id="28a5d-160">The <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> method is used to configure the service's bindings.</span></span> <span data-ttu-id="28a5d-161">V tomto scénáři to není vyžadováno.</span><span class="sxs-lookup"><span data-stu-id="28a5d-161">It is not required in this scenario.</span></span> <span data-ttu-id="28a5d-162"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> slouží ke konfiguraci expedičních odpravcích služby.</span><span class="sxs-lookup"><span data-stu-id="28a5d-162">The <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> is used to configure the service's dispatchers.</span></span> <span data-ttu-id="28a5d-163">Tato metoda je volána službou WCF při inicializaci <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="28a5d-163">This method is called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="28a5d-164">Do této metody jsou předány následující parametry:</span><span class="sxs-lookup"><span data-stu-id="28a5d-164">The following parameters are passed into this method:</span></span>  
  
- <span data-ttu-id="28a5d-165">`Description`: Tento argument poskytuje popis služby pro celou službu.</span><span class="sxs-lookup"><span data-stu-id="28a5d-165">`Description`: This argument provides the service description for the entire service.</span></span> <span data-ttu-id="28a5d-166">Tato možnost slouží k prověření popisných dat o koncových bodech, kontraktech, vazbách a dalších datech služby.</span><span class="sxs-lookup"><span data-stu-id="28a5d-166">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data.</span></span>  
  
- <span data-ttu-id="28a5d-167">`ServiceHostBase`: Tento argument poskytuje <xref:System.ServiceModel.ServiceHostBase>, který se právě inicializuje.</span><span class="sxs-lookup"><span data-stu-id="28a5d-167">`ServiceHostBase`: This argument provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="28a5d-168">Ve vlastní <xref:System.ServiceModel.Description.IServiceBehavior> implementace nové instance `ObjectPoolingInstanceProvider` je vytvořena instance a přiřazena vlastnosti <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> v každém <xref:System.ServiceModel.Dispatcher.DispatchRuntime> v objektu ServiceHostBase.</span><span class="sxs-lookup"><span data-stu-id="28a5d-168">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation a new instance of `ObjectPoolingInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.DispatchRuntime> in the ServiceHostBase.</span></span>  
  
```csharp  
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
                throttle ??= cd.ServiceThrottle;
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
  
 <span data-ttu-id="28a5d-169">Kromě <xref:System.ServiceModel.Description.IServiceBehavior> implementace má <xref:System.EnterpriseServices.ObjectPoolingAttribute> třídy několik členů k přizpůsobení fondu objektů pomocí argumentů atributu.</span><span class="sxs-lookup"><span data-stu-id="28a5d-169">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the <xref:System.EnterpriseServices.ObjectPoolingAttribute> class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="28a5d-170">Mezi tyto členy patří <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>a <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, aby odpovídaly sadě funkcí sdružování objektů poskytované službou .NET Enterprise Services.</span><span class="sxs-lookup"><span data-stu-id="28a5d-170">These members include <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, and <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="28a5d-171">Chování sdružování objektů lze nyní přidat do služby WCF zadáním poznámky k implementaci služby pomocí nově vytvořeného vlastního atributu `ObjectPooling`.</span><span class="sxs-lookup"><span data-stu-id="28a5d-171">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```csharp  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="28a5d-172">Spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="28a5d-172">Running the Sample</span></span>  
 <span data-ttu-id="28a5d-173">Ukázka předvádí výhody výkonu, které lze v určitých scénářích využít při vytváření fondů objektů.</span><span class="sxs-lookup"><span data-stu-id="28a5d-173">The sample demonstrates the performance benefits that can be gained by using object pooling in certain scenarios.</span></span>  
  
 <span data-ttu-id="28a5d-174">Aplikace služby implementuje dvě služby – `WorkService` a `ObjectPooledWorkService`.</span><span class="sxs-lookup"><span data-stu-id="28a5d-174">The service application implements two services -- `WorkService` and `ObjectPooledWorkService`.</span></span> <span data-ttu-id="28a5d-175">Obě služby sdílejí stejnou implementaci – obě služby vyžadují nákladný inicializaci a pak zveřejňují `DoWork()`é metody, které jsou poměrně levné.</span><span class="sxs-lookup"><span data-stu-id="28a5d-175">Both services share the same implementation -- they both require expensive initialization and then expose a `DoWork()` method that is relatively cheap.</span></span> <span data-ttu-id="28a5d-176">Jediným rozdílem je, že `ObjectPooledWorkService` má nakonfigurované sdružování objektů:</span><span class="sxs-lookup"><span data-stu-id="28a5d-176">The only difference is that the `ObjectPooledWorkService` has object pooling configured:</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="28a5d-177">Když spustíte klienta nástroje, čas zavolá `WorkService` 5 časů.</span><span class="sxs-lookup"><span data-stu-id="28a5d-177">When you run the client, it times calling the `WorkService` 5 times.</span></span> <span data-ttu-id="28a5d-178">Pak časy, které volají `ObjectPooledWorkService` 5 časů.</span><span class="sxs-lookup"><span data-stu-id="28a5d-178">It then times calling the `ObjectPooledWorkService` 5 times.</span></span> <span data-ttu-id="28a5d-179">Rozdíl v čase se pak zobrazí:</span><span class="sxs-lookup"><span data-stu-id="28a5d-179">The difference in time is then displayed:</span></span>  
  
```console
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
> <span data-ttu-id="28a5d-180">Při prvním spuštění klienta se obě služby projeví přibližně po stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="28a5d-180">The first time the client is run both services appear to take about the same amount of time.</span></span> <span data-ttu-id="28a5d-181">Pokud ukázku znovu spustíte, vidíte, že `ObjectPooledWorkService` vrátí mnohem rychlejší, protože ve fondu již existuje instance daného objektu.</span><span class="sxs-lookup"><span data-stu-id="28a5d-181">If you re-run the sample, you can see that the `ObjectPooledWorkService` returns much quicker because an instance of that object already exists in the pool.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="28a5d-182">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="28a5d-182">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="28a5d-183">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="28a5d-183">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="28a5d-184">Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="28a5d-184">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="28a5d-185">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="28a5d-185">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="28a5d-186">Pokud pro obnovení konfigurace této ukázky používáte Svcutil. exe, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídal kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="28a5d-186">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="28a5d-187">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="28a5d-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="28a5d-188">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="28a5d-188">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="28a5d-189">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="28a5d-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="28a5d-190">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="28a5d-190">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
