---
title: IMetaDataEmit::DefineProperty – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineProperty
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineProperty
helpviewer_keywords:
- IMetaDataEmit::DefineProperty method [.NET Framework metadata]
- DefineProperty method [.NET Framework metadata]
ms.assetid: 5c4c1dc2-d40d-4173-bbe6-7058fb21c98f
topic_type:
- apiref
ms.openlocfilehash: 479cb25ad8e1c263d3539a4203ac5bea781eb931
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009372"
---
# <a name="imetadataemitdefineproperty-method"></a>IMetaDataEmit::DefineProperty – metoda
Vytvoří definici vlastnosti pro zadaný typ se zadaným `get` a přístupovým objektem `set` metody a získá token do této definice vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineProperty (
    [in]  mdTypeDef          td,
    [in]  LPCWSTR            szProperty,
    [in]  DWORD              dwPropFlags,
    [in]  PCCOR_SIGNATURE    pvSig,
    [in]  ULONG              cbSig,
    [in]  DWORD              dwCPlusTypeFlag,
    [in]  void const         *pValue,
    [in]  ULONG              cchValue,
    [in]  mdMethodDef        mdSetter,
    [in]  mdMethodDef        mdGetter,
    [in]  mdMethodDef        rmdOtherMethods[],
    [out] mdProperty         *pmdProp
);  
```  
  
## <a name="parameters"></a>Parametry  
 `td`  
 pro Token třídy nebo rozhraní, na kterém je vlastnost definována.  
  
 `szProperty`  
 pro Název vlastnosti.  
  
 `dwPropFlags`  
 pro Příznaky vlastností.  
  
 `pvSig`  
 pro Signatura vlastnosti  
  
 `cbSig`  
 pro Počet bajtů v `pvSig` .  
  
 `dwCPlusTypeFlag`  
 pro Typ výchozí hodnoty vlastnosti  
  
 `pValue`  
 pro Výchozí hodnota vlastnosti  
  
 `cchValue`  
 pro Počet znaků (Unicode) v `pValue` .  
  
 `mdSetter`  
 pro Metoda, která nastaví hodnotu vlastnosti.  
  
 `mdGetter`  
 pro Metoda, která získá hodnotu vlastnosti.  
  
 `rmdOtherMethods[]`  
 pro Pole dalších metod přidružených k vlastnosti. Ukončete pole pomocí `mdTokenNil` .  
  
 `pmdProp`  
 mimo `mdProperty`Přiřazený token.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataEmit – rozhraní](imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](imetadataemit2-interface.md)
