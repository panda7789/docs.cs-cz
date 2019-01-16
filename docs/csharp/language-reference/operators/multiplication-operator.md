---
title: '* Operator - C# odkaz'
ms.custom: seodec18
ms.date: 04/04/2018
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
ms.openlocfilehash: f4490c4632d9344eb879ea55c20787b838781d91
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333730"
---
# <a name="-operator-c-reference"></a>* – operátor (C# odkaz)

Operátor násobení (`*`) vypočítá součin z operandů. Všechny číselné typy obsahuje předdefinované operátory násobení.

`*` slouží také jako operátor zrušení odkazu, který umožňuje čtení a zápis na ukazatel.

## <a name="remarks"></a>Poznámky

`*` Operátor se používá také, chcete-li deklarovat typy ukazatelů a ke zrušení ukazatele. Tento operátor jde použít jenom v kontextu unsafe, udávají použití [nebezpečné](../keywords/unsafe.md) – klíčové slovo která vyžaduje [/ unsafe](../compiler-options/unsafe-compiler-option.md) – možnost kompilátoru.  Operátor zrušení odkazu se také označuje jako operátor dereference.

Uživatelem definované typy mohou přetížit binárního souboru `*` – operátor (viz [operátor](../keywords/operator.md)). Při je binární operátor přetížen, odpovídající operátor přiřazení, pokud existuje, je také implicitně přetížená.

## <a name="example"></a>Příklad

[!code-csharp-interactive[csRefOperators#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#50)]

## <a name="example"></a>Příklad

[!code-csharp[csRefOperators#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#51)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Nebezpečný kód a ukazatele](../../programming-guide/unsafe-code-pointers/index.md)
- [Operátory jazyka C#](index.md)