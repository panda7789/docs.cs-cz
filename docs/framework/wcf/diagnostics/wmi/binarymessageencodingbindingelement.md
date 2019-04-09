---
title: BinaryMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
ms.openlocfilehash: e0551e7b4b05151490625912742aa6b26ef0216e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145675"
---
# <a name="binarymessageencodingbindingelement"></a>BinaryMessageEncodingBindingElement
BinaryMessageEncodingBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třídě BinaryMessageEncodingBindingElement nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třídě BinaryMessageEncodingBindingElement má následující vlastnosti.  
  
## <a name="maxreadpoolsize"></a>MaxReadPoolSize  
 Datový typ: sint32  
  
 Typ přístupu: jen pro čtení  
  
 Celé číslo, které definuje počet zpráv lze souběžně číst bez přidělení nových čtecích zařízení.  
  
## <a name="maxsessionsize"></a>maxSessionSize  
 Datový typ: sint32  
  
 Typ přístupu: jen pro čtení  
  
 Hodnota, která určuje velikost v bajtech, použité pro kódování vyrovnávací paměti.  
  
## <a name="maxwritepoolsize"></a>maxWritePoolSize  
 Datový typ: sint32  
  
 Typ přístupu: jen pro čtení  
  
 Celé číslo, které definuje počet zpráv souběžně poslaných bez přidělení nových modulů pro zápis.  
  
## <a name="readerquotas"></a>ReaderQuotas  
 Datový typ: XmlDictionaryReaderQuotas  
  
 Typ přístupu: jen pro čtení  
  
 Kvóty čtecích zařízení.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
