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
ms.openlocfilehash: 5b4b0682b2bddff96cb3d720900ed3aa39f06f9d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431849"
---
# <a name="imetadataemitdefineimporttype-method"></a>IMetaDataEmit::DefineImportType – metoda
Vytvoří odkaz na zadaný typ, který je definován mimo aktuální rozsah, a definuje token pro tento odkaz.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
  
## <a name="parameters"></a>Parametry  
 `pAssemImport`  
 pro Rozhraní [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) , které představuje sestavení, ze kterého je importován cílový typ.  
  
 `pbHashValue`  
 pro Pole, které obsahuje hodnotu hash pro sestavení určené parametrem `pAssemImport`.  
  
 `cbHashValue`  
 pro Počet bajtů v poli `pbHashValue`.  
  
 `pImport`  
 pro Rozhraní [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) , které představuje obor metadat, ze kterého je importován cílový typ.  
  
 `tdImport`  
 pro Token `mdTypeDef`, který určuje cílový typ.  
  
 `pAssemEmit`  
 pro Rozhraní [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) představující sestavení, do kterého se naimportuje cílový typ.  
  
 `ptr`  
 mimo Token `mdTypeRef`, který je definován v aktuálním oboru pro odkaz na typ.  
  
## <a name="remarks"></a>Poznámky  
 Před voláním metody [IMetaDataEmit::D efineimportmember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) lze pomocí metody `DefineImportType` vytvořit odkaz na typ v aktuálním oboru pro nadřazenou třídu člena nebo pro nadřazené rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
