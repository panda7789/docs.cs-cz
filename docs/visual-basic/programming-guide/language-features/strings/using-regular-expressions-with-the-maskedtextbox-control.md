---
title: Používání regulárních výrazů s ovládacím prvkem MaskedTextBox
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], regular expressions
- strings [Visual Basic], masked edit
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
ms.openlocfilehash: 12d500fa0ff4945dcf2d5009bdba6d337834707e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346265"
---
# <a name="using-regular-expressions-with-the-maskedtextbox-control-in-visual-basic"></a>Používání regulárních výrazů s ovládacím prvkem MaskedTextBox v jazyce Visual Basic
Tento příklad ukazuje, jak převést jednoduché regulární výrazy pro práci s ovládacím prvkem <xref:System.Windows.Forms.MaskedTextBox>.  
  
## <a name="description-of-the-masking-language"></a>Popis jazyka maskování  
 Standardní <xref:System.Windows.Forms.MaskedTextBox> jazyk maskování je založený na tom, který používá ovládací prvek `Masked Edit` v Visual Basic 6,0 a měl by být obeznámený s tím, že uživatelé migrují z této platformy.  
  
 Vlastnost <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> ovládacího prvku <xref:System.Windows.Forms.MaskedTextBox> určuje, jakou vstupní masku chcete použít. Maska musí být řetězec složený z jednoho nebo více prvků maskování z následující tabulky.  
  
|Maskování elementu|Popis|Element regulárního výrazu|  
|---------------------|-----------------|--------------------------------|  
|0|Jakákoli jedna číslice od 0 do 9. Vyžaduje se položka.|\d|  
|9|Číslice nebo mezera. Položka je volitelná.|[ \d]?|  
|#|Číslice nebo mezera. Položka je volitelná. Pokud je tato pozice ponechána v masce prázdná, bude vykreslena jako mezera. Znaménka plus (+) a minus (-) jsou povoleny.|[ \d+-]?|  
|L|Písmeno ASCII. Vyžaduje se položka.|[a-zA-Z]|  
|?|Písmeno ASCII. Položka je volitelná.|[a-zA-Z]?|  
|&|Optické. Vyžaduje se položka.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]|  
|C|Optické. Položka je volitelná.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]?|  
|A|Písmena. Položka je volitelná.|\W|  
|.|Culture – vhodný zástupný symbol.|Není k dispozici.|  
|,|Zástupný symbol pro tisíce odpovídající jazykové verzi.|Není k dispozici.|  
|:|Oddělovač času odpovídající jazykové verzi.|Není k dispozici.|  
|/|Oddělovač data odpovídající jazykové verzi.|Není k dispozici.|  
|$|Symbol měny odpovídající jazykové verzi.|Není k dispozici.|  
|\<|Převede všechny znaky, které následují malými písmeny.|Není k dispozici.|  
|>|Převede všechny znaky, které následují na velká písmena.|Není k dispozici.|  
|&#124;|Provede předchozí posun nahoru nebo dolů.|Není k dispozici.|  
|&#92;|Řídí znak masky a přepíná ho na literál. "\\\\" je řídicí sekvence zpětného lomítka.|&#92;|  
|Všechny ostatní znaky.|Literály. Všechny prvky, které nejsou maskou, se zobrazí jako v <xref:System.Windows.Forms.MaskedTextBox>.|Všechny ostatní znaky.|  
  
 Výchozí symboly Decimal (.), sekundy (,), Time (:), Date (/) a Currency ($) pro zobrazení symbolů definovaných jazykovou verzí aplikace. Můžete vynutit, aby jim zobrazovaly symboly pro jinou jazykovou verzi pomocí vlastnosti <xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A>.  
  
## <a name="regular-expressions-and-masks"></a>Regulární výrazy a masky  
 I když můžete použít regulární výrazy a masky k ověření vstupu uživatele, nejsou zcela ekvivalentní. Regulární výrazy mohou vyjádřit složitější vzory než masky, ale masky mohou vyjádřit stejné informace mnohem stručně a v kulturním relevantním formátu.  
  
 Následující tabulka porovnává čtyři regulární výrazy a ekvivalentní masky pro každý z nich.  
  
|Regulární výraz|Zrušit|Poznámky|  
|------------------------|----------|-----------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|`/` znak v masce je oddělovač logických dat, který se zobrazí uživateli jako oddělovač data odpovídající aktuální jazykové verzi aplikace.|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|Datum (den, měsíc, měsíc a rok) ve formátu USA, ve kterém se zobrazuje zkratka měsíčního měsíce s počátečním velkým písmenem následovaným dvěma malými písmeny.|  
|`(\(\d{3}\)-)?\d{3}-d{4}`|`(999)-000-0000`|USA telefonní číslo, kód oblasti je nepovinný. Pokud uživatel nechce zadat volitelné znaky, může buď zadat mezery, nebo umístit ukazatel myši přímo na pozici v masce reprezentované prvním 0.|  
|`$\d{6}.00`|`$999,999.00`|Hodnota měny v rozsahu od 0 do 999999. Znaky Currency, thousandth a Decimal budou nahrazeny za běhu s jejich ekvivalenty specifickými pro jazykovou verzi.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>
- <xref:System.Windows.Forms.MaskedTextBox>
- [Ověřování řetězců v Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
- [Ovládací prvek MaskedTextBox](../../../../framework/winforms/controls/maskedtextbox-control-windows-forms.md)
