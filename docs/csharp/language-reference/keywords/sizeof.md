---
title: sizeof – C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: a00c4f96e62f7fd7d7c352aece097acd5b600ae2
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422395"
---
# <a name="sizeof-c-reference"></a>sizeof (Referenční dokumentace jazyka C#)

Umožňuje získat velikost v bajtech pro nespravovaným typem.

Nespravované typy patří:

- Jednoduché typy, které jsou uvedeny v následující tabulce:

   |Výraz|Konstantní hodnota|
   |----------------|--------------------|
   |`sizeof(sbyte)`|1|
   |`sizeof(byte)`|1|
   |`sizeof(short)`|2|
   |`sizeof(ushort)`|2|
   |`sizeof(int)`|4|
   |`sizeof(uint)`|4|
   |`sizeof(long)`|8|
   |`sizeof(ulong)`|8|
   |`sizeof(char)`|2 (Unicode)|
   |`sizeof(float)`|4|
   |`sizeof(double)`|8|
   |`sizeof(decimal)`|16|
   |`sizeof(bool)`|1|

- Typy výčtu.

- Typy ukazatelů.

- Uživatelem definované struktury, které neobsahují žádné instance pole nebo vlastnosti automaticky implementované instance, které jsou odkazové typy nebo sestavené typy.

Následující příklad ukazuje, jak načíst velikost `int`:

```csharp
// Constant value 4:
int intSize = sizeof(int);
```

## <a name="remarks"></a>Poznámky

Od verze 2.0 jazyka C#, používání `sizeof` jednoduché nebo výčet typů již nevyžaduje zkompilovat kód ve [nebezpečné](unsafe.md) kontextu.

`sizeof` Operátor nelze přetížit. Hodnoty vrácené `sizeof` operátor jsou typu `int`. V předchozí tabulce jsou uvedeny konstantní hodnoty, které jsou substituovány za `sizeof` výrazy, které mají určité jednoduché typy jako operandy.

Pro všechny ostatní typy, včetně struktur, `sizeof` operátor lze použít pouze v nezabezpečené bloky kódu. Přestože lze použít <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> metoda, hodnota vrácená touto metodou není vždy stejná jako hodnota vrácená `sizeof`. <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> Vrátí velikost po typ byl zařazen, zatímco `sizeof` vrátí velikost tak, jak byl přidělen modulem common language runtime, včetně žádné odsazení.

## <a name="example"></a>Příklad

[!code-csharp[csrefKeywordsOperator#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#11)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [enum](enum.md)
- [Nebezpečný kód a ukazatele](../../programming-guide/unsafe-code-pointers/index.md)
- [Struktury](../../programming-guide/classes-and-structs/structs.md)
- [Konstanty](../../programming-guide/classes-and-structs/constants.md)
