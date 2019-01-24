---
title: – Optimalizace
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: ddb12eb473ce53e60835acb8f1076655f78fafd1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574375"
---
# <a name="-optimize"></a>– Optimalizace
Povolí nebo zakáže optimalizace kompilátoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`+` &#124; `-`|Volitelné. `-optimize-` Možnost zakáže optimalizace kompilátoru. `-optimize+` Možnost povolí optimalizace. Ve výchozím nastavení jsou zakázané optimalizace.|  
  
## <a name="remarks"></a>Poznámky  
 Optimalizace kompilátoru zkontrolujte výstupní soubor menší, rychlejší a efektivnější. Nicméně, protože optimalizace změnou kódu ve výstupním souboru `-optimize+` mohou ztížit ladění.  
  
 Všechny moduly, které generuje s použitím `-target:module` pro sestavení musíte použít stejné `-optimize` nastavení jako sestavení. Další informace najdete v tématu [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).  
  
 Můžete kombinovat `-optimize` a `-debug` možnosti.  
  
|Chcete-li nastavit – optimalizace v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1.  Mají projekt vybraný v **Průzkumníka řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.<br />     <br />2.  Klikněte na tlačítko **kompilaci** kartu.<br />3.  Klikněte na tlačítko **Upřesnit** tlačítko.<br />4.  Upravit **povolit optimalizace** zaškrtávací políčko.|  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` a povolí optimalizace kompilátoru.  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a>Viz také:
- [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)
- [-debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
