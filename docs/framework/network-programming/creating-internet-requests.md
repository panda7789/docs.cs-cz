---
title: Vytváření internetových žádostí
description: Přečtěte si, jak aplikace vytvářejí instance WebRequest prostřednictvím WebRequest. Create, statické metody, která vytvoří odvozenou třídu založenou na schématu identifikátoru URI, které je předáno.
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
ms.openlocfilehash: 598ef9d44737ef6b33af833cbfb7788170165588
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502623"
---
# <a name="creating-internet-requests"></a><span data-ttu-id="2326a-103">Vytváření internetových žádostí</span><span class="sxs-lookup"><span data-stu-id="2326a-103">Creating Internet Requests</span></span>
<span data-ttu-id="2326a-104">Aplikace vytváří <xref:System.Net.WebRequest> instance pomocí <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="2326a-104">Applications create <xref:System.Net.WebRequest> instances through the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="2326a-105">Toto je statická metoda, která vytvoří třídu odvozenou od **WebRequest** na základě předaného schématu identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="2326a-105">This is a static method that creates a class derived from **WebRequest** based on the URI scheme passed to it.</span></span>  
  
## <a name="web-file-and-ftp-requests"></a><span data-ttu-id="2326a-106">Webové, souborové a FTP požadavky</span><span class="sxs-lookup"><span data-stu-id="2326a-106">Web, File and FTP Requests</span></span>  
 <span data-ttu-id="2326a-107">.NET Framework poskytuje <xref:System.Net.HttpWebRequest> třídu, která je odvozena z **WebRequest**, pro zpracování požadavků HTTP a HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2326a-107">The .NET Framework provides the <xref:System.Net.HttpWebRequest> class, which is derived from **WebRequest**, to handle HTTP and HTTPS requests.</span></span> <span data-ttu-id="2326a-108">Ve většině případů třída **WebRequest** poskytuje všechny vlastnosti, které potřebujete k vytvoření žádosti; v případě potřeby však můžete přetypovat objekty **WebRequest** vytvořené metodou **WebRequest. Create** pro typ **HttpWebRequest** pro přístup k vlastnostem specifickým pro protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="2326a-108">In most cases, the **WebRequest** class provides all the properties you need to make a request; however, if necessary, you can cast **WebRequest** objects created by the **WebRequest.Create** method to the **HttpWebRequest** type to access the HTTP-specific properties of the request.</span></span> <span data-ttu-id="2326a-109">Podobně objekt **HttpWebResponse** zpracovává odpovědi z požadavků HTTP a HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2326a-109">Similarly, the **HttpWebResponse** object handles the responses from HTTP and HTTPS requests.</span></span> <span data-ttu-id="2326a-110">Chcete-li získat přístup k vlastnostem objektu **HttpWebResponse** specifickým pro protokol HTTP, je třeba přetypovat objekty **WebResponse** na typ **HttpWebResponse** .</span><span class="sxs-lookup"><span data-stu-id="2326a-110">To access the HTTP-specific properties of the **HttpWebResponse** object, you need to cast **WebResponse** objects to the **HttpWebResponse** type.</span></span>  
  
 <span data-ttu-id="2326a-111">.NET Framework také poskytuje <xref:System.Net.FileWebRequest> <xref:System.Net.FileWebResponse> třídy a pro zpracování požadavků na prostředky, které používají schéma identifikátoru URI "File:".</span><span class="sxs-lookup"><span data-stu-id="2326a-111">The .NET Framework also provides the <xref:System.Net.FileWebRequest> and <xref:System.Net.FileWebResponse> classes to handle requests for resources that use the "file:" URI scheme.</span></span> <span data-ttu-id="2326a-112">Podobně <xref:System.Net.FtpWebRequest> <xref:System.Net.FtpWebResponse> třídy a jsou k dispozici pro zpracování požadavků na prostředky, které používají schéma "FTP:".</span><span class="sxs-lookup"><span data-stu-id="2326a-112">Likewise, the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes are provided to handle requests for resources that use the "ftp:" scheme.</span></span> <span data-ttu-id="2326a-113">Pokud je váš požadavek na prostředek, který používá některé z těchto schémat, můžete použít metodu **WebRequest. Create** k získání objektu, se kterým se má váš požadavek vytvořit.</span><span class="sxs-lookup"><span data-stu-id="2326a-113">If your request is for a resource that uses any of these schemes, you can use the **WebRequest.Create** method to obtain an object with which to make your request.</span></span>  
  
 <span data-ttu-id="2326a-114">Pro zpracování požadavků, které používají jiné protokoly na úrovni aplikace, je nutné implementovat třídy specifické pro protokol odvozené od **WebRequest** a **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="2326a-114">To handle requests that use other application-level protocols, you need to implement protocol-specific classes derived from **WebRequest** and **WebResponse**.</span></span> <span data-ttu-id="2326a-115">Další informace najdete v tématu [programování protokolů pro připojení](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="2326a-115">For more information, see [Programming Pluggable Protocols](programming-pluggable-protocols.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2326a-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2326a-116">See also</span></span>

- [<span data-ttu-id="2326a-117">Postupy:Vyžádání dat pomocí třídy WebRequest</span><span class="sxs-lookup"><span data-stu-id="2326a-117">How to: Request Data Using the WebRequest Class</span></span>](how-to-request-data-using-the-webrequest-class.md)
- [<span data-ttu-id="2326a-118">Žádosti o data</span><span class="sxs-lookup"><span data-stu-id="2326a-118">Requesting Data</span></span>](requesting-data.md)
