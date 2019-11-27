---
title: Rozdíly mezi vlastnostmi a proměnnými
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
ms.openlocfilehash: bbed3248840803d36607a67c8373fed15c07445f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341211"
---
# <a name="differences-between-properties-and-variables-in-visual-basic"></a>Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic
Proměnné a vlastnosti obojí představuje hodnoty, ke kterým máte přístup. Existují však rozdíly v ukládání a implementaci.  
  
## <a name="variables"></a>Proměnné  
 *Proměnná* odpovídá přímo umístění v paměti. Můžete definovat proměnnou s jediným příkazem deklarace. Proměnná může být *lokální proměnná*, definovaná v proceduře a dostupná pouze v rámci tohoto postupu, nebo může být *členskou proměnnou*, definovaná v modulu, třídě nebo struktuře, ale není uvnitř žádné procedury. Členská proměnná se označuje také jako *pole*.  
  
## <a name="properties"></a>Vlastnosti  
 *Vlastnost* je datový element definovaný v modulu, třídě nebo struktuře. Definujete vlastnost s blokem kódu mezi příkazy `Property` a `End Property`. Blok kódu obsahuje proceduru `Get`, `Set` postup nebo obojí. Tyto postupy se nazývají *procedury vlastností* nebo *přistupující objekty vlastnosti*. Kromě načítání nebo ukládání hodnoty vlastnosti mohou také provádět vlastní akce, jako je například aktualizace čítače přístupu.  
  
## <a name="differences"></a>Rozdíly  
 V následující tabulce jsou uvedeny některé důležité rozdíly mezi proměnnými a vlastnostmi.  
  
|Bod rozdílu|Proměnná|Vlastnost|  
|-------------------------|--------------|--------------|  
|Deklarace|Příkaz s jednou deklarací|Řada příkazů v bloku kódu|  
|Implementace|Umístění jednoho úložiště|Spustitelný kód (procedury vlastností)|  
|Úložiště|Přímo spojené s hodnotou proměnné|Obvykle je interní úložiště nedostupné mimo třídu nebo modul obsahující vlastnost.<br /><br /> Hodnota vlastnosti může nebo nemusí existovat jako uložený element <sup>1</sup> .|  
|Spustitelný kód|Žádné|Musí mít aspoň jeden postup.|  
|Přístup pro čtení a zápis|Čtení/zápis nebo jen pro čtení|Čtení/zápis, jen pro čtení nebo jen pro zápis|  
|Vlastní akce (kromě přijetí nebo vrácení hodnoty)|Není možné|Dá se provést jako součást nastavení nebo načítání hodnoty vlastnosti.|  
  
 <sup>1</sup> na rozdíl od proměnné nemusí hodnota vlastnosti odpovídat přímo na jednu položku úložiště. Úložiště může být rozdělené do částí pro pohodlí a zabezpečení nebo hodnota může být uložena v zašifrované podobě. V těchto případech `Get` procedura sestaví nebo dešifruje uloženou hodnotu a procedura `Set` by zašifroval novou hodnotu nebo rozdělila ji do úložiště prvků. Hodnota vlastnosti může být v dočasném režimu, jako je například denní čas. v takovém případě by `Get` procedura tuto vlastnost při každém přístupu k vlastnosti počítala průběžně.  
  
## <a name="see-also"></a>Viz také:

- [Procedury vlastnosti](./property-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Příkaz Property](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Příkaz Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Postupy: Vytvoření vlastnosti](./how-to-create-a-property.md)
- [Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Postupy: Volání procedury vlastnosti](./how-to-call-a-property-procedure.md)
- [Postupy: deklarace a volání výchozí vlastnosti v Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Postupy: Vložení hodnoty do vlastnosti](./how-to-put-a-value-in-a-property.md)
- [Postupy: Získání hodnoty z vlastnosti](./how-to-get-a-value-from-a-property.md)
