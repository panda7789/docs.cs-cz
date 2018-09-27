---
title: Správa připojení
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Internet, connections
- HTTP, classes for connecting
- requesting data from Internet, connections
- sending data, connections
- receiving data, connections
- ServicePoint class, about ServicePoint class
- response to Internet request, connections
- connections [.NET Framework], classes
- network resources, connections
- downloading Internet resources, connections
- ServicePointManager class, about ServicePointManager class
ms.assetid: 9b3d3de7-189f-4f7d-81ae-9c29c441aaaa
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 1e4eb6c88bfad132f9e974445adf9ae0d6531f57
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2018
ms.locfileid: "47399434"
---
# <a name="managing-connections"></a><span data-ttu-id="a7f77-102">Správa připojení</span><span class="sxs-lookup"><span data-stu-id="a7f77-102">Managing Connections</span></span>
<span data-ttu-id="a7f77-103">Aplikace, které používají protokol HTTP pro připojení k datovým prostředkům můžete použít rozhraní .NET Framework <xref:System.Net.ServicePoint> a <xref:System.Net.ServicePointManager> třídy ke správě připojení k Internetu a aby to pomohl ostatním dosažení optimálního škálování a výkon.</span><span class="sxs-lookup"><span data-stu-id="a7f77-103">Applications that use HTTP to connect to data resources can use the .NET Framework's <xref:System.Net.ServicePoint> and <xref:System.Net.ServicePointManager> classes to manage connections to the Internet and to help them achieve optimum scale and performance.</span></span>  
  
 <span data-ttu-id="a7f77-104">**ServicePoint** třída poskytuje aplikace s koncovým bodem, do které můžete připojit aplikaci pro přístup k internetovým prostředkům.</span><span class="sxs-lookup"><span data-stu-id="a7f77-104">The **ServicePoint** class provides an application with an endpoint to which the application can connect to access Internet resources.</span></span> <span data-ttu-id="a7f77-105">Každý **ServicePoint** informacemi, že pomáhá optimalizovat připojení pomocí internetového serveru při sdílení informací o optimalizaci mezi připojení ke zlepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="a7f77-105">Each **ServicePoint** contains information that helps optimize connections with an Internet server by sharing optimization information between connections to improve performance.</span></span>  
  
 <span data-ttu-id="a7f77-106">Každý **ServicePoint** je identifikován podle identifikátor URI (Uniform Resource) a jsou rozdělené do kategorií podle schéma identifikátor a fragmentům hostitele identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="a7f77-106">Each **ServicePoint** is identified by a Uniform Resource Identifier (URI) and is categorized according to the scheme identifier and host fragments of the URI.</span></span> <span data-ttu-id="a7f77-107">Například stejné **ServicePoint** instance by požadavky poskytovat identifikátory URI `http://www.contoso.com/index.htm` a `http://www.contoso.com/news.htm?date=today` protože mají stejný identifikátor schématu (http) a fragmentů hostitele (`www.contoso.com`).</span><span class="sxs-lookup"><span data-stu-id="a7f77-107">For example, the same **ServicePoint** instance would provide requests to the URIs `http://www.contoso.com/index.htm` and `http://www.contoso.com/news.htm?date=today` since they have the same scheme identifier (http) and host fragments (`www.contoso.com`).</span></span> <span data-ttu-id="a7f77-108">Pokud má aplikace již trvalé připojení k serveru `www.contoso.com`, použije toto připojení k načtení obou požadavků, takže není nutné vytvořit dvě připojení.</span><span class="sxs-lookup"><span data-stu-id="a7f77-108">If the application already has a persistent connection to the server `www.contoso.com`, it uses that connection to retrieve both requests, avoiding the need to create two connections.</span></span>  
  
 <span data-ttu-id="a7f77-109">**Třída ServicePointManager** je statická třída, která spravuje vytváření a ničení **ServicePoint** instancí.</span><span class="sxs-lookup"><span data-stu-id="a7f77-109">**ServicePointManager** is a static class that manages the creation and destruction of **ServicePoint** instances.</span></span> <span data-ttu-id="a7f77-110">**Třída ServicePointManager** vytvoří **ServicePoint** když aplikace požádá o prostředek Internet, který se nenachází v kolekci stávajících **ServicePoint** instance.</span><span class="sxs-lookup"><span data-stu-id="a7f77-110">The **ServicePointManager** creates a **ServicePoint** when the application requests an Internet resource that is not in the collection of existing **ServicePoint** instances.</span></span> <span data-ttu-id="a7f77-111">**ServicePoint** instancí jsou zničeny při překročení jejich maximální doba nečinnosti, nebo když se počet stávajících **ServicePoint** překračuje maximální počet instancí **ServicePoint**instancí aplikace.</span><span class="sxs-lookup"><span data-stu-id="a7f77-111">**ServicePoint** instances are destroyed when they have exceeded their maximum idle time or when the number of existing **ServicePoint** instances exceeds the maximum number of **ServicePoint** instances for the application.</span></span> <span data-ttu-id="a7f77-112">Můžete řídit, výchozí maximální doba nečinnosti a maximální počet **ServicePoint** instance tak, že nastavíte <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> a <xref:System.Net.ServicePointManager.MaxServicePoints%2A> vlastnosti **Třída ServicePointManager**.</span><span class="sxs-lookup"><span data-stu-id="a7f77-112">You can control both the default maximum idle time and the maximum number of **ServicePoint** instances by setting the <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> and <xref:System.Net.ServicePointManager.MaxServicePoints%2A> properties on the **ServicePointManager**.</span></span>  
  
 <span data-ttu-id="a7f77-113">Počet připojení mezi klientem a serverem, které může mít výrazný dopad na propustnost aplikace.</span><span class="sxs-lookup"><span data-stu-id="a7f77-113">The number of connections between a client and server can have a dramatic impact on application throughput.</span></span> <span data-ttu-id="a7f77-114">Ve výchozím nastavení aplikace s využitím <xref:System.Net.HttpWebRequest> třída používá maximálně dvě trvalé připojení k danému serveru, ale můžete nastavit maximální počet připojení na základě jednotlivých aplikací.</span><span class="sxs-lookup"><span data-stu-id="a7f77-114">By default, an application using the <xref:System.Net.HttpWebRequest> class uses a maximum of two persistent connections to a given server, but you can set the maximum number of connections on a per-application basis.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7f77-115">Specifikace protokolu HTTP/1.1 omezuje počet připojení z aplikace do dvou připojení na serveru.</span><span class="sxs-lookup"><span data-stu-id="a7f77-115">The HTTP/1.1 specification limits the number of connections from an application to two connections per server.</span></span>  
  
 <span data-ttu-id="a7f77-116">Optimální počet připojení, které závisí na skutečných podmínek, ve kterých je aplikace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="a7f77-116">The optimum number of connections depends on the actual conditions in which the application runs.</span></span> <span data-ttu-id="a7f77-117">Zvýšení počtu připojení aplikace k dispozici nemusí mít vliv na výkon aplikace.</span><span class="sxs-lookup"><span data-stu-id="a7f77-117">Increasing the number of connections available to the application may not affect application performance.</span></span> <span data-ttu-id="a7f77-118">Pokud chcete zjistit dopad další připojení, spuštění testů výkonu při různých počet připojení.</span><span class="sxs-lookup"><span data-stu-id="a7f77-118">To determine the impact of more connections, run performance tests while varying the number of connections.</span></span> <span data-ttu-id="a7f77-119">Můžete změnit počet připojení, které aplikace používá tak, že změníte statické <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> vlastnost **Třída ServicePointManager** třídy při inicializaci aplikace, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="a7f77-119">You can change the number of connections that an application uses by changing the static <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> property on the **ServicePointManager** class at application initialization, as shown in the following code sample.</span></span>  
  
