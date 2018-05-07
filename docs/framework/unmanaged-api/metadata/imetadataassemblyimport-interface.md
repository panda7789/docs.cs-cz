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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: da75f98edb54080658dc86f48d4ebb458d72f20d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataassemblyimport-interface"></a>IMetaDataAssemblyImport – rozhraní
Poskytuje metody pro přístup a kontrolu obsah manifestu sestavení.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CloseEnum – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-closeenum-method.md)|Uvolní popisovač zadaný enumerátor.|  
|[EnumAssemblyRefs – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumassemblyrefs-method.md)|Získá ukazatele rozhraní na enumerátor, který obsahuje `mdAssemblyRef` tokeny sestavení odkazuje sestavení v aktuálním oboru metadat.|  
|[EnumExportedTypes – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumexportedtypes-method.md)|Získá ukazatele rozhraní na enumerátor, který obsahuje `mdExportedType` tokeny typy modelu COM, odkazuje na sestavení v aktuálním oboru metadat.|  
|[EnumFiles – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumfiles-method.md)|Získá ukazatele rozhraní na enumerátor, který obsahuje `mdFile` tokeny souborů odkazuje sestavení v aktuálním oboru metadat.|  
|[EnumManifestResources – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enummanifestresources-method.md)|Získá ukazatele rozhraní na enumerátor, který obsahuje `mdManifestResource` tokeny prostředků odkazuje sestavení v aktuálním oboru metadat.|  
|[FindAssembliesByName – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findassembliesbyname-method.md)|Získá pole `mdAssemblyRef` tokeny pro sestavení se zadaným názvem.|  
|[FindExportedTypeByName – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findexportedtypebyname-method.md)|Získá `mdExportedType` tokenu pro typ COM se zadaným názvem.|  
|[FindManifestResourceByName – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findmanifestresourcebyname-method.md)|Získá `mdManifestResource` tokenu pro prostředek se zadaným názvem.|  
|[GetAssemblyFromScope – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyfromscope-method.md)|Získá token pro sestavení v aktuálním oboru metadat.|  
|[GetAssemblyProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyprops-method.md)|Získá nastavení vlastností zadaného sestavení.|  
|[GetAssemblyRefProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyrefprops-method.md)|Získá nastavení vlastností zadaného `mdAssemblyRef` tokenu.|  
|[GetExportedTypeProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getexportedtypeprops-method.md)|Získá nastavení vlastností zadaného typu modelu COM.|  
|[GetFileProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getfileprops-method.md)|Získá nastavení vlastností zadaného souboru.|  
|[GetManifestResourceProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getmanifestresourceprops-method.md)|Získá nastavení vlastností zadaného prostředku manifestu.|  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
