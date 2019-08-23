---
title: Sdružování
ms.date: 03/30/2017
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
ms.openlocfilehash: a01b7897031bb379dd8aaa30e32454c08b14cc08
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965539"
---
# <a name="pooling"></a><span data-ttu-id="7773c-102">Sdružování</span><span class="sxs-lookup"><span data-stu-id="7773c-102">Pooling</span></span>
<span data-ttu-id="7773c-103">Tato ukázka předvádí, jak můžete Windows Communication Foundation (WCF) pro podporu sdružování objektů.</span><span class="sxs-lookup"><span data-stu-id="7773c-103">This sample demonstrates how to extend Windows Communication Foundation (WCF) to support object pooling.</span></span> <span data-ttu-id="7773c-104">Ukázka ukazuje, jak vytvořit atribut, který je syntakticky a sémanticky podobný `ObjectPoolingAttribute` funkci atributu Enterprise Services.</span><span class="sxs-lookup"><span data-stu-id="7773c-104">The sample demonstrates how to create an attribute that is syntactically and semantically similar to the `ObjectPoolingAttribute` attribute functionality of Enterprise Services.</span></span> <span data-ttu-id="7773c-105">Sdružování objektů může poskytovat výrazné zvýšení výkonu aplikace.</span><span class="sxs-lookup"><span data-stu-id="7773c-105">Object pooling can provide a dramatic boost to an application's performance.</span></span> <span data-ttu-id="7773c-106">Může ale mít opačný efekt, pokud se nepoužívá správně.</span><span class="sxs-lookup"><span data-stu-id="7773c-106">However, it can have the opposite effect if it is not used properly.</span></span> <span data-ttu-id="7773c-107">Sdružování objektů pomáhá snižovat režijní náklady na opětovné vytváření často používaných objektů, které vyžadují rozsáhlou inicializaci.</span><span class="sxs-lookup"><span data-stu-id="7773c-107">Object pooling helps reduce the overhead of recreating frequently used objects that require extensive initialization.</span></span> <span data-ttu-id="7773c-108">Nicméně pokud volání metody u objektu ve fondu trvá značnou dobu, sdružování objektů zařadí do fronty další požadavky hned po dosažení maximální velikosti fondu.</span><span class="sxs-lookup"><span data-stu-id="7773c-108">However, if a call to a method on a pooled object takes a considerable amount of time to complete, object pooling queues additional requests as soon as the maximum pool size is reached.</span></span> <span data-ttu-id="7773c-109">Proto může neúspěšné obsluhovat některé žádosti o vytvoření objektu vyvoláním výjimky časového limitu.</span><span class="sxs-lookup"><span data-stu-id="7773c-109">Thus it may fail to serve some object creation requests by throwing a timeout exception.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7773c-110">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="7773c-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7773c-111">Prvním krokem při vytváření rozšíření WCF je určení bodu rozšiřitelnosti, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="7773c-111">The first step in creating a WCF extension is to decide the extensibility point to use.</span></span>  
  
 <span data-ttu-id="7773c-112">V rámci WCF pojem *Dispatcher* označuje komponentu za běhu odpovědnou za převod příchozích zpráv do vyvolání metod v rámci služby uživatele a pro převod návratových hodnot z této metody na odchozí zprávu.</span><span class="sxs-lookup"><span data-stu-id="7773c-112">In WCF the term *dispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="7773c-113">Služba WCF vytvoří dispečera pro každý koncový bod.</span><span class="sxs-lookup"><span data-stu-id="7773c-113">A WCF service creates a dispatcher for each endpoint.</span></span> <span data-ttu-id="7773c-114">Klient WCF musí použít dispečera, pokud je kontrakt přidružený k tomuto klientovi duplexní smlouvou.</span><span class="sxs-lookup"><span data-stu-id="7773c-114">A WCF client must use a dispatcher if the contract associated with that client is a duplex contract.</span></span>  
  
 <span data-ttu-id="7773c-115">Odesílatelé kanálu a koncových bodů nabízejí rozšiřitelnost kanálu a smlouvy tím, že zveřejňují různé vlastnosti, které řídí chování dispečera.</span><span class="sxs-lookup"><span data-stu-id="7773c-115">The channel and endpoint dispatchers offer channel-and contract-wide extensibility by exposing various properties that control the behavior of the dispatcher.</span></span> <span data-ttu-id="7773c-116"><xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> Vlastnost také umožňuje kontrolu, úpravu nebo přizpůsobení procesu odesílání.</span><span class="sxs-lookup"><span data-stu-id="7773c-116">The <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> property also enables you to inspect, modify, or customize the dispatching process.</span></span> <span data-ttu-id="7773c-117">Tato ukázka se <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> zaměřuje na vlastnost, která odkazuje na objekt, který poskytuje instance třídy služby.</span><span class="sxs-lookup"><span data-stu-id="7773c-117">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="the-iinstanceprovider"></a><span data-ttu-id="7773c-118">IInstanceProvider</span><span class="sxs-lookup"><span data-stu-id="7773c-118">The IInstanceProvider</span></span>  
 <span data-ttu-id="7773c-119">Ve službě WCF vytvoří dispečer instance třídy služby pomocí <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, který <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7773c-119">In WCF, the dispatcher creates instances of the service class using a <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, which implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="7773c-120">Toto rozhraní má tři metody:</span><span class="sxs-lookup"><span data-stu-id="7773c-120">This interface has three methods:</span></span>  
  
