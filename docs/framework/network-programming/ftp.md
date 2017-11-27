---
title: FTP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: FTP
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d7b169a6de494d10fa332ebf5f2aa315ae69653a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ftp"></a><span data-ttu-id="845ce-102">FTP</span><span class="sxs-lookup"><span data-stu-id="845ce-102">FTP</span></span>
<span data-ttu-id="845ce-103">Rozhraní .NET Framework poskytuje komplexní podporu pro protokol FTP s <xref:System.Net.FtpWebRequest> a <xref:System.Net.FtpWebResponse> třídy.</span><span class="sxs-lookup"><span data-stu-id="845ce-103">The .NET Framework provides comprehensive support for the FTP protocol with the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes.</span></span> <span data-ttu-id="845ce-104">Tyto třídy jsou odvozeny od <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="845ce-104">These classes are derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="845ce-105">Ve většině případů <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> třídy poskytují všechno, co je potřeba provést žádost, ale pokud budete potřebovat přístup k FTP funkcím vystaveny jako vlastnosti, můžete tyto třídy k přiřazení typu <xref:System.Net.FtpWebRequest> nebo <xref:System.Net.FtpWebResponse>.</span><span class="sxs-lookup"><span data-stu-id="845ce-105">In most cases, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide all that is necessary to make the request, but if you need access to the FTP-specific features exposed as properties, you can typecast these classes to <xref:System.Net.FtpWebRequest> or <xref:System.Net.FtpWebResponse>.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="845ce-106">Příklady</span><span class="sxs-lookup"><span data-stu-id="845ce-106">Examples</span></span>  
 <span data-ttu-id="845ce-107">Další informace naleznete v následujících tématech: [postup: stahovat soubory s FTP](../../../docs/framework/network-programming/how-to-download-files-with-ftp.md), [postup: nahrání souborů s FTP](../../../docs/framework/network-programming/how-to-upload-files-with-ftp.md), a [postup: obsah adresáře seznamu s FTP](../../../docs/framework/network-programming/how-to-list-directory-contents-with-ftp.md).</span><span class="sxs-lookup"><span data-stu-id="845ce-107">For more information, see the following topics: [How to: Download Files with FTP](../../../docs/framework/network-programming/how-to-download-files-with-ftp.md), [How to: Upload Files with FTP](../../../docs/framework/network-programming/how-to-upload-files-with-ftp.md), and [How to: List Directory Contents with FTP](../../../docs/framework/network-programming/how-to-list-directory-contents-with-ftp.md).</span></span>  
  
## <a name="ftp-and-proxies"></a><span data-ttu-id="845ce-108">FTP a proxy servery</span><span class="sxs-lookup"><span data-stu-id="845ce-108">FTP and proxies</span></span>  
 <span data-ttu-id="845ce-109">Pokud proxy server (určená elementem <xref:System.Net.FtpWebRequest.Proxy%2A> vlastnost) je proxy server HTTP, pak pouze <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, a <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> jsou podporované příkazy.</span><span class="sxs-lookup"><span data-stu-id="845ce-109">If a proxy (specified by the <xref:System.Net.FtpWebRequest.Proxy%2A> property) is an HTTP proxy, then only the <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, and <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> commands are supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="845ce-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="845ce-110">See Also</span></span>  
 [<span data-ttu-id="845ce-111">Přístup k Internetu prostřednictvím proxy serveru</span><span class="sxs-lookup"><span data-stu-id="845ce-111">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [<span data-ttu-id="845ce-112">Síťové programování ukázky</span><span class="sxs-lookup"><span data-stu-id="845ce-112">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)  
 [<span data-ttu-id="845ce-113">Ukázka technologie FTP klienta.</span><span class="sxs-lookup"><span data-stu-id="845ce-113">FTP Client Technology Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=179557)  
 [<span data-ttu-id="845ce-114">Ukázka Průzkumníka FTP technologie</span><span class="sxs-lookup"><span data-stu-id="845ce-114">FTP Explorer Technology Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=179569)  
 [<span data-ttu-id="845ce-115">Pomocí protokolů aplikací</span><span class="sxs-lookup"><span data-stu-id="845ce-115">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
