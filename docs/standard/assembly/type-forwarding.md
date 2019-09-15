---
title: Předávání typů v modulu CLR (Common Language Runtime)
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- cpp
ms.openlocfilehash: f71b56daf5e8a012a66f60805246b4164d1b0a07
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973017"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a>Předávání typů v modulu CLR (Common Language Runtime)
Přesměrování typu umožňuje přesunout typ do jiného sestavení bez nutnosti opětovné kompilace aplikací, které používají původní sestavení.  
  
 Předpokládejme například, že aplikace používá `Example` třídu v sestavení s názvem *Utility. dll*. Vývojáři *nástroje Utility. dll* se mohou rozhodnout Refaktorovat sestavení a v procesu, který by mohli `Example` třídu přesunout do jiného sestavení. Pokud je stará verze souboru *Utility. dll* nahrazena novou verzí *nástroje Utility. dll* a jeho doprovodném sestavením, aplikace `Example` , která třídu používá, se `Example` nezdařila, protože nemůže najít třídu v nové verzi  *Nástroj. dll*.  
  
 Vývojáři *nástroje Utility. dll* se k tomu mohou vyhnout přesměrováním požadavků `Example` pro <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> třídu pomocí atributu. Pokud byl atribut použit pro novou verzi *nástroje Utility. dll*, požadavky `Example` na třídu jsou předány sestavení, které nyní obsahuje třídu. Stávající aplikace bude nadále fungovat normálně bez nutnosti rekompilace.  
  
> [!NOTE]
> V .NET Framework verze 2,0 nemůžete předávané typy ze sestavení napsaných v Visual Basic. Aplikace napsaná v Visual Basic však může využívat předané typy. To znamená, že pokud aplikace používá sestavení kódované v C# nebo C++a typ z tohoto sestavení je předáván do jiného sestavení, Visual Basic aplikace může použít předaný typ.  
  
## <a name="forward-types"></a>Předávané typy  
 Existují čtyři kroky pro předání typu:  
  
1. Přesune zdrojový kód pro typ z původního sestavení do cílového sestavení.  
   
2. V sestavení, kde se používá typ, přidejte <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> pro typ, který byl přesunut. Následující kód ukazuje atribut pro typ s názvem `Example` , který byl přesunut.  
   
   ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
   ```
   
   ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
   ```  
   
3. Zkompilujte sestavení, které nyní obsahuje typ.  
   
4. Znovu zkompilujte sestavení, kde se nachází typ, s odkazem na sestavení, které nyní obsahuje typ. Například pokud kompilujete C# soubor z příkazového řádku, použijte možnost [/Reference (C# možnosti kompilátoru)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) a určete sestavení, které obsahuje daný typ. V C++Použijte direktivu [#using](/cpp/preprocessor/hash-using-directive-cpp) ve zdrojovém souboru k určení sestavení, které obsahuje daný typ.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [Předávání typů (C++/CLI)](/cpp/windows/type-forwarding-cpp-cli)
- [#using direktiva](/cpp/preprocessor/hash-using-directive-cpp)
