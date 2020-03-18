---
title: Předdefinované typy odkazů – odkaz jazyka C#
description: Další informace o typy odkazů, které mají C# klíčová slova, které můžete použít k jejich deklarování.
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
ms.openlocfilehash: c2c03f47babd9ccf87eb60d33b9d65d1a9c82e2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399642"
---
# <a name="built-in-reference-types-c-reference"></a>Předdefinované typy odkazů (odkaz C#)

C# má řadu předdefinovaných typů odkazů. Mají klíčová slova nebo operátory, které jsou synonyma pro typ v knihovně .NET.

## <a name="the-object-type"></a>Typ objektu

Tento `object` typ je <xref:System.Object?displayProperty=nameWithType> alias pro v rozhraní .NET. V systému sjednoceného typu jazyka C# všechny typy, předdefinované a uživatelem definované, <xref:System.Object?displayProperty=nameWithType>typy odkazů a typy hodnot, dědí přímo nebo nepřímo z . Proměnným typu `object`můžete přiřadit hodnoty libovolného typu . Libovolnou `object` proměnnou lze přiřadit k výchozí `null`hodnotě pomocí literálu . Když je proměnná typu hodnoty převedena na objekt, říká se, že je *zabalená*. Pokud je proměnná typu `object` převedena na typ hodnoty, říká se, že je *rozbalena*. Další informace naleznete v [tématu Box a rozbalení](../../programming-guide/types/boxing-and-unboxing.md).

## <a name="the-string-type"></a>Typ řetězce

Typ `string` představuje posloupnost nula nebo více znaků Unicode. `string`je alias <xref:System.String?displayProperty=nameWithType> pro v rozhraní .NET.

