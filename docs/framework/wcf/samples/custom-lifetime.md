---
title: Vlastní doba života
ms.date: 08/20/2018
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
ms.openlocfilehash: 1946608c69401fb08f6eb458a8adabea24563963
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467743"
---
# <a name="custom-lifetime"></a><span data-ttu-id="40108-102">Vlastní doba života</span><span class="sxs-lookup"><span data-stu-id="40108-102">Custom lifetime</span></span>

<span data-ttu-id="40108-103">Tato ukázka předvádí, jak psát rozšíření Windows Communication Foundation (WCF) k poskytování služeb vlastní doba života pro sdílené instance služby WCF.</span><span class="sxs-lookup"><span data-stu-id="40108-103">This sample demonstrates how to write a Windows Communication Foundation (WCF) extension to provide custom lifetime services for shared WCF service instances.</span></span>

> [!NOTE]
> <span data-ttu-id="40108-104">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto článku.</span><span class="sxs-lookup"><span data-stu-id="40108-104">The setup procedure and build instructions for this sample are located at the end of this article.</span></span>

## <a name="shared-instancing"></a><span data-ttu-id="40108-105">Sdílené vytváření instancí</span><span class="sxs-lookup"><span data-stu-id="40108-105">Shared instancing</span></span>

<span data-ttu-id="40108-106">WCF nabízí několik vytvoření instance režimů pro vaše instance služby.</span><span class="sxs-lookup"><span data-stu-id="40108-106">WCF offers several instancing modes for your service instances.</span></span> <span data-ttu-id="40108-107">Sdílené vytvoření instance režimu popsaná v tomto článku poskytuje způsob, jak sdílet instanci služby mezi několika kanály.</span><span class="sxs-lookup"><span data-stu-id="40108-107">The shared instancing mode covered in this article provides a way to share a service instance between multiple channels.</span></span> <span data-ttu-id="40108-108">Klienti mohou kontaktovat metoda factory ve službě a vytvořit nový kanál komunikaci.</span><span class="sxs-lookup"><span data-stu-id="40108-108">Clients can contact a factory method in the service and create a new channel to start communication.</span></span> <span data-ttu-id="40108-109">Následující fragment kódu ukazuje, jak klientská aplikace vytvoří nový kanál do existující instance služby:</span><span class="sxs-lookup"><span data-stu-id="40108-109">The following code snippet shows how a client application creates a new channel to an existing service instance:</span></span>

```csharp
// Create a header for the shared instance id
MessageHeader shareableInstanceContextHeader = MessageHeader.CreateHeader(
        CustomHeader.HeaderName,
        CustomHeader.HeaderNamespace,
        Guid.NewGuid().ToString());

// Create the channel factory
ChannelFactory<IEchoService> channelFactory =
    new ChannelFactory<IEchoService>("echoservice");

// Create the first channel
IEchoService proxy = channelFactory.CreateChannel();

// Call an operation to create shared service instance
using (new OperationContextScope((IClientChannel)proxy))
{
    OperationContext.Current.OutgoingMessageHeaders.Add(shareableInstanceContextHeader);
    Console.WriteLine("Service returned: " + proxy.Echo("Apple"));
}

((IChannel)proxy).Close();

// Create the second channel
IEchoService proxy2 = channelFactory.CreateChannel();

// Call an operation using the same header that will reuse the shared service instance
using (new OperationContextScope((IClientChannel)proxy2))
{
    OperationContext.Current.OutgoingMessageHeaders.Add(shareableInstanceContextHeader);
    Console.WriteLine("Service returned: " + proxy2.Echo("Apple"));
}
```

