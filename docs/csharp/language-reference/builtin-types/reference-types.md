---
title: Vestavěné typy odkazu - C# odkaz
description: Seznamte se s typy odkazů, které mají C# klíčových slov můžete použít k deklaraci.
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
ms.openlocfilehash: 4bc93216d74e2732870e08edd4bdb9570391cf5f
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2019
ms.locfileid: "67877195"
---
# <a name="built-in-reference-types-c-reference"></a>Vestavěné typy odkazu (C# odkaz)

C#má řadu vestavěné typy odkazu. Mají klíčových slov nebo operátorů, které jsou synonyma pro typy v knihovně .NET. 

## <a name="the-object-type"></a>Typ objektu

`object` Typ je alias pro <xref:System.Object?displayProperty=nameWithType> v rozhraní .NET. V systému unified typů jazyka C#, všechny typy, typy odkazů předdefinovaných a definovaný uživatelem, a typů hodnot, dědí přímo nebo nepřímo <xref:System.Object?displayProperty=nameWithType>. Můžete přiřadit proměnné typu hodnoty libovolného typu `object`. Žádné `object` proměnné je možné přiřadit k jeho výchozí hodnotu literálu `null`. Když je proměnné typu hodnoty převeden na objekt, je označen jako *boxed*. Pokud proměnnou typu objektu je převeden na typ hodnoty, je označen jako *nezabalené*. Další informace najdete v tématu [zabalení a rozbalení](../../programming-guide/types/boxing-and-unboxing.md). 

## <a name="the-string-type"></a>Typ string

`string` Typ představuje posloupnost nula nebo více znaků Unicode. `string` je alias pro <xref:System.String?displayProperty=nameWithType> v rozhraní .NET.

