---
title: Sdružování
ms.date: 03/30/2017
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
ms.openlocfilehash: 46abc2c9c667ea7614581d7fafaa8e174db7f14f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183409"
---
# <a name="pooling"></a><span data-ttu-id="12f2d-102">Sdružování</span><span class="sxs-lookup"><span data-stu-id="12f2d-102">Pooling</span></span>
<span data-ttu-id="12f2d-103">Tato ukázka ukazuje, jak rozšířit Windows Communication Foundation (WCF) pro podporu sdružování objektů.</span><span class="sxs-lookup"><span data-stu-id="12f2d-103">This sample demonstrates how to extend Windows Communication Foundation (WCF) to support object pooling.</span></span> <span data-ttu-id="12f2d-104">Ukázka ukazuje, jak vytvořit atribut, který je syntakticky `ObjectPoolingAttribute` a sémanticky podobný atribut funkce Enterprise Services.</span><span class="sxs-lookup"><span data-stu-id="12f2d-104">The sample demonstrates how to create an attribute that is syntactically and semantically similar to the `ObjectPoolingAttribute` attribute functionality of Enterprise Services.</span></span> <span data-ttu-id="12f2d-105">Sdružování objektů může poskytnout dramatické zvýšení výkonu aplikace.</span><span class="sxs-lookup"><span data-stu-id="12f2d-105">Object pooling can provide a dramatic boost to an application's performance.</span></span> <span data-ttu-id="12f2d-106">Může však mít opačný účinek, pokud není správně používán.</span><span class="sxs-lookup"><span data-stu-id="12f2d-106">However, it can have the opposite effect if it is not used properly.</span></span> <span data-ttu-id="12f2d-107">Sdružování objektů pomáhá snížit režii opětovného vytvoření často používaných objektů, které vyžadují rozsáhlou inicializaci.</span><span class="sxs-lookup"><span data-stu-id="12f2d-107">Object pooling helps reduce the overhead of recreating frequently used objects that require extensive initialization.</span></span> <span data-ttu-id="12f2d-108">Pokud však volání metody na sdružený objekt trvá značné množství času na dokončení, sdružování objektů fronty další požadavky, jakmile je dosaženo maximální velikost i fondu.</span><span class="sxs-lookup"><span data-stu-id="12f2d-108">However, if a call to a method on a pooled object takes a considerable amount of time to complete, object pooling queues additional requests as soon as the maximum pool size is reached.</span></span> <span data-ttu-id="12f2d-109">Proto může selhat sloužit některé požadavky na vytvoření objektu vyvoláním výjimku časového času.</span><span class="sxs-lookup"><span data-stu-id="12f2d-109">Thus it may fail to serve some object creation requests by throwing a timeout exception.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="12f2d-110">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="12f2d-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="12f2d-111">Prvním krokem při vytváření rozšíření WCF je rozhodnout bod rozšiřitelnosti použít.</span><span class="sxs-lookup"><span data-stu-id="12f2d-111">The first step in creating a WCF extension is to decide the extensibility point to use.</span></span>  
  
 <span data-ttu-id="12f2d-112">V WCF termín *dispečer* odkazuje na součást za běhu odpovědné za převod příchozích zpráv na vyvolání metody ve službě uživatele a pro převod vrácené hodnoty z této metody na odchozí zprávu.</span><span class="sxs-lookup"><span data-stu-id="12f2d-112">In WCF the term *dispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="12f2d-113">Služba WCF vytvoří dispečera pro každý koncový bod.</span><span class="sxs-lookup"><span data-stu-id="12f2d-113">A WCF service creates a dispatcher for each endpoint.</span></span> <span data-ttu-id="12f2d-114">Klient WCF musí použít dispečera, pokud je smlouva přidružená k tomuto klientovi duplexní smlouvou.</span><span class="sxs-lookup"><span data-stu-id="12f2d-114">A WCF client must use a dispatcher if the contract associated with that client is a duplex contract.</span></span>  
  
 <span data-ttu-id="12f2d-115">Dispečeři kanálu a koncového bodu nabízejí rozšiřitelnost celého kanálu a kontraktu tím, že vystavují různé vlastnosti, které řídí chování dispečera.</span><span class="sxs-lookup"><span data-stu-id="12f2d-115">The channel and endpoint dispatchers offer channel-and contract-wide extensibility by exposing various properties that control the behavior of the dispatcher.</span></span> <span data-ttu-id="12f2d-116">Vlastnost <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> také umožňuje kontrolovat, upravovat nebo přizpůsobit proces odesílání.</span><span class="sxs-lookup"><span data-stu-id="12f2d-116">The <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> property also enables you to inspect, modify, or customize the dispatching process.</span></span> <span data-ttu-id="12f2d-117">Tato ukázka se <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> zaměřuje na vlastnost, která odkazuje na objekt, který poskytuje instance třídy služby.</span><span class="sxs-lookup"><span data-stu-id="12f2d-117">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="the-iinstanceprovider"></a><span data-ttu-id="12f2d-118">Zprostředkovatel iinstance</span><span class="sxs-lookup"><span data-stu-id="12f2d-118">The IInstanceProvider</span></span>  
 <span data-ttu-id="12f2d-119">V WCF dispečer vytvoří instance třídy <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>služby pomocí <xref:System.ServiceModel.Dispatcher.IInstanceProvider> , který implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="12f2d-119">In WCF, the dispatcher creates instances of the service class using a <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, which implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="12f2d-120">Toto rozhraní má tři metody:</span><span class="sxs-lookup"><span data-stu-id="12f2d-120">This interface has three methods:</span></span>  
  
