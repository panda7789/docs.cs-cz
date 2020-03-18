---
title: Typy ukazatelů – průvodce programováním jazyka C#
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: dc03744559a87a2548c5bee9452c22cd20f337b8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77627707"
---
# <a name="pointer-types-c-programming-guide"></a>Typy ukazatelů (Průvodce programováním v C#)

V nezabezpečeném kontextu lze jako konkrétní typ použít typ ukazatele, typ hodnoty nebo typ odkazu. Deklarace typu ukazatele má jednu z následujících forem:

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

Typ zadaný `*` před typem ukazatele v typu se nazývá **referenční typ**. Pouze [nespravovaný typ](../../language-reference/builtin-types/unmanaged-types.md) může být referenční typ.

Typy ukazatelů nedědí z [objektu](../../language-reference/builtin-types/reference-types.md) a neexistují `object`žádné převody mezi typy ukazatelů a . Dále není pro ukazatele k dispozici podpora zabalení a rozbalení. Můžete však převádět mezi různými typy ukazatele, nebo mezi různými typy ukazatele a integrálními typy.

Při deklaraci většího počtu ukazatelů ve stejné deklaraci je spolu se základním typem zapsán pouze symbol hvězdičky (*). Nepoužívá se jako předpona u názvů jednotlivých ukazatelů. Například:

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

Ukazatel nemůže odkazovat na odkaz nebo [strukturu,](../../language-reference/builtin-types/struct.md) která obsahuje odkazy, protože odkaz na objekt může být uvolněno i v případě, že na něj ukazuje ukazatel. Systém uvolňování paměti neukládá přehled o tom, zda na konkrétní objekt neodkazují některé typy ukazatele.

Hodnota proměnné ukazatele typu `myType*` je adresa proměnné typu `myType`. Následují příklady deklarace typu ukazatele:

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

Výraz `*myVariable` označuje proměnnou `int` nalezenou na adrese `myVariable`obsažené v aplikaci .

Existuje několik příkladů ukazatelů v tématech [pevné prohlášení](../../language-reference/keywords/fixed-statement.md) a [ukazatel převody](./pointer-conversions.md). Následující příklad používá `unsafe` klíčové `fixed` slovo a příkaz a ukazuje, jak se zpřímí vnitřní ukazatel.  Tento kód spustíte vložením do funkce Main konzolové aplikace. Tyto příklady musí být zkompilovány s [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler sada možností.

[!code-csharp[Using pointer types](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#5)]

Operátor dereference nelze použít na ukazatel `void*`typu . Můžete však použít přetypování neplatného ukazatele a převést jej na jiný typ ukazatele, a naopak.

Ukazatel může `null`být . Použití operátoru dereference na ukazatele null způsobí chování definované implementací.

Předávání ukazatelů mezi metodami může způsobit nedefinované chování. Zvažte metodu, která vrací ukazatel `in`na `out`místní `ref` proměnnou prostřednictvím , nebo parametr nebo jako výsledek funkce. Pokud byl ukazatel nastaven v pevném bloku, pak proměnná, na kterou odkazuje, již nemusí být pevně stanovená.

V následující tabulce je uveden seznam operátorů a příkazů, které mohou fungovat u ukazatelů v nezabezpečeném kontextu:

|Operátor/Příkaz|Použití|
|-------------------------|---------|
|`*`|Provádí dereferenci ukazatele.|
|`->`|Zpřístupňuje člen struktury prostřednictvím ukazatele.|
|`[]`|Indexuje ukazatel.|
|`&`|Získá adresu proměnné.|
|`++` a `--`|Zvýší a sníží ukazatele.|
|`+` a `-`|Provádí aritmetické operace ukazatele.|
|`==`, `!=` `<`, `>` `<=`, , a`>=`|Porovnává ukazatele.|
|[`stackalloc`Operátor](../../language-reference/operators/stackalloc.md)|Přidělí paměť v zásobníku.|
|[`fixed`Prohlášení](../../language-reference/keywords/fixed-statement.md)|Dočasně pevně stanoví proměnnou tak, aby bylo možné vyhledat její adresu.|

Další informace o operátorech souvisejících s ukazatelem naleznete v [tématu Ukazatele související operátory](../../language-reference/operators/pointer-related-operators.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [Typy ukazatelů](~/_csharplang/spec/unsafe-code.md#pointer-types) [ve specifikaci jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Nebezpečný kód a ukazatele](index.md)
- [Převody ukazatele](pointer-conversions.md)
- [Referenční typy](../../language-reference/keywords/reference-types.md)
- [Typy hodnot](../../language-reference/builtin-types/value-types.md)
- [unsafe](../../language-reference/keywords/unsafe.md)
