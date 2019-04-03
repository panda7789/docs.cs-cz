---
title: Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- variables [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- variables [Visual Basic], definition
- Visual Basic code, variables
- Visual Basic code, properties
- properties [Visual Basic], values
- properties [Visual Basic], defined
- variables [Visual Basic], and properties
- properties [Visual Basic], and variables
ms.assetid: 7a03a8be-5381-431f-bd7c-16e887e4e07b
ms.openlocfilehash: de4800e23519c2cc1c8b2b219287b9fa018b9bbf
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842899"
---
# <a name="differences-between-properties-and-variables-in-visual-basic"></a>Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic
Proměnné a vlastnosti představují hodnoty, které můžete přistupovat. Nicméně existují rozdíly v úložišti a implementaci.  
  
## <a name="variables"></a>Proměnné  
 A *proměnnou* odpovídá na umístění v paměti. Definujte proměnnou s příkazem jedné deklarace. Proměnná může být *lokální proměnná*, definované uvnitř procedury a k dispozici pouze v rámci tohoto postupu, nebo může být *členskou proměnnou*, definované v modulu, třídy nebo struktury, ale ne uvnitř žádné postup. Členské proměnné se také nazývá *pole*.  
  
## <a name="properties"></a>Vlastnosti  
 A *vlastnost* je datový prvek definovaný v modulu, třídy nebo struktury. Definovat vlastnost s bloku kódu mezi `Property` a `End Property` příkazy. Obsahuje blok kódu `Get` postupu `Set` procedury nebo obojí. Tyto postupy jsou volány *procedury vlastnosti* nebo *přistupující objekty vlastnosti*. Kromě načítání nebo ukládání hodnotu vlastnosti, se můžete také provádět vlastní akce, jako je aktualizace čítače k přístupu.  
  
## <a name="differences"></a>Rozdíly  
 V následující tabulce jsou uvedeny některé rozdíly mezi proměnných a vlastností.  
  
|Bod rozdíl|Proměnná|Vlastnost|  
|-------------------------|--------------|--------------|  
|Deklarace|Příkaz jediné deklaraci|Řadu příkazů v bloku kódu|  
|Implementace|Jedno umístění úložiště|Spustitelný kód (procedury vlastnosti)|  
|Úložiště|Přímo přidružené k hodnotě proměnné|Obvykle má interní úložiště není k dispozici mimo vlastnosti obsahující třídu nebo modul<br /><br /> Hodnota vlastnosti může nebo nemusí existovat jako prvek uložené <sup>1</sup>|  
|Spustitelný kód|Žádné|Musí mít alespoň jeden postup|  
|Oprávnění ke čtení a zápis|Čtení a zápis nebo jen pro čtení|Čtení a zápis, jen pro čtení nebo jen pro zápis|  
|Vlastní akce (navíc k přijetí nebo vrácení hodnoty)|Není možná.|Můžete provést v rámci nastavení nebo načtení hodnoty vlastnosti|  
  
 <sup>1</sup> na rozdíl od proměnné, nemusí odpovídat hodnotu vlastnosti přímo na jednu položku z úložiště. Úložiště může rozdělit na části pro usnadnění práce nebo zabezpečení, nebo hodnota může být uložena v šifrovaném tvaru. V těchto případech `Get` procedury by spojit nebo dešifrovat uložené hodnoty a `Set` procedury by šifrování novou hodnotu nebo ho rozdělte do základní úložiště. Hodnota vlastnosti může být dočasné, jako je čas, v takovém případě `Get` postup by vypočítat průběžně pokaždé, když je přístup k vlastnosti.  
  
## <a name="see-also"></a>Viz také:

- [Procedury vlastnosti](./property-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Příkaz Property](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Příkaz Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Postupy: Vytvoření vlastnosti](./how-to-create-a-property.md)
- [Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Postupy: Volání procedury vlastnosti](./how-to-call-a-property-procedure.md)
- [Postupy: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Postupy: Vložení hodnoty do vlastnosti](./how-to-put-a-value-in-a-property.md)
- [Postupy: Získání hodnoty z vlastnosti](./how-to-get-a-value-from-a-property.md)
