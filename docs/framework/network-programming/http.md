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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048002"
---
# <a name="http"></a>HTTP
.NET Framework poskytuje komplexní podporu protokolu HTTP, která tvoří většinu všech internetových přenosů s <xref:System.Net.HttpWebRequest> třídami a. <xref:System.Net.HttpWebResponse> Tyto třídy, které jsou <xref:System.Net.WebRequest> odvozeny z a <xref:System.Net.WebResponse>, jsou ve výchozím nastavení vráceny <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> pokaždé, když statická metoda zjistí identifikátor URI začínající řetězcem "http" nebo "https". Ve většině případů třídy **WebRequest** a **WebResponse** poskytují vše potřebné k provedení požadavku, ale pokud potřebujete přístup k funkcím specifickým pro protokol HTTP, které jsou vystaveny jako vlastnosti, můžete tyto třídy přetypovat na **HttpWebRequest** nebo **HttpWebResponse**.  
  
 **HttpWebRequest** a **HttpWebResponse** zapouzdřují standardní transakce požadavků a odpovědí HTTP a poskytují přístup k běžným hlavičkám http. Tyto třídy také podporují většinu funkcí protokolu HTTP 1,1, včetně přesměrování, odesílání a přijímání dat v blocích, ověřování, předběžném ověřování, šifrování, podpora proxy serveru, ověřování certifikátů serveru a správu připojení. Vlastní hlavičky a hlavičky neposkytované prostřednictvím vlastností lze ukládat v a získávat prostřednictvím vlastnosti **Headers** .  
  
 **HttpWebRequest** je výchozí třída, kterou používá **WebRequest** a není nutné ji registrovat předtím, než můžete předat identifikátor URI metodě **WebRequest. Create** .  
  
 Aplikaci můžete nastavit tak, aby se automaticky sledovala přesměrování HTTP nastavením <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> vlastnosti na **hodnotu true** (výchozí). Aplikace bude přesměrovat požadavky a <xref:System.Net.HttpWebResponse.ResponseUri%2A> vlastnost **HttpWebResponse** bude obsahovat skutečný webový prostředek, který odpověděl na požadavek. Pokud nastavíte **AllowAutoRedirect** na **false**, aplikace musí být schopná zpracovat přesměrování jako chyby protokolu HTTP.  
  
 Aplikace dostávají chyby protokolu HTTP zachycením <xref:System.Net.WebException> <xref:System.Net.WebException.Status%2A> s nastavením na <xref:System.Net.WebExceptionStatus>. Vlastnost obsahuje WebResponse odeslanou serverem a indikuje, že došlo k skutečné chybě HTTP. <xref:System.Net.WebException.Response%2A>  
  
## <a name="see-also"></a>Viz také:

- [Přístup k internetu přes proxy server](accessing-the-internet-through-a-proxy.md)
- [Použití aplikačních protokolů](using-application-protocols.md)
- [Postupy: Přístup k vlastnostem specifickým pro protokol HTTP](how-to-access-http-specific-properties.md)
