---
title: 'Postupy: Volání procedury, která vrátí hodnotu.'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: a110cf9f3b42c7244d8d5bf7b49d5e6dac8c2e21
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388761"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a>Postupy: Volání procedury, která vrátí hodnotu (Visual Basic).
`Function`Procedura vrátí hodnotu volajícímu kódu. Zavoláte ho tak, že zahrnete jeho název a argumenty buď na pravé straně příkazu přiřazení, nebo ve výrazu.  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a>Volání procedury funkce v rámci výrazu  
  
1. Použijte `Function` název procedury stejným způsobem, jako byste použili proměnnou. Můžete použít `Function` volání procedury kdekoliv, kde můžete použít proměnnou nebo konstantu ve výrazu.  
  
2. Chcete-li uzavřít seznam argumentů, použijte název procedury s závorkami. Pokud neexistují žádné argumenty, můžete volitelně vynechat závorky. Použití závorek však usnadňuje čtení kódu.  
  
3. Argumenty umístěte do seznamu argumentů v závorkách a oddělte je čárkami. Ujistěte se, že jste zadali argumenty ve stejném pořadí, v jakém `Function` procedura definuje odpovídající parametry.  
  
     Alternativně můžete předat jeden nebo více argumentů podle názvu. Další informace najdete v tématu [předávání argumentů podle pozice a názvu](./passing-arguments-by-position-and-by-name.md).  
  
4. Hodnota vrácená procedurou se účastní ve výrazu stejně jako hodnota proměnné nebo konstanty.  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a>Volání procedury funkce v příkazu přiřazení  
  
1. Použijte `Function` název procedury za znaménkem EQUAL ( `=` ) v příkazu přiřazení.  
  
2. Chcete-li uzavřít seznam argumentů, použijte název procedury s závorkami. Pokud neexistují žádné argumenty, můžete volitelně vynechat závorky. Použití závorek však usnadňuje čtení kódu.  
  
3. Argumenty umístěte do seznamu argumentů v závorkách a oddělte je čárkami. Ujistěte se, že jste zadali argumenty ve stejném pořadí, v jakém `Function` procedura definuje odpovídající parametry, pokud je předáte podle názvu.  
  
4. Hodnota vrácená procedurou je uložena v proměnné nebo vlastnosti na levé straně příkazu přiřazení.  
  
## <a name="example"></a>Příklad  
 Následující příklad volá Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> pro načtení hodnoty proměnné prostředí operačního systému. První řádek volá `Environ` v rámci výrazu a druhý řádek jej zavolá v příkazu přiřazení. `Environ`Převede název proměnné jako svůj jediný argument. Vrátí hodnotu proměnné pro volající kód.  
  
 [!code-vb[VbVbcnProcedures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#7)]  
  
## <a name="see-also"></a>Viz také

- [Procedury funkcí](./function-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Function – příkaz](../../../language-reference/statements/function-statement.md)
- [Postupy: Vytvoření procedury, která vrací hodnotu](./how-to-create-a-procedure-that-returns-a-value.md)
- [Postupy: Vrácení hodnoty z procedury](./how-to-return-a-value-from-a-procedure.md)
- [Postupy: Volání procedury, která nevrátí hodnotu.](./how-to-call-a-procedure-that-does-not-return-a-value.md)
