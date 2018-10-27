---
title: Běžné typy dat (referenční dokumentace nespravovaného rozhraní API)
ms.date: 03/30/2017
ms.assetid: e4ab2c4c-9433-4eba-9e9a-096de406cafb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 561a6a5a8e778ab59a0d0f1f7f5327104ead2c79
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185531"
---
# <a name="common-data-types-unmanaged-api-reference"></a>Běžné typy dat (referenční dokumentace nespravovaného rozhraní API)
Toto téma obsahuje seznam jednoduché datové typy používají nespravované rozhraní API pro rozhraní .NET Framework, které jsou definovány pomocí jazyka C/C++ `typedef` příkazy. Tyto datové typy jsou obvykle aliasy pro C/C++ primitivní datové typy. Obvykle jsou neprůhledné; hodnoty těchto datových typů To znamená že jsou vrácené konkrétní funkce nebo metoda tak, aby se mohou být předány jiné funkce nebo metody bez úprav.  
  
|Datový typ|Definice|Definované v|Popis|  
|---------------|----------------|----------------|-----------------|  
|AppDomainID|`typedef UINT_PTR AppDomainID;`|corprof.h|Identifikátor domény aplikace.|  
|AssemblyID|`typedef UINT_PTR AssemblyID;`|corprof.h|Identifikátor sestavení.|  
|ID třídy|`typedef UINT_PTR ClassID;`|corprof.h|Identifikátor spravované třídy.|  
|CONNID|`typedef DWORD CONNID;`|cordebug.h, mscoree.h|Identifikátor připojení pro vlákno, které je připojený k instanci systému Microsoft SQL Server.|  
|contextID|`typedef UINT_PTR ContextID;`|corprof.h|Identifikátor kontext přidružený k konkrétní spravované vlákno.|  
|COR_PRF_ELT_INFO|`typedef UINT_PTR COR_PRF_ELT_INFO;`|corprof.h|Neprůhledný popisovač, který představuje informace o konkrétní rámec zásobníku.|  
|COR_PRF_FRAME_INFO|`typedef UINT_PTR COR_PRF_FRAME_INFO;`|corprof.h|Neprůhledné zpracovat, na kterou odkazuje na blok zásobníku. Je platný pouze během zpětného volání, který je předán.|  
|CORDB_ADDRESS|`typedef ULONG64 CORDB_ADDRESS;`|cordebug.h|Adresy v paměti.|  
|CORDB_CONTINUE_STATUS|`typedef DWORD CORDB_CONTINUE_STATUS;`|cordebug.h|Stav pokračování.|  
|CORDB_REGISTER|`typedef ULONG64 CORDB_REGISTER;`|cordebug.h|Hodnota registru procesoru.|  
|FunctionID|`typedef UINT_PTR FunctionID;`|corprof.h|Identifikátor funkce nebo metody.|  
|GCHandleID|`typedef UINT_PTR GCHandleID;`|corprof.h|Popisovač kolekce uvolnění paměti.|  
|mdToken|`typedef UINT32 mdToken;`|corprof.h|Token metadat (řádek v tabulce metadata).|  
|ID modulu|`typedef UINT_PTR ModuleID;`|corprof.h|Identifikátor modulu sestavení.|  
|ID objektu|`typedef UINT_PTR ObjectID;`|corprof.h|Identifikátor objektu.|  
|ID procesu|`typedef UINT_PTR ProcessID;`|corprof.h|Identifikátor spravovaného procesu.|  
|ReJITID|`typedef UINT_PTR ReJITID;`|corprof.h|Identifikátor funkce zpracovaných kompilátorem JIT.|  
|TASKID|`typedef UINT64 TASKID;`|cordebug.h, mscoree.h|Identifikátor [iclrtask –](../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.|  
|Idvlákna|`typedef UINT_PTR ThreadID;`|corprof.h|Identifikátor spravované vlákno.|  
  
## <a name="see-also"></a>Viz také  
- [Referenční informace o nespravovaném rozhraní API](../../../docs/framework/unmanaged-api/index.md)
