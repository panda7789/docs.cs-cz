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
ms.openlocfilehash: 5c81bc82e19bce658336e4860a61f2721e17423d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431698"
---
# <a name="imetadataemitdefineparam-method"></a>IMetaDataEmit::DefineParam – metoda
Vytvoří definici parametru se specifikovanou signaturou pro metodu, na kterou se odkazuje pomocí zadaného tokenu, a získá token pro tuto definici parametru.  
  
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
 pro Token pro metodu, jejíž parametr je právě definován.  
  
 `ulParamSeq`  
 pro Pořadové číslo parametru.  
  
 `szName`  
 pro Název parametru v kódování Unicode.  
  
 `dwParamFlags`  
 pro Příznaky pro parametr Toto je Bitová maska `CorParamAttr` hodnot.  
  
 `dwCPlusTypeFlag`  
 [in] `ELEMENT_TYPE_` *\** hodnoty konstanty.  
  
 `pValue`  
 pro Hodnota konstanty pro parametr  
  
 `cchValue`  
 pro Velikost `pValue`znaků Unicode.  
  
 `ppd`  
 mimo Byl přiřazen token `mdParamDef`.  
  
## <a name="remarks"></a>Poznámky  
 Hodnoty sekvence v `ulParamSeq` začínají hodnotou 1 pro parametry. Návratová hodnota má pořadové číslo 0.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