<span data-ttu-id="40108-110">Na rozdíl od ostatních vytvoření instance režimech sdílené vytvoření instance režimu má jedinečný způsob, jak uvolnění instancí služby.</span><span class="sxs-lookup"><span data-stu-id="40108-110">Unlike other instancing modes, the shared instancing mode has a unique way of releasing the service instances.</span></span> <span data-ttu-id="40108-111">Ve výchozím nastavení, když jsou uzavřeny všechny kanály pro <xref:System.ServiceModel.InstanceContext>, modul runtime služby WCF zkontroluje, zda služba <xref:System.ServiceModel.InstanceContextMode> nastaven na <xref:System.ServiceModel.InstanceContextMode.PerCall> nebo <xref:System.ServiceModel.InstanceContextMode.PerSession>a pokud to uvolní instanci a nároky prostředky.</span><span class="sxs-lookup"><span data-stu-id="40108-111">By default, when all the channels are closed for an <xref:System.ServiceModel.InstanceContext>, the WCF service runtime checks to see if the service <xref:System.ServiceModel.InstanceContextMode> is configured to <xref:System.ServiceModel.InstanceContextMode.PerCall> or <xref:System.ServiceModel.InstanceContextMode.PerSession>, and if so releases the instance and claims the resources.</span></span> <span data-ttu-id="40108-112">Pokud vlastní <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> je používán, vyvolá WCF <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metoda implementace poskytovatele před uvolněním instance.</span><span class="sxs-lookup"><span data-stu-id="40108-112">If a custom <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> is being used, WCF invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of the provider implementation before releasing the instance.</span></span> <span data-ttu-id="40108-113">Pokud <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> vrátí `true` se uvolní instanci, jinak <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementace je zodpovědný za upozornění `Dispatcher` ze stavu nečinnosti pomocí metody zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="40108-113">If <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> returns `true` the instance is released, otherwise the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is responsible for notifying the `Dispatcher` of the idle state by using a callback method.</span></span> <span data-ttu-id="40108-114">To se provádí pomocí volání <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> metoda zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="40108-114">This is done by calling the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method of the provider.</span></span>

<span data-ttu-id="40108-115">Tato ukázka předvádí, jak můžete zpoždění uvolnění <xref:System.ServiceModel.InstanceContext> s časový limit nečinnosti 20 sekund.</span><span class="sxs-lookup"><span data-stu-id="40108-115">This sample demonstrates how you can delay releasing the <xref:System.ServiceModel.InstanceContext> with an idle timeout of 20 seconds.</span></span>

## <a name="extending-the-instancecontext"></a><span data-ttu-id="40108-116">Rozšíření kontextu InstanceContext</span><span class="sxs-lookup"><span data-stu-id="40108-116">Extending the InstanceContext</span></span>

<span data-ttu-id="40108-117">Ve službě WCF <xref:System.ServiceModel.InstanceContext> je propojení mezi instance služby a `Dispatcher`.</span><span class="sxs-lookup"><span data-stu-id="40108-117">In WCF, <xref:System.ServiceModel.InstanceContext> is the link between the service instance and the `Dispatcher`.</span></span> <span data-ttu-id="40108-118">WCF umožňuje rozšířit tak, že přidáte nový stav a chování pomocí způsobu rozšiřitelném objektu této součásti modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="40108-118">WCF allows you to extend this runtime component by adding new state or behavior by using its extensible object pattern.</span></span> <span data-ttu-id="40108-119">Vzor rozšiřitelném objektu se používá ve službě WCF buď rozšířit existující třídy modulu runtime s novými funkcemi nebo přidávání nových funkcí stavu k objektu.</span><span class="sxs-lookup"><span data-stu-id="40108-119">The extensible object pattern is used in WCF to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="40108-120">Existují tři rozhraní ve vzoru rozšiřitelném objektu: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>, a <xref:System.ServiceModel.IExtensionCollection%601>.</span><span class="sxs-lookup"><span data-stu-id="40108-120">There are three interfaces in the extensible object pattern: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>, and <xref:System.ServiceModel.IExtensionCollection%601>.</span></span>

<span data-ttu-id="40108-121"><xref:System.ServiceModel.IExtensibleObject%601> Rozhraní implementují objekty umožňující rozšíření, která přizpůsobit jejich funkce.</span><span class="sxs-lookup"><span data-stu-id="40108-121">The <xref:System.ServiceModel.IExtensibleObject%601> interface is implemented by objects to allow extensions that customize their functionality.</span></span>

