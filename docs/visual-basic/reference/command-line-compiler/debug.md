---
title: /debug (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- debug compiler switches
- /debug compiler option [Visual Basic]
- -debug compiler option [Visual Basic]
- debug compiler option [Visual Basic]
ms.assetid: c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2
ms.openlocfilehash: 9bf7170cee31f92481b15fb1227f21895cd3734d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827975"
---
# <a name="-debug-visual-basic"></a>-debug (Visual Basic)
Způsobí, že kompilátor generovat ladicí informace a umístěte ho do výstupních souborů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-debug[+ | -]  
' -or-  
-debug:[full | pdbonly]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`+` &#124; `-`|Volitelné. Určení `+` nebo `/debug` způsobí, že kompilátor generovat ladicí informace a umístěte ho do souboru pdb. Určení `-` má stejný účinek jako bez zadání `/debug`.|  
|`full` &#124; `pdbonly`|Volitelné. Určuje typ ladicích informací generovaných kompilátorem. Pokud nezadáte `/debug:pdbonly`, výchozí hodnota je `full`, což vám umožní připojit ke spuštěnému programu ladicí program. `pdbonly` Argument umožňuje ladění zdrojového kódu, když je program spuštěn v ladicím programu, ale zobrazí jazyk sestavení kódu pouze v případě, že je spuštěný program je připojen k ladicímu programu.|  
  
## <a name="remarks"></a>Poznámky  
 Tuto možnost použijte, chcete-li vytvořit sestavení pro ladění. Pokud nezadáte `/debug`, `/debug+`, nebo `/debug:full`, nebude možné ladit výstupní soubor programu.  
  
 Ve výchozím nastavení, není aktivováno ladicí informace (`/debug-`). Chcete-li generovat ladicí informace, zadejte `/debug` nebo `/debug+`.  
  
 Informace o tom, jak konfigurovat výkon ladění aplikace najdete v tématu [usnadnění bitové kopie k ladění](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md).  
  
|Chcete-li nastavit - debug v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1.  S projekt vybraný v **Průzkumníka řešení**na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. <br />2.  Klikněte na tlačítko **kompilaci** kartu.<br />3.  Klikněte na tlačítko **Upřesnit možnosti kompilace**.<br />4.  Upravte hodnotu v **Generovat ladicí informace** pole.|  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu vloží ladicí informace do výstupního souboru `App.exe`.  
  
```  
vbc -debug -out:app.exe test.vb  
```  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)
- [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
