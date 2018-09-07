---
title: Odkazy a příkaz Imports (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
ms.openlocfilehash: 89d360e5caa3cdb0dd1ecb985ea7ba727e5a6d9d
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44080150"
---
# <a name="references-and-the-imports-statement-visual-basic"></a>Odkazy a příkaz Imports (Visual Basic)
Můžete zpřístupnit externí objekty do vašeho projektu výběrem **přidat odkaz** příkaz **projektu** nabídky. Odkazy v jazyce Visual Basic se může odkazovat na sestavení, které jsou podobné, ale obsahují další informace o knihovnách typů.  
  
## <a name="the-imports-statement"></a>Příkaz Imports  
 Sestavení obsahují jeden nebo více oborů názvů. Když přidáte odkaz na sestavení, můžete také přidat `Imports` příkazu pro modul, který určuje, zda se toto sestavení obory názvů v rámci modulu. `Imports` Příkaz poskytuje oboru kontext, který vám umožní používat pouze část oboru názvů, který je nutné zadat jedinečný odkaz.  
  
 `Imports` Příkaz má následující syntaxi:  
  
 `Imports` [`|``Aliasname` =] `Namespace`  
  
 `Aliasname` odkazuje na krátký název, který můžete použít v kódu k odkazování na importované oboru názvů. `Namespace` je k dispozici prostřednictvím obor názvů odkazu na projekt, prostřednictvím definice v rámci projektu, nebo předchozí `Imports` příkazu.  
  
 Modul může obsahovat libovolný počet `Imports` příkazy. Musí být uvedena po všech `Option` příkazy, pokud jsou k dispozici, ale před spuštěním kódu.  
  
> [!NOTE]
>  Nepleťte si odkazy na projekt s `Imports` příkazu nebo `Declare` příkazu. Odkazy na projekt zpřístupnit externí objekty, jako jsou objekty v sestaveních pro projekty jazyka Visual Basic. `Imports` Prohlášení se používá pro zjednodušení přístupu do odkazů projektu, ale neposkytuje přístup k těmto objektům. `Declare` Prohlášení se používá k deklarování odkazu na externí procedura v dynamická knihovna (DLL).  
  
## <a name="using-aliases-with-the-imports-statement"></a>Aliasy Using se příkaz Imports  
 `Imports` Příkaz usnadňuje přístup metod tříd pomocí tím eliminuje nutnost explicitně zadejte plně kvalifikované názvy odkazů. Aliasy umožňují lépe vyhovující název přiřadit pouze jednu část oboru názvů. Například sekvence, která způsobí, že každé text, který se má zobrazit na více řádcích vrátit návrat na začátek řádku a nového řádku je součástí <xref:Microsoft.VisualBasic.ControlChars> v modulu <xref:Microsoft.VisualBasic?displayProperty=nameWithType> oboru názvů. Použití této konstanty v programu bez alias, je třeba zadáním následujícího kódu:  
  
 [!code-vb[VbVbalrApplication#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]  
  
 `Imports` příkazy musí být vždy první řádky hned za všechny `Option` příkazy v modulu. Následující fragment kódu ukazuje, jak importovat a přiřadit alias <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> modul:  
  
 [!code-vb[VbVbalrApplication#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]  
  
 Budoucí odkazy na tento obor názvů může být podstatně kratší:  
  
 [!code-vb[VbVbalrApplication#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]  
  
 Pokud `Imports` příkaz neobsahuje název aliasu, prvky definované v rámci importované oboru názvů lze použít v modulu bez kvalifikace. Pokud je zadán název aliasu, se musí použít jako kvalifikátoru pro názvy obsažené v daném oboru názvů.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.ControlChars>
- <xref:Microsoft.VisualBasic>
- [Obory názvů v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
- [Sestavení a globální mezipaměť sestavení (GAC)](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
- [Postupy: Vytváření a použití sestavení s pomocí příkazového řádku](../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)  
- [Příkaz Imports (obor názvů a typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
