---
title: Vlastní doba života
ms.date: 08/20/2018
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
ms.openlocfilehash: 8625877d9b4d05d5cf06af2c9f8ef10f701e98db
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715469"
---
# <a name="custom-lifetime"></a><span data-ttu-id="ef9bf-102">Vlastní doba života</span><span class="sxs-lookup"><span data-stu-id="ef9bf-102">Custom lifetime</span></span>

<span data-ttu-id="ef9bf-103">Tato ukázka předvádí, jak napsat rozšíření Windows Communication Foundation (WCF), které poskytuje vlastní služby životnosti pro sdílené instance služby WCF.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-103">This sample demonstrates how to write a Windows Communication Foundation (WCF) extension to provide custom lifetime services for shared WCF service instances.</span></span>

> [!NOTE]
> <span data-ttu-id="ef9bf-104">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto článku.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-104">The setup procedure and build instructions for this sample are located at the end of this article.</span></span>

## <a name="shared-instancing"></a><span data-ttu-id="ef9bf-105">Sdílené vytváření instancí</span><span class="sxs-lookup"><span data-stu-id="ef9bf-105">Shared instancing</span></span>

<span data-ttu-id="ef9bf-106">WCF nabízí několik režimů vytváření instancí pro vaše instance služby.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-106">WCF offers several instancing modes for your service instances.</span></span> <span data-ttu-id="ef9bf-107">Režim sdíleného vytváření instancí, který je popsaný v tomto článku, poskytuje způsob, jak sdílet instanci služby mezi několika kanály.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-107">The shared instancing mode covered in this article provides a way to share a service instance between multiple channels.</span></span> <span data-ttu-id="ef9bf-108">Klienti můžou ve službě kontaktovat výrobní metodu a vytvořit nový kanál pro zahájení komunikace.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-108">Clients can contact a factory method in the service and create a new channel to start communication.</span></span> <span data-ttu-id="ef9bf-109">Následující fragment kódu ukazuje, jak klientská aplikace vytvoří nový kanál do existující instance služby:</span><span class="sxs-lookup"><span data-stu-id="ef9bf-109">The following code snippet shows how a client application creates a new channel to an existing service instance:</span></span>

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

<span data-ttu-id="ef9bf-110">Na rozdíl od jiných režimů vytváření instancí má režim sdíleného vytváření instancí jedinečný způsob, jak tyto instance služby uvolnit.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-110">Unlike other instancing modes, the shared instancing mode has a unique way of releasing the service instances.</span></span> <span data-ttu-id="ef9bf-111">Když se ve výchozím nastavení pro <xref:System.ServiceModel.InstanceContext>zavřou všechny kanály, modul runtime služby WCF zkontroluje, jestli je <xref:System.ServiceModel.InstanceContextMode> služby nakonfigurované na <xref:System.ServiceModel.InstanceContextMode.PerCall> nebo <xref:System.ServiceModel.InstanceContextMode.PerSession>, a pokud tak uvolní instanci a vyžádá prostředky.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-111">By default, when all the channels are closed for an <xref:System.ServiceModel.InstanceContext>, the WCF service runtime checks to see if the service <xref:System.ServiceModel.InstanceContextMode> is configured to <xref:System.ServiceModel.InstanceContextMode.PerCall> or <xref:System.ServiceModel.InstanceContextMode.PerSession>, and if so releases the instance and claims the resources.</span></span> <span data-ttu-id="ef9bf-112">Pokud se používá vlastní <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>, WCF vyvolá metodu <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> implementace zprostředkovatele před uvolněním instance.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-112">If a custom <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> is being used, WCF invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of the provider implementation before releasing the instance.</span></span> <span data-ttu-id="ef9bf-113">Pokud <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> vrátí `true` instance, v opačném případě <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementace je zodpovědná za oznamování `Dispatcher` stavu nečinnosti pomocí metody zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-113">If <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> returns `true` the instance is released, otherwise the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is responsible for notifying the `Dispatcher` of the idle state by using a callback method.</span></span> <span data-ttu-id="ef9bf-114">To se provádí voláním metody <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-114">This is done by calling the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method of the provider.</span></span>

