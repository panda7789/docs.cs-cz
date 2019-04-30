---
title: 'Postupy: Volání procedury, která vrací hodnotu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: 6f45f01489ee84b6addb1f7c7c8dc584332f38dd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864179"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a>Postupy: Volání procedury, která vrací hodnotu (Visual Basic)
A `Function` postup vrací hodnotu volajícímu kódu. Při volání včetně jejího názvu a argumenty buď na pravé straně příkazu přiřazení nebo ve výrazu.  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a>Pro volání funkce ve výrazu  
  
1. Použít `Function` postup pojmenovat stejně jako byste použili proměnné. Můžete použít `Function` volání procedur, kdekoli ve výrazu můžete použít proměnnou nebo konstantu.  
  
2. Použijte název procedury se závorkami uvést seznam argumentů. Pokud neexistují žádné argumenty, můžete volitelně vynechejte závorky. Však pomocí závorek díky váš kód lépe čitelný.  
  
3. Umístěte argumenty v seznamu argumentů v závorkách, oddělené čárkami. Je nutné zadat argumenty ve stejném pořadí, které `Function` procedura definuje odpovídající parametry.  
  
     Alternativně můžete předat jeden nebo více argumentů podle názvu. Další informace najdete v tématu [předávání argumentů podle pozice a názvu](./passing-arguments-by-position-and-by-name.md).  
  
4. Hodnota vrácená z procedury podílí na výraz, stejně jako hodnota proměnné nebo by konstanty.  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a>Volat funkci proceduru v příkazu přiřazení  
  
1. Použití `Function` název procedury po rovnosti (`=`) přihlaste příkazu přiřazení.  
  
2. Použijte název procedury se závorkami uvést seznam argumentů. Pokud neexistují žádné argumenty, můžete volitelně vynechejte závorky. Však pomocí závorek díky váš kód lépe čitelný.  
  
3. Umístěte argumenty v seznamu argumentů v závorkách, oddělené čárkami. Je nutné zadat argumenty ve stejném pořadí, které `Function` procedura definuje odpovídající parametry, pokud jsou byly předány podle názvu.  
  
4. Hodnota vrácená z procedury je uložen v proměnné nebo vlastnosti na levé straně příkazu přiřazení.  
  
## <a name="example"></a>Příklad  
 Následující příklad volá jazyka Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> k načtení hodnoty proměnné prostředí operačního systému. První řádek volá `Environ` v rámci výrazu a druhý řádek nazve je v příkazu přiřazení. `Environ` přijímá název proměnné jako její jediný argument. Vrátí hodnotu proměnné volajícímu kódu.  
  
 [!code-vb[VbVbcnProcedures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#7)]  
  
## <a name="see-also"></a>Viz také:

- [Procedury funkce](./function-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Příkaz Function](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Postupy: Vytvořit proceduru, která vrací hodnotu](./how-to-create-a-procedure-that-returns-a-value.md)
- [Postupy: Vrácení hodnoty z procedury](./how-to-return-a-value-from-a-procedure.md)
- [Postupy: Volání procedury, která nevrací hodnotu](./how-to-call-a-procedure-that-does-not-return-a-value.md)
