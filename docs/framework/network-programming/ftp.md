---
title: FTP – .NET
description: Přečtěte si o komplexní podpoře protokolu FTP, který .NET Framework poskytuje pomocí tříd FtpWebRequest a FtpWebResponse.
ms.date: 03/30/2017
helpviewer_keywords:
- FTP
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
ms.openlocfilehash: d21ca43cd1041df358dc5e2add9560fb33e85d83
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502584"
---
# <a name="ftp"></a><span data-ttu-id="e2c07-103">FTP</span><span class="sxs-lookup"><span data-stu-id="e2c07-103">FTP</span></span>

<span data-ttu-id="e2c07-104">.NET Framework poskytuje komplexní podporu protokolu FTP s <xref:System.Net.FtpWebRequest> <xref:System.Net.FtpWebResponse> třídami a.</span><span class="sxs-lookup"><span data-stu-id="e2c07-104">The .NET Framework provides comprehensive support for the FTP protocol with the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes.</span></span> <span data-ttu-id="e2c07-105">Tyto třídy jsou odvozeny z <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> .</span><span class="sxs-lookup"><span data-stu-id="e2c07-105">These classes are derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="e2c07-106">Ve většině případů <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> třídy a poskytují vše potřebné k provedení požadavku, ale pokud potřebujete přístup k funkcím specifickým pro FTP, které jsou vystaveny jako vlastnosti, můžete tyto třídy přetypovat do <xref:System.Net.FtpWebRequest> nebo <xref:System.Net.FtpWebResponse> .</span><span class="sxs-lookup"><span data-stu-id="e2c07-106">In most cases, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide all that is necessary to make the request, but if you need access to the FTP-specific features exposed as properties, you can typecast these classes to <xref:System.Net.FtpWebRequest> or <xref:System.Net.FtpWebResponse>.</span></span>

## <a name="examples"></a><span data-ttu-id="e2c07-107">Příklady</span><span class="sxs-lookup"><span data-stu-id="e2c07-107">Examples</span></span>

<span data-ttu-id="e2c07-108">Další informace najdete v následujících tématech: [Postupy: stahování souborů pomocí FTP](how-to-download-files-with-ftp.md), [Postupy: nahrání souborů s protokolem FTP](how-to-upload-files-with-ftp.md)a [Postupy: výpis obsahu adresáře pomocí protokolu FTP](how-to-list-directory-contents-with-ftp.md).</span><span class="sxs-lookup"><span data-stu-id="e2c07-108">For more information, see the following topics: [How to: Download Files with FTP](how-to-download-files-with-ftp.md), [How to: Upload Files with FTP](how-to-upload-files-with-ftp.md), and [How to: List Directory Contents with FTP](how-to-list-directory-contents-with-ftp.md).</span></span>

## <a name="ftp-and-proxies"></a><span data-ttu-id="e2c07-109">FTP a proxy</span><span class="sxs-lookup"><span data-stu-id="e2c07-109">FTP and proxies</span></span>

<span data-ttu-id="e2c07-110">Je-li proxy server (určený <xref:System.Net.FtpWebRequest.Proxy%2A> vlastností) proxy serveru http, <xref:System.Net.WebRequestMethods.Ftp.DownloadFile> <xref:System.Net.WebRequestMethods.Ftp.ListDirectory> <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> jsou podporovány pouze příkazy, a.</span><span class="sxs-lookup"><span data-stu-id="e2c07-110">If a proxy (specified by the <xref:System.Net.FtpWebRequest.Proxy%2A> property) is an HTTP proxy, then only the <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, and <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> commands are supported.</span></span>

## <a name="see-also"></a><span data-ttu-id="e2c07-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e2c07-111">See also</span></span>

- [<span data-ttu-id="e2c07-112">Přístup k internetu přes proxy server</span><span class="sxs-lookup"><span data-stu-id="e2c07-112">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="e2c07-113">Ukázky programování sítě</span><span class="sxs-lookup"><span data-stu-id="e2c07-113">Network Programming Samples</span></span>](network-programming-samples.md)
- [<span data-ttu-id="e2c07-114">Použití aplikačních protokolů</span><span class="sxs-lookup"><span data-stu-id="e2c07-114">Using Application Protocols</span></span>](using-application-protocols.md)
