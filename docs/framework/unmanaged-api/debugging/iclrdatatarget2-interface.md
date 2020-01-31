---
title: ICLRDataTarget2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2
helpviewer_keywords:
- ICLRDataTarget2 interface [.NET Framework debugging]
ms.assetid: 94249397-861b-4294-a538-cf01466a66d3
topic_type:
- apiref
ms.openlocfilehash: bdc8378a129dd5bb1d9fdcb080c7b5cd53d34091
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789079"
---
# <a name="iclrdatatarget2-interface"></a>ICLRDataTarget2 – rozhraní
Podtřída [ICLRDataTarget](iclrdatatarget-interface.md) , která je používána vrstvou služeb přístupu k datům k manipulaci s oblastmi virtuální paměti v cílovém procesu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[AllocVirtual – metoda](iclrdatatarget2-allocvirtual-method.md)|Přidělí paměť v adresním prostoru cílového procesu.|  
|[FreeVirtual – metoda](iclrdatatarget2-freevirtual-method.md)|Uvolní paměť, která byla dříve přidělena v adresním prostoru cílového procesu.|  
  
## <a name="remarks"></a>Poznámky  
 Klient API (tzn. ladicí program) musí implementovat toto rozhraní v závislosti na konkrétním cílovém procesu. Například živý proces bude mít jinou implementaci než výpis paměti. Cíl nemusí podporovat změny jeho oblastí paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** ClrData. idl, ClrData. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRDataTarget – rozhraní](iclrdatatarget-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
