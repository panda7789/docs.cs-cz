---
title: AssemblyComparisonResult – výčet
ms.date: 03/30/2017
api_name:
- AssemblyComparisonResult
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- AssemblyComparisonResult
helpviewer_keywords:
- AssemblyComparisonResult enumeration [.NET Framework fusion]
ms.assetid: bd042f89-10b1-40ca-946e-46da082f5263
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6c417eec9583ff069c9d61fa31e9c14f3931130
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778505"
---
# <a name="assemblycomparisonresult-enumeration"></a>AssemblyComparisonResult – výčet
Označuje ekvivalence dvě sestavení identity, počítáno od [compareassemblyidentity –](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md) funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum _tagAssemblyComparisonResult {  
    ACR_Unknown,   
    ACR_EquivalentFullMatch,  
    ACR_EquivalentWeakNamed,  
    ACR_EquivalentFXUnified,  
    ACR_EquivalentUnified,    
    ACR_NonEquivalentVersion,  
    ACR_NonEquivalent,      
    ACR_EquivalentPartialMatch,  
    ACR_EquivalentPartialWeakNamed,    
    ACR_EquivalentPartialUnified,  
    ACR_EquivalentPartialFXUnified,  
    ACR_NonEquivalentPartialVersion    
} AssemblyComparisonResult;  
```  
  
## <a name="members"></a>Členové  
  
|Název členu|Popis|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|Označuje, že všechna sestavení pole v porovnání shody.|  
|`ACR_EquivalentFXUnified`|Označuje, že sestavení jsou považovány za ekvivalentní založené na běžných sjednocení modul runtime verze (CLR) jazyka čísla verze sestavení v rozhraní .NET Framework verze 2.0.|  
|`ACR_EquivalentPartialFXUnified`|Označuje částečnou shodu sestavení založená na modulu CLR sjednocení čísla verze sestavení v rozhraní .NET Framework 2.0.|  
|`ACR_EquivalentPartialMatch`|Označuje částečnou shodu sestavení.|  
|`ACR_EquivalentPartialUnified`|Označuje částečnou shodu sestavení založená na starší verzi sjednocení čísla verzí.|  
|`ACR_EquivalentPartialWeakNamed`|Označuje částečnou shodu s jednoduchým názvem sestavení.|  
|`ACR_EquivalentUnified`|Označuje, že sestavení jsou považovány za ekvivalentní podle sjednocení CLR verze čísel ve starších verzích rozhraní .NET Framework.|  
|`ACR_EquivalentWeakNamed`|Označuje shodu mezi dvěma s jednoduchým názvem sestavení, jejichž čísla verze byly ignorovány.|  
|`ACR_NonEquivalent`|Označuje, že žádná shoda, která proběhla mezi dvě sestavení.|  
|`ACR_NonEquivalentPartialVersion`|Označuje, že daná dvě sestavení shodovat s výjimkou čísla verze, které se shodují jen částečně.|  
|`ACR_NonEquivalentVersion`|Označuje, že tato dvě sestavení shodovat s výjimkou jejich čísla verzí, které se neshodují.|  
|`ACR_Unknown`|Označuje, že-do referenčních materiálech o ekvivalenci důvod není znám.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Fusion.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [CompareAssemblyIdentity – funkce](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)
- [Výčty pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
