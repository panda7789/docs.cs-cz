---
title: DirectCast – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords:
- DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
ms.openlocfilehash: 96cb2082d59373deb34d6894270205b7c1045850
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371515"
---
# <a name="directcast-operator-visual-basic"></a>DirectCast – operátor (Visual Basic)
Zavádí operaci převodu typu na základě dědičnosti nebo implementace.  
  
## <a name="remarks"></a>Poznámky  
 `DirectCast`nepoužívá rutiny pomocné rutiny runtime Visual Basic pro převod, takže může poskytovat poněkud lepší výkon než `CType` při převodu do a z datového typu `Object` .  
  
 `DirectCast`Klíčové slovo se používá podobně jako při použití [funkce CType](../functions/ctype-function.md) a klíčového slova [operátoru TryCast](trycast-operator.md) . Výraz zadejte jako první argument a typ, který jej převede jako druhý argument. `DirectCast`vyžaduje vztah dědičnosti nebo implementace mezi datovými typy dvou argumentů. To znamená, že jeden typ musí dědit z nebo implementovat druhý.  
  
## <a name="errors-and-failures"></a>Chyby a selhání  
 `DirectCast`vygeneruje chybu kompilátoru, pokud zjistí, že neexistuje vztah dědičnosti nebo implementace. Chybějící Chyba kompilátoru ale nezaručuje úspěšný převod. Pokud je požadovaný převod zúžený, může v době běhu selhat. Pokud k tomu dojde, modul runtime vyvolá <xref:System.InvalidCastException> chybu.  
  
## <a name="conversion-keywords"></a>Klíčová slova převodu  
 Porovnání klíčových slov převodu typů je následující.  
  
|Klíčové slovo|Datové typy|Relace argumentu|Selhání za běhu|  
|---|---|---|---|  
|[CType – funkce](../functions/ctype-function.md)|Všechny typy dat|Mezi dvěma datovými typy musí být definovaný rozšiřující nebo zužující převod.|Vyvolá<xref:System.InvalidCastException>|  
|`DirectCast`|Všechny typy dat|Jeden typ musí dědit z nebo implementovat jiný typ.|Vyvolá<xref:System.InvalidCastException>|  
|[TryCast – operátor](trycast-operator.md)|Pouze odkazované typy|Jeden typ musí dědit z nebo implementovat jiný typ.|Vrátí hodnotu [Nothing](../nothing.md) .|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje dvě použití `DirectCast` , jednu, která selže v době běhu a druhá, která je úspěšná.  
  
 [!code-vb[VbVbalrKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#1)]  
  
 V předchozím příkladu je běhový typ typu `q` `Double` . `CType`úspěch, protože `Double` lze převést na `Integer` . První ale v `DirectCast` době běhu se nezdařila, protože typ modulu runtime `Double` nemá žádný vztah dědičnosti s `Integer` , i když existuje převod. Druhá je `DirectCast` úspěšná, protože se převede z typu <xref:System.Windows.Forms.Form> na typ <xref:System.Windows.Forms.Control> , ze kterého <xref:System.Windows.Forms.Form> dědí.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>
- [Rozšíření a zúžení převodů](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Implicitní a explicitní převody](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
