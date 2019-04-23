---
title: 'Postupy: Předání argumentů proceduře (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- arguments [Visual Basic], passing to procedures
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], calling
- argument passing [Visual Basic], procedures
ms.assetid: 08723588-3890-4ddc-8249-79e049e0f241
ms.openlocfilehash: 012ad8e6229958575030ee820a3b0b79cc50facc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59333903"
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a>Postupy: Předání argumentů proceduře (Visual Basic)
Při volání procedury, použijte název procedury se seznamem argumentů v závorkách. Zadat argument odpovídající každý povinný parametr postupu definuje, a volitelně můžete zadat argumenty, které mají `Optional` parametry. Pokud nezadáte `Optional` parametr ve volání musí obsahovat čárku k označení příslušné místo v seznamu argumentů, pokud zadáváte libovolné další argumenty.  
  
 Pokud chcete předat argument typu dat liší od odpovídajícího parametru, jako například `Byte` k `String`, nastavíte přepínač kontrola typu ([Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) k `Off`. Pokud `Option Strict` je `On`, je nutné použít buď rozšiřující převody nebo klíčová slova explicitní převod. Další informace najdete v tématu [Widening a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) a [funkce pro převod typů](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 Další informace najdete v tématu [parametry a argumenty procedury](./procedure-parameters-and-arguments.md).  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a>K předání jeden nebo více argumentů proceduře  
  
1. V příkazu volání použijte název procedury se závorkami.  
  
2. Uvnitř závorek uveďte seznam argumentů. Argument pro každý požadovaný parametr postupu definuje zahrnout a argumenty oddělujte čárkami.  
  
3. Ujistěte se, že každý argument není platný výraz, který je vyhodnocen jako typ dat lze převést na typ procesu definuje pro odpovídající parametr.  
  
4. Pokud parametr je definován jako [volitelné](../../../../visual-basic/language-reference/modifiers/optional.md), můžete zahrnout do seznamu argumentů, nebo ji vynechte. Pokud ho vynecháte, použije procedura výchozí hodnotu definovanou pro tento parametr.  
  
5. Pokud vynecháte argument `Optional` parametrů a je jiný parametr v seznamu parametrů po něm, určíte místo vynechaný argument navíc čárkou v seznamu argumentů.  
  
     Následující příklad volá jazyka Visual Basic <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> funkce.  
  
     [!code-vb[VbVbcnProcedures#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#34)]  
  
     V předchozím příkladu poskytuje požadované první argument, který je řetězec zprávy, který se má zobrazit. Vynechá argument pro volitelný druhý parametr, který určuje tlačítka, který se má zobrazit v okně se zprávou. Protože volání neposkytne hodnotu, `MsgBox` používá výchozí hodnotu `MsgBoxStyle.OKOnly`, zobrazuje pouze **OK** tlačítko.  
  
     Označuje druhou čárkou v seznamu argumentů místo vynechaný druhého argumentu a volitelný třetí parametr je předán poslední řetězec `MsgBox`, což je text, který má být zobrazen v záhlaví programu.  
  
## <a name="see-also"></a>Viz také:

- [Procedury Sub](./sub-procedures.md)
- [Procedury funkce](./function-procedures.md)
- [Procedury vlastnosti](./property-procedures.md)
- [Procedury operátoru](./operator-procedures.md)
- [Postupy: Definování parametru pro proceduru](./how-to-define-a-parameter-for-a-procedure.md)
- [Předávání argumentů podle hodnoty a reference](./passing-arguments-by-value-and-by-reference.md)
- [Rekurzivní procedury](./recursive-procedures.md)
- [Přetížení procedury](./procedure-overloading.md)
- [Objekty a třídy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Objektově orientované programování (Visual Basic)](../../concepts/object-oriented-programming.md)
