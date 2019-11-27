---
title: IMetaDataAssemblyImport – rozhraní
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport
helpviewer_keywords:
- IMetaDataAssemblyImport interface [.NET Framework metadata]
ms.assetid: 29c6fba5-4cea-417d-b484-7ed22ebff1c9
topic_type:
- apiref
ms.openlocfilehash: 289e26868ff2eb9e1d97cf084e9a888815062ea4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436303"
---
# <a name="imetadataassemblyimport-interface"></a>IMetaDataAssemblyImport – rozhraní
Poskytuje metody pro přístup k obsahu manifestu sestavení a jeho prohlížení.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CloseEnum – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-closeenum-method.md)|Uvolní popisovač pro zadaný enumerátor.|  
|[EnumAssemblyRefs – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumassemblyrefs-method.md)|Získá ukazatel rozhraní na enumerátor, který obsahuje `mdAssemblyRef` tokeny sestavení, na které odkazuje sestavení v aktuálním oboru metadat.|  
|[EnumExportedTypes – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumexportedtypes-method.md)|Získá ukazatel rozhraní na enumerátor, který obsahuje `mdExportedType` tokeny typů COM, na které se odkazuje sestavení v aktuálním oboru metadat.|  
|[EnumFiles – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumfiles-method.md)|Získá ukazatel rozhraní na enumerátor, který obsahuje `mdFile` tokeny souborů, na které se odkazuje sestavení v aktuálním oboru metadat.|  
|[EnumManifestResources – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enummanifestresources-method.md)|Získá ukazatel rozhraní na enumerátor, který obsahuje `mdManifestResource` tokeny prostředků, na které se odkazuje sestavení v aktuálním oboru metadat.|  
|[FindAssembliesByName – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findassembliesbyname-method.md)|Získá pole `mdAssemblyRef`ch tokenů pro sestavení se zadaným názvem.|  
|[FindExportedTypeByName – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findexportedtypebyname-method.md)|Získá token `mdExportedType` pro typ COM se zadaným názvem.|  
|[FindManifestResourceByName – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findmanifestresourcebyname-method.md)|Získá token `mdManifestResource` pro prostředek se zadaným názvem.|  
|[GetAssemblyFromScope – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyfromscope-method.md)|Získá token pro sestavení v aktuálním oboru metadat.|  
|[GetAssemblyProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyprops-method.md)|Získá nastavení vlastností zadaného sestavení.|  
|[GetAssemblyRefProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyrefprops-method.md)|Získá nastavení vlastností zadaného tokenu `mdAssemblyRef`.|  
|[GetExportedTypeProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getexportedtypeprops-method.md)|Získá nastavení vlastností zadaného typu modelu COM.|  
|[GetFileProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getfileprops-method.md)|Získá nastavení vlastností zadaného souboru.|  
|[GetManifestResourceProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getmanifestresourceprops-method.md)|Získá nastavení vlastností zadaného prostředku manifestu.|  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
