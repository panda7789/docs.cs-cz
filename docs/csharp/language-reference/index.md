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
ms.openlocfilehash: fd5c39bfcb05296a36d94ea64946f8c29ed7e4d6
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70925343"
---
# <a name="c-reference"></a>Referenční dokumentace jazyka C#
Tato část poskytuje referenční materiál o C# klíčových slovech, operátorech, speciálních znacích, direktivách preprocesoru, možnostech kompilátoru a chybách a upozorněních kompilátoru.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Klíčová slova jazyka C#](./keywords/index.md)  
 Obsahuje odkazy na informace o C# klíčových slovech a syntaxi.  
  
 [Operátory jazyka C#](./operators/index.md)  
 Obsahuje odkazy na informace o C# operátorech a syntaxi.  

 [Speciální znaky v jazyce C#](./tokens/index.md)  
 Obsahuje odkazy na informace o speciálních kontextových znacích C# v a jejich využití.  

 [C# Direktivy preprocesoru](./preprocessor-directives/index.md)  
 Obsahuje odkazy na informace o příkazech kompilátoru pro vložení ve C# zdrojovém kódu.  
  
 [Možnosti kompilátoru jazyka C#](./compiler-options/index.md)  
 Obsahuje informace o možnostech kompilátoru a o jejich použití.  
  
 [Chyby kompilátoru jazyka C#](./compiler-messages/index.md)  
 Obsahuje fragmenty kódu, které ukazují příčinu a opravu C# chyb a upozornění kompilátoru.  
  
 [C#Specifikace jazyka](../../../_csharplang/spec/introduction.md)  
 Specifikace C# jazyka 6,0. Toto je návrh konceptu pro jazyk C# 6,0. Tento dokument bude revidován prostřednictvím práce s výborem Standards C# ECMA. Verze 5,0 byla vydána v prosinci 2017 jako standardní dokument [ECMA-334 5 Edition](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf) .

Funkce, které byly implementovány ve C# verzích po 6,0, jsou reprezentovány v návrzích specifikace jazyka. Tyto dokumenty popisují rozdíly ve specifikaci jazyka, aby bylo možné tyto nové funkce Přidat. Tyto jsou ve formuláři návrhu konceptu. Tyto specifikace budou upřesněny a odeslány do výboru standardů ECMA pro formální kontrolu a začlenění do budoucí verze C# Standard.

 [C#Návrhy specifikace 7,0](../../../_csharplang/proposals/csharp-7.0/pattern-matching.md)  
 V C# 7,0 je implementováno několik nových funkcí. Patří mezi ně porovnávání vzorů, místní funkce, deklarace proměnných out, výrazy throw, binární literály a oddělovače číslic. Tato složka obsahuje specifikace pro každou z těchto funkcí.
  
 [C#Návrhy specifikace 7,1](../../../_csharplang/proposals/csharp-7.1/async-main.md)  
 V C# 7,1 jsou přidané nové funkce. Nejprve můžete napsat `Main` metodu, která vrátí `Task` nebo `Task<int>`. To umožňuje přidat `async` modifikátor do `Main`. `default` Výraz lze použít bez typu v umístění, kde lze typ odvodit. Také je možné odvodit názvy členů řazené kolekce členů. A nakonec lze použít porovnávání vzorů s obecnými typy.

 [C#Návrhy specifikace 7,2](../../../_csharplang/proposals/csharp-7.2/readonly-ref.md)  
 C#7,2 Přidání řady malých funkcí. Pomocí `in` klíčového slova můžete předat argumenty s odkazem jen pro čtení. K dispozici je množství změn nízké úrovně, které podporují bezpečnost v době kompilace pro `Span` a související typy. V některých situacích můžete použít pojmenované argumenty, kde jsou později argumenty pozice. Modifikátor `private protected` přístupu umožňuje určit, že volající jsou omezeny na odvozené typy implementované ve stejném sestavení. `?:` Operátor lze přeložit na odkaz na proměnnou. Můžete také formátovat hexadecimální a binární čísla pomocí počátečního oddělovače číslic.

 [C#Návrhy specifikace 7,3](../../../_csharplang/proposals/csharp-7.3/blittable.md)  
 C#7,3 je další verze bodu, která zahrnuje několik malých aktualizací. V parametrech obecného typu můžete použít nová omezení. Další změny usnadňují práci s `fixed` poli, včetně použití [`stackalloc`](./operators/stackalloc.md) přidělení. Místní proměnné deklarované s `ref` klíčovým slovem mohou být reasssigned, aby odkazovaly na nové úložiště. Atributy lze umístit do automaticky implementovaných vlastností, které cílí na pole zálohování generované kompilátorem. Proměnné výrazu lze použít v inicializátorech. Řazené kolekce členů lze porovnat s rovností (nebo nerovností). Existuje také vylepšení řešení přetížení.
  
 [C#Návrhy specifikace 8,0](../../../_csharplang/proposals/csharp-8.0/nullable-reference-types.md)  
 C#8,0 je k dispozici v rozhraní .NET Core 3,0. Mezi tyto funkce patří typy odkazů s možnou hodnotou null, rekurzivní porovnávání vzorů, výchozí členy rozhraní, asynchronní datové proudy, rozsahy a indexy, vzory založené na vzorcích a používání deklarací, přiřazení slučování null a členy instance ReadOnly.
  
## <a name="related-sections"></a>Související oddíly  

 [Průvodce jazykem C#](../index.md)  
 Poskytuje portál pro vizuální C# dokumentaci.  
  
 [Použití vývojového prostředí sady Visual Studio pro jazyk C#](/visualstudio/get-started/csharp)  
 Obsahuje odkazy na koncepční témata a témata související s úlohami, které popisují rozhraní IDE a editor.  
  
 [Průvodce programováním v jazyce C#](../programming-guide/index.md)  
 Obsahuje informace o používání C# programovacího jazyka.
