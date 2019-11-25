---
title: Podmíněná kompilace
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: 19a2c70941a9a72574f7e624743def74b80c4e39
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347463"
---
# <a name="conditional-compilation-in-visual-basic"></a>Podmíněná kompilace v jazyce Visual Basic
In *conditional compilation*, particular blocks of code in a program are compiled selectively while others are ignored.  
  
 For example, you may want to write debugging statements that compare the speed of different approaches to the same programming task, or you may want to localize an application for multiple languages. Conditional compilation statements are designed to run during compile time, not at run time.  
  
 You denote blocks of code to be conditionally compiled with the `#If...Then...#Else` directive. For example, to create French- and German-language versions of the same application from the same source code, you embed platform-specific code segments in `#If...Then` statements using the predefined constants `FrenchVersion` and `GermanVersion`. The following example demonstrates how:  
  
 [!code-vb[VbVbalrConditionalComp#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#5)]  
  
 If you set the value of the `FrenchVersion` conditional compilation constant to `True` at compile time, the conditional code for the French version is compiled. If you set the value of the `GermanVersion` constant to `True`, the compiler uses the German version. If neither is set to `True`, the code in the last `Else` block runs.  
  
> [!NOTE]
> Autocompletion will not function when editing code and using conditional compilation directives if the code is not part of the current branch.  
  
## <a name="declaring-conditional-compilation-constants"></a>Declaring Conditional Compilation Constants  
 You can set conditional compilation constants in one of three ways:  
  
- In the **Project Designer**  
  
- At the command line when using the command-line compiler  
  
- In your code  
  
 Conditional compilation constants have a special scope and cannot be accessed from standard code. The scope of a conditional compilation constant is dependent on the way it is set. The following table lists the scope of constants declared using each of the three ways mentioned above.  
  
|How constant is set|Scope of constant|  
|---|---|  
|**Project Designer**|Public to all files in the project|  
|Příkazový řádek|Public to all files passed to the command-line compiler|  
|`#Const` statement in code|Private to the file in which it is declared|  
  
|To set constants in the Project Designer|  
|---|  
|-   Before creating your executable file, set constants in the **Project Designer** by following the steps provided in [Managing Project and Solution Properties](/visualstudio/ide/managing-project-and-solution-properties).|  
  
|To set constants at the command line|  
|---|  
|-   Use the **-d** switch to enter conditional compilation constants, as in the following example:<br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     No space is required between the **-d** switch and the first constant. For more information, see [-define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).<br />     Command-line declarations override declarations entered in the **Project Designer**, but do not erase them. Arguments set in **Project Designer** remain in effect for subsequent compilations.<br />     When writing constants in the code itself, there are no strict rules as to their placement, since their scope is the entire module in which they are declared.|  
  
|To set constants in your code|  
|---|  
|-   Place the constants in the declaration block of the module in which they are used. This helps keep your code organized and easier to read.|  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|---|---|  
|[Struktura programu a zásady týkající se kódu](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|Provides suggestions for making your code easy to read and maintain.|  
  
## <a name="reference"></a>Odkaz  
 [Direktiva #Const](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [Direktivy #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [-define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
