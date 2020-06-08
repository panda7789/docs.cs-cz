---
title: Žádosti o data
description: Naučte se, jak připojitelné protokoly umožňují vyvíjet aplikace, které používají jedno rozhraní k načítání dat z více protokolů.
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
ms.openlocfilehash: 19350d685a81d56657ca0a117d61b50ae24fab6a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502181"
---
# <a name="requesting-data"></a><span data-ttu-id="6cde7-103">Žádosti o data</span><span class="sxs-lookup"><span data-stu-id="6cde7-103">Requesting Data</span></span>
<span data-ttu-id="6cde7-104">Vývoj aplikací, které běží v distribuovaném operačním prostředí dnešního Internetu, vyžaduje efektivní a snadno použitelné metody pro načítání dat z prostředků všech typů.</span><span class="sxs-lookup"><span data-stu-id="6cde7-104">Developing applications that run in the distributed operating environment of today's Internet requires an efficient, easy-to-use method for retrieving data from resources of all types.</span></span> <span data-ttu-id="6cde7-105">Připojitelné protokoly umožňují vyvíjet aplikace, které používají jedno rozhraní k načítání dat z více protokolů sítě Internet.</span><span class="sxs-lookup"><span data-stu-id="6cde7-105">Pluggable protocols let you develop applications that use a single interface to retrieve data from multiple Internet protocols.</span></span>  
  
