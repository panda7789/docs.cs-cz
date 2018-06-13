---
title: BinaryMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
ms.openlocfilehash: 03a33f01fe6b6f75e81749c96c31770009350b05
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486560"
---
# <a name="binarymessageencodingbindingelement"></a>BinaryMessageEncodingBindingElement
BinaryMessageEncodingBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída BinaryMessageEncodingBindingElement nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída BinaryMessageEncodingBindingElement má následující vlastnosti.  
  
## <a name="maxreadpoolsize"></a>maxReadPoolSize  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Celé číslo, které definuje počet zpráv lze číst souběžně bez přidělení nového čtečky.  
  
## <a name="maxsessionsize"></a>maxSessionSize  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Hodnota, která určuje velikost v bajtech vyrovnávací paměti používané pro kódování.  
  
## <a name="maxwritepoolsize"></a>maxWritePoolSize  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Celé číslo, které definuje počet zpráv lze najednou odeslat bez přiděluje nový zapisovače.  
  
## <a name="readerquotas"></a>ReaderQuotas  
 Datový typ: XmlDictionaryReaderQuotas, který  
  
 Přístup k typu: jen pro čtení  
  
 Kvóty čtečky.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
