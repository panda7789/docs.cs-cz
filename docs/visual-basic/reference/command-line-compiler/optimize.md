---
title: -Optimalizace
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7df1c873c166def9fde1bedc139470263e3e4437
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="-optimize"></a>-Optimalizace
Povolí nebo zakáže optimalizace kompilátoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`+` &#124; `-`|Volitelné. `-optimize-` Možnost zakáže optimalizace kompilátoru. `-optimize+` Možnost umožňuje optimalizace. Ve výchozím nastavení jsou zakázány optimalizace.|  
  
## <a name="remarks"></a>Poznámky  
 Optimalizace kompilátoru byl výstupní soubor menší, rychlejší a efektivnější. Nicméně, protože optimalizace mít za následek změny uspořádání kódu ve výstupním souboru `-optimize+` mohou ztížit ladění.  
  
 Všechny moduly, které vygeneroval s `-target:module` pro sestavení musíte použít stejné `-optimize` nastavení jako sestavení. Další informace najdete v tématu [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).  
  
 Můžete kombinovat `-optimize` a `-debug` možnosti.  
  
|Chcete-li nastavit - Optimalizujte v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1.  Máte projekt vybraný v **Průzkumníku řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.<br />     <br />2.  Klikněte **zkompilovat** kartě.<br />3.  Klikněte **Upřesnit** tlačítko.<br />4.  Změnit **povolit optimalizace** zaškrtávací políčko.|  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` a umožňuje optimalizace kompilátoru.  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
