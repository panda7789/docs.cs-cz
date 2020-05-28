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
ms.openlocfilehash: edce5cb93b770fb5730e5a06633ffffacf332f7a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004686"
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
 pro Rozhraní [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) , které představuje sestavení, ze kterého je importován cílový typ.  
  
 `pbHashValue`  
 pro Pole, které obsahuje hodnotu hash pro sestavení určené parametrem `pAssemImport` .  
  
 `cbHashValue`  
 pro Počet bajtů v `pbHashValue` poli.  
  
 `pImport`  
 pro Rozhraní [IMetaDataImport](imetadataimport-interface.md) , které představuje obor metadat, ze kterého je importován cílový typ.  
  
 `tdImport`  
 pro `mdTypeDef`Token, který určuje cílový typ.  
  
 `pAssemEmit`  
 pro Rozhraní [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) představující sestavení, do kterého se naimportuje cílový typ.  
  
 `ptr`  
 mimo `mdTypeRef`Token, který je definován v aktuálním oboru pro odkaz na typ.  
  
## <a name="remarks"></a>Poznámky  
 Před voláním metody [IMetaDataEmit::D efineimportmember](imetadataemit-defineimportmember-method.md) lze použít `DefineImportType` metodu pro vytvoření odkazu na typ v aktuálním oboru pro nadřazenou třídu člena nebo pro nadřazené rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataEmit – rozhraní](imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](imetadataemit2-interface.md)