<span data-ttu-id="40108-122"><xref:System.ServiceModel.IExtension%601> Rozhraní implementují objekty, které může být rozšíření třídy typu `T`.</span><span class="sxs-lookup"><span data-stu-id="40108-122">The <xref:System.ServiceModel.IExtension%601> interface is implemented by objects that can be extensions of classes of type `T`.</span></span>

<span data-ttu-id="40108-123">A nakonec <xref:System.ServiceModel.IExtensionCollection%601> rozhraní je kolekce <xref:System.ServiceModel.IExtension%601> implementace, které umožňuje načítání implementace <xref:System.ServiceModel.IExtension%601> podle jejich typu.</span><span class="sxs-lookup"><span data-stu-id="40108-123">And finally, the <xref:System.ServiceModel.IExtensionCollection%601> interface is a collection of <xref:System.ServiceModel.IExtension%601> implementations that allows for retrieving an implementation of <xref:System.ServiceModel.IExtension%601> by their type.</span></span>

<span data-ttu-id="40108-124">Proto aby bylo možné rozšířit <xref:System.ServiceModel.InstanceContext>, musí implementovat <xref:System.ServiceModel.IExtension%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="40108-124">Therefore, in order to extend the <xref:System.ServiceModel.InstanceContext>, you must implement the <xref:System.ServiceModel.IExtension%601> interface.</span></span> <span data-ttu-id="40108-125">V tento ukázkový projekt `CustomLeaseExtension` třída obsahuje tuto implementaci.</span><span class="sxs-lookup"><span data-stu-id="40108-125">In this sample project, the `CustomLeaseExtension` class contains this implementation.</span></span>

```csharp
class CustomLeaseExtension : IExtension<InstanceContext>
{
}
```

<span data-ttu-id="40108-126"><xref:System.ServiceModel.IExtension%601> Rozhraní poskytuje dva způsoby <xref:System.ServiceModel.IExtension%601.Attach%2A> a <xref:System.ServiceModel.IExtension%601.Detach%2A>.</span><span class="sxs-lookup"><span data-stu-id="40108-126">The <xref:System.ServiceModel.IExtension%601> interface has two methods <xref:System.ServiceModel.IExtension%601.Attach%2A> and <xref:System.ServiceModel.IExtension%601.Detach%2A>.</span></span> <span data-ttu-id="40108-127">Jak naznačují jejich názvy, jsou tyto dvě metody volá, když modul runtime připojí a odpojí rozšíření do instance <xref:System.ServiceModel.InstanceContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="40108-127">As their names imply, these two methods are called when the runtime attaches and detaches the extension to an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="40108-128">V této ukázce `Attach` metoda se používá ke sledování <xref:System.ServiceModel.InstanceContext> objekt, který patří k aktuální instanci rozšíření.</span><span class="sxs-lookup"><span data-stu-id="40108-128">In this sample, the `Attach` method is used to keep track of the <xref:System.ServiceModel.InstanceContext> object that belongs to the current instance of the extension.</span></span>

```csharp
InstanceContext owner;

public void Attach(InstanceContext owner)
{
    this.owner = owner;
}
```

<span data-ttu-id="40108-129">Kromě toho musíte přidat nezbytné provádění na rozšíření pro zajištění podpory delší životnost.</span><span class="sxs-lookup"><span data-stu-id="40108-129">In addition, you must add the necessary implementation to the extension to provide the extended lifetime support.</span></span> <span data-ttu-id="40108-130">Proto `ICustomLease` rozhraní je deklarována s požadovanou metody a je implementována v `CustomLeaseExtension` třídy.</span><span class="sxs-lookup"><span data-stu-id="40108-130">Therefore, the `ICustomLease` interface is declared with the desired methods and is implemented in the `CustomLeaseExtension` class.</span></span>

```csharp
interface ICustomLease
{
    bool IsIdle { get; }
    InstanceContextIdleCallback Callback { get; set; }
}

class CustomLeaseExtension : IExtension<InstanceContext>, ICustomLease
{
}
```

