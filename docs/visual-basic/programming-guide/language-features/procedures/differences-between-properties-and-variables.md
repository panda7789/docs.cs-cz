---
title: "Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cb30972e2b49a7005749f57c0223b9fa493cde52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-properties-and-variables-in-visual-basic"></a>Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic
Proměnné a vlastnosti představují hodnoty, kterým můžete přistupovat. Existují však rozdíly v úložišti a implementace.  
  
## <a name="variables"></a>Proměnné  
 A *proměnná* odpovídá přímo do umístění v paměti. Definujete proměnnou s příkazem jediné deklaraci. Může být proměnné *místní proměnné*, definované uvnitř procedury a k dispozici pouze v rámci tohoto postupu, nebo může být *členské proměnné*, definované v modulu, třídu nebo strukturu, ale ne do žádného postup. Členské proměnné se taky říká *pole*.  
  
## <a name="properties"></a>Vlastnosti  
 A *vlastnost* je element data, která je definovaná v modulu, třídu nebo strukturu. Definuje vlastnost s blok kódu mezi `Property` a `End Property` příkazy. Obsahuje blok kódu `Get` postupu `Set` postup nebo obojí. Tyto postupy se nazývají *procedury vlastností* nebo *přístupové objekty vlastnosti*. Kromě načítání nebo ukládání hodnotu vlastnosti, se můžete také provést vlastní akce, jako je aktualizace čítače k přístupu.  
  
## <a name="differences"></a>Rozdíly  
 V následující tabulce jsou uvedeny některé rozdíly mezi proměnné a vlastnosti.  
  
|Bod rozdílu|Proměnná|Vlastnost|  
|-------------------------|--------------|--------------|  
|Deklarace|Příkaz jediné deklaraci|Řadu příkazy v bloku kódu|  
|Implementace|Jedno umístění úložiště|Spustitelný kód (procedury vlastností)|  
|Úložiště|Přímo spojené s hodnota proměnné|Obvykle je interní úložiště není k dispozici mimo obsahující třídy nebo modulu vlastnosti<br /><br /> Hodnota vlastnosti může nebo nemusí existovat jako element uložené <sup>1</sup>|  
|Spustitelného kódu|Žádné|Musí mít alespoň jeden postup|  
|Oprávnění ke čtení a zápisu|Pro čtení a zápis nebo jen pro čtení|Pro čtení a zápis, jen pro čtení, nebo jen pro zápis|  
|Vlastní akce (kromě přijetí nebo vrací hodnotu)|Není možná.|Můžete provést v rámci nastavení nebo načtení hodnota vlastnosti|  
  
 <sup>1</sup> na rozdíl od proměnné, nemusí odpovídat hodnotě vlastnosti přímo na jednu položku úložiště. Úložiště může rozdělit na části pro usnadnění práce nebo zabezpečení, nebo hodnota může být uložena v šifrovaném formátu. V těchto případech `Get` postup by spojit nebo dešifrovat uložené hodnoty a `Set` procedura by šifrování novou hodnotu nebo jej rozdělte do základní úložiště. Hodnotu vlastnosti může být dočasné, jako je čas, den, v takovém případě `Get` postup by vypočítat ho za chodu při každém přístupu k vlastnosti.  
  
## <a name="see-also"></a>Viz také  
 [Procedury vlastností](./property-procedures.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Property – příkaz](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Postupy: vytvoření vlastnosti](./how-to-create-a-property.md)  
 [Postupy: deklarace vlastnosti se smíšenými úrovněmi přístupu](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [Postupy: volání procedury vlastnosti](./how-to-call-a-property-procedure.md)  
 [Postupy: deklarace a volání výchozí vlastnosti v jazyce Visual Basic](./how-to-declare-and-call-a-default-property.md)  
 [Postupy: vložení hodnoty do vlastnosti](./how-to-put-a-value-in-a-property.md)  
 [Postupy: získání hodnoty z vlastnosti](./how-to-get-a-value-from-a-property.md)