I když `string` je typem odkazu [operátory rovnosti `==` a `!=` ](../operators/equality-operators.md#string-equality) jsou definovány pro porovnání hodnoty `string` objekty, ne odkazuje. Tím je testování rovnosti řetězců intuitivnější. Příklad:

```csharp-interactive
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine(object.ReferenceEquals(a, b));
```

Zobrazí "hodnotu True" a potom "False" protože obsah řetězce jsou ekvivalentní, ale `a` a `b` neodkazují na stejné instanci řetězce.

[+ – Operátor](../operators/addition-operator.md#string-concatenation) zřetězí řetězce:

```csharp
string a = "good " + "morning";
```

Tím se vytvoří objekt string obsahující "good morning".

Řetězce jsou *neměnné*– obsah řetězce objektu nelze změnit po vytvoření objektu, přestože je syntaxe zobrazí jako by tomu. Například při psaní tohoto kódu kompilátor ve skutečnosti vytváří nový objekt řetězce pro uchování nového posloupnost znaků, a tento nový objekt je přiřazen k `b`. Paměť, která kdyby byly přiděleny pro `b` (Pokud obsahovala řetězec "h") je pak nárok uvolňování paměti.

```csharp
string b = "h";
b += "ello";
```

`[]` [Operátor](../operators/member-access-operators.md#indexer-operator-) lze použít pro přístup jen pro čtení k jednotlivé znaky `string`. Platné hodnoty začínají `0` a musí být menší než délka `string`:

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

Podobně `[]` také lze použít operátor pro iterace přes každý znak v `string`:

```csharp-interactive
string str = "test";

for (int i = 0; i < str.Length; i++)
{
  Console.Write(str[i] + " ");
}
// Output: t e s t
``` 

Řetězcové literály jsou typu `string` a může být zapsaný ve dvou formách, v uvozovkách a `@`– v uvozovkách. Citovaný řetězec, který literály jsou uzavřeny v dvojitých uvozovkách ("):

```csharp
"good morning"  // a string literal
```

Řetězcové literály může obsahovat libovolný znak literálu. Řídicí sekvence jsou zahrnuty. Následující příklad používá řídicí sekvence `\\` pro zpětné lomítko, `\u0066` písmenem f, a `\n` pro nový řádek.

```csharp-interactive
string a = "\\\u0066\n F";
Console.WriteLine(a);
\\ Output:
\\ \f
\\  F
```

> [!NOTE]
> Řídicí kód `\udddd` (kde `dddd` je čtyřmístné číslo) představuje znak Unicode U +`dddd`. Osm číslice sady Unicode řídícími kódy jsou také rozpoznána: `\Udddddddd`.

[Literály doslovném řetězci](../tokens/verbatim.md) začínat `@` a jsou také uzavřen do dvojitých uvozovek. Příklad:

```csharp
@"good morning"  // a string literal
```

Výhodou doslovném řetězci je, že řídicí sekvence jsou *není* zpracování, což usnadňuje zapsat, například plně kvalifikovaný název souboru Windows:

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

Zahrnout dvojitých uvozovek na @-quoted řetězec, uveďte ji dvakrát:

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

## <a name="the-delegate-type"></a>Typ delegáta

Deklarace typu delegáta je podobná signatuře metody. Nemá návratovou hodnotu a libovolný počet parametrů typu:

```csharp
public delegate void MessageDelegate(string message);
public delegate int AnotherDelegate(MyType m, long num);
```

V rozhraní .NET `System.Action` a `System.Func` typy poskytují obecné definice pro mnoho běžných delegátů. Pravděpodobně není nutné definovat nové typy vlastního delegáta. Místo toho můžete vytvořit konkretizací poskytnutých obecných typů.

A `delegate` je typem odkazu, který můžete použít k zapouzdření pojmenovaná nebo anonymní metodu. Delegáti jsou podobní ukazatelům na funkci v jazyce C++; Delegáti jsou však typově bezpečné a zabezpečené. Aplikace delegátů viz [delegáti](../../programming-guide/delegates/index.md) a [obecných delegátů](../../programming-guide/generics/generic-delegates.md). Delegáti jsou základem [události](../../programming-guide/events/index.md). Delegát může být vytvořena tím, že přidružíte buď pomocí pojmenovaných nebo anonymní metodu.

Delegát musí být vytvořena pomocí metody nebo lambda výraz, který je kompatibilní návratový typ a vstupní parametry. Další informace o stupeň odchylky, který je povolen v podpisu metody, naleznete v tématu [odchylky v delegátech](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md). Pro použití s anonymní metody delegáta a kód k ní být přidruženo jsou deklarovány společně. 

## <a name="the-dynamic-type"></a>Dynamický typ.

`dynamic` Typ Určuje, které používají proměnné a odkazy na jeho kontrola typu v době kompilace členy jednorázové přihlášení. Tyto operace jsou místo toho přeložit v době běhu. `dynamic` Typ zjednodušuje přístup k rozhraní API modelu COM, jako je například rozhraní API Office automatizace, dynamické rozhraní API, například knihovny IronPython a do HTML Document Object Model (DOM).

Typ `dynamic` se chová jako typ `object` ve většině případů. Konkrétně lze převést libovolný výraz jinou hodnotu než null na `dynamic` typu. `dynamic` Typ se liší od `object` v této operace, které obsahují výrazy typu `dynamic` se nevyřeší nebo typ zaškrtnutí kompilátorem. Čas spuštění kompilátoru balíčky, které společně informace o operaci a tyto informace se později používá k vyhodnocení operaci. Jako součást procesu proměnné typu `dynamic` jsou kompilovány do proměnné typu `object`. Proto zadejte `dynamic` existuje pouze v době kompilace, ne za běhu.

V následujícím příkladu se liší od proměnné typu `dynamic` na proměnnou typu `object`. Ověření typu každou proměnnou v době kompilace, umístěte ukazatel myši nad `dyn` nebo `obj` v `WriteLine` příkazy. Zkopírujte následující kód do editoru, kde je k dispozici technologie IntelliSense. Technologie IntelliSense zobrazuje **dynamické** pro `dyn` a **objekt** pro `obj`.

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

<xref:System.Console.WriteLine%2A> Příkazy zobrazuje typy za běhu `dyn` a `obj`. V tomto okamžiku mají stejný typ celé číslo. Následující výstup je vytvořen:

```console
System.Int32
System.Int32
```

Pokud chcete zobrazit rozdíl mezi `dyn` a `obj` v době kompilace, přidejte následující dva řádky mezi prohlášení a `WriteLine` příkazů v předchozím příkladu.

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 Chyba kompilátoru hlášené pro pokus o přidání celého čísla a objekt ve výrazu `obj + 3`. Však žádná chybová zpráva pro `dyn + 3`. Výraz, který obsahuje `dyn` nepovolenou v době kompilace, protože typ `dyn` je `dynamic`.

Následující příklad používá `dynamic` v několika deklarace. `Main` Metoda se také liší od typu v době kompilace kontroly s kontrolu typu za běhu.

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

### <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Klíčová slova jazyka C#](../keywords/index.md)
- [Události](../../../csharp/programming-guide/events/index.md)
- [Použití typu dynamic](../../programming-guide/types/using-type-dynamic.md)
- [Doporučené postupy pro používání řetězců](../../../standard/base-types/best-practices-strings.md)
- [Základní operace s řetězci](../../../standard/base-types/basic-string-operations.md)
- [Vytváření nových řetězců](../../../standard/base-types/creating-new.md)
- [Typové zkoušky a převod operátorů](../operators/type-testing-and-conversion-operators.md)
- [Postupy: bezpečné přetypování pomocí porovnávání vzorů a jako operátorů a is](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [Návod: vytváření a používání dynamických objektů](../../programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- <xref:System.Object?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
