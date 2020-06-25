---
title: Vytváření internetových žádostí
description: Zjistěte, jak aplikace vytvářejí instance WebRequest pomocí metody WebRequest. Create, která vytvoří odvozenou třídu založenou na schématu identifikátoru URI, které je předáno.
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
ms.openlocfilehash: 389c7bf5969eca4322aa680a6f28dec0b899709a
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325634"
---
# <a name="create-internet-requests"></a><span data-ttu-id="554b9-103">Vytváření internetových požadavků</span><span class="sxs-lookup"><span data-stu-id="554b9-103">Create internet requests</span></span>

<span data-ttu-id="554b9-104">Aplikace vytváří <xref:System.Net.WebRequest> instance pomocí <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="554b9-104">Applications create <xref:System.Net.WebRequest> instances through the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="554b9-105"><xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>je statická metoda, která vytvoří třídu odvozenou z na <xref:System.Net.WebRequest> základě předaného schématu identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="554b9-105"><xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> is a static method that creates a class derived from <xref:System.Net.WebRequest> based on the URI scheme passed to it.</span></span>  
  
## <a name="web-file-and-ftp-requests"></a><span data-ttu-id="554b9-106">Webové, souborové a FTP požadavky</span><span class="sxs-lookup"><span data-stu-id="554b9-106">Web, file, and FTP requests</span></span>

<span data-ttu-id="554b9-107">.NET Framework poskytuje <xref:System.Net.HttpWebRequest> třídu, která je odvozena z `WebRequest` , pro zpracování požadavků HTTP a HTTPS.</span><span class="sxs-lookup"><span data-stu-id="554b9-107">.NET Framework provides the <xref:System.Net.HttpWebRequest> class, which is derived from `WebRequest`, to handle HTTP and HTTPS requests.</span></span> <span data-ttu-id="554b9-108">Ve většině případů `WebRequest` Třída poskytuje všechny vlastnosti, které potřebujete k vytvoření žádosti. v případě potřeby však můžete přetypovat `WebRequest` objekty vytvořené `WebRequest.Create` metodou na `HttpWebRequest` typ pro přístup k vlastnostem specifickým pro protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="554b9-108">In most cases, the `WebRequest` class provides all the properties you need to make a request; however, if necessary, you can cast `WebRequest` objects created by the `WebRequest.Create` method to the `HttpWebRequest` type to access the HTTP-specific properties of the request.</span></span> <span data-ttu-id="554b9-109">Podobně `HttpWebResponse` objekt zpracovává odpovědi z požadavků HTTP a HTTPS.</span><span class="sxs-lookup"><span data-stu-id="554b9-109">Similarly, the `HttpWebResponse` object handles the responses from HTTP and HTTPS requests.</span></span> <span data-ttu-id="554b9-110">Chcete-li získat přístup k vlastnostem specifického pro protokol HTTP `HttpWebResponse` , je nutné přetypování `WebResponse` objektů na `HttpWebResponse` typ.</span><span class="sxs-lookup"><span data-stu-id="554b9-110">To access the HTTP-specific properties of the `HttpWebResponse` object, you need to cast `WebResponse` objects to the `HttpWebResponse` type.</span></span>  
  
<span data-ttu-id="554b9-111">.NET Framework také poskytuje <xref:System.Net.FileWebRequest> třídy a <xref:System.Net.FileWebResponse> pro zpracování požadavků na prostředky, které používají schéma identifikátoru URI "File:".</span><span class="sxs-lookup"><span data-stu-id="554b9-111">.NET Framework also provides the <xref:System.Net.FileWebRequest> and <xref:System.Net.FileWebResponse> classes to handle requests for resources that use the "file:" URI scheme.</span></span> <span data-ttu-id="554b9-112">Podobně <xref:System.Net.FtpWebRequest> <xref:System.Net.FtpWebResponse> třídy a jsou k dispozici pro zpracování požadavků na prostředky, které používají schéma "FTP:".</span><span class="sxs-lookup"><span data-stu-id="554b9-112">Likewise, the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes are provided to handle requests for resources that use the "ftp:" scheme.</span></span> <span data-ttu-id="554b9-113">Pokud je váš požadavek na prostředek, který používá některé z těchto schémat, můžete použít `WebRequest.Create` metodu k získání objektu, se kterým chcete svůj požadavek vytvořit.</span><span class="sxs-lookup"><span data-stu-id="554b9-113">If your request is for a resource that uses any of these schemes, you can use the `WebRequest.Create` method to obtain an object with which to make your request.</span></span>  
  
<span data-ttu-id="554b9-114">Pro zpracování požadavků, které používají jiné protokoly na úrovni aplikace, implementujte třídy specifické pro protokol odvozené z `WebRequest` a `WebResponse` .</span><span class="sxs-lookup"><span data-stu-id="554b9-114">To handle requests that use other application-level protocols, implement protocol-specific classes derived from `WebRequest` and `WebResponse`.</span></span> <span data-ttu-id="554b9-115">Další informace najdete v tématu [programování protokolů pro připojení](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="554b9-115">For more information, see [Programming Pluggable Protocols](programming-pluggable-protocols.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="554b9-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="554b9-116">See also</span></span>

- [<span data-ttu-id="554b9-117">Postupy:Vyžádání dat pomocí třídy WebRequest</span><span class="sxs-lookup"><span data-stu-id="554b9-117">How to: Request Data Using the WebRequest Class</span></span>](how-to-request-data-using-the-webrequest-class.md)
- [<span data-ttu-id="554b9-118">Žádosti o data</span><span class="sxs-lookup"><span data-stu-id="554b9-118">Requesting Data</span></span>](requesting-data.md)
