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
ms.openlocfilehash: 9945b66f9d9fcdfb075bd48f5f56f30f2fdf7712
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="type-forwarding-in-the-common-language-runtime"></a>Předávání typů v modulu Common Language Runtime
Předávání typů umožňuje přesunout typu do jiného sestavení bez nutnosti její kompilace aplikace, které používají původní sestavení.  
  
 Předpokládejme například, že aplikace používá `Example` třídy v sestavení s názvem `Utility.dll`. Vývojáři `Utility.dll` rozhodnout Refaktorovat sestavení a v procesu může přesunout `Example` třída pro jiné sestavení. Pokud stará verze `Utility.dll` je nahrazena novou verzi `Utility.dll` a jeho doprovodné sestavení, aplikace, která používá `Example` třída nezdaří, protože nebyl nalezen `Example` třídy v nové verzi `Utility.dll`.  
  
 Vývojáři `Utility.dll` můžete předejít předá požadavky `Example` pomocí <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> atribut. Pokud atribut použilo na novou verzi `Utility.dll`, požadavky `Example` třídy se předávají do sestavení, které teď obsahuje třídu. Existující aplikace i nadále fungovat normálně, bez opětovnou kompilaci.  
  
> [!NOTE]
>  V rozhraní .NET Framework verze 2.0 nemohou předat dál typy ze sestavení, které jsou napsané v jazyce Visual Basic. Aplikace napsané v jazyce Visual Basic však může spotřebovat přesměrovaná typy. To znamená pokud aplikace používá sestavení programového v C# nebo C++ a typu z tohoto sestavení se předají do jiné sestavení, můžete použít aplikace Visual Basic přesměrovaná typu.  
  
## <a name="forwarding-types"></a>Předávání typů  
 Existují čtyři kroky předávání typu:  
  
1.  Zdrojový kód pro typ přesunete z původní sestavení do sestavení cílový.  
  
2.  V sestavení, kde lze najít typ, přidejte <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> pro typ, který byl přesunut. Následující kód ukazuje atribut pro typ s názvem `Example` , byl přesunut.  
  
    ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
    ```  
  
    ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
    ```  
  
3.  Kompilace sestavení, které teď obsahuje typu.  
  
4.  Znovu zkompiluje sestavení, kde lze najít s odkazem na sestavení, které teď obsahuje typ typu. Například, pokud jsou kompilace souboru C# z příkazového řádku, použijte [/Reference (možnosti kompilátoru C#)](~/docs/csharp/language-reference/compiler-options/reference-compiler-option.md) možnost zadat sestavení, které obsahuje typ. V jazyce C++ pomocí [#using](http://msdn.microsoft.com/library/870b15e5-f361-40a8-ba1c-c57d75c8809a) ve zdrojovém souboru k zadání sestavení, které obsahuje typ direktivy.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>  
 [Předávání typů (C++/CLI)](/cpp/windows/type-forwarding-cpp-cli)  
 [#using – direktiva](http://msdn.microsoft.com/library/870b15e5-f361-40a8-ba1c-c57d75c8809a)
