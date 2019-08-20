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
ms.openlocfilehash: a5a32fa0a98cda37d7f599b20ef2b507cadd730c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69604210"
---
# <a name="built-in-reference-types-c-reference"></a>Předdefinované typy odkazů (C# referenční)

C#má několik předdefinovaných typů odkazů. Mají klíčová slova nebo operátory, které jsou synonyma pro typ v knihovně .NET. 

## <a name="the-object-type"></a>Typ objektu

`object` Typ je<xref:System.Object?displayProperty=nameWithType> alias v rozhraní .NET. V sjednoceném typu systému C#jsou všechny typy, předdefinované a uživatelsky definované typy odkazů a typy hodnot děděny přímo nebo nepřímo z. <xref:System.Object?displayProperty=nameWithType> K proměnným typu `object`můžete přiřadit hodnoty libovolného typu. Jakoukoli `object` proměnnou lze přiřadit její výchozí hodnotě pomocí literálu `null`. Když je proměnná typu hodnoty převedena na typ Object, je označována jako zabalená. Je-li proměnná typu Object převedena na typ hodnoty, je označována jako nezabaleno. Další informace naleznete v tématu [zabalení a rozbalení](../../programming-guide/types/boxing-and-unboxing.md). 

## <a name="the-string-type"></a>Typ řetězce

`string` Typ představuje sekvenci nula nebo více znaků Unicode. `string`je alias pro <xref:System.String?displayProperty=nameWithType> v rozhraní .NET.

