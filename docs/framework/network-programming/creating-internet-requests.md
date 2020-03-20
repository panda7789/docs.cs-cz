---
title: Vytváření internetových žádostí
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
ms.openlocfilehash: 80e3a6bd199691df9391e88d5a64fab5df2a08a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048624"
---
# <a name="creating-internet-requests"></a>Vytváření internetových žádostí
Aplikace <xref:System.Net.WebRequest> vytvořit instance <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> prostřednictvím metody. Jedná se o statickou metodu, která vytvoří třídu odvozenou z **webového požadavku** na základě schématu URI, které jí bylo předáno.  
  
## <a name="web-file-and-ftp-requests"></a>Webové, souborové a FTP požadavky  
 Rozhraní .NET Framework <xref:System.Net.HttpWebRequest> poskytuje třídu, která je odvozena z **WebRequest**, pro zpracování požadavků HTTP a HTTPS. Ve většině případů třída **WebRequest** poskytuje všechny vlastnosti, které potřebujete k vytvoření požadavku; V případě potřeby však můžete přetypovat objekty **WebRequest** vytvořené metodou **WebRequest.Create** do typu **HttpWebRequest** pro přístup k vlastnostem požadavku specifickým pro protokol HTTP. Podobně **httpwebresponse** objekt zpracovává odpovědi z požadavků HTTP a HTTPS. Chcete-li získat přístup k vlastnostem objektu **HttpWebResponse** specifickým pro protokol HTTP, je třeba přetypovat objekty **WebResponse** do typu **HttpWebResponse.**  
  
 Rozhraní .NET Framework <xref:System.Net.FileWebRequest> také <xref:System.Net.FileWebResponse> poskytuje třídy a pro zpracování požadavků na prostředky, které používají schéma IDENTIFIKÁTORURI "file:". Podobně <xref:System.Net.FtpWebRequest> a <xref:System.Net.FtpWebResponse> třídy jsou k dispozici pro zpracování požadavků na prostředky, které používají schéma "ftp:". Pokud váš požadavek je pro prostředek, který používá některý z těchto schémat, můžete použít **WebRequest.Create** metoda získat objekt, se kterým chcete podat požadavek.  
  
 Chcete-li zpracovávat požadavky, které používají jiné protokoly na úrovni aplikace, je třeba implementovat třídy specifické pro protokol odvozené z **WebRequest** a **WebResponse**. Další informace naleznete [v tématu Programming Pluggable Protocols](programming-pluggable-protocols.md).  
  
## <a name="see-also"></a>Viz také

- [Postupy:Vyžádání dat pomocí třídy WebRequest](how-to-request-data-using-the-webrequest-class.md)
- [Žádosti o data](requesting-data.md)
