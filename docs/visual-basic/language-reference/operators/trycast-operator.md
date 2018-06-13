---
title: TryCast – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords:
- TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
ms.openlocfilehash: d8825b8eee35ea514d4001a6a5c1cc5139c67454
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33600147"
---
# <a name="trycast-operator-visual-basic"></a>TryCast – operátor (Visual Basic)
Představuje operaci převodu typu, který nevyvolá výjimku.  
  
## <a name="remarks"></a>Poznámky  
 Pokud se nezdaří pokus o převodu, `CType` a `DirectCast` obě throw <xref:System.InvalidCastException> chyby. To může nepříznivě ovlivnit výkon aplikace. `TryCast` Vrátí [nic](../../../visual-basic/language-reference/nothing.md)tak, aby místo nutnosti zpracování možnou výjimkou, potřebovat pouze zkušební vrácených výsledků proti `Nothing`.  
  
 Můžete použít `TryCast` – klíčové slovo stejným způsobem jako použijete [CType – funkce](../../../visual-basic/language-reference/functions/ctype-function.md) a [DirectCast – operátor](../../../visual-basic/language-reference/operators/directcast-operator.md) – klíčové slovo. Můžete zadat jako první argument a zadejte ji do převést jako druhý argument výrazu. `TryCast` funguje pouze na odkazových typech, jako jsou třídy a rozhraní. To vyžaduje relaci dědičnosti nebo implementace mezi těmito dvěma typy. To znamená, že jeden typ musí dědit z nebo implementovat dalších.  
  
## <a name="errors-and-failures"></a>Chyby a selhání  
 `TryCast` Chyba kompilátoru generuje, pokud zjistí, že neexistuje žádný vztah dědičnosti nebo implementace. Ale nedostatek Chyba kompilátoru nezaručuje úspěšné převod. Pokud je zužující převod požadované, pravděpodobně nezdaří za běhu. V takovém případě `TryCast` vrátí [nic](../../../visual-basic/language-reference/nothing.md).  
  
## <a name="conversion-keywords"></a>Klíčová slova převodu  
 Porovnání klíčová slova převodu typu je následující.  
  
|– Klíčové slovo|Typy dat|Argument relace|Běhové chyby|  
|---|---|---|---|  
|[Funkce CType](../../../visual-basic/language-reference/functions/ctype-function.md)|Žádné datové typy|Je nutné definovat rozšiřující nebo zužující převod mezi dvěma datovými typy|Vyvolá <xref:System.InvalidCastException>|  
|[Operátor DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md)|Žádné datové typy|Jeden typ musí dědit z nebo provádět další typ.|Vyvolá <xref:System.InvalidCastException>|  
|`TryCast`|Odkazové typy pouze|Jeden typ musí dědit z nebo provádět další typ.|Vrátí [nic](../../../visual-basic/language-reference/nothing.md)|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `TryCast`.  
  
 [!code-vb[VbVbalrKeywords#6](../../../visual-basic/language-reference/codesnippet/VisualBasic/trycast-operator_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Implicitní a explicitní převody](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
