---
title: /debug (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- debug compiler switches
- /debug compiler option [Visual Basic]
- -debug compiler option [Visual Basic]
- debug compiler option [Visual Basic]
ms.assetid: c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18d74b8f0a7b319e08780a8db9175c7be16d932e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="-debug-visual-basic"></a>-debug (Visual Basic)
Způsobí, že kompilátor generovat ladicí informace a jeho následné uložení do výstupní soubory.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-debug[+ | -]  
' -or-  
-debug:[full | pdbonly]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`+` &#124; `-`|Volitelné. Určení `+` nebo `/debug` způsobí, že kompilátor generovat ladicí informace a umístěte jej do souboru pdb. Určení `-` má stejný účinek jako bez zadání `/debug`.|  
|`full` &#124; `pdbonly`|Volitelné. Určuje typ ladicí informace generované kompilátorem. Pokud nezadáte `/debug:pdbonly`, výchozí hodnota je `full`, což umožňuje připojit ladicí program spuštěného programu. `pdbonly` Argument pro možnost zdrojového kódu ladění při spuštění programu v ladicím programu, ale zobrazí kódu jazyka sestavení jenom v případě, že se spuštěným programem je připojen k ladicího programu.|  
  
## <a name="remarks"></a>Poznámky  
 Tuto možnost použijte k vytvoření sestavení pro ladění. Pokud nezadáte `/debug`, `/debug+`, nebo `/debug:full`, nebude možné ladit výstupní soubor vašeho programu.  
  
 Ve výchozím nastavení, není vygenerované ladicí informace (`/debug-`). Chcete-li generovat ladicí informace, zadejte `/debug` nebo `/debug+`.  
  
 Informace o tom, jak nakonfigurovat ladění výkonu aplikace, najdete v tématu [snadněji bitové kopie pro ladění](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md).  
  
|Chcete-li nastavit - debug v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1.  S projekt vybraný v **Průzkumníku řešení**na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. <br />2.  Klikněte **zkompilovat** kartě.<br />3.  Klikněte na tlačítko **rozšířené možnosti kompilace**.<br />4.  Změňte hodnotu v **Generovat ladicí informace** pole.|  
  
## <a name="example"></a>Příklad  
 Následující příklad vloží informace o ladění do výstupního souboru `App.exe`.  
  
```  
vbc -debug -out:app.exe test.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
