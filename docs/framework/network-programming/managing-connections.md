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
ms.openlocfilehash: 11c17c6893800fce8bbff8f49b3a207c161bcdfa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047637"
---
# <a name="managing-connections"></a><span data-ttu-id="2ce2e-102">Správa připojení</span><span class="sxs-lookup"><span data-stu-id="2ce2e-102">Managing Connections</span></span>
<span data-ttu-id="2ce2e-103">Aplikace, které používají protokol HTTP k připojení k <xref:System.Net.ServicePoint> datovým prostředkům, mohou ke správě připojení k Internetu pomocí <xref:System.Net.ServicePointManager> rozhraní .NET Framework a tříd y a pomáhají jim dosáhnout optimálního rozsahu a výkonu.</span><span class="sxs-lookup"><span data-stu-id="2ce2e-103">Applications that use HTTP to connect to data resources can use the .NET Framework's <xref:System.Net.ServicePoint> and <xref:System.Net.ServicePointManager> classes to manage connections to the Internet and to help them achieve optimum scale and performance.</span></span>  
  
 <span data-ttu-id="2ce2e-104">Třída **ServicePoint** poskytuje aplikaci koncový bod, ke kterému se aplikace může připojit k přístupu k internetovým prostředkům.</span><span class="sxs-lookup"><span data-stu-id="2ce2e-104">The **ServicePoint** class provides an application with an endpoint to which the application can connect to access Internet resources.</span></span> <span data-ttu-id="2ce2e-105">Každý **ServicePoint** obsahuje informace, které pomáhají optimalizovat připojení s internetovým serverem sdílením informací o optimalizaci mezi připojeními ke zlepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="2ce2e-105">Each **ServicePoint** contains information that helps optimize connections with an Internet server by sharing optimization information between connections to improve performance.</span></span>  
  
 <span data-ttu-id="2ce2e-106">Každý **ServicePoint** je identifikován identifikátorem URI (Uniform Resource Identifier) a je rozdělen do kategorií podle identifikátoru schématu a fragmentů hostitele identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="2ce2e-106">Each **ServicePoint** is identified by a Uniform Resource Identifier (URI) and is categorized according to the scheme identifier and host fragments of the URI.</span></span> <span data-ttu-id="2ce2e-107">Například stejná instance **ServicePoint** by poskytovala `http://www.contoso.com/index.htm` požadavky `http://www.contoso.com/news.htm?date=today` na identifikátory URI a protože mají stejný`www.contoso.com`identifikátor schématu (http) a fragmenty hostitele ( ).</span><span class="sxs-lookup"><span data-stu-id="2ce2e-107">For example, the same **ServicePoint** instance would provide requests to the URIs `http://www.contoso.com/index.htm` and `http://www.contoso.com/news.htm?date=today` since they have the same scheme identifier (http) and host fragments (`www.contoso.com`).</span></span> <span data-ttu-id="2ce2e-108">Pokud aplikace již má trvalé připojení `www.contoso.com`k serveru , používá toto připojení k načtení obou požadavků, aby se zabránilo nutnosti vytvořit dvě připojení.</span><span class="sxs-lookup"><span data-stu-id="2ce2e-108">If the application already has a persistent connection to the server `www.contoso.com`, it uses that connection to retrieve both requests, avoiding the need to create two connections.</span></span>  
  
 <span data-ttu-id="2ce2e-109">**ServicePointManager** je statická třída, která spravuje vytváření a ničení instancí **ServicePoint.**</span><span class="sxs-lookup"><span data-stu-id="2ce2e-109">**ServicePointManager** is a static class that manages the creation and destruction of **ServicePoint** instances.</span></span> <span data-ttu-id="2ce2e-110">**ServicePointManager** vytvoří **ServicePoint,** když aplikace požaduje internetový prostředek, který není v kolekci existujících instancí **ServicePoint.**</span><span class="sxs-lookup"><span data-stu-id="2ce2e-110">The **ServicePointManager** creates a **ServicePoint** when the application requests an Internet resource that is not in the collection of existing **ServicePoint** instances.</span></span> <span data-ttu-id="2ce2e-111">**Instance ServicePoint** jsou zničeny, pokud překročily maximální dobu nečinnosti nebo pokud počet existujících instancí **ServicePoint** překročí maximální počet instancí **ServicePoint** pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2ce2e-111">**ServicePoint** instances are destroyed when they have exceeded their maximum idle time or when the number of existing **ServicePoint** instances exceeds the maximum number of **ServicePoint** instances for the application.</span></span> <span data-ttu-id="2ce2e-112">Můžete řídit výchozí maximální dobu nečinnosti a maximální počet instancí <xref:System.Net.ServicePointManager.MaxServicePoints%2A> **ServicePoint** nastavením <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> vlastnosti a na **ServicePointManager**.</span><span class="sxs-lookup"><span data-stu-id="2ce2e-112">You can control both the default maximum idle time and the maximum number of **ServicePoint** instances by setting the <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> and <xref:System.Net.ServicePointManager.MaxServicePoints%2A> properties on the **ServicePointManager**.</span></span>  
  
 <span data-ttu-id="2ce2e-113">Počet připojení mezi klientem a serverem může mít dramatický dopad na propustnost aplikace.</span><span class="sxs-lookup"><span data-stu-id="2ce2e-113">The number of connections between a client and server can have a dramatic impact on application throughput.</span></span> <span data-ttu-id="2ce2e-114">Ve výchozím nastavení aplikace <xref:System.Net.HttpWebRequest> používající třídu používá maximálně dvě trvalá připojení k danému serveru, ale můžete nastavit maximální počet připojení pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2ce2e-114">By default, an application using the <xref:System.Net.HttpWebRequest> class uses a maximum of two persistent connections to a given server, but you can set the maximum number of connections on a per-application basis.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2ce2e-115">Specifikace HTTP/1.1 omezuje počet připojení z aplikace na dvě připojení na server.</span><span class="sxs-lookup"><span data-stu-id="2ce2e-115">The HTTP/1.1 specification limits the number of connections from an application to two connections per server.</span></span>  
  
 <span data-ttu-id="2ce2e-116">Optimální počet připojení závisí na skutečných podmínkách, ve kterých je aplikace spuštěna.</span><span class="sxs-lookup"><span data-stu-id="2ce2e-116">The optimum number of connections depends on the actual conditions in which the application runs.</span></span> <span data-ttu-id="2ce2e-117">Zvýšení počtu připojení, která jsou k dispozici pro aplikaci, nemusí mít vliv na výkon aplikace.</span><span class="sxs-lookup"><span data-stu-id="2ce2e-117">Increasing the number of connections available to the application may not affect application performance.</span></span> <span data-ttu-id="2ce2e-118">Chcete-li zjistit dopad více připojení, spusťte testy výkonu při směšení počtu připojení.</span><span class="sxs-lookup"><span data-stu-id="2ce2e-118">To determine the impact of more connections, run performance tests while varying the number of connections.</span></span> <span data-ttu-id="2ce2e-119">Počet připojení, která aplikace používá, můžete změnit <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> statickou vlastnost ve třídě **ServicePointManager** při inicializaci aplikace, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="2ce2e-119">You can change the number of connections that an application uses by changing the static <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> property on the **ServicePointManager** class at application initialization, as shown in the following code sample.</span></span>  
  
