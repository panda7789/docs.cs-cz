---
title: Namespace nebo typ zadaný v importech úrovni projektu &#39; &lt;qualifiedelementname&gt; &#39; nemá&#39;t obsahovat všechny veřejné člen nebo nebyla nalezena
ms.date: 07/20/2015
f1_keywords:
- vbc40057
- bc40057
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
ms.openlocfilehash: d6d0c931262d892ec3e65888a76f25218b23d868
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595810"
---
# <a name="namespace-or-type-specified-in-the-project-level-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a>Namespace nebo typ zadaný v importech úrovni projektu &#39; &lt;qualifiedelementname&gt; &#39; nemá&#39;t obsahovat všechny veřejné člen nebo nebyla nalezena
Namespace nebo typ zadaný v úrovni projektu Imports\<qualifiedelementname >' neobsahuje žádný veřejný člen nebo nebyla nalezena. Zajistěte, aby obor názvů nebo typ je definovaný a obsahuje nejméně jeden člen veřejné. Ujistěte se, že název aliasu neobsahuje jiné aliasy.  
  
 Importu vlastnost projektu určuje obsahující element, který nelze nalézt nebo nejsou definovány žádné `Public` členy.  
  
 A *obsahující element* můžou být obor názvů, třída, struktura, modulu, rozhraní nebo výčet. Element obsahující obsahuje členy, jako jsou proměnné, postupy nebo jiné obsahující prvky.  
  
 Účelem importu je umožnit kódu členům přístup k oboru názvů nebo typ bez nutnosti jejich kvalifikaci. Projekt může být také nutné přidat odkaz na obor názvů nebo typu. Další informace najdete v tématu "Import obsahující prvků" v [odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Pokud kompilátor nemůže najít zadaný element obsahující, nelze ho přeložit odkazy, které ho používají. Pokud najde elementu, ale element nevystavuje žádné `Public` členy, pak žádný odkaz může být úspěšné. V obou případech je smysl pro import elementu.  
  
 Můžete použít **Návrhář projektu** k určení elementy pro import. Použití **importovat obory názvů** části **odkazy** stránky. Můžete získat **Návrhář projektu** dvojitým kliknutím **Můj projekt** ikonu v **Průzkumníku řešení**.  
  
 **ID chyby:** BC40057  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Otevřete **Návrhář projektu** a přepněte do **odkaz** stránky.  
  
2.  V **importovat obory názvů** části, ověřte, zda je přístupný z projektu obsahující element.  
  
3.  Ověřte, zda obsahující element zpřístupňuje alespoň jeden `Public` člen.  
  
## <a name="see-also"></a>Viz také  
 [Stránka Odkazy, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)  
 [Public](../../../visual-basic/language-reference/modifiers/public.md)  
 [Obory názvů v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [Odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
