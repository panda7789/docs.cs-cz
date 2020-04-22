---
title: Typy struktur – odkaz jazyka C#
ms.date: 04/21/2020
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- struct type [C#]
- structure type [C#]
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: dbe9b47625589de834b7a8021640885ca0920b96
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "82021274"
---
# <a name="structure-types-c-reference"></a>Typy struktur (odkaz C#

*Typ struktury* (nebo *typ struktury*) je [typ hodnoty,](value-types.md) který může zapouzdřit data a související funkce. `struct` Klíčové slovo slouží k definování typu struktury:

[!code-csharp[struct example](snippets/StructType.cs#StructExample)]

Typy struktur mají *hodnotu sémantiku*. To znamená, že proměnná typu struktury obsahuje instanci typu. Ve výchozím nastavení jsou hodnoty proměnných zkopírovány při přiřazení, předání argumentu metodě a vrácení výsledku metody. V případě proměnné typu struktura je zkopírována instance typu. Další informace naleznete v [tématu Value types](value-types.md).

Obvykle se používají typy struktury k návrhu malé typy zaměřené na data, které poskytují malé nebo žádné chování. Například .NET používá typy struktury představují číslo [(celé číslo](integral-numeric-types.md) i [skutečné](floating-point-numeric-types.md)), [logická hodnota](bool.md), [znak Unicode](char.md), [instance time](xref:System.DateTime). Pokud se zaměřujete na chování typu, zvažte definování [třídy](../keywords/class.md). Typy tříd mají *referenční sémantiku*. To znamená, že proměnná typu třídy obsahuje odkaz na instanci typu, nikoli samotnou instanci.

Vzhledem k tomu, že typy struktur mají hodnotovou sémantiku, doporučujeme definovat *neměnné* typy struktur.

## <a name="readonly-struct"></a>`readonly`Struct

Počínaje C# 7.2, pomocí `readonly` modifikátoru deklarovat, že typ struktury je neměnný:

[!code-csharp[readonly struct](snippets/StructType.cs#ReadonlyStruct)]

Všechny datové členy `readonly` struktury musí být jen pro čtení takto:

- Každá deklarace pole musí mít [ `readonly` modifikátor.](../keywords/readonly.md)
- Každá vlastnost, včetně automaticky implementovaných, musí být jen pro čtení

To zaručuje, že žádný `readonly` člen struktury modifikuje stav struktury.

> [!NOTE]
> Ve `readonly` struktuře může datový člen proměnlivého typu odkazu stále zmutovat svůj vlastní stav. Například nelze nahradit <xref:System.Collections.Generic.List%601> instanci, ale můžete do ní přidat nové prvky.

## <a name="readonly-instance-members"></a>`readonly`členové instance

Počínaje C# 8.0, můžete také `readonly` použít modifikátor deklarovat, že člen instance nemění stav struktury. Pokud nemůžete deklarovat celý `readonly`typ struktury `readonly` jako , použijte modifikátor označit členy instance, které nemění stav struktury. Ve `readonly` struktuře je každý člen `readonly`instance implicitně .

V `readonly` rámci člena instance nelze přiřadit pole instance struktury. `readonly` Člen však může volat`readonly` nečlena. V takovém případě kompilátor vytvoří kopii instance struktury`readonly` a volá nečlen na této kopii. V důsledku toho původní instance struktury není změněn.

`readonly` Modifikátor obvykle použijete na následující druhy členů instance:

- Metody:

  [!code-csharp[readonly method](snippets/StructType.cs#ReadonlyMethod)]

  `readonly` Modifikátor můžete také použít na metody, <xref:System.Object?displayProperty=nameWithType>které přepíší metody deklarované v :

  [!code-csharp[readonly override](snippets/StructType.cs#ReadonlyOverride)]

- vlastnosti a indexery:

  [!code-csharp[readonly property get](snippets/StructType.cs#ReadonlyProperty)]

  Pokud potřebujete použít `readonly` modifikátor pro oba přístupové objekty vlastnosti nebo indexeru, použijte jej v deklaraci vlastnosti nebo indexeru.

  > [!NOTE]
  > Kompilátor deklaruje `get` přistupující `readonly`objekt automaticky [implementované vlastnosti](../../programming-guide/classes-and-structs/auto-implemented-properties.md) jako , bez ohledu na přítomnost `readonly` modifikátoru v deklaraci vlastnosti.

`readonly` Modifikátor nelze použít na statické členy typu struktury.

Kompilátor může použít `readonly` modifikátor pro optimalizace výkonu. Další informace naleznete v [tématu Zápis bezpečné a efektivní kód jazyka C#](../../write-safe-efficient-code.md).

## <a name="limitations-with-the-design-of-a-structure-type"></a>Omezení s návrhem typu konstrukce

Při návrhu typu struktury máte stejné možnosti jako u typu [třídy,](../keywords/class.md) s následujícími výjimkami:

- Nelze deklarovat konstruktor bez parametrů. Každý typ struktury již poskytuje implicitní konstruktor bez parametrů, který vytváří [výchozí hodnotu](default-values.md) typu.

- Pole nebo vlastnost instance nelze inicializovat v jeho deklaraci. Můžete však inicializovat [statické](../keywords/static.md) nebo [const](../keywords/const.md) pole nebo statické vlastnosti na jeho deklaraci.

- Konstruktor typu struktury musí inicializovat všechna pole instance typu.

- Typ struktury nemůže dědit z jiné třídy nebo typu struktury a nemůže být základem třídy. Typ struktury však může implementovat [rozhraní](../keywords/interface.md).

- Finalizační [metodu](../../programming-guide/classes-and-structs/destructors.md) nelze deklarovat v rámci typu struktury.

## <a name="instantiation-of-a-structure-type"></a>Vytvoření instance typu struktury

V C# je nutné inicializovat deklarované proměnné před ji lze použít. Vzhledem k tomu, že `null` proměnná typu struktury nemůže být (pokud se nejedná o proměnnou [typu hodnoty s možnou hodnotou s možnou hodnotou),](nullable-value-types.md)je nutné vytvořit instanci odpovídajícího typu. Existuje několik způsobů, jak to udělat.

Obvykle konsitujete typ struktury voláním příslušného [`new`](../operators/new-operator.md) konstruktoru s operátorem. Každý typ struktury má alespoň jeden konstruktor. To je implicitní konstruktor bez parametrů, který vytváří [výchozí hodnotu](default-values.md) typu. Výchozí [výraz hodnoty](../operators/default.md) můžete také použít k vytvoření výchozí hodnoty typu.

Pokud jsou přístupná všechna pole instance typu struktury, můžete ji `new` také vytvořit bez operátora. V takovém případě je nutné inicializovat všechna pole instance před prvním použitím instance. Následující příklad ukazuje, jak to udělat:

[!code-csharp[without new](snippets/StructType.cs#WithoutNew)]

V případě [předdefinovaných typů hodnot](value-types.md#built-in-value-types)použijte odpovídající literály k určení hodnoty typu.

## <a name="passing-structure-type-variables-by-reference"></a>Předávání proměnných typu struktury odkazem

Když předáte proměnnou typu struktury metodě jako argument nebo vrátíte hodnotu typu struktury z metody, zkopíruje se celá instance typu struktury. To může ovlivnit výkon kódu ve scénářích s vysokým výkonem, které zahrnují velké typy struktur. Kopírování hodnot se můžete vyhnout předáním proměnné typu struktury odkazem. Modifikátory parametrů [`ref`](../keywords/ref.md#passing-an-argument-by-reference), [`out`](../keywords/out-parameter-modifier.md)nebo [`in`](../keywords/in-parameter-modifier.md) metody označují, že argument musí být předán odkazem. Použijte [ref vrátí](../../programming-guide/classes-and-structs/ref-returns.md) výsledek metody odkazem. Další informace naleznete v [tématu Zápis bezpečné a efektivní kód jazyka C#](../../write-safe-efficient-code.md).

## <a name="ref-struct"></a>`ref`Struct

Počínaje C# 7.2, můžete `ref` použít modifikátor v deklaraci typu struktury. Instance `ref` typu struktury jsou přiděleny v zásobníku a nelze uniknout spravované haldy. Aby bylo zajištěno, že kompilátor omezuje použití `ref` typy struktury takto:

- Struktura `ref` nemůže být typ prvku pole.
- Struktura `ref` nemůže být deklarovaný typ pole třídy nebo`ref` non-struct.
- Struktura `ref` nemůže implementovat rozhraní.
- Struktura `ref` nemůže být zabalena nebo <xref:System.ValueType?displayProperty=nameWithType> <xref:System.Object?displayProperty=nameWithType>.
- Struktura `ref` nemůže být argument typu.
- Proměnnou `ref` struktury nelze zachytit [výrazem lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) nebo [místní funkcí](../../programming-guide/classes-and-structs/local-functions.md).
- Proměnnou `ref` struktury nelze použít v [`async`](../keywords/async.md) metodě. Proměnné struktury však můžete použít `ref` v synchronních metodách, například <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601>v těch, které vracejí nebo .
- Proměnnou `ref` struktury nelze použít v [iterátorech](../../iterators.md).

Typ `ref` struktury obvykle definujete, když potřebujete typ, který zahrnuje `ref` také datové členy typů struktury:

[!code-csharp[ref struct](snippets/StructType.cs#RefStruct)]

Chcete-li `ref` deklarovat strukturu jako [`readonly`](#readonly-struct), zkombinujte modifikátory `readonly` a `ref` `ref` v deklaraci typu `readonly` (modifikátor musí být před modifikátorem):

[!code-csharp[readonly ref struct](snippets/StructType.cs#ReadonlyRef)]

V rozhraní .NET jsou `ref` <xref:System.Span%601?displayProperty=nameWithType> příklady <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>struktury a .

## <a name="conversions"></a>Převody

Pro všechny typy struktury (s <xref:System.ValueType?displayProperty=nameWithType> výjimkou <xref:System.Object?displayProperty=nameWithType> [ `ref` ](#ref-struct) typů struktury) existují převody [zabalení a rozbalení](../../programming-guide/types/boxing-and-unboxing.md) do a z a typy a. Existují také zabalení a rozbalení převody mezi typ struktury a rozhraní, které implementuje.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [Structs](~/_csharplang/spec/structs.md) ve [specifikaci jazyka C#](~/_csharplang/spec/introduction.md).

Další informace o funkcích zavedených v c# 7.2 a novějších naleznete v následujících poznámkách k návrhu funkce:

- [Struktury jen pro čtení](~/_csharplang/proposals/csharp-7.2/readonly-ref.md#readonly-structs)
- [Členy instance Readonly](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)
- [Zabezpečení typů ref-like za kompilace](~/_csharplang/proposals/csharp-7.2/span-safety.md)

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Pokyny pro návrh - Výběr mezi třídou a strukturou](../../../standard/design-guidelines/choosing-between-class-and-struct.md)
- [Pokyny pro návrh - Design Struct](../../../standard/design-guidelines/struct.md)
- [Třídy a struktury](../../programming-guide/classes-and-structs/index.md)
