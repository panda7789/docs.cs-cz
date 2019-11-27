---
title: IMetaDataEmit2 – rozhraní
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2
helpviewer_keywords:
- IMetaDataEmit2 interface [.NET Framework metadata]
ms.assetid: 866dc96b-bbfc-4c0f-80c2-38ce93072106
topic_type:
- apiref
ms.openlocfilehash: 7ceae6f7713ab0eb1feff550838325df0ea52de2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447913"
---
# <a name="imetadataemit2-interface"></a>IMetaDataEmit2 – rozhraní
Rozšiřuje rozhraní [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) primárně tak, aby poskytovala schopnost pracovat s obecnými typy.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[DefineGenericParam – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)|Vytvoří definici pro parametr obecného typu a získá token k tomuto parametru obecného typu.|  
|[DefineMethodSpec – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md)|Vytvoří obecnou instanci metody a získá do definice token.|  
|[GetDeltaSaveSize – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md)|Získá hodnotu označující rozdíl velikosti dat, který je potřeba k vyjádření změn pro aktuální relaci úprav a pokračování.|  
|[ResetENCLog – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md)|Obnoví protokol Edit-and-Continue a spustí novou relaci.|  
|[SaveDelta – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedelta-method.md)|Uloží změny z aktuální relace úprav a pokračování do zadaného souboru.|  
|[SaveDeltaToMemory – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)|Uloží změny z aktuální relace úprav a pokračování do paměti.|  
|[SaveDeltaToStream – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatostream-method.md)|Uloží změny z aktuální relace úprav a pokračování do zadaného datového proudu.|  
|[SetGenericParamProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-setgenericparamprops-method.md)|Nastaví hodnoty vlastností pro definici obecného parametru, na kterou odkazuje zadaný token.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
