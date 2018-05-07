---
title: IMetaDataEmit::DefineImportType – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineImportType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineImportType
helpviewer_keywords:
- DefineImportType method [.NET Framework metadata]
- IMetaDataEmit::DefineImportType method [.NET Framework metadata]
ms.assetid: 37fd27af-8062-4904-ace4-51bb78ec600a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 68e6f7599db55ed9429f159b380a8a9f8ae3f034
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitdefineimporttype-method"></a>IMetaDataEmit::DefineImportType – metoda
Vytvoří odkaz na zadaný typ, který je definován v aktuálním oboru a definuje token pro tento odkaz.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DefineImportType (   
    [in]  IMetaDataAssemblyImport  *pAssemImport,   
    [in]  const void               *pbHashValue,   
    [in]  ULONG                    cbHashValue,    
    [in]  IMetaDataImport          *pImport,   
    [in]  mdTypeDef                tdImport,   
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,   
    [out] mdTypeRef                *ptr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pAssemImport`  
 [v] [Imetadataassemblyimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) rozhraní, které představuje sestavení, ve kterém je naimportována na typ cíle.  
  
 `pbHashValue`  
 [v] Pole, které obsahuje hodnotu hash pro sestavení určeného `pAssemImport`.  
  
 `cbHashValue`  
 [v] Počet bajtů `pbHashValue` pole.  
  
 `pImport`  
 [v] [Imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) rozhraní, které představuje metadata oboru, ze kterého je naimportována na typ cíle.  
  
 `tdImport`  
 [v] `mdTypeDef` Token, který určuje typ cíle.  
  
 `pAssemEmit`  
 [v] [Imetadataassemblyemit –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) rozhraní, které představuje sestavení, do kterého je naimportována na typ cíle.  
  
 `ptr`  
 [out] `mdTypeRef` Token, který je definován v aktuálním oboru pro odkaz na typ.  
  
## <a name="remarks"></a>Poznámky  
 Před voláním [imetadataemit::defineimportmember –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) metodu, můžete použít `DefineImportType` metodu pro vytvoření odkaz na typ v aktuálním oboru pro nadřazené třídy nebo rozhraní nadřazeného člena.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
