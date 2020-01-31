---
title: ICLRDataEnumMemoryRegionsCallback – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegionsCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegionsCallback
helpviewer_keywords:
- ICLRDataEnumMemoryRegionsCallback interface [.NET Framework debugging]
ms.assetid: 3f1af8b0-8478-48e0-a7ec-3e90e0b97649
topic_type:
- apiref
ms.openlocfilehash: 4e3891996af5945ed95c8c37dddfee5c446db248
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789112"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a>ICLRDataEnumMemoryRegionsCallback – rozhraní
Poskytuje metodu zpětného volání pro [ICLRDataEnumMemoryRegions –:: EnumMemoryRegions –](iclrdataenummemoryregions-enummemoryregions-method.md) , která oznamuje ladicímu programu výsledek pokusu o vytvoření výčtu konkrétní oblasti paměti.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumMemoryRegion – metoda](iclrdataenummemoryregionscallback-enummemoryregion-method.md)|Volá se `ICLRDataEnumMemoryRegions::EnumMemoryRegions`, aby se nahlásila ladicímu programu v důsledku pokusu o vytvoření výčtu konkrétní oblasti paměti.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** ClrData. idl, ClrData. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
