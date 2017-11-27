---
title: "Struktura programu a pravidla týkající se kódu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- coding conventions
- Visual Basic code, coding conventions
- coding conventions [Visual Basic], Visual Basic
- programs [Visual Basic], structure
- program structure [Visual Basic]
- naming conventions [Visual Basic], Visual Basic
- best practices [Visual Basic], coding conventions
- conventions [Visual Basic], Visual Basic coding
- Visual Basic code
- programming [Visual Basic], Visual Basic coding conventions
ms.assetid: dd9be76f-6944-4e78-ad72-0b6084a3fc13
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b38ba9623a20dcd1be4bc96f4aff1eb646b0a053
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="program-structure-and-code-conventions-visual-basic"></a>Struktura programu a pravidla týkající se kódu (Visual Basic)
Tato část obsahuje typické [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programu struktura, poskytuje jednoduchou [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programu "Hello, World" a popisuje [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] pravidla vytváření kódu. Pravidla týkající se kódu jsou návrhy, které soustředit není na programu logiku, ale na její fyzickou strukturu a vzhled. Následující je snazší kódu pro čtení, pochopit a údržbu. Pravidla týkající se kódu mohou zahrnovat mimo jiné:  
  
-   Standardizovaná formátech pro označování a komentářů kódu.  
  
-   Pokyny pro mezery, formátování a odsazení kódu.  
  
-   Zásady vytváření názvů pro objekty, proměnné a postupy.  
  
 Následující témata poskytují sadu pokyny pro programovací [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programy, společně s příklady dobrý využití.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Struktura programu v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 Poskytuje přehled prvků, které tvoří [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.  
  
 [Hlavní procedura v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)  
 Popisuje postup, který slouží jako počáteční bod a celkové řízení pro vaše aplikace.  
  
 [Odkazy a příkaz Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 Popisuje, jak odkazovat na objekty v jiných sestavení.  
  
 [Obory názvů v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 Popisuje, jak obory názvů uspořádání objektů v rámci sestavení.  
  
 [Zásady vytváření názvů jazyka Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 Obsahuje obecné pokyny pro pojmenování procedury, konstanty, proměnné, argumentů a objekty.  
  
 [Visual Basic – konvence kódování](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
 Zkontroluje pokyny použité při vývoji ukázky v této dokumentaci.  
  
 [Podmíněná kompilace](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 Popisuje, jak selektivně zkompilovat konkrétní bloky kódu při řízení kompilátoru ostatní ignorovat.  
  
 [Postupy: přerušení a kombinace příkazů v kódu](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 Ukazuje, jak k rozdělení dlouhých příkazů do více řádků a kombinace příkazů krátký na jeden řádek.  
  
 [Postupy: sbalení a skrytí sekcí kódu](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)  
 Ukazuje, jak sbalení a skrytí sekcí kódu [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] editor kódu.  
  
 [Postupy: popisků příkazů](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)  
 Ukazuje, jak označit řádek kódu pro jeho rozpoznání pro použití s příkazy, jako `On Error Goto`.  
  
 [Speciální znaky v kódu](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 Popisuje, jak a kde chcete použít jiné než číselné a neabecední znaky.  
  
 [Komentáře v kódu](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 Popisuje postup přidání popisný komentáře do vašeho kódu.  
  
 [Klíčová slova jako názvy elementu v kódu](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 Popisuje, jak použít závorky (`[]`) a tím vymezit názvy proměnných, které jsou také [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] klíčová slova.  
  
 [ME, My, MyBase a MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 Popisuje různé způsoby, jak odkazovat na prvky [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.  
  
 [Omezení jazyka Visual Basic](../../../visual-basic/programming-guide/program-structure/limitations.md)  
 Popisuje odebrání známé kódování omezení v rámci [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
## <a name="related-sections"></a>Související oddíly  
 [Typografická pravidla a pravidla vytváření kódu](../../../visual-basic/language-reference/typographic-and-code-conventions.md)  
 Poskytuje standardní konvence psaní kódu pro [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
 [Psaní kódu](/visualstudio/ide/writing-code-in-the-code-and-text-editor)  
 Popisuje funkce, které usnadňují můžete zapsat a spravovat váš kód.
