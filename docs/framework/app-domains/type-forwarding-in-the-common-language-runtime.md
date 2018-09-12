---
title: Předávání typů v modulu Common Language Runtime
ms.date: 03/30/2017
dev_langs:
- csharp
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d25bac953ff68422a1dddc54bdb01b4b4f241cbb
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44509574"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a>Předávání typů v modulu Common Language Runtime
Předávání typů vám umožní přesunout typu na jiné sestavení bez nutnosti znovu kompilovat aplikace, které používají původní sestavení.  
  
 Předpokládejme například, že aplikace používá `Example` třídy v sestavení s názvem `Utility.dll`. Vývojáři `Utility.dll` rozhodnout Refaktorovat sestavení a v procesu může být přesunout `Example` třídy na jiné sestavení. Pokud je starší verze této `Utility.dll` je nahrazena novou verzi `Utility.dll` a jeho sestavení doprovodné aplikace, která používá `Example` třídy se nezdaří, protože nelze nalézt `Example` třídy v nové verzi sady `Utility.dll`.  
  
 Vývojáři `Utility.dll` lze zabránit předá požadavky `Example` třídy pomocí <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> atribut. Pokud byl použit atribut na novou verzi `Utility.dll`, žádosti o `Example` třídy jsou předaný do sestavení, která nyní obsahuje třídu. Existující aplikaci i nadále fungovat normálně, bez opětovnou kompilaci.  
  
> [!NOTE]
>  V rozhraní .NET Framework verze 2.0 nemohou předat dál typy ze sestavení, které jsou napsané v jazyce Visual Basic. Aplikace napsané v jazyce Visual Basic však může spotřebovat předané typy. To znamená pokud aplikace používá sestavení nakódovat v jazyce C# nebo C++ a typ v tomto sestavení je přemístěn na jiné sestavení, můžete použít aplikaci Visual Basic předaný typ.  
  
## <a name="forwarding-types"></a>Předávání typů  
 Předávání typu čtyři kroky:  
  
1.  Zdrojový kód pro typ přesuňte z původní sestavení do cílového sestavení.  
  
2.  V sestavení, kde lze najít typ, přidejte <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> pro typ, který byl přesunut. Následující kód ukazuje atributu pro typ s názvem `Example` , který byl přesunut.  
  
    ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
    ```  
  
    ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
    ```  
  
3.  Kompilace, která nyní obsahuje typ sestavení.  
  
4.  Znovu zkompilujte použití typu budou umístěné, s odkazem na sestavení, která nyní obsahuje typ sestavení. Například pokud kompilujete soubor jazyka C# z příkazového řádku, použijte [/Reference (možnosti kompilátoru C#)](~/docs/csharp/language-reference/compiler-options/reference-compiler-option.md) možnost určit, který obsahuje typ sestavení. V jazyce C++, použijte [#using](https://msdn.microsoft.com/library/870b15e5-f361-40a8-ba1c-c57d75c8809a) směrnice ve zdrojovém souboru k určení, která obsahuje typ sestavení.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>  
 [Předávání typů (C++/CLI)](/cpp/windows/type-forwarding-cpp-cli)  
 [#using – direktiva](https://msdn.microsoft.com/library/870b15e5-f361-40a8-ba1c-c57d75c8809a)
