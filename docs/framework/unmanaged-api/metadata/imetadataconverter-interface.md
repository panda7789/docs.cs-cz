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
ms.openlocfilehash: b6ca7c619d32e69ffac20b80561171d0320db2d4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008375"
---
# <a name="imetadataconverter-interface"></a>IMetaDataConverter – rozhraní
Poskytuje metody pro mapování knihoven typů na signatury jejich metadat a jejich převod z jednoho na druhý.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[GetMetaDataFromTypeInfo – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypeinfo-method.md)|Získá ukazatel na instanci [IMetaDataImport](imetadataimport-interface.md) , která představuje signaturu metadat pro knihovnu typů, na kterou odkazuje zadaná `ITypeInfo` instance.|  
|[GetMetaDataFromTypeLib – metoda](imetadataconverter-getmetadatafromtypelib-method.md)|Získá ukazatel na `IMetaDataImport` instanci, která představuje signaturu metadat pro knihovnu typů reprezentované zadanou `ITypeLib` instancí.|  
|[GetTypeLibFromMetaData – metoda](imetadataconverter-gettypelibfrommetadata-method.md)|Získá ukazatel na `ITypeLib` instanci, která představuje knihovnu typů, která má zadaný název modulu a knihovny.|  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Rozhraní pro metadata](metadata-interfaces.md)
- [IMetaDataImport – rozhraní](imetadataimport-interface.md)
