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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047317"
---
# <a name="requesting-data"></a><span data-ttu-id="31107-102">Žádosti o data</span><span class="sxs-lookup"><span data-stu-id="31107-102">Requesting Data</span></span>
<span data-ttu-id="31107-103">Vývoj aplikací, které běží v distribuovaném provozním prostředí dnešního Internetu, vyžaduje efektivní a snadno použitelnou metodu pro načítání dat z prostředků všech typů.</span><span class="sxs-lookup"><span data-stu-id="31107-103">Developing applications that run in the distributed operating environment of today's Internet requires an efficient, easy-to-use method for retrieving data from resources of all types.</span></span> <span data-ttu-id="31107-104">Připojitelné protokoly umožňují vyvíjet aplikace, které používají jediné rozhraní k načtení dat z více internetových protokolů.</span><span class="sxs-lookup"><span data-stu-id="31107-104">Pluggable protocols let you develop applications that use a single interface to retrieve data from multiple Internet protocols.</span></span>  
  
## <a name="uploading-and-downloading-data-from-an-internet-server"></a><span data-ttu-id="31107-105">Nahrávání a stahování dat z internetového serveru</span><span class="sxs-lookup"><span data-stu-id="31107-105">Uploading and Downloading Data from an Internet Server</span></span>  
 <span data-ttu-id="31107-106">Pro jednoduché transakce požadavků a <xref:System.Net.WebClient> odpovědí poskytuje třída nejjednodušší metodu pro nahrávání dat nebo stahování dat z internetového serveru.</span><span class="sxs-lookup"><span data-stu-id="31107-106">For simple request and response transactions, the <xref:System.Net.WebClient> class provides the easiest method for uploading data to or downloading data from an Internet server.</span></span> <span data-ttu-id="31107-107">**WebClient** poskytuje metody pro nahrávání a stahování souborů, odesílání a přijímání datových proudů a odesílání vyrovnávací paměti dat na server a příjem odpovědi.</span><span class="sxs-lookup"><span data-stu-id="31107-107">**WebClient** provides methods for uploading and downloading files, sending and receiving streams, and sending a data buffer to the server and receiving a response.</span></span> <span data-ttu-id="31107-108">**WebClient** používá <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> třídy a k navazování skutečných připojení k internetovému prostředku, takže je k dispozici libovolný registrovaný připojitelný protokol.</span><span class="sxs-lookup"><span data-stu-id="31107-108">**WebClient** uses the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes to make the actual connections to the Internet resource, so any registered pluggable protocol is available for use.</span></span>  
  
 <span data-ttu-id="31107-109">Klientské aplikace, které potřebují provádět složitější transakce, vyžadují data ze serverů používajících třídu **WebRequest** a její následníky.</span><span class="sxs-lookup"><span data-stu-id="31107-109">Client applications that need to make more complex transactions request data from servers using the **WebRequest** class and its descendants.</span></span> <span data-ttu-id="31107-110">**WebRequest** zapouzdřuje podrobnosti o připojení k serveru, odeslání požadavku a přijetí odpovědi.</span><span class="sxs-lookup"><span data-stu-id="31107-110">**WebRequest** encapsulates the details of connecting to the server, sending the request, and receiving the response.</span></span> <span data-ttu-id="31107-111">**WebRequest** je abstraktní třída, která definuje sadu vlastností a metod, které jsou k dispozici pro všechny aplikace, které používají připojitelné protokoly.</span><span class="sxs-lookup"><span data-stu-id="31107-111">**WebRequest** is an abstract class that defines a set of properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="31107-112">Následovníci **WebRequest**, <xref:System.Net.HttpWebRequest>například implementovat vlastnosti a metody definované **WebRequest** způsobem, který je konzistentní s podkladovým protokolem.</span><span class="sxs-lookup"><span data-stu-id="31107-112">Descendants of **WebRequest**, such as <xref:System.Net.HttpWebRequest>, implement the properties and methods defined by **WebRequest** in a way that is consistent with the underlying protocol.</span></span>  
  
 <span data-ttu-id="31107-113">Třída **WebRequest** vytvoří instance potomků **WebRequest** specifické pro protokol pomocí hodnoty <xref:System.Net.WebRequest.Create%2A> identifikátoru URI předané jeho metodě k určení konkrétní instance odvozené třídy, kterou chcete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="31107-113">The **WebRequest** class creates protocol-specific instances of **WebRequest** descendants, using the value of the URI passed to its <xref:System.Net.WebRequest.Create%2A> method to determine the specific derived-class instance to create.</span></span> <span data-ttu-id="31107-114">Aplikace označují, který **potomek WebRequest** by měl být použit ke zpracování <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> požadavku registrací konstruktoru potomka pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="31107-114">Applications indicate which **WebRequest** descendant should be used to handle a request by registering the descendant's constructor with the <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="31107-115">Požadavek je podán a internetová <xref:System.Net.WebRequest.GetResponse%2A> prostředek voláním metody na **WebRequest**.</span><span class="sxs-lookup"><span data-stu-id="31107-115">A request is made to the Internet resource by calling the <xref:System.Net.WebRequest.GetResponse%2A> method on the **WebRequest**.</span></span> <span data-ttu-id="31107-116">Metoda **GetResponse** vytvoří požadavek specifický pro protokol z vlastností **aplikace WebRequest**, vytvoří připojení soketu TCP nebo UDP k serveru a odešle požadavek.</span><span class="sxs-lookup"><span data-stu-id="31107-116">The **GetResponse** method constructs the protocol-specific request from the properties of the **WebRequest**, makes the TCP or UDP socket connection to the server, and sends the request.</span></span> <span data-ttu-id="31107-117">Pro požadavky, které odesílají data na server, například HTTP <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> **Post** nebo FTP **Put** požadavky, metoda poskytuje síťový datový proud, ve kterém chcete odeslat data.</span><span class="sxs-lookup"><span data-stu-id="31107-117">For requests that send data to the server, such as HTTP **Post** or FTP **Put** requests, the <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> method provides a network stream in which to send the data.</span></span>  
  
 <span data-ttu-id="31107-118">Metoda **GetResponse** vrátí **webovou odezvu** specifickou pro protokol, která odpovídá **požadavku WebRequest.**</span><span class="sxs-lookup"><span data-stu-id="31107-118">The **GetResponse** method returns a protocol-specific **WebResponse** that matches the **WebRequest.**</span></span>  
  
 <span data-ttu-id="31107-119">Třída **WebResponse** je také abstraktní třída, která definuje vlastnosti a metody, které jsou k dispozici všem aplikacím, které používají připojitelné protokoly.</span><span class="sxs-lookup"><span data-stu-id="31107-119">The **WebResponse** class is also an abstract class that defines properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="31107-120">**Následovníci WebResponse** implementují tyto vlastnosti a metody pro základní protokol.</span><span class="sxs-lookup"><span data-stu-id="31107-120">**WebResponse** descendants implement these properties and methods for the underlying protocol.</span></span> <span data-ttu-id="31107-121">Třída <xref:System.Net.HttpWebResponse> například implementuje třídu **WebResponse** pro protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="31107-121">The <xref:System.Net.HttpWebResponse> class, for example, implements the **WebResponse** class for HTTP.</span></span>  
  
 <span data-ttu-id="31107-122">Data vrácená serverem jsou prezentována aplikaci v <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> datovém proudu vráceném metodou.</span><span class="sxs-lookup"><span data-stu-id="31107-122">The data returned by the server is presented to the application in the stream returned by the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="31107-123">Tento datový proud můžete použít jako každý jiný, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="31107-123">You can use this stream like any other, as shown in the following example.</span></span>  
  
```csharp  
StreamReader sr =  
   new StreamReader(resp.GetResponseStream(), Encoding.ASCII);  
```  
  
```vb  
Dim sr As StreamReader  
sr = New StreamReader(resp.GetResponseStream(), Encoding.ASCII)  
```  
  
## <a name="see-also"></a><span data-ttu-id="31107-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="31107-124">See also</span></span>

- [<span data-ttu-id="31107-125">Síťové programování v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="31107-125">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="31107-126">Postupy: Vyžádání webové stránky a načtení výsledků jako streamu</span><span class="sxs-lookup"><span data-stu-id="31107-126">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>](how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)
- [<span data-ttu-id="31107-127">Postupy: Načtení položky WebResponse specifické pro protokol, která odpovídá položce WebRequest</span><span class="sxs-lookup"><span data-stu-id="31107-127">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>](how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)
