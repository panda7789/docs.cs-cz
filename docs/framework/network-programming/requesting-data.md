---
title: "Požadavek na Data"
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
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 76ea605444b5d1776c5a85891db4f3460e9df24b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="requesting-data"></a><span data-ttu-id="d795e-102">Požadavek na Data</span><span class="sxs-lookup"><span data-stu-id="d795e-102">Requesting Data</span></span>
<span data-ttu-id="d795e-103">Vývoj aplikací, které běží v distribuované provozní prostředí dnešní Internetu vyžaduje metodu efektivní, snadno použitelné pro načítání dat ze všech typů prostředků.</span><span class="sxs-lookup"><span data-stu-id="d795e-103">Developing applications that run in the distributed operating environment of today's Internet requires an efficient, easy-to-use method for retrieving data from resources of all types.</span></span> <span data-ttu-id="d795e-104">Modulární protokoly umožňují vyvíjet aplikace, které pomocí jediného rozhraní k načtení dat z více internetových protokolech.</span><span class="sxs-lookup"><span data-stu-id="d795e-104">Pluggable protocols let you develop applications that use a single interface to retrieve data from multiple Internet protocols.</span></span>  
  
## <a name="uploading-and-downloading-data-from-an-internet-server"></a><span data-ttu-id="d795e-105">Nahrávání a stahování dat z internetového serveru</span><span class="sxs-lookup"><span data-stu-id="d795e-105">Uploading and Downloading Data from an Internet Server</span></span>  
 <span data-ttu-id="d795e-106">Pro jednoduché požadavku a odpovědi transakce <xref:System.Net.WebClient> třída poskytuje nejsnazší pro nahrávání dat nebo stahování dat z internetového serveru.</span><span class="sxs-lookup"><span data-stu-id="d795e-106">For simple request and response transactions, the <xref:System.Net.WebClient> class provides the easiest method for uploading data to or downloading data from an Internet server.</span></span> <span data-ttu-id="d795e-107">**Webový klient** poskytuje metody pro odesílání a stahování souborů, přijímající a odesílající datové proudy, vyrovnávací paměť dat na server a přijímání odpověď.</span><span class="sxs-lookup"><span data-stu-id="d795e-107">**WebClient** provides methods for uploading and downloading files, sending and receiving streams, and sending a data buffer to the server and receiving a response.</span></span> <span data-ttu-id="d795e-108">**Webový klient** používá <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> je k dispozici pro použití třídy aby skutečné připojení k Internetu, takže všechny registrované modulární protokol.</span><span class="sxs-lookup"><span data-stu-id="d795e-108">**WebClient** uses the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes to make the actual connections to the Internet resource, so any registered pluggable protocol is available for use.</span></span>  
  
 <span data-ttu-id="d795e-109">Klientských aplikací, které je třeba, aby složitější data požadavku transakcí ze serverů pomocí **WebRequest** třídy a jeho následníky.</span><span class="sxs-lookup"><span data-stu-id="d795e-109">Client applications that need to make more complex transactions request data from servers using the **WebRequest** class and its descendants.</span></span> <span data-ttu-id="d795e-110">**WebRequest** zapouzdří podrobnosti o připojení k serveru, odesílání požadavku a přijetí odpovědi.</span><span class="sxs-lookup"><span data-stu-id="d795e-110">**WebRequest** encapsulates the details of connecting to the server, sending the request, and receiving the response.</span></span> <span data-ttu-id="d795e-111">**WebRequest** je abstraktní třída, která definuje sadu vlastností a metod, které jsou k dispozici pro všechny aplikace, které používají modulární protokoly.</span><span class="sxs-lookup"><span data-stu-id="d795e-111">**WebRequest** is an abstract class that defines a set of properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="d795e-112">Následníků **WebRequest**, jako například <xref:System.Net.HttpWebRequest>, implementovat vlastnosti a metody definované **WebRequest** způsobem, který je v souladu s základního protokolu.</span><span class="sxs-lookup"><span data-stu-id="d795e-112">Descendants of **WebRequest**, such as <xref:System.Net.HttpWebRequest>, implement the properties and methods defined by **WebRequest** in a way that is consistent with the underlying protocol.</span></span>  
  
 <span data-ttu-id="d795e-113">**WebRequest** třída vytváří instance specifické pro protokol **WebRequest** následníky, pomocí hodnoty identifikátoru URI předaný jeho <xref:System.Net.WebRequest.Create%2A> metoda určení konkrétní odvozené třídy instance pro vytvoření.</span><span class="sxs-lookup"><span data-stu-id="d795e-113">The **WebRequest** class creates protocol-specific instances of **WebRequest** descendants, using the value of the URI passed to its <xref:System.Net.WebRequest.Create%2A> method to determine the specific derived-class instance to create.</span></span> <span data-ttu-id="d795e-114">Vyberte aplikace, které **WebRequest** následník se má použít k má požadavek zpracovat tak, že zaregistrujete následník konstruktor s <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="d795e-114">Applications indicate which **WebRequest** descendant should be used to handle a request by registering the descendant's constructor with the <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="d795e-115">Žádosti se k internetového zdroji voláním <xref:System.Net.WebRequest.GetResponse%2A> metodu **WebRequest**.</span><span class="sxs-lookup"><span data-stu-id="d795e-115">A request is made to the Internet resource by calling the <xref:System.Net.WebRequest.GetResponse%2A> method on the **WebRequest**.</span></span> <span data-ttu-id="d795e-116">**GetResponse** metoda vytvoří žádost specifické pro protokol z vlastností **WebRequest**, vytvoří soketu připojení TCP nebo UDP na server a odešle žádost.</span><span class="sxs-lookup"><span data-stu-id="d795e-116">The **GetResponse** method constructs the protocol-specific request from the properties of the **WebRequest**, makes the TCP or UDP socket connection to the server, and sends the request.</span></span> <span data-ttu-id="d795e-117">Pro požadavky, které odesílají data na server, jako je například HTTP **Post** nebo FTP **Put** požadavky, <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> metoda poskytuje datový proud sítě, ve kterém se má odeslat data.</span><span class="sxs-lookup"><span data-stu-id="d795e-117">For requests that send data to the server, such as HTTP **Post** or FTP **Put** requests, the <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> method provides a network stream in which to send the data.</span></span>  
  
 <span data-ttu-id="d795e-118">**GetResponse** metoda vrátí hodnotu konkrétního protokolu **WebResponse** odpovídající **WebRequest.**</span><span class="sxs-lookup"><span data-stu-id="d795e-118">The **GetResponse** method returns a protocol-specific **WebResponse** that matches the **WebRequest.**</span></span>  
  
 <span data-ttu-id="d795e-119">**WebResponse** třída je také abstraktní třída, která definuje vlastnosti a metody, které jsou k dispozici pro všechny aplikace, které používají modulární protokoly.</span><span class="sxs-lookup"><span data-stu-id="d795e-119">The **WebResponse** class is also an abstract class that defines properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="d795e-120">**WebResponse** následníky implementovat tyto vlastnosti a metody pro základní protokol.</span><span class="sxs-lookup"><span data-stu-id="d795e-120">**WebResponse** descendants implement these properties and methods for the underlying protocol.</span></span> <span data-ttu-id="d795e-121"><xref:System.Net.HttpWebResponse> Například třída implementuje **WebResponse** třídy pro protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="d795e-121">The <xref:System.Net.HttpWebResponse> class, for example, implements the **WebResponse** class for HTTP.</span></span>  
  
 <span data-ttu-id="d795e-122">Data vrácená serverem jsou zobrazena na aplikaci v datový proud vrácený <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="d795e-122">The data returned by the server is presented to the application in the stream returned by the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d795e-123">Tento datový proud stejně jako jakýkoli jiný, můžete použít, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d795e-123">You can use this stream like any other, as shown in the following example.</span></span>  
  
```csharp  
StreamReader sr =  
   new StreamReader(resp.GetResponseStream(), Encoding.ASCII);  
```  
  
```vb  
Dim sr As StreamReader  
sr = New StreamReader(resp.GetResponseStream(), Encoding.ASCII)  
```  
  
## <a name="see-also"></a><span data-ttu-id="d795e-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="d795e-124">See Also</span></span>  
 [<span data-ttu-id="d795e-125">Síťové programování v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d795e-125">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)  
 [<span data-ttu-id="d795e-126">Postupy: Vyžádání webové stránky a načtení výsledků jako streamu</span><span class="sxs-lookup"><span data-stu-id="d795e-126">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>](../../../docs/framework/network-programming/how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)  
 [<span data-ttu-id="d795e-127">Postupy: Načtení položky WebResponse specifické pro protokol, která odpovídá položce WebRequest</span><span class="sxs-lookup"><span data-stu-id="d795e-127">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>](../../../docs/framework/network-programming/how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)
