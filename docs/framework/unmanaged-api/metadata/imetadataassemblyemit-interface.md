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
ms.openlocfilehash: 807e1ee831a43a4ef1e7b0a269ee38131f24081e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008115"
---
# <a name="imetadataassemblyemit-interface"></a>IMetaDataAssemblyEmit – rozhraní
Poskytuje metody, které podporují model s použitím společného jazykového modulu CLR k řešení a využívání prostředků.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[DefineAssembly – metoda](imetadataassemblyemit-defineassembly-method.md)|Vytvoří strukturu dat sestavení obsahující metadata pro zadané sestavení a vrátí přidružený token metadat.|  
|[DefineAssemblyRef – metoda](imetadataassemblyemit-defineassemblyref-method.md)|Vytvoří `AssemblyRef` strukturu obsahující metadata pro sestavení, na které odkazuje toto sestavení, a vrátí přidružený token metadat.|  
|[DefineExportedType – metoda](imetadataassemblyemit-defineexportedtype-method.md)|Vytvoří `ExportedType` strukturu obsahující metadata pro zadaný exportovaný typ a vrátí přidružený token metadat.|  
|[DefineFile – metoda](imetadataassemblyemit-definefile-method.md)|Vytvoří `File` strukturu metadat obsahující metadata pro sestavení, na které odkazuje toto sestavení, a vrátí přidružený token metadat.|  
|[DefineManifestResource – metoda](imetadataassemblyemit-definemanifestresource-method.md)|Vytvoří `ManifestResource` strukturu obsahující metadata pro zadaný prostředek manifestu a vrátí přidružený token metadat.|  
|[SetAssemblyProps – metoda](imetadataassemblyemit-setassemblyprops-method.md)|Upraví zadanou `Assembly` strukturu metadat.|  
|[SetAssemblyRefProps – metoda](imetadataassemblyemit-setassemblyrefprops-method.md)|Upraví zadanou `AssemblyRef` strukturu metadat.|  
|[SetExportedTypeProps – metoda](imetadataassemblyemit-setexportedtypeprops-method.md)|Upraví zadanou `ExportedType` strukturu metadat.|  
|[SetFileProps – metoda](imetadataassemblyemit-setfileprops-method.md)|Upraví zadanou `File` strukturu metadat.|  
|[SetManifestResourceProps – metoda](imetadataassemblyemit-setmanifestresourceprops-method.md)|Upraví zadanou `ManifestResource` strukturu metadat.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Rozhraní pro metadata](metadata-interfaces.md)
- [IMetaDataAssemblyImport – rozhraní](imetadataassemblyimport-interface.md)
