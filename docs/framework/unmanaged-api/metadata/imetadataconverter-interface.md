---
title: IMetaDataConverter – rozhraní
ms.date: 03/30/2017
api_name:
- IMetaDataConverter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter
helpviewer_keywords:
- IMetaDataConverter interface [.NET Framework metadata]
ms.assetid: 9caea662-0167-4267-b14a-2fa42c3be4ea
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3d3377617ddd6b82ad88d22f6ffda04b1d6ae837
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61904745"
---
# <a name="imetadataconverter-interface"></a>IMetaDataConverter – rozhraní
Poskytuje metody pro mapování knihovny typů na jejich podpisy metadat a pro převod z jednoho na druhý.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetMetaDataFromTypeInfo – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypeinfo-method.md)|Získá ukazatel [imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instanci, která představuje podpis metadat pro knihovnu typů odkazuje zadaný `ITypeInfo` instance.|  
|[GetMetaDataFromTypeLib – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypelib-method.md)|Získá ukazatel na `IMetaDataImport` instanci, která představuje podpis metadat pro knihovnu typů reprezentována zadaný `ITypeLib` instance.|  
|[GetTypeLibFromMetaData – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-gettypelibfrommetadata-method.md)|Získá ukazatel `ITypeLib` instanci, která představuje knihovnu typů, který má zadané názvy modulů a knihovna.|  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