<span data-ttu-id="40108-131">Když WCF vyvolá <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metoda ve <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementace, toto volání se směruje na <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metodu `CustomLeaseExtension`.</span><span class="sxs-lookup"><span data-stu-id="40108-131">When WCF invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method in the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation, this call is routed to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of the `CustomLeaseExtension`.</span></span> <span data-ttu-id="40108-132">Pak, bude `CustomLeaseExtension` zkontroluje jeho privátní stav chcete zobrazit, zda <xref:System.ServiceModel.InstanceContext> nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="40108-132">Then, the `CustomLeaseExtension` checks its private state to see whether the <xref:System.ServiceModel.InstanceContext> is idle.</span></span> <span data-ttu-id="40108-133">Pokud je nečinné, vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="40108-133">If it is idle, it returns `true`.</span></span> <span data-ttu-id="40108-134">V opačném případě spustí časovač po zadanou dobu životnosti rozšířené.</span><span class="sxs-lookup"><span data-stu-id="40108-134">Otherwise, it starts a timer for a specified amount of extended lifetime.</span></span>

```csharp
public bool IsIdle
{
  get
  {
    lock (thisLock)
    {
      if (isIdle)
      {
        return true;
      }
      else
      {
        StartTimer();
        return false;
      }
    }
  }
}
```

<span data-ttu-id="40108-135">V časovače `Elapsed` událostí, aby bylo možné spustit další cyklus vyčištění je volána funkce zpětného volání dispečerem.</span><span class="sxs-lookup"><span data-stu-id="40108-135">In the timer’s `Elapsed` event, the callback function in the Dispatcher is called in order to start another clean-up cycle.</span></span>

```csharp
void idleTimer_Elapsed(object sender, ElapsedEventArgs args)
{
    lock (thisLock)
    {
        StopTimer();
        isIdle = true;
        Utility.WriteMessageToConsole(
            ResourceHelper.GetString("MsgLeaseExpired"));
        callback(owner);
    }
}
```

<span data-ttu-id="40108-136">Neexistuje žádný způsob, jak obnovit spuštěné časovač při přijme novou zprávu pro instanci, který se přesouvá do nečinného stavu.</span><span class="sxs-lookup"><span data-stu-id="40108-136">There's no way to renew the running timer when a new message arrives for the instance being moved to the idle state.</span></span>

<span data-ttu-id="40108-137">Implementuje vzorek <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> zachycení volání <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metoda a tras do `CustomLeaseExtension`.</span><span class="sxs-lookup"><span data-stu-id="40108-137">The sample implements <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> to intercept the calls to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method and route them to the `CustomLeaseExtension`.</span></span> <span data-ttu-id="40108-138"><xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> Je součástí implementace `CustomLifetimeLease` třídy.</span><span class="sxs-lookup"><span data-stu-id="40108-138">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is contained in `CustomLifetimeLease` class.</span></span> <span data-ttu-id="40108-139"><xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> Je vyvolána metoda WCF se uvolnit instance služby.</span><span class="sxs-lookup"><span data-stu-id="40108-139">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method is invoked when WCF is about to release the service instance.</span></span> <span data-ttu-id="40108-140">Existuje však pouze jedna instance konkrétní třídy `ISharedSessionInstance` implementace ServiceBehavior <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> kolekce.</span><span class="sxs-lookup"><span data-stu-id="40108-140">However, there is only one instance of a particular `ISharedSessionInstance` implementation in the ServiceBehavior’s <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> collection.</span></span> <span data-ttu-id="40108-141">To znamená, že neexistuje žádný způsob, že pokud <xref:System.ServiceModel.InstanceContext> je uzavřený v době kontroly WCF <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="40108-141">This means there's no way of knowing if the <xref:System.ServiceModel.InstanceContext> is closed at the time WCF checks the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span> <span data-ttu-id="40108-142">Proto tato ukázka používá vlákno uzamčení k serializaci požadavků <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="40108-142">Therefore, this sample uses thread locking to serialize requests to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="40108-143">Použití uzamčení podprocesu není doporučený postup vzhledem k tomu, že serializace může mít vážný vliv výkon vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="40108-143">Using thread locking is not a recommended approach because serialization can severely affect the performance of your application.</span></span>

