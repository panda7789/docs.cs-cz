---
title: MtomMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
ms.openlocfilehash: 49a640a666131491366646d6d486d25a515e35bf
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185703"
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
  
 Přístup k typu: jen pro čtení  
  
 Kódování znakové sady, chcete-li být použito pro vysílání zpráv z vazby.  
  
### <a name="maxreadpoolsize"></a>maxReadPoolSize  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Celé číslo, které definuje počet zpráv lze souběžně číst bez přidělení nových čtecích zařízení.  
  
### <a name="maxwritepoolsize"></a>maxWritePoolSize  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Celé číslo, které definuje počet zpráv souběžně poslaných bez přidělení nových modulů pro zápis.  
  
### <a name="readerquotas"></a>readerQuotas  
 Datový typ: XmlDictionaryReaderQuotas, který  
  
 Přístup k typu: jen pro čtení  
  
 Kvóty čtecích zařízení.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