## <a name="uploading-and-downloading-data-from-an-internet-server"></a><span data-ttu-id="6cde7-106">Nahrávání a stahování dat z internetového serveru</span><span class="sxs-lookup"><span data-stu-id="6cde7-106">Uploading and Downloading Data from an Internet Server</span></span>  
 <span data-ttu-id="6cde7-107">Pro jednoduché transakce požadavků a odpovědí <xref:System.Net.WebClient> poskytuje třída nejjednodušší způsob, jak nahrávat data nebo stahovat data z internetového serveru.</span><span class="sxs-lookup"><span data-stu-id="6cde7-107">For simple request and response transactions, the <xref:System.Net.WebClient> class provides the easiest method for uploading data to or downloading data from an Internet server.</span></span> <span data-ttu-id="6cde7-108">**Webový klient** poskytuje metody pro nahrávání a stahování souborů, odesílání a příjem datových proudů a posílání vyrovnávací paměti dat na server a příjem odpovědi.</span><span class="sxs-lookup"><span data-stu-id="6cde7-108">**WebClient** provides methods for uploading and downloading files, sending and receiving streams, and sending a data buffer to the server and receiving a response.</span></span> <span data-ttu-id="6cde7-109">**Webový klient** používá <xref:System.Net.WebRequest> třídy a <xref:System.Net.WebResponse> k tomu, aby provedl skutečná připojení k internetovému prostředku, takže jakýkoli registrovaný připojitelný protokol je k dispozici pro použití.</span><span class="sxs-lookup"><span data-stu-id="6cde7-109">**WebClient** uses the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes to make the actual connections to the Internet resource, so any registered pluggable protocol is available for use.</span></span>  
  
 <span data-ttu-id="6cde7-110">Klientské aplikace, které potřebují provádět složitější transakce, vyžadují data ze serverů pomocí třídy **WebRequest** a jejích potomků.</span><span class="sxs-lookup"><span data-stu-id="6cde7-110">Client applications that need to make more complex transactions request data from servers using the **WebRequest** class and its descendants.</span></span> <span data-ttu-id="6cde7-111">**WebRequest** zapouzdřuje podrobnosti o připojení k serveru, posílá požadavek a obdrží odpověď.</span><span class="sxs-lookup"><span data-stu-id="6cde7-111">**WebRequest** encapsulates the details of connecting to the server, sending the request, and receiving the response.</span></span> <span data-ttu-id="6cde7-112">**WebRequest** je abstraktní třída, která definuje sadu vlastností a metod, které jsou k dispozici pro všechny aplikace, které používají připojitelné protokoly.</span><span class="sxs-lookup"><span data-stu-id="6cde7-112">**WebRequest** is an abstract class that defines a set of properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="6cde7-113">Následníky **WebRequest**, například <xref:System.Net.HttpWebRequest> , implementují vlastnosti a metody definované **WebRequest** způsobem, který je konzistentní s podkladovým protokolem.</span><span class="sxs-lookup"><span data-stu-id="6cde7-113">Descendants of **WebRequest**, such as <xref:System.Net.HttpWebRequest>, implement the properties and methods defined by **WebRequest** in a way that is consistent with the underlying protocol.</span></span>  
  
 <span data-ttu-id="6cde7-114">Třída **WebRequest** vytvoří instance pro následníky **WebRequest** pomocí hodnoty identifikátoru URI předané jeho <xref:System.Net.WebRequest.Create%2A> metodě k určení konkrétní instance odvozené třídy, která se má vytvořit.</span><span class="sxs-lookup"><span data-stu-id="6cde7-114">The **WebRequest** class creates protocol-specific instances of **WebRequest** descendants, using the value of the URI passed to its <xref:System.Net.WebRequest.Create%2A> method to determine the specific derived-class instance to create.</span></span> <span data-ttu-id="6cde7-115">Aplikace označují, který člen **WebRequest** by měl být použit ke zpracování požadavku registrací konstruktoru následníka s <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> metodou.</span><span class="sxs-lookup"><span data-stu-id="6cde7-115">Applications indicate which **WebRequest** descendant should be used to handle a request by registering the descendant's constructor with the <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="6cde7-116">Požadavek se provede na prostředek v Internetu voláním <xref:System.Net.WebRequest.GetResponse%2A> metody na **WebRequest**.</span><span class="sxs-lookup"><span data-stu-id="6cde7-116">A request is made to the Internet resource by calling the <xref:System.Net.WebRequest.GetResponse%2A> method on the **WebRequest**.</span></span> <span data-ttu-id="6cde7-117">Metoda **GetResponse** sestaví požadavek specifický pro protokol z vlastností **WebRequest**, vytvoří připojení soketu TCP nebo UDP k serveru a odešle požadavek.</span><span class="sxs-lookup"><span data-stu-id="6cde7-117">The **GetResponse** method constructs the protocol-specific request from the properties of the **WebRequest**, makes the TCP or UDP socket connection to the server, and sends the request.</span></span> <span data-ttu-id="6cde7-118">V případě požadavků, které odesílají data na server, jako jsou **Post** požadavky HTTP Post **nebo FTP,** <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> poskytuje metoda síťový datový proud, ve kterém se budou data odesílat.</span><span class="sxs-lookup"><span data-stu-id="6cde7-118">For requests that send data to the server, such as HTTP **Post** or FTP **Put** requests, the <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> method provides a network stream in which to send the data.</span></span>  
  
 <span data-ttu-id="6cde7-119">Metoda **GetResponse** vrací **WebResponse** specifickou pro protokol, který odpovídá **WebRequest.**</span><span class="sxs-lookup"><span data-stu-id="6cde7-119">The **GetResponse** method returns a protocol-specific **WebResponse** that matches the **WebRequest.**</span></span>  
  
 <span data-ttu-id="6cde7-120">Třída **WebResponse** je také abstraktní třída, která definuje vlastnosti a metody, které jsou k dispozici pro všechny aplikace, které používají připojitelná protokoly.</span><span class="sxs-lookup"><span data-stu-id="6cde7-120">The **WebResponse** class is also an abstract class that defines properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="6cde7-121">Následníky **WebResponse** implementují tyto vlastnosti a metody pro základní protokol.</span><span class="sxs-lookup"><span data-stu-id="6cde7-121">**WebResponse** descendants implement these properties and methods for the underlying protocol.</span></span> <span data-ttu-id="6cde7-122"><xref:System.Net.HttpWebResponse>Třída například implementuje třídu **WebResponse** pro protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="6cde7-122">The <xref:System.Net.HttpWebResponse> class, for example, implements the **WebResponse** class for HTTP.</span></span>  
  
 <span data-ttu-id="6cde7-123">Data vrácená serverem se zobrazí aplikaci v datovém proudu vráceném <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metodou.</span><span class="sxs-lookup"><span data-stu-id="6cde7-123">The data returned by the server is presented to the application in the stream returned by the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="6cde7-124">Tento datový proud můžete použít jako kterýkoli jiný, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6cde7-124">You can use this stream like any other, as shown in the following example.</span></span>  
  
```csharp  
StreamReader sr =  
   new StreamReader(resp.GetResponseStream(), Encoding.ASCII);  
```  
  
```vb  
Dim sr As StreamReader  
sr = New StreamReader(resp.GetResponseStream(), Encoding.ASCII)  
```  
  
## <a name="see-also"></a><span data-ttu-id="6cde7-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6cde7-125">See also</span></span>

- [<span data-ttu-id="6cde7-126">Síťové programování v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6cde7-126">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="6cde7-127">Postupy: Vyžádání webové stránky a načtení výsledků jako streamu</span><span class="sxs-lookup"><span data-stu-id="6cde7-127">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>](how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)
- [<span data-ttu-id="6cde7-128">Postupy: Načtení položky WebResponse specifické pro protokol, která odpovídá položce WebRequest</span><span class="sxs-lookup"><span data-stu-id="6cde7-128">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>](how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)