- <span data-ttu-id="7773c-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: Když zpráva dorazí dispečera, <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> volá metodu pro vytvoření instance třídy služby ke zpracování zprávy.</span><span class="sxs-lookup"><span data-stu-id="7773c-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: When a message arrives the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="7773c-122">Frekvence volání této metody je určena <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastností.</span><span class="sxs-lookup"><span data-stu-id="7773c-122">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="7773c-123">Například pokud <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> je vlastnost nastavena na <xref:System.ServiceModel.InstanceContextMode.PerCall> novou instanci třídy služby, je vytvořena pro zpracování každé zprávy, která dorazí, takže <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> se zavolá při každém přijetí zprávy.</span><span class="sxs-lookup"><span data-stu-id="7773c-123">For example, if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall> a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> is called whenever a message arrives.</span></span>  
  
- <span data-ttu-id="7773c-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: To je shodné s předchozí metodou, s výjimkou toho, že je vyvolána, pokud neexistuje žádný argument zprávy.</span><span class="sxs-lookup"><span data-stu-id="7773c-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: This is identical to the previous method, except this is invoked when there is no Message argument.</span></span>  
  
- <span data-ttu-id="7773c-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: Když uplyne doba života instance služby, Dispečer volá <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> metodu.</span><span class="sxs-lookup"><span data-stu-id="7773c-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: When a service instance's lifetime has elapsed, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> method.</span></span> <span data-ttu-id="7773c-126">Stejně jako u <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metody je frekvence volání této metody určena <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastností.</span><span class="sxs-lookup"><span data-stu-id="7773c-126">Just like for the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="7773c-127">Fond objektů</span><span class="sxs-lookup"><span data-stu-id="7773c-127">The Object Pool</span></span>  
 <span data-ttu-id="7773c-128">Vlastní <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementace poskytuje pro službu nezbytnou sémantiku sdružování objektů.</span><span class="sxs-lookup"><span data-stu-id="7773c-128">A custom <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation provides the required object pooling semantics for a service.</span></span> <span data-ttu-id="7773c-129">Proto má `ObjectPoolingInstanceProvider` Tato ukázka typ, který poskytuje vlastní <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementaci pro sdružování.</span><span class="sxs-lookup"><span data-stu-id="7773c-129">Therefore, this sample has an `ObjectPoolingInstanceProvider` type that provides custom implementation of <xref:System.ServiceModel.Dispatcher.IInstanceProvider> for pooling.</span></span> <span data-ttu-id="7773c-130">`Dispatcher` Při<xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> volání metody místo vytvoření nové instance vyhledá vlastní implementace existující objekt ve fondu v paměti.</span><span class="sxs-lookup"><span data-stu-id="7773c-130">When the `Dispatcher` calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="7773c-131">Pokud je k dispozici, je vrácena.</span><span class="sxs-lookup"><span data-stu-id="7773c-131">If one is available, it is returned.</span></span> <span data-ttu-id="7773c-132">V opačném případě se vytvoří nový objekt.</span><span class="sxs-lookup"><span data-stu-id="7773c-132">Otherwise, a new object is created.</span></span> <span data-ttu-id="7773c-133">Implementace pro `GetInstance` je uvedena v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="7773c-133">The implementation for `GetInstance` is shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="7773c-134">Vlastní `ReleaseInstance` implementace přidá uvolněnou instanci zpátky do fondu a sníží `ActiveObjectsCount` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7773c-134">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="7773c-135">Rozhraní `Dispatcher` může volat tyto metody z různých vláken, a proto je vyžadován synchronizovaný přístup ke členům úrovně třídy `ObjectPoolingInstanceProvider` ve třídě.</span><span class="sxs-lookup"><span data-stu-id="7773c-135">The `Dispatcher` can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolingInstanceProvider` class is required.</span></span>  
  
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
  
 <span data-ttu-id="7773c-136">`ReleaseInstance` Metoda poskytuje funkci Vyčištění inicializace.</span><span class="sxs-lookup"><span data-stu-id="7773c-136">The `ReleaseInstance` method provides a "clean up initialization" feature.</span></span> <span data-ttu-id="7773c-137">Fond běžně udržuje minimální počet objektů za dobu života fondu.</span><span class="sxs-lookup"><span data-stu-id="7773c-137">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="7773c-138">Nicméně můžou existovat období nadměrného využití, které vyžaduje vytvoření dalších objektů ve fondu, aby dosáhly maximálního limitu určeného v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="7773c-138">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="7773c-139">Pokud se ale fond stane méně aktivním, může se stát, že tyto nadbytečné objekty budou dodatečně režijní.</span><span class="sxs-lookup"><span data-stu-id="7773c-139">Eventually, when the pool becomes less active, those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="7773c-140">Proto když `activeObjectsCount` se dosáhne nuly, spustí se časovač nečinnosti, který spustí a provede čisticí cyklus.</span><span class="sxs-lookup"><span data-stu-id="7773c-140">Therefore, when the `activeObjectsCount` reaches zero, an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
