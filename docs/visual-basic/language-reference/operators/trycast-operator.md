---
title: TryCast – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords:
- TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
ms.openlocfilehash: 1bd92428927927a84c1de8f88d176a8f0aba4af2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524937"
---
# <a name="trycast-operator-visual-basic"></a>TryCast – operátor (Visual Basic)
Zavádí operaci převodu typu, který nevyvolá výjimku.  
  
## <a name="remarks"></a>Poznámky  
 Pokud se nezdaří pokus o převod `CType` a `DirectCast` obě throw <xref:System.InvalidCastException> chyby. To může nepříznivě ovlivnit výkon vaší aplikace. `TryCast` Vrátí [nic](../../../visual-basic/language-reference/nothing.md), abyste nemuseli pro zpracování možnou výjimkou potřebujete pouze testovací vrácený výsledek proti `Nothing`.  
  
 Použijete `TryCast` – klíčové slovo stejným způsobem je použít [funkce CType](../../../visual-basic/language-reference/functions/ctype-function.md) a [DirectCast – operátor](../../../visual-basic/language-reference/operators/directcast-operator.md) – klíčové slovo. Můžete zadat výraz jako první argument a typ převést tak, jako druhý argument. `TryCast` funguje pouze na typy odkazů, jako je například třídy a rozhraní. Vyžaduje vztahu dědičnosti nebo implementace mezi těmito dvěma typy. To znamená, že jeden typ musí dědit z nebo implementovat druhé.  
  
## <a name="errors-and-failures"></a>Chyby a selhání  
 `TryCast` vygeneruje chybu kompilátoru, pokud zjistí, že neexistuje žádný vztah dědičnosti nebo implementace. Nezaručuje chybějící chybu kompilátoru úspěšný převod. Pokud je požadovaný převod zužující, může v době běhu selhat. Pokud k tomu dojde, `TryCast` vrátí [nic](../../../visual-basic/language-reference/nothing.md).  
  
## <a name="conversion-keywords"></a>Klíčová slova převodu  
 Porovnání klíčová slova převodu typu je následujícím způsobem.  
  
|Klíčové slovo|Typy dat|Argument vztah|Chyba za běhu|  
|---|---|---|---|  
|[Funkce CType](../../../visual-basic/language-reference/functions/ctype-function.md)|Všechny datové typy|Rozšíření ani zúžení při převodu musí být definovány mezi těmito dvěma datovými typy|Vyvolá výjimku <xref:System.InvalidCastException>|  
|[Operátor DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md)|Všechny datové typy|Jeden typ musí dědit z nebo implementoval další typ.|Vyvolá výjimku <xref:System.InvalidCastException>|  
|`TryCast`|Odkazové typy pouze|Jeden typ musí dědit z nebo implementoval další typ.|Vrátí [nic](../../../visual-basic/language-reference/nothing.md)|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `TryCast`.  
  
 [!code-vb[VbVbalrKeywords#6](../../../visual-basic/language-reference/codesnippet/VisualBasic/trycast-operator_1.vb)]  
  
## <a name="see-also"></a>Viz také:
- [Rozšíření a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Implicitní a explicitní převody](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
