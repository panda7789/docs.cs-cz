---
title: Protected (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
ms.openlocfilehash: 86758c68f0f3bfe214a695f656d3924eadd27e31
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642691"
---
# <a name="protected-visual-basic"></a>Protected (Visual Basic)
Modifikátor přístupu člena, který určuje, že jeden nebo více deklarovaný programový prvek je přístupný jenom v rámci své vlastní třídy nebo z odvozené třídy.  
  
## <a name="remarks"></a>Poznámky  
 Někdy programovací element deklarovaný ve třídě obsahuje citlivé údaje nebo s omezeným přístupem kódu a chcete omezit přístup k elementu. Nicméně pokud je třída odvoditelný a očekáváte, že hierarchie odvozené třídy, může být nezbytné pro tyto odvozených tříd pro přístup k data nebo kód. V takovém případě má element být přístupné ze základní třídy a ze všech odvozených tříd. Omezení přístupu k elementu tímto způsobem je možné deklarovat s `Protected`.  

> [!NOTE]
> `Protected` Modifikátor přístupu je možné kombinovat s dvěma další modifikátory:
> - [Protected Friend](protected-friend.md) modifikátor zpřístupňuje člen třídy z v rámci této třídy z odvozené třídy a ze stejného sestavení, ve kterém je třída definovaná. 
> - [Private Protected](private-protected.md) modifikátor zpřístupňuje člen třídy odvozené typy, ale pouze v rámci jeho obsahujícího sestavení.
  
## <a name="rules"></a>pravidla  
  
- **Místní deklarace.** Můžete použít `Protected` pouze na úrovni třídy. To znamená, že deklarace kontext `Protected` elementu musí být třída a nemůže být zdrojový soubor, obor názvů, rozhraní, modul, struktury nebo proceduru.  

## <a name="behavior"></a>Chování  
  
- **Úroveň přístupu.** Veškerý kód ve třídě můžete přístup k jeho prvkům. Kód do třídy, která je odvozena ze základní třídy lze přistupovat ke všem `Protected` prvky základní třídy. To platí pro všechny generací odvození. To znamená, že se třída dostanete `Protected` elementů základní třídy základní třídy a tak dále.  
  
     Chráněného přístupu je nadmnožinou nebo podmnožinu přístup typu friend.  
  
- **Modifikátory přístupu.** Klíčová slova, které určují úroveň přístupu se nazývají *modifikátorů přístupu*. Porovnání přístupu modifikátory přístupu najdete v tématu [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `Protected` Modifikátor lze použít v těchto kontextech:  
  
 [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Příkaz Const](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Příkaz Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Příkaz Enum](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Příkaz Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také:

- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](private-protected.md)
- [Protected Friend](protected-friend.md)
- [Úrovně přístupu v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
