---
title: DirectCast – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords:
- DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
ms.openlocfilehash: 8ea29b80cf27bbb2c21a8cebbfaa0a294e05f11d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331311"
---
# <a name="directcast-operator-visual-basic"></a>DirectCast – operátor (Visual Basic)
Zavádí operaci převodu typu na základě dědičnosti nebo implementace.  
  
## <a name="remarks"></a>Poznámky  
 `DirectCast` neVisual Basic používá rutiny pomocné rutiny runtime pro převod, takže může poskytovat poněkud lepší výkon než `CType` při převodu na nebo z datového typu `Object`.  
  
 Klíčové slovo `DirectCast` lze použít podobně jako způsob použití [funkce CType](../../../visual-basic/language-reference/functions/ctype-function.md) a klíčového slova [operátoru TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md) . Výraz zadejte jako první argument a typ, který jej převede jako druhý argument. `DirectCast` vyžaduje vztah dědičnosti nebo implementace mezi datovými typy dvou argumentů. To znamená, že jeden typ musí dědit z nebo implementovat druhý.  
  
## <a name="errors-and-failures"></a>Chyby a selhání  
 `DirectCast` generuje chybu kompilátoru, pokud zjistí, že neexistuje žádná dědičnost nebo implementace relace. Chybějící Chyba kompilátoru ale nezaručuje úspěšný převod. Pokud je požadovaný převod zúžený, může v době běhu selhat. Pokud k tomu dojde, modul runtime vyvolá chybu <xref:System.InvalidCastException>.  
  
## <a name="conversion-keywords"></a>Klíčová slova převodu  
 Porovnání klíčových slov převodu typů je následující.  
  
|Klíčové slovo|Typy dat|Relace argumentu|Selhání za běhu|  
|---|---|---|---|  
|[Funkce CType](../../../visual-basic/language-reference/functions/ctype-function.md)|Všechny typy dat|Mezi dvěma datovými typy musí být definovaný rozšiřující nebo zužující převod.|Vyvolá <xref:System.InvalidCastException>|  
|`DirectCast`|Všechny typy dat|Jeden typ musí dědit z nebo implementovat jiný typ.|Vyvolá <xref:System.InvalidCastException>|  
|[Operátor TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md)|Pouze odkazované typy|Jeden typ musí dědit z nebo implementovat jiný typ.|Vrátí hodnotu [Nothing](../../../visual-basic/language-reference/nothing.md) .|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje dva způsoby použití `DirectCast`, což je jeden, který selže v době běhu a druhý, který je úspěšný.  
  
 [!code-vb[VbVbalrKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#1)]  
  
 V předchozím příkladu je `q` typ běhu `Double`. `CType` jsou úspěšné, protože `Double` je možné převést na `Integer`. První `DirectCast` ale v době běhu nefunguje, protože typ za běhu `Double` nemá žádný vztah dědičnosti s `Integer`, i když existuje převod. Druhý `DirectCast` úspěch, protože se převede z typu <xref:System.Windows.Forms.Form> na typ <xref:System.Windows.Forms.Control>, ze kterého <xref:System.Windows.Forms.Form> dědí.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>
- [Rozšíření a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Implicitní a explicitní převody](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
