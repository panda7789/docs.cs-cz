---
title: "Běžné typy dat (referenční dokumentace nespravovaného rozhraní API)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: e4ab2c4c-9433-4eba-9e9a-096de406cafb
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a565ec6ded0a82ed4ab3c0fd03b082d996369ddc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="common-data-types-unmanaged-api-reference"></a>Běžné typy dat (referenční dokumentace nespravovaného rozhraní API)
Toto téma obsahuje seznam jednoduché datové typy používané nespravovaná rozhraní API pro rozhraní .NET Framework, které jsou definovány pomocí jazyka C/C++ `typedef` příkazy. Tyto datové typy jsou obvykle aliasy pro C/C++ primitivní datové typy. Hodnoty tyto datové typy jsou obvykle neprůhledného; To znamená jsou vrácena určitou funkci nebo metodu tak, aby se dá předat do jiné funkce nebo metody bez úprav.  
  
|Datový typ|Definice|Definované v|Popis|  
|---------------|----------------|----------------|-----------------|  
|AppDomainID|`typedef UINT_PTR AppDomainID;`|corprof.h|Identifikátor domény aplikace.|  
|AssemblyID|`typedef UINT_PTR AssemblyID;`|corprof.h|Identifikátor sestavení.|  
|ID třídy|`typedef UINT_PTR ClassID;`|corprof.h|Identifikátor spravované třídy.|  
|CONNID|`typedef DWORD CONNID;`|cordebug.h, mscoree.h|Identifikátor připojení pro vlákno, které je připojen k instanci serveru Microsoft SQL Server.|  
|ID|`typedef UINT_PTR ContextID;`|corprof.h|Identifikátor kontext přidružený konkrétní spravované vlákno.|  
|COR_PRF_ELT_INFO|`typedef UINT_PTR COR_PRF_ELT_INFO;`|corprof.h|Neprůhledného popisovače, který představuje informace o konkrétní zásobníku.|  
|COR_PRF_FRAME_INFO|`typedef UINT_PTR COR_PRF_FRAME_INFO;`|corprof.h|Neprůhledné zpracování této odkazuje na rámec zásobníku. Je platná pouze během zpětného volání, ke kterému je předán.|  
|CORDB_ADDRESS|`typedef ULONG64 CORDB_ADDRESS;`|cordebug.h|Adresu v paměti.|  
|CORDB_CONTINUE_STATUS|`typedef DWORD CORDB_CONTINUE_STATUS;`|cordebug.h|Stav pokračování.|  
|CORDB_REGISTER|`typedef ULONG64 CORDB_REGISTER;`|cordebug.h|Hodnota registru procesoru.|  
|FunctionID|`typedef UINT_PTR FunctionID;`|corprof.h|Identifikátor funkci nebo metodu.|  
|GCHandleID|`typedef UINT_PTR GCHandleID;`|corprof.h|Obslužná rutina kolekce paměti.|  
|mdToken|`typedef UINT32 mdToken;`|corprof.h|Token metadat (řádek v tabulce metadata).|  
|ID modulu|`typedef UINT_PTR ModuleID;`|corprof.h|Identifikátor modul sestavení.|  
|ObjectID|`typedef UINT_PTR ObjectID;`|corprof.h|Identifikátor objektu.|  
|ID procesu|`typedef UINT_PTR ProcessID;`|corprof.h|Identifikátor spravovaného procesu.|  
|ReJITID|`typedef UINT_PTR ReJITID;`|corprof.h|Identifikátor jitted funkce.|  
|TASKID|`typedef UINT64 TASKID;`|cordebug.h, mscoree.h|Identifikátor [iclrtask –](../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.|  
|ID podprocesu|`typedef UINT_PTR ThreadID;`|corprof.h|Identifikátor spravované vlákno.|  
  
## <a name="see-also"></a>Viz také  
 [Referenční informace o nespravovaném rozhraní API](../../../docs/framework/unmanaged-api/index.md)
