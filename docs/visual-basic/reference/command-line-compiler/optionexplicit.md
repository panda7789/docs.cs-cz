---
title: -optionexplicit
ms.date: 07/20/2015
f1_keywords:
- /optionexplicit
- -optionexplicit
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
ms.openlocfilehash: 1de1b3a816739fc5f8ba1d1251b673c0b708d106
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969489"
---
# <a name="-optionexplicit"></a>-optionexplicit
Pokud proměnné nejsou deklarovány před jejich použití způsobí, že kompilátor pro hlášení chyb.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Volitelné. Zadejte `-optionexplicit+` tak, aby vyžadovala explicitní deklaraci proměnných. `-optionexplicit+` Možnost je výchozí a je stejný jako `-optionexplicit`. `-optionexplicit-` Možnost umožňuje implicitní deklaraci proměnných.  
  
## <a name="remarks"></a>Poznámky  
 Pokud soubor zdrojového kódu obsahuje [Option Explicit – příkaz](../../../visual-basic/language-reference/statements/option-explicit-statement.md), přepíše příkaz `-optionexplicit` nastavení příkazového řádku kompilátoru.  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a>Chcete-li nastavit - optionexplicit v integrovaném vývojovém prostředí sady Visual Studio  
  
1.  Mají projekt vybraný v **Průzkumníka řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.   
  
2.  Klikněte na tlačítko **kompilaci** kartu.  
  
3.  Upravte hodnotu v **Option Explicit** pole.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje, kdy `-optionexplicit-` se používá.  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a>Viz také:
- [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Příkaz Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
