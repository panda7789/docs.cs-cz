---
title: "Vlastní doba života"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2538a9c483b949dfef1c60bd2225f5daf4e01117
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="custom-lifetime"></a><span data-ttu-id="8af2b-102">Vlastní doba života</span><span class="sxs-lookup"><span data-stu-id="8af2b-102">Custom Lifetime</span></span>
<span data-ttu-id="8af2b-103">Tento příklad ukazuje, jak k zápisu [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] rozšíření k poskytování služeb vlastní doba života sdílených [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] instancí služby.</span><span class="sxs-lookup"><span data-stu-id="8af2b-103">This sample demonstrates how to write a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] extension to provide custom lifetime services for shared [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service instances.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8af2b-104">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="8af2b-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="shared-instancing"></a><span data-ttu-id="8af2b-105">Sdílené, vytváření instancí</span><span class="sxs-lookup"><span data-stu-id="8af2b-105">Shared Instancing</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="8af2b-106">nabízí několik zřizování instancí režimy pro vaše instance služby.</span><span class="sxs-lookup"><span data-stu-id="8af2b-106"> offers several instancing modes for your service instances.</span></span> <span data-ttu-id="8af2b-107">Režim vytváření instancí sdílené zahrnuté v tomto tématu poskytuje způsob, jak sdílet instanci služby mezi více typů komunikačních kanálů.</span><span class="sxs-lookup"><span data-stu-id="8af2b-107">The Shared Instancing mode covered in this topic provides a way to share a service instance between multiple channels.</span></span> <span data-ttu-id="8af2b-108">Klienty můžete buď vyřešit instance adresa koncového bodu místně nebo se obraťte na metoda factory ve službě k získání adresa koncového bodu spuštěné instance.</span><span class="sxs-lookup"><span data-stu-id="8af2b-108">Clients can either resolve the instance’s endpoint address locally or contact a factory method in the service to obtain the endpoint address of a running instance.</span></span> <span data-ttu-id="8af2b-109">Jakmile má adresa koncového bodu, může vytvořit nový kanál a spustit komunikace.</span><span class="sxs-lookup"><span data-stu-id="8af2b-109">Once it has the endpoint address, it can create a new channel and start communication.</span></span> <span data-ttu-id="8af2b-110">Následující fragment kódu ukazuje, jak klientská aplikace vytvoří nový kanál ke stávající instanci služby.</span><span class="sxs-lookup"><span data-stu-id="8af2b-110">The following code snippet shows how a client application creates a new channel to an existing service instance.</span></span>  
  
```  
// Create the first channel.  
IEchoService proxy = channelFactory.CreateChannel();  
  
// Resolve the instance.  
EndpointAddress epa = ((IClientChannel)proxy).ResolveInstance();  
  
// Create new channel factory with the endpoint address resolved by   
// previous statement.  
ChannelFactory<IEchoService> channelFactory2 =  
                new ChannelFactory<IEchoService>("echoservice",  
                epa);  
  
// Create the second channel to the same instance.  
IEchoService proxy2 = channelFactory2.CreateChannel();  
```  
  
 <span data-ttu-id="8af2b-111">Na rozdíl od jiných zřizování instancí režimy režimu sdílení zřizování instancí má jedinečný způsob vydání instance služby.</span><span class="sxs-lookup"><span data-stu-id="8af2b-111">Unlike other instancing modes, the shared instancing mode has a unique way of releasing the service instances.</span></span> <span data-ttu-id="8af2b-112">Když jsou uzavřeny všechny kanály pro instance služby [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime spustí časovač.</span><span class="sxs-lookup"><span data-stu-id="8af2b-112">When all the channels are closed for an instance, the service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime starts a timer.</span></span> <span data-ttu-id="8af2b-113">Pokud nikdo vytvoří připojení, než vyprší časový limit [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uvolní instanci a deklarace identity prostředky.</span><span class="sxs-lookup"><span data-stu-id="8af2b-113">If nobody makes a connection before the timeout expires, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] releases the instance and claims the resources.</span></span> <span data-ttu-id="8af2b-114">Jako součást procesu rušením [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vyvolá <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metoda všech <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementace před uvolněním instance.</span><span class="sxs-lookup"><span data-stu-id="8af2b-114">As a part of the teardown procedure [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of all <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementations before releasing the instance.</span></span> <span data-ttu-id="8af2b-115">Pokud všechny z nich vrátí `true` vydání instance.</span><span class="sxs-lookup"><span data-stu-id="8af2b-115">If all of them return `true` the instance is released.</span></span> <span data-ttu-id="8af2b-116">V opačném případě <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementace je zodpovědná za upozornění `Dispatcher` ze stavu nečinnosti pomocí metody zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="8af2b-116">Otherwise the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is responsible for notifying the `Dispatcher` of the idle state by using a callback method.</span></span>  
  
 <span data-ttu-id="8af2b-117">Ve výchozím nastavení má hodnotu časového limitu nečinnosti <xref:System.ServiceModel.InstanceContext> je jedna minuta.</span><span class="sxs-lookup"><span data-stu-id="8af2b-117">By default, the idle timeout value of <xref:System.ServiceModel.InstanceContext> is one minute.</span></span> <span data-ttu-id="8af2b-118">Ale tento příklad znázorňuje, jak můžete rozšířit pomocí vlastního rozšíření.</span><span class="sxs-lookup"><span data-stu-id="8af2b-118">However this sample demonstrates how you can extend this using a custom extension.</span></span>  
  
## <a name="extending-the-instancecontext"></a><span data-ttu-id="8af2b-119">Rozšíření objekt InstanceContext.</span><span class="sxs-lookup"><span data-stu-id="8af2b-119">Extending the InstanceContext</span></span>  
 <span data-ttu-id="8af2b-120">V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], <xref:System.ServiceModel.InstanceContext> je propojení mezi instance služby a `Dispatcher`.</span><span class="sxs-lookup"><span data-stu-id="8af2b-120">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], <xref:System.ServiceModel.InstanceContext> is the link between the service instance and the `Dispatcher`.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="8af2b-121">Umožňuje rozšířit tuto součást modulu runtime přidáním nového stavu nebo chování pomocí jeho vzor extensible objektu.</span><span class="sxs-lookup"><span data-stu-id="8af2b-121"> allows you to extend this runtime component by adding new state or behavior by using its extensible object pattern.</span></span> <span data-ttu-id="8af2b-122">Vzor extensible objektu se používá v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] buď rozšířit existující třídy runtime s novými funkcemi, nebo při přidání nových funkcí stavu do objektu.</span><span class="sxs-lookup"><span data-stu-id="8af2b-122">The extensible object pattern is used in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="8af2b-123">Existují tři rozhraní ve vzoru extensible objektu: `IExtensibleObject<T>`, `IExtension<T>`, a `IExtensionCollection<T>`.</span><span class="sxs-lookup"><span data-stu-id="8af2b-123">There are three interfaces in the extensible object pattern: `IExtensibleObject<T>`, `IExtension<T>`, and `IExtensionCollection<T>`.</span></span>  
  
 <span data-ttu-id="8af2b-124">`IExtensibleObject<T>` Rozhraní je implementováno modulem objekty, které chcete povolit rozšíření, které přizpůsobení jejich funkce.</span><span class="sxs-lookup"><span data-stu-id="8af2b-124">The `IExtensibleObject<T>` interface is implemented by objects to allow extensions which customize their functionality.</span></span>  
  
 <span data-ttu-id="8af2b-125">`IExtension<T>` Rozhraní je implementováno modulem objekty, které může být rozšíření třídy typu `T`.</span><span class="sxs-lookup"><span data-stu-id="8af2b-125">The `IExtension<T>` interface is implemented by objects that can be extensions of classes of type `T`.</span></span>  
  
 <span data-ttu-id="8af2b-126">A nakonec `IExtensionCollection<T>` rozhraní je kolekce `IExtensions` umožňuje pro načítání `IExtensions` dle jejich typu.</span><span class="sxs-lookup"><span data-stu-id="8af2b-126">And finally, the `IExtensionCollection<T>` interface is a collection of `IExtensions` that allows for retrieving `IExtensions` by their type.</span></span>  
  
 <span data-ttu-id="8af2b-127">Proto chcete-li rozšířit <xref:System.ServiceModel.InstanceContext> musí implementovat `IExtension` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8af2b-127">Therefore in order to extend the <xref:System.ServiceModel.InstanceContext> you must implement the `IExtension` interface.</span></span> <span data-ttu-id="8af2b-128">V tomto projektu vzorku `CustomLeaseExtension` třída obsahuje tato implementace.</span><span class="sxs-lookup"><span data-stu-id="8af2b-128">In this sample project the `CustomLeaseExtension` class contains this implementation.</span></span>  
  
```  
class CustomLeaseExtension : IExtension<InstanceContext>  
{  
}  
```  
  
 <span data-ttu-id="8af2b-129">`IExtension` Rozhraní má dvě metody `Attach` a `Detach`.</span><span class="sxs-lookup"><span data-stu-id="8af2b-129">The `IExtension` interface has two methods `Attach` and `Detach`.</span></span> <span data-ttu-id="8af2b-130">Jako jejich názvy implikují, tyto dvě metody jsou volány při modul runtime připojí a odpojí rozšíření pro instance <xref:System.ServiceModel.InstanceContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="8af2b-130">As their names imply, these two methods are called when the runtime attaches and detaches the extension to an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="8af2b-131">V této ukázce `Attach` metoda se používá ke sledování <xref:System.ServiceModel.InstanceContext> objekt, který patří na aktuální instanci rozšíření.</span><span class="sxs-lookup"><span data-stu-id="8af2b-131">In this sample, the `Attach` method is used to keep track of the <xref:System.ServiceModel.InstanceContext> object that belongs to the current instance of the extension.</span></span>  
  
```  
InstanceContext owner;  
  
public void Attach(InstanceContext owner)  
{  
  this.owner = owner;   
}  
```  
  
 <span data-ttu-id="8af2b-132">Kromě toho musíte přidat potřebné implementaci rozšíření poskytovat podporu delší doba platnosti.</span><span class="sxs-lookup"><span data-stu-id="8af2b-132">In addition, you must add the necessary implementation to the extension to provide the extended lifetime support.</span></span> <span data-ttu-id="8af2b-133">Proto `ICustomLease` rozhraní je deklarovaný s požadovanou metody a je implementována ve `CustomLeaseExtension` třídy.</span><span class="sxs-lookup"><span data-stu-id="8af2b-133">Therefore the `ICustomLease` interface is declared with the desired methods and is implemented in the `CustomLeaseExtension` class.</span></span>  
  
```  
interface ICustomLease  
{  
    bool IsIdle { get; }          
    InstanceContextIdleCallback Callback { get; set; }  
}  
  
class CustomLeaseExtension : IExtension<InstanceContext>, ICustomLease  
{  
}  
```  
  
 <span data-ttu-id="8af2b-134">Když [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vyvolá <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metoda v <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementace toto volání se směruje na <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metodu `CustomLeaseExtension`.</span><span class="sxs-lookup"><span data-stu-id="8af2b-134">When [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method in the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation this call is routed to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of the `CustomLeaseExtension`.</span></span> <span data-ttu-id="8af2b-135">Pak se `CustomLeaseExtension` kontroluje stav privátní zobrazíte jestli <xref:System.ServiceModel.InstanceContext> nečinný.</span><span class="sxs-lookup"><span data-stu-id="8af2b-135">Then the `CustomLeaseExtension` checks its private state to see whether the <xref:System.ServiceModel.InstanceContext> is idle.</span></span> <span data-ttu-id="8af2b-136">Pokud je nečinnosti se vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="8af2b-136">If it is idle it returns `true`.</span></span> <span data-ttu-id="8af2b-137">Jinak spustí časovač po zadanou dobu životnosti rozšířené.</span><span class="sxs-lookup"><span data-stu-id="8af2b-137">Otherwise, it starts a timer for a specified amount of extended lifetime.</span></span>  
  
```  
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
  
 <span data-ttu-id="8af2b-138">V časovače `Elapsed` událost funkce zpětného volání v dispečera je volána, aby bylo možné spustit jinou vyčištění cyklus.</span><span class="sxs-lookup"><span data-stu-id="8af2b-138">In the timer’s `Elapsed` event the callback function in the Dispatcher is called in order to start another clean up cycle.</span></span>  
  
```  
void idleTimer_Elapsed(object sender, ElapsedEventArgs args)  
{  
    idleTimer.Stop();  
    isIdle = true;    
    callback(owner);  
}  
```  
  
 <span data-ttu-id="8af2b-139">Neexistuje žádný způsob, jak obnovit časovač spuštěná, pokud dorazí novou zprávu pro instanci přesouvání do nečinného stavu.</span><span class="sxs-lookup"><span data-stu-id="8af2b-139">There is no way to renew the running timer when a new message arrives for the instance being moved to the idle state.</span></span>  
  
 <span data-ttu-id="8af2b-140">Ukázka implementuje <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> zachytávat volání <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metoda a směrování je `CustomLeaseExtension`.</span><span class="sxs-lookup"><span data-stu-id="8af2b-140">The sample implements <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> to intercept the calls to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method and route them to the `CustomLeaseExtension`.</span></span> <span data-ttu-id="8af2b-141"><xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> Implementace je součástí `CustomLifetimeLease` třídy.</span><span class="sxs-lookup"><span data-stu-id="8af2b-141">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is contained in `CustomLifetimeLease` class.</span></span> <span data-ttu-id="8af2b-142"><xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> Metoda je volána při [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] je verze instance služby.</span><span class="sxs-lookup"><span data-stu-id="8af2b-142">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method is invoked when [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is about to release the service instance.</span></span> <span data-ttu-id="8af2b-143">Je však pouze jednu instanci konkrétní `ISharedSessionInstance` implementace v ServiceBehavior <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> kolekce.</span><span class="sxs-lookup"><span data-stu-id="8af2b-143">However, there is only one instance of a particular `ISharedSessionInstance` implementation in the ServiceBehavior’s <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> collection.</span></span> <span data-ttu-id="8af2b-144">To znamená, že se nedá nijak zjistit, <xref:System.ServiceModel.InstanceContext> dochází k uzavření v době [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kontroluje <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="8af2b-144">This means there is no way of knowing the <xref:System.ServiceModel.InstanceContext> being closed at the time [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] checks the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span> <span data-ttu-id="8af2b-145">Proto tato ukázka používá zámek k serializaci požadavky na přístup z více vláken <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="8af2b-145">Therefore this sample uses thread locking to serialize requests to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8af2b-146">Použití vláken uzamčení není doporučený postup protože serializace vážně mohou ovlivnit výkon vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="8af2b-146">Using thread locking is not a recommended approach because serialization can severely affect the performance of your application.</span></span>  
  
 <span data-ttu-id="8af2b-147">Privátní členské proměnné se používá v `CustomLeaseExtension` třída sledovat `IsIdle` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8af2b-147">A private member variable is used in the `CustomLeaseExtension` class to track the `IsIdle` value.</span></span> <span data-ttu-id="8af2b-148">Pokaždé, když hodnota <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> se načte `IsIdle` privátního člena je vrácen a obnovit `false`.</span><span class="sxs-lookup"><span data-stu-id="8af2b-148">Each time the value of <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> is retrieved the `IsIdle` private member is returned and reset to `false`.</span></span> <span data-ttu-id="8af2b-149">Je nezbytné k nastavení této hodnoty na `false` Pokud chcete mít jistotu dispečera volání <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="8af2b-149">It is essential to set this value to `false` in order to make sure the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method.</span></span>  
  
```  
public bool IsIdle  
{  
    get   
    {  
       lock (thisLock)  
       {  
           bool idleCopy = isIdle;  
           isIdle = false;  
           return idleCopy;  
       }  
    }  
}  
```  
  
 <span data-ttu-id="8af2b-150">Pokud `ISharedSessionLifetime.IsIdle` vlastnost vrátí `false` dispečera zaregistruje funkci zpětného volání pomocí `NotifyIdle` metoda.</span><span class="sxs-lookup"><span data-stu-id="8af2b-150">If the `ISharedSessionLifetime.IsIdle` property returns `false` the Dispatcher registers a callback function by using the `NotifyIdle` method.</span></span> <span data-ttu-id="8af2b-151">Tato metoda přijímá odkaz na <xref:System.ServiceModel.InstanceContext> vydán.</span><span class="sxs-lookup"><span data-stu-id="8af2b-151">This method receives a reference to the <xref:System.ServiceModel.InstanceContext> being released.</span></span> <span data-ttu-id="8af2b-152">Proto můžete dotazovat ukázkový kód `ICustomLease` rozšíření typů a zkontrolujte `ICustomLease.IsIdle` vlastnost v rozšířených stavu.</span><span class="sxs-lookup"><span data-stu-id="8af2b-152">Therefore the sample code can query the `ICustomLease` type extension and check the `ICustomLease.IsIdle` property in the extended state.</span></span>  
  
```  
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
  
 <span data-ttu-id="8af2b-153">Před `ICustomLease.IsIdle` vlastnost je zaškrtnuta možnost vlastnost zpětné volání je třeba nastavit, protože to je nezbytné pro `CustomLeaseExtension` dispečera upozornit, když se stane nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="8af2b-153">Before the `ICustomLease.IsIdle` property is checked the Callback property needs to be set as this is essential for `CustomLeaseExtension` to notify the Dispatcher when it becomes idle.</span></span> <span data-ttu-id="8af2b-154">Pokud `ICustomLease.IsIdle` vrátí `true`, `isIdle` privátního člena je jednoduše nastavena v `CustomLifetimeLease` k `true` a volá metodu zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="8af2b-154">If `ICustomLease.IsIdle` returns `true`, the `isIdle` private member is simply set in `CustomLifetimeLease` to `true` and calls the callback method.</span></span> <span data-ttu-id="8af2b-155">Protože kód obsahuje zámek, jiná vlákna nelze změnit hodnotu této privátního člena.</span><span class="sxs-lookup"><span data-stu-id="8af2b-155">Because the code holds a lock, other threads cannot change the value of this private member.</span></span> <span data-ttu-id="8af2b-156">A při příštím kontroluje dispečera `ISharedSessionLifetime.IsIdle`, vrátí `true` a umožňuje dispečera verzi instance.</span><span class="sxs-lookup"><span data-stu-id="8af2b-156">And the next time Dispatcher checks the `ISharedSessionLifetime.IsIdle`, it returns `true` and lets Dispatcher release the instance.</span></span>  
  
 <span data-ttu-id="8af2b-157">Teď, když základ pro vlastní rozšíření bylo dokončeno, musí být připojených k modelu služby.</span><span class="sxs-lookup"><span data-stu-id="8af2b-157">Now that the groundwork for the custom extension is completed, it has to be hooked up to the service model.</span></span> <span data-ttu-id="8af2b-158">Spojit `CustomLeaseExtension` implementace k <xref:System.ServiceModel.InstanceContext>, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] poskytuje <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> rozhraní k provedení zavádění z <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="8af2b-158">To hook up the `CustomLeaseExtension` implementation to the <xref:System.ServiceModel.InstanceContext>, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides the <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> interface to perform the bootstrapping of <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="8af2b-159">V ukázce `CustomLeaseInitializer` třída implementuje toto rozhraní a přidá instanci `CustomLeaseExtension` k <xref:System.ServiceModel.InstanceContext.Extensions%2A> kolekci z inicializace jedinou metodou.</span><span class="sxs-lookup"><span data-stu-id="8af2b-159">In the sample, the `CustomLeaseInitializer` class implements this interface and adds an instance of `CustomLeaseExtension` to the <xref:System.ServiceModel.InstanceContext.Extensions%2A> collection from the only method initialization.</span></span> <span data-ttu-id="8af2b-160">Tato metoda je volána dispečera při inicializaci <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="8af2b-160">This method is called by Dispatcher while initializing the <xref:System.ServiceModel.InstanceContext>.</span></span>  
  
```  
public void Initialize(InstanceContext instanceContext, Message message)  
{  
  IExtension<InstanceContext> customLeaseExtension =  
    new CustomLeaseExtension(timeout);  
  instanceContext.Extensions.Add(customLeaseExtension);  
}  
```  
  
 <span data-ttu-id="8af2b-161">Nakonec `System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` a <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> implementace je byl zapojen až modelu služby pomocí <xref:System.ServiceModel.Description.IServiceBehavior> implementace.</span><span class="sxs-lookup"><span data-stu-id="8af2b-161">Finally the `System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` and <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> implementations are is hooked up to the service model by using the <xref:System.ServiceModel.Description.IServiceBehavior> implementation.</span></span> <span data-ttu-id="8af2b-162">Tato implementace je umístěn v `CustomLeaseTimeAttribute` třídy a také je odvozena z `Attribute` základní třída vystavit toto chování jako atribut.</span><span class="sxs-lookup"><span data-stu-id="8af2b-162">This implementation is placed in the `CustomLeaseTimeAttribute` class and it also derives from the `Attribute` base class to expose this behavior as an attribute.</span></span> <span data-ttu-id="8af2b-163">V `IServiceBehavior.ApplyBehavior` metoda, instancí <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> a `System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` implementace jsou přidány do `System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextLifetimes` a <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextInitializers%2A> kolekce <xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime> v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="8af2b-163">In the `IServiceBehavior.ApplyBehavior` method, instances of <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> and `System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` implementations are added to the `System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextLifetimes` and <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextInitializers%2A> collections of the <xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime> respectively.</span></span>  
  
```  
public void ApplyBehavior(ServiceDescription description,   
           ServiceHostBase serviceHostBase,   
           Collection<DispatchBehavior> behaviors,  
           Collection<BindingParameterCollection> parameters)  
{  
    CustomLifetimeLease customLease = new CustomLifetimeLease();  
    CustomLeaseInitializer initializer =   
                new CustomLeaseInitializer(timeout);  
  
    foreach (DispatchBehavior dispatchBehavior in behaviors)  
    {  
        dispatchBehavior.InstanceContextLifetimes.Add(customLease);  
        dispatchBehavior.InstanceContextInitializers.Add(initializer);  
    }  
}  
```  
  
 <span data-ttu-id="8af2b-164">Toto chování lze přidat do třídu Ukázka služby podle její zadávání poznámek k `CustomLeaseTime` atribut.</span><span class="sxs-lookup"><span data-stu-id="8af2b-164">This behavior can be added to a sample service class by annotating it with the `CustomLeaseTime` attribute.</span></span>  
  
```  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.Shareable)]  
[CustomLeaseTime(Timeout = 20000)]  
public class EchoService : IEchoService  
{  
  //…  
}  
```  
  
 <span data-ttu-id="8af2b-165">Při spuštění vzorového operaci požadavky a odpovědi se zobrazují v oknech konzoly služby a klienta.</span><span class="sxs-lookup"><span data-stu-id="8af2b-165">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="8af2b-166">Stisknutím klávesy ENTER v každé okna konzoly vypnout klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="8af2b-166">Press ENTER in each console window to shut down the service and client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8af2b-167">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="8af2b-167">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="8af2b-168">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8af2b-168">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="8af2b-169">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8af2b-169">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="8af2b-170">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8af2b-170">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8af2b-171">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="8af2b-171">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8af2b-172">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="8af2b-172">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8af2b-173">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="8af2b-173">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8af2b-174">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="8af2b-174">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`  
  
## <a name="see-also"></a><span data-ttu-id="8af2b-175">Viz také</span><span class="sxs-lookup"><span data-stu-id="8af2b-175">See Also</span></span>
