---
title: Předávání typů v modulu CLR (Common Language Runtime)
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
dev_langs:
- csharp
- cpp
ms.openlocfilehash: 215636a9617a2723d8ab69640c1d3e69491a7d87
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160362"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a>Předávání typů v modulu CLR (Common Language Runtime)
Předávání typů umožňuje přesunout typ do jiného sestavení bez nutnosti překompilovat aplikace, které používají původní sestavení.  
  
 Předpokládejme například, že `Example` aplikace používá třídu v sestavení s názvem *Utility.dll*. Vývojáři *utility.dll* může rozhodnout o refaktorování sestavení a `Example` v procesu mohou přesunout třídu do jiného sestavení. Pokud je stará verze služby *Utility.dll* nahrazena novou verzí souboru *Utility.dll* `Example` a jejím doprovodným `Example` sestavením, aplikace, která používá třídu, se nezdaří, protože nemůže najít třídu v nové verzi *souboru Utility.dll*.  
  
 Vývojáři *Utility.dll* můžete vyhnout tím, že `Example` předávání požadavků <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> pro třídu pomocí atributu. Pokud byl atribut použit pro novou verzi *služby Utility.dll*, požadavky na třídu `Example` jsou předány sestavení, které nyní obsahuje třídu. Existující aplikace nadále fungovat normálně, bez rekompilace.  
  
> [!NOTE]
> V rozhraní .NET Framework verze 2.0 nelze předávat typy ze sestavení napsaných v jazyce Visual Basic. Aplikace napsaná v jazyce Visual Basic však může využívat předané typy. To znamená, že pokud aplikace používá sestavení kódované v jazyce C# nebo C++ a typ z tohoto sestavení je předán do jiného sestavení, aplikace jazyka visual basic můžete použít předaný typ.  
  
## <a name="forward-types"></a>Dopředné typy  
 Existují čtyři kroky k předávání typu:  
  
1. Přesuňte zdrojový kód pro typ z původního sestavení do cílového sestavení.  

2. V sestavě, kde byl typ umístěn, přidejte a <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> pro typ, který byl přesunut. Následující kód zobrazuje atribut pro `Example` typ s názvem, který byl přesunut.  

   ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
   ```

   ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
   ```  

3. Zkompilujte sestavení, které nyní obsahuje typ.  

4. Překompilujte sestavení, kde typ slouží k umístění, s odkazem na sestavení, které nyní obsahuje typ. Například pokud sestavujete soubor Jazyka C# z příkazového řádku, použijte možnost [-reference (C# kompilátor)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) k určení sestavení, které obsahuje typ. V jazyce C++ použijte direktivu [#using](/cpp/preprocessor/hash-using-directive-cpp) ve zdrojovém souboru k určení sestavení, které obsahuje typ.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [Předávání typů (C++/CLI)](/cpp/windows/type-forwarding-cpp-cli)
- [směrnice o #using](/cpp/preprocessor/hash-using-directive-cpp)
