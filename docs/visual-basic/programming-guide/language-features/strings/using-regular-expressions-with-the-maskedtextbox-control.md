---
title: Používání regulárních výrazů s ovládacím prvkem MaskedTextBox
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], regular expressions
- strings [Visual Basic], masked edit
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
ms.openlocfilehash: b997f6f495fca51e888bb995fee0361d29d68048
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148281"
---
# <a name="using-regular-expressions-with-the-maskedtextbox-control-in-visual-basic"></a>Používání regulárních výrazů s ovládacím prvkem MaskedTextBox v jazyce Visual Basic
Tento příklad ukazuje, jak převést jednoduché regulární výrazy pro práci s ovládacím <xref:System.Windows.Forms.MaskedTextBox> prvkem.  
  
## <a name="description-of-the-masking-language"></a>Popis maskovacího jazyka  
 Standardní <xref:System.Windows.Forms.MaskedTextBox> maskovací jazyk je založen na `Masked Edit` jazyku používaném ovládacím prvkem v jazyce Visual Basic 6.0 a měl by být známý uživatelům, kteří migrují z této platformy.  
  
 Vlastnost <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> ovládacího <xref:System.Windows.Forms.MaskedTextBox> prvku určuje, jakou vstupní masku použít. Maska musí být řetězec složený z jednoho nebo více maskovacích prvků z následující tabulky.  
  
|Maskovací prvek|Popis|Element regulárního výrazu|  
|---------------------|-----------------|--------------------------------|  
|0|Libovolná jedna číslice mezi 0 a 9. Vstup je vyžadován.|\d|  
|9|Číslice nebo mezera. Položka je nepovinná.|[ \d]?|  
|#|Číslice nebo mezera. Položka je nepovinná. Pokud je tato pozice ponechána prázdná v masce, bude vykreslena jako mezera. Plus (+) a minus (-) značky jsou povoleny.|[ \d+-]?|  
|L|Dopis ASCII. Vstup je vyžadován.|[a-zA-Z]|  
|?|Dopis ASCII. Položka je nepovinná.|[a-zA-Z]?|  
|&|Znak. Vstup je vyžadován.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]|  
|C|Znak. Položka je nepovinná.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]?|  
|A|Alfanumerické. Položka je nepovinná.|\W|  
|.|Desítkový zástupný symbol odpovídající jazykové verzi.|Není k dispozici.|  
|,|Zástupný symbol tisíců vhodných pro jazykovou verzi.|Není k dispozici.|  
|:|Oddělovač času odpovídající jazykové verzi.|Není k dispozici.|  
|/|Oddělovač data odpovídající jazykové verzi.|Není k dispozici.|  
|$|Symbol měny odpovídající jazykové verzi.|Není k dispozici.|  
|\<|Převede všechny znaky, které následují, na malá písmena.|Není k dispozici.|  
|>|Převede všechny znaky, které následují, na velká písmena.|Není k dispozici.|  
|&#124;|Odpočiňte předchozí posun nahoru nebo posun dolů.|Není k dispozici.|  
|&#92;|Unikne znak masky a změní ji na doslovný. "\\\\" je úniková sekvence pro zpětné lomítko.|&#92;|  
|Všechny ostatní postavy.|Literály. Všechny prvky, které nejsou <xref:System.Windows.Forms.MaskedTextBox>maskou, se zobrazí jako oni sami v rámci .|Všechny ostatní postavy.|  
  
 Desetinné číslo (.), tisíciny (,), čas (:), datum (/) a symboly měny ($) jsou ve výchozím nastavení nastaveny tak, aby tyto symboly byly definovány jazykovou verzí aplikace. Můžete je vynutit zobrazení symbolů <xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A> pro jinou jazykovou verzi pomocí vlastnosti.  
  
## <a name="regular-expressions-and-masks"></a>Regulární výrazy a masky  
 Přestože regulární výrazy a masky můžete použít k ověření vstupu uživatele, nejsou zcela ekvivalentní. Regulární výrazy mohou vyjadřovat složitější vzory než masky, ale masky mohou vyjadřovat stejné informace stručněji a v kulturně relevantním formátu.  
  
 Následující tabulka porovnává čtyři regulární výrazy a ekvivalentní masku pro každý z nich.  
  
|Regulární výraz|Maska|Poznámky|  
|------------------------|----------|-----------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|Znak `/` v masce je logický oddělovač kalendářních dat a zobrazí se uživateli jako oddělovač data odpovídající aktuální jazykové verzi aplikace.|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|Datum (den, zkratka měsíce a rok) ve formátu Usa, ve kterém je zobrazena třípísmenná zkratka měsíce s počátečním velkým písmenem následovaným dvěma velkými písmeny.|  
|`(\(\d{3}\)-)?\d{3}-d{4}`|`(999)-000-0000`|Spojené státy telefonní číslo, směrové číslo oblasti volitelné. Pokud uživatel nechce zadávat volitelné znaky, může buď zadat mezery nebo umístit ukazatel myši přímo na pozici v masce reprezentované první 0.|  
|`$\d{6}.00`|`$999,999.00`|Hodnota měny v rozsahu 0 až 999999. Měna, tisícina a desetinné znaky budou nahrazeny za běhu jejich ekvivalenty specifické pro jazykovou verzi.|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>
- <xref:System.Windows.Forms.MaskedTextBox>
- [Ověřování řetězců v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
- [MaskedTextBox – ovládací prvek](../../../../framework/winforms/controls/maskedtextbox-control-windows-forms.md)
