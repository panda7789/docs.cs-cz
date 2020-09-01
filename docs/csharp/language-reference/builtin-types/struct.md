---
description: 'Další informace o typu struktury v jazyce C #'
title: Typy struktur – reference jazyka C#
ms.date: 04/21/2020
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- struct type [C#]
- structure type [C#]
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 7f3940ce487b9e382150234f317cf1dba34bb060
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89132726"
---
# <a name="structure-types-c-reference"></a>Typy struktury (Referenční dokumentace jazyka C#)

*Typ struktury* (nebo *typ struktury*) je [typ hodnoty](value-types.md) , který může zapouzdřit data a související funkce. `struct`Klíčové slovo lze použít k definování typu struktury:

[!code-csharp[struct example](snippets/StructType.cs#StructExample)]

Typy struktur mají *sémantiku hodnot*. To znamená, že proměnná typu struktury obsahuje instanci typu. Ve výchozím nastavení jsou proměnné hodnoty zkopírovány při přiřazení, předání argumentu metodě a vrácení výsledku metody. V případě proměnné typu struktury je zkopírována instance typu. Další informace naleznete v tématu [typy hodnot](value-types.md).

Pro návrh malých typů orientovaných na data, které poskytují pouze malé nebo žádné chování, je obvykle používán typ struktury. Například .NET používá typy struktury k reprezentaci čísla ( [Integer](integral-numeric-types.md) i [reálné](floating-point-numeric-types.md)), [logické hodnoty](bool.md), [znaku Unicode](char.md), [instance času](xref:System.DateTime). Pokud jste se zaměřili na chování typu, zvažte definování [třídy](../keywords/class.md). Typy tříd mají *sémantiku odkazů*. To znamená, že proměnná typu třídy obsahuje odkaz na instanci typu, nikoli na samotnou instanci.

Vzhledem k tomu, že typy struktury mají sémantiku hodnot, doporučujeme definovat *neměnné* typy struktury.

## <a name="readonly-struct"></a>`readonly` nemají

Počínaje jazykem C# 7,2 použijete `readonly` Modifikátor k deklaraci, že typ struktury je neměnný:

[!code-csharp[readonly struct](snippets/StructType.cs#ReadonlyStruct)]

Všechna data členů `readonly` struktury musí být jen pro čtení, jak je znázorněno níže:

- Jakákoli deklarace pole musí mít [ `readonly` Modifikátor](../keywords/readonly.md) .
- Jakákoli vlastnost, včetně automaticky implementovaných, musí být jen pro čtení.

To zaručuje, že žádný člen `readonly` struktury nemění stav struktury. V jazyce C# 8,0 a novějším to znamená, že další členy instance s výjimkou konstruktorů jsou implicitně [`readonly`](#readonly-instance-members) .

> [!NOTE]
> V rámci `readonly` struktury může být datový člen proměnlivého typu odkazu stále v jeho vlastním stavu. Například nelze nahradit <xref:System.Collections.Generic.List%601> instanci, ale do ní můžete přidat nové prvky.

## <a name="readonly-instance-members"></a>`readonly` členy instance

Počínaje jazykem C# 8,0 můžete také použít `readonly` Modifikátor k deklaraci, že člen instance neupravuje stav struktury. Pokud nemůžete deklarovat typ celé struktury jako `readonly` , použijte `readonly` Modifikátor k označení členů instance, které nemění stav struktury.

V rámci `readonly` člena instance nelze přiřadit pole instance struktury. `readonly`Člen však může volat `readonly` nečlen. V takovém případě kompilátor vytvoří kopii instance struktury a zavolá do `readonly` této kopie nečlen. V důsledku toho se původní instance struktury nezmění.

Obvykle použijete `readonly` modifikátor pro následující typy členů instance:

- způsobů

  [!code-csharp[readonly method](snippets/StructType.cs#ReadonlyMethod)]

  Můžete také použít `readonly` Modifikátor na metody, které přepisují metody deklarované v <xref:System.Object?displayProperty=nameWithType> :

  [!code-csharp[readonly override](snippets/StructType.cs#ReadonlyOverride)]

- vlastnosti a indexery:

  [!code-csharp[readonly property get](snippets/StructType.cs#ReadonlyProperty)]

  Pokud potřebujete použít `readonly` modifikátor u přístupových objektů vlastnosti nebo indexeru, použijte ji v deklaraci vlastnosti nebo indexeru.

  > [!NOTE]
  > Kompilátor deklaruje `get` přistupující objekt pro [automaticky implementovanou vlastnost](../../programming-guide/classes-and-structs/auto-implemented-properties.md) jako `readonly` , bez ohledu na přítomnost `readonly` modifikátoru v deklaraci vlastnosti.

Nemůžete použít `readonly` modifikátor u statických členů typu struktury.

Kompilátor může využít `readonly` modifikátor pro optimalizace výkonu. Další informace najdete v tématu [Zápis bezpečného a efektivního kódu v jazyce C#](../../write-safe-efficient-code.md).

## <a name="limitations-with-the-design-of-a-structure-type"></a>Omezení s návrhem typu struktury

Při návrhu typu struktury máte stejné možnosti jako u typu [třídy](../keywords/class.md) , s následujícími výjimkami:

- Nemůžete deklarovat konstruktor bez parametrů. Každý typ struktury již poskytuje implicitní konstruktor bez parametrů, který vytváří [výchozí hodnotu](default-values.md) typu.

- V deklaraci nelze inicializovat pole instance nebo vlastnost. V deklaraci ale můžete inicializovat [statické](../keywords/static.md) nebo [konstantní](../keywords/const.md) pole nebo statickou vlastnost.

- Konstruktor typu struktury musí inicializovat všechna pole instance daného typu.

- Typ struktury nemůže dědit z jiné třídy nebo typu struktury a nemůže být základem třídy. Typ struktury však může implementovat [rozhraní](../keywords/interface.md).

- Nelze deklarovat [finalizační metodu](../../programming-guide/classes-and-structs/destructors.md) v rámci typu struktury.

## <a name="instantiation-of-a-structure-type"></a>Vytvoření instance typu struktury

V jazyce C# je nutné inicializovat deklarovanou proměnnou předtím, než bude možné ji použít. Vzhledem k tomu, že proměnná typu struktury nemůže být (Pokud se nejedná o `null` proměnnou [typu hodnoty s možnou hodnotou null](nullable-value-types.md)), je nutné vytvořit instanci odpovídajícího typu. To lze provést několika způsoby.

Obvykle vytváříte instanci typu struktury voláním vhodného konstruktoru s [`new`](../operators/new-operator.md) operátorem. Každý typ struktury má alespoň jeden konstruktor. To je implicitní konstruktor bez parametrů, který vytváří [výchozí hodnotu](default-values.md) typu. Výchozí hodnotu typu můžete vytvořit také pomocí [výchozího výrazu hodnoty](../operators/default.md) .

Pokud jsou všechna pole instance typu struktury dostupná, můžete také vytvořit instanci bez `new` operátoru. V takovém případě je nutné inicializovat všechna pole instance před prvním použitím instance. Následující příklad ukazuje, jak to provést:

[!code-csharp[without new](snippets/StructType.cs#WithoutNew)]

V případě [předdefinovaných hodnotových typů](value-types.md#built-in-value-types)použijte odpovídající literály k určení hodnoty typu.

## <a name="passing-structure-type-variables-by-reference"></a>Předávání proměnných typu struktury podle odkazu

Pokud předáte proměnnou typu struktury do metody jako argument nebo vrátíte hodnotu typu struktury z metody, je zkopírována celá instance typu struktury. To může mít vliv na výkon vašeho kódu ve scénářích s vysokým výkonem, které zahrnují typy velkých struktur. Kopírování hodnot se můžete vyhnout předáním proměnné typu struktury odkazem. Použijte [`ref`](../keywords/ref.md#passing-an-argument-by-reference) [`out`](../keywords/out-parameter-modifier.md) [`in`](../keywords/in-parameter-modifier.md) modifikátory parametrů metody, nebo, aby označovaly, že argument musí být předán odkazem. Pomocí [funkce ref](../../programming-guide/classes-and-structs/ref-returns.md) Return můžete vrátit výsledek metody odkazem. Další informace najdete v tématu [Zápis bezpečného a efektivního kódu v jazyce C#](../../write-safe-efficient-code.md).

## <a name="ref-struct"></a>`ref` nemají

Počínaje jazykem C# 7,2 můžete použít `ref` Modifikátor v deklaraci typu struktury. Instance `ref` typu struktury jsou přiděleny v zásobníku a nemohou uniknout do spravované haldy. Aby bylo zajištěno, že kompilátor omezuje využití `ref` typů struktury následujícím způsobem:

- `ref`Struktura nemůže být typem elementu pole.
- `ref`Struktura nemůže být deklarovaného typu pro pole třídy nebo bez `ref` struktury.
- `ref`Struktura nemůže implementovat rozhraní.
- `ref`Struktura nemůže být zabalená do <xref:System.ValueType?displayProperty=nameWithType> nebo <xref:System.Object?displayProperty=nameWithType> .
- `ref`Struktura nemůže být argumentem typu.
- `ref`Proměnná struktury nemůže být zachycena [výrazem lambda](../operators/lambda-expressions.md) nebo [místní funkcí](../../programming-guide/classes-and-structs/local-functions.md).
- `ref`V metodě nelze použít proměnnou struktury [`async`](../keywords/async.md) . Můžete však použít `ref` proměnné struktury v synchronních metodách, například v těch, které vracejí <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> .
- `ref`V [iterátorech](../../iterators.md)nelze použít proměnnou struktury.

Obvykle definujete `ref` typ struktury, pokud potřebujete typ, který také obsahuje datové členy `ref` typů struktur:

[!code-csharp[ref struct](snippets/StructType.cs#RefStruct)]

Deklarace `ref` struktury jako [`readonly`](#readonly-struct) , kombinování `readonly` `ref` modifikátorů a v deklaraci typu ( `readonly` modifikátor musí být před `ref` modifikátorem):

[!code-csharp[readonly ref struct](snippets/StructType.cs#ReadonlyRef)]

V rozhraní .NET `ref` jsou příklady struktury <xref:System.Span%601?displayProperty=nameWithType> a <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> .

## <a name="conversions"></a>Převody

Pro libovolný typ struktury (s výjimkou typů [ `ref` struktury](#ref-struct) ) existují převody [zabalení a rozbalení](../../programming-guide/types/boxing-and-unboxing.md) do a z <xref:System.ValueType?displayProperty=nameWithType> <xref:System.Object?displayProperty=nameWithType> typů a. Existují také převody zabalení a rozbalení mezi typem struktury a jakýmkoli rozhraním, které implementuje.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v oddílu [struktury](~/_csharplang/spec/structs.md) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

Další informace o funkcích zavedených v C# 7,2 a novějších verzích najdete v následujících poznámkách k návrhu funkcí:

- [Struktury jen pro čtení](~/_csharplang/proposals/csharp-7.2/readonly-ref.md#readonly-structs)
- [Členy instance Readonly](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)
- [Zabezpečení typů ref-like za kompilace](~/_csharplang/proposals/csharp-7.2/span-safety.md)

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Pokyny pro návrh – výběr mezi třídou a strukturou](../../../standard/design-guidelines/choosing-between-class-and-struct.md)
- [Pokyny pro návrh – návrh struktury](../../../standard/design-guidelines/struct.md)
- [Třídy a struktury](../../programming-guide/classes-and-structs/index.md)
