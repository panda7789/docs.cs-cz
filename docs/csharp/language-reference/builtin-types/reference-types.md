---
title: Předdefinované typy odkazů – C# referenční informace
description: Přečtěte si informace o typech C# odkazů, které mají klíčová slova, která můžete použít k jejich deklaraci.
ms.date: 06/25/2019
f1_keywords:
- object_CSharpKeyword
- object
- delegate_CSharpKeyword
- delegate
- dynamic_CSharpKeyword
- string
- string_CSharpKeyword
helpviewer_keywords:
- object keyword [C#]
- delegate keyword [C#]
- function pointers [C#]
- dynamic [C#]
- dynamic keyword [C#]
- strings [C#], reference
- '@ string literal'
- string literals [C#]
- string keyword [C#]
ms.openlocfilehash: d8858acb2743b26cc3a5172edf4765976d81adf4
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973018"
---
# <a name="built-in-reference-types-c-reference"></a>Předdefinované typy odkazů (C# referenční)

C#má několik předdefinovaných typů odkazů. Mají klíčová slova nebo operátory, které jsou synonyma pro typ v knihovně .NET. 

## <a name="the-object-type"></a>Typ objektu

`object` typ je alias pro <xref:System.Object?displayProperty=nameWithType> v rozhraní .NET. V rámci sjednoceného typu systému C#jsou všechny typy, předdefinované a uživatelsky definované typy odkazů a typy hodnot děděny přímo nebo nepřímo z <xref:System.Object?displayProperty=nameWithType>. K proměnným typu `object`můžete přiřadit hodnoty libovolného typu. K výchozí hodnotě lze pomocí `null`literálů přiřadit jakoukoli `object` proměnnou. Když je proměnná typu hodnoty převedena na typ Object, je označována jako *zabalená*. Je-li proměnná typu Object převedena na typ hodnoty, je označována jako *nezabaleno*. Další informace naleznete v tématu [zabalení a rozbalení](../../programming-guide/types/boxing-and-unboxing.md). 

## <a name="the-string-type"></a>Typ řetězce

Typ `string` představuje sekvenci nula nebo více znaků Unicode. `string` je alias pro <xref:System.String?displayProperty=nameWithType> v rozhraní .NET.

I když je `string` odkazový typ, [operátory rovnosti `==` a `!=`](../operators/equality-operators.md#string-equality) jsou definovány pro porovnání hodnot `string` objektů, nikoli odkazů. Díky tomu je testování rovnosti řetězců intuitivnější. Příklad:

```csharp-interactive
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine(object.ReferenceEquals(a, b));
```

Zobrazí se hodnota "true" a potom "false", protože obsah řetězců je ekvivalentní, ale `a` a `b` neodkazují na stejnou instanci řetězce.

[Operátor +](../operators/addition-operator.md#string-concatenation) zřetězí řetězce:

```csharp
string a = "good " + "morning";
```

Tím se vytvoří objekt String, který obsahuje "Dobré ráno".

Řetězce jsou *neměnné*– obsah objektu String nelze po vytvoření objektu změnit, i když se syntaxe zobrazí jako v případě, že to můžete provést. Například při psaní tohoto kódu kompilátor ve skutečnosti vytvoří nový objekt String pro uložení nové sekvence znaků a tento nový objekt je přiřazen `b`. Paměť, která byla přidělena pro `b` (je-li obsažena v řetězci "h"), je pak způsobila pro uvolňování paměti.

```csharp
string b = "h";
b += "ello";
```

[Operátor](../operators/member-access-operators.md#indexer-operator-) `[]` lze použít pro přístup jen pro čtení k jednotlivým znakům `string`. Platné hodnoty začínají na `0` a musí být menší než délka `string`:

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

Podobným způsobem lze operátor `[]` použít také k iterování každého znaku v `string`:

```csharp-interactive
string str = "test";

for (int i = 0; i < str.Length; i++)
{
  Console.Write(str[i] + " ");
}
// Output: t e s t
``` 

Řetězcové literály jsou typu `string` a lze je zapsat ve dvou formulářích, v uvozovkách a `@`. Řetězcové literály v uvozovkách jsou uzavřeny v uvozovkách ("):

```csharp
"good morning"  // a string literal
```

Řetězcové literály můžou obsahovat libovolný znakový literál. K dispozici jsou řídicí sekvence. Následující příklad používá řídicí sekvenci `\\` pro zpětné lomítko, `\u0066` pro písmeno f a `\n` pro nový řádek.

```csharp-interactive
string a = "\\\u0066\n F";
Console.WriteLine(a);
\\ Output:
\\ \f
\\  F
```

> [!NOTE]
> Řídicí kód `\udddd` (kde `dddd` je číslo se čtyřmi číslicemi) představuje znak Unicode U +`dddd`. Rozpoznávají se také osmimístného kódů Escape Unicode: `\Udddddddd`.

[Doslovné řetězce literálů](../tokens/verbatim.md) začínají `@` a jsou také uzavřeny v uvozovkách. Příklad:

```csharp
@"good morning"  // a string literal
```

Výhodou doslovného řetězce je, že řídicí sekvence *nejsou zpracovávány* , což usnadňuje psaní, například plně kvalifikovaného názvu souboru systému Windows:

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

Pokud chcete do řetězce @-quoted přidat dvojitou uvozovku, poklikejte na ni:

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

## <a name="the-delegate-type"></a>Typ delegáta

Deklarace typu delegáta je podobná podpisu metody. Má návratovou hodnotu a libovolný počet parametrů libovolného typu:

```csharp
public delegate void MessageDelegate(string message);
public delegate int AnotherDelegate(MyType m, long num);
```

V rozhraní .NET typy `System.Action` a `System.Func` poskytují obecné definice pro mnoho běžných delegátů. Pravděpodobně nebudete muset definovat nové vlastní typy delegátů. Místo toho můžete vytvořit instance poskytnutých obecných typů.

`delegate` je odkazový typ, který lze použít k zapouzdření pojmenované nebo anonymní metody. Delegáti jsou podobní ukazatelům funkcí C++v nástroji; Delegáti jsou však typově bezpečné a zabezpečené. Pro aplikace delegátů, přečtěte si téma [Delegáti](../../programming-guide/delegates/index.md) a [Obecné delegáty](../../programming-guide/generics/generic-delegates.md). Delegáti jsou základem pro [události](../../programming-guide/events/index.md). Pro delegáta se dá vytvořit instance, a to tak, že ho přidružíte k pojmenované nebo anonymní metodě.

Pro delegáta musí být vytvořená metoda nebo lambda výraz, který má kompatibilní návratový typ a vstupní parametry. Další informace o stupni odchylky, která je povolena v signatuře metody, naleznete v tématu [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md). Pro použití s anonymními metodami, delegát a kód, který je k němu přidružen, jsou deklarovány společně. 

## <a name="the-dynamic-type"></a>Dynamický typ

Typ `dynamic` označuje, že použití proměnné a odkazů na její členy vynechává kontrolu typu při kompilaci. Místo toho se tyto operace vyřeší za běhu. Typ `dynamic` zjednodušuje přístup k rozhraním API modelu COM, jako jsou rozhraní API služby Office Automation, k dynamickým rozhraním API, jako jsou knihovny Ironpythonu, a k HTML model DOM (Document Object Model) (DOM).

Typ `dynamic` se ve většině případů chová jako typ `object`. Konkrétně libovolný výraz, který není null, lze převést na typ `dynamic`. Typ `dynamic` se liší od `object` v tom, že operace obsahující výrazy typu `dynamic` nejsou vyřešeny nebo typu kontrolovaném kompilátorem. Kompilátor balí informace o operaci a tyto informace jsou později použity k vyhodnocení operace v době běhu. Jako součást procesu jsou proměnné typu `dynamic` kompilovány do proměnných typu `object`. Proto typ `dynamic` existuje pouze v době kompilace, nikoli v době běhu.

Následující příklad kontrastuje proměnnou typu `dynamic` na proměnnou typu `object`. Chcete-li ověřit typ každé proměnné v době kompilace, umístěte ukazatel myši nad `dyn` nebo `obj` v příkazech `WriteLine`. Zkopírujte následující kód do editoru, kde je k dispozici technologie IntelliSense. IntelliSense zobrazí **dynamickou** pro `dyn` a **objekt** pro `obj`.

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

Příkazy <xref:System.Console.WriteLine%2A> zobrazují běhové typy `dyn` a `obj`. V tomto okamžiku oba mají stejný typ Integer. Vytvoří se následující výstup:

```console
System.Int32
System.Int32
```

Chcete-li zobrazit rozdíl mezi `dyn` a `obj` v době kompilace, přidejte následující dva řádky mezi deklaracemi a příkazy `WriteLine` v předchozím příkladu.

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 Chyba kompilátoru je hlášena při pokusu o přidání celého čísla a objektu ve výrazu `obj + 3`. Pro `dyn + 3`však není hlášena žádná chyba. Výraz obsahující `dyn` není kontrolován v době kompilace, protože typ `dyn` je `dynamic`.

Následující příklad používá `dynamic` v několika deklaracích. Metoda `Main` také kontrastí kontrolu typu při kompilaci s kontrolou typu za běhu.

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

### <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Klíčová slova jazyka C#](../keywords/index.md)
- [Události](../../programming-guide/events/index.md)
- [Použití typu dynamic](../../programming-guide/types/using-type-dynamic.md)
- [Doporučené postupy pro používání řetězců](../../../standard/base-types/best-practices-strings.md)
- [Základní operace s řetězci](../../../standard/base-types/basic-string-operations.md)
- [Vytváření nových řetězců](../../../standard/base-types/creating-new.md)
- [Operátory testování typů a přetypování](../operators/type-testing-and-cast.md)
- [Jak bezpečně přetypovat pomocí porovnávání vzorů a operátorů as a is](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [Návod: vytváření a používání dynamických objektů](../../programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- <xref:System.Object?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
