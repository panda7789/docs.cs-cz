---
title: Typy ukazatelů – C# Průvodce programováním
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: 4d0801cd81e00c84be278b44730058798b0acfa9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588192"
---
# <a name="pointer-types-c-programming-guide"></a>Typy ukazatelů (Průvodce programováním v C#)

V nezabezpečeném kontextu lze jako konkrétní typ použít typ ukazatele, typ hodnoty nebo typ odkazu. Deklarace typu ukazatele má jednu z následujících forem:

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

Typ zadaný před `*` v typu ukazatele se nazývá **typ referenční**. Typ referenční může být pouze [nespravovaný typ](../../language-reference/builtin-types/unmanaged-types.md) .

Typy ukazatelů nedědí z [objektu](../../language-reference/keywords/object.md) a neexistují žádné převody mezi typy ukazatelů a `object`. Dále není pro ukazatele k dispozici podpora zabalení a rozbalení. Můžete však převádět mezi různými typy ukazatele, nebo mezi různými typy ukazatele a integrálními typy.

Při deklaraci většího počtu ukazatelů ve stejné deklaraci je spolu se základním typem zapsán pouze symbol hvězdičky (*). Nepoužívá se jako předpona u názvů jednotlivých ukazatelů. Příklad:

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

Ukazatel nemůže odkazovat na odkaz nebo na [strukturu](../../language-reference/keywords/struct.md) , která obsahuje odkazy, protože odkaz na objekt může být uvolněn z paměti i v případě, že na něj odkazuje ukazatel. Systém uvolňování paměti neukládá přehled o tom, zda na konkrétní objekt neodkazují některé typy ukazatele.

Hodnota proměnné ukazatele typu `myType*` je adresa proměnné typu. `myType` Následují příklady deklarace typu ukazatele:

|Příklad|Popis|
|-------------|-----------------|
|`int* p`|`p`je ukazatel na celé číslo.|
|`int** p`|`p`je ukazatel na ukazatel na celé číslo.|
|`int*[] p`|`p`je jednorozměrné pole ukazatelů na celá čísla.|
|`char* p`|`p`je ukazatel na znak.|
|`void* p`|`p`je ukazatel na neznámý typ.|

Operátor dereference ukazatele * lze použít pro přístup k obsahu v umístění, na které odkazuje proměnná ukazatele. Předpokládejme například následující deklaraci:

```csharp
int* myVariable;
```

Výraz `*myVariable` `myVariable`označuje `int` proměnnou nalezenou na adrese obsažené v.

Existuje několik příkladů ukazatelů v tématech s [příkazy fixed](../../language-reference/keywords/fixed-statement.md) a [převody ukazatelů](./pointer-conversions.md). Následující příklad používá `unsafe` klíčové slovo `fixed` a příkaz a ukazuje, jak zvýšit vnitřní ukazatel.  Tento kód spustíte vložením do funkce Main konzolové aplikace. Tyto příklady musí být kompilovány pomocí sady možností kompilátoru [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) .

[!code-csharp[Using pointer types](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#5)]

Nemůžete použít operátor dereference na ukazatel typu `void*`. Můžete však použít přetypování neplatného ukazatele a převést jej na jiný typ ukazatele, a naopak.

Může to být `null`ukazatel. Použití operátoru dereference na ukazatele null způsobí chování definované implementací.

Předávání ukazatelů mezi metodami může způsobit nedefinované chování. Zvažte metodu, která vrací ukazatel na místní proměnnou prostřednictvím `in`parametru, `out`nebo `ref` jako výsledek funkce. Pokud byl ukazatel nastaven v pevném bloku, pak proměnná, na kterou odkazuje, již nemusí být pevně stanovená.

V následující tabulce je uveden seznam operátorů a příkazů, které mohou fungovat u ukazatelů v nezabezpečeném kontextu:

|Operátor/Příkaz|Použití|
|-------------------------|---------|
|`*`|Provádí dereferenci ukazatele.|
|`->`|Zpřístupňuje člen struktury prostřednictvím ukazatele.|
|`[]`|Indexuje ukazatel.|
|`&`|Získá adresu proměnné.|
|`++` a `--`|Zvýší a sníží ukazatele.|
|`+` a `-`|Provádí aritmetické operace ukazatele.|
|`==`, `!=` ,`<`, ,a`>` `<=``>=`|Porovnává ukazatele.|
|[`stackalloc`podnikatel](../../language-reference/operators/stackalloc.md)|Přidělí paměť v zásobníku.|
|[`fixed`vydá](../../language-reference/keywords/fixed-statement.md)|Dočasně pevně stanoví proměnnou tak, aby bylo možné vyhledat její adresu.|

Další informace o operátorech souvisejících s ukazateli naleznete v tématu [operátory související s ukazatelem](../../language-reference/operators/pointer-related-operators.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [typy ukazatelů](~/_csharplang/spec/unsafe-code.md#pointer-types) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Nebezpečný kód a ukazatele](index.md)
- [Převody ukazatele](pointer-conversions.md)
- [Typy](../../language-reference/keywords/types.md)
- [unsafe](../../language-reference/keywords/unsafe.md)