<span data-ttu-id="40108-144">Soukromý člen pole se používá v `CustomLifetimeLease` třídy ke sledování stavu nečinnosti a vrátí <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="40108-144">A private member field is used in the `CustomLifetimeLease` class to track the idle state and is returned by the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span> <span data-ttu-id="40108-145">Pokaždé, když <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metoda je volána, `isIdle` pole je vrácena a obnovit `false`.</span><span class="sxs-lookup"><span data-stu-id="40108-145">Each time the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method is called, the `isIdle` field is returned and reset to `false`.</span></span>  <span data-ttu-id="40108-146">To je velmi důležité, nastavte hodnotu `false` Pokud chcete mít jistotu dispečer volání <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="40108-146">It is essential to set this value to `false` in order to make sure the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method.</span></span>

```csharp
public bool IsIdle(InstanceContext instanceContext)
{
    get
    {
        lock (thisLock)
        {
            //...
            bool idleCopy = isIdle;
            isIdle = false;
            return idleCopy;
        }
    }
}
```

<span data-ttu-id="40108-147">Pokud <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> vrátí metoda `false`, dispečer zaregistruje funkci zpětného volání pomocí <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="40108-147">If the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> method returns `false`, the Dispatcher registers a callback function by using the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method.</span></span> <span data-ttu-id="40108-148">Tato metoda přijímá odkaz na <xref:System.ServiceModel.InstanceContext> se vydávají.</span><span class="sxs-lookup"><span data-stu-id="40108-148">This method receives a reference to the <xref:System.ServiceModel.InstanceContext> being released.</span></span> <span data-ttu-id="40108-149">Proto se můžete dotazovat vzorový kód `ICustomLease` zadejte příponu a zkontrolujte `ICustomLease.IsIdle` v rozšířené stavové vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="40108-149">Therefore, the sample code can query the `ICustomLease` type extension and check the `ICustomLease.IsIdle` property in the extended state.</span></span>

```csharp
public void NotifyIdle(InstanceContextIdleCallback callback,
            InstanceContext instanceContext)
{
    lock (thisLock)
    {
       ICustomLease customLease =
           instanceContext.Extensions.Find<ICustomLease>();
       customLease.Callback = callback;
       isIdle = customLease.IsIdle;
       if (isIdle)
       {
             callback(instanceContext);
       }
    }
}
```

<span data-ttu-id="40108-150">Před `ICustomLease.IsIdle` zaškrtnuté vlastnosti, vlastnost zpětného volání je potřeba nastavit, protože to je nezbytné pro `CustomLeaseExtension` dispečer upozornit, když se změní na nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="40108-150">Before the `ICustomLease.IsIdle` property is checked, the Callback property needs to be set as this is essential for `CustomLeaseExtension` to notify the Dispatcher when it becomes idle.</span></span> <span data-ttu-id="40108-151">Pokud `ICustomLease.IsIdle` vrátí `true`, `isIdle` soukromý člen jednoduše nastavený `CustomLifetimeLease` k `true` a volá metodu zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="40108-151">If `ICustomLease.IsIdle` returns `true`, the `isIdle` private member is simply set in `CustomLifetimeLease` to `true` and calls the callback method.</span></span> <span data-ttu-id="40108-152">Protože kód drží zámek, ostatní vlákna nelze změnit hodnotu tento privátní člen.</span><span class="sxs-lookup"><span data-stu-id="40108-152">Because the code holds a lock, other threads can't change the value of this private member.</span></span> <span data-ttu-id="40108-153">A při příštím volání dispečer <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>, vrátí `true` a umožňuje uvolnění instance dispečeru.</span><span class="sxs-lookup"><span data-stu-id="40108-153">And the next time Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>, it returns `true` and lets Dispatcher release the instance.</span></span>