<span data-ttu-id="ef9bf-115">Tato ukázka předvádí, jak můžete zpozdit uvolnění <xref:System.ServiceModel.InstanceContext> s časovým limitem nečinnosti 20 sekund.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-115">This sample demonstrates how you can delay releasing the <xref:System.ServiceModel.InstanceContext> with an idle timeout of 20 seconds.</span></span>

## <a name="extending-the-instancecontext"></a><span data-ttu-id="ef9bf-116">Rozšíření InstanceContext</span><span class="sxs-lookup"><span data-stu-id="ef9bf-116">Extending the InstanceContext</span></span>

<span data-ttu-id="ef9bf-117">V rámci WCF je <xref:System.ServiceModel.InstanceContext> propojení mezi instancí služby a `Dispatcher`.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-117">In WCF, <xref:System.ServiceModel.InstanceContext> is the link between the service instance and the `Dispatcher`.</span></span> <span data-ttu-id="ef9bf-118">Služba WCF umožňuje rozšířit tuto komponentu modulu runtime přidáním nového stavu nebo chování pomocí jeho modelu rozšiřitelného objektu.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-118">WCF allows you to extend this runtime component by adding new state or behavior by using its extensible object pattern.</span></span> <span data-ttu-id="ef9bf-119">Model rozšiřitelného objektu se používá ve službě WCF pro rozšiřující existující běhové třídy s novými funkcemi nebo pro přidání nových funkcí stavu do objektu.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-119">The extensible object pattern is used in WCF to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="ef9bf-120">Existují tři rozhraní ve vzoru rozšiřitelného objektu: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>a <xref:System.ServiceModel.IExtensionCollection%601>.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-120">There are three interfaces in the extensible object pattern: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>, and <xref:System.ServiceModel.IExtensionCollection%601>.</span></span>

<span data-ttu-id="ef9bf-121">Rozhraní <xref:System.ServiceModel.IExtensibleObject%601> je implementováno pomocí objektů a umožňuje rozšíření, která přizpůsobují jejich funkce.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-121">The <xref:System.ServiceModel.IExtensibleObject%601> interface is implemented by objects to allow extensions that customize their functionality.</span></span>

<span data-ttu-id="ef9bf-122">Rozhraní <xref:System.ServiceModel.IExtension%601> je implementováno objekty, které mohou být rozšíření třídy typu `T`.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-122">The <xref:System.ServiceModel.IExtension%601> interface is implemented by objects that can be extensions of classes of type `T`.</span></span>

<span data-ttu-id="ef9bf-123">A nakonec <xref:System.ServiceModel.IExtensionCollection%601> rozhraní je kolekce <xref:System.ServiceModel.IExtension%601> implementace, které umožňují načíst implementaci <xref:System.ServiceModel.IExtension%601> podle jejich typu.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-123">And finally, the <xref:System.ServiceModel.IExtensionCollection%601> interface is a collection of <xref:System.ServiceModel.IExtension%601> implementations that allows for retrieving an implementation of <xref:System.ServiceModel.IExtension%601> by their type.</span></span>

<span data-ttu-id="ef9bf-124">Proto pro účely rozšiřování <xref:System.ServiceModel.InstanceContext>musíte implementovat rozhraní <xref:System.ServiceModel.IExtension%601>.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-124">Therefore, in order to extend the <xref:System.ServiceModel.InstanceContext>, you must implement the <xref:System.ServiceModel.IExtension%601> interface.</span></span> <span data-ttu-id="ef9bf-125">V tomto ukázkovém projektu třída `CustomLeaseExtension` obsahuje tuto implementaci.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-125">In this sample project, the `CustomLeaseExtension` class contains this implementation.</span></span>

