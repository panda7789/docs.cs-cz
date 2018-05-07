---
title: Typy ukazatelů (Průvodce programováním v C#)
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: cbc75a2ec6fe826cb192b1e8bef61c7295f13916
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="pointer-types-c-programming-guide"></a>Typy ukazatelů (Průvodce programováním v C#)

V nezabezpečeném kontextu lze jako konkrétní typ použít typ ukazatele, typ hodnoty nebo typ odkazu. Deklarace typu ukazatele má jednu z následujících forem:

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

Typ určený před `*` v ukazatel typu nazývá **referrent typu**. Některé z následujících typů může být typu referrent:

- Žádný typ, integrální: [sbyte](../../language-reference/keywords/sbyte.md), [bajtů](../../language-reference/keywords/byte.md), [krátké](../../language-reference/keywords/short.md), [ushort](../../language-reference/keywords/ushort.md), [int](../../language-reference/keywords/int.md), [Celé_číslo](../../language-reference/keywords/uint.md), [dlouho](../../language-reference/keywords/long.md), [ulong](../../language-reference/keywords/ulong.md).
- Všechny plovoucí typu bodu: [float](../../language-reference/keywords/float.md), [dvojité](../../language-reference/keywords/double.md).
- [Char](../../language-reference/keywords/char.md).
- [BOOL](../../language-reference/keywords/bool.md).
- [Decimal](../../language-reference/keywords/decimal.md).
- Všechny [výčtu](../../language-reference/keywords/enum.md) typu.
- Jakýkoli typ ukazatele. To umožňuje výrazy, jako `void**`.
- Jakýkoli typ struktury definované uživatelem, který obsahuje pouze pole nespravovaných typů.

Typy ukazatelů nedědí z [objekt](../../language-reference/keywords/object.md) a neexistují žádné převody mezi typy ukazatelů a `object`. Dále není pro ukazatele k dispozici podpora zabalení a rozbalení. Můžete však převádět mezi různými typy ukazatele, nebo mezi různými typy ukazatele a integrálními typy.

Při deklaraci většího počtu ukazatelů ve stejné deklaraci je spolu se základním typem zapsán pouze symbol hvězdičky (*). Nepoužívá se jako předpona u názvů jednotlivých ukazatelů. Příklad:

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

Ukazatel nemůže odkazovat na odkaz nebo na [struktura](../../language-reference/keywords/struct.md) obsahující odkazy, protože odkaz na objekt může být uvolnění z paměti i v případě, že ukazatel ukazovat na ni. Systém uvolňování paměti neukládá přehled o tom, zda na konkrétní objekt neodkazují některé typy ukazatele.

Hodnoty proměnné ukazatele typu `myType*` je adresa proměnné typu `myType`. Následují příklady deklarace typu ukazatele:

|Příklad|Popis|
|-------------|-----------------|
|`int* p`|`p` je zde ukazatel na celé číslo.|
|`int** p`|`p` je zde ukazatel na ukazatel na celé číslo.|
|`int*[] p`|`p` je jednorozměrná pole ukazatele na celá čísla.|
|`char* p`|`p` je zde ukazatel na char.|
|`void* p`|`p` je zde ukazatel na neznámého typu.|

Operátor dereference ukazatele * lze použít pro přístup k obsahu v umístění, na které odkazuje proměnná ukazatele. Předpokládejme například následující deklaraci:

```csharp
int* myVariable;
```

Výraz `*myVariable` označuje `int` proměnná najít na adrese obsažené v `myVariable`.

Existuje několik příkladů ukazatele v tématech [příkazu pevnou](../../language-reference/keywords/fixed-statement.md) a [převody ukazatele](../../programming-guide/unsafe-code-pointers/pointer-conversions.md). Následující příklad používá `unsafe` – klíčové slovo a `fixed` příkaz a ukazuje, jak se zvýší vnitřní ukazatel.  Tento kód spustíte vložením do funkce Main konzolové aplikace. Tyto příklady musí být zkompilovány s [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) sadu možností kompilátoru.

[!code-csharp[Using pointer types](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#5)]

Deferenční operátor nelze použít pro ukazatel typu `void*`. Můžete však použít přetypování neplatného ukazatele a převést jej na jiný typ ukazatele, a naopak.

Může být ukazatel `null`. Použití operátoru dereference na ukazatele null způsobí chování definované implementací.

Předávání ukazatele mezi metod může způsobit nedefinované chování. Vezměte v úvahu metodu, která vrací ukazatel na místní proměnné prostřednictvím `in`, `out`, nebo `ref` parametr nebo v důsledku funkce. Pokud byl ukazatel nastaven v pevném bloku, pak proměnná, na kterou odkazuje, již nemusí být pevně stanovená.

V následující tabulce je uveden seznam operátorů a příkazů, které mohou fungovat u ukazatelů v nezabezpečeném kontextu:

|Operátor/Příkaz|Použití|
|-------------------------|---------|
|*|Provádí dereferenci ukazatele.|
|->|Zpřístupňuje člen struktury prostřednictvím ukazatele.|
|[]|Indexuje ukazatel.|
|`&`|Získá adresu proměnné.|
|++ a --|Zvýší a sníží ukazatele.|
|+ a -|Provádí aritmetické operace ukazatele.|
|==,! =, \<, >, \<=, a > =|Porovnává ukazatele.|
|`stackalloc`|Přidělí paměť v zásobníku.|
|`fixed` Příkaz|Dočasně pevně stanoví proměnnou tak, aby bylo možné vyhledat její adresu.|

## <a name="c-language-specification"></a>Specifikace jazyka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také
 [Průvodce programováním v jazyce C#](../index.md)  
 [Nebezpečný kód a ukazatele](index.md)  
 [Převody ukazatele](pointer-conversions.md)  
 [Výrazy ukazatelů](pointer-expressions.md)  
 [Typy](../../language-reference/keywords/types.md)  
 [unsafe](../../language-reference/keywords/unsafe.md)  
 [fixed – příkaz](../../language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../language-reference/keywords/stackalloc.md)  
 [Zabalení a rozbalení](../types/boxing-and-unboxing.md)
