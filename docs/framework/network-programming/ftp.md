---
title: FTP - .NET
ms.date: 03/30/2017
helpviewer_keywords:
- FTP
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
ms.openlocfilehash: d945f03077a863d9e1baa6b59fe8a908566aba5a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "61642877"
---
# <a name="ftp"></a><span data-ttu-id="ddec4-102">FTP</span><span class="sxs-lookup"><span data-stu-id="ddec4-102">FTP</span></span>

<span data-ttu-id="ddec4-103">Rozhraní .NET Framework poskytuje komplexní podporu protokolu <xref:System.Net.FtpWebRequest> <xref:System.Net.FtpWebResponse> FTP s třídami a.</span><span class="sxs-lookup"><span data-stu-id="ddec4-103">The .NET Framework provides comprehensive support for the FTP protocol with the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes.</span></span> <span data-ttu-id="ddec4-104">Tyto třídy jsou <xref:System.Net.WebRequest> <xref:System.Net.WebResponse>odvozeny od a .</span><span class="sxs-lookup"><span data-stu-id="ddec4-104">These classes are derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="ddec4-105">Ve většině případů <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> a třídy poskytují vše, co je nezbytné k požadavku, ale pokud potřebujete přístup k funkce specifické <xref:System.Net.FtpWebRequest> <xref:System.Net.FtpWebResponse>pro FTP vystaveny jako vlastnosti, můžete typecast tyto třídy nebo .</span><span class="sxs-lookup"><span data-stu-id="ddec4-105">In most cases, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide all that is necessary to make the request, but if you need access to the FTP-specific features exposed as properties, you can typecast these classes to <xref:System.Net.FtpWebRequest> or <xref:System.Net.FtpWebResponse>.</span></span>

## <a name="examples"></a><span data-ttu-id="ddec4-106">Příklady</span><span class="sxs-lookup"><span data-stu-id="ddec4-106">Examples</span></span>

<span data-ttu-id="ddec4-107">Další informace naleznete v následujících [tématech: Postup: Stažení souborů pomocí protokolu FTP](how-to-download-files-with-ftp.md), [Postup: Nahrání souborů pomocí protokolu FTP](how-to-upload-files-with-ftp.md)a [Seznam obsahu adresáře pomocí protokolu FTP](how-to-list-directory-contents-with-ftp.md).</span><span class="sxs-lookup"><span data-stu-id="ddec4-107">For more information, see the following topics: [How to: Download Files with FTP](how-to-download-files-with-ftp.md), [How to: Upload Files with FTP](how-to-upload-files-with-ftp.md), and [How to: List Directory Contents with FTP](how-to-list-directory-contents-with-ftp.md).</span></span>

## <a name="ftp-and-proxies"></a><span data-ttu-id="ddec4-108">FTP a proxy servery</span><span class="sxs-lookup"><span data-stu-id="ddec4-108">FTP and proxies</span></span>

<span data-ttu-id="ddec4-109">Pokud je proxy server <xref:System.Net.FtpWebRequest.Proxy%2A> (určený vlastností) proxy <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>http, jsou podporovány pouze příkazy , <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>a <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> příkazy.</span><span class="sxs-lookup"><span data-stu-id="ddec4-109">If a proxy (specified by the <xref:System.Net.FtpWebRequest.Proxy%2A> property) is an HTTP proxy, then only the <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, and <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> commands are supported.</span></span>

## <a name="see-also"></a><span data-ttu-id="ddec4-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="ddec4-110">See also</span></span>

- [<span data-ttu-id="ddec4-111">Přístup k internetu přes proxy server</span><span class="sxs-lookup"><span data-stu-id="ddec4-111">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="ddec4-112">Ukázky programování sítě</span><span class="sxs-lookup"><span data-stu-id="ddec4-112">Network Programming Samples</span></span>](network-programming-samples.md)
- [<span data-ttu-id="ddec4-113">Použití aplikačních protokolů</span><span class="sxs-lookup"><span data-stu-id="ddec4-113">Using Application Protocols</span></span>](using-application-protocols.md)
