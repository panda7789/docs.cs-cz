---
title: /debug (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- debug compiler switches
- /debug compiler option [Visual Basic]
- -debug compiler option [Visual Basic]
- debug compiler option [Visual Basic]
ms.assetid: c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f1c90b28f1df18e7e0a4f9e22730e1c3476fa650
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="debug-visual-basic"></a>/debug (Visual Basic)
Způsobí, že kompilátor generovat ladicí informace a jeho následné uložení do výstupní soubory.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/debug[+ | -]  
' -or-  
/debug:[full | pdbonly]  
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
  
|Chcete-li nastavit/Debug v sadě Visual Studio integrované vývojové prostředí|  
|---|  
|1.  S projekt vybraný v **Průzkumníku řešení**na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. Další informace najdete v tématu [Úvod do Návrhář projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Klikněte **zkompilovat** kartě.<br />3.  Klikněte na tlačítko **rozšířené možnosti kompilace**.<br />4.  Změňte hodnotu v **Generovat ladicí informace** pole.|  
  
## <a name="example"></a>Příklad  
 Následující příklad vloží informace o ladění do výstupního souboru `App.exe`.  
  
```  
vbc /debug /out:app.exe test.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
