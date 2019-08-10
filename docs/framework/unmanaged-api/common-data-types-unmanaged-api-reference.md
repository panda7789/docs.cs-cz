---
title: Běžné typy dat (referenční dokumentace nespravovaného rozhraní API)
ms.date: 03/30/2017
ms.assetid: e4ab2c4c-9433-4eba-9e9a-096de406cafb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b56840ce68caa3eed50773668c64e2622a646ddf
ms.sourcegitcommit: 46c68557bf6395f0ab9915f7558f2faae0097695
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68892075"
---
# <a name="common-data-types-unmanaged-api-reference"></a>Běžné typy dat (referenční dokumentace nespravovaného rozhraní API)
Toto téma obsahuje seznam jednoduchých datových typů používaných nespravovanými rozhraními API pro .NET Framework, které jsou definoványC++ `typedef` pomocí C/příkazy. Tyto datové typy jsou obvykle aliasy pro C++C++ /primitivní datové typy. Hodnoty těchto datových typů jsou obvykle neprůhledné; To znamená, že jsou vráceny určitou funkcí nebo metodou, aby mohly být předány jiným funkcím nebo metodám bez úprav.  
  
|Datový typ|Definice|Definováno v|Popis|  
|---------------|----------------|----------------|-----------------|  
|AppDomainID|`typedef UINT_PTR AppDomainID;`|corprof.h|Identifikátor domény aplikace|  
|AssemblyID|`typedef UINT_PTR AssemblyID;`|corprof.h|Identifikátor sestavení.|  
|ClassID|`typedef UINT_PTR ClassID;`|corprof.h|Identifikátor spravované třídy.|  
|CLRDATA_ADDRESS|`typedef ULONG64 CLRDATA_ADDRESS;`|ClrData. h|64 adresa paměti.|
|CLRDATA_ENUM|`typedef ULONG64 CLRDATA_ADDRESS;`|Není k dispozici|64 adresa paměti.|
|ID PŘIPOJENÍ|`typedef DWORD CONNID;`|CorDebug. h, Mscoree. h|Identifikátor připojení pro vlákno, které je připojeno k instanci Microsoft SQL Server.|  
|ContextID|`typedef UINT_PTR ContextID;`|corprof.h|Identifikátor kontextu přidruženého ke konkrétnímu spravovanému vláknu.|  
|COR_PRF_ELT_INFO|`typedef UINT_PTR COR_PRF_ELT_INFO;`|corprof.h|Neprůhledný popisovač, který představuje informace o konkrétním bloku zásobníku.|  
|COR_PRF_FRAME_INFO|`typedef UINT_PTR COR_PRF_FRAME_INFO;`|corprof.h|Neprůhledný popisovač, který odkazuje na rámec zásobníku. Je platná pouze během zpětného volání, na které je předáno.|  
|CORDB_ADDRESS|`typedef ULONG64 CORDB_ADDRESS;`|CorDebug. h|Adresa v paměti.|  
|CORDB_CONTINUE_STATUS|`typedef DWORD CORDB_CONTINUE_STATUS;`|CorDebug. h|Stav pokračování.|  
|CORDB_REGISTER|`typedef ULONG64 CORDB_REGISTER;`|CorDebug. h|Hodnota registru procesoru.|
|FunctionID|`typedef UINT_PTR FunctionID;`|corprof.h|Identifikátor funkce nebo metody.|  
|GCHandleID|`typedef UINT_PTR GCHandleID;`|corprof.h|Popisovač uvolňování paměti.|  
|mdMethodDef|`typedef mdToken mdMethodDef;`|CorDebug. h|Token definice metody.|
|mdToken|`typedef UINT32 mdToken;`|corprof.h|Token metadat (řádek v tabulce metadat).|  
|ModuleID|`typedef UINT_PTR ModuleID;`|corprof.h|Identifikátor modulu sestavení|  
|Objektu|`typedef UINT_PTR ObjectID;`|corprof.h|Identifikátor objektu.|  
|PCCOR_SIGNATURE|`typedef SIZE_T PCCOR_SIGNATURE;`|CorDebug. h|Ukazatel na signaturu členu nebo metadat.|
|ProcessID|`typedef UINT_PTR ProcessID;`|corprof.h|Identifikátor spravovaného procesu.|  
|ReJITID|`typedef UINT_PTR ReJITID;`|corprof.h|Identifikátor funkce zpracovaných kompilátorem JIT|  
|SIZE_T|`typedef ULONG_PTR SIZE_T;`|CorSym. h|Ukazatel na 64ovou adresu paměti.|
|TASKID|`typedef UINT64 TASKID;`|CorDebug. h, Mscoree. h|Identifikátor instance [ICLRTask](../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)|  
|IDvlákna|`typedef UINT_PTR ThreadID;`|corprof.h|Identifikátor spravovaného vlákna.|  
  
## <a name="see-also"></a>Viz také:

- [Referenční informace o nespravovaném rozhraní API](../../../docs/framework/unmanaged-api/index.md)
