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
ms.openlocfilehash: a58e03875ec021b41479085fa9e27a4321ae965e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004345"
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
 [in] `ELEMENT_TYPE_` *\** pro hodnotu konstanty.  
  
 `pValue`  
 pro Hodnota konstanty pro parametr  
  
 `cchValue`  
 pro Velikost (v Unicode znacích) `pValue` .  
  
 `ppd`  
 mimo `mdParamDef`Přiřazený token.  
  
## <a name="remarks"></a>Poznámky  
 Hodnoty sekvence začínají na `ulParamSeq` 1 pro parametry. Návratová hodnota má pořadové číslo 0.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataEmit – rozhraní](imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](imetadataemit2-interface.md)
