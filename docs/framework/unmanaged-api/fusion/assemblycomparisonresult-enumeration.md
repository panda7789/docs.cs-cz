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
ms.openlocfilehash: 82b81ec29dece182548ead046edc7cb754fbf00e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="assemblycomparisonresult-enumeration"></a>AssemblyComparisonResult – výčet
Označuje ekvivalenční dvě sestavení identit, počítáno od [compareassemblyidentity –](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md) funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`ACR_EquivalentFullMatch`|Označuje, že všechny sestavení polí v porovnání shody.|  
|`ACR_EquivalentFXUnified`|Označuje, že sestavení jsou považovány za ekvivalentní založené na běžné sjednocením runtime verze (CLR) jazyk čísla verzí sestavení v rozhraní .NET Framework verze 2.0.|  
|`ACR_EquivalentPartialFXUnified`|Označuje částečnou shodu sestavení podle CLR sjednocením čísla verzí sestavení v rozhraní .NET Framework 2.0.|  
|`ACR_EquivalentPartialMatch`|Označuje částečnou shodu sestavení.|  
|`ACR_EquivalentPartialUnified`|Označuje částečnou shodu sestavení založené na starší verze sjednocení čísla verzí.|  
|`ACR_EquivalentPartialWeakNamed`|Označuje částečnou shodu jednoduše pojmenované sestavení.|  
|`ACR_EquivalentUnified`|Označuje, že sestavení jsou považovány za ekvivalentní podle sjednocení CLR verze čísel ve starších verzích rozhraní .NET Framework.|  
|`ACR_EquivalentWeakNamed`|Označuje shodu mezi dvěma jednoduše pojmenované sestavení jejichž čísla verzí byly ignorovány.|  
|`ACR_NonEquivalent`|Označuje, že žádná shoda došlo mezi dvěma sestavení.|  
|`ACR_NonEquivalentPartialVersion`|Označuje, že dvě sestavení shodovat s výjimkou jejich čísla verzí, které se shodují jen částečně.|  
|`ACR_NonEquivalentVersion`|Označuje, že dvě sestavení shodovat s výjimkou jejich čísla verzí, které se neshodují.|  
|`ACR_Unknown`|Označuje, že důvod zajištění rovnocennosti není znám.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Fusion.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [CompareAssemblyIdentity – funkce](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)  
 [Výčty pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
