---
title: IMetaDataImport::EnumMethodSemantics – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodSemantics
helpviewer_keywords:
- EnumMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::EnumMethodSemantics method [.NET Framework metadata]
ms.assetid: e7e3c630-9691-46d6-94df-b5593a7bb08a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16cfa6df6251cd67860155cb8092e77a835eaaef
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223262"
---
# <a name="imetadataimportenummethodsemantics-method"></a>IMetaDataImport::EnumMethodSemantics – metoda
Vytvoří výčet vlastností a změnu vlastnosti události, ke kterým se vztahuje zadanou metodu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,   
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [out v] Ukazatel na enumerátor. První volání této metody musí mít hodnotu NULL.  
  
 `mb`  
 [in] Token MethodDef, která omezuje rozsah výčtu.  
  
 `rEventProp`  
 [out] Pole používá k ukládání vlastnosti nebo události.  
  
 `cMax`  
 [in] Maximální velikost `rEventProp` pole.  
  
 `pcEventProp`  
 [out] Počet událostí nebo vlastnosti, které jsou vráceny v `rEventProp`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSemantics` bylo úspěšně vráceno.|  
|`S_FALSE`|Neexistují žádné události nebo vlastnosti, které chcete zobrazit výčet. V takovém případě `pcEventProp` je nula.|  
  
## <a name="remarks"></a>Poznámky  
 Mnoho běžných typů modulu runtime jazyka definovat *vlastnost* `Changed` události a `On` *vlastnost* `Changed` metody související s jejich vlastností. Například <xref:System.Windows.Forms.Control?displayProperty=nameWithType> definuje typ <xref:System.Windows.Forms.Control.Font%2A> vlastnost, <xref:System.Windows.Forms.Control.FontChanged> události a <xref:System.Windows.Forms.Control.OnFontChanged%2A> metoda. Metodu přístupového objektu set <xref:System.Windows.Forms.Control.Font%2A> vlastnost volání <xref:System.Windows.Forms.Control.OnFontChanged%2A> metodu, která postupně vyvolá <xref:System.Windows.Forms.Control.FontChanged> událostí. By volat `EnumMethodSemantics` pomocí MethodDef pro <xref:System.Windows.Forms.Control.OnFontChanged%2A> zobrazíte odkazy na <xref:System.Windows.Forms.Control.Font%2A> vlastnost a <xref:System.Windows.Forms.Control.FontChanged> událostí.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
