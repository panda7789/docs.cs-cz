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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048624"
---
# <a name="creating-internet-requests"></a><span data-ttu-id="83f8e-102">Vytváření internetových žádostí</span><span class="sxs-lookup"><span data-stu-id="83f8e-102">Creating Internet Requests</span></span>
<span data-ttu-id="83f8e-103">Aplikace vytváří <xref:System.Net.WebRequest> instance <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="83f8e-103">Applications create <xref:System.Net.WebRequest> instances through the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="83f8e-104">Toto je statická metoda, která vytvoří třídu odvozenou od **WebRequest** na základě předaného schématu identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="83f8e-104">This is a static method that creates a class derived from **WebRequest** based on the URI scheme passed to it.</span></span>  
  
## <a name="web-file-and-ftp-requests"></a><span data-ttu-id="83f8e-105">Webové, souborové a FTP požadavky</span><span class="sxs-lookup"><span data-stu-id="83f8e-105">Web, File and FTP Requests</span></span>  
 <span data-ttu-id="83f8e-106">.NET Framework poskytuje <xref:System.Net.HttpWebRequest> třídu, která je odvozena z **WebRequest**, pro zpracování požadavků HTTP a HTTPS.</span><span class="sxs-lookup"><span data-stu-id="83f8e-106">The .NET Framework provides the <xref:System.Net.HttpWebRequest> class, which is derived from **WebRequest**, to handle HTTP and HTTPS requests.</span></span> <span data-ttu-id="83f8e-107">Ve většině případů třída **WebRequest** poskytuje všechny vlastnosti, které potřebujete k vytvoření žádosti; v případě potřeby však můžete přetypovat objekty **WebRequest** vytvořené metodou **WebRequest. Create** pro typ **HttpWebRequest** pro přístup k vlastnostem specifickým pro protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="83f8e-107">In most cases, the **WebRequest** class provides all the properties you need to make a request; however, if necessary, you can cast **WebRequest** objects created by the **WebRequest.Create** method to the **HttpWebRequest** type to access the HTTP-specific properties of the request.</span></span> <span data-ttu-id="83f8e-108">Podobně objekt **HttpWebResponse** zpracovává odpovědi z požadavků HTTP a HTTPS.</span><span class="sxs-lookup"><span data-stu-id="83f8e-108">Similarly, the **HttpWebResponse** object handles the responses from HTTP and HTTPS requests.</span></span> <span data-ttu-id="83f8e-109">Chcete-li získat přístup k vlastnostem objektu **HttpWebResponse** specifickým pro protokol HTTP, je třeba přetypovat objekty **WebResponse** na typ **HttpWebResponse** .</span><span class="sxs-lookup"><span data-stu-id="83f8e-109">To access the HTTP-specific properties of the **HttpWebResponse** object, you need to cast **WebResponse** objects to the **HttpWebResponse** type.</span></span>  
  
 <span data-ttu-id="83f8e-110">.NET Framework také poskytuje <xref:System.Net.FileWebRequest> třídy a <xref:System.Net.FileWebResponse> pro zpracování požadavků na prostředky, které používají "soubor:" Schéma identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="83f8e-110">The .NET Framework also provides the <xref:System.Net.FileWebRequest> and <xref:System.Net.FileWebResponse> classes to handle requests for resources that use the "file:" URI scheme.</span></span> <span data-ttu-id="83f8e-111">Podobně třídy <xref:System.Net.FtpWebResponse> a jsou k dispozici pro zpracování požadavků na prostředky, které používají schéma "FTP:". <xref:System.Net.FtpWebRequest></span><span class="sxs-lookup"><span data-stu-id="83f8e-111">Likewise, the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes are provided to handle requests for resources that use the "ftp:" scheme.</span></span> <span data-ttu-id="83f8e-112">Pokud je váš požadavek na prostředek, který používá některé z těchto schémat, můžete použít metodu **WebRequest. Create** k získání objektu, se kterým se má váš požadavek vytvořit.</span><span class="sxs-lookup"><span data-stu-id="83f8e-112">If your request is for a resource that uses any of these schemes, you can use the **WebRequest.Create** method to obtain an object with which to make your request.</span></span>  
  
 <span data-ttu-id="83f8e-113">Pro zpracování požadavků, které používají jiné protokoly na úrovni aplikace, je nutné implementovat třídy specifické pro protokol odvozené od **WebRequest** a **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="83f8e-113">To handle requests that use other application-level protocols, you need to implement protocol-specific classes derived from **WebRequest** and **WebResponse**.</span></span> <span data-ttu-id="83f8e-114">Další informace najdete v tématu [programování protokolů pro připojení](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="83f8e-114">For more information, see [Programming Pluggable Protocols](programming-pluggable-protocols.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83f8e-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="83f8e-115">See also</span></span>

- [<span data-ttu-id="83f8e-116">Postupy: Vyžádání dat pomocí třídy WebRequest</span><span class="sxs-lookup"><span data-stu-id="83f8e-116">How to: Request Data Using the WebRequest Class</span></span>](how-to-request-data-using-the-webrequest-class.md)
- [<span data-ttu-id="83f8e-117">Žádosti o data</span><span class="sxs-lookup"><span data-stu-id="83f8e-117">Requesting Data</span></span>](requesting-data.md)
