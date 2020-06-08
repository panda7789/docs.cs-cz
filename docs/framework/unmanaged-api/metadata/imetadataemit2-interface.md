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
ms.openlocfilehash: 5a232f30da8812c6f3bd94647d74151312a8593b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493033"
---
# <a name="imetadataemit2-interface"></a>IMetaDataEmit2 – rozhraní
Rozšiřuje rozhraní [IMetaDataEmit](imetadataemit-interface.md) primárně tak, aby poskytovala schopnost pracovat s obecnými typy.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[DefineGenericParam – metoda](imetadataemit2-definegenericparam-method.md)|Vytvoří definici pro parametr obecného typu a získá token k tomuto parametru obecného typu.|  
|[DefineMethodSpec – metoda](imetadataemit2-definemethodspec-method.md)|Vytvoří obecnou instanci metody a získá do definice token.|  
|[GetDeltaSaveSize – metoda](imetadataemit2-getdeltasavesize-method.md)|Získá hodnotu označující rozdíl velikosti dat, který je potřeba k vyjádření změn pro aktuální relaci úprav a pokračování.|  
|[ResetENCLog – metoda](imetadataemit2-resetenclog-method.md)|Obnoví protokol Edit-and-Continue a spustí novou relaci.|  
|[SaveDelta – metoda](imetadataemit2-savedelta-method.md)|Uloží změny z aktuální relace úprav a pokračování do zadaného souboru.|  
|[SaveDeltaToMemory – metoda](imetadataemit2-savedeltatomemory-method.md)|Uloží změny z aktuální relace úprav a pokračování do paměti.|  
|[SaveDeltaToStream – metoda](imetadataemit2-savedeltatostream-method.md)|Uloží změny z aktuální relace úprav a pokračování do zadaného datového proudu.|  
|[SetGenericParamProps – metoda](imetadataemit2-setgenericparamprops-method.md)|Nastaví hodnoty vlastností pro definici obecného parametru, na kterou odkazuje zadaný token.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro metadata](metadata-interfaces.md)
- [IMetaDataEmit – rozhraní](imetadataemit-interface.md)
