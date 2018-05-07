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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bda949db469d4b8629e54c9e5907da23ac7e169b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataassemblyemit-interface"></a>IMetaDataAssemblyEmit – rozhraní
Poskytuje metody, které podporují vlastní popis modelu používaný modul common language runtime řešení a využívat prostředky.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[DefineAssembly – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md)|Vytvoří strukturu dat sestavení obsahující metadata pro zadaného sestavení a vrátí token přidružených metadat.|  
|[DefineAssemblyRef – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)|Vytvoří `AssemblyRef` struktura obsahující metadata pro sestavení, které toto sestavení odkazuje a vrátí token přidružených metadat.|  
|[DefineExportedType – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)|Vytvoří `ExportedType` struktura obsahující metadata pro zadaný typ exportovat a vrátí token přidružených metadat.|  
|[DefineFile – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)|Vytvoří `File` strukturu metadat obsahující metadata pro sestavení odkazuje toto sestavení a vrátí token přidružených metadat.|  
|[DefineManifestResource – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md)|Vytvoří `ManifestResource` struktury obsahující metadata pro zadanou prostředku manifestu a vrátí token přidružených metadat.|  
|[SetAssemblyProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyprops-method.md)|Upraví zadaný `Assembly` strukturu metadat.|  
|[SetAssemblyRefProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyrefprops-method.md)|Upraví zadaný `AssemblyRef` strukturu metadat.|  
|[SetExportedTypeProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setexportedtypeprops-method.md)|Upraví zadaný `ExportedType` strukturu metadat.|  
|[SetFileProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setfileprops-method.md)|Upraví zadaný `File` strukturu metadat.|  
|[SetManifestResourceProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setmanifestresourceprops-method.md)|Upraví zadaný `ManifestResource` strukturu metadat.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [IMetaDataAssemblyImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
