---
title: Používání regulárních výrazů s ovládacím prvkem MaskedTextBox v jazyce Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], regular expressions
- strings [Visual Basic], masked edit
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c72542c05123ef62a8f95afbe1bb19cb823d1f21
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="using-regular-expressions-with-the-maskedtextbox-control-in-visual-basic"></a>Používání regulárních výrazů s ovládacím prvkem MaskedTextBox v jazyce Visual Basic
Tento příklad ukazuje, jak převést jednoduché regulárních výrazů pro práci s <xref:System.Windows.Forms.MaskedTextBox> ovládacího prvku.  
  
## <a name="description-of-the-masking-language"></a>Popis jazyka maskování  
 Standardní <xref:System.Windows.Forms.MaskedTextBox> maskování jazyk podle používají `Masked Edit` řízení v jazyce Visual Basic 6.0 a měli seznámit uživatelům při migraci z této platformy.  
  
 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> Vlastnost <xref:System.Windows.Forms.MaskedTextBox> řízení Určuje, jaké vstupní maska používat. Maska musí být řetězec tvořený jeden nebo více elementů maskování v následující tabulce.  
  
|Element maskování|Popis|Element regulární výraz|  
|---------------------|-----------------|--------------------------------|  
|0|Jediná číslice mezi 0 a 9. Položka je povinná.|\d|  
|9|Číslice nebo mezera. Položka je nepovinná.|[\d]?|  
|#|Číslice nebo mezera. Položka je nepovinná. Pokud toto umístění je prázdné v masce, bude vykresleno jako prostor. Plus (+) a minus (-) jsou povoleny znaky.|[\d+-]?|  
|L|Písmeno ASCII. Položka je povinná.|[a-zA-Z]|  
|?|Písmeno ASCII. Položka je nepovinná.|[a-zA-Z]?|  
|&|Znak. Položka je povinná.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]|  
|C|Znak. Položka je nepovinná.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]?|  
|OBJEKT|Alfanumerické znaky. Položka je nepovinná.|\W|  
|.|Decimal zástupný příslušnou jazykovou verzi.|Není k dispozici.|  
|,|Zástupný symbol tisíc příslušnou jazykovou verzi.|Není k dispozici.|  
|:|Oddělovač času příslušnou jazykovou verzi.|Není k dispozici.|  
|/|Oddělovač data příslušnou jazykovou verzi.|Není k dispozici.|  
|$|Symbolu měny příslušnou jazykovou verzi.|Není k dispozici.|  
|\<|Převede všechny znaky, které následují na malá písmena.|Není k dispozici.|  
|>|Převede všechny znaky, které následují na velká písmena.|Není k dispozici.|  
|&#124;|Vrátí zpět předchozí posunutí nahoru nebo posunutí.|Není k dispozici.|  
|\|Řídicí sekvence maska znak, zakažte ho do literál. "\\\\" je řídicí sekvence pro zpětné lomítko.|\|  
|Všechny ostatní znaky.|Literály. Všechny elementy bez maska se zobrazí jako sami v rámci <xref:System.Windows.Forms.MaskedTextBox>.|Všechny ostatní znaky.|  
  
 Decimal (.), tisícin (,), čas (:), datum (/) a výchozí symboly měny ($) k zobrazení těchto symbolů podle definice jazykovou verzi aplikace. Můžete vynutit, aby zobrazení symbolů pro jinou jazykovou verzi pomocí <xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A> vlastnost.  
  
## <a name="regular-expressions-and-masks"></a>Regulární výrazy a masek  
 Přestože regulární výrazy a masek je možné použít k ověření vstupu uživatele, nejsou úplně ekvivalentní. Regulární výrazy můžete express vzory složitější než masek, ale masek můžete express stejné informace, více stručně a ve formátu jazykově relevantní.  
  
 Následující tabulka porovnává čtyři regulární výrazy a ekvivalentní maska pro každou.  
  
|Regulární výraz|Maska|Poznámky|  
|------------------------|----------|-----------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|`/` Znak v maska je oddělovač logické data a uživateli se objeví jako oddělovač data, která je vhodné pro aktuální jazykovou verzi aplikace.|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|Datum (den, zkratka měsíc a rok) ve Spojených státech amerických formát, ve kterém se zobrazí zkratka měsíc tří písmen s počáteční velké písmeno, za nímž následuje dvě malá písmena.|  
|`(\(\d{3}\)-)?\d{3}-d{4}`|`(999)-000-0000`|Telefonní číslo pro USA, směrové číslo oblasti volitelné. Pokud uživatel nechce zadejte volitelné znaků, se můžete zadat mezery nebo umístěte ukazatel myši přímo na pozici v masce reprezentována první 0.|  
|`$\d{6}.00`|`$999,999.00`|Hodnotu měny v rozsahu od 0 do 999999. Měna, / 1 000 a decimal znaky se nahradí za běhu jejich ekvivalenty specifické pro jazykovou verzi.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>  
 <xref:System.Windows.Forms.MaskedTextBox>  
 [Ověřování řetězců v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)  
 [Ovládací prvek MaskedTextBox](../../../../framework/winforms/controls/maskedtextbox-control-windows-forms.md)
