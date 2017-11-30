---
title: "IMetaDataAssemblyImport – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport
helpviewer_keywords: IMetaDataAssemblyImport interface [.NET Framework metadata]
ms.assetid: 29c6fba5-4cea-417d-b484-7ed22ebff1c9
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ef5b913dc9b1391c63cb123e1f922ca61da6a5bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataassemblyimport-interface"></a>IMetaDataAssemblyImport – rozhraní
Poskytuje metody pro přístup a kontrolu obsah manifestu sestavení.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Closeenum – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-closeenum-method.md)|Uvolní popisovač zadaný enumerátor.|  
|[Enumassemblyrefs – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumassemblyrefs-method.md)|Získá ukazatele rozhraní na enumerátor, který obsahuje `mdAssemblyRef` tokeny sestavení odkazuje sestavení v aktuálním oboru metadat.|  
|[Enumexportedtypes – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumexportedtypes-method.md)|Získá ukazatele rozhraní na enumerátor, který obsahuje `mdExportedType` tokeny typy modelu COM, odkazuje na sestavení v aktuálním oboru metadat.|  
|[Enumfiles – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumfiles-method.md)|Získá ukazatele rozhraní na enumerátor, který obsahuje `mdFile` tokeny souborů odkazuje sestavení v aktuálním oboru metadat.|  
|[Enummanifestresources – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enummanifestresources-method.md)|Získá ukazatele rozhraní na enumerátor, který obsahuje `mdManifestResource` tokeny prostředků odkazuje sestavení v aktuálním oboru metadat.|  
|[Findassembliesbyname – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findassembliesbyname-method.md)|Získá pole `mdAssemblyRef` tokeny pro sestavení se zadaným názvem.|  
|[Findexportedtypebyname – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findexportedtypebyname-method.md)|Získá `mdExportedType` tokenu pro typ COM se zadaným názvem.|  
|[Findmanifestresourcebyname – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findmanifestresourcebyname-method.md)|Získá `mdManifestResource` tokenu pro prostředek se zadaným názvem.|  
|[Getassemblyfromscope – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyfromscope-method.md)|Získá token pro sestavení v aktuálním oboru metadat.|  
|[Getassemblyprops – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyprops-method.md)|Získá nastavení vlastností zadaného sestavení.|  
|[Getassemblyrefprops – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyrefprops-method.md)|Získá nastavení vlastností zadaného `mdAssemblyRef` tokenu.|  
|[Getexportedtypeprops – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getexportedtypeprops-method.md)|Získá nastavení vlastností zadaného typu modelu COM.|  
|[Getfileprops – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getfileprops-method.md)|Získá nastavení vlastností zadaného souboru.|  
|[Getmanifestresourceprops – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getmanifestresourceprops-method.md)|Získá nastavení vlastností zadaného prostředku manifestu.|  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [Imetadataassemblyemit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
