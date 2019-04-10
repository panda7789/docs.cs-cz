---
title: Odvození z odpovědi WebResponse
ms.date: 03/30/2017
helpviewer_keywords:
- Deriving from WebResponse
ms.assetid: f11d4866-a199-4087-9306-a5a4c18b13db
ms.openlocfilehash: 6bdb21b8aaf8deb39e3abd68a69a9a5a10247e6f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226042"
---
# <a name="deriving-from-webresponse"></a>Odvození z odpovědi WebResponse
<xref:System.Net.WebResponse> Třída je abstraktní základní třídu, která poskytuje základní metody a vlastnosti pro vytvoření odpovědi specifické pro protokol, který odpovídá modelu připojitelných protokolů rozhraní .NET Framework. Aplikace, které používají <xref:System.Net.WebRequest> třídy požadovat data ze zdroje dostávat odpovědi v **WebResponse**. Konkrétní **WebResponse** následníků musí implementovat abstraktní členové **WebResponse** třídy.  
  
 Přidružené **WebRequest** musíte vytvořit třídu **WebResponse** následníky. Například <xref:System.Net.HttpWebResponse> pouze jako výsledek volání se vytvářejí instance <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> nebo <xref:System.Net.HttpWebRequest.EndGetResponse%2A?displayProperty=nameWithType>. Každý **WebResponse** obsahuje výsledek požadavku na prostředek a není určena pro znovu použít.  
  
## <a name="contentlength-property"></a>Vlastnost ContentLength  
 <xref:System.Net.WebResponse.ContentLength%2A> Vlastnost určuje počet bajtů dat, které jsou k dispozici z datový proud vrácený <xref:System.Net.WebResponse.GetResponseStream%2A> metody. **ContentLength** vlastnost nenaznačuje, že počet bajtů informace záhlaví nebo metadata vrácená serverem; značí pouze počet bajtů dat v požadované vlastní prostředek.  
  
## <a name="contenttype-property"></a>ContentType Property  
 <xref:System.Net.WebResponse.ContentType%2A> Vlastnost poskytuje všechny speciální informace, že váš protokol vyžaduje, abyste odeslat klientovi, který identifikuje typ obsahu je odesláno serverem. Obvykle je to typ obsahu MIME vrácená data.  
  
## <a name="headers-property"></a>Vlastnost záhlaví  
 <xref:System.Net.WebResponse.Headers%2A> Vlastnost obsahuje libovolnou kolekci dvojic název/hodnota metadat přidružený k odpovědi. Veškerá metadata, vyžaduje protokol, který může být vyjádřena jako dvojice název/hodnota může být součástí **záhlaví** vlastnost.  
  
 Není nutné použít **záhlaví** vlastnost použít hlavičku metadat. Metadata specifická pro protokol může být vystavena jako vlastnosti; například <xref:System.Net.HttpWebResponse.LastModified%2A?displayProperty=nameWithType> zpřístupňuje vlastnost **Last-Modified** hlavičky protokolu HTTP. Pokud zveřejňujete hlavičku metadat jako vlastnost, by nemělo umožňovat stejnou vlastnost používat **záhlaví** vlastnost.  
  
## <a name="responseuri-property"></a>ResponseUri Property  
 <xref:System.Net.WebResponse.ResponseUri%2A> Vlastnost obsahuje identifikátor URI prostředku, která ve skutečnosti k dispozici odpověď. Pro protokoly, které nepodporují přesměrování **ResponseUri** budou stejné jako <xref:System.Net.WebRequest.RequestUri%2A> vlastnost **WebRequest** , který je vytvořen odpověď. Pokud protokol podporuje přesměrování požadavku, **ResponseUri** bude obsahovat identifikátor URI odpovědi.  
  
## <a name="close-method"></a>Close – metoda  
 <xref:System.Net.WebResponse.Close%2A> Metoda zavře připojení podle požadavků a odpovědí a vyčistí prostředky využívané třídou odpovědi. **Zavřít** metoda zavře všechny instance služby stream používá odpověď, ale nevyvolá výjimku, pokud datový proud odpovědí dříve zavřel volání <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metody.  
  
## <a name="getresponsestream-method"></a>Metodu GetResponseStream  
 <xref:System.Net.WebResponse.GetResponseStream%2A> Metoda vrátí datového proudu s odpovědí z požadovaný prostředek. Datový proud odpovědí obsahuje pouze data vrácená prostředku. žádné záhlaví nebo metadata, které jsou zahrnuty v odpovědi by mělo být odebrána z odpovědi a vystavit aplikace prostřednictvím vlastnosti specifické pro protokol nebo **záhlaví** vlastnost.  
  
 Instance datového proudu, který je vrácený **GetResponseStream** metoda vlastní aplikace a je možné uzavřít bez zavření **WebResponse**. Podle konvence volání **WebResponse.Close** metoda také zavře datový proud vrácený **GetResponse**.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.WebResponse>
- <xref:System.Net.HttpWebResponse>
- <xref:System.Net.FileWebResponse>
- [Programování připojitelných protokolů](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
- [Odvození ze žádosti WebRequest](../../../docs/framework/network-programming/deriving-from-webrequest.md)
