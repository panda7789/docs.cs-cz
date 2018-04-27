---
title: Odkazy a příkaz Imports (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 051351c2fa0648de54bbfd36b1630ec1cd49d6f0
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="references-and-the-imports-statement-visual-basic"></a>Odkazy a příkaz Imports (Visual Basic)
Můžete zpřístupnit externí objekty do projektu výběrem **přidat odkaz na** příkaz na **projektu** nabídky. Odkazy v jazyce Visual Basic může ukazovat na sestavení, které jsou jako knihovny typů ale obsahují více informací.  
  
## <a name="the-imports-statement"></a>Příkaz Imports  
 Sestavení obsahovat jeden nebo více oborů názvů. Když přidáte odkaz na sestavení, můžete také přidat `Imports` příkaz, který má modul, který určuje, zda obory názvů toto sestavení v modulu. `Imports` Příkaz poskytuje oboru kontext, který vám umožní používat jenom ta část oboru názvů, který je nutné zadat jedinečný odkaz.  
  
 `Imports` Příkaz má následující syntaxi:  
  
 `Imports` [`|``Aliasname` =] `Namespace`  
  
 `Aliasname` odkazuje na krátký název, který můžete použít v kódu odkazovat na importovaný obor názvů. `Namespace` je k dispozici prostřednictvím buď obor názvů odkaz na projekt, prostřednictvím definice v rámci projektu nebo předchozí `Imports` příkaz.  
  
 Modul může obsahovat libovolný počet `Imports` příkazy. Musí být po všech `Option` příkazy, pokud existuje, ale před jakýkoli jiný kód.  
  
> [!NOTE]
>  Nezaměňujte odkazy na projekt s `Imports` příkaz nebo `Declare` příkaz. Odkazy na projekt zpřístupnit externí objekty, například objekty v sestaveních pro projekty Visual Basic. `Imports` Příkaz slouží k zjednodušení přístupu k odkazy na projekt, ale neposkytuje přístup k těmto objektům. `Declare` Příkaz se používá k deklaraci odkaz na externí procedura v dynamické knihovně (DLL).  
  
## <a name="using-aliases-with-the-imports-statement"></a>Aliasy pomocí příkaz Imports  
 `Imports` Příkaz usnadňuje přístup metody třídy odstraněním potřeba explicitně zadejte plně kvalifikované názvy odkazy. Aliasy umožňují příjemnější název přiřadit pouze jeden součástí oboru názvů. Například pořadí, které způsobí, že jedna část textu, který se má zobrazit na více řádcích vrátit znaků CR/nového řádku je součástí <xref:Microsoft.VisualBasic.ControlChars> modulu v <xref:Microsoft.VisualBasic?displayProperty=nameWithType> oboru názvů. Pokud chcete používat tuto konstanta v programu bez alias, museli byste zadáním následujícího kódu:  
  
 [!code-vb[VbVbalrApplication#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]  
  
 `Imports` příkazy musí být vždycky okamžitě následující všechny řádky první `Option` příkazy v modulu. Následující fragment kódu ukazuje, jak importovat a přiřadit na alias <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> modul:  
  
 [!code-vb[VbVbalrApplication#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]  
  
 Může být výrazně kratší budoucí odkazy na tento obor názvů:  
  
 [!code-vb[VbVbalrApplication#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]  
  
 Pokud `Imports` příkaz neobsahuje název aliasu, elementy, které jsou definované v rámci oboru názvů importované lze použít v modulu bez kvalifikace. Pokud je zadaný název aliasu, musíte ho použít jako kvalifikátory pro názvy obsažené v daném oboru názvů.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.ControlChars>  
 <xref:Microsoft.VisualBasic>  
   
 [Obory názvů v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [Sestavení a globální mezipaměť sestavení (GAC)](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Postupy: Vytváření a použití sestavení s pomocí příkazového řádku](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)  
 [Příkaz Imports (obor názvů a typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
