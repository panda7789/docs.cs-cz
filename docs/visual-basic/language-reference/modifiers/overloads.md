---
title: Přetížení
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
ms.openlocfilehash: 44823b409cfa81dc889aabacf101fac90bf851e0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351413"
---
# <a name="overloads-visual-basic"></a>Přetížení (Visual Basic)

Určuje, že vlastnost nebo procedura znovu deklaruje jednu nebo více existujících vlastností nebo procedur se stejným názvem.

## <a name="remarks"></a>Poznámky

*Přetížení* je postup poskytnutí více než jedné definice pro danou vlastnost nebo název procedury ve stejném oboru. Redeklarace vlastnosti nebo procedury s jiným podpisem se někdy označuje jako *skrývání pomocí signatury*.

## <a name="rules"></a>Pravidla

- **Kontext deklarace** `Overloads` lze použít pouze v příkazu deklarace vlastnosti nebo procedury.

- **Kombinované modifikátory.** Nemůžete zadat `Overloads` společně se [stíny](../../../visual-basic/language-reference/modifiers/shadows.md) ve stejné deklaraci procedury.

- **Požadované rozdíly** *Signatura* v této deklaraci musí být odlišná od signatury každé vlastnosti nebo procedury, kterou přetěžuje. Signatura zahrnuje název vlastnosti nebo procedury spolu s následujícími vlastnostmi:

  - počet parametrů

  - pořadí parametrů

  - datové typy parametrů

  - počet parametrů typu (pro obecný postup)

  - návratový typ (pouze pro proceduru operátora převodu)

  Všechna přetížení musí mít stejný název, ale každá se musí lišit od všech ostatních v jednom nebo více předchozích ohledech. To umožňuje kompilátoru odlišit, která verze se má použít, když kód volá vlastnost nebo proceduru.

- **Nepovolené rozdíly.** Změna jednoho nebo více následujících možností není platná pro přetížení vlastnosti nebo procedury, protože nejsou součástí signatury:

  - bez ohledu na to, jestli vrátí hodnotu (pro proceduru)

  - Datový typ návratové hodnoty (s výjimkou operátoru převodu)

  - názvy parametrů nebo parametrů typu

  - omezení parametrů typu (pro obecný postup)

  - Klíčová slova modifikátoru parametru (například `ByRef` nebo `Optional`)

  - Klíčová slova modifikátoru vlastnosti nebo procedury (například `Public` nebo `Shared`)

- **Volitelný modifikátor** Nemusíte používat modifikátor `Overloads`, pokud definujete více přetížených vlastností nebo procedur ve stejné třídě. Pokud však použijete `Overloads` v jedné z deklarací, je nutné ji použít ve všech těchto deklaracích.

- **Nastínování a přetížení.** `Overloads` lze také použít ke stínování existujícího člena nebo sady přetížených členů v základní třídě. Při použití `Overloads` tímto způsobem deklarujete vlastnost nebo metodu se stejným názvem a stejným seznamem parametrů jako člen základní třídy a nezadáte klíčové slovo `Shadows`.

Použijete-li `Overrides`, kompilátor implicitně přidá `Overloads`, aby vaše rozhraní API knihovny fungovala C# snadněji.

V těchto kontextech lze použít modifikátor `Overloads`:

- [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)

- [Příkaz Operator](../../../visual-basic/language-reference/statements/operator-statement.md)

- [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)

- [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a>Viz také:

- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Přetížení procedury](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [Obecné typy v Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [Postupy: Definice operátoru převodu](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
