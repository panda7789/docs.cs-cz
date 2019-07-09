---
title: Přetížení (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Overloads
- Overloads
helpviewer_keywords:
- Overloads keyword [Visual Basic]
- hiding by signature
- Shadows keyword [Visual Basic]
- signature, hiding by
ms.assetid: 0c6820b8-25b2-4664-bc59-5ca93c99c042
ms.openlocfilehash: 838207fe3ac5b8f57d030617546b9b7fa25dc939
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663543"
---
# <a name="overloads-visual-basic"></a>Přetížení (Visual Basic)

Určuje, že se vlastnost nebo procedura znovu deklaruje jednu nebo více existujících vlastností nebo procedur se stejným názvem.

## <a name="remarks"></a>Poznámky

*Přetížení* je zvyk poskytování více než jednu definici pro danou vlastnost nebo procedura názvu ve stejném oboru. Změně deklarace se vlastnost nebo procedura s jiným podpisem se někdy označuje jako *skrytí podle podpisu*.

## <a name="rules"></a>pravidla

- **Místní deklarace.** Můžete použít `Overloads` pouze v příkazu deklarace vlastnost nebo procedura.

- **Kombinované modifikátory.** Nelze zadat `Overloads` spolu s [stíny](../../../visual-basic/language-reference/modifiers/shadows.md) ve stejné deklaraci procedury.

- **Požadované rozdíly.** *Podpis* v této deklaraci musí být odlišný od podpis každou vlastnost nebo proceduru, která ji přetíží. Podpis se skládá z názvu vlastnost nebo procedura spolu s následující:

  - počet parametrů

  - pořadí parametrů

  - datové typy parametrů

  - počet parametrů typu (pro obecný postup)

  - Návratový typ (pouze pro procedury operátoru převodu)

  Všechna přetížení musí mít stejný název, ale každý se musí lišit od všech ostatních počítačů v jedné nebo více předchozích ohledech. To umožňuje kompilátoru k rozlišení, které verze se má použít, když kód volá vlastnost nebo procedura.

- **Nepovolené rozdíly.** Změna jeden nebo více z následujících akcí není platná pro přetížení se vlastnost nebo procedura, protože nejsou součástí podpisu:

  - Určuje, jestli vrací hodnotu (postup)

  - Datový typ vrácené hodnoty (s výjimkou operátoru převodu)

  - názvy parametrů nebo parametry typu

  - omezení parametrů typů (pro obecný postup)

  - klíčová slova modifikátor parametrů (jako například `ByRef` nebo `Optional`)

  - Vlastnost nebo procedura modifikátor klíčová slova (jako například `Public` nebo `Shared`)

- **Volitelný modifikátor.** Není nutné používat `Overloads` modifikátor při definování více přetížených vlastností nebo procedur ve stejné třídě. Nicméně pokud používáte `Overloads` v jednom z deklarací, je nutné je použít pro všechny z nich.

- **Stínový provoz a přetížení.** `Overloads` Můžete také použít stínové existujícího člena nebo sadu přetížených členů v základní třídě. Při použití `Overloads` tímto způsobem můžete deklarovat vlastnosti nebo metody se stejným názvem a seznamu parametrů jako člena základní třídy a nezadáte `Shadows` – klíčové slovo.

Pokud používáte `Overrides`, kompilátor implicitně přidá `Overloads` tak, aby vaše knihovna rozhraní API pro práci s C# snadněji.

`Overloads` Modifikátor lze použít v těchto kontextech:

- [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)

- [Příkaz Operator](../../../visual-basic/language-reference/statements/operator-statement.md)

- [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)

- [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a>Viz také:

- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Přetížení procedury](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [Obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [Postupy: Definice operátora převodu](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
