---
title: FTP – .NET
ms.date: 03/30/2017
helpviewer_keywords:
- FTP
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
ms.openlocfilehash: d945f03077a863d9e1baa6b59fe8a908566aba5a
ms.sourcegitcommit: 90775b20343b6ad831af6f5380f8ab7553abb16b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2019
ms.locfileid: "54186147"
---
# <a name="ftp"></a><span data-ttu-id="77838-102">FTP</span><span class="sxs-lookup"><span data-stu-id="77838-102">FTP</span></span>

<span data-ttu-id="77838-103">Rozhraní .NET Framework poskytuje komplexní podporu pro protokolu FTP se <xref:System.Net.FtpWebRequest> a <xref:System.Net.FtpWebResponse> třídy.</span><span class="sxs-lookup"><span data-stu-id="77838-103">The .NET Framework provides comprehensive support for the FTP protocol with the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes.</span></span> <span data-ttu-id="77838-104">Tyto třídy jsou odvozeny z <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="77838-104">These classes are derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="77838-105">Ve většině případů <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> třídy poskytují vše, co je to nezbytně nutné k požadavku, ale pokud potřebujete přístup k FTP funkcím vystavena jako vlastnosti, můžete přetypovat na tyto třídy <xref:System.Net.FtpWebRequest> nebo <xref:System.Net.FtpWebResponse>.</span><span class="sxs-lookup"><span data-stu-id="77838-105">In most cases, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide all that is necessary to make the request, but if you need access to the FTP-specific features exposed as properties, you can typecast these classes to <xref:System.Net.FtpWebRequest> or <xref:System.Net.FtpWebResponse>.</span></span>

## <a name="examples"></a><span data-ttu-id="77838-106">Příklady</span><span class="sxs-lookup"><span data-stu-id="77838-106">Examples</span></span>

<span data-ttu-id="77838-107">Další informace naleznete v následujících tématech: [Postupy: Stahování souborů přes FTP](how-to-download-files-with-ftp.md), [jak: Nahrávání souborů přes FTP](how-to-upload-files-with-ftp.md), a [jak: Výpisy obsahu adresářů přes FTP](how-to-list-directory-contents-with-ftp.md).</span><span class="sxs-lookup"><span data-stu-id="77838-107">For more information, see the following topics: [How to: Download Files with FTP](how-to-download-files-with-ftp.md), [How to: Upload Files with FTP](how-to-upload-files-with-ftp.md), and [How to: List Directory Contents with FTP](how-to-list-directory-contents-with-ftp.md).</span></span>

## <a name="ftp-and-proxies"></a><span data-ttu-id="77838-108">FTP a proxy servery</span><span class="sxs-lookup"><span data-stu-id="77838-108">FTP and proxies</span></span>

<span data-ttu-id="77838-109">Pokud proxy server (určená <xref:System.Net.FtpWebRequest.Proxy%2A> vlastnost) je proxy server HTTP, pak pouze <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, a <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> příkazy jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="77838-109">If a proxy (specified by the <xref:System.Net.FtpWebRequest.Proxy%2A> property) is an HTTP proxy, then only the <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, and <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> commands are supported.</span></span>

## <a name="see-also"></a><span data-ttu-id="77838-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="77838-110">See also</span></span>

- [<span data-ttu-id="77838-111">Přístup k internetu přes proxy server</span><span class="sxs-lookup"><span data-stu-id="77838-111">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="77838-112">Ukázky programování sítě</span><span class="sxs-lookup"><span data-stu-id="77838-112">Network Programming Samples</span></span>](network-programming-samples.md)
- [<span data-ttu-id="77838-113">Použití aplikačních protokolů</span><span class="sxs-lookup"><span data-stu-id="77838-113">Using Application Protocols</span></span>](using-application-protocols.md)
