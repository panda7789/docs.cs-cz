---
title: Název <membername> není kompatibilní se specifikací CLS.
ms.date: 07/20/2015
f1_keywords:
- bc40031
- vbc40031
helpviewer_keywords:
- BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
ms.openlocfilehash: 45c9332237dffc7311daeedaf36035d9e9958415
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397178"
---
# <a name="name-membername-is-not-cls-compliant"></a>Název \<membername> není kompatibilní se specifikací CLS.
Sestavení je označeno jako, `<CLSCompliant(True)>` ale zpřístupňuje člena s názvem, který začíná podtržítkem ( `_` ).  
  
 Programovací prvek může obsahovat jedno nebo více podtržítek, ale aby splňovaly [jazykovou nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), nesmí začínat podtržítkem. Viz [deklarované názvy elementů](../../programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 Použijete-li na <xref:System.CLSCompliantAttribute> programovací prvek, nastavíte `isCompliant` parametr atributu na hodnotu `True` nebo `False` k označení dodržování předpisů nebo nedodržení předpisů. Pro tento parametr neexistuje výchozí hodnota a je třeba uvést hodnotu.  
  
 Pokud na prvek nepoužijete <xref:System.CLSCompliantAttribute> , bude považován za nekompatibilní.  
  
 Ve výchozím nastavení je tato zpráva upozornění. Informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC40031  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pokud máte kontrolu nad zdrojovým kódem, změňte název členu tak, aby nezačínal podtržítkem.  
  
- Pokud vyžadujete, aby název členu zůstal beze změny, odeberte <xref:System.CLSCompliantAttribute> z jeho definice nebo ho označte jako `<CLSCompliant(False)>` . Můžete přesto označit sestavení jako `<CLSCompliant(True)>` .  
  
## <a name="see-also"></a>Viz také

- [Deklarované názvy elementů](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [Zásady vytváření názvů jazyka Visual Basic](../../programming-guide/program-structure/naming-conventions.md)
