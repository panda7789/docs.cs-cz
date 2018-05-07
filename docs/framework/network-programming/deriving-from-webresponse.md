---
title: Odvozování z WebResponse
ms.date: 03/30/2017
helpviewer_keywords:
- Deriving from WebResponse
ms.assetid: f11d4866-a199-4087-9306-a5a4c18b13db
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 14a1260bf67469e792439985fec43ac44c6f0c9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="deriving-from-webresponse"></a>Odvozování z WebResponse
<xref:System.Net.WebResponse> Třída je abstraktní základní třída, která poskytuje základní metody a vlastnosti pro vytvoření odpovědi specifické pro protokol, který nejlépe odpovídá modulární protokol model rozhraní .NET Framework. Aplikace, které používají <xref:System.Net.WebRequest> třídy data žádosti z prostředků přijímat odpovědi v **WebResponse**. Specifické pro protokol **WebResponse** následníků musí implementovat abstraktní členy **WebResponse** třídy.  
  
 Přidruženého **WebRequest** musíte vytvořit třídu **WebResponse** následníky. Například <xref:System.Net.HttpWebResponse> vytváření instancí pouze jako výsledek volání <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> nebo <xref:System.Net.HttpWebRequest.EndGetResponse%2A?displayProperty=nameWithType>. Každý **WebResponse** obsahuje výsledek požadavku na prostředek a není určena pro znovu použít.  
  
## <a name="contentlength-property"></a>Vlastnost ContentLength  
 <xref:System.Net.WebResponse.ContentLength%2A> Vlastnost udává počet bajtů dat, které jsou k dispozici z datového proudu vrácený <xref:System.Net.WebResponse.GetResponseStream%2A> metoda. **ContentLength** vlastnost neindikuje počet bajtů vrácených serverem záhlaví nebo metadata informací; znamená počet bajtů dat v samotné požadovaný prostředek.  
  
## <a name="contenttype-property"></a>Vlastnost ContentType  
 <xref:System.Net.WebResponse.ContentType%2A> Vlastnost poskytuje žádné speciální informace, že váš protokol vyžaduje k odeslání do klienta k identifikaci typ obsahu, které jsou odesílány serverem. Obvykle je to typ MIME obsahu žádná data vrácená.  
  
## <a name="headers-property"></a>Vlastnost hlavičky  
 <xref:System.Net.WebResponse.Headers%2A> Vlastnost obsahuje libovolné kolekci dvojic název/hodnota metadat přidružený k odpovědi. Veškerá metadata, vyžaduje protokol, který může být vyjádřený jako můžou být součástí dvojici název/hodnota **hlavičky** vlastnost.  
  
 Není nutné použít **hlavičky** vlastnost na používání záhlaví metadat. Metadata specifická pro protokol mohou být zpřístupněny jako vlastnosti; například <xref:System.Net.HttpWebResponse.LastModified%2A?displayProperty=nameWithType> zpřístupňuje vlastnost **poslední úpravy** hlavičky protokolu HTTP. Když vystavit Záhlaví metadat jako vlastnost byste neměli povolit stejné vlastnosti, která má nastavit pomocí **hlavičky** vlastnost.  
  
## <a name="responseuri-property"></a>Vlastnost ResponseUri  
 <xref:System.Net.WebResponse.ResponseUri%2A> Vlastnost obsahuje identifikátor URI prostředku, který ve skutečnosti zadat odpovědi. Pro protokoly, které nepodporují přesměrování **ResponseUri** bude stejné jako <xref:System.Net.WebRequest.RequestUri%2A> vlastnost **WebRequest** odpověď, který vytvořil. Pokud protokol podporuje přesměrování požadavku, **ResponseUri** bude obsahovat identifikátor URI odpovědi.  
  
## <a name="close-method"></a>Close – metoda  
 <xref:System.Net.WebResponse.Close%2A> Metoda zavře připojení k požadavku a odpovědi a vyčistí prostředky využívané třídou odpovědi. **Zavřít** metoda zavře všechny instance datového proudu používané odpovědi, ale nevyvolá výjimku, pokud datového proudu odpovědi dříve uzavřel volání <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metoda.  
  
## <a name="getresponsestream-method"></a>GetResponseStream – metoda  
 <xref:System.Net.WebResponse.GetResponseStream%2A> Metoda vrátí datový proud, který obsahuje odpověď od požadovaný prostředek. Datového proudu odpovědi obsahuje pouze data vrácený prostředků; všechny hlavičky nebo metadata, které jsou zahrnuty v odpovědi by měl odstraní z odpovědi a viditelné na aplikace prostřednictvím vlastnosti specifické pro protokol nebo **hlavičky** vlastnost.  
  
 Instanci datového proudu vrácený **GetResponseStream** metoda vlastní aplikace a je možné uzavřít bez zavření **WebResponse**. Podle konvence volání **WebResponse.Close** metoda také zavře datový proud vrácený **GetResponse**.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.WebResponse>  
 <xref:System.Net.HttpWebResponse>  
 <xref:System.Net.FileWebResponse>  
 [Programování připojitelných protokolů](../../../docs/framework/network-programming/programming-pluggable-protocols.md)  
 [Odvození ze žádosti WebRequest](../../../docs/framework/network-programming/deriving-from-webrequest.md)
