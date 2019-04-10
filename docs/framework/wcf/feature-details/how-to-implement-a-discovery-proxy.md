---
title: 'Postupy: Implementace zjišťování proxy'
ms.date: 03/30/2017
ms.assetid: 78d70e0a-f6c3-4cfb-a7ca-f66ebddadde0
ms.openlocfilehash: b3e0b5cef01998c1e509586ba1fab3924eb7bc0b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59321013"
---
# <a name="how-to-implement-a-discovery-proxy"></a><span data-ttu-id="f12fe-102">Postupy: Implementace zjišťování proxy</span><span class="sxs-lookup"><span data-stu-id="f12fe-102">How to: Implement a Discovery Proxy</span></span>
<span data-ttu-id="f12fe-103">Toto téma vysvětluje, jak implementace zjišťování proxy.</span><span class="sxs-lookup"><span data-stu-id="f12fe-103">This topic explains how to implement a discovery proxy.</span></span> <span data-ttu-id="f12fe-104">Další informace o funkci zjišťování v Windows Communication Foundation (WCF) najdete v tématu [přehled zjišťování WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f12fe-104">For more information about the discovery feature in Windows Communication Foundation (WCF), see [WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).</span></span> <span data-ttu-id="f12fe-105">Zjišťování proxy můžete implementovat tak, že vytvoříte třídu, která rozšiřuje <xref:System.ServiceModel.Discovery.DiscoveryProxy> abstraktní třídy.</span><span class="sxs-lookup"><span data-stu-id="f12fe-105">A discovery proxy can be implemented by creating a class that extends the <xref:System.ServiceModel.Discovery.DiscoveryProxy> abstract class.</span></span> <span data-ttu-id="f12fe-106">Existuje mnoho z jiné třídy, které podporují definovaný a použít v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="f12fe-106">There are a number of other support classes defined and used in this sample.</span></span> `OnResolveAsyncResult`<span data-ttu-id="f12fe-107">, `OnFindAsyncResult`, a `AsyncResult`.</span><span class="sxs-lookup"><span data-stu-id="f12fe-107">, `OnFindAsyncResult`, and `AsyncResult`.</span></span> <span data-ttu-id="f12fe-108">Tyto třídy implementace <xref:System.IAsyncResult> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f12fe-108">These classes implement the <xref:System.IAsyncResult> interface.</span></span> <span data-ttu-id="f12fe-109">Další informace o <xref:System.IAsyncResult> naleznete v tématu [rozhraní System.IAsyncResult](xref:System.IAsyncResult).</span><span class="sxs-lookup"><span data-stu-id="f12fe-109">For more information about <xref:System.IAsyncResult> see [System.IAsyncResult interface](xref:System.IAsyncResult).</span></span>

 <span data-ttu-id="f12fe-110">Implementace proxy zjišťování je rozdělit do tří hlavních částí v tomto tématu:</span><span class="sxs-lookup"><span data-stu-id="f12fe-110">Implementing a discovery proxy is broken down into three main parts in this topic:</span></span>

-   <span data-ttu-id="f12fe-111">Definujte třídu, která obsahuje úložiště dat a rozšiřuje abstraktní <xref:System.ServiceModel.Discovery.DiscoveryProxy> třídy.</span><span class="sxs-lookup"><span data-stu-id="f12fe-111">Define a class that contains a data store and extends the abstract <xref:System.ServiceModel.Discovery.DiscoveryProxy> class.</span></span>

-   <span data-ttu-id="f12fe-112">Implementace pomocné rutiny `AsyncResult` třídy.</span><span class="sxs-lookup"><span data-stu-id="f12fe-112">Implement the helper `AsyncResult` class.</span></span>

-   <span data-ttu-id="f12fe-113">Hostitel Proxy zjišťování.</span><span class="sxs-lookup"><span data-stu-id="f12fe-113">Host the Discovery Proxy.</span></span>

### <a name="to-create-a-new-console-application-project"></a><span data-ttu-id="f12fe-114">Chcete-li vytvořit nový projekt konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="f12fe-114">To create a new console application project</span></span>

1. <span data-ttu-id="f12fe-115">Start Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="f12fe-115">Start Visual Studio 2012.</span></span>

2. <span data-ttu-id="f12fe-116">Vytvořte nový projekt konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="f12fe-116">Create a new console application project.</span></span> <span data-ttu-id="f12fe-117">Pojmenujte projekt `DiscoveryProxy` a název řešení `DiscoveryProxyExample`.</span><span class="sxs-lookup"><span data-stu-id="f12fe-117">Name the project `DiscoveryProxy` and the name the solution `DiscoveryProxyExample`.</span></span>

3. <span data-ttu-id="f12fe-118">Přidejte následující odkazy do projektu</span><span class="sxs-lookup"><span data-stu-id="f12fe-118">Add the following references to the project</span></span>

    1.  <span data-ttu-id="f12fe-119">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="f12fe-119">System.ServiceModel.dll</span></span>

    2.  <span data-ttu-id="f12fe-120">System.Servicemodel.Discovery.dll</span><span class="sxs-lookup"><span data-stu-id="f12fe-120">System.Servicemodel.Discovery.dll</span></span>

    > [!CAUTION]
    >  <span data-ttu-id="f12fe-121">Ujistěte se, že odkazujete verze 4.0 nebo novější z těchto sestavení.</span><span class="sxs-lookup"><span data-stu-id="f12fe-121">Ensure that you reference version 4.0 or greater of these assemblies.</span></span>

### <a name="to-implement-the-proxydiscoveryservice-class"></a><span data-ttu-id="f12fe-122">Pro implementaci třídy ProxyDiscoveryService</span><span class="sxs-lookup"><span data-stu-id="f12fe-122">To implement the ProxyDiscoveryService class</span></span>

1. <span data-ttu-id="f12fe-123">Přidejte nový soubor kódu do projektu a pojmenujte ho DiscoveryProxy.cs.</span><span class="sxs-lookup"><span data-stu-id="f12fe-123">Add a new code file to your project and name it DiscoveryProxy.cs.</span></span>

2. <span data-ttu-id="f12fe-124">Přidejte následující `using` příkazy DiscoveryProxy.cs.</span><span class="sxs-lookup"><span data-stu-id="f12fe-124">Add the following `using` statements to DiscoveryProxy.cs.</span></span>

    ```
    using System;
    using System.Collections.Generic;
    using System.ServiceModel;
    using System.ServiceModel.Discovery;
    using System.Xml;
    ```

3. <span data-ttu-id="f12fe-125">Odvodit `DiscoveryProxyService` z <xref:System.ServiceModel.Discovery.DiscoveryProxy>.</span><span class="sxs-lookup"><span data-stu-id="f12fe-125">Derive the `DiscoveryProxyService` from <xref:System.ServiceModel.Discovery.DiscoveryProxy>.</span></span> <span data-ttu-id="f12fe-126">Použít `ServiceBehavior` atribut pro třídu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="f12fe-126">Apply the `ServiceBehavior` attribute to the class as shown in the following example.</span></span>

    ```
    // Implement DiscoveryProxy by extending the DiscoveryProxy class and overriding the abstract methods
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single, ConcurrencyMode = ConcurrencyMode.Multiple)]
    public class DiscoveryProxyService : DiscoveryProxy
    {
    }
    ```

4. <span data-ttu-id="f12fe-127">Uvnitř `DiscoveryProxy` třídy definují slovník pro uchování registrovaných služeb.</span><span class="sxs-lookup"><span data-stu-id="f12fe-127">Inside the `DiscoveryProxy` class define a dictionary to hold the registered services.</span></span>

    ```
    // Repository to store EndpointDiscoveryMetadata.
    Dictionary<EndpointAddress, EndpointDiscoveryMetadata> onlineServices;
    ```

5. <span data-ttu-id="f12fe-128">Definujte konstruktor, který inicializuje slovníku.</span><span class="sxs-lookup"><span data-stu-id="f12fe-128">Define a constructor that initializes the dictionary.</span></span>

    ```
    public DiscoveryProxyService()
            {
                this.onlineServices = new Dictionary<EndpointAddress, EndpointDiscoveryMetadata>();
            }
    ```

### <a name="to-define-the-methods-used-to-update-the-discovery-proxy-cache"></a><span data-ttu-id="f12fe-129">Chcete-li definovat metody použité k aktualizaci mezipaměti proxy zjišťování</span><span class="sxs-lookup"><span data-stu-id="f12fe-129">To define the methods used to update the discovery proxy cache</span></span>

1. <span data-ttu-id="f12fe-130">Implementace `AddOnlineservice` metodu pro přidání služby do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="f12fe-130">Implement the `AddOnlineservice` method to add services to the cache.</span></span> <span data-ttu-id="f12fe-131">Tomu se říká pokaždé, když se proxy server přijme zprávu o oznámení.</span><span class="sxs-lookup"><span data-stu-id="f12fe-131">This is called every time the proxy receives an announcement message.</span></span>

    ```
    void AddOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
            {
                lock (this.onlineServices)
                {
                    this.onlineServices[endpointDiscoveryMetadata.Address] = endpointDiscoveryMetadata;
                }

                PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Adding");
            }
    ```

2. <span data-ttu-id="f12fe-132">Implementace `RemoveOnlineService` metodu, která slouží k odebrání služby z mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="f12fe-132">Implement the `RemoveOnlineService` method that is used to remove services from the cache.</span></span>

    ```
    void RemoveOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
            {
                if (endpointDiscoveryMetadata != null)
                {
                    lock (this.onlineServices)
                    {
                        this.onlineServices.Remove(endpointDiscoveryMetadata.Address);
                    }

                    PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Removing");
                }
            }
    ```

3. <span data-ttu-id="f12fe-133">Implementace `MatchFromOnlineService` metody, které se pokoušejí tak, aby odpovídaly služby se službou ve slovníku.</span><span class="sxs-lookup"><span data-stu-id="f12fe-133">Implement the `MatchFromOnlineService` methods that attempt to match a service with a service in the dictionary.</span></span>

    ```
    void MatchFromOnlineService(FindRequestContext findRequestContext)
            {
                lock (this.onlineServices)
                {
                    foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
                    {
                        if (findRequestContext.Criteria.IsMatch(endpointDiscoveryMetadata))
                        {
                            findRequestContext.AddMatchingEndpoint(endpointDiscoveryMetadata);
                        }
                    }
                }
            }
    ```

    ```
    EndpointDiscoveryMetadata MatchFromOnlineService(ResolveCriteria criteria)
            {
                EndpointDiscoveryMetadata matchingEndpoint = null;
                lock (this.onlineServices)
                {
                    foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
                    {
                        if (criteria.Address == endpointDiscoveryMetadata.Address)
                        {
                            matchingEndpoint = endpointDiscoveryMetadata;
                        }
                    }
                }
                return matchingEndpoint;
            }
    ```

4. <span data-ttu-id="f12fe-134">Implementace `PrintDiscoveryMetadata` metodu, která poskytuje uživatelům text konzoly výstupu, jaký zjišťování proxy dělá.</span><span class="sxs-lookup"><span data-stu-id="f12fe-134">Implement the `PrintDiscoveryMetadata` method that provides the user with console text output of what the discovery proxy is doing.</span></span>

    ```
    void PrintDiscoveryMetadata(EndpointDiscoveryMetadata endpointDiscoveryMetadata, string verb)
            {
                Console.WriteLine("\n**** " + verb + " service of the following type from cache. ");
                foreach (XmlQualifiedName contractName in endpointDiscoveryMetadata.ContractTypeNames)
                {
                    Console.WriteLine("** " + contractName.ToString());
                    break;
                }
                Console.WriteLine("**** Operation Completed");
            }
    ```

5. <span data-ttu-id="f12fe-135">Přidejte následující třídy AsyncResult do DiscoveryProxyService.</span><span class="sxs-lookup"><span data-stu-id="f12fe-135">Add the following AsyncResult classes to the DiscoveryProxyService.</span></span> <span data-ttu-id="f12fe-136">Tyto třídy se používají k rozlišení mezi výsledky jiné asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="f12fe-136">These classes are used to differentiate between the different asynchronous operation results.</span></span>

    ```
    sealed class OnOnlineAnnouncementAsyncResult : AsyncResult
            {
                public OnOnlineAnnouncementAsyncResult(AsyncCallback callback, object state)
                    : base(callback, state)
                {
                    this.Complete(true);
                }

                public static void End(IAsyncResult result)
                {
                    AsyncResult.End<OnOnlineAnnouncementAsyncResult>(result);
                }
            }

            sealed class OnOfflineAnnouncementAsyncResult : AsyncResult
            {
                public OnOfflineAnnouncementAsyncResult(AsyncCallback callback, object state)
                    : base(callback, state)
                {
                    this.Complete(true);
                }

                public static void End(IAsyncResult result)
                {
                    AsyncResult.End<OnOfflineAnnouncementAsyncResult>(result);
                }
            }

            sealed class OnFindAsyncResult : AsyncResult
            {
                public OnFindAsyncResult(AsyncCallback callback, object state)
                    : base(callback, state)
                {
                    this.Complete(true);
                }

                public static void End(IAsyncResult result)
                {
                    AsyncResult.End<OnFindAsyncResult>(result);
                }
            }

            sealed class OnResolveAsyncResult : AsyncResult
            {
                EndpointDiscoveryMetadata matchingEndpoint;

                public OnResolveAsyncResult(EndpointDiscoveryMetadata matchingEndpoint, AsyncCallback callback, object state)
                    : base(callback, state)
                {
                    this.matchingEndpoint = matchingEndpoint;
                    this.Complete(true);
                }

                public static EndpointDiscoveryMetadata End(IAsyncResult result)
                {
                    OnResolveAsyncResult thisPtr = AsyncResult.End<OnResolveAsyncResult>(result);
                    return thisPtr.matchingEndpoint;
                }
            }
    ```

### <a name="to-define-the-methods-that-implement-the-discovery-proxy-functionality"></a><span data-ttu-id="f12fe-137">Chcete-li definovat metody, které implementují funkce proxy zjišťování</span><span class="sxs-lookup"><span data-stu-id="f12fe-137">To define the methods that implement the discovery proxy functionality</span></span>

1. <span data-ttu-id="f12fe-138">Přepsat <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOnlineAnnouncement%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="f12fe-138">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOnlineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="f12fe-139">Tato metoda je volána, když proxy zjišťování obdrží zprávu online oznámení.</span><span class="sxs-lookup"><span data-stu-id="f12fe-139">This method is called when the discovery proxy receives an online announcement message.</span></span>

    ```
    // OnBeginOnlineAnnouncement method is called when a Hello message is received by the Proxy
            protected override IAsyncResult OnBeginOnlineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
            {
                this.AddOnlineService(endpointDiscoveryMetadata);
                return new OnOnlineAnnouncementAsyncResult(callback, state);
            }
    ```

2. <span data-ttu-id="f12fe-140">Přepsat <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOnlineAnnouncement%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="f12fe-140">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOnlineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="f12fe-141">Tato metoda je volána, když proxy zjišťování dokončí zpracování zprávy oznámením.</span><span class="sxs-lookup"><span data-stu-id="f12fe-141">This method is called when the discovery proxy finishes processing an announcement message.</span></span>

    ```
    protected override void OnEndOnlineAnnouncement(IAsyncResult result)
            {
                OnOnlineAnnouncementAsyncResult.End(result);
            }
    ```

3. <span data-ttu-id="f12fe-142">Přepsat <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOfflineAnnouncement%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="f12fe-142">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOfflineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="f12fe-143">Tato metoda je volána pomocí zjišťování proxy obdrží zprávu o oznámení v režimu offline.</span><span class="sxs-lookup"><span data-stu-id="f12fe-143">This method is called with the discovery proxy receives an offline announcement message.</span></span>

    ```
    // OnBeginOfflineAnnouncement method is called when a Bye message is received by the Proxy
            protected override IAsyncResult OnBeginOfflineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
            {
                this.RemoveOnlineService(endpointDiscoveryMetadata);
                return new OnOfflineAnnouncementAsyncResult(callback, state);
            }
    ```

4. <span data-ttu-id="f12fe-144">Přepsat <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOfflineAnnouncement%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="f12fe-144">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOfflineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="f12fe-145">Tato metoda je volána, když proxy zjišťování dokončí zpracování zprávu o oznámení v režimu offline.</span><span class="sxs-lookup"><span data-stu-id="f12fe-145">This method is called when the discovery proxy finishes processing an offline announcement message.</span></span>

    ```
    protected override void OnEndOfflineAnnouncement(IAsyncResult result)
            {
                OnOfflineAnnouncementAsyncResult.End(result);
            }
    ```

5. <span data-ttu-id="f12fe-146">Přepsat <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="f12fe-146">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="f12fe-147">Tato metoda je volána, když přijme požadavek hledání proxy zjišťování.</span><span class="sxs-lookup"><span data-stu-id="f12fe-147">This method is called when the discovery proxy receives a find request.</span></span>

    ```
    // OnBeginFind method is called when a Probe request message is received by the Proxy
            protected override IAsyncResult OnBeginFind(FindRequestContext findRequestContext, AsyncCallback callback, object state)
            {
                this.MatchFromOnlineService(findRequestContext);
                return new OnFindAsyncResult(callback, state);
            }
    protected override IAsyncResult OnBeginFind(FindRequest findRequest, AsyncCallback callback, object state)
    {
        Collection<EndpointDiscoveryMetadata> matchingEndpoints = MatchFromCache(findRequest.Criteria);
        return new OnFindAsyncResult(
                    matchingEndpoints,
                    callback,
                    state);
    }
    ```

6. <span data-ttu-id="f12fe-148">Přepsat <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="f12fe-148">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="f12fe-149">Tato metoda je volána po dokončení zjišťování proxy zpracování požadavku hledání.</span><span class="sxs-lookup"><span data-stu-id="f12fe-149">This method is called when the discovery proxy finishes processing a find request.</span></span>

    ```
    protected override void OnEndFind(IAsyncResult result)
            {
                OnFindAsyncResult.End(result);
            }
    ```

7. <span data-ttu-id="f12fe-150">Přepsat <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginResolve%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="f12fe-150">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginResolve%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="f12fe-151">Tato metoda je volána, když proxy zjišťování přijme zprávu vyřešit.</span><span class="sxs-lookup"><span data-stu-id="f12fe-151">This method is called when the discovery proxy receives a resolve message.</span></span>

    ```
    // OnBeginFind method is called when a Resolve request message is received by the Proxy
            protected override IAsyncResult OnBeginResolve(ResolveCriteria resolveCriteria, AsyncCallback callback, object state)
            {
                return new OnResolveAsyncResult(this.MatchFromOnlineService(resolveCriteria), callback, state);
            }
    protected override IAsyncResult OnBeginResolve(ResolveRequest resolveRequest, AsyncCallback callback, object state)
    {
        return new OnResolveAsyncResult(
            this.proxy.MatchFromOnlineService(resolveRequest.Criteria),
            callback,
            state);
    }
    ```

8. <span data-ttu-id="f12fe-152">Přepsat <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndResolve%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="f12fe-152">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndResolve%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="f12fe-153">Tato metoda je volána po dokončení zjišťování proxy zpracovává zprávu vyřešit.</span><span class="sxs-lookup"><span data-stu-id="f12fe-153">This method is called when the discovery proxy finishes processing a resolve message.</span></span>

    ```
    protected override EndpointDiscoveryMetadata OnEndResolve(IAsyncResult result)
    {
        return OnResolveAsyncResult.End(result);
    }
    ```

 <span data-ttu-id="f12fe-154">OnBegin...</span><span class="sxs-lookup"><span data-stu-id="f12fe-154">The OnBegin..</span></span> <span data-ttu-id="f12fe-155">/ OnEnd...</span><span class="sxs-lookup"><span data-stu-id="f12fe-155">/ OnEnd..</span></span> <span data-ttu-id="f12fe-156">metody poskytují logiku pro zjišťování dalších operací.</span><span class="sxs-lookup"><span data-stu-id="f12fe-156">methods provide the logic for the subsequent discovery operations.</span></span> <span data-ttu-id="f12fe-157">Například <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A> a <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A> metody implementovat logiku hledání pro zjišťování proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="f12fe-157">For example the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A> and <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A> methods implement the find logic for discovery proxy.</span></span> <span data-ttu-id="f12fe-158">Přijetí zprávy test proxy zjišťování jsou tyto metody provádět odeslat odpověď zpět klientovi.</span><span class="sxs-lookup"><span data-stu-id="f12fe-158">When the discovery proxy receives a probe message these methods are executed to send a response back to the client.</span></span> <span data-ttu-id="f12fe-159">Můžete upravit logiku hledání podle potřeby, například můžete začlenit vlastní obor odpovídající algoritmy nebo konkrétní metadat XML aplikace analýze jako součást operace hledání.</span><span class="sxs-lookup"><span data-stu-id="f12fe-159">You may modify the find logic as you wish, for example you can incorporate custom scope matching by algorithms or application specific XML metadata parsing as part of your find operation.</span></span>

### <a name="to-implement-the-asyncresult-class"></a><span data-ttu-id="f12fe-160">Chcete-li implementovat třídu AsyncResult</span><span class="sxs-lookup"><span data-stu-id="f12fe-160">To implement the AsyncResult class</span></span>

1. <span data-ttu-id="f12fe-161">Definujte abstraktní základní třídu AsyncResult, který se používá k odvození různých tříd asynchronní výsledek.</span><span class="sxs-lookup"><span data-stu-id="f12fe-161">Define the abstract base class AsyncResult which is used to derive the various async result classes.</span></span>

2. <span data-ttu-id="f12fe-162">Vytvořte nový soubor kódu s názvem AsyncResult.cs.</span><span class="sxs-lookup"><span data-stu-id="f12fe-162">Create a new code file called AsyncResult.cs.</span></span>

3. <span data-ttu-id="f12fe-163">Přidejte následující `using` příkazy AsyncResult.cs.</span><span class="sxs-lookup"><span data-stu-id="f12fe-163">Add the following `using` statements to AsyncResult.cs.</span></span>

    ```
    using System;
    using System.Threading;
    ```

4. <span data-ttu-id="f12fe-164">Přidejte následující třídu AsyncResult.</span><span class="sxs-lookup"><span data-stu-id="f12fe-164">Add the following AsyncResult class.</span></span>

    ```
    abstract class AsyncResult : IAsyncResult
        {
            AsyncCallback callback;
            bool completedSynchronously;
            bool endCalled;
            Exception exception;
            bool isCompleted;
            ManualResetEvent manualResetEvent;
            object state;
            object thisLock;

            protected AsyncResult(AsyncCallback callback, object state)
            {
                this.callback = callback;
                this.state = state;
                this.thisLock = new object();
            }

            public object AsyncState
            {
                get
                {
                    return state;
                }
            }

            public WaitHandle AsyncWaitHandle
            {
                get
                {
                    if (manualResetEvent != null)
                    {
                        return manualResetEvent;
                    }
                    lock (ThisLock)
                    {
                        if (manualResetEvent == null)
                        {
                            manualResetEvent = new ManualResetEvent(isCompleted);
                        }
                    }
                    return manualResetEvent;
                }
            }

            public bool CompletedSynchronously
            {
                get
                {
                    return completedSynchronously;
                }
            }

            public bool IsCompleted
            {
                get
                {
                    return isCompleted;
                }
            }

            object ThisLock
            {
                get
                {
                    return this.thisLock;
                }
            }

            protected static TAsyncResult End<TAsyncResult>(IAsyncResult result)
                where TAsyncResult : AsyncResult
            {
                if (result == null)
                {
                    throw new ArgumentNullException("result");
                }

                TAsyncResult asyncResult = result as TAsyncResult;

                if (asyncResult == null)
                {
                    throw new ArgumentException("Invalid async result.", "result");
                }

                if (asyncResult.endCalled)
                {
                    throw new InvalidOperationException("Async object already ended.");
                }

                asyncResult.endCalled = true;

                if (!asyncResult.isCompleted)
                {
                    asyncResult.AsyncWaitHandle.WaitOne();
                }

                if (asyncResult.manualResetEvent != null)
                {
                    asyncResult.manualResetEvent.Close();
                }

                if (asyncResult.exception != null)
                {
                    throw asyncResult.exception;
                }

                return asyncResult;
            }

            protected void Complete(bool completedSynchronously)
            {
                if (isCompleted)
                {
                    throw new InvalidOperationException("This async result is already completed.");
                }

                this.completedSynchronously = completedSynchronously;

                if (completedSynchronously)
                {
                    this.isCompleted = true;
                }
                else
                {
                    lock (ThisLock)
                    {
                        this.isCompleted = true;
                        if (this.manualResetEvent != null)
                        {
                            this.manualResetEvent.Set();
                        }
                    }
                }

                if (callback != null)
                {
                    callback(this);
                }
            }

            protected void Complete(bool completedSynchronously, Exception exception)
            {
                this.exception = exception;
                Complete(completedSynchronously);
            }
        }
    ```

### <a name="to-host-the-discoveryproxy"></a><span data-ttu-id="f12fe-165">K hostování objektu DiscoveryProxy.</span><span class="sxs-lookup"><span data-stu-id="f12fe-165">To host the DiscoveryProxy</span></span>

1. <span data-ttu-id="f12fe-166">Otevřete soubor Program.cs v projektu DiscoveryProxyExample.</span><span class="sxs-lookup"><span data-stu-id="f12fe-166">Open the Program.cs file in the DiscoveryProxyExample project.</span></span>

2. <span data-ttu-id="f12fe-167">Přidejte následující `using` příkazy.</span><span class="sxs-lookup"><span data-stu-id="f12fe-167">Add the following `using` statements.</span></span>

    ```
    using System;
    using System.ServiceModel;
    using System.ServiceModel.Discovery;
    ```

3. <span data-ttu-id="f12fe-168">V rámci `Main()` metodu, přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="f12fe-168">Within the `Main()` method, add the following code.</span></span> <span data-ttu-id="f12fe-169">Tím se vytvoří instance `DiscoveryProxy` třídy.</span><span class="sxs-lookup"><span data-stu-id="f12fe-169">This creates an instance of the `DiscoveryProxy` class.</span></span>

    ```
    Uri probeEndpointAddress = new Uri("net.tcp://localhost:8001/Probe");
                Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

                // Host the DiscoveryProxy service
                ServiceHost proxyServiceHost = new ServiceHost(new DiscoveryProxyService());
    ```

4. <span data-ttu-id="f12fe-170">Dále přidejte následující kód k přidání koncového bodu zjišťování a koncový bod oznámení.</span><span class="sxs-lookup"><span data-stu-id="f12fe-170">Next add the following code to add a discovery endpoint and an announcement endpoint.</span></span>

    ```
    try
              {
                  // Add DiscoveryEndpoint to receive Probe and Resolve messages
                  DiscoveryEndpoint discoveryEndpoint = new DiscoveryEndpoint(new NetTcpBinding(), new EndpointAddress(probeEndpointAddress));
                  discoveryEndpoint.IsSystemEndpoint = false;

                  // Add AnnouncementEndpoint to receive Hello and Bye announcement messages
                  AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(), new EndpointAddress(announcementEndpointAddress));

                  proxyServiceHost.AddServiceEndpoint(discoveryEndpoint);
                  proxyServiceHost.AddServiceEndpoint(announcementEndpoint);

                  proxyServiceHost.Open();

                  Console.WriteLine("Proxy Service started.");
                  Console.WriteLine();
                  Console.WriteLine("Press <ENTER> to terminate the service.");
                  Console.WriteLine();
                  Console.ReadLine();

                  proxyServiceHost.Close();
              }
              catch (CommunicationException e)
              {
                  Console.WriteLine(e.Message);
              }
              catch (TimeoutException e)
              {
                  Console.WriteLine(e.Message);
              }

              if (proxyServiceHost.State != CommunicationState.Closed)
              {
                  Console.WriteLine("Aborting the service...");
                  proxyServiceHost.Abort();
              }
    ```

 <span data-ttu-id="f12fe-171">Dokončili jste implementace proxy zjišťování.</span><span class="sxs-lookup"><span data-stu-id="f12fe-171">You have completed implementing the discovery proxy.</span></span> <span data-ttu-id="f12fe-172">Pokračovat k [jak: Implementace zjistitelné služby, která se registruje pomocí Proxy zjišťování](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md).</span><span class="sxs-lookup"><span data-stu-id="f12fe-172">Continue on to [How to: Implement a Discoverable Service that Registers with the Discovery Proxy](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md).</span></span>

## <a name="example"></a><span data-ttu-id="f12fe-173">Příklad</span><span class="sxs-lookup"><span data-stu-id="f12fe-173">Example</span></span>
 <span data-ttu-id="f12fe-174">Toto je úplný přehled kód použitý v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="f12fe-174">This is the full listing of the code used in this topic.</span></span>

```
// DiscoveryProxy.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.Collections.Generic;
using System.ServiceModel;
using System.ServiceModel.Discovery;
using System.Xml;

namespace Microsoft.Samples.Discovery
{
    // Implement DiscoveryProxy by extending the DiscoveryProxy class and overriding the abstract methods
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single, ConcurrencyMode = ConcurrencyMode.Multiple)]
    public class DiscoveryProxyService : DiscoveryProxy
    {
        // Repository to store EndpointDiscoveryMetadata. A database or a flat file could also be used instead.
        Dictionary<EndpointAddress, EndpointDiscoveryMetadata> onlineServices;

        public DiscoveryProxyService()
        {
            this.onlineServices = new Dictionary<EndpointAddress, EndpointDiscoveryMetadata>();
        }

        // OnBeginOnlineAnnouncement method is called when a Hello message is received by the Proxy
        protected override IAsyncResult OnBeginOnlineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
        {
            this.AddOnlineService(endpointDiscoveryMetadata);
            return new OnOnlineAnnouncementAsyncResult(callback, state);
        }

        protected override void OnEndOnlineAnnouncement(IAsyncResult result)
        {
            OnOnlineAnnouncementAsyncResult.End(result);
        }

        // OnBeginOfflineAnnouncement method is called when a Bye message is received by the Proxy
        protected override IAsyncResult OnBeginOfflineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
        {
            this.RemoveOnlineService(endpointDiscoveryMetadata);
            return new OnOfflineAnnouncementAsyncResult(callback, state);
        }

        protected override void OnEndOfflineAnnouncement(IAsyncResult result)
        {
            OnOfflineAnnouncementAsyncResult.End(result);
        }

        // OnBeginFind method is called when a Probe request message is received by the Proxy
        protected override IAsyncResult OnBeginFind(FindRequestContext findRequestContext, AsyncCallback callback, object state)
        {
            this.MatchFromOnlineService(findRequestContext);
            return new OnFindAsyncResult(callback, state);
        }

        protected override void OnEndFind(IAsyncResult result)
        {
            OnFindAsyncResult.End(result);
        }

        // OnBeginFind method is called when a Resolve request message is received by the Proxy
        protected override IAsyncResult OnBeginResolve(ResolveCriteria resolveCriteria, AsyncCallback callback, object state)
        {
            return new OnResolveAsyncResult(this.MatchFromOnlineService(resolveCriteria), callback, state);
        }

        protected override EndpointDiscoveryMetadata OnEndResolve(IAsyncResult result)
        {
            return OnResolveAsyncResult.End(result);
        }

        // The following are helper methods required by the Proxy implementation
        void AddOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
        {
            lock (this.onlineServices)
            {
                this.onlineServices[endpointDiscoveryMetadata.Address] = endpointDiscoveryMetadata;
            }

            PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Adding");
        }

        void RemoveOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
        {
            if (endpointDiscoveryMetadata != null)
            {
                lock (this.onlineServices)
                {
                    this.onlineServices.Remove(endpointDiscoveryMetadata.Address);
                }

                PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Removing");
            }
        }

        void MatchFromOnlineService(FindRequestContext findRequestContext)
        {
            lock (this.onlineServices)
            {
                foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
                {
                    if (findRequestContext.Criteria.IsMatch(endpointDiscoveryMetadata))
                    {
                        findRequestContext.AddMatchingEndpoint(endpointDiscoveryMetadata);
                    }
                }
            }
        }

        EndpointDiscoveryMetadata MatchFromOnlineService(ResolveCriteria criteria)
        {
            EndpointDiscoveryMetadata matchingEndpoint = null;
            lock (this.onlineServices)
            {
                foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
                {
                    if (criteria.Address == endpointDiscoveryMetadata.Address)
                    {
                        matchingEndpoint = endpointDiscoveryMetadata;
                    }
                }
            }
            return matchingEndpoint;
        }

        void PrintDiscoveryMetadata(EndpointDiscoveryMetadata endpointDiscoveryMetadata, string verb)
        {
            Console.WriteLine("\n**** " + verb + " service of the following type from cache. ");
            foreach (XmlQualifiedName contractName in endpointDiscoveryMetadata.ContractTypeNames)
            {
                Console.WriteLine("** " + contractName.ToString());
                break;
            }
            Console.WriteLine("**** Operation Completed");
        }

        sealed class OnOnlineAnnouncementAsyncResult : AsyncResult
        {
            public OnOnlineAnnouncementAsyncResult(AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.Complete(true);
            }

            public static void End(IAsyncResult result)
            {
                AsyncResult.End<OnOnlineAnnouncementAsyncResult>(result);
            }
        }

        sealed class OnOfflineAnnouncementAsyncResult : AsyncResult
        {
            public OnOfflineAnnouncementAsyncResult(AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.Complete(true);
            }

            public static void End(IAsyncResult result)
            {
                AsyncResult.End<OnOfflineAnnouncementAsyncResult>(result);
            }
        }

        sealed class OnFindAsyncResult : AsyncResult
        {
            public OnFindAsyncResult(AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.Complete(true);
            }

            public static void End(IAsyncResult result)
            {
                AsyncResult.End<OnFindAsyncResult>(result);
            }
        }

        sealed class OnResolveAsyncResult : AsyncResult
        {
            EndpointDiscoveryMetadata matchingEndpoint;

            public OnResolveAsyncResult(EndpointDiscoveryMetadata matchingEndpoint, AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.matchingEndpoint = matchingEndpoint;
                this.Complete(true);
            }

            public static EndpointDiscoveryMetadata End(IAsyncResult result)
            {
                OnResolveAsyncResult thisPtr = AsyncResult.End<OnResolveAsyncResult>(result);
                return thisPtr.matchingEndpoint;
            }
        }
    }
}
```

```
// AsyncResult.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.Threading;

namespace Microsoft.Samples.Discovery
{
    abstract class AsyncResult : IAsyncResult
    {
        AsyncCallback callback;
        bool completedSynchronously;
        bool endCalled;
        Exception exception;
        bool isCompleted;
        ManualResetEvent manualResetEvent;
        object state;
        object thisLock;

        protected AsyncResult(AsyncCallback callback, object state)
        {
            this.callback = callback;
            this.state = state;
            this.thisLock = new object();
        }

        public object AsyncState
        {
            get
            {
                return state;
            }
        }

        public WaitHandle AsyncWaitHandle
        {
            get
            {
                if (manualResetEvent != null)
                {
                    return manualResetEvent;
                }
                lock (ThisLock)
                {
                    if (manualResetEvent == null)
                    {
                        manualResetEvent = new ManualResetEvent(isCompleted);
                    }
                }
                return manualResetEvent;
            }
        }

        public bool CompletedSynchronously
        {
            get
            {
                return completedSynchronously;
            }
        }

        public bool IsCompleted
        {
            get
            {
                return isCompleted;
            }
        }

        object ThisLock
        {
            get
            {
                return this.thisLock;
            }
        }

        protected static TAsyncResult End<TAsyncResult>(IAsyncResult result)
            where TAsyncResult : AsyncResult
        {
            if (result == null)
            {
                throw new ArgumentNullException("result");
            }

            TAsyncResult asyncResult = result as TAsyncResult;

            if (asyncResult == null)
            {
                throw new ArgumentException("Invalid async result.", "result");
            }

            if (asyncResult.endCalled)
            {
                throw new InvalidOperationException("Async object already ended.");
            }

            asyncResult.endCalled = true;

            if (!asyncResult.isCompleted)
            {
                asyncResult.AsyncWaitHandle.WaitOne();
            }

            if (asyncResult.manualResetEvent != null)
            {
                asyncResult.manualResetEvent.Close();
            }

            if (asyncResult.exception != null)
            {
                throw asyncResult.exception;
            }

            return asyncResult;
        }

        protected void Complete(bool completedSynchronously)
        {
            if (isCompleted)
            {
                throw new InvalidOperationException("This async result is already completed.");
            }

            this.completedSynchronously = completedSynchronously;

            if (completedSynchronously)
            {
                this.isCompleted = true;
            }
            else
            {
                lock (ThisLock)
                {
                    this.isCompleted = true;
                    if (this.manualResetEvent != null)
                    {
                        this.manualResetEvent.Set();
                    }
                }
            }

            if (callback != null)
            {
                callback(this);
            }
        }

        protected void Complete(bool completedSynchronously, Exception exception)
        {
            this.exception = exception;
            Complete(completedSynchronously);
        }
    }
}
```

```
// program.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.ServiceModel;
using System.ServiceModel.Discovery;

namespace Microsoft.Samples.Discovery
{
    class Program
    {
        public static void Main()
        {
            Uri probeEndpointAddress = new Uri("net.tcp://localhost:8001/Probe");
            Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

            // Host the DiscoveryProxy service
            ServiceHost proxyServiceHost = new ServiceHost(new DiscoveryProxyService());

            try
            {
                // Add DiscoveryEndpoint to receive Probe and Resolve messages
                DiscoveryEndpoint discoveryEndpoint = new DiscoveryEndpoint(new NetTcpBinding(), new EndpointAddress(probeEndpointAddress));
                discoveryEndpoint.IsSystemEndpoint = false;

                // Add AnnouncementEndpoint to receive Hello and Bye announcement messages
                AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(), new EndpointAddress(announcementEndpointAddress));

                proxyServiceHost.AddServiceEndpoint(discoveryEndpoint);
                proxyServiceHost.AddServiceEndpoint(announcementEndpoint);

                proxyServiceHost.Open();

                Console.WriteLine("Proxy Service started.");
                Console.WriteLine();
                Console.WriteLine("Press <ENTER> to terminate the service.");
                Console.WriteLine();
                Console.ReadLine();

                proxyServiceHost.Close();
            }
            catch (CommunicationException e)
            {
                Console.WriteLine(e.Message);
            }
            catch (TimeoutException e)
            {
                Console.WriteLine(e.Message);
            }

            if (proxyServiceHost.State != CommunicationState.Closed)
            {
                Console.WriteLine("Aborting the service...");
                proxyServiceHost.Abort();
            }
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="f12fe-175">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f12fe-175">See also</span></span>

- [<span data-ttu-id="f12fe-176">Přehled zjišťování WCF</span><span class="sxs-lookup"><span data-stu-id="f12fe-176">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [<span data-ttu-id="f12fe-177">Postupy: Implementace zjistitelné služby, která se registruje pomocí proxy zjišťování</span><span class="sxs-lookup"><span data-stu-id="f12fe-177">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)
- [<span data-ttu-id="f12fe-178">Postupy: Implementace klientské aplikace používající zjišťování proxy k vyhledání služby</span><span class="sxs-lookup"><span data-stu-id="f12fe-178">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
- [<span data-ttu-id="f12fe-179">Postupy: Test proxy zjišťování</span><span class="sxs-lookup"><span data-stu-id="f12fe-179">How to: Test the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)