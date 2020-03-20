---
title: IMetaDataEmit::DefineParam – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineParam
helpviewer_keywords:
- IMetaDataEmit::DefineParam method [.NET Framework metadata]
- DefineParam method [.NET Framework metadata]
ms.assetid: d86a3d14-4796-4909-9591-dfafe3de5ce4
topic_type:
- apiref
ms.openlocfilehash: 2807458549db02598ba05f2aa80fa6ea6fbc5a13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177696"
---
# <a name="imetadataemitdefineparam-method"></a>IMetaDataEmit::DefineParam – metoda
Vytvoří definici parametru se zadaným podpisem pro metodu, na kterou odkazuje zadaný token, a získá token pro tuto definici parametru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineParam (  
    [in]  mdMethodDef md,
    [in]  ULONG       ulParamSeq,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwParamFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,  
    [in]  ULONG       cchValue,
    [out] mdParamDef  *ppd
);  
```  
  
## <a name="parameters"></a>Parametry  
 `md`  
 [v] Token pro metodu, jejíž parametr je definován.  
  
 `ulParamSeq`  
 [v] Pořadové číslo parametru.  
  
 `szName`  
 [v] Název parametru v unicode.  
  
 `dwParamFlags`  
 [v] Příznaky parametru. Toto je bitová maska `CorParamAttr` hodnot.  
  
 `dwCPlusTypeFlag`  
 [v] `ELEMENT_TYPE_` pro konstantní hodnotu. *\**  
  
 `pValue`  
 [v] Konstantní hodnota parametru.  
  
 `cchValue`  
 [v] Velikost znaku Unicode . `pValue`  
  
 `ppd`  
 [out] Přiřazen `mdParamDef` token.  
  
## <a name="remarks"></a>Poznámky  
 Sekvenční `ulParamSeq` hodnoty v začíná 1 pro parametry. Vrácená hodnota má pořadové číslo 0.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