```csharp
class CustomLeaseExtension : IExtension<InstanceContext>
{
}
```

<span data-ttu-id="ef9bf-126">Rozhraní <xref:System.ServiceModel.IExtension%601> má dvě metody <xref:System.ServiceModel.IExtension%601.Attach%2A> a <xref:System.ServiceModel.IExtension%601.Detach%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-126">The <xref:System.ServiceModel.IExtension%601> interface has two methods <xref:System.ServiceModel.IExtension%601.Attach%2A> and <xref:System.ServiceModel.IExtension%601.Detach%2A>.</span></span> <span data-ttu-id="ef9bf-127">Protože jejich názvy implikují, tyto dvě metody jsou volány, když modul runtime připojí a odpojí rozšíření s instancí třídy <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-127">As their names imply, these two methods are called when the runtime attaches and detaches the extension to an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="ef9bf-128">V této ukázce je `Attach` metoda použita k udržení přehledu o <xref:System.ServiceModel.InstanceContext> objektu, který patří do aktuální instance rozšíření.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-128">In this sample, the `Attach` method is used to keep track of the <xref:System.ServiceModel.InstanceContext> object that belongs to the current instance of the extension.</span></span>

```csharp
InstanceContext owner;

public void Attach(InstanceContext owner)
{
    this.owner = owner;
}
```

<span data-ttu-id="ef9bf-129">Kromě toho musíte do rozšíření přidat nezbytnou implementaci, která poskytuje rozšířenou podporu životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-129">In addition, you must add the necessary implementation to the extension to provide the extended lifetime support.</span></span> <span data-ttu-id="ef9bf-130">Proto rozhraní `ICustomLease` je deklarováno s požadovanými metodami a je implementováno ve třídě `CustomLeaseExtension`.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-130">Therefore, the `ICustomLease` interface is declared with the desired methods and is implemented in the `CustomLeaseExtension` class.</span></span>

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

<span data-ttu-id="ef9bf-131">Když WCF vyvolá metodu <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> v implementaci <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>, toto volání je směrováno na metodu <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> `CustomLeaseExtension`.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-131">When WCF invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method in the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation, this call is routed to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of the `CustomLeaseExtension`.</span></span> <span data-ttu-id="ef9bf-132">Pak `CustomLeaseExtension` zkontroluje svůj privátní stav, aby bylo možné zjistit, zda <xref:System.ServiceModel.InstanceContext> nečinný.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-132">Then, the `CustomLeaseExtension` checks its private state to see whether the <xref:System.ServiceModel.InstanceContext> is idle.</span></span> <span data-ttu-id="ef9bf-133">Pokud je nečinné, vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-133">If it is idle, it returns `true`.</span></span> <span data-ttu-id="ef9bf-134">V opačném případě spustí časovač pro zadanou dobu rozšířené doby života.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-134">Otherwise, it starts a timer for a specified amount of extended lifetime.</span></span>

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

<span data-ttu-id="ef9bf-135">V události `Elapsed` časovače je volána funkce zpětného volání v dispečeru, aby bylo možné spustit další čisticí cyklus.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-135">In the timer’s `Elapsed` event, the callback function in the Dispatcher is called in order to start another clean-up cycle.</span></span>

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

<span data-ttu-id="ef9bf-136">Neexistuje žádný způsob, jak obnovit spuštěný časovač při doručení nové zprávy pro instanci, která je přesunuta do stavu nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-136">There's no way to renew the running timer when a new message arrives for the instance being moved to the idle state.</span></span>

