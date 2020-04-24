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
Způsobí, že kompilátor ohlásí chyby, pokud proměnné nejsou deklarovány dříve, než budou použity.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
 `+`&#124;`-`  
 Nepovinný parametr. Určete `-optionexplicit+` , aby vyžadoval explicitní deklaraci proměnných. `-optionexplicit+` Možnost je výchozí a je stejná jako `-optionexplicit`. `-optionexplicit-` Možnost umožňuje implicitní deklaraci proměnných.  
  
## <a name="remarks"></a>Poznámky  
 Pokud soubor zdrojového kódu obsahuje [příkaz Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md), příkaz přepíše nastavení kompilátoru `-optionexplicit` příkazového řádku.  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a>Nastavení-OptionExplicit – v integrovaném vývojovém prostředí sady Visual Studio  
  
1. Máte projekt vybraný v **Průzkumník řešení**. V nabídce **projekt** klikněte na příkaz **vlastnosti**.
  
2. Klikněte na kartu **kompilovat** .  
  
3. Upravte hodnotu v poli **explicitní možnosti** .  
  
## <a name="example"></a>Příklad  
 Následující kód kompiluje při `-optionexplicit-` použití.  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [– OptionCompare –](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [– OptionStrict –](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [– optioninfer –](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Příkaz Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