- <span data-ttu-id="12f2d-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: Když přijde zpráva Dispečer volá metodu <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> k vytvoření instance třídy služby ke zpracování zprávy.</span><span class="sxs-lookup"><span data-stu-id="12f2d-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: When a message arrives the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="12f2d-122">Frekvence volání této metody je určena <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastností.</span><span class="sxs-lookup"><span data-stu-id="12f2d-122">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="12f2d-123">Například pokud <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> je vlastnost <xref:System.ServiceModel.InstanceContextMode.PerCall> nastavena na novou instanci třídy služby <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> je vytvořen pro zpracování každé zprávy, která dorazí, tak se nazývá vždy, když zpráva dorazí.</span><span class="sxs-lookup"><span data-stu-id="12f2d-123">For example, if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall> a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> is called whenever a message arrives.</span></span>  
  
- <span data-ttu-id="12f2d-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: Toto je shodné s předchozí metodou, s výjimkou tohoto je vyvolána, pokud neexistuje žádný Message argument.</span><span class="sxs-lookup"><span data-stu-id="12f2d-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: This is identical to the previous method, except this is invoked when there is no Message argument.</span></span>  
  
- <span data-ttu-id="12f2d-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: Po uplynutí životnosti instance služby dispečer <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> volá metodu.</span><span class="sxs-lookup"><span data-stu-id="12f2d-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: When a service instance's lifetime has elapsed, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> method.</span></span> <span data-ttu-id="12f2d-126">Stejně jako <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> pro metodu, frekvence volání této metody <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> je určena vlastnost.</span><span class="sxs-lookup"><span data-stu-id="12f2d-126">Just like for the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="12f2d-127">Fond objektů</span><span class="sxs-lookup"><span data-stu-id="12f2d-127">The Object Pool</span></span>  
 <span data-ttu-id="12f2d-128">Vlastní <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementace poskytuje požadované objektsdrálky sémantiku pro službu.</span><span class="sxs-lookup"><span data-stu-id="12f2d-128">A custom <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation provides the required object pooling semantics for a service.</span></span> <span data-ttu-id="12f2d-129">Proto tato ukázka `ObjectPoolingInstanceProvider` má typ, <xref:System.ServiceModel.Dispatcher.IInstanceProvider> který poskytuje vlastní implementaci pro sdružování.</span><span class="sxs-lookup"><span data-stu-id="12f2d-129">Therefore, this sample has an `ObjectPoolingInstanceProvider` type that provides custom implementation of <xref:System.ServiceModel.Dispatcher.IInstanceProvider> for pooling.</span></span> <span data-ttu-id="12f2d-130">Při `Dispatcher` volání <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metody, namísto vytvoření nové instance, vlastní implementace hledá existující objekt ve fondu v paměti.</span><span class="sxs-lookup"><span data-stu-id="12f2d-130">When the `Dispatcher` calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="12f2d-131">Pokud je k dispozici, je vrácena.</span><span class="sxs-lookup"><span data-stu-id="12f2d-131">If one is available, it is returned.</span></span> <span data-ttu-id="12f2d-132">V opačném případě je vytvořen nový objekt.</span><span class="sxs-lookup"><span data-stu-id="12f2d-132">Otherwise, a new object is created.</span></span> <span data-ttu-id="12f2d-133">Implementace pro `GetInstance` je uveden v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="12f2d-133">The implementation for `GetInstance` is shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="12f2d-134">Vlastní `ReleaseInstance` implementace přidá uvolněnou instanci zpět do `ActiveObjectsCount` fondu a sníží hodnotu.</span><span class="sxs-lookup"><span data-stu-id="12f2d-134">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="12f2d-135">Můžete `Dispatcher` volat tyto metody z různých vláken, a proto je vyžadován `ObjectPoolingInstanceProvider` synchronizovaný přístup k členům na úrovni třídy ve třídě.</span><span class="sxs-lookup"><span data-stu-id="12f2d-135">The `Dispatcher` can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolingInstanceProvider` class is required.</span></span>  
  
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
  
 <span data-ttu-id="12f2d-136">Metoda `ReleaseInstance` poskytuje funkci "vyčištění inicializace".</span><span class="sxs-lookup"><span data-stu-id="12f2d-136">The `ReleaseInstance` method provides a "clean up initialization" feature.</span></span> <span data-ttu-id="12f2d-137">Obvykle fond udržuje minimální počet objektů po dobu životnosti fondu.</span><span class="sxs-lookup"><span data-stu-id="12f2d-137">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="12f2d-138">Však může být období nadměrného využití, které vyžadují vytvoření další objekty ve fondu k dosažení maximální limit zadaný v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="12f2d-138">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="12f2d-139">Nakonec při fondu stane méně aktivní, tyto nadbytečné objekty se může stát další režii.</span><span class="sxs-lookup"><span data-stu-id="12f2d-139">Eventually, when the pool becomes less active, those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="12f2d-140">Proto když `activeObjectsCount` dosáhne nuly, spustí se časovač nečinnosti, který aktivuje a provede cyklus čištění.</span><span class="sxs-lookup"><span data-stu-id="12f2d-140">Therefore, when the `activeObjectsCount` reaches zero, an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
## <a name="adding-the-behavior"></a><span data-ttu-id="12f2d-141">Přidání chování</span><span class="sxs-lookup"><span data-stu-id="12f2d-141">Adding the Behavior</span></span>  
 <span data-ttu-id="12f2d-142">Rozšíření vrstvy dispečera jsou zahnutý nahoru pomocí následující chod:</span><span class="sxs-lookup"><span data-stu-id="12f2d-142">Dispatcher-layer extensions are hooked up using the following behaviors:</span></span>  
  
- <span data-ttu-id="12f2d-143">Chování služby.</span><span class="sxs-lookup"><span data-stu-id="12f2d-143">Service Behaviors.</span></span> <span data-ttu-id="12f2d-144">Ty umožňují přizpůsobení celého běhu služby.</span><span class="sxs-lookup"><span data-stu-id="12f2d-144">These allow for the customization of the entire service runtime.</span></span>  
  
- <span data-ttu-id="12f2d-145">Chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="12f2d-145">Endpoint Behaviors.</span></span> <span data-ttu-id="12f2d-146">Ty umožňují přizpůsobení koncových bodů služby, konkrétně dispečera kanálu a koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="12f2d-146">These allow for the customization of service endpoints, specifically a Channel and Endpoint Dispatcher.</span></span>  
  
- <span data-ttu-id="12f2d-147">Chování smlouvy.</span><span class="sxs-lookup"><span data-stu-id="12f2d-147">Contract Behaviors.</span></span> <span data-ttu-id="12f2d-148">Ty umožňují přizpůsobení obou <xref:System.ServiceModel.Dispatcher.ClientRuntime> <xref:System.ServiceModel.Dispatcher.DispatchRuntime> tříd a tříd na straně klienta a služby v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="12f2d-148">These allow for the customization of both <xref:System.ServiceModel.Dispatcher.ClientRuntime> and <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client and the service respectively.</span></span>  
  
 <span data-ttu-id="12f2d-149">Pro účely rozšíření sdružování objektů musí být vytvořeno chování služby.</span><span class="sxs-lookup"><span data-stu-id="12f2d-149">For the purpose of an object pooling extension a service behavior must be created.</span></span> <span data-ttu-id="12f2d-150">Chování služby jsou vytvořeny <xref:System.ServiceModel.Description.IServiceBehavior> implementací rozhraní.</span><span class="sxs-lookup"><span data-stu-id="12f2d-150">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="12f2d-151">Existuje několik způsobů, jak seznámit model služby o vlastní chování:</span><span class="sxs-lookup"><span data-stu-id="12f2d-151">There are several ways to make the service model aware of the custom behaviors:</span></span>  
  
- <span data-ttu-id="12f2d-152">Použití vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="12f2d-152">Using a custom attribute.</span></span>  
  
- <span data-ttu-id="12f2d-153">Imperativně přidání do kolekce chování popis služby.</span><span class="sxs-lookup"><span data-stu-id="12f2d-153">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
- <span data-ttu-id="12f2d-154">Rozšíření konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="12f2d-154">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="12f2d-155">Tato ukázka používá vlastní atribut.</span><span class="sxs-lookup"><span data-stu-id="12f2d-155">This sample uses a custom attribute.</span></span> <span data-ttu-id="12f2d-156">Když <xref:System.ServiceModel.ServiceHost> je vytvořen zkoumá atributy použité v definici typu služby a přidá dostupné chování do kolekce chování popis služby.</span><span class="sxs-lookup"><span data-stu-id="12f2d-156">When the <xref:System.ServiceModel.ServiceHost> is constructed it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="12f2d-157">Rozhraní <xref:System.ServiceModel.Description.IServiceBehavior> má v něm <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>tři <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>metody <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>-- , a .</span><span class="sxs-lookup"><span data-stu-id="12f2d-157">The interface <xref:System.ServiceModel.Description.IServiceBehavior> has three methods in it -- <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="12f2d-158">Metoda <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> se používá k zajištění, že chování lze použít na službu.</span><span class="sxs-lookup"><span data-stu-id="12f2d-158">The <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> method is used to ensure that the behavior can be applied to the service.</span></span> <span data-ttu-id="12f2d-159">V této ukázce implementace zajišťuje, že <xref:System.ServiceModel.InstanceContextMode.Single>služba není nakonfigurována s .</span><span class="sxs-lookup"><span data-stu-id="12f2d-159">In this sample, the implementation ensures that the service is not configured with <xref:System.ServiceModel.InstanceContextMode.Single>.</span></span> <span data-ttu-id="12f2d-160">Metoda <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> se používá ke konfiguraci vazby služby.</span><span class="sxs-lookup"><span data-stu-id="12f2d-160">The <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> method is used to configure the service's bindings.</span></span> <span data-ttu-id="12f2d-161">Není vyžadováno v tomto scénáři.</span><span class="sxs-lookup"><span data-stu-id="12f2d-161">It is not required in this scenario.</span></span> <span data-ttu-id="12f2d-162">Slouží <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> ke konfiguraci dispečerů služby.</span><span class="sxs-lookup"><span data-stu-id="12f2d-162">The <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> is used to configure the service's dispatchers.</span></span> <span data-ttu-id="12f2d-163">Tato metoda je volána <xref:System.ServiceModel.ServiceHost> WCF při inicializování.</span><span class="sxs-lookup"><span data-stu-id="12f2d-163">This method is called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="12f2d-164">Do této metody jsou předány následující parametry:</span><span class="sxs-lookup"><span data-stu-id="12f2d-164">The following parameters are passed into this method:</span></span>  
  
- <span data-ttu-id="12f2d-165">`Description`: Tento argument poskytuje popis služby pro celou službu.</span><span class="sxs-lookup"><span data-stu-id="12f2d-165">`Description`: This argument provides the service description for the entire service.</span></span> <span data-ttu-id="12f2d-166">To lze použít ke kontrole popisdat o koncových bodech služby, smlouvy, vazby a další data.</span><span class="sxs-lookup"><span data-stu-id="12f2d-166">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data.</span></span>  
  
- <span data-ttu-id="12f2d-167">`ServiceHostBase`: Tento argument <xref:System.ServiceModel.ServiceHostBase> poskytuje, který je právě inicializován.</span><span class="sxs-lookup"><span data-stu-id="12f2d-167">`ServiceHostBase`: This argument provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="12f2d-168">Ve vlastní <xref:System.ServiceModel.Description.IServiceBehavior> implementaci `ObjectPoolingInstanceProvider` je vytvořena instance a přiřazena <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> k vlastnosti v každé <xref:System.ServiceModel.Dispatcher.DispatchRuntime> v ServiceHostBase.</span><span class="sxs-lookup"><span data-stu-id="12f2d-168">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation a new instance of `ObjectPoolingInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.DispatchRuntime> in the ServiceHostBase.</span></span>  
  
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
  
 <span data-ttu-id="12f2d-169">Kromě <xref:System.ServiceModel.Description.IServiceBehavior> implementace má <xref:System.EnterpriseServices.ObjectPoolingAttribute> třída několik členů pro přizpůsobení fondu objektů pomocí argumentů atributu.</span><span class="sxs-lookup"><span data-stu-id="12f2d-169">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the <xref:System.EnterpriseServices.ObjectPoolingAttribute> class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="12f2d-170">Mezi tyto <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A> <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>členy <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>patří , , a , aby odpovídaly sadě funkcí sdružování objektů poskytované službou .NET Enterprise Services.</span><span class="sxs-lookup"><span data-stu-id="12f2d-170">These members include <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, and <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="12f2d-171">Chování sdružování objektů lze nyní přidat do služby WCF anotací `ObjectPooling` implementace služby s nově vytvořeným vlastním atributem.</span><span class="sxs-lookup"><span data-stu-id="12f2d-171">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```csharp  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="12f2d-172">Spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="12f2d-172">Running the Sample</span></span>  
 <span data-ttu-id="12f2d-173">Ukázka ukazuje výhody výkonu, které lze získat pomocí sdružování objektů v určitých scénářích.</span><span class="sxs-lookup"><span data-stu-id="12f2d-173">The sample demonstrates the performance benefits that can be gained by using object pooling in certain scenarios.</span></span>  
  
 <span data-ttu-id="12f2d-174">Aplikace služby implementuje `WorkService` `ObjectPooledWorkService`dvě služby – a .</span><span class="sxs-lookup"><span data-stu-id="12f2d-174">The service application implements two services -- `WorkService` and `ObjectPooledWorkService`.</span></span> <span data-ttu-id="12f2d-175">Obě služby sdílejí stejnou implementaci – obě vyžadují `DoWork()` nákladnou inicializaci a pak zveřejňují metodu, která je relativně levná.</span><span class="sxs-lookup"><span data-stu-id="12f2d-175">Both services share the same implementation -- they both require expensive initialization and then expose a `DoWork()` method that is relatively cheap.</span></span> <span data-ttu-id="12f2d-176">Jediným rozdílem `ObjectPooledWorkService` je, že má sdružování objektů nakonfigurováno:</span><span class="sxs-lookup"><span data-stu-id="12f2d-176">The only difference is that the `ObjectPooledWorkService` has object pooling configured:</span></span>  
  
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
  
 <span data-ttu-id="12f2d-177">Při spuštění klienta, to `WorkService` krát volání 5 krát.</span><span class="sxs-lookup"><span data-stu-id="12f2d-177">When you run the client, it times calling the `WorkService` 5 times.</span></span> <span data-ttu-id="12f2d-178">To pak krát `ObjectPooledWorkService` volání 5 krát.</span><span class="sxs-lookup"><span data-stu-id="12f2d-178">It then times calling the `ObjectPooledWorkService` 5 times.</span></span> <span data-ttu-id="12f2d-179">Poté se zobrazí časový rozdíl:</span><span class="sxs-lookup"><span data-stu-id="12f2d-179">The difference in time is then displayed:</span></span>  
  
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
> <span data-ttu-id="12f2d-180">Při prvním spuštění klienta se zdá, že obě služby mají přibližně stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="12f2d-180">The first time the client is run both services appear to take about the same amount of time.</span></span> <span data-ttu-id="12f2d-181">Pokud znovu spustíte ukázku, uvidíte, že `ObjectPooledWorkService` vrátí mnohem rychleji, protože instance tohoto objektu již existuje ve fondu.</span><span class="sxs-lookup"><span data-stu-id="12f2d-181">If you re-run the sample, you can see that the `ObjectPooledWorkService` returns much quicker because an instance of that object already exists in the pool.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="12f2d-182">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="12f2d-182">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="12f2d-183">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="12f2d-183">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="12f2d-184">Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="12f2d-184">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="12f2d-185">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="12f2d-185">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="12f2d-186">Pokud používáte Svcutil.exe k obnovení konfigurace pro tuto ukázku, nezapomeňte upravit název koncového bodu v konfiguraci klienta tak, aby odpovídalkódu klienta.</span><span class="sxs-lookup"><span data-stu-id="12f2d-186">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="12f2d-187">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="12f2d-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="12f2d-188">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="12f2d-188">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="12f2d-189">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="12f2d-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="12f2d-190">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="12f2d-190">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
