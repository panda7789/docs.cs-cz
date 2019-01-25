---
title: Požadavek na Data
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sending data
- WebRequest class, sending and receiving data
- requesting data from Internet, about requesting data
- WebClient class, sending and receiving data
- network, requesting data
- receiving data
- sending data, about sending data
- response to Internet request, about responding to Internet requests
- data requests
- receiving data, about receiving data
- Internet, requesting data
ms.assetid: df6f1e1d-6f2a-45dd-8141-4a85c3dafe1d
ms.openlocfilehash: 8e469e5480bbec8a04dbf280d4698acd5b328d72
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54678483"
---
# <a name="requesting-data"></a><span data-ttu-id="c7a43-102">Požadavek na Data</span><span class="sxs-lookup"><span data-stu-id="c7a43-102">Requesting Data</span></span>
<span data-ttu-id="c7a43-103">Vývoj aplikací, které běží v distribuované provozní prostředí dnešní Internet vyžaduje metodu efektivní a snadno použitelné pro načítání dat ze všech typů prostředků.</span><span class="sxs-lookup"><span data-stu-id="c7a43-103">Developing applications that run in the distributed operating environment of today's Internet requires an efficient, easy-to-use method for retrieving data from resources of all types.</span></span> <span data-ttu-id="c7a43-104">Připojitelných protokolů umožňují vyvíjet aplikace, které používají jednotné rozhraní pro načtení dat z více protokolů sítě Internet.</span><span class="sxs-lookup"><span data-stu-id="c7a43-104">Pluggable protocols let you develop applications that use a single interface to retrieve data from multiple Internet protocols.</span></span>  
  
