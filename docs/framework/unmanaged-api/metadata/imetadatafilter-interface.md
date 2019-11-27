---
title: IMetaDataFilter – rozhraní
ms.date: 03/30/2017
api_name:
- IMetaDataFilter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter
helpviewer_keywords:
- IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: ec0856ef-8c56-40ba-bf60-86e0ce8b337f
topic_type:
- apiref
ms.openlocfilehash: e8b15f478eb3b94b7cdcab3b69d54e7cc99be13b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440162"
---
# <a name="imetadatafilter-interface"></a>IMetaDataFilter – rozhraní
Poskytuje metody pro označování a filtrování tokenů metadat, aby nedocházelo k opakujícím se akcím, které již byly provedeny.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IsTokenMarked – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-istokenmarked-method.md)|Získá hodnotu, která označuje, zda byl zpracován zadaný token metadat.|  
|[MarkToken – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-marktoken-method.md)|Nastaví hodnotu označující, že zadaný token metadat byl zpracován.|  
|[UnmarkAll – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-unmarkall-method.md)|Odstraní značky zpracování ze všech tokenů v aktuálním oboru metadat.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
