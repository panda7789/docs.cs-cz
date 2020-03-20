---
title: IMetaDataEmit::DefineField – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type:
- apiref
ms.openlocfilehash: 8ca5ab70f60de4d783800fb18612a8f04cb9cee1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177705"
---
# <a name="imetadataemitdefinefield-method"></a>IMetaDataEmit::DefineField – metoda
Vytvoří definici pole se zadaným podpisem metadat a získá token pro tuto definici pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineField (
    [in]  mdTypeDef   td,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwFieldFlags,
    [in]  PCCOR_SIGNATURE pvSigBlob,
    [in]  ULONG       cbSigBlob,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue,
    [out] mdFieldDef  *pmd
);  
```  
  
## <a name="parameters"></a>Parametry  
 `td`  
 [v] Token `mdTypeDef` pro ohraničující třídu nebo rozhraní.  
  
 `szName`  
 [v] Název pole v unicode.  
  
 `dwFieldFlags`  
 [v] Atributy pole. Toto je bitová maska `CorFieldAttr` hodnot.  
  
 `pvSigBlob`  
 [v] Podpis pole jako objekt BLOB.  
  
 `cbSigBlob`  
 [v] Počet bajtů v `pvSigBlob`.  
  
 `dwCPlusTypeFlag`  
 [v] Pro `ELEMENT_TYPE_` *\** konstantní hodnotu. To je `CorElementType` hodnota. Pokud nedefinujete konstantní hodnotu pole, použijte `ELEMENT_TYPE_END`.  
  
 `pValue`  
 [v] Konstantní hodnota pole.  
  
 `cchValue`  
 [v] Velikost znaků (Unicode) `pValue`.  
  
 `pmd`  
 [out] Přiřazen `mdFieldDef` token.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
