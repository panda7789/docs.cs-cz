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
# <a name="ftp"></a>FTP
Rozhraní .NET Framework poskytuje komplexní podporu pro protokol FTP s <xref:System.Net.FtpWebRequest> a <xref:System.Net.FtpWebResponse> třídy. Tyto třídy jsou odvozeny od <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse>. Ve většině případů <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> třídy poskytují všechno, co je potřeba provést žádost, ale pokud budete potřebovat přístup k FTP funkcím vystaveny jako vlastnosti, můžete tyto třídy k přiřazení typu <xref:System.Net.FtpWebRequest> nebo <xref:System.Net.FtpWebResponse>.  
  
## <a name="examples"></a>Příklady  
 Další informace naleznete v následujících tématech: [postup: stahovat soubory s FTP](../../../docs/framework/network-programming/how-to-download-files-with-ftp.md), [postup: nahrání souborů s FTP](../../../docs/framework/network-programming/how-to-upload-files-with-ftp.md), a [postup: obsah adresáře seznamu s FTP](../../../docs/framework/network-programming/how-to-list-directory-contents-with-ftp.md).  
  
## <a name="ftp-and-proxies"></a>FTP a proxy servery  
 Pokud proxy server (určená elementem <xref:System.Net.FtpWebRequest.Proxy%2A> vlastnost) je proxy server HTTP, pak pouze <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, a <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> jsou podporované příkazy.  
  
## <a name="see-also"></a>Viz také  
 [Přístup k Internetu prostřednictvím proxy serveru](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [Síťové programování ukázky](../../../docs/framework/network-programming/network-programming-samples.md)  
 [Ukázka technologie FTP klienta.](http://go.microsoft.com/fwlink/?LinkID=179557)  
 [Ukázka Průzkumníka FTP technologie](http://go.microsoft.com/fwlink/?LinkID=179569)  
 [Pomocí protokolů aplikací](../../../docs/framework/network-programming/using-application-protocols.md)
