---
title: 'Postupy: Změna hodnoty argumentu procedury'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
ms.openlocfilehash: e562c0f5ec01380c792b4dc064554171cfb007e7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74339958"
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a>Postupy: Změna hodnoty argumentu procedury (Visual Basic)
Když zavoláte proceduru, každý argument, který zadáte, odpovídá jednomu z parametrů definovaných v proceduře. V některých případech kód procedury může změnit hodnotu podkladové hodnoty argumentu v volajícím kódu. V jiných případech může procedura změnit pouze svou místní kopii argumentu.  
  
 Když zavoláte proceduru, Visual Basic vytvoří místní kopii každého argumentu, který je předaný metodě [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). Pro každý argument předaný [parametr ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)Visual Basic poskytne kód procedury přímý odkaz na programovací element podkladové argumentu v volajícím kódu.  
  
 Pokud podkladový prvek v kódu volání je upravitelný prvek a argument je předán `ByRef`, kód procedury může použít přímý odkaz pro změnu hodnoty prvku v kódu volajícího.  
  
## <a name="changing-the-underlying-value"></a>Změna základní hodnoty  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a>Změna základní hodnoty argumentu procedury v kódu volání  
  
1. V deklaraci procedury zadejte typ [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) pro parametr odpovídající argumentu.  
  
2. V kódu volajícího předejte jako argument upravitelný programový prvek.  
  
3. V kódu volajícího nemusíte v seznamu argumentů uzavřít argument do závorek.  
  
4. V kódu procedury použijte název parametru pro přiřazení hodnoty k základnímu prvku v volajícím kódu.  
  
 Ukázku najdete v níže uvedeném příkladu.  
  
## <a name="changing-local-copies"></a>Změna místních kopií  
 Pokud podkladový prvek v kódu volání je neupravitelný prvek, nebo pokud je argument předán `ByVal`, procedura nemůže změnit jeho hodnotu v volajícím kódu. Procedura však může změnit svou místní kopii takového argumentu.  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a>Chcete-li změnit kopii argumentu procedury v kódu procedury  
  
1. V deklaraci procedury zadejte [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) pro parametr odpovídající argumentu.  
  
     -nebo-  
  
     V kódu volajícího uveďte argument do závorek v seznamu argumentů. To vynutí Visual Basic předat argument podle hodnoty, a to i v případě, že odpovídající parametr určuje `ByRef`.  
  
2. V kódu procedury použijte název parametru k přiřazení hodnoty místní kopii argumentu. Podkladová hodnota v kódu volajícího není změněna.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje dva postupy, které přebírají proměnnou pole a pracují s jejími prvky. Postup `increase` jednoduše přidá jeden do každého prvku. `replace` procedura přiřadí parametr novému poli `a()` a poté přidá jeden do každého prvku.  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#36)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 První `MsgBox` volání zobrazí "po zvýšení (n): 11, 21, 31, 41". Protože `n` pole je odkazový typ, `replace` mohou změnit jeho členy, i když je mechanismus předávání `ByVal`.  
  
 Druhý `MsgBox` volání zobrazí "po nahrazení (n): 101, 201, 301". Vzhledem k tomu, že `n` je předán `ByRef`, `replace` může změnit proměnnou `n` ve volání kódu a přiřadit nové pole. Vzhledem k tomu, že `n` je odkazový typ, `replace` mohou také měnit jeho členy.  
  
 Můžete zabránit postupu v úpravě proměnné samotné v kódu volání. Viz [Postupy: Ochrana argumentu procedury proti změnám hodnot](./how-to-protect-a-procedure-argument-against-value-changes.md).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Pokud předáte proměnnou odkazem, je nutné použít klíčové slovo `ByRef` k určení tohoto mechanismu.  
  
 Výchozí hodnotou v Visual Basic je předání argumentů podle hodnoty. Nicméně je dobrým programovacím postupem, jak zahrnout klíčové slovo [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) nebo [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) s každým deklarovaným parametrem. To usnadňuje čtení kódu.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 V případě, že je možné změnit hodnotu podkladového typu argumentu v volajícím kódu, je vždy potenciálním rizikem. Ujistěte se, že jste očekávali, že tato hodnota se má změnit, a je připravená ji před použitím ověřit.  
  
## <a name="see-also"></a>Viz také:

- [Procedury](./index.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Postupy: Předání argumentů proceduře](./how-to-pass-arguments-to-a-procedure.md)
- [Předávání argumentů podle hodnoty a reference](./passing-arguments-by-value-and-by-reference.md)
- [Rozdíly mezi upravitelnými a neupravitelnými argumenty](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [Rozdíly mezi předáním argumentu podle hodnoty a podle reference](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [Postupy: Ochrana argumentu procedury před změnami hodnoty](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Postupy: Vynucení předání argumentu podle hodnoty](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Předávání argumentů podle pozice a názvu](./passing-arguments-by-position-and-by-name.md)
- [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