## <a name="uploading-and-downloading-data-from-an-internet-server"></a><span data-ttu-id="c7a43-105">Nahrávání a stahování dat z internetového serveru</span><span class="sxs-lookup"><span data-stu-id="c7a43-105">Uploading and Downloading Data from an Internet Server</span></span>  
 <span data-ttu-id="c7a43-106">Pro jednoduché žádosti a odpovědi transakce <xref:System.Net.WebClient> třída poskytuje nejjednodušší metodu pro nahrávání dat do nebo stahování dat z internetového serveru.</span><span class="sxs-lookup"><span data-stu-id="c7a43-106">For simple request and response transactions, the <xref:System.Net.WebClient> class provides the easiest method for uploading data to or downloading data from an Internet server.</span></span> <span data-ttu-id="c7a43-107">**Webový klient** poskytuje metody pro nahrávání a stahování souborů, příjem a odesílání datových proudů, vyrovnávací paměť dat na server a přijímání odpovědí.</span><span class="sxs-lookup"><span data-stu-id="c7a43-107">**WebClient** provides methods for uploading and downloading files, sending and receiving streams, and sending a data buffer to the server and receiving a response.</span></span> <span data-ttu-id="c7a43-108">**Webový klient** používá <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> třídy pro skutečné připojení k internetového zdroji, tak žádné registrována připojitelných protokolů je k dispozici pro použití.</span><span class="sxs-lookup"><span data-stu-id="c7a43-108">**WebClient** uses the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes to make the actual connections to the Internet resource, so any registered pluggable protocol is available for use.</span></span>  
  
 <span data-ttu-id="c7a43-109">Klientské aplikace, které je potřeba provést složitější data požadavku transakcí ze serverů pomocí **WebRequest** třídy a jejích potomků.</span><span class="sxs-lookup"><span data-stu-id="c7a43-109">Client applications that need to make more complex transactions request data from servers using the **WebRequest** class and its descendants.</span></span> <span data-ttu-id="c7a43-110">**WebRequest** zapouzdřuje informace připojování k serveru, požadavek odesílat a přijímat odpovědi.</span><span class="sxs-lookup"><span data-stu-id="c7a43-110">**WebRequest** encapsulates the details of connecting to the server, sending the request, and receiving the response.</span></span> <span data-ttu-id="c7a43-111">**WebRequest** je abstraktní třída, která definuje sadu vlastností a metod, které jsou k dispozici pro všechny aplikace, které pomocí připojitelných protokolů.</span><span class="sxs-lookup"><span data-stu-id="c7a43-111">**WebRequest** is an abstract class that defines a set of properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="c7a43-112">Následníky **WebRequest**, jako například <xref:System.Net.HttpWebRequest>, implementovat vlastnosti a metody definované **WebRequest** způsobem, který je konzistentní se základním protokolu.</span><span class="sxs-lookup"><span data-stu-id="c7a43-112">Descendants of **WebRequest**, such as <xref:System.Net.HttpWebRequest>, implement the properties and methods defined by **WebRequest** in a way that is consistent with the underlying protocol.</span></span>  
  
 <span data-ttu-id="c7a43-113">**WebRequest** třídy vytvoří konkrétní instance **WebRequest** následníky, hodnotu identifikátoru URI s použitím předaného do jeho <xref:System.Net.WebRequest.Create%2A> metodou ke zjištění konkrétních odvozených tříd instance má vytvořit.</span><span class="sxs-lookup"><span data-stu-id="c7a43-113">The **WebRequest** class creates protocol-specific instances of **WebRequest** descendants, using the value of the URI passed to its <xref:System.Net.WebRequest.Create%2A> method to determine the specific derived-class instance to create.</span></span> <span data-ttu-id="c7a43-114">Vyberte aplikace, které **WebRequest** potomkem by měla sloužit ke zpracování požadavku tak, že zaregistrujete potomka konstruktor s <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="c7a43-114">Applications indicate which **WebRequest** descendant should be used to handle a request by registering the descendant's constructor with the <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="c7a43-115">Vytvoří se požadavek k internetového zdroji voláním <xref:System.Net.WebRequest.GetResponse%2A> metodu **WebRequest**.</span><span class="sxs-lookup"><span data-stu-id="c7a43-115">A request is made to the Internet resource by calling the <xref:System.Net.WebRequest.GetResponse%2A> method on the **WebRequest**.</span></span> <span data-ttu-id="c7a43-116">**GetResponse** metoda vytvoří konkrétní žádosti z vlastností **WebRequest**, vytvoří protokol TCP nebo UDP soketu připojení k serveru a odešle žádost.</span><span class="sxs-lookup"><span data-stu-id="c7a43-116">The **GetResponse** method constructs the protocol-specific request from the properties of the **WebRequest**, makes the TCP or UDP socket connection to the server, and sends the request.</span></span> <span data-ttu-id="c7a43-117">Pro žádosti, které odesílají data na serveru, např. HTTP **příspěvek** nebo FTP **umístit** požadavků, <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> metoda poskytuje datové proudy sítě ve kterých se mají odeslat data.</span><span class="sxs-lookup"><span data-stu-id="c7a43-117">For requests that send data to the server, such as HTTP **Post** or FTP **Put** requests, the <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> method provides a network stream in which to send the data.</span></span>  
  
 <span data-ttu-id="c7a43-118">**GetResponse** metoda vrátí hodnotu konkrétního protokol **WebResponse** , který odpovídá **WebRequest.**</span><span class="sxs-lookup"><span data-stu-id="c7a43-118">The **GetResponse** method returns a protocol-specific **WebResponse** that matches the **WebRequest.**</span></span>  
  
 <span data-ttu-id="c7a43-119">**WebResponse** třídy je také abstraktní třída, která definuje vlastnosti a metody, které jsou k dispozici pro všechny aplikace, které pomocí připojitelných protokolů.</span><span class="sxs-lookup"><span data-stu-id="c7a43-119">The **WebResponse** class is also an abstract class that defines properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="c7a43-120">**WebResponse** následníky implementovat tyto vlastnosti a metody pro základní protokol.</span><span class="sxs-lookup"><span data-stu-id="c7a43-120">**WebResponse** descendants implement these properties and methods for the underlying protocol.</span></span> <span data-ttu-id="c7a43-121"><xref:System.Net.HttpWebResponse> , Například implementuje třída **WebResponse** třídy pro protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="c7a43-121">The <xref:System.Net.HttpWebResponse> class, for example, implements the **WebResponse** class for HTTP.</span></span>  
  
 <span data-ttu-id="c7a43-122">Data vrácená serverem se zobrazují na aplikaci v stream vrácený poskytovatelem <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="c7a43-122">The data returned by the server is presented to the application in the stream returned by the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c7a43-123">Tento datový proud stejně jako jakýkoli jiný, můžete použít, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c7a43-123">You can use this stream like any other, as shown in the following example.</span></span>  
  
```csharp  
StreamReader sr =  
   new StreamReader(resp.GetResponseStream(), Encoding.ASCII);  
```  
  
```vb  
Dim sr As StreamReader  
sr = New StreamReader(resp.GetResponseStream(), Encoding.ASCII)  
```  
  
## <a name="see-also"></a><span data-ttu-id="c7a43-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c7a43-124">See also</span></span>
- [<span data-ttu-id="c7a43-125">Síťové programování v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c7a43-125">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)
- [<span data-ttu-id="c7a43-126">Postupy: Vyžádání webové stránky a načtení výsledků jako Stream</span><span class="sxs-lookup"><span data-stu-id="c7a43-126">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>](../../../docs/framework/network-programming/how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)
- [<span data-ttu-id="c7a43-127">Postupy: Načíst WebResponse specifické pro protokol, který odpovídá položce WebRequest</span><span class="sxs-lookup"><span data-stu-id="c7a43-127">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>](../../../docs/framework/network-programming/how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)
