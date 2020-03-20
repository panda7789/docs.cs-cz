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
ms.openlocfilehash: 80e3a6bd199691df9391e88d5a64fab5df2a08a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048624"
---
# <a name="creating-internet-requests"></a><span data-ttu-id="b6387-102">Vytváření internetových žádostí</span><span class="sxs-lookup"><span data-stu-id="b6387-102">Creating Internet Requests</span></span>
<span data-ttu-id="b6387-103">Aplikace <xref:System.Net.WebRequest> vytvořit instance <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> prostřednictvím metody.</span><span class="sxs-lookup"><span data-stu-id="b6387-103">Applications create <xref:System.Net.WebRequest> instances through the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b6387-104">Jedná se o statickou metodu, která vytvoří třídu odvozenou z **webového požadavku** na základě schématu URI, které jí bylo předáno.</span><span class="sxs-lookup"><span data-stu-id="b6387-104">This is a static method that creates a class derived from **WebRequest** based on the URI scheme passed to it.</span></span>  
  
## <a name="web-file-and-ftp-requests"></a><span data-ttu-id="b6387-105">Webové, souborové a FTP požadavky</span><span class="sxs-lookup"><span data-stu-id="b6387-105">Web, File and FTP Requests</span></span>  
 <span data-ttu-id="b6387-106">Rozhraní .NET Framework <xref:System.Net.HttpWebRequest> poskytuje třídu, která je odvozena z **WebRequest**, pro zpracování požadavků HTTP a HTTPS.</span><span class="sxs-lookup"><span data-stu-id="b6387-106">The .NET Framework provides the <xref:System.Net.HttpWebRequest> class, which is derived from **WebRequest**, to handle HTTP and HTTPS requests.</span></span> <span data-ttu-id="b6387-107">Ve většině případů třída **WebRequest** poskytuje všechny vlastnosti, které potřebujete k vytvoření požadavku; V případě potřeby však můžete přetypovat objekty **WebRequest** vytvořené metodou **WebRequest.Create** do typu **HttpWebRequest** pro přístup k vlastnostem požadavku specifickým pro protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="b6387-107">In most cases, the **WebRequest** class provides all the properties you need to make a request; however, if necessary, you can cast **WebRequest** objects created by the **WebRequest.Create** method to the **HttpWebRequest** type to access the HTTP-specific properties of the request.</span></span> <span data-ttu-id="b6387-108">Podobně **httpwebresponse** objekt zpracovává odpovědi z požadavků HTTP a HTTPS.</span><span class="sxs-lookup"><span data-stu-id="b6387-108">Similarly, the **HttpWebResponse** object handles the responses from HTTP and HTTPS requests.</span></span> <span data-ttu-id="b6387-109">Chcete-li získat přístup k vlastnostem objektu **HttpWebResponse** specifickým pro protokol HTTP, je třeba přetypovat objekty **WebResponse** do typu **HttpWebResponse.**</span><span class="sxs-lookup"><span data-stu-id="b6387-109">To access the HTTP-specific properties of the **HttpWebResponse** object, you need to cast **WebResponse** objects to the **HttpWebResponse** type.</span></span>  
  
 <span data-ttu-id="b6387-110">Rozhraní .NET Framework <xref:System.Net.FileWebRequest> také <xref:System.Net.FileWebResponse> poskytuje třídy a pro zpracování požadavků na prostředky, které používají schéma IDENTIFIKÁTORURI "file:".</span><span class="sxs-lookup"><span data-stu-id="b6387-110">The .NET Framework also provides the <xref:System.Net.FileWebRequest> and <xref:System.Net.FileWebResponse> classes to handle requests for resources that use the "file:" URI scheme.</span></span> <span data-ttu-id="b6387-111">Podobně <xref:System.Net.FtpWebRequest> a <xref:System.Net.FtpWebResponse> třídy jsou k dispozici pro zpracování požadavků na prostředky, které používají schéma "ftp:".</span><span class="sxs-lookup"><span data-stu-id="b6387-111">Likewise, the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes are provided to handle requests for resources that use the "ftp:" scheme.</span></span> <span data-ttu-id="b6387-112">Pokud váš požadavek je pro prostředek, který používá některý z těchto schémat, můžete použít **WebRequest.Create** metoda získat objekt, se kterým chcete podat požadavek.</span><span class="sxs-lookup"><span data-stu-id="b6387-112">If your request is for a resource that uses any of these schemes, you can use the **WebRequest.Create** method to obtain an object with which to make your request.</span></span>  
  
 <span data-ttu-id="b6387-113">Chcete-li zpracovávat požadavky, které používají jiné protokoly na úrovni aplikace, je třeba implementovat třídy specifické pro protokol odvozené z **WebRequest** a **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="b6387-113">To handle requests that use other application-level protocols, you need to implement protocol-specific classes derived from **WebRequest** and **WebResponse**.</span></span> <span data-ttu-id="b6387-114">Další informace naleznete [v tématu Programming Pluggable Protocols](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="b6387-114">For more information, see [Programming Pluggable Protocols](programming-pluggable-protocols.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6387-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="b6387-115">See also</span></span>

- [<span data-ttu-id="b6387-116">Postupy:Vyžádání dat pomocí třídy WebRequest</span><span class="sxs-lookup"><span data-stu-id="b6387-116">How to: Request Data Using the WebRequest Class</span></span>](how-to-request-data-using-the-webrequest-class.md)
- [<span data-ttu-id="b6387-117">Žádosti o data</span><span class="sxs-lookup"><span data-stu-id="b6387-117">Requesting Data</span></span>](requesting-data.md)
