---
title: IMetaDataAssemblyEmit::SetExportedTypeProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetExportedTypeProps
helpviewer_keywords:
- SetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 1c090153-fd5f-46c7-9cff-39a78d992c8f
topic_type:
- apiref
ms.openlocfilehash: ae682c354a7a5188611b103008a3e18f8d821260
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431938"
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a>IMetaDataAssemblyEmit::SetExportedTypeProps – metoda
Upraví zadanou `ExportedType` strukturu metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,   
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ct`  
 pro Token metadat, který určuje `ExportedType` strukturu metadat, která se má upravit.  
  
 `tkImplementation`  
 pro Token typu `File`, `AssemblyRef`nebo `ExportedType`, který určuje, jak je tento typ implementován.  
  
 `tkTypeDef`  
 pro Token `TypeDef`, na který se odkazuje v souboru kódu.  
  
 `dwExportedTypeFlags`  
 pro Bitová kombinace hodnot, které určují atributy typu.  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li vytvořit `ExportedType` struktury metadat, použijte metodu [IMetaDataAssemblyEmit::D efineexportedtype](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