Ačkoli `string` je typ odkazu, [operátory `==` rovnosti a `!=` ](../operators/equality-operators.md#string-equality) jsou definovány pro porovnání hodnot `string` objektů, nikoli odkazů. To umožňuje testování rovnosti řetězců intuitivnější. Například:

```csharp-interactive
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine(object.ReferenceEquals(a, b));
```

Zobrazí se "True" a pak "False", protože obsah `a` řetězců `b` jsou ekvivalentní, ale neodkazují na stejnou instanci řetězce.

[Operátor +](../operators/addition-operator.md#string-concatenation) zřetězí řetězce:

```csharp
string a = "good " + "morning";
```

Tím se vytvoří objekt řetězce, který obsahuje "dobré ráno".

Řetězce jsou *neměnné*-- obsah objektu řetězce nelze po vytvoření objektu změnit, i když syntaxe způsobí, že se zobrazí, jako byste to mohli udělat. Například při psaní tohoto kódu kompilátor ve skutečnosti vytvoří nový objekt řetězce pro uložení nové `b`sekvence znaků a tento nový objekt je přiřazen . Paměť, která byla přidělena pro `b` (pokud obsahuje řetězec "h") je pak způsobilé pro uvolnění paměti.

```csharp
string b = "h";
b += "ello";
```

`[]` [Operátor](../operators/member-access-operators.md#indexer-operator-) lze použít pro přístup jen pro čtení k jednotlivým znakům řetězce. Platné hodnoty indexu `0` začínají na a musí být menší než délka řetězce:

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

Podobným způsobem může `[]` být operátor také použit pro iterace nad každým znakem v řetězci:

```csharp-interactive
string str = "test";

for (int i = 0; i < str.Length; i++)
{
  Console.Write(str[i] + " ");
}
// Output: t e s t
```

Řetězcové literály `string` jsou typu a mohou být `@`zapsány ve dvou formách, citovány a citovány. Literály řetězce v uvozovkách jsou uzavřeny v uvozovkách ("):

```csharp
"good morning"  // a string literal
```

Řetězcové literály mohou obsahovat libovolný literál znaku. Jsou zahrnuty únikové sekvence. Následující příklad používá `\\` sekvenci `\u0066` escape pro zpětné `\n` lomítko, pro písmeno f a pro nový řádek.

```csharp-interactive
string a = "\\\u0066\n F";
Console.WriteLine(a);
// Output:
// \f
//  F
```

> [!NOTE]
> Řídicí kód `\udddd` (kde `dddd` je čtyřmístné číslo) představuje znak`dddd`Unicode U+ . Osmmístné únikové kódy Unicode jsou také rozpoznány: `\Udddddddd`.

[Literály řetězce doslovný](../tokens/verbatim.md) začíná `@` a jsou také uzavřeny v uvozovkách. Například:

```csharp
@"good morning"  // a string literal
```

Výhodou doslovných řetězců je, že únikové sekvence *nejsou* zpracovány, což usnadňuje psaní, například plně kvalifikovaný název souboru systému Windows:

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

Chcete-li do @-quoted řetězce zahrnout dvojité uvozovky, zdvojnásobte je:

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

## <a name="the-delegate-type"></a>Typ delegáta

Deklarace typu delegáta je podobná podpisu metody. Má vrácenou hodnotu a libovolný počet parametrů libovolného typu:

```csharp
public delegate void MessageDelegate(string message);
public delegate int AnotherDelegate(MyType m, long num);
```

V rozhraní `System.Action` .NET a `System.Func` typy poskytují obecné definice pro mnoho běžných delegátů. Pravděpodobně nebudete muset definovat nové typy vlastních delegátů. Místo toho můžete vytvořit instance poskytnutých obecných typů.

A `delegate` je typ odkazu, který lze použít k zapouzdření pojmenované nebo anonymní metody. Delegáti jsou podobné ukazatele funkce v jazyce C++; delegáti jsou však typově bezpečné a zabezpečené. Aplikace delegátů naleznete v tématu [Delegáti](../../programming-guide/delegates/index.md) a [Obecné delegáty](../../programming-guide/generics/generic-delegates.md). Delegáti jsou základem pro [události](../../programming-guide/events/index.md). Delegát může být vytvořena instance tím, že jej přisuzuje buď s pojmenovanou nebo anonymní metodou.

Delegát musí být vytvořena instance s metodou nebo lambda výraz, který má kompatibilní návratový typ a vstupní parametry. Další informace o stupni odchylky, která je povolena v podpisu metody, naleznete [v tématu Odchylka v delegátech](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md). Pro použití s anonymní metody, delegát a kód, který má být přidružen y jsou deklarovány společně.

## <a name="the-dynamic-type"></a>Dynamický typ

Typ `dynamic` označuje, že použití proměnné a odkazy na jeho členy obejít kontrolu typu kompilace. Místo toho jsou tyto operace vyřešeny v době běhu. Typ `dynamic` zjednodušuje přístup k rozhraní API modelu COM, jako jsou rozhraní API automatizace sady Office, k dynamickým rozhraním API, jako jsou knihovny IronPython, a k objektovému modelu dokumentu HTML (DOM).

Typ `dynamic` se ve `object` většině případů chová jako typ. Zejména všechny non-null výraz lze převést `dynamic` na typ. Typ `dynamic` se liší `object` od v tom, že `dynamic` operace, které obsahují výrazy typu nejsou vyřešeny nebo typ kontrolovánkompilátorem. Kompilátor balíčky společně informace o operaci a tyto informace se později používá k vyhodnocení operace za běhu. Jako součást procesu jsou proměnné `dynamic` typu kompilovány do `object`proměnných typu . Proto typ `dynamic` existuje pouze v době kompilace, nikoli v době běhu.

Následující příklad kontrastuje proměnnou `dynamic` typu s `object`proměnnou typu . Chcete-li ověřit typ každé proměnné v době `dyn` kompilace, umístěte ukazatel myši nad nebo `obj` v příkazech. `WriteLine` Zkopírujte následující kód do editoru, kde je k dispozici technologie IntelliSense. Technologie IntelliSense `dyn` zobrazuje **dynamické** funkce pro a **objekt** pro . `obj`

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

Příkazy <xref:System.Console.WriteLine%2A> zobrazují typy za `dyn` běhu `obj`a . V tomto okamžiku mají oba stejný typ, celé číslo. Vytvoří se následující výstup:

```console
System.Int32
System.Int32
```

Chcete-li zobrazit `dyn` `obj` rozdíl mezi a v době kompilace, přidejte následující dva řádky mezi deklarace a `WriteLine` příkazy v předchozím příkladu.

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 Chyba kompilátoru je hlášena pro pokus o přidání celého čísla a objektu ve výrazu `obj + 3`. Pro soubor však `dyn + 3`není hlášena žádná chyba. Výraz, který `dyn` obsahuje není zaškrtnuto v době `dyn` `dynamic`kompilace, protože typ je .

Následující příklad `dynamic` používá v několika deklaracích. Metoda `Main` také kontrastuje kontrolu typu kompilace s kontrolou typu run-time.

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

### <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [C# Klíčová slova](../keywords/index.md)
- [Akce](../../programming-guide/events/index.md)
- [Použití typu dynamic](../../programming-guide/types/using-type-dynamic.md)
- [Doporučené postupy pro používání řetězců](../../../standard/base-types/best-practices-strings.md)
- [Základní operace s řetězci](../../../standard/base-types/basic-string-operations.md)
- [Vytváření nových řetězců](../../../standard/base-types/creating-new.md)
- [Operátory pro testování typů a přetypování](../operators/type-testing-and-cast.md)
- [Jak bezpečně obsazení pomocí porovnávání vzorů a as a je operátory](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [Návod: vytváření a používání dynamických objektů](../../programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- <xref:System.Object?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
