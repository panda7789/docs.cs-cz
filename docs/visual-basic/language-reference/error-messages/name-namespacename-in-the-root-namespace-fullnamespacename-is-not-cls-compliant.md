---
title: Název <namespacename> v kořenovém oboru názvů <fullnamespacename> není kompatibilní se specifikací.
ms.date: 07/20/2015
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords:
- BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
ms.openlocfilehash: 821044d3ee359a052fa6a763e9c5a89da5d6f607
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775572"
---
# <a name="name-namespacename-in-the-root-namespace-fullnamespacename-is-not-cls-compliant"></a>Název \<namespacename > v kořenovém oboru názvů \<fullnamespacename > není kompatibilní se specifikací CLS.
Sestavení je označeno jako `<CLSCompliant(True)>`, ale element názvu kořenového oboru názvů začíná podtržítkem (`_`).  
  
 Programovací prvek může obsahovat jedno nebo více podtržítek, ale aby splňovaly [jazykovou nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), nesmí začínat podtržítkem. Viz [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 Použijete-li <xref:System.CLSCompliantAttribute> na programovací prvek, nastavíte parametr `isCompliant` atributu na hodnotu `True` nebo `False` k označení dodržování předpisů nebo nedodržení předpisů. Pro tento parametr neexistuje výchozí hodnota a je třeba uvést hodnotu.  
  
 Pokud nepoužijete <xref:System.CLSCompliantAttribute> na prvek, považuje se za nevyhovující.  
  
 Ve výchozím nastavení je tato zpráva upozornění. Informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC40039  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pokud požadujete kompatibilitu se specifikací CLS, změňte název kořenového oboru názvů tak, aby žádný z jeho elementů nezačínal podtržítkem.  
  
- Pokud vyžadujete, aby název oboru názvů zůstal beze změny, odeberte <xref:System.CLSCompliantAttribute> ze sestavení nebo jej označte jako `<CLSCompliant(False)>`.  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Obory názvů v Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [-rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)
- [Stránka Aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Visual Basic konvence pojmenování](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
