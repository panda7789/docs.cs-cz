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
ms.openlocfilehash: abbb02b7bd22c4b301c5565037f55aa1019fc3ce
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170596"
---
# <a name="http"></a>HTTP
Rozhraní .NET Framework poskytuje komplexní podporu pro protokol HTTP, které tvoří většinou všechny přenosy z Internetu, se <xref:System.Net.HttpWebRequest> a <xref:System.Net.HttpWebResponse> třídy. Tyto třídy odvozené z <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse>, jsou vráceny ve výchozím nastavení pokaždé, když se statickou metodu <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> zaznamená identifikátor URI začínající řetězcem "http" nebo "https". Ve většině případů **WebRequest** a **WebResponse** třídy poskytují všechny možnosti, které je nezbytné k odeslání požadavku, ale pokud potřebujete přístup k funkcím specifickým pro HTTP jako vlastnosti, můžete přetypovat Tyto třídy **HttpWebRequest** nebo **HttpWebResponse**.  
  
 **HttpWebRequest** a **HttpWebResponse** zapouzdřují standardní transakce požadavku a odpovědi HTTP a poskytují přístup k společné hlavičky HTTP. Tyto třídy také podporují většinu funkcí protokolu HTTP 1.1, včetně paralelní zpracování, odesílání a přijímání dat do bloků dat, ověřování, předběžné ověření, šifrování, podpora proxy, ověření certifikátu serveru a připojení správy. Vlastní hlavičky a není k dispozici prostřednictvím vlastností můžete uložené v a získat přístup prostřednictvím **záhlaví** vlastnost.  
  
 **HttpWebRequest** je výchozí třídou používané **WebRequest** a nemusí být před předáním identifikátor URI pro zaregistrovaný **WebRequest.Create** metoda.  
  
 Provedete aplikace následovat i přesměrování HTTP automaticky tak, že nastavíte <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> vlastnost **true** (výchozí). Aplikace bude přesměrovávat žádosti a <xref:System.Net.HttpWebResponse.ResponseUri%2A> vlastnost **HttpWebResponse** bude obsahovat skutečná webového prostředku, který odpověděl na požadavek. Pokud nastavíte **AllowAutoRedirect** k **false**, vaše aplikace musí být schopný zvládnout přesměrování jako chyby protokolu HTTP.  
  
 Aplikace zobrazí chyby protokolu HTTP pomocí zachycování <xref:System.Net.WebException> s <xref:System.Net.WebException.Status%2A> nastavena na <xref:System.Net.WebExceptionStatus>. <xref:System.Net.WebException.Response%2A> Obsahuje vlastnost **WebResponse** odeslané serverem a označuje skutečné došlo k chybě protokolu HTTP.  
  
## <a name="see-also"></a>Viz také:

- [Přístup k internetu přes proxy server](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
- [Použití aplikačních protokolů](../../../docs/framework/network-programming/using-application-protocols.md)
- [Postupy: Přístup k vlastnostem specifickým pro HTTP](../../../docs/framework/network-programming/how-to-access-http-specific-properties.md)
