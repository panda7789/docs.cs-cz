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
ms.openlocfilehash: e3cdb648397ca4f4aa2326e4f2349a5a14c3edcc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178295"
---
# <a name="assemblycomparisonresult-enumeration"></a>AssemblyComparisonResult – výčet
Označuje rovnocennost dvou identit sestavení, jak je určeno [CompareAssemblyIdentity](compareassemblyidentity-function.md) funkce.  
  
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
|`ACR_EquivalentFullMatch`|Označuje, že všechna pole sestavení v porovnání odpovídají.|  
|`ACR_EquivalentFXUnified`|Označuje, že sestavení jsou považovány za ekvivalentní na základě sjednocení čísla verzí sestavení v rozhraní .NET Framework verze 2.0 ve verzi CLR (CLR) ve společném jazyce.|  
|`ACR_EquivalentPartialFXUnified`|Označuje částečnou shodu sestavení na základě sjednocení CLR čísel verzí sestavení v rozhraní .NET Framework 2.0.|  
|`ACR_EquivalentPartialMatch`|Označuje částečnou shodu sestavení.|  
|`ACR_EquivalentPartialUnified`|Označuje částečnou shodu sestavení na základě staršího sjednocení čísel verzí.|  
|`ACR_EquivalentPartialWeakNamed`|Označuje částečnou shodu jednoduše pojmenovaných sestavení.|  
|`ACR_EquivalentUnified`|Označuje, že sestavení jsou považovány za ekvivalentní na základě clr sjednocení čísel verzí ve starších verzích rozhraní .NET Framework.|  
|`ACR_EquivalentWeakNamed`|Označuje shodu mezi dvěma jednoduše pojmenovanými sestaveními, jejichž čísla verzí byla ignorována.|  
|`ACR_NonEquivalent`|Označuje, že mezi dvěma sestaveními nedošlo k žádné shodě.|  
|`ACR_NonEquivalentPartialVersion`|Označuje, že dvě sestavení odpovídají s výjimkou jejich čísel verzí, které odpovídají pouze částečně.|  
|`ACR_NonEquivalentVersion`|Označuje, že dvě sestavení odpovídají s výjimkou jejich čísla verzí, které se neshodují.|  
|`ACR_Unknown`|Označuje, že důvod neekvivalence není znám.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** Fusion.h  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [CompareAssemblyIdentity – funkce](compareassemblyidentity-function.md)
- [Výčty fúzí](fusion-enumerations.md)
