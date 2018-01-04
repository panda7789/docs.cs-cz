---
title: "Název &lt;parametr namespacename&gt; v kořenového oboru názvů &lt;fullnamespacename&gt; není kompatibilní se specifikací CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords: BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3a89f8cfe4038a81002777886de1155bea72ba22
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="name-ltnamespacenamegt-in-the-root-namespace-ltfullnamespacenamegt-is-not-cls-compliant"></a>Název &lt;parametr namespacename&gt; v kořenového oboru názvů &lt;fullnamespacename&gt; není kompatibilní se specifikací CLS
Sestavení je označena jako `<CLSCompliant(True)>`, ale element název kořenového oboru názvů začíná podtržítkem (`_`).  
  
 Programovací element může obsahovat jeden nebo více podtržítka, ale aby byly kompatibilní s [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), se nesmí začínat podtržítkem. V tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 Pokud použijete <xref:System.CLSCompliantAttribute> programovací element, nastavíte atributu `isCompliant` buď parametr `True` nebo `False` indikující dodržování předpisů nebo nesplňujících požadavky. Neexistuje žádný výchozí hodnotou tohoto parametru, a je nutné zadat hodnotu.  
  
 Pokud se nevztahují <xref:System.CLSCompliantAttribute> na element, je považován za nedodržuje předpisy.  
  
 Ve výchozím nastavení je tato zpráva upozornění. Informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC40039  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud budete potřebovat souladu se specifikací CLS, změňte název kořenového oboru názvů tak, aby žádný z jejích elementů začíná podtržítkem.  
  
-   Pokud budete potřebovat, že název oboru názvů zůstanou beze změny, potom odeberte <xref:System.CLSCompliantAttribute> ze sestavení nebo označte ji jako `<CLSCompliant(False)>`.  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [Obory názvů v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [/rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)  
 [Stránka Aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [Deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Zásady vytváření názvů jazyka Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 
