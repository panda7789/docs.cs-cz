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
# <a name="ftp"></a>FTP

Rozhraní .NET Framework poskytuje komplexní podporu protokolu <xref:System.Net.FtpWebRequest> <xref:System.Net.FtpWebResponse> FTP s třídami a. Tyto třídy jsou <xref:System.Net.WebRequest> <xref:System.Net.WebResponse>odvozeny od a . Ve většině případů <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> a třídy poskytují vše, co je nezbytné k požadavku, ale pokud potřebujete přístup k funkce specifické <xref:System.Net.FtpWebRequest> <xref:System.Net.FtpWebResponse>pro FTP vystaveny jako vlastnosti, můžete typecast tyto třídy nebo .

## <a name="examples"></a>Příklady

Další informace naleznete v následujících [tématech: Postup: Stažení souborů pomocí protokolu FTP](how-to-download-files-with-ftp.md), [Postup: Nahrání souborů pomocí protokolu FTP](how-to-upload-files-with-ftp.md)a [Seznam obsahu adresáře pomocí protokolu FTP](how-to-list-directory-contents-with-ftp.md).

## <a name="ftp-and-proxies"></a>FTP a proxy servery

Pokud je proxy server <xref:System.Net.FtpWebRequest.Proxy%2A> (určený vlastností) proxy <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>http, jsou podporovány pouze příkazy , <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>a <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> příkazy.

## <a name="see-also"></a>Viz také

- [Přístup k internetu přes proxy server](accessing-the-internet-through-a-proxy.md)
- [Ukázky programování sítě](network-programming-samples.md)
- [Použití aplikačních protokolů](using-application-protocols.md)
