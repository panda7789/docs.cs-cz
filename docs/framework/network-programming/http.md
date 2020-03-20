---
title: HTTP
ms.date: 03/30/2017
helpviewer_keywords:
- protocols, HTTP
- sending data, HTTP
- HttpWebResponse class, sending and receiving data
- HTTP
- receiving data, HTTP
- application protocols, HTTP
- Internet, HTTP
- network resources, HTTP
- HTTP, about HTTP
- HttpWebRequest class, sending and receiving data
ms.assetid: 985fe5d8-eb71-4024-b361-41fbdc1618d8
ms.openlocfilehash: c8c799a50e5d63bbf411c338eb9e93f85a942bb0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048002"
---
# <a name="http"></a>HTTP
Rozhraní .NET Framework poskytuje komplexní podporu pro protokol HTTP, který tvoří většinu <xref:System.Net.HttpWebRequest> <xref:System.Net.HttpWebResponse> veškerého internetového provozu s třídami a. Tyto třídy, <xref:System.Net.WebRequest> odvozené od a <xref:System.Net.WebResponse>, jsou <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> vráceny ve výchozím nastavení vždy, když statická metoda narazí na identifikátor URI začínající "http" nebo "https". Ve většině případů **třídy WebRequest** a **WebResponse** poskytují vše, co je nezbytné k tomu, aby požadavek, ale pokud potřebujete přístup k funkcím specifickým pro protokol HTTP vystavených jako vlastnosti, můžete tyto třídy přetypovat na **HttpWebRequest** nebo **HttpWebResponse**.  
  
 **HttpWebRequest** a **HttpWebResponse** zapouzdřují standardní transakci požadavku a odpovědi HTTP a poskytují přístup ke společným hlavičkám HTTP. Tyto třídy také podporují většinu funkcí protokolu HTTP 1.1, včetně pipeliningu, odesílání a přijímání dat v blocích, ověřování, předběžnéověřování, šifrování, podporu proxy serveru, ověření certifikátu serveru a správy připojení. Vlastní záhlaví a záhlaví, která nejsou poskytována prostřednictvím vlastností, mohou být uložena v vlastnosti **Záhlaví** a přístupná k nim.  
  
 **HttpWebRequest** je výchozí třída používaná **webovou aplikací A** před předáním identifikátoru URI metodě **WebRequest.Create** nemusí být registrována.  
  
 Aplikaci můžete automaticky sledovat přesměrování HTTP nastavením vlastnosti <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> na **hodnotu true** (výchozí). Aplikace přesměruje požadavky a <xref:System.Net.HttpWebResponse.ResponseUri%2A> vlastnost **HttpWebResponse** bude obsahovat skutečný webový prostředek, který odpověděl na požadavek. Pokud nastavíte **AllowAutoRedirect** na **false**, aplikace musí být schopen zpracovat přesměrování jako chyby protokolu HTTP.  
  
 Aplikace obdrží chyby protokolu <xref:System.Net.WebException> HTTP <xref:System.Net.WebException.Status%2A> zachycením a s nastavenou na <xref:System.Net.WebExceptionStatus>. Vlastnost <xref:System.Net.WebException.Response%2A> obsahuje **webovou odezvu** odeslanou serverem a označuje skutečnou chybu PROTOKOLU HTTP, která byla zjištěna.  
  
## <a name="see-also"></a>Viz také

- [Přístup k internetu přes proxy server](accessing-the-internet-through-a-proxy.md)
- [Použití aplikačních protokolů](using-application-protocols.md)
- [Postupy: Přístup k vlastnostem specifickým pro HTTP](how-to-access-http-specific-properties.md)
