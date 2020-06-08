---
title: Vytváření internetových žádostí
description: Přečtěte si, jak aplikace vytvářejí instance WebRequest prostřednictvím WebRequest. Create, statické metody, která vytvoří odvozenou třídu založenou na schématu identifikátoru URI, které je předáno.
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
ms.openlocfilehash: 598ef9d44737ef6b33af833cbfb7788170165588
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502623"
---
# <a name="creating-internet-requests"></a>Vytváření internetových žádostí
Aplikace vytváří <xref:System.Net.WebRequest> instance pomocí <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> metody. Toto je statická metoda, která vytvoří třídu odvozenou od **WebRequest** na základě předaného schématu identifikátoru URI.  
  
## <a name="web-file-and-ftp-requests"></a>Webové, souborové a FTP požadavky  
 .NET Framework poskytuje <xref:System.Net.HttpWebRequest> třídu, která je odvozena z **WebRequest**, pro zpracování požadavků HTTP a HTTPS. Ve většině případů třída **WebRequest** poskytuje všechny vlastnosti, které potřebujete k vytvoření žádosti; v případě potřeby však můžete přetypovat objekty **WebRequest** vytvořené metodou **WebRequest. Create** pro typ **HttpWebRequest** pro přístup k vlastnostem specifickým pro protokol HTTP. Podobně objekt **HttpWebResponse** zpracovává odpovědi z požadavků HTTP a HTTPS. Chcete-li získat přístup k vlastnostem objektu **HttpWebResponse** specifickým pro protokol HTTP, je třeba přetypovat objekty **WebResponse** na typ **HttpWebResponse** .  
  
 .NET Framework také poskytuje <xref:System.Net.FileWebRequest> <xref:System.Net.FileWebResponse> třídy a pro zpracování požadavků na prostředky, které používají schéma identifikátoru URI "File:". Podobně <xref:System.Net.FtpWebRequest> <xref:System.Net.FtpWebResponse> třídy a jsou k dispozici pro zpracování požadavků na prostředky, které používají schéma "FTP:". Pokud je váš požadavek na prostředek, který používá některé z těchto schémat, můžete použít metodu **WebRequest. Create** k získání objektu, se kterým se má váš požadavek vytvořit.  
  
 Pro zpracování požadavků, které používají jiné protokoly na úrovni aplikace, je nutné implementovat třídy specifické pro protokol odvozené od **WebRequest** a **WebResponse**. Další informace najdete v tématu [programování protokolů pro připojení](programming-pluggable-protocols.md).  
  
## <a name="see-also"></a>Viz také:

- [Postupy:Vyžádání dat pomocí třídy WebRequest](how-to-request-data-using-the-webrequest-class.md)
- [Žádosti o data](requesting-data.md)