## <a name="adding-the-behavior"></a><span data-ttu-id="7773c-141">Přidání chování</span><span class="sxs-lookup"><span data-stu-id="7773c-141">Adding the Behavior</span></span>  
 <span data-ttu-id="7773c-142">Rozšíření dispečera vrstev jsou zapojená pomocí následujícího chování:</span><span class="sxs-lookup"><span data-stu-id="7773c-142">Dispatcher-layer extensions are hooked up using the following behaviors:</span></span>  
  
- <span data-ttu-id="7773c-143">Chování služby.</span><span class="sxs-lookup"><span data-stu-id="7773c-143">Service Behaviors.</span></span> <span data-ttu-id="7773c-144">Tyto možnosti umožňují přizpůsobení celého modulu runtime služby.</span><span class="sxs-lookup"><span data-stu-id="7773c-144">These allow for the customization of the entire service runtime.</span></span>  
  
- <span data-ttu-id="7773c-145">Chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="7773c-145">Endpoint Behaviors.</span></span> <span data-ttu-id="7773c-146">To umožňuje přizpůsobení koncových bodů služby, konkrétně kanálu a dispečera koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="7773c-146">These allow for the customization of service endpoints, specifically a Channel and Endpoint Dispatcher.</span></span>  
  
- <span data-ttu-id="7773c-147">Chování kontraktu.</span><span class="sxs-lookup"><span data-stu-id="7773c-147">Contract Behaviors.</span></span> <span data-ttu-id="7773c-148">Tyto možnosti umožňují přizpůsobení obou <xref:System.ServiceModel.Dispatcher.ClientRuntime> <xref:System.ServiceModel.Dispatcher.DispatchRuntime> tříd i na straně klienta i služby.</span><span class="sxs-lookup"><span data-stu-id="7773c-148">These allow for the customization of both <xref:System.ServiceModel.Dispatcher.ClientRuntime> and <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client and the service respectively.</span></span>  
  
 <span data-ttu-id="7773c-149">Pro účely rozšíření sdružování objektů musí být vytvořeno chování služby.</span><span class="sxs-lookup"><span data-stu-id="7773c-149">For the purpose of an object pooling extension a service behavior must be created.</span></span> <span data-ttu-id="7773c-150">Chování služby je vytvořeno implementací <xref:System.ServiceModel.Description.IServiceBehavior> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7773c-150">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="7773c-151">Existuje několik způsobů, jak zajistit, aby Service Model věděli o vlastním chování:</span><span class="sxs-lookup"><span data-stu-id="7773c-151">There are several ways to make the service model aware of the custom behaviors:</span></span>  
  
