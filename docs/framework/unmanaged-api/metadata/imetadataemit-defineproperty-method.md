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
ms.openlocfilehash: f11b374ed0ecbfc137c43fb641ae691237604691
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431520"
---
# <a name="imetadataemitdefineproperty-method"></a>IMetaDataEmit::DefineProperty – metoda
Vytvoří definici vlastnosti pro zadaný typ se zadanými přístupovými metodami metody `get` a `set` a získá token této definici vlastnosti.  
  
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
 pro Počet bajtů v `pvSig`.  
  
 `dwCPlusTypeFlag`  
 pro Typ výchozí hodnoty vlastnosti  
  
 `pValue`  
 pro Výchozí hodnota vlastnosti  
  
 `cchValue`  
 pro Počet znaků (Unicode) v `pValue`.  
  
 `mdSetter`  
 pro Metoda, která nastaví hodnotu vlastnosti.  
  
 `mdGetter`  
 pro Metoda, která získá hodnotu vlastnosti.  
  
 `rmdOtherMethods[]`  
 pro Pole dalších metod přidružených k vlastnosti. Ukončete pole pomocí `mdTokenNil`.  
  
 `pmdProp`  
 mimo Byl přiřazen token `mdProperty`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
