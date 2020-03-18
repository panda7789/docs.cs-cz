---
title: Použití textového dynamického průvodce – C# Programovací příručka
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic [C#], about dynamic type
- dynamic type [C#]
ms.assetid: 3828989d-c967-4a51-b948-857ebc8fdf26
ms.openlocfilehash: c5ac5b3692266010f0be8672ef744baaa32e6a03
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75711854"
---
# <a name="using-type-dynamic-c-programming-guide"></a>Použití dynamického typu (Průvodce programováním jazyka C#)

C# 4 zavádí nový `dynamic`typ, . Typ je statický typ, ale objekt `dynamic` typu obchází kontrolu statického typu. Ve většině případů funguje jako `object`typ . V době kompilace prvek, který `dynamic` je zadán tak, jak se předpokládá, že podporuje všechny operace. Proto není třeba se starat o tom, zda objekt získá jeho hodnotu z rozhraní COM API, z dynamického jazyka, jako je IronPython, z HTML document object model (DOM), z reflexe nebo odněkud odjinud v programu. Pokud však kód není platný, jsou chyby zachyceny za běhu.

Například pokud metoda `exampleMethod1` instance v následujícím kódu má pouze jeden parametr, kompilátor `ec.exampleMethod1(10, 4)`rozpozná, že první volání metody , není platné, protože obsahuje dva argumenty. Volání způsobí chybu kompilátoru. Druhé volání metody , `dynamic_ec.exampleMethod1(10, 4)`není kontrolováno kompilátorem, protože `dynamic_ec` `dynamic`typ je . Proto je hlášena žádná chyba kompilátoru. Chyba však neunikne oznámení neomezeně dlouho. Je zachycen a za běhu a způsobí výjimku za běhu.

[!code-csharp[CsProgGuideTypes#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#50)]

[!code-csharp[CsProgGuideTypes#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#56)]

Role kompilátoru v těchto příkladech je balíček společně informace o tom, co každý příkaz `dynamic`navrhuje udělat objektu nebo výrazu, který je zadán jako . V době běhu jsou zkontrolovány uložené informace a jakýkoli příkaz, který není platný, způsobí výjimku za běhu.

Výsledkem většiny dynamických `dynamic`operací je sama o sobě . Pokud například spočine ukazatel myši `testSum` nad použitím v následujícím příkladu, technologie IntelliSense zobrazí dynamický testSum typu **(místní proměnná).**

[!code-csharp[CsProgGuideTypes#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#51)]

Operace, ve kterých `dynamic` výsledek není zahrnovat:

* Převody `dynamic` z na jiný typ.
* Volání konstruktoru, která `dynamic`zahrnují argumenty typu .

Například typ `testInstance` v následujícím prohlášení `ExampleClass`je `dynamic`, ne :

[!code-csharp[CsProgGuideTypes#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#52)]

Příklady převodů jsou uvedeny v následující části Konverze.

## <a name="conversions"></a>Převody

Převody mezi dynamickými objekty a jinými typy jsou snadné. To umožňuje vývojáři přepínat mezi dynamickým a nedynamickým chováním.

Libovolný objekt lze implicitně převést na dynamický typ, jak je znázorněno v následujících příkladech.

[!code-csharp[CsProgGuideTypes#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#53)]

Naopak implicitní převod lze dynamicky použít pro `dynamic`libovolný výraz typu .

[!code-csharp[CsProgGuideTypes#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#54)]

## <a name="overload-resolution-with-arguments-of-type-dynamic"></a>Řešení přetížení argumenty typu dynamické

Řešení přetížení dochází v době běhu namísto v době kompilace, pokud jeden `dynamic`nebo více argumentů ve volání metody `dynamic`mají typ , nebo pokud příjemce volání metody je typu . V následujícím příkladu, pokud `exampleMethod2` je definována pouze přístupná `d1` metoda pro provedení argumentu řetězce, odeslání jako argument nezpůsobí chybu kompilátoru, ale způsobí výjimku za běhu. Řešení přetížení se nezdaří za běhu, `d1` `int`protože `exampleMethod2` typ běhu je a vyžaduje řetězec.

[!code-csharp[CsProgGuideTypes#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#55)]

## <a name="dynamic-language-runtime"></a>Dynamický jazyk runtime

Dynamický jazyk runtime (DLR) je nové rozhraní API v rozhraní .NET Framework 4. Poskytuje infrastrukturu, která `dynamic` podporuje typ v jazyce C# a také implementaci dynamických programovacích jazyků, jako je IronPython a IronRuby. Další informace o dlr naleznete [v tématu Přehled dynamického jazykového běhu](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).

## <a name="com-interop"></a>zprostředkovatel komunikace s objekty COM

C# 4 obsahuje několik funkcí, které zlepšují možnosti spolupráce s rozhraními API COM, jako jsou rozhraní API automatizace sady Office. Mezi vylepšení patří použití `dynamic` typu a [pojmenované a volitelné argumenty](../classes-and-structs/named-and-optional-arguments.md).

Mnoho metod COM umožňuje variaci typů argumentů a `object`návratový typ určením typů jako . To si vyžádalo explicitní přetypování hodnot ke koordinaci s proměnnými silného typu v c#. Pokud kompilujete pomocí [-link (C# Compiler Options),](../../language-reference/compiler-options/link-compiler-option.md) zavedení `dynamic` typu umožňuje zacházet s výskyty `object` v podpisech COM, jako by byly typu `dynamic`, a tím, aby se zabránilo hodně z přetypování. Následující příkazy například kontrastují s přístupem k buňce `dynamic` v tabulce `dynamic` aplikace Microsoft Office Excel s typem a bez něj.

[!code-csharp[csOfficeWalkthrough#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#12)]

[!code-csharp[csOfficeWalkthrough#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#13)]

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Dynamické](../../language-reference/builtin-types/reference-types.md)|Popisuje použití klíčového `dynamic` slova.|
|[Přehled dynamického jazykového běhu](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)|Obsahuje přehled dlr, což je runtime prostředí, které přidává sadu služeb pro dynamické jazyky do clr (COMMON Language runtime).|
|[Návod: Vytváření a používání dynamických objektů](walkthrough-creating-and-using-dynamic-objects.md)|Obsahuje podrobné pokyny pro vytvoření vlastního dynamického objektu a pro `IronPython` vytvoření projektu, který přistupuje ke knihovně.|
|[Jak získat přístup k objektům interoperability Office pomocí funkcí jazyka C#](../interop/how-to-access-office-onterop-objects.md)|Ukazuje, jak vytvořit projekt, který používá pojmenované `dynamic` a volitelné argumenty, typ a další vylepšení, které zjednodušují přístup k objektům rozhraní API sady Office.|
