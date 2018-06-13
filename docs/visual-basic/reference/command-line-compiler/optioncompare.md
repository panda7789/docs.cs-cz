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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1906710ef10634187782f9355146dfa7ccb7748
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653400"
---
# <a name="-optioncompare"></a>-optioncompare
Určuje, jak jsou vytvářeny porovnání řetězců.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a>Poznámky  
 Můžete zadat `-optioncompare` v jednom ze dvou formách: `-optioncompare:binary` použít binární porovnání řetězců, a `-optioncompare:text` použít porovnávání řetězců textu. Ve výchozím nastavení, kompilátor použije `-optioncompare:binary`.  
  
 V systému Windows aktuální znaková stránka Určuje binární řazení. Typické binární řazení vypadá takto:  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 Porovnání řetězců založený na textu jsou založené na pořadí řazení velká a malá písmena text určen podle národního prostředí vašeho systému. Pořadí řazení typické text vypadá takto:  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a>Chcete-li nastavit - optioncompare v integrovaném vývojovém prostředí sady Visual Studio  
  
1.  Máte projekt vybraný v **Průzkumníku řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.   
  
2.  Klikněte **zkompilovat** kartě.  
  
3.  Změňte hodnotu v **možnost porovnat** pole.  
  
### <a name="to-set--optioncompare-programmatically"></a>Chcete-li nastavit - optioncompare prostřednictvím kódu programu  
  
-   V tématu [Option Compare – příkaz](../../../visual-basic/language-reference/statements/option-compare-statement.md).  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `ProjFile.vb` a používá porovnání binárního řetězce.  
  
```console
vbc -optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Příkaz Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [Dialogové okno Možnosti výchozí hodnoty, projekty, Visual Basic](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