<span data-ttu-id="40108-154">Teď, když se dokončí připravovat základy pro vlastní rozšíření, musí být připojili k modelu služby.</span><span class="sxs-lookup"><span data-stu-id="40108-154">Now that the groundwork for the custom extension is completed, it has to be hooked up to the service model.</span></span> <span data-ttu-id="40108-155">K připojení `CustomLeaseExtension` implementaci <xref:System.ServiceModel.InstanceContext>, poskytuje WCF <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> rozhraní k provedení spuštění z <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="40108-155">To hook up the `CustomLeaseExtension` implementation to the <xref:System.ServiceModel.InstanceContext>, WCF provides the <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> interface to perform the bootstrapping of <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="40108-156">V ukázce `CustomLeaseInitializer` třída implementuje toto rozhraní a přidá instanci `CustomLeaseExtension` k <xref:System.ServiceModel.InstanceContext.Extensions%2A> kolekce z jedinou metodou inicializace.</span><span class="sxs-lookup"><span data-stu-id="40108-156">In the sample, the `CustomLeaseInitializer` class implements this interface and adds an instance of `CustomLeaseExtension` to the <xref:System.ServiceModel.InstanceContext.Extensions%2A> collection from the only method initialization.</span></span> <span data-ttu-id="40108-157">Tato metoda je volána metodou dispečera při inicializaci <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="40108-157">This method is called by Dispatcher while initializing the <xref:System.ServiceModel.InstanceContext>.</span></span>

```csharp
public void InitializeInstanceContext(InstanceContext instanceContext,
    System.ServiceModel.Channels.Message message, IContextChannel channel)

    //...

    IExtension<InstanceContext> customLeaseExtension =
        new CustomLeaseExtension(timeout, headerId);
    instanceContext.Extensions.Add(customLeaseExtension);
}
```

 <span data-ttu-id="40108-158">Nakonec <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementace je připojili k modelu služby s použitím <xref:System.ServiceModel.Description.IServiceBehavior> implementace.</span><span class="sxs-lookup"><span data-stu-id="40108-158">Finally the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is hooked up to the service model by using the <xref:System.ServiceModel.Description.IServiceBehavior> implementation.</span></span> <span data-ttu-id="40108-159">Tato implementace se umístí do `CustomLeaseTimeAttribute` třídy a také se odvozuje od `Attribute` základní třída vystavit toto chování jako atribut.</span><span class="sxs-lookup"><span data-stu-id="40108-159">This implementation is placed in the `CustomLeaseTimeAttribute` class and it also derives from the `Attribute` base class to expose this behavior as an attribute.</span></span>

```csharp
public void ApplyDispatchBehavior(ServiceDescription description,
           ServiceHostBase serviceHostBase)
{
    CustomLifetimeLease customLease = new CustomLifetimeLease(timeout);

    foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)
    {
        ChannelDispatcher cd = cdb as ChannelDispatcher;

        if (cd != null)
        {
            foreach (EndpointDispatcher ed in cd.Endpoints)
            {
                ed.DispatchRuntime.InstanceContextProvider = customLease;
            }
        }
    }
}
```

<span data-ttu-id="40108-160">Toto chování lze přidat do třídy Ukázka služby s anotací `CustomLeaseTime` atribut.</span><span class="sxs-lookup"><span data-stu-id="40108-160">This behavior can be added to a sample service class by annotating it with the `CustomLeaseTime` attribute.</span></span>

```csharp
[CustomLeaseTime(Timeout = 20000)]
public class EchoService : IEchoService
{
  //…
}
```

<span data-ttu-id="40108-161">Při spuštění ukázky operace žádosti a odpovědi se zobrazují v oknech konzoly služby a klienta.</span><span class="sxs-lookup"><span data-stu-id="40108-161">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="40108-162">Stisknutím klávesy ENTER v každé okno konzoly pro vypnutí klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="40108-162">Press ENTER in each console window to shut down the service and client.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="40108-163">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="40108-163">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="40108-164">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="40108-164">Ensure that you've performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="40108-165">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="40108-165">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="40108-166">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="40108-166">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="40108-167">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="40108-167">The samples may already be installed on your machine.</span></span> <span data-ttu-id="40108-168">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="40108-168">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="40108-169">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="40108-169">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="40108-170">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="40108-170">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`
