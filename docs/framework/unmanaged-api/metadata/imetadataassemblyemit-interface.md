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
ms.openlocfilehash: 3a66ef090a205019493e099919739867e3936873
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081793"
---
# <a name="imetadataassemblyemit-interface"></a>IMetaDataAssemblyEmit – rozhraní
Poskytuje metody, které podporují vlastní popis modelu používá modul common language runtime řešení a využívat prostředky.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[DefineAssembly – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md)|Vytvoří strukturu dat sestavení obsahující metadata pro zadané sestavení a vrátí token metadat.|  
|[DefineAssemblyRef – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)|Vytvoří `AssemblyRef` struktura obsahující metadata pro sestavení, které toto sestavení odkazuje a vrátí token metadat.|  
|[DefineExportedType – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)|Vytvoří `ExportedType` struktura obsahující metadata pro zadanou exportovat typ a vrátí token metadat.|  
|[DefineFile – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)|Vytvoří `File` struktury metadat obsahující metadata pro sestavení odkazuje toto sestavení a vrátí token metadat.|  
|[DefineManifestResource – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md)|Vytvoří `ManifestResource` struktury obsahující metadata pro zadaný prostředek manifestu a vrátí token metadat.|  
|[SetAssemblyProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyprops-method.md)|Upraví zadaný `Assembly` struktury metadat.|  
|[SetAssemblyRefProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyrefprops-method.md)|Upraví zadaný `AssemblyRef` struktury metadat.|  
|[SetExportedTypeProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setexportedtypeprops-method.md)|Upraví zadaný `ExportedType` struktury metadat.|  
|[SetFileProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setfileprops-method.md)|Upraví zadaný `File` struktury metadat.|  
|[SetManifestResourceProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setmanifestresourceprops-method.md)|Upraví zadaný `ManifestResource` struktury metadat.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataAssemblyImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