```csharp  
// Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4;  
```  
  
```vb  
' Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4  
```  
  
 <span data-ttu-id="a7f77-120">Změna **ServicePointManager.DefaultConnectionLimit** vlastnost nemá vliv na dříve inicializován **ServicePoint** instancí.</span><span class="sxs-lookup"><span data-stu-id="a7f77-120">Changing the **ServicePointManager.DefaultConnectionLimit** property does not affect previously initialized **ServicePoint** instances.</span></span> <span data-ttu-id="a7f77-121">Následující kód ukazuje změnu limitu připojení na existující **ServicePoint** pro server `http://www.contoso.com` na hodnotu uloženou v `newLimit`.</span><span class="sxs-lookup"><span data-stu-id="a7f77-121">The following code demonstrates changing the connection limit on an existing **ServicePoint** for the server `http://www.contoso.com` to the value stored in `newLimit`.</span></span>  
  
```csharp  
Uri uri = new Uri("http://www.contoso.com/");  
ServicePoint sp = ServicePointManager.FindServicePoint(uri);  
sp.ConnectionLimit = newLimit;  
```  
  
```vb  
Dim uri As New Uri("http://www.contoso.com/")  
Dim sp As ServicePoint = ServicePointManager.FindServicePoint(uri)  
sp.ConnectionLimit = newLimit  
```  
  
## <a name="see-also"></a><span data-ttu-id="a7f77-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="a7f77-122">See Also</span></span>  
 [<span data-ttu-id="a7f77-123">Seskupení připojení</span><span class="sxs-lookup"><span data-stu-id="a7f77-123">Connection Grouping</span></span>](../../../docs/framework/network-programming/connection-grouping.md)  
 [<span data-ttu-id="a7f77-124">Použití aplikačních protokolů</span><span class="sxs-lookup"><span data-stu-id="a7f77-124">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
