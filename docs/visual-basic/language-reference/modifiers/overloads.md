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
ms.openlocfilehash: bd0931cab520f8580c0d7473a44e350752e287bb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392103"
---
# <a name="overloads-visual-basic"></a>Přetížení (Visual Basic)

Určuje, že vlastnost nebo procedura znovu deklaruje jednu nebo více existujících vlastností nebo procedur se stejným názvem.

## <a name="remarks"></a>Poznámky

*Přetížení* je postup poskytnutí více než jedné definice pro danou vlastnost nebo název procedury ve stejném oboru. Redeklarace vlastnosti nebo procedury s jiným podpisem se někdy označuje jako *skrývání pomocí signatury*.

## <a name="rules"></a>Pravidla

- **Kontext deklarace** Můžete použít `Overloads` pouze v příkazu deklarace vlastnosti nebo procedury.

- **Kombinované modifikátory.** Nemůžete zadat `Overloads` společně se [stíny](shadows.md) v rámci stejné deklarace procedury.

- **Požadované rozdíly** *Signatura* v této deklaraci musí být odlišná od signatury každé vlastnosti nebo procedury, kterou přetěžuje. Signatura zahrnuje název vlastnosti nebo procedury spolu s následujícími vlastnostmi:

  - počet parametrů

  - pořadí parametrů

  - datové typy parametrů

  - počet parametrů typu (pro obecný postup)

  - návratový typ (pouze pro proceduru operátora převodu)

  Všechna přetížení musí mít stejný název, ale každá se musí lišit od všech ostatních v jednom nebo více předchozích ohledech. To umožňuje kompilátoru odlišit, která verze se má použít, když kód volá vlastnost nebo proceduru.

- **Nepovolené rozdíly.** Změna jednoho nebo více následujících možností není platná pro přetížení vlastnosti nebo procedury, protože nejsou součástí signatury:

  - bez ohledu na to, jestli vrátí hodnotu (pro proceduru)

  - datový typ návratové hodnoty (s výjimkou operátoru převodu)

  - názvy parametrů nebo parametrů typu

  - omezení parametrů typu (pro obecný postup)

  - Klíčová slova modifikátoru parametru (například `ByRef` nebo `Optional` )

  - Klíčová slova modifikátoru vlastnosti nebo procedury (například `Public` nebo `Shared` )

- **Volitelný modifikátor** Nemusíte používat `Overloads` Modifikátor při definování více přetížených vlastností nebo procedur ve stejné třídě. Pokud však použijete `Overloads` v jedné z deklarací, je nutné ji použít ve všech těchto deklaracích.

- **Nastínování a přetížení.** `Overloads`lze také použít pro stín existujícího člena nebo sadu přetížených členů v základní třídě. Při použití `Overloads` tímto způsobem deklarujete vlastnost nebo metodu se stejným názvem a stejným seznamem parametrů jako člen základní třídy a nezadáte `Shadows` klíčové slovo.

Použijete `Overrides` -li, kompilátor implicitně přidá, `Overloads` aby vaše rozhraní API knihovny pracovalo s jazykem C# snadněji.

`Overloads`V těchto kontextech lze použít modifikátor:

- [Function – příkaz](../statements/function-statement.md)

- [Operator – příkaz](../statements/operator-statement.md)

- [Property – příkaz](../statements/property-statement.md)

- [Sub – příkaz](../statements/sub-statement.md)

## <a name="see-also"></a>Viz také

- [Shadows](shadows.md)
- [Přetížení procedury](../../programming-guide/language-features/procedures/procedure-overloading.md)
- [Obecné typy v Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [Procedury operátoru](../../programming-guide/language-features/procedures/operator-procedures.md)
- [Postupy: Definice operátoru převodu](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
