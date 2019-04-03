---
title: Struktura programu jazyka Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], Visual Basic
- program structure [Visual Basic], Visual Basic
- procedures [Visual Basic], structure
- Visual Basic code, program structure
ms.assetid: ad0c6531-d762-4c77-a700-de16b07b6119
ms.openlocfilehash: 5817d4d37610c87bb7e4ade407421ddce7a3a862
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828118"
---
# <a name="structure-of-a-visual-basic-program"></a>Struktura programu jazyka Visual Basic
V aplikaci Visual Basic je vytvářeny z standardních stavebních bloků. A *řešení* se skládá z jednoho nebo více projektů. A *projektu* zase může obsahovat jedno nebo více sestavení. Každý *sestavení* je zkompilován z jednoho nebo více zdrojových souborů. A *zdrojový soubor* obsahuje definice a implementaci tříd, struktur, moduly a rozhraní, takže v konečném důsledku obsahující váš kód.  
  
 Další informace o těchto stavebních bloků programu v jazyce Visual Basic najdete v tématu [řešení a projekty](/visualstudio/ide/solutions-and-projects-in-visual-studio) a [sestavení v rozhraní .NET](../../../standard/assembly/index.md).  
  
## <a name="file-level-programming-elements"></a>Elementy programování na úrovni souboru  
 Při spuštění projektu nebo souboru a otevřete editor kódu, se zobrazí kód již na místě a ve správném pořadí. Veškerý kód, který napíšete postupujte podle následujících pořadí:  
  
1.  `Option` Příkazy  
  
2.  `Imports` Příkazy  
  
3.  `Namespace` Příkazy a elementů na úrovni oboru názvů  
  
 Pokud zadáte příkazy v jiném pořadí, může dojít k chybám kompilace.  
  
 Program může také obsahovat příkazy podmíněné kompilace. Můžete intersperse tyto ve zdrojovém souboru mezi příkazy předchozí pořadí.  
  
### <a name="option-statements"></a>Možnost příkazy  
 `Option` příkazy stanovit pravidla základu pro následující kód, pomáhá zabránit chyby syntaxe a logiku. [Option Explicit – příkaz](../../../visual-basic/language-reference/statements/option-explicit-statement.md) zajistí, že všechny proměnné jsou deklarovány a neobsahuje překlepy, což zkracuje dobu ladění. [Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md) pomáhá minimalizovat logiky chyby a ztráty dat, ke kterému může dojít při práci mezi proměnné různé datové typy. [Možnost porovnat příkaz](../../../visual-basic/language-reference/statements/option-compare-statement.md) určuje řetězce způsob, jak jsou porovnány k sobě navzájem, na základě jejich `Binary` nebo `Text` hodnoty.  
  
### <a name="imports-statements"></a>Příkazy Imports  
 Můžete zahrnout [příkaz Imports (Namespace .NET a typ)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) k importu názvů definován vně vašeho projektu. `Imports` Příkaz umožňuje kódu odkazovat na třídami a ostatními typy definované v rámci importované oboru názvů, aniž byste museli kvalifikovat je. Můžete použít tolik `Imports` příkazy podle potřeby. Další informace najdete v tématu [odkazy a příkaz Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md).  
  
### <a name="namespace-statements"></a>Příkazy Namespace  
 Obory názvů vám pomohou organizovat a klasifikovat vaše programovací prvky z důvodu snadnějšího seskupování a přístup k. Můžete použít [příkaz Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md) ke klasifikaci následující příkazy v rámci určitého oboru názvů. Další informace najdete v tématu [obory názvů v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
### <a name="conditional-compilation-statements"></a>Příkazy podmíněné kompilace  
 Příkazy podmíněné kompilace může vyskytovat téměř kdekoli ve zdrojovém souboru. Způsobí částí kódu zahrnuty nebo vyloučeny v době kompilace v závislosti na určitých podmínek. Můžete také je pro ladění vaší aplikace, protože podmíněné kód se spustí pouze v režimu ladění. Další informace najdete v tématu [podmíněné kompilace](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md).  
  
## <a name="namespace-level-programming-elements"></a>Namespace – úroveň programovací elementy  
 Třídy, struktury a moduly obsahovat veškerý kód ve zdrojovém souboru. Jsou *úrovni oboru názvů* prvky, které se mohou objevit v oboru názvů nebo na úrovni zdroje souboru. Drží deklarace dalších programovacích prvků. Rozhraní, které definují element podpisy, ale poskytnout implementaci, zobrazit i na úrovni modulu. Další informace na úrovni modulu prvky naleznete v následujících tématech:  
  
-   [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
-   [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
-   [Příkaz Module](../../../visual-basic/language-reference/statements/module-statement.md)  
  
-   [Příkaz Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 Výčty a Delegáti jsou prvky dat na úrovni oboru názvů.  
  
## <a name="module-level-programming-elements"></a>Úroveň modulu programovací elementy  
 Postupy, operátory, vlastnosti a události jsou jediným programovací prvky, které mohou obsahovat spustitelného kódu (příkazy, které provádějí akce za běhu). Jsou *úrovni modulu* prvky programu. Další informace o postupu úrovně prvky naleznete v následujících tématech:  
  
-   [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
-   [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [Příkaz Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
-   [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 Údaje na úrovni modulu jsou proměnné, konstanty, výčty a delegáti.  
  
## <a name="procedure-level-programming-elements"></a>Úroveň procedury programovací elementy  
 Většina obsahu *úroveň procedury* prvky jsou spustitelné příkazy, které tvoří kód za běhu programu. Všechny spustitelný kód musí být v některých postupu (`Function`, `Sub`, `Operator`, `Get`, `Set`, `AddHandler`, `RemoveHandler`, `RaiseEvent`). Další informace najdete v tématu [příkazy](../../../visual-basic/programming-guide/language-features/statements.md).  
  
 Prvky dat na úrovni řízení jsou omezené na místní proměnné a konstanty.  
  
## <a name="the-main-procedure"></a>Hlavní procedura  
 `Main` Postup je první kód spustit, když vaše aplikace se načetl. `Main` slouží jako počáteční bod a celkové ovládání aplikace. Existují čtyři typy prvků `Main`:  
  
-   `Sub Main()`  
  
-   `Sub Main(ByVal cmdArgs() As String)`  
  
-   `Function Main() As Integer`  
  
-   `Function Main(ByVal cmdArgs() As String) As Integer`  
  
 Nejběžnější řadu tento postup je `Sub Main()`. Další informace najdete v tématu [hlavní procedura v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md).  
  
## <a name="see-also"></a>Viz také:

- [Hlavní procedura v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
- [Zásady vytváření názvů jazyka Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [Visual Basic Limitations](../../../visual-basic/programming-guide/program-structure/limitations.md)
