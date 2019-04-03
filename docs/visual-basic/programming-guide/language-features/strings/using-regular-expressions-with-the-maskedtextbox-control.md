---
title: Používání regulárních výrazů s ovládacím prvkem MaskedTextBox v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], regular expressions
- strings [Visual Basic], masked edit
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
ms.openlocfilehash: e0165fb8d573878ae19378b2656d89627680b804
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826732"
---
# <a name="using-regular-expressions-with-the-maskedtextbox-control-in-visual-basic"></a>Používání regulárních výrazů s ovládacím prvkem MaskedTextBox v jazyce Visual Basic
Tento příklad ukazuje, jak převést jednoduché regulárních výrazů pro práci s <xref:System.Windows.Forms.MaskedTextBox> ovládacího prvku.  
  
## <a name="description-of-the-masking-language"></a>Popis jazyka maskování  
 Standardní <xref:System.Windows.Forms.MaskedTextBox> maskování jazyka podle používají `Masked Edit` řízení v jazyce Visual Basic 6.0 a měla by být migraci z této platformy uživatelé znají.  
  
 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> Vlastnost <xref:System.Windows.Forms.MaskedTextBox> ovládacího prvku určuje, jaké vstupní maska používat. Maska musí být řetězec skládá z jedné nebo více prvků maskování z následující tabulky.  
  
|Element maskování|Popis|Regulární výraz element|  
|---------------------|-----------------|--------------------------------|  
|0|Libovolná číslice od 0 do 9. Je nutné provést zadání.|\d|  
|9|Číslice nebo mezera. Položka je nepovinná.|[ \d]?|  
|#|Číslice nebo mezera. Položka je nepovinná. Pokud toto umístění je prázdné v masce, zobrazí se jako mezera. Plus (+) a minus (-) jsou povolené znaky.|[ \d+-]?|  
|L|Písmeno ASCII. Je nutné provést zadání.|[a-zA-Z]|  
|?|Písmeno ASCII. Položka je nepovinná.|[a-zA-Z]?|  
|&|znak. Je nutné provést zadání.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]|  
|C|znak. Položka je nepovinná.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]?|  
|OBJEKT|Alfanumerické znaky. Položka je nepovinná.|\W|  
|.|Odpovídající jazykovou verzi zástupný znak desetinné čárky.|Není k dispozici.|  
|, |Zástupný symbol tisíců odpovídající jazykovou verzi.|Není k dispozici.|  
|:|Oddělovač času odpovídající jazykovou verzi.|Není k dispozici.|  
|/|Oddělovač data odpovídající jazykovou verzi.|Není k dispozici.|  
|$|Symbol měny odpovídající jazykovou verzi.|Není k dispozici.|  
|\<|Převede všechny znaky, které následují na malá písmena.|Není k dispozici.|  
|>|Převede všechny znaky, které následují na velká písmena.|Není k dispozici.|  
|&#124;|Vrátí zpět předchozí posunutí nahoru a přesunout.|Není k dispozici.|  
|&#92;|Řídicí sekvence znaku masky zapnutí na literál. "\\\\" je řídicí sekvenci zpětného lomítka.|&#92;|  
|Všechny ostatní znaky.|Literály. Všechny elementy bez masky se zobrazí jako sami v rámci <xref:System.Windows.Forms.MaskedTextBox>.|Všechny ostatní znaky.|  
  
 Desetinné číslo (.), tisícin (,), čas (:), datum (/) a výchozí symboly měny ($) k zobrazení těchto symbolů podle jazykové verze vaší aplikace. Můžete vynutit, je pro zobrazení symbolů pro jinou jazykovou verzi pomocí <xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A> vlastnost.  
  
## <a name="regular-expressions-and-masks"></a>Regulární výrazy a masek  
 I když regulárních výrazů a masek slouží k ověření vstupu uživatele, nejsou zcela ekvivalentní. Regulární výrazy můžete vyjádřit složitější vzorce než masky, ale masky můžete vyjádřit stejné informace, informace ve zhuštěné a jazykově odpovídající formát.  
  
 Následující tabulka porovnává pro všechny čtyři regulárních výrazů a odpovídající masku.  
  
|Regulární výraz|Maska|Poznámky|  
|------------------------|----------|-----------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|`/` Znak v maska je logický oddělovač, se zobrazí uživateli jako oddělovač data pro aktuální jazykovou verzi aplikace.|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|Datum (den, zkratku měsíce a roku) ve Spojených státech amerických formát, ve kterém se zobrazí zkratku měsíce tří písmen s počáteční velkým písmenem, za nímž následuje dvě písmena malá.|  
|`(\(\d{3}\)-)?\d{3}-d{4}`|`(999)-000-0000`|Spojené státy telefonní číslo, předčíslí volitelné. Pokud uživatel nechce zadejte volitelné znaky, které můžete zadat mezery nebo umístěte ukazatel myši přímo na pozici v masce reprezentována první 0.|  
|`$\d{6}.00`|`$999,999.00`|Hodnota měny v rozsahu 0-999999. Měna, / 1 000 a decimální znaky se nahradí za běhu ekvivalenty specifické pro jazykovou verzi.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>
- <xref:System.Windows.Forms.MaskedTextBox>
- [Ověřování řetězců v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
- [Ovládací prvek MaskedTextBox](../../../../framework/winforms/controls/maskedtextbox-control-windows-forms.md)
