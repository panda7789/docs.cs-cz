---
title: IMetaDataAssemblyEmit – rozhraní
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit
helpviewer_keywords:
- IMetaDataAssemblyEmit interface [.NET Framework metadata]
ms.assetid: 34fb03cc-2285-4a45-ac48-ad993b7a921a
topic_type:
- apiref
ms.openlocfilehash: 6b36d63101c1e9550a979d858764e9052cf45792
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447929"
---
# <a name="imetadataassemblyemit-interface"></a>IMetaDataAssemblyEmit – rozhraní
Provides methods that support the self-description model used by the common language runtime to resolve and consume resources.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[DefineAssembly – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md)|Creates an assembly data structure containing metadata for the specified assembly, and returns the associated metadata token.|  
|[DefineAssemblyRef – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)|Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.|  
|[DefineExportedType – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)|Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.|  
|[DefineFile – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)|Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.|  
|[DefineManifestResource – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md)|Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.|  
|[SetAssemblyProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyprops-method.md)|Modifies the specified `Assembly` metadata structure.|  
|[SetAssemblyRefProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyrefprops-method.md)|Modifies the specified `AssemblyRef` metadata structure.|  
|[SetExportedTypeProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setexportedtypeprops-method.md)|Modifies the specified `ExportedType` metadata structure.|  
|[SetFileProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setfileprops-method.md)|Modifies the specified `File` metadata structure.|  
|[SetManifestResourceProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setmanifestresourceprops-method.md)|Modifies the specified `ManifestResource` metadata structure.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MsCorEE.dll  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataAssemblyImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
