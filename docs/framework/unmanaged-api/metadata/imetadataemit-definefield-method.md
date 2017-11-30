---
title: "IMetaDataEmit::DefineField – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineField
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2a544d7e676b71fb00b8fd7a3d871867f7f55626
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinefield-method"></a>IMetaDataEmit::DefineField – metoda
Vytvoří definici pole s podpisem Zadaná metadata a získá token tuto definici pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `td`  
 [v] `mdTypeDef` Tokenu pro nadřazených třídy nebo rozhraní.  
  
 `szName`  
 [v] Název pole ve formátu Unicode.  
  
 `dwFieldFlags`  
 [v] Atributy pole. Toto je bitová maska s `CorFieldAttr` hodnoty.  
  
 `pvSigBlob`  
 [v] Podpis pole jako objekt BLOB.  
  
 `cbSigBlob`  
 [v] Počet bajtů v `pvSigBlob`.  
  
 `dwCPlusTypeFlage`  
 [v] `ELEMENT_TYPE_`  *\**  Pro konstantní hodnotu. Toto je `CorElementType` hodnotu. Pokud není definování konstantní hodnota pro pole, použijte `ELEMENT_TYPE_END`.  
  
 `pValue`  
 [v] Hodnota konstanty pro pole.  
  
 `cchValue`  
 [v] Velikost v znaků (Unicode) `pValue`.  
  
 `pmd`  
 [out] `mdFieldDef` Token přiřazený.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Imetadataemit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [Imetadataemit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
