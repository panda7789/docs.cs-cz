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
ms.openlocfilehash: 2a67f50fa1042e8d3957a9a0394507f260a328c6
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009012"
---
# <a name="imetadataassemblyimport-interface"></a>IMetaDataAssemblyImport – rozhraní
Poskytuje metody pro přístup k obsahu manifestu sestavení a jeho prohlížení.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[CloseEnum – metoda](imetadataassemblyimport-closeenum-method.md)|Uvolní popisovač pro zadaný enumerátor.|  
|[EnumAssemblyRefs – metoda](imetadataassemblyimport-enumassemblyrefs-method.md)|Získá ukazatel rozhraní na enumerátor, který obsahuje `mdAssemblyRef` tokeny sestavení odkazované sestavením v aktuálním oboru metadat.|  
|[EnumExportedTypes – metoda](imetadataassemblyimport-enumexportedtypes-method.md)|Získá ukazatel rozhraní na enumerátor, který obsahuje `mdExportedType` tokeny typů com, na které odkazuje sestavení v aktuálním oboru metadat.|  
|[EnumFiles – metoda](imetadataassemblyimport-enumfiles-method.md)|Získá ukazatel rozhraní na enumerátor, který obsahuje `mdFile` tokeny souborů, na které odkazuje sestavení v aktuálním oboru metadat.|  
|[EnumManifestResources – metoda](imetadataassemblyimport-enummanifestresources-method.md)|Získá ukazatel rozhraní na enumerátor, který obsahuje `mdManifestResource` tokeny prostředků, na které se odkazuje v rámci sestavení v aktuálním oboru metadat.|  
|[FindAssembliesByName – metoda](imetadataassemblyimport-findassembliesbyname-method.md)|Získá pole `mdAssemblyRef` tokenů pro sestavení se zadaným názvem.|  
|[FindExportedTypeByName – metoda](imetadataassemblyimport-findexportedtypebyname-method.md)|Získá `mdExportedType` token pro typ com se zadaným názvem.|  
|[FindManifestResourceByName – metoda](imetadataassemblyimport-findmanifestresourcebyname-method.md)|Získá `mdManifestResource` token pro prostředek se zadaným názvem.|  
|[GetAssemblyFromScope – metoda](imetadataassemblyimport-getassemblyfromscope-method.md)|Získá token pro sestavení v aktuálním oboru metadat.|  
|[GetAssemblyProps – metoda](imetadataassemblyimport-getassemblyprops-method.md)|Získá nastavení vlastností zadaného sestavení.|  
|[GetAssemblyRefProps – metoda](imetadataassemblyimport-getassemblyrefprops-method.md)|Získá nastavení vlastností zadaného `mdAssemblyRef` tokenu.|  
|[GetExportedTypeProps – metoda](imetadataassemblyimport-getexportedtypeprops-method.md)|Získá nastavení vlastností zadaného typu modelu COM.|  
|[GetFileProps – metoda](imetadataassemblyimport-getfileprops-method.md)|Získá nastavení vlastností zadaného souboru.|  
|[GetManifestResourceProps – metoda](imetadataassemblyimport-getmanifestresourceprops-method.md)|Získá nastavení vlastností zadaného prostředku manifestu.|  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Rozhraní pro metadata](metadata-interfaces.md)
- [IMetaDataAssemblyEmit – rozhraní](imetadataassemblyemit-interface.md)
