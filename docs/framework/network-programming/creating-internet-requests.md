---
title: Vytváření internetových žádostí
ms.date: 03/30/2017
helpviewer_keywords:
- WebRequest class, sending and receiving data
- Networking
- HttpWebResponse class, sending and receiving data
- requesting data from Internet, creating requests
- Network Resources
- Internet, requesting data
- data requests, creating requests
ms.assetid: faab683e-3f1e-4eee-b5e9-59f7245033d5
ms.openlocfilehash: 2a4915796310e4f6899d833f20bc5260e0ee032b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61643124"
---
# <a name="creating-internet-requests"></a><span data-ttu-id="8311e-102">Vytváření internetových žádostí</span><span class="sxs-lookup"><span data-stu-id="8311e-102">Creating Internet Requests</span></span>
<span data-ttu-id="8311e-103">Vytvoření aplikace <xref:System.Net.WebRequest> instance prostřednictvím <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="8311e-103">Applications create <xref:System.Net.WebRequest> instances through the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="8311e-104">Toto je statická metoda, která vytvoří třídu odvozenou z **WebRequest** podle do něho předaný schéma identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="8311e-104">This is a static method that creates a class derived from **WebRequest** based on the URI scheme passed to it.</span></span>  
  
## <a name="web-file-and-ftp-requests"></a><span data-ttu-id="8311e-105">Webový server, souboru a požadavky protokolu FTP</span><span class="sxs-lookup"><span data-stu-id="8311e-105">Web, File and FTP Requests</span></span>  
 <span data-ttu-id="8311e-106">Rozhraní .NET Framework poskytuje <xref:System.Net.HttpWebRequest> třídu, která je odvozena od **WebRequest**, pro zpracování požadavků HTTP a HTTPS.</span><span class="sxs-lookup"><span data-stu-id="8311e-106">The .NET Framework provides the <xref:System.Net.HttpWebRequest> class, which is derived from **WebRequest**, to handle HTTP and HTTPS requests.</span></span> <span data-ttu-id="8311e-107">Ve většině případů **WebRequest** třída poskytuje všechny vlastnosti, je třeba provést požadavek, ale v případě potřeby můžete přetypovat **WebRequest** objekty vytvořené **WebRequest.Create**  metodu **HttpWebRequest** typ, který má přístup k vlastnostem specifickým pro HTTP žádosti.</span><span class="sxs-lookup"><span data-stu-id="8311e-107">In most cases, the **WebRequest** class provides all the properties you need to make a request; however, if necessary, you can cast **WebRequest** objects created by the **WebRequest.Create** method to the **HttpWebRequest** type to access the HTTP-specific properties of the request.</span></span> <span data-ttu-id="8311e-108">Podobně **HttpWebResponse** objekt zpracovává odpovědi z požadavků HTTP a HTTPS.</span><span class="sxs-lookup"><span data-stu-id="8311e-108">Similarly, the **HttpWebResponse** object handles the responses from HTTP and HTTPS requests.</span></span> <span data-ttu-id="8311e-109">Pro přístup k vlastnostem specifickým pro HTTP **HttpWebResponse** objektu, je třeba přetypovat **WebResponse** objektů **HttpWebResponse** typu.</span><span class="sxs-lookup"><span data-stu-id="8311e-109">To access the HTTP-specific properties of the **HttpWebResponse** object, you need to cast **WebResponse** objects to the **HttpWebResponse** type.</span></span>  
  
 <span data-ttu-id="8311e-110">Také poskytuje rozhraní .NET Framework <xref:System.Net.FileWebRequest> a <xref:System.Net.FileWebResponse> třídy, které zpracovávají požadavky na prostředky, které používají "file:" Schéma identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="8311e-110">The .NET Framework also provides the <xref:System.Net.FileWebRequest> and <xref:System.Net.FileWebResponse> classes to handle requests for resources that use the "file:" URI scheme.</span></span> <span data-ttu-id="8311e-111">Podobně <xref:System.Net.FtpWebRequest> a <xref:System.Net.FtpWebResponse> třídy jsou k dispozici pro zpracování požadavků pro prostředky, které používají "ftp:" schéma.</span><span class="sxs-lookup"><span data-stu-id="8311e-111">Likewise, the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes are provided to handle requests for resources that use the "ftp:" scheme.</span></span> <span data-ttu-id="8311e-112">Pokud je váš požadavek pro prostředek, který používá některou z těchto režimů, můžete použít **WebRequest.Create** metodu k získání objektu, pomocí kterého se má podat žádost.</span><span class="sxs-lookup"><span data-stu-id="8311e-112">If your request is for a resource that uses any of these schemes, you can use the **WebRequest.Create** method to obtain an object with which to make your request.</span></span>  
  
 <span data-ttu-id="8311e-113">Pro zpracování požadavků, které používají jiné protokoly na úrovni aplikace, budete muset implementovat konkrétní třídy odvozené od **WebRequest** a **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="8311e-113">To handle requests that use other application-level protocols, you need to implement protocol-specific classes derived from **WebRequest** and **WebResponse**.</span></span> <span data-ttu-id="8311e-114">Další informace najdete v tématu [programování připojitelných protokolů](../../../docs/framework/network-programming/programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="8311e-114">For more information, see [Programming Pluggable Protocols](../../../docs/framework/network-programming/programming-pluggable-protocols.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8311e-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8311e-115">See also</span></span>

- [<span data-ttu-id="8311e-116">Postupy: Žádost o Data pomocí třídy WebRequest</span><span class="sxs-lookup"><span data-stu-id="8311e-116">How to: Request Data Using the WebRequest Class</span></span>](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)
- [<span data-ttu-id="8311e-117">Žádosti o data</span><span class="sxs-lookup"><span data-stu-id="8311e-117">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
