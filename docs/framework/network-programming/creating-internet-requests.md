---
title: Vytváření žádostí o Internetu
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 8ebe861fc2de8b21ee766e52dada1eec10169f16
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="creating-internet-requests"></a>Vytváření žádostí o Internetu
Vytvoření aplikace <xref:System.Net.WebRequest> instance prostřednictvím <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> metoda. Toto je statickou metodu, která vytvoří třídy odvozené od **WebRequest** založené na schéma identifikátoru URI do ní předán.  
  
## <a name="web-file-and-ftp-requests"></a>Webové aplikace, soubor a požadavky protokolu FTP  
 Poskytuje rozhraní .NET Framework <xref:System.Net.HttpWebRequest> třídy, která je odvozená od **WebRequest**pro zpracování požadavků HTTP a HTTPS. Ve většině případů **WebRequest** třída poskytuje všechny vlastnosti, které musíte provést žádost o; však v případě potřeby můžete převést **WebRequest** objekty vytvořené **WebRequest.Create**  metodu **HttpWebRequest** typ, který má přístup k protokolu HTTP specifické vlastnosti požadavku. Podobně **HttpWebResponse** objekt zpracovává odpovědi z žádostí HTTP a HTTPS. Pro přístup k vlastnosti specifické pro protokol HTTP **HttpWebResponse** objektu, musíte převést **WebResponse** objekty ke **HttpWebResponse** typu.  
  
 Také poskytuje rozhraní .NET Framework <xref:System.Net.FileWebRequest> a <xref:System.Net.FileWebResponse> třídy pro zpracování požadavků na zdroje, které používají "souboru:" schéma identifikátoru URI. Podobně <xref:System.Net.FtpWebRequest> a <xref:System.Net.FtpWebResponse> třídy jsou k dispozici pro zpracování požadavků na zdroje, které používají "ftp:" schéma. Pokud vaše žádost je pro prostředek, který používá některé z těchto režimů, můžete použít **WebRequest.Create** metoda získat objekt, ke které má být zkontrolujte vaši žádost.  
  
 Pro zpracování žádostí, které používají jiné protokoly na úrovni aplikace, potřebujete implementovat specifické třídy odvozené od **WebRequest** a **WebResponse**. Další informace najdete v tématu [programování modulární protokoly](../../../docs/framework/network-programming/programming-pluggable-protocols.md).  
  
## <a name="see-also"></a>Viz také  
 [Postupy:Vyžádání dat pomocí třídy WebRequest](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)  
 [Žádosti o data](../../../docs/framework/network-programming/requesting-data.md)
