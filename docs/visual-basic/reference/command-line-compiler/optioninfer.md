---
title: -optioninfer
ms.date: 07/20/2015
f1_keywords:
- -optioninfer
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
ms.openlocfilehash: c6fc7e9dcfbce938ad75b0f357c2bfa9cd10703a
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005321"
---
# <a name="-optioninfer"></a>-optioninfer
Povoluje použití odvození místního typu v deklaracích proměnných.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`+` &#124; `-`|Volitelné. Chcete-li povolit odvození místního typu, zadejte hodnotu `-optioninfer+`, nebo `-optioninfer-` pro jeho blokování. Možnost `-optioninfer` bez zadané hodnoty je stejná jako `-optioninfer+`. Výchozí hodnota, pokud není k dispozici přepínač `-optioninfer`, je také `-optioninfer+`. Výchozí hodnota je nastavena v souboru odpovědí Vbc. rsp.|  
  
> [!NOTE]
> Pomocí možnosti `-noconfig` můžete zachovat interní výchozí hodnoty kompilátoru místo těch, které jsou zadány v Vbc. rsp. Výchozí hodnota kompilátoru pro tuto možnost je `-optioninfer-`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud soubor zdrojového kódu obsahuje [příkaz Option](../../../visual-basic/language-reference/statements/option-infer-statement.md), přepíše příkaz nastavení kompilátoru příkazového řádku `-optioninfer`.  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a>Nastavení-optioninfer – v integrovaném vývojovém prostředí sady Visual Studio  
  
1. Vyberte projekt v **Průzkumník řešení**. V nabídce **projekt** klikněte na příkaz **vlastnosti**.  
  
2. Na kartě **kompilovat** upravte hodnotu v poli **možnost odvodit** .  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `test.vb` s povoleným odvozením místního typu.  
  
```console
vbc -optioninfer+ test.vb  
```  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Příkaz Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [Odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [Stránka Kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [Sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)
