---
title: MtomMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
ms.openlocfilehash: ad4f2cc3b03111854d10d6a1c1128f090a629a07
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54490973"
---
# <a name="mtommessageencodingbindingelement"></a>MtomMessageEncodingBindingElement
MtomMessageEncodingBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída MtomMessageEncodingBindingElement nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída MtomMessageEncodingBindingElement má následující vlastnosti:  
  
### <a name="encoding"></a>Kódování  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Kódování znakové sady, chcete-li být použito pro vysílání zpráv z vazby.  
  
### <a name="maxreadpoolsize"></a>MaxReadPoolSize  
 Datový typ: sint32  
  
 Typ přístupu: jen pro čtení  
  
 Celé číslo, které definuje počet zpráv lze souběžně číst bez přidělení nových čtecích zařízení.  
  
### <a name="maxwritepoolsize"></a>maxWritePoolSize  
 Datový typ: sint32  
  
 Typ přístupu: jen pro čtení  
  
 Celé číslo, které definuje počet zpráv souběžně poslaných bez přidělení nových modulů pro zápis.  
  
### <a name="readerquotas"></a>ReaderQuotas  
 Datový typ: XmlDictionaryReaderQuotas  
  
 Typ přístupu: jen pro čtení  
  
 Kvóty čtecích zařízení.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
