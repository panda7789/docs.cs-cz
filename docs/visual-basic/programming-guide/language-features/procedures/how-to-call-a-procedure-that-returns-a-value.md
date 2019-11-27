---
title: 'Postupy: Volání procedury, která vrátí hodnotu.'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: 7f5d46babf31ea3c6babb29c0f1c08a23e51d598
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340730"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a>Postupy: Volání procedury, která vrátí hodnotu (Visual Basic).
Procedura `Function` vrátí hodnotu volajícímu kódu. Zavoláte ho tak, že zahrnete jeho název a argumenty buď na pravé straně příkazu přiřazení, nebo ve výrazu.  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a>Volání procedury funkce v rámci výrazu  
  
1. Použijte název `Function` procedury stejným způsobem jako při použití proměnné. Můžete použít volání procedury `Function` kdekoli, kde můžete použít proměnnou nebo konstantu ve výrazu.  
  
2. Chcete-li uzavřít seznam argumentů, použijte název procedury s závorkami. Pokud neexistují žádné argumenty, můžete volitelně vynechat závorky. Použití závorek však usnadňuje čtení kódu.  
  
3. Argumenty umístěte do seznamu argumentů v závorkách a oddělte je čárkami. Ujistěte se, že jste zadali argumenty ve stejném pořadí, v jakém `Function` postup definuje odpovídající parametry.  
  
     Alternativně můžete předat jeden nebo více argumentů podle názvu. Další informace najdete v tématu [předávání argumentů podle pozice a názvu](./passing-arguments-by-position-and-by-name.md).  
  
4. Hodnota vrácená procedurou se účastní ve výrazu stejně jako hodnota proměnné nebo konstanty.  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a>Volání procedury funkce v příkazu přiřazení  
  
1. Použijte název `Function` procedury za znaménkem rovná se (`=`) v příkazu přiřazení.  
  
2. Chcete-li uzavřít seznam argumentů, použijte název procedury s závorkami. Pokud neexistují žádné argumenty, můžete volitelně vynechat závorky. Použití závorek však usnadňuje čtení kódu.  
  
3. Argumenty umístěte do seznamu argumentů v závorkách a oddělte je čárkami. Ujistěte se, že jste zadali argumenty ve stejném pořadí, v jakém `Function` postup definuje odpovídající parametry, pokud je předáte podle názvu.  
  
4. Hodnota vrácená procedurou je uložena v proměnné nebo vlastnosti na levé straně příkazu přiřazení.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je volána <xref:Microsoft.VisualBasic.Interaction.Environ%2A> Visual Basic pro načtení hodnoty proměnné prostředí operačního systému. První řádek volá `Environ` v rámci výrazu a druhý řádek jej zavolá v příkazu přiřazení. `Environ` přebírá název proměnné jako jediný argument. Vrátí hodnotu proměnné pro volající kód.  
  
 [!code-vb[VbVbcnProcedures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#7)]  
  
## <a name="see-also"></a>Viz také:

- [Procedury funkce](./function-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Příkaz Function](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Postupy: Vytvoření procedury, která vrací hodnotu](./how-to-create-a-procedure-that-returns-a-value.md)
- [Postupy: Vrácení hodnoty z procedury](./how-to-return-a-value-from-a-procedure.md)
- [Postupy: Volání procedury, která nevrací hodnotu](./how-to-call-a-procedure-that-does-not-return-a-value.md)
