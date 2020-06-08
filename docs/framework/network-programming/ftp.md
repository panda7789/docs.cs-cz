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
# <a name="ftp"></a>FTP

.NET Framework poskytuje komplexní podporu protokolu FTP s <xref:System.Net.FtpWebRequest> <xref:System.Net.FtpWebResponse> třídami a. Tyto třídy jsou odvozeny z <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> . Ve většině případů <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> třídy a poskytují vše potřebné k provedení požadavku, ale pokud potřebujete přístup k funkcím specifickým pro FTP, které jsou vystaveny jako vlastnosti, můžete tyto třídy přetypovat do <xref:System.Net.FtpWebRequest> nebo <xref:System.Net.FtpWebResponse> .

## <a name="examples"></a>Příklady

Další informace najdete v následujících tématech: [Postupy: stahování souborů pomocí FTP](how-to-download-files-with-ftp.md), [Postupy: nahrání souborů s protokolem FTP](how-to-upload-files-with-ftp.md)a [Postupy: výpis obsahu adresáře pomocí protokolu FTP](how-to-list-directory-contents-with-ftp.md).

## <a name="ftp-and-proxies"></a>FTP a proxy

Je-li proxy server (určený <xref:System.Net.FtpWebRequest.Proxy%2A> vlastností) proxy serveru http, <xref:System.Net.WebRequestMethods.Ftp.DownloadFile> <xref:System.Net.WebRequestMethods.Ftp.ListDirectory> <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> jsou podporovány pouze příkazy, a.

## <a name="see-also"></a>Viz také:

- [Přístup k internetu přes proxy server](accessing-the-internet-through-a-proxy.md)
- [Ukázky programování sítě](network-programming-samples.md)
- [Použití aplikačních protokolů](using-application-protocols.md)
