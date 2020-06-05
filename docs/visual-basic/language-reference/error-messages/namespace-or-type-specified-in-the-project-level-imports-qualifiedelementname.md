---
title: Obor názvů nebo typ zadaný v příkazu Imports '<qualifiedelementname>' na úrovni projektu neobsahuje žádného veřejného člena nebo nebyl nalezen.
ms.date: 07/20/2015
f1_keywords:
- vbc40057
- bc40057
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
ms.openlocfilehash: 0ee235252d69e6f77ce53b048f45e73d0969e864
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409449"
---
# <a name="namespace-or-type-specified-in-the-project-level-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a>Obor názvů nebo typ zadaný v příkazu Imports '\<qualifiedelementname>' na úrovni projektu neobsahuje žádného veřejného člena nebo nebyl nalezen.
Obor názvů nebo typ zadaný v importech na úrovni projektu neobsahuje \<qualifiedelementname> žádné veřejné členy nebo se nedá najít. Ujistěte se, že je obor názvů nebo typ definován a obsahuje nejméně jeden veřejný člen. Ujistěte se, že název aliasu neobsahuje další aliasy.  
  
 Vlastnost Import projektu určuje obsahující prvek, který buď nebyl nalezen, nebo nedefinuje žádné `Public` členy.  
  
 *Obsahující element* může být obor názvů, třída, struktura, modul, rozhraní nebo výčet. Obsahující element obsahuje členy, jako jsou proměnné, procedury nebo jiné obsahující prvky.  
  
 Účelem importu je dovolit vašemu kódu přístup k oboru názvů nebo členům typu bez nutnosti jejich zařazení. Projekt může také potřebovat přidat odkaz na obor názvů nebo typ. Další informace naleznete v tématu "Import obsahující prvky" v [odkazech na deklarované elementy](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Pokud kompilátor nemůže najít zadaný element, který obsahuje, nemůže vyřešit odkazy, které ho používají. Pokud prvek najde, ale nezveřejňuje žádné `Public` členy, nemůže být žádný odkaz úspěšný. V obou případech je to pro import elementu nevýznamný.  
  
 K určení prvků pro import lze použít **Návrhář projektu** . Použijte část **importované obory názvů** na stránce **odkazy** . Můžete získat přístup k **Návrháři projektu** dvojitým kliknutím na ikonu **můj projekt** v **Průzkumník řešení**.  
  
 **ID chyby:** BC40057  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Otevřete **Návrháře projektu** a přepněte na **referenční** stránku.  
  
2. V části **importované obory názvů** ověřte, zda je obsažený element přístupný z vašeho projektu.  
  
3. Ověřte, zda nadřazený element zveřejňuje alespoň jeden `Public` člen.  
  
## <a name="see-also"></a>Viz také

- [Stránka Odkazy, návrhář projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
- [Republik](../modifiers/public.md)
- [Obory názvů v jazyce Visual Basic](../../programming-guide/program-structure/namespaces.md)
- [Odkazy na deklarované elementy](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
