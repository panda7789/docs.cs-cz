---
title: C#odkaz
ms.date: 02/14/2017
helpviewer_keywords:
- Visual C#, language reference
- language reference [C#]
- Programmer's Reference for C#
- C# language, reference
- reference, C# language
ms.assetid: 06de3167-c16c-4e1a-b3c5-c27841d4569a
ms.openlocfilehash: 4875e53327e24c4b5983a4a3b79b5beced368725
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428615"
---
# <a name="c-reference"></a>C#odkaz

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
 V C# 7,1 jsou přidané nové funkce. Nejprve můžete napsat metodu `Main`, která vrací `Task` nebo `Task<int>`. To umožňuje přidat modifikátor `async` do `Main`. Výraz `default` lze použít bez typu v umístění, kde lze typ odvodit. Také je možné odvodit názvy členů řazené kolekce členů. A nakonec lze použít porovnávání vzorů s obecnými typy.

 [C#Návrhy specifikace 7,2](../../../_csharplang/proposals/csharp-7.2/readonly-ref.md)  
 C#7,2 Přidání řady malých funkcí. Argumenty můžete předat odkazem ReadOnly pomocí klíčového slova `in`. K dispozici je množství změn nízké úrovně, které podporují bezpečnost v době kompilace pro `Span` a související typy. V některých situacích můžete použít pojmenované argumenty, kde jsou později argumenty pozice. Modifikátor přístupu `private protected` umožňuje určit, že volající jsou omezeny na odvozené typy implementované ve stejném sestavení. Operátor `?:` lze přeložit na odkaz na proměnnou. Můžete také formátovat hexadecimální a binární čísla pomocí počátečního oddělovače číslic.

 [C#Návrhy specifikace 7,3](../../../_csharplang/proposals/csharp-7.3/blittable.md)  
 C#7,3 je další verze bodu, která zahrnuje několik malých aktualizací. V parametrech obecného typu můžete použít nová omezení. Další změny usnadňují práci s `fixed` poli, včetně použití přidělení [`stackalloc`](./operators/stackalloc.md) . Místní proměnné deklarované s klíčovým slovem `ref` mohou být přiřazeny k odkazování na nové úložiště. Atributy lze umístit do automaticky implementovaných vlastností, které cílí na pole zálohování generované kompilátorem. Proměnné výrazu lze použít v inicializátorech. Řazené kolekce členů lze porovnat s rovností (nebo nerovností). Existuje také vylepšení řešení přetížení.
  
 [C#Návrhy specifikace 8,0](../../../_csharplang/proposals/csharp-8.0/nullable-reference-types.md)  
 C#8,0 je k dispozici v rozhraní .NET Core 3,0. Mezi tyto funkce patří typy odkazů s možnou hodnotou null, rekurzivní porovnávání vzorů, metody rozhraní Standard, asynchronní streamy, rozsahy a indexy, založené na vzorcích a používání deklarací, přiřazení sloučení s hodnotou null a členy instance s vlastností ReadOnly.
  
## <a name="related-sections"></a>Související oddíly  

 [Použití vývojového prostředí sady Visual Studio pro jazyk C#](/visualstudio/get-started/csharp)  
 Obsahuje odkazy na koncepční témata a témata související s úlohami, které popisují rozhraní IDE a editor.  
  
 [Průvodce programováním v C#](../programming-guide/index.md)  
 Obsahuje informace o používání C# programovacího jazyka.
