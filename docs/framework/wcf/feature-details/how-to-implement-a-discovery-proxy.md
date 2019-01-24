---
title: 'Postupy: Implementace zjišťování proxy'
ms.date: 03/30/2017
ms.assetid: 78d70e0a-f6c3-4cfb-a7ca-f66ebddadde0
ms.openlocfilehash: 12adc7215e929bb56aafe104546eb6e58af52ddb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608911"
---
# <a name="how-to-implement-a-discovery-proxy"></a>Postupy: Implementace zjišťování proxy
Toto téma vysvětluje, jak implementace zjišťování proxy. Další informace o funkci zjišťování v Windows Communication Foundation (WCF) najdete v tématu [přehled zjišťování WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md). Zjišťování proxy můžete implementovat tak, že vytvoříte třídu, která rozšiřuje <xref:System.ServiceModel.Discovery.DiscoveryProxy> abstraktní třídy. Existuje mnoho z jiné třídy, které podporují definovaný a použít v této ukázce. `OnResolveAsyncResult`, `OnFindAsyncResult`, a `AsyncResult`. Tyto třídy implementace <xref:System.IAsyncResult> rozhraní. Další informace o <xref:System.IAsyncResult> naleznete v tématu [rozhraní System.IAsyncResult](xref:System.IAsyncResult).

 Implementace proxy zjišťování je rozdělit do tří hlavních částí v tomto tématu:

-   Definujte třídu, která obsahuje úložiště dat a rozšiřuje abstraktní <xref:System.ServiceModel.Discovery.DiscoveryProxy> třídy.

-   Implementace pomocné rutiny `AsyncResult` třídy.

-   Hostitel Proxy zjišťování.

### <a name="to-create-a-new-console-application-project"></a>Chcete-li vytvořit nový projekt konzolové aplikace

1.  Start Visual Studio 2012.

2.  Vytvořte nový projekt konzolové aplikace. Pojmenujte projekt `DiscoveryProxy` a název řešení `DiscoveryProxyExample`.

3.  Přidejte následující odkazy do projektu

    1.  System.ServiceModel.dll

    2.  System.Servicemodel.Discovery.dll

    > [!CAUTION]
    >  Ujistěte se, že odkazujete verze 4.0 nebo novější z těchto sestavení.

### <a name="to-implement-the-proxydiscoveryservice-class"></a>Pro implementaci třídy ProxyDiscoveryService

1.  Přidejte nový soubor kódu do projektu a pojmenujte ho DiscoveryProxy.cs.

2.  Přidejte následující `using` příkazy DiscoveryProxy.cs.

    ```
    using System;
    using System.Collections.Generic;
    using System.ServiceModel;
    using System.ServiceModel.Discovery;
    using System.Xml;
    ```

3.  Odvodit `DiscoveryProxyService` z <xref:System.ServiceModel.Discovery.DiscoveryProxy>. Použít `ServiceBehavior` atribut pro třídu, jak je znázorněno v následujícím příkladu.

    ```
    // Implement DiscoveryProxy by extending the DiscoveryProxy class and overriding the abstract methods
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single, ConcurrencyMode = ConcurrencyMode.Multiple)]
    public class DiscoveryProxyService : DiscoveryProxy
    {
    }
    ```

4.  Uvnitř `DiscoveryProxy` třídy definují slovník pro uchování registrovaných služeb.

    ```
    // Repository to store EndpointDiscoveryMetadata.
    Dictionary<EndpointAddress, EndpointDiscoveryMetadata> onlineServices;
    ```

5.  Definujte konstruktor, který inicializuje slovníku.

    ```
    public DiscoveryProxyService()
            {
                this.onlineServices = new Dictionary<EndpointAddress, EndpointDiscoveryMetadata>();
            }
    ```

### <a name="to-define-the-methods-used-to-update-the-discovery-proxy-cache"></a>Chcete-li definovat metody použité k aktualizaci mezipaměti proxy zjišťování

1.  Implementace `AddOnlineservice` metodu pro přidání služby do mezipaměti. Tomu se říká pokaždé, když se proxy server přijme zprávu o oznámení.

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

2.  Implementace `RemoveOnlineService` metodu, která slouží k odebrání služby z mezipaměti.

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

3.  Implementace `MatchFromOnlineService` metody, které se pokoušejí tak, aby odpovídaly služby se službou ve slovníku.

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

4.  Implementace `PrintDiscoveryMetadata` metodu, která poskytuje uživatelům text konzoly výstupu, jaký zjišťování proxy dělá.

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

5.  Přidejte následující třídy AsyncResult do DiscoveryProxyService. Tyto třídy se používají k rozlišení mezi výsledky jiné asynchronní operace.

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

### <a name="to-define-the-methods-that-implement-the-discovery-proxy-functionality"></a>Chcete-li definovat metody, které implementují funkce proxy zjišťování

