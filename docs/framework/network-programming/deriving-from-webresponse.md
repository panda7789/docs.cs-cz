---
title: Odvození z odpovědi WebResponse
ms.date: 03/30/2017
helpviewer_keywords:
- Deriving from WebResponse
ms.assetid: f11d4866-a199-4087-9306-a5a4c18b13db
ms.openlocfilehash: bd06928b08eb085ef13371687fb1e5b92c6c1d86
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048581"
---
# <a name="deriving-from-webresponse"></a>Odvození z odpovědi WebResponse
Třída <xref:System.Net.WebResponse> je abstraktní základní třída, která poskytuje základní metody a vlastnosti pro vytvoření odpovědi specifické pro protokol, která odpovídá modelu protokolu připojitelnérozhraní rozhraní .NET Framework. Aplikace, které <xref:System.Net.WebRequest> používají třídu k vyžádání dat z prostředků, obdrží odpovědi v **aplikaci WebResponse**. Následovníci **webové odezvy** specifické pro protokol musí implementovat abstraktní členy třídy **WebResponse.**  
  
 Přidružená třída **WebRequest** musí vytvořit potomky **webové odezvy.** Instance jsou <xref:System.Net.HttpWebResponse> například vytvořeny pouze jako <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> výsledek <xref:System.Net.HttpWebRequest.EndGetResponse%2A?displayProperty=nameWithType>volání nebo . Každá **webová odpověď** obsahuje výsledek požadavku na prostředek a není určena k opětovnému použití.  
  
## <a name="contentlength-property"></a>Vlastnost ContentLength  
 Vlastnost <xref:System.Net.WebResponse.ContentLength%2A> označuje počet bajtů dat, které jsou k dispozici <xref:System.Net.WebResponse.GetResponseStream%2A> z datového proudu vrácené metodou. Vlastnost **ContentLength** neoznačuje počet bajtů informací záhlaví nebo metadat vrácených serverem. označuje pouze počet bajtů dat v samotném požadovaném prostředku.  
  
## <a name="contenttype-property"></a>Vlastnost ContentType  
 Vlastnost <xref:System.Net.WebResponse.ContentType%2A> poskytuje všechny speciální informace, které protokol vyžaduje, abyste odeslali klientovi k identifikaci typu obsahu odesílaného serverem. Obvykle se jedná o typ obsahu MIME všech vrácených dat.  
  
## <a name="headers-property"></a>Vlastnost záhlaví  
 Vlastnost <xref:System.Net.WebResponse.Headers%2A> obsahuje libovolnou kolekci párů názvů a hodnot metadat spojených s odpovědí. Všechna metadata potřebná protokolem, která mohou být vyjádřena jako dvojice název/hodnota, mohou být zahrnuta do **vlastnosti Headers.**  
  
 Není nutné používat **Headers** vlastnost používat metadata záhlaví. Metadata specifická pro protokol mohou být vystavena jako vlastnosti; například vlastnost zpřístupňuje **poslední upravené** hlavičky HTTP. <xref:System.Net.HttpWebResponse.LastModified%2A?displayProperty=nameWithType> Když zveřejňujete metadata záhlaví jako vlastnost, neměli byste povolit stejnou vlastnost, která má být nastavena pomocí **headers** vlastnost.  
  
## <a name="responseuri-property"></a>Vlastnost ResponseUri  
 Vlastnost <xref:System.Net.WebResponse.ResponseUri%2A> obsahuje identifikátor URI prostředku, který skutečně poskytl odpověď. Pro protokoly, které nepodporují přesměrování **ResponseUri** bude <xref:System.Net.WebRequest.RequestUri%2A> stejný jako vlastnost **WebRequest,** který vytvořil odpověď. Pokud protokol podporuje přesměrování požadavku, **ResponseUri** bude obsahovat identifikátor URI odpovědi.  
  
## <a name="close-method"></a>Close – metoda  
 Metoda <xref:System.Net.WebResponse.Close%2A> zavře všechna připojení provedené požadavek a odpověď a vyčistí prostředky používané odpověď. Close **Close** Metoda zavře všechny instance datového proudu používané odpověď, ale nevyvolá výjimku, pokud byl <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> datový proud odpovědi dříve uzavřen volání metody.  
  
## <a name="getresponsestream-method"></a>Metoda GetResponseStream  
 Metoda <xref:System.Net.WebResponse.GetResponseStream%2A> vrátí datový proud obsahující odpověď z požadovaného prostředku. Datový proud odpovědí obsahuje pouze data vrácená prostředek; všechny záhlaví nebo metadata zahrnutá v odpovědi by měla být odebrána z odpovědi a vystavena aplikaci prostřednictvím vlastností specifických pro protokol nebo **vlastností Headers.**  
  
 Instance datového proudu vrácená metodou **GetResponseStream** je vlastněna aplikací a může být uzavřena bez zavření **webové odpovědi**. Podle konvence volání **WebResponse.Close** metoda také zavře datový proud vrácený **GetResponse**.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Net.WebResponse>
- <xref:System.Net.HttpWebResponse>
- <xref:System.Net.FileWebResponse>
- [Programování připojitelných protokolů](programming-pluggable-protocols.md)
- [Odvození ze žádosti WebRequest](deriving-from-webrequest.md)
