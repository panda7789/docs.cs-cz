---
title: -optimize
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: e8daf4a49123623b6470bc3c6281869f1b9b3d0f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005368"
---
# <a name="-optimize"></a>-optimize
Povolí nebo zakáže optimalizace kompilátoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`+` &#124; `-`|Volitelné. Možnost `-optimize-` zakáže optimalizace kompilátoru. Možnost `-optimize+` povoluje optimalizace. Ve výchozím nastavení jsou optimalizace zakázané.|  
  
## <a name="remarks"></a>Poznámky  
 Optimalizace kompilátoru usnadňují, rychlejší a efektivnější výstupní soubor. Vzhledem k tomu, že optimalizace mají za následek změnu uspořádání kódu ve výstupním souboru, `-optimize+` může způsobit obtížné ladění.  
  
 Všechny moduly generované pomocí `-target:module` pro sestavení musí používat stejné nastavení `-optimize` jako sestavení. Další informace najdete v tématu [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).  
  
 Můžete kombinovat možnosti `-optimize` a `-debug`.  
  
|Nastavení – optimalizace v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1. v **Průzkumník řešení**mít vybraný projekt. V nabídce **projekt** klikněte na příkaz **vlastnosti**.<br />     <br />2. klikněte na kartu **kompilovat** .<br />3. klikněte na tlačítko **Upřesnit** .<br />4. Upravte zaškrtávací políčko **Povolit optimalizace** .|  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` a povoluje optimalizace kompilátoru.  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [-Debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
