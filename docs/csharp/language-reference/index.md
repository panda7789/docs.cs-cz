---
title: Referenční dokumentace k jazyku C#
ms.date: 02/14/2017
helpviewer_keywords:
- Visual C#, language reference
- language reference [C#]
- Programmer's Reference for C#
- C# language, reference
- reference, C# language
ms.assetid: 06de3167-c16c-4e1a-b3c5-c27841d4569a
ms.openlocfilehash: 4875e53327e24c4b5983a4a3b79b5beced368725
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74428615"
---
# <a name="c-reference"></a>Referenční dokumentace k jazyku C#

Tato část obsahuje referenční materiál o c# klíčová slova, operátory, speciální znaky, direktivy preprocesoru, možnosti kompilátoru a chyby kompilátoru a upozornění.  
  
## <a name="in-this-section"></a>V tomto oddílu

 [C# Klíčová slova](./keywords/index.md)  
 Obsahuje odkazy na informace o klíčových slovech jazyka C# a syntaxi.  
  
 [Operátory jazyka C#](./operators/index.md)  
 Obsahuje odkazy na informace o operátorech jazyka C# a syntaxi.  

 [Speciální znaky v jazyce C#](./tokens/index.md)  
 Obsahuje odkazy na informace o zvláštních kontextových znacích v c# a jejich použití.  

 [Direktivy preprocesoru jazyka C#](./preprocessor-directives/index.md)  
 Obsahuje odkazy na informace o příkazech kompilátoru pro vkládání do zdrojového kódu jazyka C#.  
  
 [Možnosti kompilátoru jazyka C#](./compiler-options/index.md)  
 Obsahuje informace o možnostech kompilátoru a o jejich použití.  
  
 [Chyby kompilátoru jazyka C#](./compiler-messages/index.md)  
 Zahrnuje fragmenty kódu, které demonstrují příčinu a opravu chyb a upozornění kompilátoru jazyka C#.  
  
 [Specifikace jazyka C#](../../../_csharplang/spec/introduction.md)  
 Specifikace jazyka C# 6.0. Toto je návrh návrhu jazyka C# 6.0. Tento dokument bude zpřesněn prostřednictvím práce s výborem pro standardy ECMA C#. Verze 5.0 byla vydána v prosinci 2017 jako standardní dokument [ECMA-334 5th Edition.](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf)

Funkce, které byly implementovány ve verzích jazyka C# po 6.0 jsou zastoupeny v návrzích specifikace jazyka. Tyto dokumenty popisují rozdíly na specifikace jazyka za účelem přidání těchto nových funkcí. Ty jsou v podobě návrhu. Tyto specifikace budou zpřesněny a předloženy výboru pro normy ECMA k formálnímu přezkoumání a začlenění do budoucí verze normy C# .

 [C# 7.0 Specifikace Návrhy](../../../_csharplang/proposals/csharp-7.0/pattern-matching.md)  
 Existuje celá řada nových funkcí implementovaných v C# 7.0. Patří mezi ně porovnávání vzorů, místní funkce, mimo deklarace proměnných, throw výrazy, binární literály a oddělovače číslic. Tato složka obsahuje specifikace pro každou z těchto funkcí.
  
 [C# 7.1 Specifikace Návrhy](../../../_csharplang/proposals/csharp-7.1/async-main.md)  
 V c# 7.1 jsou přidány nové funkce. Nejprve můžete napsat `Main` metodu, která vrátí `Task` nebo `Task<int>`. To umožňuje přidat `async` modifikátor do aplikace `Main`. Výraz `default` lze použít bez typu v umístěních, kde lze odvodit typ. Také řazené kolekce členů názvy lze odvodit. Nakonec porovnávání vzorů lze použít s obecnými typy.

 [C# 7.2 Specifikace Návrhy](../../../_csharplang/proposals/csharp-7.2/readonly-ref.md)  
 C# 7.2 přidal řadu malých funkcí. Argumenty můžete předat pouze pro `in` čtení pomocí klíčového slova. Existuje celá řada změn nižší úrovně pro podporu `Span` bezpečnosti kompilace v době kompilace a související typy. Můžete použít pojmenované argumenty, kde pozdější argumenty jsou poziční, v některých situacích. Modifikátor `private protected` přístupu umožňuje určit, že volající jsou omezeny na odvozené typy implementované ve stejném sestavení. Operátor `?:` může vyřešit odkaz na proměnnou. Můžete také formátovat šestnáctková a binární čísla pomocí oddělovače předních číslic.

 [C# 7.3 Specifikace Návrhy](../../../_csharplang/proposals/csharp-7.3/blittable.md)  
 C# 7.3 je další bod vydání, které obsahuje několik malých aktualizací. Můžete použít nová omezení pro parametry obecného typu. Další změny usnadňují práci `fixed` s poli, [`stackalloc`](./operators/stackalloc.md) včetně použití přidělení. Místní proměnné deklarované pomocí klíčového `ref` slova mohou být znovu přiřazeny k odkazu na nové úložiště. Atributy můžete umístit na automaticky implementované vlastnosti, které cílí na záložní pole generované kompilátorem. Proměnné výrazu lze použít v inicializačních metodách. Řazené kolekce členů mohou být porovnány pro rovnost (nebo nerovnost). Došlo také k určitým vylepšením řešení přetížení.
  
 [C# 8.0 Specifikace Návrhy](../../../_csharplang/proposals/csharp-8.0/nullable-reference-types.md)  
 C# 8.0 je k dispozici s rozhraním .NET Core 3.0. Funkce zahrnují typy odkazů s možnou hodnotou null, porovnávání rekurzivních vzorů, výchozí metody rozhraní, asynchronní datové proudy, rozsahy a indexy, vzor založený na použití a použití deklarací, přiřazení null coalescing a členy instancí pouze pro čtení.
  
## <a name="related-sections"></a>Související oddíly  

 [Použití vývojového prostředí sady Visual Studio pro jazyk C#](/visualstudio/get-started/csharp)  
 Obsahuje odkazy na koncepční a úkolová témata, která popisují rozhraní IDE a editor.  
  
 [Programovací příručka jazyka C#](../programming-guide/index.md)  
 Obsahuje informace o použití programovacího jazyka C#.
