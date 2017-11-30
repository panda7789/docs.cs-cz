---
title: "Postupy: Předání argumentů proceduře (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3debb4fa6e7b15f9c321ef207d0cc04181a98da2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a>Postupy: Předání argumentů proceduře (Visual Basic)
Při volání procedury, postupujte podle název procedury s seznam argumentů v závorkách. Zadejte argument odpovídající všechny požadované parametry postupu definuje a volitelně můžete zadat argumenty, které mají `Optional` parametry. Pokud nezadáte `Optional` parametr ve volání, musí obsahovat čárkami k označení jeho místo v seznamu argumentů, pokud jsou zadávání žádné další argumenty.  
  
 Pokud máte v úmyslu předat argument typu dat, jako z jeho odpovídající parametr `Byte` k `String`, můžete nastavit přepínač kontrola typu ([Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) k `Off`. Pokud `Option Strict` je `On`, je nutné použít buď rozšiřující převody nebo klíčových slov explicitní převod. Další informace najdete v tématu [Widening a zužující převody](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) a [funkce pro převod typů](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 Další informace najdete v tématu [parametry a argumenty procedury](./procedure-parameters-and-arguments.md).  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a>Předání jeden nebo více argumentů proceduře  
  
1.  V příkazu volání postupujte podle název procedury v závorkách.  
  
2.  V závorkách uveďte seznam argumentů. Argument pro každý požadovaný parametr postupu definuje zahrnout a oddělte je čárkami.  
  
3.  Zajistěte, aby že každý argument je platný výraz, který se vyhodnotí jako typ dat lze převést na typ postupu definuje pro odpovídající parametr.  
  
4.  Pokud parametr je definován jako [volitelné](../../../../visual-basic/language-reference/modifiers/optional.md), můžete zahrnout do seznamu argumentů nebo ji vynechat. Pokud ji vynecháte, postup používá výchozí hodnotu definovanou pro tento parametr.  
  
5.  Pokud vynecháte argument `Optional` parametr a jiný parametr, který je po ho v seznamu parametrů, můžete označit místní vynechání argumentu navíc čárkou v seznamu argumentů.  
  
     Následující příklad volání [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> funkce.  
  
     [!code-vb[VbVbcnProcedures#34](./codesnippet/VisualBasic/how-to-pass-arguments-to-a-procedure_1.vb)]  
  
     V předchozím příkladu poskytuje požadované první argument, který je zpráva řetězec, který se má zobrazit. Se vynechá argument volitelný druhý parametr, který určuje tlačítka, který se má zobrazit v dialogovém okně. Protože volání neposkytuje hodnotu, `MsgBox` používá výchozí hodnotu `MsgBoxStyle.OKOnly`, který zobrazuje pouze **OK** tlačítko.  
  
     Druhý čárkou v seznamu argumentů označí místo vynechaných druhý argument a je předán poslední řetězec volitelný třetí parametr `MsgBox`, což je text, který se zobrazí v záhlaví.  
  
## <a name="see-also"></a>Viz také  
 [Sub – procedury](./sub-procedures.md)  
 [Function – procedury](./function-procedures.md)  
 [Procedury vlastností](./property-procedures.md)  
 [Procedury operátoru](./operator-procedures.md)  
 [Postupy: definování parametru pro proceduru](./how-to-define-a-parameter-for-a-procedure.md)  
 [Předávání argumentů podle hodnoty a podle Reference](./passing-arguments-by-value-and-by-reference.md)  
 [Rekurzivní procedury](./recursive-procedures.md)  
 [Přetížení procedury](./procedure-overloading.md)  
 [Objekty a třídy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Objektově orientované programování](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)
