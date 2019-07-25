---
title: Nespravované typy C# – referenční informace
ms.date: 07/23/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 5b08b55f5c52fe2ad20cb25bca0449eb26e333ca
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68440236"
---
# <a name="unmanaged-types-c-reference"></a>Nespravované typyC# (Referenční dokumentace)

**Nespravovaný typ** je jakýkoli typ, který není odkazovým typem nebo vytvořeným typem (typ, který obsahuje alespoň jeden argument typu) a neobsahuje typ odkazu ani vytvořená pole typu na jakékoli úrovni vnoření. Jinými slovy, nespravovaný typ je jedna z následujících:

- `sbyte`, `byte` ,`short`, ,`int`, ,`long`,,,, ,`double`nebo `uint` `ulong` `char` `float` `ushort` `decimal``bool`
- Libovolný typ [výčtu](../keywords/enum.md)
- Libovolný typ [ukazatele](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- Libovolný uživatelsky definovaný typ [struktury](../keywords/struct.md) , který není konstruovaným typem a obsahuje pole pouze nespravovaných typů.

Počínaje C# 7,3 můžete [ `unmanaged` omezení](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) použít k určení toho, že parametr typu je nespravovaný typ bez ukazatele.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [typy ukazatelů](~/_csharplang/spec/unsafe-code.md#pointer-types) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [sizeof – operátor](../keywords/sizeof.md)
- [stackalloc – operátor](../operators/stackalloc.md)
