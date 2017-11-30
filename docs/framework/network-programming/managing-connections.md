---
title: "Správa připojení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f3a8900aca9ebfa14fbf49d4d3634bc486793c0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="managing-connections"></a><span data-ttu-id="c5929-102">Správa připojení</span><span class="sxs-lookup"><span data-stu-id="c5929-102">Managing Connections</span></span>
<span data-ttu-id="c5929-103">Aplikace, které používají protokol HTTP pro připojení k prostředkům dat můžete použít rozhraní .NET Framework <xref:System.Net.ServicePoint> a <xref:System.Net.ServicePointManager> třídy ke správě připojení k Internetu a pomáhá jim dosáhnout optimálního škálování a výkon.</span><span class="sxs-lookup"><span data-stu-id="c5929-103">Applications that use HTTP to connect to data resources can use the .NET Framework's <xref:System.Net.ServicePoint> and <xref:System.Net.ServicePointManager> classes to manage connections to the Internet and to help them achieve optimum scale and performance.</span></span>  
  
 <span data-ttu-id="c5929-104">**Servisním místem** třída poskytuje aplikace s koncovým bodem, který lze aplikace připojí k přístup k internetovým prostředkům.</span><span class="sxs-lookup"><span data-stu-id="c5929-104">The **ServicePoint** class provides an application with an endpoint to which the application can connect to access Internet resources.</span></span> <span data-ttu-id="c5929-105">Každý **servisním místem** obsahuje informace, že pomáhá optimalizovat připojení pomocí internetového serveru pomocí sdílení informací optimalizace mezi připojení ke zlepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="c5929-105">Each **ServicePoint** contains information that helps optimize connections with an Internet server by sharing optimization information between connections to improve performance.</span></span>  
  
 <span data-ttu-id="c5929-106">Každý **servisním místem** je identifikován pomocí identifikátor URI (Uniform Resource) a je zařazený do kategorie podle fragmenty identifikátor a hostitele schéma identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="c5929-106">Each **ServicePoint** is identified by a Uniform Resource Identifier (URI) and is categorized according to the scheme identifier and host fragments of the URI.</span></span> <span data-ttu-id="c5929-107">Například stejné **servisním místem** instance by poskytují žádosti na identifikátory URI http://www.contoso.com/index.htm a http://www.contoso.com/news.htm?date=today, protože mají stejný identifikátor schématu (http) a hostitele fragmenty (www.contoso.com).</span><span class="sxs-lookup"><span data-stu-id="c5929-107">For example, the same **ServicePoint** instance would provide requests to the URIs http://www.contoso.com/index.htm and http://www.contoso.com/news.htm?date=today since they have the same scheme identifier (http) and host fragments (www.contoso.com).</span></span> <span data-ttu-id="c5929-108">Pokud aplikace už má trvalé připojení k serveru www.contoso.com, používá toto připojení k načtení oba požadavky, takže není nutné vytvořit dvě připojení.</span><span class="sxs-lookup"><span data-stu-id="c5929-108">If the application already has a persistent connection to the server www.contoso.com, it uses that connection to retrieve both requests, avoiding the need to create two connections.</span></span>  
  
 <span data-ttu-id="c5929-109">**ServicePointManager –** je statická třída, která spravuje vytváření a zničení **servisním místem** instance.</span><span class="sxs-lookup"><span data-stu-id="c5929-109">**ServicePointManager** is a static class that manages the creation and destruction of **ServicePoint** instances.</span></span> <span data-ttu-id="c5929-110">**ServicePointManager –** vytvoří **servisním místem** při aplikace požádá o prostředek Internet, který není v kolekci existující **servisním místem** instance.</span><span class="sxs-lookup"><span data-stu-id="c5929-110">The **ServicePointManager** creates a **ServicePoint** when the application requests an Internet resource that is not in the collection of existing **ServicePoint** instances.</span></span> <span data-ttu-id="c5929-111">**Servisním místem** instance jsou zničen čas překročení jejich maximální doby nečinnosti nebo pokud je to číslo existující **servisním místem** překračuje maximální počet instancí **servisním místem**instancí aplikace.</span><span class="sxs-lookup"><span data-stu-id="c5929-111">**ServicePoint** instances are destroyed when they have exceeded their maximum idle time or when the number of existing **ServicePoint** instances exceeds the maximum number of **ServicePoint** instances for the application.</span></span> <span data-ttu-id="c5929-112">Můžete ovládat maximální dobu výchozí nečinnosti a maximální počet **servisním místem** instance podle nastavení <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> a <xref:System.Net.ServicePointManager.MaxServicePoints%2A> vlastnosti **ServicePointManager –**.</span><span class="sxs-lookup"><span data-stu-id="c5929-112">You can control both the default maximum idle time and the maximum number of **ServicePoint** instances by setting the <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> and <xref:System.Net.ServicePointManager.MaxServicePoints%2A> properties on the **ServicePointManager**.</span></span>  
  
 <span data-ttu-id="c5929-113">Počet připojení mezi klientem a serverem může mít výrazný dopad na propustnost aplikace.</span><span class="sxs-lookup"><span data-stu-id="c5929-113">The number of connections between a client and server can have a dramatic impact on application throughput.</span></span> <span data-ttu-id="c5929-114">Ve výchozím nastavení aplikace pomocí <xref:System.Net.HttpWebRequest> třída používá maximálně dvě trvalé připojení k danému serveru, ale můžete nastavit maximální počet připojení na základě jednotlivých aplikací.</span><span class="sxs-lookup"><span data-stu-id="c5929-114">By default, an application using the <xref:System.Net.HttpWebRequest> class uses a maximum of two persistent connections to a given server, but you can set the maximum number of connections on a per-application basis.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5929-115">Specifikace protokolu HTTP/1.1 omezí počet připojení z aplikace do dvě připojení na server.</span><span class="sxs-lookup"><span data-stu-id="c5929-115">The HTTP/1.1 specification limits the number of connections from an application to two connections per server.</span></span>  
  
 <span data-ttu-id="c5929-116">Optimální počet připojení závisí na skutečné podmínky, ve kterých je aplikace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="c5929-116">The optimum number of connections depends on the actual conditions in which the application runs.</span></span> <span data-ttu-id="c5929-117">Zvýšením počtu připojení aplikace k dispozici nemusí ovlivnit výkon aplikace.</span><span class="sxs-lookup"><span data-stu-id="c5929-117">Increasing the number of connections available to the application may not affect application performance.</span></span> <span data-ttu-id="c5929-118">Pokud chcete zjistit dopad více připojení, spusťte testy výkonu a budeme obměňovat počet připojení.</span><span class="sxs-lookup"><span data-stu-id="c5929-118">To determine the impact of more connections, run performance tests while varying the number of connections.</span></span> <span data-ttu-id="c5929-119">Můžete změnit počet připojení, které aplikace používá změnou statických <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> vlastnost **ServicePointManager –** třídy v inicializace aplikací, jak znázorňuje následující ukázka kódu.</span><span class="sxs-lookup"><span data-stu-id="c5929-119">You can change the number of connections that an application uses by changing the static <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> property on the **ServicePointManager** class at application initialization, as shown in the following code sample.</span></span>  
  
