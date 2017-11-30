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
ms.openlocfilehash: dead17435cd147bdcdf91bdc5b8e0aa651e9e9fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
|1.  Máte projekt vybraný v **Průzkumníku řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.<br />     Další informace najdete v tématu [Úvod do Návrhář projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Klikněte **zkompilovat** kartě.<br />3.  Klikněte **Upřesnit** tlačítko.<br />4.  Změnit **povolit optimalizace** zaškrtávací políčko.|  
  
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
