---
title: "IMetaDataEmit::TranslateSigWithScope – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.TranslateSigWithScope
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::TranslateSigWithScope
helpviewer_keywords:
- TranslateSigWithScope method [.NET Framework metadata]
- IMetaDataEmit::TranslateSigWithScope method [.NET Framework metadata]
ms.assetid: 47915d33-b7bf-409e-b484-4ee1df15de22
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ceb6a8bfbee5823e7080d8c98647da93a10a5b79
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemittranslatesigwithscope-method"></a>IMetaDataEmit::TranslateSigWithScope – metoda
Importuje sestavení do aktuální obor a získá nové podpis metadata pro sloučené obor.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT TranslateSigWithScope (   
    [in]  IMetaDataAssemblyImport   *pAssemImport,   
    [in]  const void                *pbHashValue,   
    [in]  ULONG                     cbHashValue,   
    [in]  IMetaDataImport           *import,   
    [in]  PCCOR_SIGNATURE           pbSigBlob,   
    [in]  ULONG                     cbSigBlob,  
    [in]  IMetaDataAssemblyEmit     *pAssemEmit,   
    [in]  IMetaDataEmit             *emit,   
    [out] PCOR_SIGNATURE            pvTranslatedSig,   
    [in]  ULONG                     cbTranslatedSigMax,   
    [out] ULONG                     *pcbTranslatedSig   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pAssemImport`  
 [v] Rozhraní pro import sestavení (kde je definován podpis).  
  
 `pbHashValue`  
 [v] Hodnota hash objektu blob pro sestavení.  
  
 `cbHashValue`  
 [v] Počet bajtů v `pbHashValue`.  
  
 `import`  
 [v] Rozhraní pro import metadat obor.  
  
 `pbSigBlob`  
 [v] Podpis určených k importu.  
  
 `cbSigBlob`  
 [v] Velikost v bajtech z `pbSigBlob`.  
  
 `pAssemEmit`  
 [v] Rozhraní pro export sestavení.  
  
 `emit`  
 [v] Rozhraní pro export metadat obor.  
  
 `pvTranslatedSig`  
 [out] Vyrovnávací paměti pro uložení objektů blob přeložený podpis.  
  
 `cbTranslatedSigMax`  
 [v] Kapacitu, v bajtech z `pvTranslatedSig`.  
  
 `pcbTranslatedSig`  
 [out] Počet skutečného bajtů přeložený podpis.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [IMetaDataAssemblyImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