```csharp  
// Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4;  
```  
  
```vb  
' Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4  
```  
  
 <span data-ttu-id="c5929-120">Změna **ServicePointManager.DefaultConnectionLimit** vlastnost nemá vliv na dříve inicializovaného **servisním místem** instance.</span><span class="sxs-lookup"><span data-stu-id="c5929-120">Changing the **ServicePointManager.DefaultConnectionLimit** property does not affect previously initialized **ServicePoint** instances.</span></span> <span data-ttu-id="c5929-121">Následující kód ukazuje, změna limitu připojení na existujícím **servisním místem** pro server http://www.contoso.com k s hodnotou uloženou v `newLimit`.</span><span class="sxs-lookup"><span data-stu-id="c5929-121">The following code demonstrates changing the connection limit on an existing **ServicePoint** for the server http://www.contoso.com to the value stored in `newLimit`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c5929-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="c5929-122">See Also</span></span>  
 [<span data-ttu-id="c5929-123">Seskupení připojení</span><span class="sxs-lookup"><span data-stu-id="c5929-123">Connection Grouping</span></span>](../../../docs/framework/network-programming/connection-grouping.md)  
 [<span data-ttu-id="c5929-124">Pomocí protokolů aplikací</span><span class="sxs-lookup"><span data-stu-id="c5929-124">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
