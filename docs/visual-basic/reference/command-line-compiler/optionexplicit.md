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
ms.openlocfilehash: 37ccd14dae0ebba2535185f2646e312d9bb70390
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266726"
---
# <a name="-optionexplicit"></a>-optionexplicit
Způsobí, že kompilátor hlásit chyby, pokud proměnné nejsou deklarovány před jejich použitím.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
 `+`&#124;`-`  
 Nepovinný parametr. Určete, `-optionexplicit+` chcete-li vyžadovat explicitní deklaraci proměnných. Tato `-optionexplicit+` možnost je výchozí a `-optionexplicit`je stejná jako . Tato `-optionexplicit-` možnost umožňuje implicitní deklaraci proměnných.  
  
## <a name="remarks"></a>Poznámky  
 Pokud soubor zdrojového kódu obsahuje [příkaz Option](../../../visual-basic/language-reference/statements/option-explicit-statement.md)Explicit `-optionexplicit` , příkaz přepíše nastavení kompilátoru příkazového řádku.  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a>Nastavení -optionexplicit v ide sady Visual Studio  
  
1. V **Průzkumníku řešení**je vybrán projekt . V nabídce **Project** klepněte na **položku Vlastnosti**.
  
2. Klikněte na kartu **Kompilace.**  
  
3. Upravte hodnotu v poli **Explicitní možnost.**  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje při `-optionexplicit-` použití.  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a>Viz také

- [Kompilátor příkazového řádku jazyka Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [-optionstrict -optionstrict -optionstrict -option](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Příkaz Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
