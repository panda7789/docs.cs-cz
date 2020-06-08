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
ms.openlocfilehash: 213cbd955e3d47a49abde579a54af48641e225ec
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491911"
---
# <a name="imetadataimportenummethodsemantics-method"></a>IMetaDataImport::EnumMethodSemantics – metoda
Vytvoří výčet vlastností a událostí změny vlastností, na které se vztahuje zadaná metoda.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
 [in, out] Ukazatel na enumerátor. Pro první volání této metody musí mít hodnotu NULL.  
  
 `mb`  
 pro Token MethodDef omezující obor výčtu.  
  
 `rEventProp`  
 mimo Pole, které se používá k uložení událostí nebo vlastností.  
  
 `cMax`  
 pro Maximální velikost `rEventProp` pole.  
  
 `pcEventProp`  
 mimo Počet událostí nebo vlastností vrácených v `rEventProp` .  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSemantics`úspěšně vráceno.|  
|`S_FALSE`|Neexistují žádné události ani vlastnosti k zobrazení výčtu. V takovém případě `pcEventProp` je nula.|  
  
## <a name="remarks"></a>Poznámky  
 Mnoho typů modulu CLR (Common Language Runtime) definuje události *vlastností* `Changed` a `On` *Property* `Changed` metody vlastností týkající se jejich vlastností. <xref:System.Windows.Forms.Control?displayProperty=nameWithType>Typ například definuje <xref:System.Windows.Forms.Control.Font%2A> vlastnost, <xref:System.Windows.Forms.Control.FontChanged> událost a <xref:System.Windows.Forms.Control.OnFontChanged%2A> metodu. Metoda set přistupující metody <xref:System.Windows.Forms.Control.Font%2A> volání vlastnosti <xref:System.Windows.Forms.Control.OnFontChanged%2A> , která vyvolá <xref:System.Windows.Forms.Control.FontChanged> událost. `EnumMethodSemantics`Pro <xref:System.Windows.Forms.Control.OnFontChanged%2A> získání odkazů na <xref:System.Windows.Forms.Control.Font%2A> vlastnost a událost byste volali pomocí prvku MethodDef pro <xref:System.Windows.Forms.Control.FontChanged> .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](imetadataimport2-interface.md)
