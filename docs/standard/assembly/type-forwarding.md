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
ms.openlocfilehash: 1b00eea3c28a160a5afc41d910144033d2339070
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524460"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a>Předávání typů v modulu CLR (Common Language Runtime)
Přesměrování typu umožňuje přesunout typ do jiného sestavení bez nutnosti opětovné kompilace aplikací, které používají původní sestavení.  
  
 Předpokládejme například, že aplikace používá třídu `Example` v sestavení s názvem *Utility. dll*. Vývojáři *nástroje Utility. dll* se mohou rozhodnout Refaktorovat sestavení a v procesu, který by mohl přesunout třídu `Example` do jiného sestavení. Pokud je stará verze souboru *Utility. dll* nahrazena novou verzí *nástroje Utility. dll* a jeho doprovodné sestavení, aplikace, která používá `Example` třídy, se nezdařila, protože nemůže najít třídu `Example` v nové verzi *nástroje. dll.* .  
  
 Vývojáři *nástroje Utility. dll* se k tomu mohou vyhnout přesměrováním požadavků pro třídu `Example` pomocí atributu <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>. Pokud byl atribut použit pro novou verzi *nástroje Utility. dll*, požadavky na třídu `Example` jsou předávány sestavení, které nyní obsahuje třídu. Stávající aplikace bude nadále fungovat normálně bez nutnosti rekompilace.  
  
> [!NOTE]
> V .NET Framework verze 2,0 nemůžete předávané typy ze sestavení napsaných v Visual Basic. Aplikace napsaná v Visual Basic však může využívat předané typy. To znamená, že pokud aplikace používá sestavení kódované v C# nebo C++a typ z tohoto sestavení je předáván do jiného sestavení, Visual Basic aplikace může použít předaný typ.  
  
## <a name="forward-types"></a>Předávané typy  
 Existují čtyři kroky pro předání typu:  
  
1. Přesune zdrojový kód pro typ z původního sestavení do cílového sestavení.  
   
2. Do sestavení, kde se používá typ, přidejte <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> pro typ, který byl přesunut. Následující kód ukazuje atribut pro typ s názvem `Example`, který byl přesunut.  
   
   ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
   ```
   
   ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
   ```  
   
3. Zkompilujte sestavení, které nyní obsahuje typ.  
   
4. Znovu zkompilujte sestavení, kde se nachází typ, s odkazem na sestavení, které nyní obsahuje typ. Například pokud kompilujete C# soubor z příkazového řádku, použijte možnost [-Reference (C# možnosti kompilátoru)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) k určení sestavení, které obsahuje typ. V C++Použijte direktivu [#using](/cpp/preprocessor/hash-using-directive-cpp) ve zdrojovém souboru k určení sestavení, které obsahuje daný typ.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [Předávání typů (C++/CLI)](/cpp/windows/type-forwarding-cpp-cli)
- [#using direktiva](/cpp/preprocessor/hash-using-directive-cpp)
