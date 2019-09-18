---
title: Žádosti o data
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
ms.openlocfilehash: 1f367caf7656a83597b6262a5746686df15d33b4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047317"
---
# <a name="requesting-data"></a><span data-ttu-id="fc9f4-102">Žádosti o data</span><span class="sxs-lookup"><span data-stu-id="fc9f4-102">Requesting Data</span></span>
<span data-ttu-id="fc9f4-103">Vývoj aplikací, které běží v distribuovaném operačním prostředí dnešního Internetu, vyžaduje efektivní a snadno použitelné metody pro načítání dat z prostředků všech typů.</span><span class="sxs-lookup"><span data-stu-id="fc9f4-103">Developing applications that run in the distributed operating environment of today's Internet requires an efficient, easy-to-use method for retrieving data from resources of all types.</span></span> <span data-ttu-id="fc9f4-104">Připojitelné protokoly umožňují vyvíjet aplikace, které používají jedno rozhraní k načítání dat z více protokolů sítě Internet.</span><span class="sxs-lookup"><span data-stu-id="fc9f4-104">Pluggable protocols let you develop applications that use a single interface to retrieve data from multiple Internet protocols.</span></span>  
  
## <a name="uploading-and-downloading-data-from-an-internet-server"></a><span data-ttu-id="fc9f4-105">Nahrávání a stahování dat z internetového serveru</span><span class="sxs-lookup"><span data-stu-id="fc9f4-105">Uploading and Downloading Data from an Internet Server</span></span>  
 <span data-ttu-id="fc9f4-106">Pro jednoduché transakce <xref:System.Net.WebClient> požadavků a odpovědí poskytuje třída nejjednodušší způsob, jak nahrávat data nebo stahovat data z internetového serveru.</span><span class="sxs-lookup"><span data-stu-id="fc9f4-106">For simple request and response transactions, the <xref:System.Net.WebClient> class provides the easiest method for uploading data to or downloading data from an Internet server.</span></span> <span data-ttu-id="fc9f4-107">**Webový klient** poskytuje metody pro nahrávání a stahování souborů, odesílání a příjem datových proudů a posílání vyrovnávací paměti dat na server a příjem odpovědi.</span><span class="sxs-lookup"><span data-stu-id="fc9f4-107">**WebClient** provides methods for uploading and downloading files, sending and receiving streams, and sending a data buffer to the server and receiving a response.</span></span> <span data-ttu-id="fc9f4-108">**Webový klient** používá <xref:System.Net.WebRequest> třídy a <xref:System.Net.WebResponse> k tomu, aby provedl skutečná připojení k internetovému prostředku, takže jakýkoli registrovaný připojitelný protokol je k dispozici pro použití.</span><span class="sxs-lookup"><span data-stu-id="fc9f4-108">**WebClient** uses the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes to make the actual connections to the Internet resource, so any registered pluggable protocol is available for use.</span></span>  
  
 <span data-ttu-id="fc9f4-109">Klientské aplikace, které potřebují provádět složitější transakce, vyžadují data ze serverů pomocí třídy **WebRequest** a jejích potomků.</span><span class="sxs-lookup"><span data-stu-id="fc9f4-109">Client applications that need to make more complex transactions request data from servers using the **WebRequest** class and its descendants.</span></span> <span data-ttu-id="fc9f4-110">**WebRequest** zapouzdřuje podrobnosti o připojení k serveru, posílá požadavek a obdrží odpověď.</span><span class="sxs-lookup"><span data-stu-id="fc9f4-110">**WebRequest** encapsulates the details of connecting to the server, sending the request, and receiving the response.</span></span> <span data-ttu-id="fc9f4-111">**WebRequest** je abstraktní třída, která definuje sadu vlastností a metod, které jsou k dispozici pro všechny aplikace, které používají připojitelné protokoly.</span><span class="sxs-lookup"><span data-stu-id="fc9f4-111">**WebRequest** is an abstract class that defines a set of properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="fc9f4-112">Následníky **WebRequest**, například <xref:System.Net.HttpWebRequest>, implementují vlastnosti a metody definované **WebRequest** způsobem, který je konzistentní s podkladovým protokolem.</span><span class="sxs-lookup"><span data-stu-id="fc9f4-112">Descendants of **WebRequest**, such as <xref:System.Net.HttpWebRequest>, implement the properties and methods defined by **WebRequest** in a way that is consistent with the underlying protocol.</span></span>  
  
 <span data-ttu-id="fc9f4-113">Třída **WebRequest** vytvoří instance pro následníky **WebRequest** pomocí hodnoty identifikátoru URI předané jeho <xref:System.Net.WebRequest.Create%2A> metodě k určení konkrétní instance odvozené třídy, která se má vytvořit.</span><span class="sxs-lookup"><span data-stu-id="fc9f4-113">The **WebRequest** class creates protocol-specific instances of **WebRequest** descendants, using the value of the URI passed to its <xref:System.Net.WebRequest.Create%2A> method to determine the specific derived-class instance to create.</span></span> <span data-ttu-id="fc9f4-114">Aplikace označují, který člen **WebRequest** by měl být použit ke zpracování požadavku registrací konstruktoru následníka s <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> metodou.</span><span class="sxs-lookup"><span data-stu-id="fc9f4-114">Applications indicate which **WebRequest** descendant should be used to handle a request by registering the descendant's constructor with the <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="fc9f4-115">Požadavek se provede na prostředek v Internetu voláním <xref:System.Net.WebRequest.GetResponse%2A> metody na **WebRequest**.</span><span class="sxs-lookup"><span data-stu-id="fc9f4-115">A request is made to the Internet resource by calling the <xref:System.Net.WebRequest.GetResponse%2A> method on the **WebRequest**.</span></span> <span data-ttu-id="fc9f4-116">Metoda **GetResponse** sestaví požadavek specifický pro protokol z vlastností **WebRequest**, vytvoří připojení soketu TCP nebo UDP k serveru a odešle požadavek.</span><span class="sxs-lookup"><span data-stu-id="fc9f4-116">The **GetResponse** method constructs the protocol-specific request from the properties of the **WebRequest**, makes the TCP or UDP socket connection to the server, and sends the request.</span></span> <span data-ttu-id="fc9f4-117">V **případě požadavků,** které odesílají data na server, jako jsou <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> požadavky HTTP **post** nebo FTP, poskytuje metoda síťový datový proud, ve kterém se budou data odesílat.</span><span class="sxs-lookup"><span data-stu-id="fc9f4-117">For requests that send data to the server, such as HTTP **Post** or FTP **Put** requests, the <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> method provides a network stream in which to send the data.</span></span>  
  
 <span data-ttu-id="fc9f4-118">Metoda **GetResponse** vrací **WebResponse** specifickou pro protokol, který odpovídá **WebRequest.**</span><span class="sxs-lookup"><span data-stu-id="fc9f4-118">The **GetResponse** method returns a protocol-specific **WebResponse** that matches the **WebRequest.**</span></span>  
  
 <span data-ttu-id="fc9f4-119">Třída **WebResponse** je také abstraktní třída, která definuje vlastnosti a metody, které jsou k dispozici pro všechny aplikace, které používají připojitelná protokoly.</span><span class="sxs-lookup"><span data-stu-id="fc9f4-119">The **WebResponse** class is also an abstract class that defines properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="fc9f4-120">Následníky **WebResponse** implementují tyto vlastnosti a metody pro základní protokol.</span><span class="sxs-lookup"><span data-stu-id="fc9f4-120">**WebResponse** descendants implement these properties and methods for the underlying protocol.</span></span> <span data-ttu-id="fc9f4-121">Třída například implementuje třídu WebResponse pro protokol HTTP. <xref:System.Net.HttpWebResponse></span><span class="sxs-lookup"><span data-stu-id="fc9f4-121">The <xref:System.Net.HttpWebResponse> class, for example, implements the **WebResponse** class for HTTP.</span></span>  
  
 <span data-ttu-id="fc9f4-122">Data vrácená serverem se zobrazí aplikaci v datovém proudu vráceném <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metodou.</span><span class="sxs-lookup"><span data-stu-id="fc9f4-122">The data returned by the server is presented to the application in the stream returned by the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="fc9f4-123">Tento datový proud můžete použít jako kterýkoli jiný, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="fc9f4-123">You can use this stream like any other, as shown in the following example.</span></span>  
  
```csharp  
StreamReader sr =  
   new StreamReader(resp.GetResponseStream(), Encoding.ASCII);  
```  
  
```vb  
Dim sr As StreamReader  
sr = New StreamReader(resp.GetResponseStream(), Encoding.ASCII)  
```  
  
## <a name="see-also"></a><span data-ttu-id="fc9f4-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fc9f4-124">See also</span></span>

- [<span data-ttu-id="fc9f4-125">Síťové programování v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fc9f4-125">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="fc9f4-126">Postupy: Požádat o webovou stránku a načíst výsledky jako datový proud</span><span class="sxs-lookup"><span data-stu-id="fc9f4-126">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>](how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)
- [<span data-ttu-id="fc9f4-127">Postupy: Načtení WebResponse konkrétního protokolu, který odpovídá WebRequest</span><span class="sxs-lookup"><span data-stu-id="fc9f4-127">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>](how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)
