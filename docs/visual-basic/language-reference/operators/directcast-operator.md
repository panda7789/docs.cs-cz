---
title: DirectCast – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords:
- DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
ms.openlocfilehash: 628ce4f06b91d0f514f71dea3aad8ea0fee6dccf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778544"
---
# <a name="directcast-operator-visual-basic"></a>DirectCast – operátor (Visual Basic)
Zavádí operaci převodu typu na základě dědičnosti nebo implementace.  
  
## <a name="remarks"></a>Poznámky  
 `DirectCast` nepoužívá jazyka Visual Basic za běhu pomocné rutiny pro převod, tak může poskytnout mírně vyšší výkon než `CType` při převodu do a z datového typu `Object`.  
  
 Můžete použít `DirectCast` – klíčové slovo podobným způsobem, jakým používáte [funkce CType](../../../visual-basic/language-reference/functions/ctype-function.md) a [TryCast – operátor](../../../visual-basic/language-reference/operators/trycast-operator.md) – klíčové slovo. Můžete zadat výraz jako první argument a typ převést tak, jako druhý argument. `DirectCast` vyžaduje vztahu dědičnosti nebo implementace mezi datovými typy obou argumentů. To znamená, že jeden typ musí dědit z nebo implementovat druhé.  
  
## <a name="errors-and-failures"></a>Chyby a selhání  
 `DirectCast` vygeneruje chybu kompilátoru, pokud zjistí, že neexistuje žádný vztah dědičnosti nebo implementace. Nezaručuje chybějící chybu kompilátoru úspěšný převod. Pokud je požadovaný převod zužující, může v době běhu selhat. Pokud se to stane, modul runtime vyvolá výjimku <xref:System.InvalidCastException> chyby.  
  
## <a name="conversion-keywords"></a>Klíčová slova převodu  
 Porovnání klíčová slova převodu typu je následujícím způsobem.  
  
|Klíčové slovo|Typy dat|Argument vztah|Chyba za běhu|  
|---|---|---|---|  
|[Funkce CType](../../../visual-basic/language-reference/functions/ctype-function.md)|Všechny datové typy|Rozšíření ani zúžení při převodu musí být definovány mezi těmito dvěma datovými typy|Vyvolá výjimku <xref:System.InvalidCastException>|  
|`DirectCast`|Všechny datové typy|Jeden typ musí dědit z nebo implementoval další typ.|Vyvolá výjimku <xref:System.InvalidCastException>|  
|[Operátor TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md)|Odkazové typy pouze|Jeden typ musí dědit z nebo implementoval další typ.|Vrátí [nic](../../../visual-basic/language-reference/nothing.md)|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje dva způsoby použití `DirectCast`, jeden, který selže v době běhu a jeden neuspěje.  
  
 [!code-vb[VbVbalrKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#1)]  
  
 V předchozím příkladu za běhu typ `q` je `Double`. `CType` úspěšná, protože `Double` lze převést na `Integer`. Nicméně první `DirectCast` selže v době běhu, protože typ za běhu `Double` nemá žádný vztah dědičnosti s `Integer`, i když existuje převod. Druhá `DirectCast` proběhne úspěšně, protože ji převede z typu <xref:System.Windows.Forms.Form> na typ <xref:System.Windows.Forms.Control>, ze kterého <xref:System.Windows.Forms.Form> dědí.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>
- [Rozšíření a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Implicitní a explicitní převody](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
