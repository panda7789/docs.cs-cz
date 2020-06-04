---
title: TryCast – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords:
- TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
ms.openlocfilehash: 8f0d4f612cd5a96e0b0ab7305c41e00790613cc8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406372"
---
# <a name="trycast-operator-visual-basic"></a>TryCast – operátor (Visual Basic)
Zavádí operaci převodu typu, která nevyvolá výjimku.  
  
## <a name="remarks"></a>Poznámky  
 Pokud pokus o převod neproběhne úspěšně `CType` , `DirectCast` vyvolejte <xref:System.InvalidCastException> chybu. To může mít nepříznivý vliv na výkon aplikace. `TryCast`nevrátí [žádnou](../nothing.md)hodnotu, takže namísto nutnosti zpracovat možnou výjimku budete potřebovat pouze test vráceného výsledku `Nothing` .  
  
 `TryCast`Klíčové slovo se používá stejným způsobem jako [funkce CType](../functions/ctype-function.md) a klíčové slovo [operátoru DirectCast](directcast-operator.md) . Výraz zadejte jako první argument a typ, který jej převede jako druhý argument. `TryCast`funguje pouze na odkazových typech, jako jsou třídy a rozhraní. Vyžaduje vztah dědičnosti nebo implementace mezi těmito dvěma typy. To znamená, že jeden typ musí dědit z nebo implementovat druhý.  
  
## <a name="errors-and-failures"></a>Chyby a selhání  
 `TryCast`vygeneruje chybu kompilátoru, pokud zjistí, že neexistuje vztah dědičnosti nebo implementace. Chybějící Chyba kompilátoru ale nezaručuje úspěšný převod. Pokud je požadovaný převod zúžený, může v době běhu selhat. V takovém případě `TryCast` vrátí hodnotu [Nothing](../nothing.md).  
  
## <a name="conversion-keywords"></a>Klíčová slova převodu  
 Porovnání klíčových slov převodu typů je následující.  
  
|Klíčové slovo|Datové typy|Relace argumentu|Selhání za běhu|  
|---|---|---|---|  
|[CType – funkce](../functions/ctype-function.md)|Všechny typy dat|Mezi dvěma datovými typy musí být definovaný rozšiřující nebo zužující převod.|Vyvolá<xref:System.InvalidCastException>|  
|[DirectCast – operátor](directcast-operator.md)|Všechny typy dat|Jeden typ musí dědit z nebo implementovat jiný typ.|Vyvolá<xref:System.InvalidCastException>|  
|`TryCast`|Pouze odkazované typy|Jeden typ musí dědit z nebo implementovat jiný typ.|Vrátí hodnotu [Nothing](../nothing.md) .|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít `TryCast` .  
  
 [!code-vb[VbVbalrKeywords#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Viz také

- [Rozšíření a zúžení převodů](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Implicitní a explicitní převody](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
