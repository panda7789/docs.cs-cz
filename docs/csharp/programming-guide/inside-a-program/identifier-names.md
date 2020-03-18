---
title: Názvy identifikátorů
description: Naučte se pravidla pro platné názvy identifikátorů v programovacím jazyce C#.
ms.date: 08/21/2018
ms.openlocfilehash: bef6e2ea285b5391af3350ae42a4105d140c6d1b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77673365"
---
# <a name="identifier-names"></a>Názvy identifikátorů

**Identifikátor** je název, který přiřadíte typu (třída, rozhraní, struktura, delegát nebo výčt), člen, proměnná nebo obor názvů. Platné identifikátory se musí řídit těmito pravidly:

- Identifikátory musí začínat `_`písmenem nebo .
- Identifikátory mohou obsahovat znaky písmen Unicode, desetinné číslice, spojovací znaky Unicode, znaky kombinující znaky Unicode nebo formátovací znaky Unicode. Další informace o kategoriích Unicode naleznete v [databázi kategorií Unicode](https://www.unicode.org/reports/tr44/).
Můžete deklarovat identifikátory, které odpovídají `@` c# klíčová slova pomocí předpony na identifikátor. Není `@` součástí názvu identifikátoru. Například `@if` deklaruje `if`identifikátor s názvem . Tyto [doslovné identifikátory](../../language-reference/tokens/verbatim.md) jsou primárně pro interoperabilitu s identifikátory deklarovanými v jiných jazycích.

For a complete definition of valid identifiers, see the [Identifiers topic in the C# Language Specification](../../../../_csharplang/spec/lexical-structure.md#identifiers).

## <a name="naming-conventions"></a>Zásady vytváření názvů

Kromě pravidel existuje řada [konvencí pojmenování identifikátorů používaných](../../../standard/design-guidelines/naming-guidelines.md) v rámci rozhraní API .NET. Podle konvence c# `PascalCase` programy používají pro názvy typů, obory názvů a všechny veřejné členy. Kromě toho jsou společné následující konvence:

- Názvy rozhraní začínají `I`velkým písmenem .
- Typy atributů končí `Attribute`slovem .
- Typy výčtu používají jednotné ho nitkového označení pro nepříznaky a množné číslo pro příznaky.
- Identifikátory by neměly `_` obsahovat dva po sobě jdoucí znaky. Tyto názvy jsou vyhrazeny pro identifikátory generované kompilátorem.

## <a name="c-language-specification"></a>Specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [V programu v jazyce C#](./index.md)
- [Odkaz jazyka C#](../../language-reference/index.md)
- [Třídy](../classes-and-structs/classes.md)
- [Typy struktur](../../language-reference/builtin-types/struct.md)
- [Obory názvů](../namespaces/index.md)
- [Rozhraní](../interfaces/index.md)
- [Delegáty](../delegates/index.md)
