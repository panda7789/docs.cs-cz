---
title: -optimize
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: 337cb794ef9a405a178f1998cbe27b5da7709382
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397438"
---
# <a name="-optimize"></a>-optimize
Povolí nebo zakáže optimalizace kompilátoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Pojem|Definice|  
|---|---|  
|`+`&#124;`-`|Nepovinný parametr. `-optimize-`Možnost zakáže optimalizace kompilátoru. `-optimize+`Možnost povoluje optimalizace. Ve výchozím nastavení jsou optimalizace zakázané.|  
  
## <a name="remarks"></a>Poznámky  
 Optimalizace kompilátoru usnadňují, rychlejší a efektivnější výstupní soubor. Vzhledem k tomu, že optimalizace mají za následek změnu uspořádání kódu ve výstupním souboru, `-optimize+` může být ladění obtížné.  
  
 Všechny moduly generované v `-target:module` pro sestavení musí používat stejné `-optimize` nastavení jako sestavení. Další informace najdete v tématu [-target (Visual Basic)](target.md).  
  
 Můžete kombinovat `-optimize` `-debug` Možnosti a.  
  
|Nastavení – optimalizace v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1. v **Průzkumník řešení**mít vybraný projekt. V nabídce **projekt** klikněte na příkaz **vlastnosti**.<br />     <br />2. klikněte na kartu **kompilovat** .<br />3. klikněte na tlačítko **Upřesnit** .<br />4. Upravte zaškrtávací políčko **Povolit optimalizace** .|  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` a povolí optimalizace kompilátoru.  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](index.md)
- [-Debug (Visual Basic)](debug.md)
- [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)
- [-Target (Visual Basic)](target.md)
