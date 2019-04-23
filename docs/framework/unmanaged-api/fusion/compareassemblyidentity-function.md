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
ms.openlocfilehash: 652000367c19572f73296c704047830ce1c74574
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59231035"
---
# <a name="compareassemblyidentity-function"></a>CompareAssemblyIdentity – funkce
Porovná dvě identit sestavení pro určení, zda jsou ekvivalentní.  
  
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
  
## <a name="parameters"></a>Parametry  
 `pwzAssemblyIdentity1`  
 [in] Textovou identitu první sestavení v porovnání.  
  
 `fUnified1`  
 [in] Příznak logické hodnoty označující sjednocení zadané uživatelem pro `pwzAssemblyIdentity1`.  
  
 `pwzAssemblyIdentity2`  
 [in] Textovou identitu druhou sestavení v porovnání.  
  
 `fUnified2`  
 [in] Příznak logické hodnoty označující sjednocení zadané uživatelem pro `pwzAssemblyIdentity2`.  
  
 `pfEquivalent`  
 [out] Logický příznak, který určuje, zda daná dvě sestavení jsou ekvivalentní.  
  
 `pResult`  
 [out] [Assemblycomparisonresult –](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md) výčet, který obsahuje podrobné informace o porovnání.  
  
## <a name="return-value"></a>Návratová hodnota  
 `pfEquivalent` Vrátí logickou hodnotu, která určuje, zda daná dvě sestavení jsou ekvivalentní. `pResult` Vrátí jednu z `AssemblyComparisonResult` hodnot, které se poskytují podrobnější důvod pro hodnotu vlastnosti `pfEquivalent`.  
  
## <a name="remarks"></a>Poznámky  
 `CompareAssemblyIdentity` kontroluje, zda `pwzAssemblyIdentity1` a `pwzAssemblyIdentity2` jsou ekvivalentní. `pfEquivalent` je nastavena na `true` v jedné nebo více z následujících podmínek:  
  
-   Identity dvě sestavení jsou ekvivalentní. Pro sestavení se silným názvem referenčních materiálech o ekvivalenci vyžaduje název sestavení, verzi, token veřejného klíče a jazykovou verzi být identické. Pro sestavení s jednoduchým názvem referenčních materiálech o ekvivalenci vyžaduje shodu v názvu sestavení a jazykovou verzi.  
  
-   Obě identit sestavení odkazovat na sestavení, které běží na rozhraní .NET Framework. Tato podmínka vrátí `true` i v případě, že číslo verze sestavení se neshodují.  
  
-   Tato dvě sestavení nejsou spravovaná sestavení, ale `fUnified1` nebo `fUnified2` byl nastaven na `true`.  
  
 `fUnified` Příznak určuje, že všechna čísla verzí až číslo verze sestavení se silným názvem jsou považovány za ekvivalentní k sestavení se silným názvem. Například pokud hodnota `pwzAssemblyIndentity1` je "MyAssembly, verze = 3.0.0.0, jazyková verze = neutral, publicKeyToken =..." a hodnota `fUnified1` je `true`, to znamená, že by měl být všechny verze MyAssembly z verze 0.0.0.0 k 3.0.0.0 považovány za ekvivalentní. V takovém případě pokud `pwzAssemblyIndentity2` odkazuje na stejné sestavení jako `pwzAssemblyIndentity1`, s tím rozdílem, že má nižší číslo verze, `pfEquivalent` je nastavena na `true`. Pokud `pwzAssemblyIdentity2` odkazuje na vyšší číslo verze `pfEquivalent` je nastavena na `true` pouze tehdy, pokud hodnota `fUnified2` je `true`.  
  
 `pResult` Parametr obsahuje konkrétní informace o proč dvě sestavení jsou považovány za ekvivalentní, nebo není ekvivalentní. Další informace najdete v tématu [assemblycomparisonresult – výčet](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Fusion.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Globální statické funkce pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
- [AssemblyComparisonResult – výčet](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md)
