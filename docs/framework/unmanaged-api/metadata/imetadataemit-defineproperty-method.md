---
title: "IMetaDataEmit::DefineProperty – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineProperty
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineProperty
helpviewer_keywords:
- IMetaDataEmit::DefineProperty method [.NET Framework metadata]
- DefineProperty method [.NET Framework metadata]
ms.assetid: 5c4c1dc2-d40d-4173-bbe6-7058fb21c98f
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: fc0403fd51f028510eb60d93ff96fc7d05606366
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Imetadataemit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [Imetadataemit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
