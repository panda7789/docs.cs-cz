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
ms.openlocfilehash: 6825a5198976cc7ab2c04ebd6e782418dcf4a8f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177684"
---
# <a name="imetadataemitdefineimporttype-method"></a>IMetaDataEmit::DefineImportType – metoda
Vytvoří odkaz na zadaný typ, který je definován mimo aktuální obor, a definuje token pro tento odkaz.  
  
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
 [v] Rozhraní [IMetaDataAssemblyImport,](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) které představuje sestavení, ze kterého je importován cílový typ.  
  
 `pbHashValue`  
 [v] Pole, které obsahuje hash pro `pAssemImport`sestavení určené .  
  
 `cbHashValue`  
 [v] Počet bajtů v `pbHashValue` poli.  
  
 `pImport`  
 [v] Rozhraní [IMetaDataImport,](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) které představuje obor metadat, ze kterého je importován cílový typ.  
  
 `tdImport`  
 [v] Token, `mdTypeDef` který určuje cílový typ.  
  
 `pAssemEmit`  
 [v] Rozhraní [IMetaDataAssemblyEmit,](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) které představuje sestavení, do kterého je importován cílový typ.  
  
 `ptr`  
 [out] Token, `mdTypeRef` který je definován v aktuálním oboru pro odkaz na typ.  
  
## <a name="remarks"></a>Poznámky  
 Před voláním metody [IMetaDataEmit::DefineImportMember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) můžete `DefineImportType` použít metodu k vytvoření odkazu na typ v aktuálním oboru pro nadřazenou třídu člena nebo nadřazené rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
