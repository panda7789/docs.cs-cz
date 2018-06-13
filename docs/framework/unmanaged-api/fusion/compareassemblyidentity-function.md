---
title: CompareAssemblyIdentity – funkce
ms.date: 03/30/2017
api_name:
- CompareAssemblyIdentity
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- CompareAssemblyIdentity
helpviewer_keywords:
- CompareAssemblyIdentity function [.NET Framework fusion]
ms.assetid: 8b364ae1-8efa-4744-a7da-81fd093d84d6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b48adcb8e9de49a312af77c8a9b80a07455ebfe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432983"
---
# <a name="compareassemblyidentity-function"></a>CompareAssemblyIdentity – funkce
Porovná dvě sestavení identity zjistěte, zda jsou ekvivalentní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI CompareAssemblyIdentity (  
    [in]  LPCWSTR                  pwzAssemblyIdentity1,  
    [in]  BOOL                     fUnified1,  
    [in]  LPCWSTR                  pwzAssemblyIdentity2,  
    [in]  BOOL                     fUnified2,  
    [out] BOOL                     *pfEquivalent,  
    [out] AssemblyComparisonResult *pResult  
 );  
```  
  
#### <a name="parameters"></a>Parametry  
 `pwzAssemblyIdentity1`  
 [v] Textové identita první sestavení v porovnání.  
  
 `fUnified1`  
 [v] Logický příznak, který označuje sjednocení zadané uživatelem pro `pwzAssemblyIdentity1`.  
  
 `pwzAssemblyIdentity2`  
 [v] Textové identita druhý sestavení v porovnání.  
  
 `fUnified2`  
 [v] Logický příznak, který označuje sjednocení zadané uživatelem pro `pwzAssemblyIdentity2`.  
  
 `pfEquivalent`  
 [out] Logický příznak, který určuje, zda jsou dvě sestavení ekvivalentní.  
  
 `pResult`  
 [out] [AssemblyComparisonResult](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md) výčet, který obsahuje podrobné informace o porovnání.  
  
## <a name="return-value"></a>Návratová hodnota  
 `pfEquivalent` Vrátí logickou hodnotu, která určuje, zda jsou dvě sestavení ekvivalentní. `pResult` Vrátí jednu z `AssemblyComparisonResult` hodnoty uvést podrobnější důvod pro hodnotu `pfEquivalent`.  
  
## <a name="remarks"></a>Poznámky  
 `CompareAssemblyIdentity` kontroluje, zda `pwzAssemblyIdentity1` a `pwzAssemblyIdentity2` odpovídají. `pfEquivalent` je nastavena na `true` pod jednou nebo více z následujících podmínek:  
  
-   Identity dvě sestavení jsou ekvivalentní. Pro sestavení se silným názvem zajištění rovnocennosti vyžaduje název sestavení, verzi, token veřejného klíče a jazykovou verzi, která shodovat. Jednoduše pojmenované sestavení zajištění rovnocennosti vyžaduje shoda s název sestavení a jazykovou verzi.  
  
-   Obě sestavení identity naleznete na sestavení, které běží na rozhraní .NET Framework. Tato podmínka vrátí `true` i v případě, že číslo verze sestavení se neshodují.  
  
-   Dvě sestavení nejsou spravovaná sestavení, ale `fUnified1` nebo `fUnified2` byla nastavena na `true`.  
  
 `fUnified` Příznak označuje, že všechna čísla verze až číslo verze sestavení silným názvem jsou považovány za ekvivalentní silně pojmenované sestavení. Například pokud hodnota `pwzAssemblyIndentity1` je "MyAssembly, verze = 3.0.0.0, culture = neutral, publicKeyToken =..." a hodnotu `fUnified1` je `true`, to znamená, že by měl být všechny verze MyAssembly z verze 0.0.0.0 k 3.0.0.0 považovány za ekvivalentní. V takovém případě pokud `pwzAssemblyIndentity2` odkazuje na stejném sestavení jako `pwzAssemblyIndentity1`kromě toho, že má nižší číslo verze, `pfEquivalent` je nastaven na `true`. Pokud `pwzAssemblyIdentity2` odkazuje na vyšší číslo verze, `pfEquivalent` je nastaven na `true` pouze v případě hodnotu `fUnified2` je `true`.  
  
 `pResult` Parametr obsahuje konkrétní informace o proč dvou sestavení jsou považovány za ekvivalentní, nebo není ekvivalentní. Další informace najdete v tématu [AssemblyComparisonResult – výčet](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Fusion.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Globální statické funkce pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
 [AssemblyComparisonResult – výčet](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md)
