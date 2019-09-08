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
ms.openlocfilehash: b52d3af38bd09ce5864c25d27e148dbd7f4639b0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795443"
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
 pro Logický příznak, který označuje, že uživatel zadal sjednocení `pwzAssemblyIdentity1`pro.  
  
 `pwzAssemblyIdentity2`  
 pro Textová identita druhého sestavení v porovnání  
  
 `fUnified2`  
 pro Logický příznak, který označuje, že uživatel zadal sjednocení `pwzAssemblyIdentity2`pro.  
  
 `pfEquivalent`  
 mimo Logický příznak, který označuje, zda jsou dvě sestavení ekvivalentní.  
  
 `pResult`  
 mimo Výčet [AssemblyComparisonResult –](assemblycomparisonresult-enumeration.md) , který obsahuje podrobné informace o porovnání.  
  
## <a name="return-value"></a>Návratová hodnota  
 `pfEquivalent`vrací logickou hodnotu, která označuje, zda jsou dvě sestavení ekvivalentní. `pResult`Vrátí jednu z `AssemblyComparisonResult` hodnot, která poskytne podrobnější důvod pro `pfEquivalent`hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 `CompareAssemblyIdentity`kontroluje, `pwzAssemblyIdentity1` zda `pwzAssemblyIdentity2` a jsou ekvivalentní. `pfEquivalent`je nastaveno na `true` jednu nebo více z následujících podmínek:  
  
- Dvě identity sestavení jsou ekvivalentní. Pro silně pojmenovaná sestavení ekvivalence vyžaduje, aby byl název sestavení, verze, token veřejného klíče a jazyková verze identické. U jednoduše pojmenovaných sestavení vyžaduje ekvivalenci shodu s názvem sestavení a kulturou.  
  
- Obě identity sestavení odkazují na sestavení, která běží na .NET Framework. Tento stav vrátí `true` i v případě, že čísla verzí sestavení se neshodují.  
  
- Tato dvě sestavení nejsou spravovaná sestavení, ale `fUnified1` nebo `fUnified2` byla nastavena na `true`.  
  
 `fUnified` Příznak označuje, že všechna čísla verzí až do čísla verze sestavení se silným názvem se považují za ekvivalent sestavení se silným názvem. Pokud je například hodnota `pwzAssemblyIndentity1` "MyAssembly, Version = 3.0.0.0, Culture = neutral, PublicKeyToken =...." a `fUnified1` hodnota je `true`, znamená to, že by měly být všechny verze MyAssembly od verze 0.0.0.0 až 3.0.0.0. považován za ekvivalentní. Pokud `pwzAssemblyIndentity2` v takovém případě odkazuje na stejné sestavení jako `pwzAssemblyIndentity1`s tím rozdílem, že má nižší číslo verze, `pfEquivalent` je nastavena na `true`. Pokud `pwzAssemblyIdentity2` odkazuje na vyšší číslo verze, je `pfEquivalent` nastavena na `true` hodnotu pouze v případě, že `fUnified2` je `true`hodnota.  
  
 `pResult` Parametr zahrnuje konkrétní informace o tom, proč jsou tato dvě sestavení považována za ekvivalentní nebo neekvivalentní. Další informace najdete v tématu [výčet AssemblyComparisonResult –](assemblycomparisonresult-enumeration.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** Fusion. h  
  
 **Knihovna** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Globální statické funkce pro fúze](fusion-global-static-functions.md)
- [AssemblyComparisonResult – výčet](assemblycomparisonresult-enumeration.md)
