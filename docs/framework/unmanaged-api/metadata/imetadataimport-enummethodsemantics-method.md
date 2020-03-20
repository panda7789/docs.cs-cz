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
ms.openlocfilehash: f20652a7f86576e64646a1f63c3e2c48b55cf811
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175457"
---
# <a name="imetadataimportenummethodsemantics-method"></a>IMetaDataImport::EnumMethodSemantics – metoda
Výčet vlastností a událostí změny vlastnosti, ke kterým se vztahuje zadaná metoda.  
  
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
 [dovnitř, ven] Ukazatel na čítač výčtu. To musí být NULL pro první volání této metody.  
  
 `mb`  
 [v] A MethodDef token, který omezuje rozsah výčtu.  
  
 `rEventProp`  
 [out] Pole používané k uložení událostí nebo vlastností.  
  
 `cMax`  
 [v] Maximální velikost `rEventProp` pole.  
  
 `pcEventProp`  
 [out] Počet událostí nebo vlastností `rEventProp`vrácených v .  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSemantics`úspěšně vrácena.|  
|`S_FALSE`|Neexistují žádné události nebo vlastnosti výčet. V tom `pcEventProp` případě je nula.|  
  
## <a name="remarks"></a>Poznámky  
 Mnoho běžných typů běhového `On`času jazyka definuje události *vlastností* `Changed` a metody *property* `Changed` související s jejich vlastnostmi. Například <xref:System.Windows.Forms.Control?displayProperty=nameWithType> typ definuje <xref:System.Windows.Forms.Control.Font%2A> vlastnost, <xref:System.Windows.Forms.Control.FontChanged> událost a metodu. <xref:System.Windows.Forms.Control.OnFontChanged%2A> Set přistupující <xref:System.Windows.Forms.Control.Font%2A> metoda <xref:System.Windows.Forms.Control.OnFontChanged%2A> vlastnostvolá metodu, <xref:System.Windows.Forms.Control.FontChanged> která zase vyvolá událost. Byste volat `EnumMethodSemantics` pomocí MethodDef <xref:System.Windows.Forms.Control.OnFontChanged%2A> pro získat odkazy <xref:System.Windows.Forms.Control.Font%2A> na <xref:System.Windows.Forms.Control.FontChanged> vlastnost a událost.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
