---
title: 'Postupy: Volání procedury, která vrátí hodnotu (Visual Basic).'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: 35f757609b6d0b36652db3b14e62ecd299a063ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649409"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a>Postupy: Volání procedury, která vrátí hodnotu (Visual Basic).
A `Function` postup vrátí hodnotu volání kódu. Můžete pro volání ho včetně jeho název a argumenty buď na pravé straně příkazu přiřazení nebo ve výrazu.  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a>K volání procedury, funkce v rámci výrazu  
  
1.  Použít `Function` postupu název stejným způsobem jako použijete proměnnou. Můžete použít `Function` volání procedur, kdekoli proměnnou nebo konstanta můžete použít ve výrazu.  
  
2.  Použijte název procedury v závorkách uveďte seznam argumentů. Pokud neexistují žádné argumenty, můžete volitelně vynechat závorkách. Však pomocí závorek usnadňuje kódu čtení.  
  
3.  Umístěte argumenty v seznamu argumentů v závorkách, oddělených čárkami. Ujistěte se, zadejte argumenty ve stejném pořadí, `Function` postupu definuje odpovídající parametry.  
  
     Alternativně můžete předat jeden nebo více argumentů podle názvu. Další informace najdete v tématu [předávání argumentů podle pozice a názvu](./passing-arguments-by-position-and-by-name.md).  
  
4.  Hodnota vrácená z procesu účastní výraz stejně jako hodnota proměnné nebo by konstanta.  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a>K volání procedury, funkce v příkazu přiřazení  
  
1.  Použití `Function` název procedury následující rovno (`=`) přihlásit příkaz přiřazení.  
  
2.  Použijte název procedury v závorkách uveďte seznam argumentů. Pokud neexistují žádné argumenty, můžete volitelně vynechat závorkách. Však pomocí závorek usnadňuje kódu čtení.  
  
3.  Umístěte argumenty v seznamu argumentů v závorkách, oddělených čárkami. Ujistěte se, zadejte argumenty ve stejném pořadí, `Function` postupu definuje odpovídajících parametrů, pokud jsou jejich předání podle názvu.  
  
4.  Hodnota vrácená v postupu je uložené v proměnné nebo vlastnosti na levé straně příkazu přiřazení.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu volání jazyka Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> k načtení hodnoty proměnné prostředí operačního systému. První řádek volání `Environ` ve výrazu a druhý řádek nazve je v příkazu přiřazení. `Environ` přebírá název proměnné jako jedinou argument. Hodnota proměnné vrátí volání kódu.  
  
 [!code-vb[VbVbcnProcedures#7](./codesnippet/VisualBasic/how-to-call-a-procedure-that-returns-a-value_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Procedury funkce](./function-procedures.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Příkaz Function](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Postupy: Vytvoření procedury, která vrací hodnotu](./how-to-create-a-procedure-that-returns-a-value.md)  
 [Postupy: Vrácení hodnoty z procedury](./how-to-return-a-value-from-a-procedure.md)  
 [Postupy: Volání procedury, která nevrací hodnotu](./how-to-call-a-procedure-that-does-not-return-a-value.md)
