---
title: Předávání typů v modulu CLR (Common Language Runtime)
description: Přesměrování typu umožňuje přesunout typ do jiného sestavení .NET, aniž by bylo nutné znovu kompilovat aplikace, které používají původní sestavení.
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
dev_langs:
- csharp
- cpp
ms.openlocfilehash: f0be61bd4ce88569e22a350a9ea9490d67e74ff3
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378587"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a>Předávání typů v modulu CLR (Common Language Runtime)
Přesměrování typu umožňuje přesunout typ do jiného sestavení bez nutnosti opětovné kompilace aplikací, které používají původní sestavení.  
  
 Předpokládejme například, že aplikace používá `Example` třídu v sestavení s názvem *Utility. dll*. Vývojáři *nástroje Utility. dll* se mohou rozhodnout Refaktorovat sestavení a v procesu, který by mohli `Example` třídu přesunout do jiného sestavení. Pokud je stará verze souboru *Utility. dll* nahrazena novou verzí *nástroje Utility. dll* a jeho doprovodném sestavením, aplikace, která třídu používá, se `Example` nezdařila, protože nemůže najít `Example` třídu v nové verzi *nástroje. dll*.  
  
 Vývojáři *nástroje Utility. dll* se k tomu mohou vyhnout přesměrováním požadavků pro `Example` třídu pomocí <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> atributu. Pokud byl atribut použit pro novou verzi *nástroje Utility. dll*, požadavky na `Example` třídu jsou předány sestavení, které nyní obsahuje třídu. Stávající aplikace bude nadále fungovat normálně bez nutnosti rekompilace.  
  
> [!NOTE]
> V .NET Framework verze 2,0 nemůžete předávané typy ze sestavení napsaných v Visual Basic. Aplikace napsaná v Visual Basic však může využívat předané typy. To znamená, že pokud aplikace používá sestavení kódované v jazyce C# nebo C++ a typ z tohoto sestavení je předáván do jiného sestavení, Visual Basic aplikace může použít předaný typ.  
  
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

4. Znovu zkompilujte sestavení, kde se nachází typ, s odkazem na sestavení, které nyní obsahuje typ. Například pokud kompilujete soubor C# z příkazového řádku, použijte možnost [-Reference (možnosti kompilátoru C#)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) k určení sestavení, které obsahuje daný typ. V jazyce C++ Použijte direktivu [#using](/cpp/preprocessor/hash-using-directive-cpp) ve zdrojovém souboru k určení sestavení, které obsahuje daný typ.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [Předávání typů (C++/CLI)](/cpp/windows/type-forwarding-cpp-cli)
- [#using direktiva](/cpp/preprocessor/hash-using-directive-cpp)
