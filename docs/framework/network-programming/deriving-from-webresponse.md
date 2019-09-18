---
title: Odvození z odpovědi WebResponse
ms.date: 03/30/2017
helpviewer_keywords:
- Deriving from WebResponse
ms.assetid: f11d4866-a199-4087-9306-a5a4c18b13db
ms.openlocfilehash: bd06928b08eb085ef13371687fb1e5b92c6c1d86
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048581"
---
# <a name="deriving-from-webresponse"></a>Odvození z odpovědi WebResponse
<xref:System.Net.WebResponse> Třída je abstraktní základní třída, která poskytuje základní metody a vlastnosti pro vytvoření odpovědi specifické pro protokol, která odpovídá modelu .NET Framework připojit k protokolu. Aplikace, které používají <xref:System.Net.WebRequest> třídu k vyžádání dat z prostředků, obdrží odpovědi v rámci **WebResponse**. Následníky **WebResponse** konkrétního protokolu musí implementovat abstraktní členy třídy **WebResponse** .  
  
 Přidružená třída **WebRequest** musí vytvořit následníky **WebResponse** . Například <xref:System.Net.HttpWebResponse> instance jsou vytvořeny pouze jako výsledek volání <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> nebo <xref:System.Net.HttpWebRequest.EndGetResponse%2A?displayProperty=nameWithType>. Každá **WebResponse** obsahuje výsledek požadavku na prostředek a není určen k jeho použití.  
  
## <a name="contentlength-property"></a>Vlastnost ContentLength  
 Vlastnost označuje počet bajtů dat, která jsou k dispozici z datového proudu vráceného <xref:System.Net.WebResponse.GetResponseStream%2A> metodou. <xref:System.Net.WebResponse.ContentLength%2A> Vlastnost **ContentLength** neindikuje počet bajtů záhlaví nebo informací o metadatech vrácených serverem. indikuje jenom počet bajtů dat v požadovaném prostředku.  
  
## <a name="contenttype-property"></a>ContentType – vlastnost  
 <xref:System.Net.WebResponse.ContentType%2A> Vlastnost poskytuje všechny zvláštní informace, které protokol vyžaduje k odeslání do klienta za účelem identifikace typu obsahu odesílaného serverem. Obvykle se jedná o typ obsahu MIME libovolných vrácených dat.  
  
## <a name="headers-property"></a>Vlastnost Headers  
 <xref:System.Net.WebResponse.Headers%2A> Vlastnost obsahuje libovolnou kolekci párů název/hodnota metadat přidružených k odpovědi. Všechna metadata potřebná v protokolu, která lze vyjádřit jako dvojici název/hodnota, lze zahrnout do vlastnosti **Headers** .  
  
 Pro použití metadat hlaviček není nutné použít vlastnost **Headers** . Metadata specifická pro protokol se dají zveřejnit jako vlastnosti. například <xref:System.Net.HttpWebResponse.LastModified%2A?displayProperty=nameWithType> vlastnost zveřejňuje hlavičku HTTP **naposledy upraveného** . Když zveřejňujete metadata hlaviček jako vlastnost, neměli byste mít možnost nastavit tuto vlastnost pomocí vlastnosti **Headers** .  
  
## <a name="responseuri-property"></a>Vlastnost ResponseUri  
 <xref:System.Net.WebResponse.ResponseUri%2A> Vlastnost obsahuje identifikátor URI prostředku, který odpověď skutečně poskytl. Pro protokoly, které nepodporují přesměrování, bude **ResponseUri** stejné jako <xref:System.Net.WebRequest.RequestUri%2A> vlastnost **WebRequest** , která odpověď vytvořila. Pokud protokol podporuje přesměrování požadavku, **ResponseUri** bude obsahovat identifikátor URI odpovědi.  
  
## <a name="close-method"></a>Close – metoda  
 <xref:System.Net.WebResponse.Close%2A> Metoda ukončí všechna připojení, která provedla požadavek a odpověď, a vyčistí prostředky používané odpovědí. Metoda **Close** zavře všechny instance streamu používané odpovědí, ale nevyvolá výjimku, pokud byl datový proud odpovědí dříve uzavřen voláním <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metody.  
  
## <a name="getresponsestream-method"></a>Metoda GetResponseStream  
 <xref:System.Net.WebResponse.GetResponseStream%2A> Metoda vrátí datový proud obsahující odpověď z požadovaného prostředku. Datový proud odpovědi obsahuje pouze data vrácená prostředkem; všechna záhlaví nebo metadata zahrnutá v odpovědi by měla být z odpovědi odstraněna a zpřístupněna aplikaci prostřednictvím vlastností specifických pro protokol nebo vlastností **hlaviček** .  
  
 Instance datového proudu vrácená metodou **GetResponseStream** je vlastněna aplikací a může být zavřena bez zavření **WebResponse**. Podle konvence volání metody **WebResponse. Close** také uzavře datový proud vrácený funkcí **GetResponse**.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.WebResponse>
- <xref:System.Net.HttpWebResponse>
- <xref:System.Net.FileWebResponse>
- [Programování připojitelných protokolů](programming-pluggable-protocols.md)
- [Odvození ze žádosti WebRequest](deriving-from-webrequest.md)
