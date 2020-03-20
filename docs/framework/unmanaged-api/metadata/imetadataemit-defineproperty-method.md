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
ms.openlocfilehash: eb3ecbf39376e7126b5ec93a26badcbf5076d1db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175782"
---
# <a name="imetadataemitdefineproperty-method"></a>IMetaDataEmit::DefineProperty – metoda
Vytvoří definici vlastnosti pro zadaný `get` `set` typ se zadanými přístupovými objekty a přistupujícími objekty metody a získá token pro tuto definici vlastnosti.  
  
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
 [v] Token pro třídu nebo rozhraní, na kterém je definována vlastnost.  
  
 `szProperty`  
 [v] Název vlastnosti.  
  
 `dwPropFlags`  
 [v] Příznaky vlastnosti.  
  
 `pvSig`  
 [v] Podpis vlastnosti.  
  
 `cbSig`  
 [v] Počet bajtů v `pvSig`.  
  
 `dwCPlusTypeFlag`  
 [v] Typ výchozí hodnoty vlastnosti.  
  
 `pValue`  
 [v] Výchozí hodnota vlastnosti.  
  
 `cchValue`  
 [v] Počet znaků (Unicode) `pValue`v .  
  
 `mdSetter`  
 [v] Metoda, která nastaví hodnotu vlastnosti.  
  
 `mdGetter`  
 [v] Metoda, která získá hodnotu vlastnosti.  
  
 `rmdOtherMethods[]`  
 [v] Pole dalších metod spojených s vlastností. Ukončete `mdTokenNil`pole pomocí .  
  
 `pmdProp`  
 [out] Přiřazen `mdProperty` token.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
