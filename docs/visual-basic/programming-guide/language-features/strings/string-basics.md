---
title: Základní informace o řetězcích v jazyce Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4a40435b76b0eee4f4eca15d5ba1a31cc58698ab
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="string-basics-in-visual-basic"></a>Základní informace o řetězcích v jazyce Visual Basic
`String` Datový typ reprezentuje řadu znaků (každý představuje zase instanci `Char` datový typ). Toto téma představuje základní koncepty řetězců v jazyce Visual Basic.  
  
## <a name="string-variables"></a>Řetězec proměnné  
 Instance řetězce lze přiřadit hodnotu literálu, která představuje posloupnost znaků. Příklad:  
  
 [!code-vb[VbVbalrStrings#63](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_1.vb)]  
  
 A `String` proměnná může také přijmout všechny výraz, který se vyhodnotí na řetězec. Příklady:  
  
 [!code-vb[VbVbalrStrings#64](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_2.vb)]  
  
 Všechny literál, který je přiřazen `String` proměnná musí být uzavřena v uvozovkách (""). To znamená, že uvozovky v rámci řetězec nemůže být reprezentovaná uvozovky. Chyba kompilátoru způsobí například následující kód:  
  
 [!code-vb[VbVbalrStrings#65](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_3.vb)]  
  
 Tento kód způsobí chybu, protože kompilátor ukončí řetězec po druhé uvozovky a zbytek řetězce byl interpretován jako kód. Chcete-li tento problém vyřešit, Visual Basic interpretuje dva znaky uvozovek v řetězcový literál jako jeden znak uvozovek do řetězce. Následující příklad ukazuje správný způsob zahrnout znak uvozovek do řetězce:  
  
 [!code-vb[VbVbalrStrings#66](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_4.vb)]  
  
 V předchozím příkladu, dva znaky uvozovek předcházející slovo `Look` stane jeden znak uvozovek do řetězce. Tři uvozovky na konci řádku představují jeden znak uvozovek v řetězce a znak ukončení řetězec.  
  
 Textové literály může obsahovat více řádků:  
  
```vb  
Dim x = "hello  
world"  
```  
  
 Výsledný řetězec obsahuje nový řádek pořadí, které jste použili v vaší řetězcový literál (vbcr, vbcrlf atd.).  Už budete muset použít staré alternativní řešení:  
  
```vb  
Dim x = <xml><![CDATA[Hello  
World]]></xml>.Value  
```  
  
## <a name="characters-in-strings"></a>Znaků v řetězcích  
 Řetězec si lze představit jako řadu `Char` hodnoty a `String` typ má integrované funkce, které vám umožní provádět mnoho manipulace na řetězec podobné manipulaci s povolenou pole. Jako všechna pole v [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], jedná se o pole s nulovým základem. Můžete použít odkaz na konkrétní znak v řetězci prostřednictvím `Chars` vlastnost, která poskytuje přístup k znak podle umístění, ve kterých se vyskytuje v řetězci. Příklad:  
  
 [!code-vb[VbVbalrStrings#67](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_5.vb)]  
  
 V předchozím příkladu `Chars` vlastnost řetězce, který vrátí čtvrtou znak v řetězci, který je `D`a přiřadí ji k `myChar`. Můžete také získat délka určitý řetězec prostřednictvím `Length` vlastnost. Pokud je třeba provést několik manipulace typ pole na řetězec, můžete ji převést na pole `Char` instance pomocí `ToCharArray` funkce řetězec. Příklad:  
  
 [!code-vb[VbVbalrStrings#68](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_6.vb)]  
  
 Proměnná `myArray` nyní obsahuje pole `Char` hodnoty, každý představující znak z `myString`.  
  
## <a name="the-immutability-of-strings"></a>Neměnitelnosti řetězce  
 Řetězec je *neměnné*, což znamená, že jeho hodnotu nelze změnit po jeho vytvoření. Ale to není zabránit vám v přiřazení více než jednu hodnotu na proměnnou string. Podívejte se na následující příklad:  
  
 [!code-vb[VbVbalrStrings#69](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_7.vb)]  
  
 Zde proměnnou string se vytvoří, přiřadit hodnotu, a pak je jeho hodnota změněna.  
  
 Přesněji řečeno, v prvním řádku, instance typu `String` se vytvoří a zadány hodnota `This string is immutable`. Na druhém řádku v příkladu se vytvoří a zadány hodnota novou instanci `Or is it?`, a proměnnou řetězce zruší její odkaz na první instanci a ukládá odkaz na novou instanci.  
  
 Na rozdíl od jiných vnitřní datové typy `String` typem je odkaz. Když proměnné typu odkaz je předána jako argument funkce nebo podprogramu, odkaz na adresu paměti se uloží data předán namísto skutečné hodnoty řetězce. Proto v předchozím příkladu název proměnné zůstane stejný, ale odkazuje na nové a jinou instanci systému `String` třídy, která obsahuje novou hodnotu.  
  
## <a name="see-also"></a>Viz také  
 [Představení řetězců v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)  
 [Datový typ String](../../../../visual-basic/language-reference/data-types/string-data-type.md)  
 [Datový typ Char](../../../../visual-basic/language-reference/data-types/char-data-type.md)  
 [Základní operace s řetězci](../../../../standard/base-types/basic-string-operations.md)
