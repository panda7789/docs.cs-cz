---
title: -optioncompare
ms.date: 07/20/2015
f1_keywords:
- /optioncompare
- -optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
ms.openlocfilehash: b88cba4d16c5a770a72b47868d11b16cbba6cae8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59340435"
---
# <a name="-optioncompare"></a>-optioncompare
Určuje způsob porovnávání řetězců.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a>Poznámky  
 Můžete zadat `-optioncompare` v jednom z těchto dvou tvarů: `-optioncompare:binary` použít porovnávání binárních řetězců a `-optioncompare:text` používat textové porovnávání řetězců. Ve výchozím nastavení, kterou kompilátor používá `-optioncompare:binary`.  
  
 V Microsoft Windows určuje aktuální znakové stránce binární řazení. Typické binární řazení vypadá takto:  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 Textový řetězec porovnání jsou založeny na pořadí řazení nerozlišujícího velikost písmen textu určuje podle národního prostředí vašeho systému. Typické textové řazení vypadá takto:  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a>Chcete-li nastavit - optioncompare v integrovaném vývojovém prostředí sady Visual Studio  
  
1. Mají projekt vybraný v **Průzkumníka řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.   
  
2. Klikněte na tlačítko **kompilaci** kartu.  
  
3. Upravte hodnotu v **Option Compare** pole.  
  
### <a name="to-set--optioncompare-programmatically"></a>Chcete-li nastavit - optioncompare prostřednictvím kódu programu  
  
-   Zobrazit [Option Compare – příkaz](../../../visual-basic/language-reference/statements/option-compare-statement.md).  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `ProjFile.vb` a používá binární porovnání řetězců.  
  
```console
vbc -optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Příkaz Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
