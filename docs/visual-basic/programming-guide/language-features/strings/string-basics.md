---
title: Základní informace o řetězcích
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
ms.openlocfilehash: 7141966e3c8a8cbce42111c56a85a00709e8fe1a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344281"
---
# <a name="string-basics-in-visual-basic"></a>Základní informace o řetězcích v jazyce Visual Basic
Datový typ `String` představuje řadu znaků (každý, který představuje v instanci datového typu `Char`). V tomto tématu se seznámíte se základními koncepty řetězců v Visual Basic.  
  
## <a name="string-variables"></a>Řetězcové proměnné  
 Instanci řetězce lze přiřadit literální hodnotu, která představuje řadu znaků. Příklad:  
  
 [!code-vb[VbVbalrStrings#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#63)]  
  
 `String` proměnná může také přijmout libovolný výraz, který se vyhodnotí jako řetězec. Příklady:  
  
 [!code-vb[VbVbalrStrings#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#64)]  
  
 Jakýkoli literál, který je přiřazen proměnné `String`, musí být uzavřen v uvozovkách (""). To znamená, že znak citace v rámci řetězce nemůže být reprezentován uvozovkami. Například následující kód způsobí chybu kompilátoru:  
  
 [!code-vb[VbVbalrStrings#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#65)]  
  
 Tento kód způsobí chybu, protože kompilátor ukončí řetězec za druhou uvozovku a zbytek řetězce je interpretován jako kód. Chcete-li tento problém vyřešit, Visual Basic interpretuje v řetězci v řetězcové literály dvě uvozovky jako jeden znak uvozovky. Následující příklad ukazuje správný způsob, jak zahrnout uvozovky do řetězce:  
  
 [!code-vb[VbVbalrStrings#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#66)]  
  
 V předchozím příkladu se dvě uvozovky před slovem `Look` v řetězci staly jedním znakem uvozovek. Tři uvozovky na konci řádku zastupují jednu uvozovku v řetězci a znak ukončení řetězce.  
  
 Řetězcové literály mohou obsahovat více řádků:  
  
```vb  
Dim x = "hello  
world"  
```  
  
 Výsledný řetězec obsahuje sekvence nového řádku, které jste použili v řetězcovém literálu (vbCr, vbCrLf atd.).  Už nemusíte používat staré alternativní řešení:  
  
```vb  
Dim x = <xml><![CDATA[Hello  
World]]></xml>.Value  
```  
  
## <a name="characters-in-strings"></a>Znaky v řetězcích  
 Řetězec lze představit jako řadu `Char` hodnot a typ `String` obsahuje integrované funkce, které umožňují provádět mnoho manipulací na řetězci, který se podobá manipulaci povolených poli. Podobně jako u všech polí v .NET Framework jsou pole založená na nule. Můžete odkazovat na konkrétní znak v řetězci prostřednictvím vlastnosti `Chars`, která poskytuje způsob, jak získat přístup k znaku podle pozice, ve které se zobrazí v řetězci. Příklad:  
  
 [!code-vb[VbVbalrStrings#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#67)]  
  
 V předchozím příkladu vlastnost `Chars` řetězce vrátí čtvrtý znak v řetězci, který je `D`a přiřadí jej `myChar`. Můžete také získat délku určitého řetězce prostřednictvím vlastnosti `Length`. Pokud potřebujete provést více manipulací typu pole na řetězec, můžete ho převést na pole instancí `Char` pomocí funkce `ToCharArray` řetězce. Příklad:  
  
 [!code-vb[VbVbalrStrings#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#68)]  
  
 Proměnná `myArray` nyní obsahuje pole hodnot `Char`, z nichž každý představuje znak z `myString`.  
  
## <a name="the-immutability-of-strings"></a>Neměnnosti řetězců  
 Řetězec je *neměnný*, což znamená, že jeho hodnotu nelze po vytvoření změnit. To však nebrání přiřazení více než jedné hodnoty k proměnné řetězce. Vezměte v úvahu v následujícím příkladu:  
  
 [!code-vb[VbVbalrStrings#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#69)]  
  
 Zde je vytvořena řetězcová proměnná s ohledem na hodnotu a její hodnota se změní.  
  
 Konkrétně v prvním řádku je vytvořena instance typu `String` a je zadána hodnota `This string is immutable`. V druhém řádku příkladu je vytvořena nová instance a s hodnotou `Or is it?`a proměnná řetězce zahodí svůj odkaz na první instanci a ukládá odkaz na novou instanci.  
  
 Na rozdíl od jiných vnitřních datových typů je `String` odkazovým typem. Pokud je proměnná typu odkazu předána jako argument funkci nebo podprogramu, odkaz na adresu paměti, kde jsou uložena data, se předává místo skutečné hodnoty řetězce. Takže v předchozím příkladu název proměnné zůstane stejný, ale odkazuje na novou a jinou instanci třídy `String`, která obsahuje novou hodnotu.  
  
## <a name="see-also"></a>Viz také:

- [Seznámení s řetězci v Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [Datový typ String](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [Datový typ Char](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [Základní operace s řetězci](../../../../standard/base-types/basic-string-operations.md)
