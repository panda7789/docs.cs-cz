---
title: "Vytváření žádostí o Internetu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WebRequest class, sending and receiving data
- Networking
- HttpWebResponse class, sending and receiving data
- requesting data from Internet, creating requests
- Network Resources
- Internet, requesting data
- data requests, creating requests
ms.assetid: faab683e-3f1e-4eee-b5e9-59f7245033d5
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 8cbbb0db657f002c189ab4db9311ca48d83c32a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="creating-internet-requests"></a><span data-ttu-id="9d986-102">Vytváření žádostí o Internetu</span><span class="sxs-lookup"><span data-stu-id="9d986-102">Creating Internet Requests</span></span>
<span data-ttu-id="9d986-103">Vytvoření aplikace <xref:System.Net.WebRequest> instance prostřednictvím <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="9d986-103">Applications create <xref:System.Net.WebRequest> instances through the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="9d986-104">Toto je statickou metodu, která vytvoří třídy odvozené od **WebRequest** založené na schéma identifikátoru URI do ní předán.</span><span class="sxs-lookup"><span data-stu-id="9d986-104">This is a static method that creates a class derived from **WebRequest** based on the URI scheme passed to it.</span></span>  
  
## <a name="web-file-and-ftp-requests"></a><span data-ttu-id="9d986-105">Webové aplikace, soubor a požadavky protokolu FTP</span><span class="sxs-lookup"><span data-stu-id="9d986-105">Web, File and FTP Requests</span></span>  
 <span data-ttu-id="9d986-106">Poskytuje rozhraní .NET Framework <xref:System.Net.HttpWebRequest> třídy, která je odvozená od **WebRequest**pro zpracování požadavků HTTP a HTTPS.</span><span class="sxs-lookup"><span data-stu-id="9d986-106">The .NET Framework provides the <xref:System.Net.HttpWebRequest> class, which is derived from **WebRequest**, to handle HTTP and HTTPS requests.</span></span> <span data-ttu-id="9d986-107">Ve většině případů **WebRequest** třída poskytuje všechny vlastnosti, které musíte provést žádost o; však v případě potřeby můžete převést **WebRequest** objekty vytvořené **WebRequest.Create**  metodu **HttpWebRequest** typ, který má přístup k protokolu HTTP specifické vlastnosti požadavku.</span><span class="sxs-lookup"><span data-stu-id="9d986-107">In most cases, the **WebRequest** class provides all the properties you need to make a request; however, if necessary, you can cast **WebRequest** objects created by the **WebRequest.Create** method to the **HttpWebRequest** type to access the HTTP-specific properties of the request.</span></span> <span data-ttu-id="9d986-108">Podobně **HttpWebResponse** objekt zpracovává odpovědi z žádostí HTTP a HTTPS.</span><span class="sxs-lookup"><span data-stu-id="9d986-108">Similarly, the **HttpWebResponse** object handles the responses from HTTP and HTTPS requests.</span></span> <span data-ttu-id="9d986-109">Pro přístup k vlastnosti specifické pro protokol HTTP **HttpWebResponse** objektu, musíte převést **WebResponse** objekty ke **HttpWebResponse** typu.</span><span class="sxs-lookup"><span data-stu-id="9d986-109">To access the HTTP-specific properties of the **HttpWebResponse** object, you need to cast **WebResponse** objects to the **HttpWebResponse** type.</span></span>  
  
 <span data-ttu-id="9d986-110">Také poskytuje rozhraní .NET Framework <xref:System.Net.FileWebRequest> a <xref:System.Net.FileWebResponse> třídy pro zpracování požadavků na zdroje, které používají "souboru:" schéma identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="9d986-110">The .NET Framework also provides the <xref:System.Net.FileWebRequest> and <xref:System.Net.FileWebResponse> classes to handle requests for resources that use the "file:" URI scheme.</span></span> <span data-ttu-id="9d986-111">Podobně <xref:System.Net.FtpWebRequest> a <xref:System.Net.FtpWebResponse> třídy jsou k dispozici pro zpracování požadavků na zdroje, které používají "ftp:" schéma.</span><span class="sxs-lookup"><span data-stu-id="9d986-111">Likewise, the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes are provided to handle requests for resources that use the "ftp:" scheme.</span></span> <span data-ttu-id="9d986-112">Pokud vaše žádost je pro prostředek, který používá některé z těchto režimů, můžete použít **WebRequest.Create** metoda získat objekt, ke které má být zkontrolujte vaši žádost.</span><span class="sxs-lookup"><span data-stu-id="9d986-112">If your request is for a resource that uses any of these schemes, you can use the **WebRequest.Create** method to obtain an object with which to make your request.</span></span>  
  
 <span data-ttu-id="9d986-113">Pro zpracování žádostí, které používají jiné protokoly na úrovni aplikace, potřebujete implementovat specifické třídy odvozené od **WebRequest** a **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="9d986-113">To handle requests that use other application-level protocols, you need to implement protocol-specific classes derived from **WebRequest** and **WebResponse**.</span></span> <span data-ttu-id="9d986-114">Další informace najdete v tématu [programování modulární protokoly](../../../docs/framework/network-programming/programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="9d986-114">For more information, see [Programming Pluggable Protocols](../../../docs/framework/network-programming/programming-pluggable-protocols.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d986-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="9d986-115">See Also</span></span>  
 [<span data-ttu-id="9d986-116">Postupy:Vyžádání dat pomocí třídy WebRequest</span><span class="sxs-lookup"><span data-stu-id="9d986-116">How to: Request Data Using the WebRequest Class</span></span>](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)  
 [<span data-ttu-id="9d986-117">Žádosti o data</span><span class="sxs-lookup"><span data-stu-id="9d986-117">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
