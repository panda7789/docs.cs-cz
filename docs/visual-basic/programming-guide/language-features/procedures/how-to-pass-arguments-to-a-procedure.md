---
title: 'Postupy: Předání argumentů proceduře'
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
ms.openlocfilehash: 903e05facccd1f2afdf4bb51b200531feb64aa79
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387774"
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a>Postupy: Předání argumentů proceduře (Visual Basic)
Při volání procedury se v závorkách použije název procedury se seznamem argumentů. Zadejte argument odpovídající každému požadovanému parametru, který procedura definuje, a volitelně můžete zadat argumenty pro `Optional` parametry. Pokud nezadáte `Optional` parametr ve volání, je nutné použít čárku k označení místa v seznamu argumentů, pokud zadáváte další argumenty.  
  
 Pokud máte v úmyslu předat argument datového typu, který se liší od odpovídajícího parametru, například `Byte` do `String` , můžete nastavit přepínač typu pro kontrolu a ([možnost striktní](../../../language-reference/statements/option-strict-statement.md)) na `Off` . Pokud `Option Strict` je `On` , je nutné použít buď rozšiřující převody, nebo explicitní klíčová slova převodu. Další informace najdete v tématu [rozšiřování a zúžení převodů](../data-types/widening-and-narrowing-conversions.md) a [funkcí pro převod typů](../../../language-reference/functions/type-conversion-functions.md).  
  
 Další informace najdete v tématu [parametry a argumenty procedury](./procedure-parameters-and-arguments.md).  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a>Předání jednoho nebo více argumentů proceduře  
  
1. V příkazu call použijte název procedury s závorkami.  
  
2. Uvnitř závorek vložte seznam argumentů. Zahrňte argument pro každý povinný parametr, který procedura definuje, a oddělte argumenty čárkami.  
  
3. Ujistěte se, že každý argument je platný výraz, který je vyhodnocen jako datový typ převoditelný na typ, který definuje procedura pro odpovídající parametr.  
  
4. Pokud je parametr definovaný jako [volitelný](../../../language-reference/modifiers/optional.md), můžete ho buď zahrnout do seznamu argumentů, nebo ho vynechat. Pokud ji vynecháte, procedura použije výchozí hodnotu definovanou pro tento parametr.  
  
5. Vynecháte-li argument pro `Optional` parametr a v seznamu parametrů je jiný parametr, můžete místo vynechaného argumentu označit čárkou navíc v seznamu argumentů.  
  
     Následující příklad volá <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> funkci Visual Basic.  
  
     [!code-vb[VbVbcnProcedures#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#34)]  
  
     Předchozí příklad dodá požadovaný první argument, což je řetězec zprávy, který má být zobrazen. Vynechá argument pro nepovinný druhý parametr, který určuje tlačítka, která se mají zobrazit v okně se zprávou. Protože volání neposkytuje hodnotu, `MsgBox` používá výchozí hodnotu, `MsgBoxStyle.OKOnly` která zobrazí pouze tlačítko **OK** .  
  
     Druhá čárka v seznamu argumentů označuje místo vynechaného druhého argumentu a poslední řetězec je předán volitelnému třetímu parametru `MsgBox` , který je text zobrazený v záhlaví.  
  
## <a name="see-also"></a>Viz také

- [Procedury Sub](./sub-procedures.md)
- [Procedury funkcí](./function-procedures.md)
- [Procedury vlastnosti](./property-procedures.md)
- [Procedury operátoru](./operator-procedures.md)
- [Postupy: Definování parametru pro proceduru](./how-to-define-a-parameter-for-a-procedure.md)
- [Předávání argumentů podle hodnoty a reference](./passing-arguments-by-value-and-by-reference.md)
- [Rekurzivní procedury](./recursive-procedures.md)
- [Přetížení procedury](./procedure-overloading.md)
- [Objekty a třídy](../objects-and-classes/index.md)
- [Objektově orientované programování (Visual Basic)](../../concepts/object-oriented-programming.md)
