---
title: Struktura programu jazyka Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], Visual Basic
- program structure [Visual Basic], Visual Basic
- procedures [Visual Basic], structure
- Visual Basic code, program structure
ms.assetid: ad0c6531-d762-4c77-a700-de16b07b6119
ms.openlocfilehash: dc6b38d78f02a42c8e7cc2aa964e9f3f74996f44
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408761"
---
# <a name="structure-of-a-visual-basic-program"></a>Struktura programu jazyka Visual Basic
Visual Basic program je sestaven ze standardních stavebních bloků. *Řešení* se skládá z jednoho nebo více projektů. *Projekt* zase může obsahovat jedno nebo více sestavení. Každé *sestavení* je kompilováno z jednoho nebo více zdrojových souborů. *Zdrojový soubor* poskytuje definici a implementaci tříd, struktur, modulů a rozhraní, které nakonec obsahují veškerý kód.  
  
 Další informace o těchto stavebních blocích Visual Basic programu naleznete v tématu [řešení a projekty](/visualstudio/ide/solutions-and-projects-in-visual-studio) a [sestavení v rozhraní .NET](../../../standard/assembly/index.md).  
  
## <a name="file-level-programming-elements"></a>Programovací prvky na úrovni souborů  
 Když spustíte projekt nebo soubor a otevřete Editor kódu, vidíte nějaký kód, který je již na místě a ve správném pořadí. Jakýkoli kód, který napíšete, by měl splňovat následující pořadí:  
  
1. `Option`učiněn  
  
2. `Imports`učiněn  
  
3. `Namespace`příkazy a elementy na úrovni oboru názvů  
  
 Pokud zadáte příkazy v jiném pořadí, může dojít k chybám kompilace.  
  
 Program může také obsahovat příkazy podmíněné kompilace. Můžete je proložit ve zdrojovém souboru mezi příkazy předchozí sekvence.  
  
### <a name="option-statements"></a>Příkazy možností  
 `Option`příkazy zřídí základní pravidla pro následný kód, což pomáhá zabránit chybám syntaxe a logiky. [Příkaz Option Explicit](../../language-reference/statements/option-explicit-statement.md) zajišťuje, aby všechny proměnné byly deklarované a napsané správně, což zkracuje dobu ladění. [Příkaz Option Strict](../../language-reference/statements/option-strict-statement.md) pomáhá minimalizovat logické chyby a ztrátu dat, ke kterým může dojít při práci mezi proměnnými různých datových typů. [Příkaz Option Compare](../../language-reference/statements/option-compare-statement.md) určuje způsob vzájemného porovnání řetězců na základě jejich `Binary` `Text` hodnot nebo.  
  
### <a name="imports-statements"></a>Příkazy Imports  
 Můžete zahrnout [příkaz Imports (obor názvů a typ .NET)](../../language-reference/statements/imports-statement-net-namespace-and-type.md) pro import názvů definovaných mimo váš projekt. `Imports`Příkaz umožňuje kódu odkazovat na třídy a jiné typy definované v importovaném oboru názvů, aniž by bylo nutné je kvalifikovat. V případě potřeby můžete použít tolik `Imports` příkazů. Další informace naleznete v tématu [odkazy a příkaz Imports](references-and-the-imports-statement.md).  
  
### <a name="namespace-statements"></a>Příkazy oboru názvů  
 Obory názvů pomáhají organizovat a klasifikovat své programovací prvky pro snadné seskupování a přístup. Použijete [příkaz Namespace](../../language-reference/statements/namespace-statement.md) k klasifikaci následujících příkazů v rámci konkrétního oboru názvů. Další informace najdete v tématu [obory názvů v Visual Basic](namespaces.md).  
  
