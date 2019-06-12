---
title: Referenční dokumentace jazyka C#
ms.date: 02/14/2017
helpviewer_keywords:
- Visual C#, language reference
- language reference [C#]
- Programmer's Reference for C#
- C# language, reference
- reference, C# language
ms.assetid: 06de3167-c16c-4e1a-b3c5-c27841d4569a
ms.openlocfilehash: 45352d97372e556627ead75d969f088de9c85bd0
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833236"
---
# <a name="c-reference"></a>Referenční dokumentace jazyka C#
Tato část poskytuje referenční materiál o C# klíčová slova, operátory, speciální znaky, direktivy preprocesoru, možnostech kompilátoru a kompilátoru chyby a upozornění.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Klíčová slova jazyka C#](../../csharp/language-reference/keywords/index.md)  
 Obsahuje odkazy na informace o C# syntaxi a klíčových slov.  
  
 [Operátory jazyka C#](../../csharp/language-reference/operators/index.md)  
 Obsahuje odkazy na informace o C# operátorů a syntaxe.  

 [Speciální znaky v jazyce C#](../../csharp/language-reference/tokens/index.md)  
 Obsahuje odkazy na informace o kontextových znaky v C# a jejich použití.  

 [C# Direktivy preprocesoru](../../csharp/language-reference/preprocessor-directives/index.md)  
 Obsahuje odkazy na informace o příkazech kompilátoru pro vkládání do C# zdrojový kód.  
  
 [Možnosti kompilátoru jazyka C#](../../csharp/language-reference/compiler-options/index.md)  
 Obsahuje informace o možnostech kompilátoru a jejich použití.  
  
 [Chyby kompilátoru jazyka C#](../../csharp/language-reference/compiler-messages/index.md)  
 Zahrnuje fragmenty kódu, které ukazují příčina a oprava C# kompilátoru chyby a upozornění.  
  
 [Specifikace jazyka C#](../../../_csharplang/spec/introduction.md)  
 C# Specifikace jazyka 6.0. Toto je koncepty C# 6.0 jazyka. V prosinci 2017 jako byla vydána verze 5.0 [Standard ECMA-334 5th Edition](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf) dokumentu.

Funkce, které byly implementovány v C# verze po 6.0 jsou reprezentovány v návrzích specifikace jazyka. Tyto dokumenty popisují rozdíly pro specifikace jazyka, aby bylo možné přidat tyto nové funkce.

 [C#7.0 návrhy jazyka](../../../_csharplang/proposals/csharp-7.0/pattern-matching.md)  
 Existuje několik nových funkcí, které jsou implementované v C# 7.0. Jejich zahrnují vzor odpovídající, místní funkce si deklarace proměnných, throw výrazy, binární literály a oddělovače číslic. Tato složka obsahuje specifikace pro každou z těchto funkcí.
  
 [C#7.1 návrhy jazyka](../../../_csharplang/proposals/csharp-7.1/async-main.md)  
 Existují nové funkce přidané do C# 7.1. Nejprve můžete napsat `Main` metodu, která vrací `Task` nebo `Task<int>`. To vám umožňuje přidat `async` modifikátor `Main`. `default` Výraz lze použít bez typu v umístění, kde jde odvodit typ. Kromě toho jde odvodit názvy členů řazené kolekce členů. Nakonec porovnávání vzorů je možné pomocí obecných typů.

 [C#7.2 návrhy jazyka](../../../_csharplang/proposals/csharp-7.2/readonly-ref.md)  
 C#7.2 přidali počet malé funkce. Pomocí odkazu jen pro čtení, můžete předat argumenty `in` – klíčové slovo. Existuje mnoho nízké úrovně změny pro podporu bezpečnosti kompilace pro `Span` a souvisejících typů. Můžete použít pojmenované argumenty, kde jsou novější argumenty poziční, v některých situacích. `private protected` Modifikátor přístupu umožňuje určit, že volající jsou omezeny na odvozené typy, které jsou implementované ve stejném sestavení. `?:` Operátor umí přeložit na odkaz na proměnnou. Můžete také formátovat čísla šestnáctkové a binární pomocí oddělovač úvodní číslice.

 [C#7.3 návrhy jazyka](../../../_csharplang/proposals/csharp-7.3/blittable.md)  
 C#7.3 je další vydání bodu, který zahrnuje několik malých aktualizací. Můžete použít nová omezení parametrů obecných typů. Další změny usnadňují práci s `fixed` pole, včetně použití [ `stackalloc` ](./operators/stackalloc.md) přidělení. Lokální proměnné deklarované pomocí `ref` – klíčové slovo může být reasssigned odkazovat na nové úložiště. Atributy lze umístit na automaticky implementované vlastnosti, které se zaměřují vygenerovaný kompilátorem pomocným polem. Výraz proměnné lze použít v inicializátorech. Zjištění rovnosti (či nerovnosti) lze porovnávat řazené kolekce členů. Také došlo některá vylepšení řešení přetížení.
  
 [C#8.0 návrhy jazyka](../../../_csharplang/proposals/csharp-8.0/nullable-reference-types.md) C# 8.0 je dostupná ve verzi preview. Následující návrhy jsou aktuální verze specifikace pro tyto funkce. Některé jsou více úplné. Některé jsou stále ve vývoji. Funkce, které byly dodány ve verzích Preview zahrnují typy s možnou hodnotou Null odkazů, rekurzivní porovnávání vzorů, asynchronní datové proudy, rozsahy a indexy, na základě pomocí vzoru a pomocí deklarací a null slučovací přiřazení.
  
## <a name="related-sections"></a>Související oddíly  

 [Průvodce jazykem C#](../../csharp/index.md)  
 Poskytuje portál vizuálu C# dokumentaci.  
  
 [Použití vývojového prostředí sady Visual Studio pro jazyk C#](/visualstudio/csharp-ide/using-the-visual-studio-development-environment-for-csharp)  
 Obsahuje odkazy na koncepční a úlohy témata, která popisují Editor a integrované vývojové prostředí.  
  
 [Průvodce programováním v jazyce C#](../../csharp/programming-guide/index.md)  
 Obsahuje informace o tom, jak používat C# programovací jazyk.
