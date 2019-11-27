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
ms.openlocfilehash: 40f24a4ea628ce92a27ab1bfe97fc87a57dfa4f0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432556"
---
# <a name="imetadataemitdefinefield-method"></a>IMetaDataEmit::DefineField – metoda
Vytvoří definici pro pole se zadaným podpisem metadat a získá token do této definice pole.  
  
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
 pro Token `mdTypeDef` nadřazené třídy nebo rozhraní.  
  
 `szName`  
 pro Název pole v kódování Unicode.  
  
 `dwFieldFlags`  
 pro Atributy pole Toto je Bitová maska `CorFieldAttr` hodnot.  
  
 `pvSigBlob`  
 pro Podpis pole jako objekt BLOB  
  
 `cbSigBlob`  
 pro Počet bajtů v `pvSigBlob`.  
  
 `dwCPlusTypeFlag`  
 pro *\** `ELEMENT_TYPE_`pro hodnotu konstanty. Toto je `CorElementType` hodnota. Pokud nedefinujete konstantní hodnotu pro pole, použijte `ELEMENT_TYPE_END`.  
  
 `pValue`  
 pro Hodnota konstanty pro pole  
  
 `cchValue`  
 pro Velikost v (Unicode) znaků `pValue`.  
  
 `pmd`  
 mimo Byl přiřazen token `mdFieldDef`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
