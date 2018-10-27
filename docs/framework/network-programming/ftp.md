---
title: FTP
ms.date: 03/30/2017
helpviewer_keywords:
- FTP
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
ms.openlocfilehash: 0f35cb5c106d041a771d17a6e528cbbc1d38042b
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187670"
---
# <a name="ftp"></a><span data-ttu-id="2c0d2-102">FTP</span><span class="sxs-lookup"><span data-stu-id="2c0d2-102">FTP</span></span>
<span data-ttu-id="2c0d2-103">Rozhraní .NET Framework poskytuje komplexní podporu pro protokolu FTP se <xref:System.Net.FtpWebRequest> a <xref:System.Net.FtpWebResponse> třídy.</span><span class="sxs-lookup"><span data-stu-id="2c0d2-103">The .NET Framework provides comprehensive support for the FTP protocol with the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes.</span></span> <span data-ttu-id="2c0d2-104">Tyto třídy jsou odvozeny z <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="2c0d2-104">These classes are derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="2c0d2-105">Ve většině případů <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> třídy poskytují vše, co je to nezbytně nutné k požadavku, ale pokud potřebujete přístup k FTP funkcím vystavena jako vlastnosti, můžete přetypovat na tyto třídy <xref:System.Net.FtpWebRequest> nebo <xref:System.Net.FtpWebResponse>.</span><span class="sxs-lookup"><span data-stu-id="2c0d2-105">In most cases, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide all that is necessary to make the request, but if you need access to the FTP-specific features exposed as properties, you can typecast these classes to <xref:System.Net.FtpWebRequest> or <xref:System.Net.FtpWebResponse>.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="2c0d2-106">Příklady</span><span class="sxs-lookup"><span data-stu-id="2c0d2-106">Examples</span></span>  
 <span data-ttu-id="2c0d2-107">Další informace naleznete v následujících tématech: [postupy: stahování souborů přes FTP](../../../docs/framework/network-programming/how-to-download-files-with-ftp.md), [postupy: nahrávání souborů s využitím protokolu FTP](../../../docs/framework/network-programming/how-to-upload-files-with-ftp.md), a [postupy: výpis obsahu adresáře s využitím protokolu FTP](../../../docs/framework/network-programming/how-to-list-directory-contents-with-ftp.md).</span><span class="sxs-lookup"><span data-stu-id="2c0d2-107">For more information, see the following topics: [How to: Download Files with FTP](../../../docs/framework/network-programming/how-to-download-files-with-ftp.md), [How to: Upload Files with FTP](../../../docs/framework/network-programming/how-to-upload-files-with-ftp.md), and [How to: List Directory Contents with FTP](../../../docs/framework/network-programming/how-to-list-directory-contents-with-ftp.md).</span></span>  
  
## <a name="ftp-and-proxies"></a><span data-ttu-id="2c0d2-108">FTP a proxy servery</span><span class="sxs-lookup"><span data-stu-id="2c0d2-108">FTP and proxies</span></span>  
 <span data-ttu-id="2c0d2-109">Pokud proxy server (určená <xref:System.Net.FtpWebRequest.Proxy%2A> vlastnost) je proxy server HTTP, pak pouze <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, a <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> příkazy jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="2c0d2-109">If a proxy (specified by the <xref:System.Net.FtpWebRequest.Proxy%2A> property) is an HTTP proxy, then only the <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, and <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> commands are supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c0d2-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="2c0d2-110">See Also</span></span>  
 [<span data-ttu-id="2c0d2-111">Přístup k internetu přes proxy server</span><span class="sxs-lookup"><span data-stu-id="2c0d2-111">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [<span data-ttu-id="2c0d2-112">Ukázky programování sítě</span><span class="sxs-lookup"><span data-stu-id="2c0d2-112">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)  
 [<span data-ttu-id="2c0d2-113">Ukázka technologie klienta FTP</span><span class="sxs-lookup"><span data-stu-id="2c0d2-113">FTP Client Technology Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=179557)  
 [<span data-ttu-id="2c0d2-114">Ukázka technologie Průzkumníka serveru FTP</span><span class="sxs-lookup"><span data-stu-id="2c0d2-114">FTP Explorer Technology Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=179569)  
 [<span data-ttu-id="2c0d2-115">Použití aplikačních protokolů</span><span class="sxs-lookup"><span data-stu-id="2c0d2-115">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
