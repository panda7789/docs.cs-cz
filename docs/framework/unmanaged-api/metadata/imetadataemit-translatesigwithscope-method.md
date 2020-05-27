---
title: IMetaDataEmit::TranslateSigWithScope – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.TranslateSigWithScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::TranslateSigWithScope
helpviewer_keywords:
- TranslateSigWithScope method [.NET Framework metadata]
- IMetaDataEmit::TranslateSigWithScope method [.NET Framework metadata]
ms.assetid: 47915d33-b7bf-409e-b484-4ee1df15de22
topic_type:
- apiref
ms.openlocfilehash: 7ef6dbc46806febc6fba89b39a8b894377225c23
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003952"
---
# <a name="imetadataemittranslatesigwithscope-method"></a>IMetaDataEmit::TranslateSigWithScope – metoda
Importuje sestavení do aktuálního oboru a získá nový podpis metadat pro sloučený obor.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
  
## <a name="parameters"></a>Parametry  
 `pAssemImport`  
 pro Rozhraní pro import sestavení (kde je definován podpis).  
  
 `pbHashValue`  
 pro Objekt BLOB algoritmu hash pro sestavení.  
  
 `cbHashValue`  
 pro Počet bajtů v `pbHashValue` .  
  
 `import`  
 pro Rozhraní pro obor metadat pro import.  
  
 `pbSigBlob`  
 pro Podpis, který se má importovat  
  
 `cbSigBlob`  
 pro Velikost v bajtech `pbSigBlob` .  
  
 `pAssemEmit`  
 pro Rozhraní pro export sestavení.  
  
 `emit`  
 pro Rozhraní pro obor metadat pro export.  
  
 `pvTranslatedSig`  
 mimo Vyrovnávací paměť pro uchování přeloženého objektu BLOB signatury.  
  
 `cbTranslatedSigMax`  
 pro Kapacita (v bajtech) `pvTranslatedSig` .  
  
 `pcbTranslatedSig`  
 mimo Počet skutečných bajtů v přeloženém podpisu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataAssemblyEmit – rozhraní](imetadataassemblyemit-interface.md)
- [IMetaDataAssemblyImport – rozhraní](imetadataassemblyimport-interface.md)
- [IMetaDataEmit – rozhraní](imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](imetadataemit2-interface.md)
- [IMetaDataImport – rozhraní](imetadataimport-interface.md)
