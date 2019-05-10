---
title: Název <namespacename> v kořenovém oboru názvů <fullnamespacename> není kompatibilní se specifikací.
ms.date: 07/20/2015
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords:
- BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
ms.openlocfilehash: faed46eaf21513945ef4eb0c76d36780e960d380
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592027"
---
# <a name="name-namespacename-in-the-root-namespace-fullnamespacename-is-not-cls-compliant"></a>Název \<namespacename > v kořenovém oboru názvů \<fullnamespacename > není kompatibilní se Specifikací CLS
Sestavení je označen jako `<CLSCompliant(True)>`, ale element název kořenového oboru názvů začíná podtržítkem (`_`).  
  
 Programovací element může obsahovat jeden nebo více podtržítka, ale chcete-li být kompatibilní s [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), se nesmí začínat podtržítkem. Zobrazit [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 Pokud použijete <xref:System.CLSCompliantAttribute> na programovací prvek, nastavíte atributu `isCompliant` buď parametr `True` nebo `False` k označení dodržování předpisů nebo při nedodržení předpisů. Neexistuje žádný výchozí hodnotou tohoto parametru, a je nutné zadat hodnotu.  
  
 Pokud se nevztahují <xref:System.CLSCompliantAttribute> na element, se považuje za jako nevyhovující.  
  
 Ve výchozím nastavení tato zpráva je upozornění. Informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC40039  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pokud budete vyžadovat dodržování specifikace CLS, změňte název kořenového oboru názvů tak, aby žádný z jeho prvků začíná podtržítkem.  
  
- Pokud budete vyžadovat, že název oboru názvů zůstanou beze změny, odstraňte <xref:System.CLSCompliantAttribute> ze sestavení nebo označte ji jako `<CLSCompliant(False)>`.  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Obory názvů v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [/rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)
- [Stránka Aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Zásady vytváření názvů jazyka Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
