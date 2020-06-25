---
title: Vytváření internetových žádostí
description: Zjistěte, jak aplikace vytvářejí instance WebRequest pomocí metody WebRequest. Create, která vytvoří odvozenou třídu založenou na schématu identifikátoru URI, které je předáno.
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
ms.openlocfilehash: 389c7bf5969eca4322aa680a6f28dec0b899709a
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325634"
---
# <a name="create-internet-requests"></a>Vytváření internetových požadavků

Aplikace vytváří <xref:System.Net.WebRequest> instance pomocí <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> metody. <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>je statická metoda, která vytvoří třídu odvozenou z na <xref:System.Net.WebRequest> základě předaného schématu identifikátoru URI.  
  
## <a name="web-file-and-ftp-requests"></a>Webové, souborové a FTP požadavky

.NET Framework poskytuje <xref:System.Net.HttpWebRequest> třídu, která je odvozena z `WebRequest` , pro zpracování požadavků HTTP a HTTPS. Ve většině případů `WebRequest` Třída poskytuje všechny vlastnosti, které potřebujete k vytvoření žádosti. v případě potřeby však můžete přetypovat `WebRequest` objekty vytvořené `WebRequest.Create` metodou na `HttpWebRequest` typ pro přístup k vlastnostem specifickým pro protokol HTTP. Podobně `HttpWebResponse` objekt zpracovává odpovědi z požadavků HTTP a HTTPS. Chcete-li získat přístup k vlastnostem specifického pro protokol HTTP `HttpWebResponse` , je nutné přetypování `WebResponse` objektů na `HttpWebResponse` typ.  
  
.NET Framework také poskytuje <xref:System.Net.FileWebRequest> třídy a <xref:System.Net.FileWebResponse> pro zpracování požadavků na prostředky, které používají schéma identifikátoru URI "File:". Podobně <xref:System.Net.FtpWebRequest> <xref:System.Net.FtpWebResponse> třídy a jsou k dispozici pro zpracování požadavků na prostředky, které používají schéma "FTP:". Pokud je váš požadavek na prostředek, který používá některé z těchto schémat, můžete použít `WebRequest.Create` metodu k získání objektu, se kterým chcete svůj požadavek vytvořit.  
  
Pro zpracování požadavků, které používají jiné protokoly na úrovni aplikace, implementujte třídy specifické pro protokol odvozené z `WebRequest` a `WebResponse` . Další informace najdete v tématu [programování protokolů pro připojení](programming-pluggable-protocols.md).  
  
## <a name="see-also"></a>Viz také

- [Postupy:Vyžádání dat pomocí třídy WebRequest](how-to-request-data-using-the-webrequest-class.md)
- [Žádosti o data](requesting-data.md)
