---
title: /optioninfer
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: /optioninfer
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4400ee58214c8f9990d4b123e17ef0f6553a5a69
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="optioninfer"></a>/optioninfer
Umožňuje použití odvození místního typu v deklarace proměnných.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/optioninfer[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`+` &#124; `-`|Volitelné. Zadejte `/optioninfer+` povolit odvození místního typu nebo `/optioninfer-` zablokujete jeho. `/optioninfer` Možnost s žádná hodnota zadána, je stejný jako `/optioninfer+`. Výchozí hodnotu v případě `/optioninfer` přepínač není k dispozici je také `/optioninfer+`. Výchozí hodnota je nastavena v souboru odpovědí, Vbc.rsp.|  
  
> [!NOTE]
>  Můžete použít `/noconfig` možnost zachování interní výchozí nastavení kompilátoru místo platformám zadaným v vbc.rsp. Tato možnost je výchozí hodnotou kompilátoru `/optioninfer-`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud obsahuje souboru se zdrojovým kódem [Option Infer – příkaz](../../../visual-basic/language-reference/statements/option-infer-statement.md), přepíše příkaz `/optioninfer` nastavení kompilátoru příkazového řádku.  
  
### <a name="to-set-optioninfer-in-the-visual-studio-ide"></a>Chcete-li nastavit/optioninfer v integrovaném vývojovém prostředí sady Visual Studio  
  
1.  Vyberte projekt v **Průzkumníku řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. Další informace najdete v tématu [NIB: Správa vlastností projektu s Návrhář projektu](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).  
  
2.  Na **zkompilovat** kartě, změňte hodnotu v **Option infer –** pole.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `test.vb` s odvození místního typu povolen.  
  
```  
vbc /optioninfer+ test.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [/ optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [/ optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Option Infer – příkaz](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [Odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Dialogové okno Možnosti výchozí hodnoty, projekty, Visual Basic](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)  
 [Stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [/ noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [Sestavování z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)
