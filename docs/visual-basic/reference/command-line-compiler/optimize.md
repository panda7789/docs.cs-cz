---
title: /optimize
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e157fb0e1fcdb3899440eed02a42b16f75541989
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="optimize"></a>/optimize
Povolí nebo zakáže optimalizace kompilátoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/optimize[ + | - ]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`+` &#124; `-`|Volitelné. `/optimize-` Možnost zakáže optimalizace kompilátoru. `/optimize+` Možnost umožňuje optimalizace. Ve výchozím nastavení jsou zakázány optimalizace.|  
  
## <a name="remarks"></a>Poznámky  
 Optimalizace kompilátoru byl výstupní soubor menší, rychlejší a efektivnější. Nicméně, protože optimalizace mít za následek změny uspořádání kódu ve výstupním souboru `/optimize+` mohou ztížit ladění.  
  
 Všechny moduly, které vygeneroval s `/target:module` pro sestavení musíte použít stejné `/optimize` nastavení jako sestavení. Další informace najdete v tématu [/Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).  
  
 Můžete kombinovat `/optimize` a `/debug` možnosti.  
  
|Chcete-li nastavit / optimize v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1.  Máte projekt vybraný v **Průzkumníku řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.<br />     <br />2.  Klikněte **zkompilovat** kartě.<br />3.  Klikněte **Upřesnit** tlačítko.<br />4.  Změnit **povolit optimalizace** zaškrtávací políčko.|  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` a umožňuje optimalizace kompilátoru.  
  
```  
vbc t2.vb /optimize  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ Debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [/ target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