- <span data-ttu-id="7773c-152">Použití vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="7773c-152">Using a custom attribute.</span></span>  
  
- <span data-ttu-id="7773c-153">Imperativně přidejte do kolekce chování popisu služby.</span><span class="sxs-lookup"><span data-stu-id="7773c-153">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
- <span data-ttu-id="7773c-154">Rozšíření konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="7773c-154">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="7773c-155">Tato ukázka používá vlastní atribut.</span><span class="sxs-lookup"><span data-stu-id="7773c-155">This sample uses a custom attribute.</span></span> <span data-ttu-id="7773c-156"><xref:System.ServiceModel.ServiceHost> Když je vytvořen, prochází atributy používané v definici typu služby a přidává dostupné chování do kolekce chování popisu služby.</span><span class="sxs-lookup"><span data-stu-id="7773c-156">When the <xref:System.ServiceModel.ServiceHost> is constructed it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="7773c-157">Rozhraní <xref:System.ServiceModel.Description.IServiceBehavior> má v něm <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>tři metody, a <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span><span class="sxs-lookup"><span data-stu-id="7773c-157">The interface <xref:System.ServiceModel.Description.IServiceBehavior> has three methods in it -- <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="7773c-158"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> Metoda se používá k zajištění toho, aby bylo možné chování použít na službu.</span><span class="sxs-lookup"><span data-stu-id="7773c-158">The <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> method is used to ensure that the behavior can be applied to the service.</span></span> <span data-ttu-id="7773c-159">V této ukázce implementace zajišťuje, aby služba nebyla nakonfigurovaná pomocí <xref:System.ServiceModel.InstanceContextMode.Single>.</span><span class="sxs-lookup"><span data-stu-id="7773c-159">In this sample, the implementation ensures that the service is not configured with <xref:System.ServiceModel.InstanceContextMode.Single>.</span></span> <span data-ttu-id="7773c-160"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> Metoda se používá ke konfiguraci vazeb služby.</span><span class="sxs-lookup"><span data-stu-id="7773c-160">The <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> method is used to configure the service's bindings.</span></span> <span data-ttu-id="7773c-161">V tomto scénáři to není vyžadováno.</span><span class="sxs-lookup"><span data-stu-id="7773c-161">It is not required in this scenario.</span></span> <span data-ttu-id="7773c-162"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> Slouží ke konfiguraci expedičních odpravcích služby.</span><span class="sxs-lookup"><span data-stu-id="7773c-162">The <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> is used to configure the service's dispatchers.</span></span> <span data-ttu-id="7773c-163">Tato metoda je volána službou WCF při <xref:System.ServiceModel.ServiceHost> inicializaci.</span><span class="sxs-lookup"><span data-stu-id="7773c-163">This method is called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="7773c-164">Do této metody jsou předány následující parametry:</span><span class="sxs-lookup"><span data-stu-id="7773c-164">The following parameters are passed into this method:</span></span>  
  
- <span data-ttu-id="7773c-165">`Description`: Tento argument poskytuje popis služby pro celou službu.</span><span class="sxs-lookup"><span data-stu-id="7773c-165">`Description`: This argument provides the service description for the entire service.</span></span> <span data-ttu-id="7773c-166">Tato možnost slouží k prověření popisných dat o koncových bodech, kontraktech, vazbách a dalších datech služby.</span><span class="sxs-lookup"><span data-stu-id="7773c-166">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data.</span></span>  
  
