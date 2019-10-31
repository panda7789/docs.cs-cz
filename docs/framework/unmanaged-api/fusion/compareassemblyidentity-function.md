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
ms.openlocfilehash: f6711902fb9d5c5c16084057b731746843cf0230
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108912"
---
# <a name="compareassemblyidentity-function"></a>CompareAssemblyIdentity – funkce
Porovná dvě identity sestavení a určí, zda jsou ekvivalentní.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
 pro Textová identita prvního sestavení v porovnání  
  
 `fUnified1`  
 pro Logický příznak, který označuje, že uživatel zadal sjednocení pro `pwzAssemblyIdentity1`.  
  
 `pwzAssemblyIdentity2`  
 pro Textová identita druhého sestavení v porovnání  
  
 `fUnified2`  
 pro Logický příznak, který označuje, že uživatel zadal sjednocení pro `pwzAssemblyIdentity2`.  
  
 `pfEquivalent`  
 mimo Logický příznak, který označuje, zda jsou dvě sestavení ekvivalentní.  
  
 `pResult`  
 mimo Výčet [AssemblyComparisonResult –](assemblycomparisonresult-enumeration.md) , který obsahuje podrobné informace o porovnání.  
  
## <a name="return-value"></a>Návratová hodnota  
 `pfEquivalent` vrací logickou hodnotu, která označuje, zda jsou dvě sestavení ekvivalentní. `pResult` vrátí jednu z hodnot `AssemblyComparisonResult` a poskytne podrobnější důvod pro hodnotu `pfEquivalent`.  
  
## <a name="remarks"></a>Poznámky  
 `CompareAssemblyIdentity` kontroluje, zda jsou `pwzAssemblyIdentity1` a `pwzAssemblyIdentity2` ekvivalentní. `pfEquivalent` je nastavené na `true` v jedné nebo několika následujících podmínkách:  
  
- Dvě identity sestavení jsou ekvivalentní. Pro silně pojmenovaná sestavení ekvivalence vyžaduje, aby byl název sestavení, verze, token veřejného klíče a jazyková verze identické. U jednoduše pojmenovaných sestavení vyžaduje ekvivalenci shodu s názvem sestavení a kulturou.  
  
- Obě identity sestavení odkazují na sestavení, která běží na .NET Framework. Tento stav vrátí `true` i v případě, že čísla verzí sestavení se neshodují.  
  
- Tato dvě sestavení nejsou spravovaná sestavení, ale `fUnified1` nebo `fUnified2` byla nastavena na `true`.  
  
 Příznak `fUnified` označuje, že všechna čísla verzí až do čísla verze sestavení se silným názvem se považují za ekvivalentní silně pojmenovanému sestavení. Pokud je například hodnota `pwzAssemblyIndentity1` "MyAssembly, Version = 3.0.0.0, Culture = neutral, publicKeyToken =...." a hodnota `fUnified1` je `true`, znamená to, že všechny verze MyAssembly z verze 0.0.0.0 na 3.0.0.0 by měly být považovány za stejného. V takovém případě, pokud `pwzAssemblyIndentity2` odkazuje na stejné sestavení jako `pwzAssemblyIndentity1`, s tím rozdílem, že má nižší číslo verze, `pfEquivalent` je nastavena na `true`. Pokud `pwzAssemblyIdentity2` odkazuje na vyšší číslo verze, `pfEquivalent` je nastaveno na `true` pouze v případě, že je `true`hodnota `fUnified2`.  
  
 Parametr `pResult` obsahuje konkrétní informace o tom, proč jsou tato dvě sestavení považována za ekvivalentní nebo neekvivalentní. Další informace najdete v tématu [výčet AssemblyComparisonResult –](assemblycomparisonresult-enumeration.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Fusion. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Globální statické funkce pro fúze](fusion-global-static-functions.md)
- [AssemblyComparisonResult – výčet](assemblycomparisonresult-enumeration.md)