```csharp  
// Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4;  
```  
  
```vb  
' Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4  
```  
  
 <span data-ttu-id="2ce2e-120">Změna vlastnosti **ServicePointManager.DefaultConnectionLimit** nemá vliv na dříve inicializované instance **Služby ServicePoint.**</span><span class="sxs-lookup"><span data-stu-id="2ce2e-120">Changing the **ServicePointManager.DefaultConnectionLimit** property does not affect previously initialized **ServicePoint** instances.</span></span> <span data-ttu-id="2ce2e-121">Následující kód ukazuje změnu limitu připojení na existující `http://www.contoso.com` **ServicePoint** pro `newLimit`server na hodnotu uloženou v aplikaci .</span><span class="sxs-lookup"><span data-stu-id="2ce2e-121">The following code demonstrates changing the connection limit on an existing **ServicePoint** for the server `http://www.contoso.com` to the value stored in `newLimit`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2ce2e-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="2ce2e-122">See also</span></span>

- [<span data-ttu-id="2ce2e-123">Seskupení připojení</span><span class="sxs-lookup"><span data-stu-id="2ce2e-123">Connection Grouping</span></span>](connection-grouping.md)
- [<span data-ttu-id="2ce2e-124">Použití aplikačních protokolů</span><span class="sxs-lookup"><span data-stu-id="2ce2e-124">Using Application Protocols</span></span>](using-application-protocols.md)
