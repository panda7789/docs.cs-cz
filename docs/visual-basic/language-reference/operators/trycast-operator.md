---
title: TryCast – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords:
- TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
ms.openlocfilehash: 53306575cfc385039be3939fd87cf993b4509af4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348217"
---
# <a name="trycast-operator-visual-basic"></a>TryCast – operátor (Visual Basic)
Zavádí operaci převodu typu, která nevyvolá výjimku.  
  
## <a name="remarks"></a>Poznámky  
 Pokud se pokus o převod nezdaří, `CType` a `DirectCast` vyvolá chybu <xref:System.InvalidCastException>. To může mít nepříznivý vliv na výkon aplikace. `TryCast` nevrátí [žádnou](../../../visual-basic/language-reference/nothing.md)hodnotu, takže místo nutnosti zpracovat možnou výjimku budete potřebovat pouze test vráceného výsledku proti `Nothing`.  
  
 Klíčové slovo `TryCast` použijete stejným způsobem jako [funkci CType](../../../visual-basic/language-reference/functions/ctype-function.md) a klíčové slovo [operátoru DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) . Výraz zadejte jako první argument a typ, který jej převede jako druhý argument. `TryCast` funguje pouze na odkazových typech, jako jsou třídy a rozhraní. Vyžaduje vztah dědičnosti nebo implementace mezi těmito dvěma typy. To znamená, že jeden typ musí dědit z nebo implementovat druhý.  
  
## <a name="errors-and-failures"></a>Chyby a selhání  
 `TryCast` generuje chybu kompilátoru, pokud zjistí, že neexistuje žádná dědičnost nebo implementace relace. Chybějící Chyba kompilátoru ale nezaručuje úspěšný převod. Pokud je požadovaný převod zúžený, může v době běhu selhat. Pokud k tomu dojde, `TryCast` nevrátí [žádnou](../../../visual-basic/language-reference/nothing.md)hodnotu.  
  
## <a name="conversion-keywords"></a>Klíčová slova převodu  
 Porovnání klíčových slov převodu typů je následující.  
  
|Klíčové slovo|Typy dat|Relace argumentu|Selhání za běhu|  
|---|---|---|---|  
|[Funkce CType](../../../visual-basic/language-reference/functions/ctype-function.md)|Všechny typy dat|Mezi dvěma datovými typy musí být definovaný rozšiřující nebo zužující převod.|Vyvolá <xref:System.InvalidCastException>|  
|[Operátor DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md)|Všechny typy dat|Jeden typ musí dědit z nebo implementovat jiný typ.|Vyvolá <xref:System.InvalidCastException>|  
|`TryCast`|Pouze odkazované typy|Jeden typ musí dědit z nebo implementovat jiný typ.|Vrátí hodnotu [Nothing](../../../visual-basic/language-reference/nothing.md) .|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít `TryCast`.  
  
 [!code-vb[VbVbalrKeywords#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Viz také:

- [Rozšíření a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Implicitní a explicitní převody](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
