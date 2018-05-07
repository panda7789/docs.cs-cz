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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5c250a577f2ccdbbfefb35225b880c0e4317db36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitdefineproperty-method"></a>IMetaDataEmit::DefineProperty – metoda
Vytvoří definici vlastnosti pro zadaný typ se zadaným `get` a `set` metody přístupových objektů a získá token pro tuto definici vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `td`  
 [v] Token pro třídy nebo rozhraní, na kterém je definována vlastnost.  
  
 `szProperty`  
 [v] Název vlastnosti.  
  
 `dwPropFlags`  
 [v] Příznaky vlastnost.  
  
 `pvSig`  
 [v] Vlastnost podpis.  
  
 `cbSig`  
 [v] Počet bajtů v `pvSig`.  
  
 `dwCPlusTypeFlag`  
 [v] Typ vlastnosti na výchozí hodnotu.  
  
 `pValue`  
 [v] Výchozí hodnota pro vlastnost.  
  
 `cchValue`  
 [v] Počet (Unicode) znaků v `pValue`.  
  
 `mdSetter`  
 [v] Metoda, která nastavuje hodnoty vlastnosti.  
  
 `mdGetter`  
 [v] Metoda, která se získá hodnotu vlastnosti.  
  
 `rmdOtherMethods[]`  
 [v] Pole jiné metody související s vlastností. Terminate – pole se `mdTokenNil`.  
  
 `pmdProp`  
 [out] `mdProperty` Token přiřazený.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
