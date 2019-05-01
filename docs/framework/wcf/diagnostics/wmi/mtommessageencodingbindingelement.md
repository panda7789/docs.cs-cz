---
title: MtomMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
ms.openlocfilehash: aed65311d2b36a5dc764511de04e34c4bfb69d7b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963241"
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