- <span data-ttu-id="7773c-167">`ServiceHostBase`: Tento argument poskytuje <xref:System.ServiceModel.ServiceHostBase> aktuálně inicializovaný.</span><span class="sxs-lookup"><span data-stu-id="7773c-167">`ServiceHostBase`: This argument provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="7773c-168">V vlastní <xref:System.ServiceModel.Description.IServiceBehavior> implementaci `ObjectPoolingInstanceProvider` je vytvořena instance nové instance a přiřazena k <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> vlastnosti v každé <xref:System.ServiceModel.Dispatcher.DispatchRuntime> z objektu ServiceHostBase.</span><span class="sxs-lookup"><span data-stu-id="7773c-168">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation a new instance of `ObjectPoolingInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.DispatchRuntime> in the ServiceHostBase.</span></span>  
  
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
  
 <span data-ttu-id="7773c-169"><xref:System.ServiceModel.Description.IServiceBehavior> Kromě<xref:System.EnterpriseServices.ObjectPoolingAttribute> implementace má třída více členů k přizpůsobení fondu objektů pomocí argumentů atributu.</span><span class="sxs-lookup"><span data-stu-id="7773c-169">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the <xref:System.EnterpriseServices.ObjectPoolingAttribute> class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="7773c-170">Mezi tyto členy <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>patří <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>,, <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>a, aby odpovídaly sadě funkcí sdružování objektů poskytované službami .NET Enterprise Services.</span><span class="sxs-lookup"><span data-stu-id="7773c-170">These members include <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, and <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="7773c-171">Chování sdružování objektů se teď dá přidat ke službě WCF tím, že se pokládá na implementaci služby s nově vytvořeným vlastním `ObjectPooling` atributem.</span><span class="sxs-lookup"><span data-stu-id="7773c-171">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="7773c-172">Spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="7773c-172">Running the Sample</span></span>  
 <span data-ttu-id="7773c-173">Ukázka předvádí výhody výkonu, které lze v určitých scénářích využít při vytváření fondů objektů.</span><span class="sxs-lookup"><span data-stu-id="7773c-173">The sample demonstrates the performance benefits that can be gained by using object pooling in certain scenarios.</span></span>  
  
 <span data-ttu-id="7773c-174">Aplikace služby implementuje dvě služby – `WorkService` a. `ObjectPooledWorkService`</span><span class="sxs-lookup"><span data-stu-id="7773c-174">The service application implements two services -- `WorkService` and `ObjectPooledWorkService`.</span></span> <span data-ttu-id="7773c-175">Obě služby sdílejí stejnou implementaci – oba vyžadují nákladný inicializaci a pak zveřejňují `DoWork()` metodu, která je poměrně levné.</span><span class="sxs-lookup"><span data-stu-id="7773c-175">Both services share the same implementation -- they both require expensive initialization and then expose a `DoWork()` method that is relatively cheap.</span></span> <span data-ttu-id="7773c-176">Jediným rozdílem je, že `ObjectPooledWorkService` má nakonfigurované sdružování objektů:</span><span class="sxs-lookup"><span data-stu-id="7773c-176">The only difference is that the `ObjectPooledWorkService` has object pooling configured:</span></span>  
  
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
  
 <span data-ttu-id="7773c-177">Když spustíte klienta nástroje, čas zavolá `WorkService` 5 časů.</span><span class="sxs-lookup"><span data-stu-id="7773c-177">When you run the client, it times calling the `WorkService` 5 times.</span></span> <span data-ttu-id="7773c-178">Pak časy, které `ObjectPooledWorkService` volají 5 časů.</span><span class="sxs-lookup"><span data-stu-id="7773c-178">It then times calling the `ObjectPooledWorkService` 5 times.</span></span> <span data-ttu-id="7773c-179">Rozdíl v čase se pak zobrazí:</span><span class="sxs-lookup"><span data-stu-id="7773c-179">The difference in time is then displayed:</span></span>  
  
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
> <span data-ttu-id="7773c-180">Při prvním spuštění klienta se obě služby projeví přibližně po stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="7773c-180">The first time the client is run both services appear to take about the same amount of time.</span></span> <span data-ttu-id="7773c-181">Pokud ukázku znovu spustíte, vidíte, že `ObjectPooledWorkService` výsledek vrátí mnohem rychlejší, protože ve fondu již existuje instance daného objektu.</span><span class="sxs-lookup"><span data-stu-id="7773c-181">If you re-run the sample, you can see that the `ObjectPooledWorkService` returns much quicker because an instance of that object already exists in the pool.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7773c-182">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="7773c-182">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="7773c-183">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7773c-183">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="7773c-184">Při sestavování řešení postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7773c-184">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="7773c-185">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7773c-185">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7773c-186">Pokud pro obnovení konfigurace této ukázky používáte Svcutil. exe, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídal kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="7773c-186">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7773c-187">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="7773c-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7773c-188">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="7773c-188">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7773c-189">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="7773c-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7773c-190">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="7773c-190">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
