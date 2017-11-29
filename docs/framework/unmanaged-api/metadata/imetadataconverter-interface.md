---
title: "IMetaDataConverter – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataConverter
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataConverter
helpviewer_keywords: IMetaDataConverter interface [.NET Framework metadata]
ms.assetid: 9caea662-0167-4267-b14a-2fa42c3be4ea
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f551a774a860f595cc90a7cca9eee2c726ef50ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataconverter-interface"></a>IMetaDataConverter – rozhraní
Poskytuje metody pro mapování knihoven typů do jejich signatur metadata a převést z jeden na druhý.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Getmetadatafromtypeinfo – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypeinfo-method.md)|Získá odkazy [imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instanci, která představuje metadata podpis pro knihovny typů, který odkazuje zadaný `ITypeInfo` instance.|  
|[Getmetadatafromtypelib – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypelib-method.md)|Získá odkazy `IMetaDataImport` instanci, která představuje metadata podpis pro knihovny typů reprezentována zadaný `ITypeLib` instance.|  
|[Gettypelibfrommetadata – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-gettypelibfrommetadata-method.md)|Získá odkazy `ITypeLib` instanci, která představuje knihovny typů, který má zadané názvy modulu a knihovny.|  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [Imetadataimport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