1.  Přepsat <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOnlineAnnouncement%2A?displayProperty=nameWithType> metody. Tato metoda je volána, když proxy zjišťování obdrží zprávu online oznámení.

    ```
    // OnBeginOnlineAnnouncement method is called when a Hello message is received by the Proxy
            protected override IAsyncResult OnBeginOnlineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
            {
                this.AddOnlineService(endpointDiscoveryMetadata);
                return new OnOnlineAnnouncementAsyncResult(callback, state);
            }
    ```

2.  Přepsat <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOnlineAnnouncement%2A?displayProperty=nameWithType> metody. Tato metoda je volána, když proxy zjišťování dokončí zpracování zprávy oznámením.

    ```
    protected override void OnEndOnlineAnnouncement(IAsyncResult result)
            {
                OnOnlineAnnouncementAsyncResult.End(result);
            }
    ```

3.  Přepsat <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOfflineAnnouncement%2A?displayProperty=nameWithType> metody. Tato metoda je volána pomocí zjišťování proxy obdrží zprávu o oznámení v režimu offline.

    ```
    // OnBeginOfflineAnnouncement method is called when a Bye message is received by the Proxy
            protected override IAsyncResult OnBeginOfflineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
            {
                this.RemoveOnlineService(endpointDiscoveryMetadata);
                return new OnOfflineAnnouncementAsyncResult(callback, state);
            }
    ```

4.  Přepsat <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOfflineAnnouncement%2A?displayProperty=nameWithType> metody. Tato metoda je volána, když proxy zjišťování dokončí zpracování zprávu o oznámení v režimu offline.

    ```
    protected override void OnEndOfflineAnnouncement(IAsyncResult result)
            {
                OnOfflineAnnouncementAsyncResult.End(result);
            }
    ```

5.  Přepsat <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> metody. Tato metoda je volána, když přijme požadavek hledání proxy zjišťování.

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

6.  Přepsat <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A?displayProperty=nameWithType> metody. Tato metoda je volána po dokončení zjišťování proxy zpracování požadavku hledání.

    ```
    protected override void OnEndFind(IAsyncResult result)
            {
                OnFindAsyncResult.End(result);
            }
    ```

7.  Přepsat <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginResolve%2A?displayProperty=nameWithType> metody. Tato metoda je volána, když proxy zjišťování přijme zprávu vyřešit.

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

8.  Přepsat <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndResolve%2A?displayProperty=nameWithType> metody. Tato metoda je volána po dokončení zjišťování proxy zpracovává zprávu vyřešit.

    ```
    protected override EndpointDiscoveryMetadata OnEndResolve(IAsyncResult result)
    {
        return OnResolveAsyncResult.End(result);
    }
    ```

 OnBegin... / OnEnd... metody poskytují logiku pro zjišťování dalších operací. Například <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A> a <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A> metody implementovat logiku hledání pro zjišťování proxy serveru. Přijetí zprávy test proxy zjišťování jsou tyto metody provádět odeslat odpověď zpět klientovi. Můžete upravit logiku hledání podle potřeby, například můžete začlenit vlastní obor odpovídající algoritmy nebo konkrétní metadat XML aplikace analýze jako součást operace hledání.

### <a name="to-implement-the-asyncresult-class"></a>Chcete-li implementovat třídu AsyncResult

1.  Definujte abstraktní základní třídu AsyncResult, který se používá k odvození různých tříd asynchronní výsledek.

2.  Vytvořte nový soubor kódu s názvem AsyncResult.cs.

3.  Přidejte následující `using` příkazy AsyncResult.cs.

    ```
    using System;
    using System.Threading;
    ```

4.  Přidejte následující třídu AsyncResult.

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

### <a name="to-host-the-discoveryproxy"></a>K hostování objektu DiscoveryProxy.

1.  Otevřete soubor Program.cs v projektu DiscoveryProxyExample.

2.  Přidejte následující `using` příkazy.

    ```
    using System;
    using System.ServiceModel;
    using System.ServiceModel.Discovery;
    ```

3.  V rámci `Main()` metodu, přidejte následující kód. Tím se vytvoří instance `DiscoveryProxy` třídy.

    ```
    Uri probeEndpointAddress = new Uri("net.tcp://localhost:8001/Probe");
                Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

                // Host the DiscoveryProxy service
                ServiceHost proxyServiceHost = new ServiceHost(new DiscoveryProxyService());
    ```

4.  Dále přidejte následující kód k přidání koncového bodu zjišťování a koncový bod oznámení.

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

 Dokončili jste implementace proxy zjišťování. Pokračovat k [jak: Implementace zjistitelné služby, která se registruje pomocí Proxy zjišťování](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md).

## <a name="example"></a>Příklad
 Toto je úplný přehled kód použitý v tomto tématu.

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

## <a name="see-also"></a>Viz také:

- [Přehled zjišťování WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [Postupy: Implementace zjistitelné služby, která se registruje pomocí Proxy zjišťování](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)
- [Postupy: Implementace klientské aplikace používající zjišťování Proxy k vyhledání služby](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
- [Postupy: Test Proxy zjišťování](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)