<span data-ttu-id="ef9bf-137">Ukázka implementuje <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> pro zachycení volání metody <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> a jejich směrování do `CustomLeaseExtension`.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-137">The sample implements <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> to intercept the calls to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method and route them to the `CustomLeaseExtension`.</span></span> <span data-ttu-id="ef9bf-138">Implementace <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> je obsažena v `CustomLifetimeLease` třídě.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-138">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is contained in `CustomLifetimeLease` class.</span></span> <span data-ttu-id="ef9bf-139">Metoda <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> je vyvolána, když se chystá služba WCF vydávat instanci služby.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-139">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method is invoked when WCF is about to release the service instance.</span></span> <span data-ttu-id="ef9bf-140">V kolekci <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> ServiceBehavior ale existuje jenom jedna instance konkrétní `ISharedSessionInstance` implementace.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-140">However, there is only one instance of a particular `ISharedSessionInstance` implementation in the ServiceBehavior’s <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> collection.</span></span> <span data-ttu-id="ef9bf-141">To znamená, že neexistuje žádný způsob, jak zjistit, zda je <xref:System.ServiceModel.InstanceContext> uzavřen v době, kdy WCF kontroluje metodu <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-141">This means there's no way of knowing if the <xref:System.ServiceModel.InstanceContext> is closed at the time WCF checks the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span> <span data-ttu-id="ef9bf-142">Proto tato ukázka používá uzamykání vláken k serializaci požadavků na metodu <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-142">Therefore, this sample uses thread locking to serialize requests to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ef9bf-143">Použití uzamykání vlákna není doporučený přístup, protože serializace může mít vážně vliv na výkon aplikace.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-143">Using thread locking is not a recommended approach because serialization can severely affect the performance of your application.</span></span>

<span data-ttu-id="ef9bf-144">Pole privátního člena se používá ve třídě `CustomLifetimeLease` ke sledování stavu nečinnosti a je vráceno metodou <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-144">A private member field is used in the `CustomLifetimeLease` class to track the idle state and is returned by the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span> <span data-ttu-id="ef9bf-145">Pokaždé, když je volána metoda <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>, je vráceno pole `isIdle` a resetování na `false`.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-145">Each time the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method is called, the `isIdle` field is returned and reset to `false`.</span></span>  <span data-ttu-id="ef9bf-146">Je nutné nastavit tuto hodnotu na `false`, abyste se ujistili, že Dispečer volá metodu <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-146">It is essential to set this value to `false` in order to make sure the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method.</span></span>

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

<span data-ttu-id="ef9bf-147">Pokud metoda <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> vrátí `false`, dispečer zaregistruje funkci zpětného volání pomocí metody <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-147">If the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> method returns `false`, the Dispatcher registers a callback function by using the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method.</span></span> <span data-ttu-id="ef9bf-148">Tato metoda obdrží odkaz na vydanou <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-148">This method receives a reference to the <xref:System.ServiceModel.InstanceContext> being released.</span></span> <span data-ttu-id="ef9bf-149">Proto může vzorový kód zadat dotaz na rozšíření typu `ICustomLease` a kontrolovat vlastnost `ICustomLease.IsIdle` v rozšířeném stavu.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-149">Therefore, the sample code can query the `ICustomLease` type extension and check the `ICustomLease.IsIdle` property in the extended state.</span></span>

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

<span data-ttu-id="ef9bf-150">Před zaškrtnutím vlastnosti `ICustomLease.IsIdle` je nutné nastavit vlastnost zpětného volání, protože je to nezbytné pro `CustomLeaseExtension`, aby byl dispečer upozorněn, když se změní na nečinný.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-150">Before the `ICustomLease.IsIdle` property is checked, the Callback property needs to be set as this is essential for `CustomLeaseExtension` to notify the Dispatcher when it becomes idle.</span></span> <span data-ttu-id="ef9bf-151">Pokud `ICustomLease.IsIdle` vrátí `true`, je `isIdle` soukromý člen jednoduše nastaven v `CustomLifetimeLease` na `true` a volá metodu zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-151">If `ICustomLease.IsIdle` returns `true`, the `isIdle` private member is simply set in `CustomLifetimeLease` to `true` and calls the callback method.</span></span> <span data-ttu-id="ef9bf-152">Vzhledem k tomu, že kód drží zámek, jiné vlákna nemohou změnit hodnotu tohoto privátního člena.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-152">Because the code holds a lock, other threads can't change the value of this private member.</span></span> <span data-ttu-id="ef9bf-153">A při příštím volání <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>, vrátí `true` a umožňuje dispečerovi uvolnit instanci.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-153">And the next time Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>, it returns `true` and lets Dispatcher release the instance.</span></span>

