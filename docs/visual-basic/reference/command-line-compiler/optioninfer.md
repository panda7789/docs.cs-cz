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
ms.openlocfilehash: f1dcc03a67880727893e55c13d65a804586b3f56
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59315501"
---
# <a name="-optioninfer"></a>-optioninfer
Umožňuje použití odvození místního typu v deklaraci proměnných.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`+` &#124; `-`|Volitelné. Zadejte `-optioninfer+` umožňující odvození místního typu, nebo `-optioninfer-` ho blokovala. `-optioninfer` Parametrem žádná hodnota zadána, je stejný jako `-optioninfer+`. Výchozí hodnotu v případě `-optioninfer` přepínač není k dispozici je také `-optioninfer+`. Výchozí hodnota je nastavena v souboru odpovědí Vbc.rsp.|  
  
> [!NOTE]
>  Můžete použít `-noconfig` – možnost kompilátoru interní výchozí hodnoty namísto platformám zadaným v vbc.rsp zachovat. Výchozí nastavení kompilátoru pro tuto možnost je `-optioninfer-`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud soubor zdrojového kódu obsahuje [Option Infer – příkaz](../../../visual-basic/language-reference/statements/option-infer-statement.md), přepíše příkaz `-optioninfer` nastavení příkazového řádku kompilátoru.  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a>Chcete-li nastavit - optioninfer v integrovaném vývojovém prostředí sady Visual Studio  
  
1. Vyberte projekt v **Průzkumníka řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
2. Na **kompilaci** kartu, upravte hodnotu v **Option infer** pole.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `test.vb` s odvození místního typu povolené.  
  
```console
vbc -optioninfer+ test.vb  
```  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)
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
