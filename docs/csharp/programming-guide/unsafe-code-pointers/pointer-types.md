---
title: Typy ukazatelů – C# Průvodce programováním pro službu
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: 028497bbeae26ded126ba4d7ce459a6a85e0bcb5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61708818"
---
# <a name="pointer-types-c-programming-guide"></a>Typy ukazatelů (Průvodce programováním v C#)

V nezabezpečeném kontextu lze jako konkrétní typ použít typ ukazatele, typ hodnoty nebo typ odkazu. Deklarace typu ukazatele má jednu z následujících forem:

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

Typ určený před `*` na ukazatel typu nazývá **referenční typ**. Některé z následujících typů může být typu referenční:

- Libovolný integrální typ: [sbyte](../../language-reference/keywords/sbyte.md), [bajtů](../../language-reference/keywords/byte.md), [krátký](../../language-reference/keywords/short.md), [ushort](../../language-reference/keywords/ushort.md), [int](../../language-reference/keywords/int.md), [uint](../../language-reference/keywords/uint.md), [dlouhé](../../language-reference/keywords/long.md), [ulong](../../language-reference/keywords/ulong.md).
- Libovolný typ s plovoucí desetinnou čárkou: [float](../../language-reference/keywords/float.md), [double](../../language-reference/keywords/double.md).
- [Char](../../language-reference/keywords/char.md).
- [BOOL](../../language-reference/keywords/bool.md).
- [desetinné](../../language-reference/keywords/decimal.md).
- Žádné [výčtu](../../language-reference/keywords/enum.md) typu.
- Jakýkoli typ ukazatele. Díky tomu výrazy, jako `void**`.
- Jakýkoli typ struktury definované uživatelem, který obsahuje pouze pole nespravovaných typů.

Typy ukazatelů nedědí z [objekt](../../language-reference/keywords/object.md) a neexistuje žádná možnost převodu mezi typy ukazatelů a `object`. Dále není pro ukazatele k dispozici podpora zabalení a rozbalení. Můžete však převádět mezi různými typy ukazatele, nebo mezi různými typy ukazatele a integrálními typy.

Při deklaraci většího počtu ukazatelů ve stejné deklaraci je spolu se základním typem zapsán pouze symbol hvězdičky (*). Nepoužívá se jako předpona u názvů jednotlivých ukazatelů. Příklad:

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

Ukazatel nemůže odkazovat na odkaz nebo do [struktura](../../language-reference/keywords/struct.md) , která obsahuje odkazy, protože odkaz na objekt může být uvolněn i v případě, že ukazatel odkazuje na ni. Systém uvolňování paměti neukládá přehled o tom, zda na konkrétní objekt neodkazují některé typy ukazatele.

Hodnota proměnné ukazatele typu `myType*` je adresa proměnné typu `myType`. Následují příklady deklarace typu ukazatele:

|Příklad|Popis|
|-------------|-----------------|
|`int* p`|`p` je ukazatel na celé číslo.|
|`int** p`|`p` je ukazatel na ukazatel na celé číslo.|
|`int*[] p`|`p` je jednorozměrné pole ukazatelů na celá čísla.|
|`char* p`|`p` je ukazatel na znak.|
|`void* p`|`p` je ukazatel na neznámého typu.|

Operátor dereference ukazatele * lze použít pro přístup k obsahu v umístění, na které odkazuje proměnná ukazatele. Předpokládejme například následující deklaraci:

```csharp
int* myVariable;
```

Výraz `*myVariable` označuje `int` nalezenou v adrese obsažené v proměnné `myVariable`.

Existuje několik příkladů ukazatelů v tématech [fixed Statement](../../language-reference/keywords/fixed-statement.md) a [převody ukazatele](../../programming-guide/unsafe-code-pointers/pointer-conversions.md). V následujícím příkladu `unsafe` – klíčové slovo a `fixed` příkaz a ukazuje, jak zvýšení vnitřního ukazatele.  Tento kód spustíte vložením do funkce Main konzolové aplikace. Tyto příklady musí být kompilována s [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) sadu možností kompilátoru.

[!code-csharp[Using pointer types](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#5)]

Operátor dereference nelze použít na ukazatel typu `void*`. Můžete však použít přetypování neplatného ukazatele a převést jej na jiný typ ukazatele, a naopak.

Ukazatel může mít `null`. Použití operátoru dereference na ukazatele null způsobí chování definované implementací.

Předávání ukazatelů mezi metodami může způsobit nedefinované chování. Vezměte v úvahu, která vrací ukazatele místní proměnné prostřednictvím `in`, `out`, nebo `ref` parametr nebo jako výsledek funkce. Pokud byl ukazatel nastaven v pevném bloku, pak proměnná, na kterou odkazuje, již nemusí být pevně stanovená.

V následující tabulce je uveden seznam operátorů a příkazů, které mohou fungovat u ukazatelů v nezabezpečeném kontextu:

|Operátor/Příkaz|Použití|
|-------------------------|---------|
|*|Provádí dereferenci ukazatele.|
|->|Zpřístupňuje člen struktury prostřednictvím ukazatele.|
|[]|Indexuje ukazatel.|
|`&`|Získá adresu proměnné.|
|++ a --|Zvýší a sníží ukazatele.|
|+ a -|Provádí aritmetické operace ukazatele.|
|==,! =, \<, >, \<= a > =|Porovnává ukazatele.|
|`stackalloc`|Přidělí paměť v zásobníku.|
|`fixed` – Příkaz|Dočasně pevně stanoví proměnnou tak, aby bylo možné vyhledat její adresu.|

## <a name="c-language-specification"></a>Specifikace jazyka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Nebezpečný kód a ukazatele](index.md)
- [Převody ukazatele](pointer-conversions.md)
- [Výrazy ukazatelů](pointer-expressions.md)
- [Typy](../../language-reference/keywords/types.md)
- [unsafe](../../language-reference/keywords/unsafe.md)
- [fixed – příkaz](../../language-reference/keywords/fixed-statement.md)
- [stackalloc](../../language-reference/keywords/stackalloc.md)
- [Zabalení a rozbalení](../types/boxing-and-unboxing.md)