<span data-ttu-id="ef9bf-154">Teď, když je základy pro vlastní rozšíření dokončený, musí být připojený k modelu služby.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-154">Now that the groundwork for the custom extension is completed, it has to be hooked up to the service model.</span></span> <span data-ttu-id="ef9bf-155">Chcete-li připojit `CustomLeaseExtension` implementaci do <xref:System.ServiceModel.InstanceContext>, WCF poskytuje rozhraní <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> k provedení zaváděcího programu <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-155">To hook up the `CustomLeaseExtension` implementation to the <xref:System.ServiceModel.InstanceContext>, WCF provides the <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> interface to perform the bootstrapping of <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="ef9bf-156">V ukázce třída `CustomLeaseInitializer` implementuje toto rozhraní a přidá instanci `CustomLeaseExtension` do kolekce <xref:System.ServiceModel.InstanceContext.Extensions%2A> pouze z inicializace metody.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-156">In the sample, the `CustomLeaseInitializer` class implements this interface and adds an instance of `CustomLeaseExtension` to the <xref:System.ServiceModel.InstanceContext.Extensions%2A> collection from the only method initialization.</span></span> <span data-ttu-id="ef9bf-157">Tato metoda je volána dispečerem při inicializaci <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-157">This method is called by Dispatcher while initializing the <xref:System.ServiceModel.InstanceContext>.</span></span>

```csharp
public void InitializeInstanceContext(InstanceContext instanceContext,
    System.ServiceModel.Channels.Message message, IContextChannel channel)

    //...

    IExtension<InstanceContext> customLeaseExtension =
        new CustomLeaseExtension(timeout, headerId);
    instanceContext.Extensions.Add(customLeaseExtension);
}
```

 <span data-ttu-id="ef9bf-158">Nakonec je implementace <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> zapojená do modelu služby pomocí implementace <xref:System.ServiceModel.Description.IServiceBehavior>.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-158">Finally the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is hooked up to the service model by using the <xref:System.ServiceModel.Description.IServiceBehavior> implementation.</span></span> <span data-ttu-id="ef9bf-159">Tato implementace je umístěna ve třídě `CustomLeaseTimeAttribute` a také je odvozena z <xref:System.Attribute> základní třídy k vystavení tohoto chování jako atributu.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-159">This implementation is placed in the `CustomLeaseTimeAttribute` class and it also derives from the <xref:System.Attribute> base class to expose this behavior as an attribute.</span></span>

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

<span data-ttu-id="ef9bf-160">Toto chování lze přidat do ukázkové třídy služby tím, že ji přidáte do atributu `CustomLeaseTime`.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-160">This behavior can be added to a sample service class by annotating it with the `CustomLeaseTime` attribute.</span></span>

```csharp
[CustomLeaseTime(Timeout = 20000)]
public class EchoService : IEchoService
{
  //…
}
```

<span data-ttu-id="ef9bf-161">Při spuštění ukázky se požadavky na operace a odpovědi zobrazí v oknech služba i klientská konzola.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-161">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="ef9bf-162">V každém okně konzoly stiskněte klávesu ENTER a ukončete službu a klienta.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-162">Press ENTER in each console window to shut down the service and client.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ef9bf-163">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="ef9bf-163">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="ef9bf-164">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ef9bf-164">Ensure that you've performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="ef9bf-165">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ef9bf-165">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="ef9bf-166">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ef9bf-166">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ef9bf-167">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-167">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ef9bf-168">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-168">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="ef9bf-169">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-169">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ef9bf-170">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-170">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`
