---
title: Struktura programu jazyka Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], Visual Basic
- program structure [Visual Basic], Visual Basic
- procedures [Visual Basic], structure
- Visual Basic code, program structure
ms.assetid: ad0c6531-d762-4c77-a700-de16b07b6119
ms.openlocfilehash: 5c45cc8982a03d5bdd974434164187b03529ae05
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="structure-of-a-visual-basic-program"></a>Struktura programu jazyka Visual Basic
V aplikaci Visual Basic je vytvářet z standardních stavebních bloků. A *řešení* se skládá z jednoho nebo několika projektů. A *projektu* pak může obsahovat jedno nebo více sestavení. Každý *sestavení* kompiluje z jednoho nebo více zdrojových souborů. A *zdrojový soubor* obsahuje definice a implementaci třídy, struktury, moduly a rozhraní, nakonec obsahujících vašeho kódu.  
  
 Další informace o těchto stavební bloky programu v jazyce Visual Basic najdete v tématu [řešení a projekty](/visualstudio/ide/solutions-and-projects-in-visual-studio) a [sestavení a globální mezipaměť sestavení](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md).  
  
## <a name="file-level-programming-elements"></a>Programovací elementy úrovni souborů  
 Při spuštění projektu nebo souboru a otevření editoru kódu, uvidíte nějaký kód již na místě a ve správném pořadí. Kód, který můžete psát postupujte podle následujících pořadí:  
  
1.  `Option` Příkazy  
  
2.  `Imports` Příkazy  
  
3.  `Namespace` Příkazy a elementů na úrovni oboru názvů  
  
 Pokud zadáte příkazy v jiném pořadí, může způsobit chyby kompilace.  
  
 Program může také obsahovat příkazy Podmíněná kompilace. Můžete intersperse tyto ve zdrojovém souboru mezi příkazy předchozí pořadí.  
  
### <a name="option-statements"></a>Možnost – příkazy  
 `Option` příkazy vytvořit pravidla základů pro následující kód, pomáhá zabránit chyby syntaxe a logiku. [Option Explicit – příkaz](../../../visual-basic/language-reference/statements/option-explicit-statement.md) zajišťuje, že všechny proměnné jsou deklarovaný a napsaný správně, což snižuje čas ladění. [Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md) pomáhá minimalizovat logiku chyby a ztráty dat, ke kterému může dojít při práci mezi proměnné různé datové typy. [Option Compare – příkaz](../../../visual-basic/language-reference/statements/option-compare-statement.md) určuje způsob řetězce jsou porovnávány k sobě navzájem, na základě některé jejich `Binary` nebo `Text` hodnoty.  
  
### <a name="imports-statements"></a>Importy – příkazy  
 Můžete použít [příkaz Imports (Namespace .NET a typ)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) import názvy definované mimo projekt. `Imports` Příkaz umožňuje kódu odkazovat na třídami a ostatními typy definované v rámci oboru názvů importované bez nutnosti jejich kvalifikaci. Můžete použít jako mnoho `Imports` příkazy podle potřeby. Další informace najdete v tématu [odkazy a příkaz Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md).  
  
### <a name="namespace-statements"></a>Namespace – příkazy  
 Obory názvů pomáhají uspořádání a klasifikovat vaše elementům programování pro usnadnění seskupování a přístup. Můžete použít [příkaz Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md) klasifikovat následující příkazy v rámci konkrétní obor názvů. Další informace najdete v tématu [obory názvů v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
### <a name="conditional-compilation-statements"></a>Příkazy Podmíněná kompilace  
 Podmíněná kompilace příkazy může vyskytovat kdekoli téměř v zdrojový soubor. Způsobí částí kódu zahrnout nebo vyloučit v době kompilace v závislosti na určité podmínky. Můžete taky je pro ladění aplikace, protože spuštění podmíněného kódu v jenom na režim ladění. Další informace najdete v tématu [Podmíněná kompilace](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md).  
  
## <a name="namespace-level-programming-elements"></a>Namespace úrovni programovací elementy  
 Tříd, struktur a moduly obsahovat veškerý kód ve zdrojovém souboru. Jsou *úrovni oboru názvů* prvky, které se mohou objevit v oboru názvů nebo na úrovni zdroje. Drží deklarací všechny ostatní programovací elementy. Rozhraní, které definují element podpisy, ale zajištění žádné implementace, zobrazit i na úrovni modulu. Další informace o úrovni modulu elementy naleznete v následujících tématech:  
  
-   [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
-   [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
-   [Příkaz Module](../../../visual-basic/language-reference/statements/module-statement.md)  
  
-   [Příkaz Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 Prvky data na úrovni oboru názvů jsou výčty a delegáti.  
  
## <a name="module-level-programming-elements"></a>Úroveň modulu programovací elementy  
 Postupy, operátory, vlastnosti a události jsou pouze programovací elementy, které mohou být uloženy spustitelného kódu (příkazy, které provádějí akce za běhu). Jsou *úroveň modulu* elementy vašeho programu. Další informace o úroveň procedury elementy naleznete v následujících tématech:  
  
-   [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
-   [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [Příkaz Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
-   [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 Prvky data na úrovni modulu jsou proměnné, konstanty, výčty a delegáti.  
  
## <a name="procedure-level-programming-elements"></a>Úroveň procedury programovací elementy  
 Většinu obsahu *úroveň procedury* prvky jsou spustitelné příkazy, které tvoří běhového kódu vašeho programu. Všechny spustitelný kód musí být v některých postupu (`Function`, `Sub`, `Operator`, `Get`, `Set`, `AddHandler`, `RemoveHandler`, `RaiseEvent`). Další informace najdete v tématu [příkazy](../../../visual-basic/programming-guide/language-features/statements.md).  
  
 Prvky dat na úrovni procedury jsou omezeny na místní proměnné a konstanty.  
  
## <a name="the-main-procedure"></a>Hlavní procedura  
 `Main` Postup je první kód spustit, když se načetl vaší aplikace. `Main` slouží jako výchozí bod a celkové řízení pro vaši aplikaci. Existují čtyři typy `Main`:  
  
-   `Sub Main()`  
  
-   `Sub Main(ByVal cmdArgs() As String)`  
  
-   `Function Main() As Integer`  
  
-   `Function Main(ByVal cmdArgs() As String) As Integer`  
  
 Nejběžnější řadu tento postup je `Sub Main()`. Další informace najdete v tématu [hlavní procedura v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md).  
  
## <a name="see-also"></a>Viz také  
 [Hlavní procedura v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)  
 [Zásady vytváření názvů jazyka Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [Omezení jazyka Visual Basic](../../../visual-basic/programming-guide/program-structure/limitations.md)
