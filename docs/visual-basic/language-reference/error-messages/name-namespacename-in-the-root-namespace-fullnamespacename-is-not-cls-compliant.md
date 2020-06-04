---
title: Název <namespacename> v kořenovém oboru názvů <fullnamespacename> není kompatibilní se specifikací.
ms.date: 07/20/2015
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords:
- BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
ms.openlocfilehash: b03a50365122c17fa311a284bd6995d1af2631c3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401534"
---
# <a name="name-namespacename-in-the-root-namespace-fullnamespacename-is-not-cls-compliant"></a>Název \<namespacename> v kořenovém oboru názvů \<fullnamespacename> není kompatibilní se specifikací.
Sestavení je označeno jako `<CLSCompliant(True)>` , ale element názvu kořenového oboru názvů začíná podtržítkem ( `_` ).  
  
 Programovací prvek může obsahovat jedno nebo více podtržítek, ale aby splňovaly [jazykovou nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), nesmí začínat podtržítkem. Viz [deklarované názvy elementů](../../programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 Použijete-li na <xref:System.CLSCompliantAttribute> programovací prvek, nastavíte `isCompliant` parametr atributu na hodnotu `True` nebo `False` k označení dodržování předpisů nebo nedodržení předpisů. Pro tento parametr neexistuje výchozí hodnota a je třeba uvést hodnotu.  
  
 Pokud na prvek nepoužijete <xref:System.CLSCompliantAttribute> , bude považován za nekompatibilní.  
  
 Ve výchozím nastavení je tato zpráva upozornění. Informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC40039  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pokud požadujete kompatibilitu se specifikací CLS, změňte název kořenového oboru názvů tak, aby žádný z jeho elementů nezačínal podtržítkem.  
  
- Pokud vyžadujete, aby název oboru názvů zůstal beze změny, odeberte <xref:System.CLSCompliantAttribute> ze sestavení nebo jej označte jako `<CLSCompliant(False)>` .  
  
## <a name="see-also"></a>Viz také

- [Namespace – příkaz](../statements/namespace-statement.md)
- [Obory názvů v jazyce Visual Basic](../../programming-guide/program-structure/namespaces.md)
- [-rootnamespace](../../reference/command-line-compiler/rootnamespace.md)
- [Stránka Aplikace, návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Deklarované názvy elementů](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [Zásady vytváření názvů jazyka Visual Basic](../../programming-guide/program-structure/naming-conventions.md)
