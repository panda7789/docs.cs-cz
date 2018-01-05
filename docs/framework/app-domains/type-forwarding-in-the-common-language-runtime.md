---
title: "Předávání typů v modulu Common Language Runtime"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 32dad99e8d5caa7d88fa302a1bea8b83847bfde3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
