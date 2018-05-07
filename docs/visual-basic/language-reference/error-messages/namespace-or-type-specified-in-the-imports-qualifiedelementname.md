---
title: Namespace nebo typ zadaný v importech &#39; &lt;qualifiedelementname&gt; &#39; nemá&#39;t obsahovat všechny veřejné člen nebo nebyla nalezena
ms.date: 07/20/2015
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords:
- BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
ms.openlocfilehash: 8be0df5cbe4b8d4a640c9b6c2e126b3828254fd6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="namespace-or-type-specified-in-the-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a>Namespace nebo typ zadaný v importech &#39; &lt;qualifiedelementname&gt; &#39; nemá&#39;t obsahovat všechny veřejné člen nebo nebyla nalezena
Namespace nebo typ zadaný v importech\<qualifiedelementname >' neobsahuje žádný veřejný člen nebo nebyla nalezena. Zajistěte, aby obor názvů nebo typ je definovaný a obsahuje nejméně jeden člen veřejné. Ujistěte se, že název aliasu neobsahuje jiné aliasy.  
  
 `Imports` Příkaz určuje obsahující element, který nelze nalézt nebo nejsou definovány žádné `Public` členy.  
  
 A *obsahující element* můžou být obor názvů, třída, struktura, modulu, rozhraní nebo výčet. Element obsahující obsahuje členy, jako jsou proměnné, postupy nebo jiné obsahující prvky.  
  
 Účelem importu je umožnit kódu členům přístup k oboru názvů nebo typ bez nutnosti jejich kvalifikaci. Projekt může být také nutné přidat odkaz na obor názvů nebo typu. Další informace najdete v tématu "Import obsahující prvků" v [odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Pokud kompilátor nemůže najít zadaný element obsahující, nelze ho přeložit odkazy, které ho používají. Pokud najde elementu, ale element nevystavuje žádné `Public` členy, pak žádný odkaz může být úspěšné. V obou případech je smysl pro import elementu.  
  
 Uvědomte si, že pokud provedete import elementu s obsahem a přiřadit import alias, nemůžete použít tento alias import k importu jiný element. Následující kód generuje chybu kompilátoru.  
  
 `Imports`   `winfrm`   `= System.Windows.Forms`  
  
 `' The following statement is`   `INVALID`   `because it reuses an import alias.`  
  
 `Imports behav =`   `winfrm`  `.Design.Behavior`  
  
 **ID chyby:** BC40056  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Ověřte, zda je přístupný z projektu obsahující element.  
  
2.  Ověřte, že specifikace obsahující element neobsahuje libovolným aliasem import z jiného importu.  
  
3.  Ověřte, zda obsahující element zpřístupňuje alespoň jeden `Public` člen.  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Imports (obor názvů a typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [Příkaz Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [Public](../../../visual-basic/language-reference/modifiers/public.md)  
 [Obory názvů v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [Odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
