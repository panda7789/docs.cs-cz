---
title: Základní informace o řetězcích
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
ms.openlocfilehash: 935926b8b83afa47c20ea68aecd6bc8c40bd0234
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363692"
---
# <a name="string-basics-in-visual-basic"></a>Základní informace o řetězcích v jazyce Visual Basic
`String`Datový typ představuje řadu znaků (každý, který představuje převeďte instanci `Char` datového typu). V tomto tématu se seznámíte se základními koncepty řetězců v Visual Basic.  
  
## <a name="string-variables"></a>Řetězcové proměnné  
 Instanci řetězce lze přiřadit literální hodnotu, která představuje řadu znaků. Příklad:  
  
 [!code-vb[VbVbalrStrings#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#63)]  
  
 `String`Proměnná může také přijmout libovolný výraz, který se vyhodnotí jako řetězec. Příklady:  
  
 [!code-vb[VbVbalrStrings#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#64)]  
  
 Jakýkoli literál, který je přiřazen `String` proměnné, musí být uzavřen v uvozovkách (""). To znamená, že znak citace v rámci řetězce nemůže být reprezentován uvozovkami. Například následující kód způsobí chybu kompilátoru:  
  
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
 Řetězec lze představit jako řadu `Char` hodnot a `String` Typ obsahuje integrované funkce, které umožňují provádět mnoho manipulací na řetězci, který se podobá manipulaci povolených poli. Podobně jako u všech polí v .NET Framework jsou pole založená na nule. Můžete odkazovat na konkrétní znak v řetězci prostřednictvím `Chars` vlastnosti, která poskytuje způsob, jak získat přístup k znaku podle pozice, ve které se zobrazí v řetězci. Příklad:  
  
 [!code-vb[VbVbalrStrings#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#67)]  
  
 Ve výše uvedeném příkladu `Chars` vrátí vlastnost řetězce čtvrtý znak v řetězci, který je `D` a přiřadí k `myChar` . Můžete také získat délku konkrétního řetězce prostřednictvím `Length` Vlastnosti. Pokud potřebujete provést více manipulací typu pole na řetězec, můžete ho převést na pole `Char` instancí pomocí `ToCharArray` funkce řetězce. Příklad:  
  
 [!code-vb[VbVbalrStrings#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#68)]  
  
 Proměnná `myArray` nyní obsahuje pole `Char` hodnot, z nichž každý představuje znak z `myString` .  
  
## <a name="the-immutability-of-strings"></a>Neměnnosti řetězců  
 Řetězec je *neměnný*, což znamená, že jeho hodnotu nelze po vytvoření změnit. To však nebrání přiřazení více než jedné hodnoty k proměnné řetězce. Uvažujte následující příklad:  
  
 [!code-vb[VbVbalrStrings#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#69)]  
  
 Zde je vytvořena řetězcová proměnná s ohledem na hodnotu a její hodnota se změní.  
  
 Konkrétně v prvním řádku `String` je vytvořena instance typu a přiřazena hodnota `This string is immutable` . V druhém řádku příkladu je vytvořena nová instance a hodnota `Or is it?` a proměnná řetězce zahodí svůj odkaz na první instanci a ukládá odkaz na novou instanci.  
  
 Na rozdíl od jiných vnitřních datových typů `String` je odkazový typ. Pokud je proměnná typu odkazu předána jako argument funkci nebo podprogramu, odkaz na adresu paměti, kde jsou uložena data, se předává místo skutečné hodnoty řetězce. Takže v předchozím příkladu název proměnné zůstane stejný, ale odkazuje na novou a jinou instanci `String` třídy, která obsahuje novou hodnotu.  
  
## <a name="see-also"></a>Viz také

- [Představení řetězců v jazyce Visual Basic](introduction-to-strings.md)
- [Datový typ String](../../../language-reference/data-types/string-data-type.md)
- [Char – datový typ](../../../language-reference/data-types/char-data-type.md)
- [Základní operace s řetězci](../../../../standard/base-types/basic-string-operations.md)