I `string` když je odkazový typ, [ `==` operátory rovnosti `!=` a](../operators/equality-operators.md#string-equality) jsou definovány pro porovnání hodnot `string` objektů, nikoli odkazů. Díky tomu je testování rovnosti řetězců intuitivnější. Příklad:

```csharp-interactive
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine(object.ReferenceEquals(a, b));
```

Zobrazí se hodnota "true" a potom "false", protože obsah řetězců je ekvivalentní, ale `a` `b` neodkazuje na stejnou instanci řetězce.

[Operátor +](../operators/addition-operator.md#string-concatenation) zřetězí řetězce:

```csharp
string a = "good " + "morning";
```

Tím se vytvoří objekt String, který obsahuje "Dobré ráno".

Řetězce jsou *neměnné*– obsah objektu String nelze po vytvoření objektu změnit, i když se syntaxe zobrazí jako v případě, že to můžete provést. Například při psaní tohoto kódu kompilátor ve skutečnosti vytvoří nový objekt řetězce, který bude obsahovat novou posloupnost znaků a který je přiřazen k `b`novému objektu. Paměť, která byla přidělena pro `b` (pokud obsahuje řetězec "h"), je pak vhodná pro uvolňování paměti.

```csharp
string b = "h";
b += "ello";
```

Operátor lze použít pro přístup jen pro čtení k jednotlivým znakům typu `string`. [](../operators/member-access-operators.md#indexer-operator-) `[]` Platné hodnoty začínají na `0` a musí být menší než délka: `string`

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

Podobným způsobem `[]` lze operátor také použít pro iteraci každého znaku `string`v:

```csharp-interactive
string str = "test";

for (int i = 0; i < str.Length; i++)
{
  Console.Write(str[i] + " ");
}
// Output: t e s t
``` 

Řetězcové literály jsou typu `string` a mohou být zapsány ve dvou formulářích, `@`v uvozovkách a v uvozovkách. Řetězcové literály v uvozovkách jsou uzavřeny v uvozovkách ("):

```csharp
"good morning"  // a string literal
```

Řetězcové literály můžou obsahovat libovolný znakový literál. K dispozici jsou řídicí sekvence. Následující příklad používá řídicí sekvenci `\\` zpětného lomítka `\u0066` , pro písmeno f a `\n` pro nový řádek.

```csharp-interactive
string a = "\\\u0066\n F";
Console.WriteLine(a);
\\ Output:
\\ \f
\\  F
```

> [!NOTE]
> Řídicí kód `\udddd` (kde `dddd` je číslo se čtyřmi číslicemi) představuje znak Unicode U +`dddd`. Rozpoznávají se také osmimístného kódů Escape Unicode: `\Udddddddd`.

[Doslovné řetězce literálů](../tokens/verbatim.md) začínají `@` na a jsou také uzavřeny v uvozovkách. Příklad:

```csharp
@"good morning"  // a string literal
```

Výhodou doslovného řetězce je, že řídicí sekvence nejsou zpracovávány, což usnadňuje psaní, například plně kvalifikovaného názvu souboru systému Windows:

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

Chcete-li do @-quoted řetězce zahrnout dvojitou uvozovku, Zdvojnásobte si ho:

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

## <a name="the-delegate-type"></a>Typ delegáta

Deklarace typu delegáta je podobná podpisu metody. Má návratovou hodnotu a libovolný počet parametrů libovolného typu:

```csharp
public delegate void MessageDelegate(string message);
public delegate int AnotherDelegate(MyType m, long num);
```

V rozhraní .NET `System.Action` a `System.Func` typy poskytují obecné definice pro mnoho běžných delegátů. Pravděpodobně nebudete muset definovat nové vlastní typy delegátů. Místo toho můžete vytvořit instance poskytnutých obecných typů.

`delegate` Je odkazový typ, který lze použít k zapouzdření pojmenované nebo anonymní metody. Delegáti jsou podobní ukazatelům funkcí C++v nástroji; Delegáti jsou však typově bezpečné a zabezpečené. Pro aplikace delegátů, přečtěte si téma [Delegáti](../../programming-guide/delegates/index.md) a [Obecné delegáty](../../programming-guide/generics/generic-delegates.md). Delegáti jsou základem pro [události](../../programming-guide/events/index.md). Pro delegáta se dá vytvořit instance, a to tak, že ho přidružíte k pojmenované nebo anonymní metodě.

Pro delegáta musí být vytvořená metoda nebo lambda výraz, který má kompatibilní návratový typ a vstupní parametry. Další informace o stupni odchylky, která je povolena v signatuře metody, naleznete v tématu [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md). Pro použití s anonymními metodami, delegát a kód, který je k němu přidružen, jsou deklarovány společně. 

## <a name="the-dynamic-type"></a>Dynamický typ

`dynamic` Typ označuje, že použití proměnné a odkazů na její členy vynechává kontrolu typu při kompilaci. Místo toho se tyto operace vyřeší za běhu. `dynamic` Typ zjednodušuje přístup k rozhraním API modelu COM, jako jsou například rozhraní API pro automatizaci systému Office, dynamická rozhraní API, jako jsou ironpythonu knihovny a HTML model DOM (Document Object Model) (DOM).

Typ `dynamic` se ve většině případů `object` chová jako typ. Konkrétně libovolný výraz, který není null, lze převést na `dynamic` typ. Typ se liší od `object` v tom, že operace obsahující výrazy typu `dynamic` nejsou vyřešeny nebo typ zkontrolovaný kompilátorem. `dynamic` Kompilátor balí informace o operaci a tyto informace jsou později použity k vyhodnocení operace v době běhu. V rámci procesu jsou proměnné typu `dynamic` kompilovány do proměnných typu. `object` Proto typ `dynamic` existuje pouze v době kompilace, nikoli v době běhu.

Následující příklad kontrastuje proměnnou typu `dynamic` na proměnnou typu. `object` Chcete-li ověřit typ každé proměnné v době kompilace, umístěte ukazatel myši nad `dyn` nebo `obj` v `WriteLine` příkazech. Zkopírujte následující kód do editoru, kde je k dispozici technologie IntelliSense. IntelliSense zobrazuje **dynamický** pro `dyn` **objekt** a pro `obj`.

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

Příkazy zobrazují běhové `dyn` typy a `obj`. <xref:System.Console.WriteLine%2A> V tomto okamžiku oba mají stejný typ Integer. Vytvoří se následující výstup:

```console
System.Int32
System.Int32
```

Chcete-li zobrazit rozdíl `dyn` mezi `obj` a v době kompilace, přidejte následující dva řádky `WriteLine` mezi deklaracemi a příkazy v předchozím příkladu.

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 Chyba kompilátoru je hlášena při pokusu o přidání celého čísla a objektu ve výrazu `obj + 3`. Není však hlášena žádná chyba pro `dyn + 3`. Výraz, který obsahuje `dyn` , není kontrolován v době kompilace, protože `dyn` typ je `dynamic`.

Následující příklad používá `dynamic` v několika deklaracích. `Main` Metoda také kontrastuje při kontrole typu za běhu při kontrole typu za běhu.

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
- [Postupy: Bezpečné přetypování pomocí porovnávání vzorů a operátorů as a is](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [Návod: vytváření a používání dynamických objektů](../../programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- <xref:System.Object?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
