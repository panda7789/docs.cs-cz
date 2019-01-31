---
title: Obor názvů nebo typ zadaný v příkazu Imports '<qualifiedelementname>' neobsahuje žádný veřejný člen nebo nebyl nalezen.
ms.date: 07/20/2015
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords:
- BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
ms.openlocfilehash: d19a769b33b3b63b7f431b73841f49632e41f9e6
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55288272"
---
# <a name="namespace-or-type-specified-in-the-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a>Namespace nebo typ zadaný v příkazu Imports'\<qualifiedelementname >' neobsahuje žádný veřejný člen nebo nebyl nalezen
Namespace nebo typ zadaný v příkazu Imports'\<qualifiedelementname >' neobsahuje žádný veřejný člen nebo nebyl nalezen. Ujistěte se, že obor názvů nebo typ definován a obsahuje nejméně jeden veřejný člen. Ujistěte se, že název aliasu neobsahuje další aliasy.  
  
 `Imports` Příkaz určuje nadřazeného elementu, který nemůže být nalezen nebo nedefinuje žádné `Public` členy.  
  
 A *obsahující element* může být obor názvů, třída, struktura, modul, rozhraní nebo výčet. Obsahující element obsahuje členy, jako jsou proměnné, postupy a další obsahující prvky.  
  
 Účelem importu je umožnit váš kód získat přístup ke členům obor názvů nebo typ bez nutnosti je vyfiltrovat. Váš projekt může být také nutné přidat odkaz na obor názvů nebo typ. Další informace najdete v tématu "Import obsahující prvky" [odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Pokud kompilátor nemůže najít zadaný nadřazený prvek, nelze ho přeložit odkazy, které ji používají. Vyhledá prvek ale elementu nevystavuje žádné `Public` členové, pak žádný odkaz může být úspěšné. V obou případech je importovat element nemá význam.  
  
 Uvědomte si, že pokud provedete import nadřazeného elementu a přiřadit alias importu, nemůžete použít tento alias importu k importu jiný element. Následující kód vygeneruje chybu kompilátoru.  
  
 `Imports`   `winfrm`   `= System.Windows.Forms`  
  
 `' The following statement is`   `INVALID`   `because it reuses an import alias.`  
  
 `Imports behav =`   `winfrm`  `.Design.Behavior`  
  
 **ID chyby:** BC40056  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Ověřte, že nadřazeného elementu je dostupná z projektu.  
  
2.  Ověřte, že specifikace nadřazeného elementu nezahrnuje jakýkoli alias import z jiného importu.  
  
3.  Ověřte, že nadřazeného elementu zpřístupňuje alespoň jeden `Public` člena.  
  
## <a name="see-also"></a>Viz také:
- [Příkaz Imports (obor názvů a typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Příkaz Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Obory názvů v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [Odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
