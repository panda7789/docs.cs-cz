---
title: Obor názvů nebo typ zadaný v příkazu Imports '<qualifiedelementname>' neobsahuje žádný veřejný člen nebo nebyl nalezen.
ms.date: 07/20/2015
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords:
- BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
ms.openlocfilehash: 8675d9c3b202200c89e12e7a5f51a19d9e3e0e64
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409462"
---
# <a name="namespace-or-type-specified-in-the-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a>Obor názvů nebo typ zadaný v příkazu Imports '\<qualifiedelementname>' neobsahuje žádný veřejný člen nebo nebyl nalezen.

Obor názvů nebo typ zadaný v importech neobsahuje \<qualifiedelementname> žádné veřejné členy nebo se nedá najít. Ujistěte se, že je obor názvů nebo typ definován a obsahuje nejméně jeden veřejný člen. Ujistěte se, že název aliasu neobsahuje další aliasy.

`Imports`Příkaz určuje obsahující prvek, který buď nebyl nalezen, nebo nedefinuje žádné `Public` členy.

*Obsahující element* může být obor názvů, třída, struktura, modul, rozhraní nebo výčet. Obsahující element obsahuje členy, jako jsou proměnné, procedury nebo jiné obsahující prvky.

Účelem importu je dovolit vašemu kódu přístup k oboru názvů nebo členům typu bez nutnosti jejich zařazení. Projekt může také potřebovat přidat odkaz na obor názvů nebo typ. Další informace naleznete v tématu "Import obsahující prvky" v [odkazech na deklarované elementy](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).

Pokud kompilátor nemůže najít zadaný element, který obsahuje, nemůže vyřešit odkazy, které ho používají. Pokud prvek najde, ale nezveřejňuje žádné `Public` členy, nemůže být žádný odkaz úspěšný. V obou případech je to pro import elementu nevýznamný.

Mějte na paměti, že Pokud importujete element, který obsahuje, a přiřadíte mu alias pro import, nemůžete použít tento alias importu k importu jiného elementu. Následující kód vygeneruje chybu kompilátoru.

```vb
Imports winfrm = System.Windows.Forms

' The following statement is INVALID  because it reuses an import alias.

Imports behave = winfrm.Design.Behavior`
```

**ID chyby:** BC40056

## <a name="to-correct-this-error"></a>Oprava této chyby

1. Ověřte, zda je obsažený element přístupný z vašeho projektu.

2. Ověřte, že specifikace obsahujícího elementu neobsahuje žádný alias importu z jiného importu.

3. Ověřte, zda nadřazený element zveřejňuje alespoň jeden `Public` člen.

## <a name="see-also"></a>Viz také

- [Imports – příkaz (obor názvů a typ rozhraní .NET)](../statements/imports-statement-net-namespace-and-type.md)
- [Namespace – příkaz](../statements/namespace-statement.md)
- [Republik](../modifiers/public.md)
- [Obory názvů v jazyce Visual Basic](../../programming-guide/program-structure/namespaces.md)
- [Odkazy na deklarované elementy](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
