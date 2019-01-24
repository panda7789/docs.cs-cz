---
title: Namespace nebo typ zadaný v příkazu Imports na úrovni projektu &#39; &lt;qualifiedelementname&gt; &#39; kódu&#39;t obsahovat žádný veřejný člen nebo nebyl nalezen
ms.date: 07/20/2015
f1_keywords:
- vbc40057
- bc40057
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
ms.openlocfilehash: 215d8d301317f711aecb88167030e70ed01408aa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54552460"
---
# <a name="namespace-or-type-specified-in-the-project-level-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a>Namespace nebo typ zadaný v příkazu Imports na úrovni projektu &#39; &lt;qualifiedelementname&gt; &#39; kódu&#39;t obsahovat žádný veřejný člen nebo nebyl nalezen
Namespace nebo typ zadaný v příkazu Imports na úrovni projektu'\<qualifiedelementname >' neobsahuje žádný veřejný člen nebo nebyl nalezen. Ujistěte se, že obor názvů nebo typ definován a obsahuje nejméně jeden veřejný člen. Ujistěte se, že název aliasu neobsahuje další aliasy.  
  
 Vlastnost importu projektu určuje nadřazeného elementu, který nemůže být nalezen nebo nedefinuje žádné `Public` členy.  
  
 A *obsahující element* může být obor názvů, třída, struktura, modul, rozhraní nebo výčet. Obsahující element obsahuje členy, jako jsou proměnné, postupy a další obsahující prvky.  
  
 Účelem importu je umožnit váš kód získat přístup ke členům obor názvů nebo typ bez nutnosti je vyfiltrovat. Váš projekt může být také nutné přidat odkaz na obor názvů nebo typ. Další informace najdete v tématu "Import obsahující prvky" [odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Pokud kompilátor nemůže najít zadaný nadřazený prvek, nelze ho přeložit odkazy, které ji používají. Vyhledá prvek ale elementu nevystavuje žádné `Public` členové, pak žádný odkaz může být úspěšné. V obou případech je importovat element nemá význam.  
  
 Můžete použít **Návrháře projektu** k určení prvků k importu. Použití **importovat obory názvů** část **odkazy** stránky. Můžete získat **Návrháře projektu** dvojitým kliknutím **Můj projekt** ikonu **Průzkumníku řešení**.  
  
 **ID chyby:** BC40057  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Otevřít **Návrháře projektu** a přepněte se na **odkaz** stránky.  
  
2.  V **importovat obory názvů** části, ověřte, zda je přístupný z projektu nadřazeného elementu.  
  
3.  Ověřte, že nadřazeného elementu zpřístupňuje alespoň jeden `Public` člena.  
  
## <a name="see-also"></a>Viz také:
- [Stránka Odkazy, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Obory názvů v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [Odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