### <a name="conditional-compilation-statements"></a>Příkazy podmíněné kompilace  
 Příkazy podmíněné kompilace se můžou vyskytovat skoro kdekoli ve zdrojovém souboru. Způsobují, že části kódu budou zahrnuty nebo vyloučeny v době kompilace v závislosti na určitých podmínkách. Můžete je také použít pro ladění aplikace, protože podmíněný kód je spouštěn pouze v režimu ladění. Další informace naleznete v tématu [Podmíněná kompilace](conditional-compilation.md).  
  
## <a name="namespace-level-programming-elements"></a>Programovací prvky na úrovni oboru názvů  
 Třídy, struktury a moduly obsahují veškerý kód ve zdrojovém souboru. Jsou to prvky na *úrovni oboru názvů* , které se mohou objevit v rámci oboru názvů nebo na úrovni zdrojového souboru. Obsahují deklarace všech ostatních programovacích prvků. Rozhraní, která definují signatury elementů, ale neposkytují žádnou implementaci, se také zobrazí na úrovni modulu. Další informace o prvcích na úrovni modulu najdete v následujících tématech:  
  
- [Class – příkaz](../../language-reference/statements/class-statement.md)  
  
- [Structure – příkaz](../../language-reference/statements/structure-statement.md)  
  
- [Module – příkaz](../../language-reference/statements/module-statement.md)  
  
- [Interface – příkaz](../../language-reference/statements/interface-statement.md)  
  
 Datové prvky na úrovni oboru názvů jsou výčty a Delegáti.  
  
## <a name="module-level-programming-elements"></a>Programovací prvky na úrovni modulu  
 Procedury, operátory, vlastnosti a události jsou jediné programovací prvky, které mohou uchovávat spustitelný kód (příkazy, které provádějí akce za běhu). Jsou to prvky na *úrovni modulu* v programu. Další informace o prvcích na úrovni procedury najdete v následujících tématech:  
  
- [Function – příkaz](../../language-reference/statements/function-statement.md)  
  
- [Sub – příkaz](../../language-reference/statements/sub-statement.md)  
  
- [Declare – příkaz](../../language-reference/statements/declare-statement.md)  
  
- [Operator – příkaz](../../language-reference/statements/operator-statement.md)  
  
- [Property – příkaz](../../language-reference/statements/property-statement.md)  
  
- [Event – příkaz](../../language-reference/statements/event-statement.md)  
  
 Prvky dat na úrovni modulu jsou proměnné, konstanty, výčty a Delegáti.  
  
## <a name="procedure-level-programming-elements"></a>Programovací prvky na úrovni procedury  
 Většina obsahu prvků na *úrovni procedury* je spustitelnými příkazy, které tvoří běhový kód programu. Veškerý spustitelný kód musí být v nějaké proceduře ( `Function` , `Sub` , `Operator` , `Get` , `Set` , `AddHandler` , `RemoveHandler` , `RaiseEvent` ). Další informace najdete v tématu [příkazy](../language-features/statements.md).  
  
 Datové prvky na úrovni procedury jsou omezeny na lokální proměnné a konstanty.  
  
## <a name="the-main-procedure"></a>Hlavní postup  
 `Main`Procedura je první kód, který se spustí při načtení vaší aplikace. `Main`slouží jako výchozí bod a celkový ovládací prvek pro vaši aplikaci. Existují čtyři varianty `Main` :  
  
- `Sub Main()`  
  
- `Sub Main(ByVal cmdArgs() As String)`  
  
- `Function Main() As Integer`  
  
- `Function Main(ByVal cmdArgs() As String) As Integer`  
  
 Nejběžnějším spektrem tohoto postupu je `Sub Main()` . Další informace najdete v tématu [hlavní postup v Visual Basic](main-procedure.md).  
  
## <a name="see-also"></a>Viz také

- [Hlavní procedura v jazyce Visual Basic](main-procedure.md)
- [Zásady vytváření názvů jazyka Visual Basic](naming-conventions.md)
- [Omezení jazyka Visual Basic](limitations.md)
