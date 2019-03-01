---
title: Základní informace o řetězcích v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
ms.openlocfilehash: 7262fded93b02c011484919f0504bb7225d8d2af
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965982"
---
# <a name="string-basics-in-visual-basic"></a>Základní informace o řetězcích v jazyce Visual Basic
`String` Datový typ představuje posloupnost znaků (nichž každý představuje zase instance `Char` datový typ). Toto téma představuje základní koncepty řetězců v jazyce Visual Basic.  
  
## <a name="string-variables"></a>Proměnné typu řetězec  
 Instance řetězce je možné přiřadit hodnotu literálu, který představuje posloupnost znaků. Příklad:  
  
 [!code-vb[VbVbalrStrings#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#63)]  
  
 A `String` proměnnou můžete také přijmout libovolný výraz, který se vyhodnotí jako řetězec. Příklady:  
  
 [!code-vb[VbVbalrStrings#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#64)]  
  
 Žádné literál, který je přiřazen k `String` proměnná musí být uzavřen v uvozovkách (""). To znamená, že uvozovka v řetězci nemůže být reprezentována znak uvozovek. Například následující kód způsobí chybu kompilátoru:  
  
 [!code-vb[VbVbalrStrings#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#65)]  
  
 Tento kód způsobí chybu, protože kompilátor ukončí řetězec po druhé uvozovky a zbývající řetězec je interpretován jako kód. Pokud chcete tento problém vyřešit, Visual Basic interpretuje dvě uvozovek v řetězcovém literálu jako jeden znak uvozovek do řetězce. Následující příklad ukazuje správný způsob vložení uvozovek do řetězce:  
  
 [!code-vb[VbVbalrStrings#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#66)]  
  
 V předchozím příkladu dvě uvozovek předchozí slovo `Look` stát jeden uvozovka v řetězci. Tři uvozovky na konci řádku představují jeden znak uvozovek do řetězce a znak ukončení řetězce.  
  
 Řetězcové literály může obsahovat více řádků:  
  
```vb  
Dim x = "hello  
world"  
```  
  
 Výsledný řetězec obsahuje sekvence znaku nového řádku, které jste použili do řetězce literálu (vbcr, vbcrlf atd.).  Už nemusíte používat staré alternativní řešení:  
  
```vb  
Dim x = <xml><![CDATA[Hello  
World]]></xml>.Value  
```  
  
## <a name="characters-in-strings"></a>Znakům v řetězcích  
 Řetězec si lze představit jako řadu objektů `Char` hodnoty a `String` typ má integrované funkce, které můžete provádět mnoho manipulace na řetězec, které se podobají manipulaci s povolenou pole. Stejně jako všechna pole v [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], jde o pole od nuly. Mohou odkazovat na konkrétní znak v řetězci prostřednictvím `Chars` vlastnost, která umožňuje přístup ke znakům podle umístění, ve kterém se zobrazí v řetězci. Příklad:  
  
 [!code-vb[VbVbalrStrings#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#67)]  
  
 Ve výše uvedeném příkladu `Chars` vlastnost řetězce vrátí čtvrtou znak v řetězci, který je `D`a přiřadí ji k `myChar`. Můžete také získat délku znamének určitého řetězce prostřednictvím `Length` vlastnost. Pokud je potřeba manipulace s více typ pole na řetězec, můžete ji převést na pole `Char` instance pomocí `ToCharArray` funkce řetězec. Příklad:  
  
 [!code-vb[VbVbalrStrings#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#68)]  
  
 Proměnná `myArray` nyní obsahuje celou řadu `Char` hodnoty, každý představující znak z `myString`.  
  
## <a name="the-immutability-of-strings"></a>Neměnnost řetězce  
 Řetězec je *neměnné*, což znamená, že jeho hodnotu nelze změnit po vytvoření. Ale to není vám bránit v přiřazení více než jednu hodnotu k proměnné řetězce. Vezměte v úvahu v následujícím příkladu:  
  
 [!code-vb[VbVbalrStrings#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#69)]  
  
 Tady se vytvoří proměnnou s řetězcem, zadána hodnota, a pak se změní jeho hodnotu.  
  
 Přesněji řečeno v prvním řádku instanci typu `String` se vytvoří a předána hodnota `This string is immutable`. Na druhém řádku v příkladu se vytvoří a předána hodnota novou instanci `Or is it?`, a proměnné řetězce zahodí svůj odkaz na první instanci a uchovává odkaz na novou instanci.  
  
 Na rozdíl od jiných vnitřních datových typů `String` je typem odkazu. Když proměnné typu odkazu je předán jako argument funkce nebo podprogramu, je předána odkazem na adresu paměti, kde jsou data uložená namísto skutečné hodnoty řetězce. Takže v předchozím příkladu název proměnné zůstala stejná, ale odkazuje na jiný instanci `String` třídu, která obsahuje novou hodnotu.  
  
## <a name="see-also"></a>Viz také:
- [Úvod do řetězců v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [Datový typ String](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [Datový typ Char](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [Základní operace s řetězci](../../../../standard/base-types/basic-string-operations.md)
