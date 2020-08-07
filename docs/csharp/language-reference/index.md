---
title: Referenční dokumentace k jazyku C#
ms.date: 02/14/2017
f1_keywords:
- _CSharpKeyword
helpviewer_keywords:
- Visual C#, language reference
- language reference [C#]
- Programmer's Reference for C#
- C# language, reference
- reference, C# language
ms.assetid: 06de3167-c16c-4e1a-b3c5-c27841d4569a
ms.openlocfilehash: bed8f430793a8d8544cf0bbb5ea765490945bfc0
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855332"
---
# <a name="c-reference"></a>Referenční dokumentace k jazyku C#

Tato část poskytuje referenční materiál o klíčových slovech jazyka C#, operátorech, speciálních znacích, direktivách preprocesoru, možnostech kompilátoru a chybách a upozorněních kompilátoru.  
  
## <a name="in-this-section"></a>V této části

 [Klíčová slova jazyka C#](./keywords/index.md)  
 Obsahuje odkazy na informace o klíčových slovech jazyka C# a syntaxi.  
  
 [Operátory jazyka C#](./operators/index.md)  
 Obsahuje odkazy na informace o operátorech a syntaxi jazyka C#.  

 [Speciální znaky jazyka C#](./tokens/index.md)  
 Obsahuje odkazy na informace o speciálních kontextových znacích v jazyce C# a jejich použití.  

 [C# – direktivy preprocesoru](./preprocessor-directives/index.md)  
 Obsahuje odkazy na informace o příkazech kompilátoru pro vkládání ve zdrojovém kódu jazyka C#.  
  
 [Možnosti kompilátoru C#](./compiler-options/index.md)  
 Obsahuje informace o možnostech kompilátoru a o jejich použití.  
  
 [Chyby kompilátoru C#](./compiler-messages/index.md)  
 Obsahuje fragmenty kódu, které ukazují příčinu a opravu chyb a upozornění kompilátoru jazyka C#.  
  
 [Specifikace jazyka C#](../../../_csharplang/spec/introduction.md)  
 Specifikace jazyka C# 6,0. Toto je návrh konceptu pro jazyk C# 6,0. Tento dokument bude provedený ve spolupráci s výborem standardu ECMA C#. Verze 5,0 byla vydána v prosinci 2017 jako standardní dokument [ECMA-334 5 Edition](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf) .

Funkce, které byly implementovány ve verzích jazyka C# po 6,0, jsou reprezentovány v návrzích specifikace jazyka. Tyto dokumenty popisují rozdíly ve specifikaci jazyka, aby bylo možné tyto nové funkce Přidat. Tyto jsou ve formuláři návrhu konceptu. Tyto specifikace budou upřesněny a odeslány do výboru standardů ECMA pro účely formálního přezkoumání a začlenění do budoucí verze standardu C#.

 [Návrhy specifikace C# 7,0](../../../_csharplang/proposals/csharp-7.0/pattern-matching.md)  
 V C# 7,0 je implementováno několik nových funkcí. Patří mezi ně porovnávání vzorů, místní funkce, deklarace proměnných out, výrazy throw, binární literály a oddělovače číslic. Tato složka obsahuje specifikace pro každou z těchto funkcí.
  
 [Návrhy specifikace C# 7,1](../../../_csharplang/proposals/csharp-7.1/async-main.md)  
 V C# 7,1 se přidaly nové funkce. Nejprve můžete napsat `Main` metodu, která vrátí `Task` nebo `Task<int>` . To umožňuje přidat `async` modifikátor do `Main` . `default`Výraz lze použít bez typu v umístění, kde lze typ odvodit. Také je možné odvodit názvy členů řazené kolekce členů. A nakonec lze použít porovnávání vzorů s obecnými typy.

 [Návrhy specifikace C# 7,2](../../../_csharplang/proposals/csharp-7.2/readonly-ref.md)  
 C# 7,2 přidalo množství malých funkcí. Pomocí klíčového slova můžete předat argumenty s odkazem jen pro čtení `in` . K dispozici je množství změn nízké úrovně, které podporují bezpečnost v době kompilace pro `Span` a související typy. V některých situacích můžete použít pojmenované argumenty, kde jsou později argumenty pozice. `private protected`Modifikátor přístupu umožňuje určit, že volající jsou omezeny na odvozené typy implementované ve stejném sestavení. `?:`Operátor lze přeložit na odkaz na proměnnou. Můžete také formátovat hexadecimální a binární čísla pomocí počátečního oddělovače číslic.

 [Návrhy specifikace C# 7,3](../../../_csharplang/proposals/csharp-7.3/blittable.md)  
 C# 7,3 je další verze místa, která zahrnuje několik malých aktualizací. V parametrech obecného typu můžete použít nová omezení. Další změny usnadňují práci s `fixed` poli, včetně použití [`stackalloc`](./operators/stackalloc.md) přidělení. Místní proměnné deklarované s `ref` klíčovým slovem mohou být přiřazeny k odkazování na nové úložiště. Atributy lze umístit do automaticky implementovaných vlastností, které cílí na pole zálohování generované kompilátorem. Proměnné výrazu lze použít v inicializátorech. Řazené kolekce členů lze porovnat s rovností (nebo nerovností). Existuje také vylepšení řešení přetížení.
  
 [Návrhy specifikace C# 8,0](../../../_csharplang/proposals/csharp-8.0/nullable-reference-types.md)  
 C# 8,0 je k dispozici v rozhraní .NET Core 3,0. Mezi tyto funkce patří typy odkazů s možnou hodnotou null, rekurzivní porovnávání vzorů, metody rozhraní Standard, asynchronní streamy, rozsahy a indexy, založené na vzorcích a používání deklarací, přiřazení sloučení s hodnotou null a členy instance s vlastností ReadOnly.
  
## <a name="related-sections"></a>Související oddíly  

 [Použití vývojového prostředí sady Visual Studio pro jazyk C#](/visualstudio/get-started/csharp)  
 Obsahuje odkazy na koncepční témata a témata související s úlohami, které popisují rozhraní IDE a editor.  
  
 [Průvodce programováním v C#](../programming-guide/index.md)  
 Obsahuje informace o použití programovacího jazyka C#.
