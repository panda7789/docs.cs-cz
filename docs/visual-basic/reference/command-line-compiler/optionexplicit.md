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
ms.openlocfilehash: 072a816f189a772543fbbd63e7202441469c0177
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="-optionexplicit"></a>-optionexplicit
Pokud nejsou proměnné deklarovány před použitím způsobí, že kompilátor zprávy o chybách.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Volitelné. Zadejte `-optionexplicit+` tak, aby vyžadovala explicitní deklarace proměnné. `-optionexplicit+` Možnost je výchozí a je stejná jako `-optionexplicit`. `-optionexplicit-` Možnost umožňuje implicitní deklarace proměnných.  
  
## <a name="remarks"></a>Poznámky  
 Pokud obsahuje souboru se zdrojovým kódem [příkazu Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md), přepíše příkaz `-optionexplicit` nastavení kompilátoru příkazového řádku.  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a>Chcete-li nastavit - optionexplicit v integrovaném vývojovém prostředí sady Visual Studio  
  
1.  Máte projekt vybraný v **Průzkumníku řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.   
  
2.  Klikněte **zkompilovat** kartě.  
  
3.  Změňte hodnotu v **Option Explicit** pole.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje při `-optionexplicit-` se používá.  
  
 [!code-vb[VbVbalrCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/optionexplicit_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Příkaz Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [Dialogové okno Možnosti výchozí hodnoty, projekty, Visual Basic](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
