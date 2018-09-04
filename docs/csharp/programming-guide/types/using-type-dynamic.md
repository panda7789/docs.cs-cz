---
title: Použití typu dynamic (C# Programming Guide)
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic [C#], about dynamic type
- dynamic type [C#]
ms.assetid: 3828989d-c967-4a51-b948-857ebc8fdf26
ms.openlocfilehash: b1ea9240da66b77723c002c6527135339af9e352
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502530"
---
# <a name="using-type-dynamic-c-programming-guide"></a>Použití typu dynamic (C# Programming Guide)

[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] zavádí nový typ `dynamic`. Typ je statický typ, ale objekt typu `dynamic` obchází kontroly statického typu. Ve většině případů funguje jako má typ `object`. V době kompilace, element, který je zadán jako `dynamic` se předpokládá, že podporují všechny operace. Proto je nemusíte mít obavy o tom, zda objekt získává svou hodnotu z rozhraní API modelu COM, z dynamického jazyka, jako je IronPython, z HTML Document Object Model (DOM), z reflexe nebo z někde jinde v programu. Nicméně pokud kód není platný, jsou zachyceny chyby za běhu.

Například pokud metodu instance `exampleMethod1` v následujícím kódu má pouze jeden parametr, který kompilátor rozpozná první volání metody, `ec.exampleMethod1(10, 4)`, není platný, protože obsahuje dva argumenty. Volání způsobí chybu kompilátoru. Druhé volání metody, `dynamic_ec.exampleMethod1(10, 4)`, není kompilátor kontrolovat, protože typ `dynamic_ec` je `dynamic`. Proto je hlášena žádná chyba kompilátoru. Nicméně chyby neuvozuje Všimněte si, že po neomezenou dobu. Je zachycena v době běhu a způsobí, že výjimka za běhu.

[!code-csharp[CsProgGuideTypes#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#50)]

[!code-csharp[CsProgGuideTypes#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#56)]

Role kompilátor v těchto příkladech je do balíčku společně informace o všech příkazů navrhuje k objektu nebo výraz, který je zadán jako `dynamic`. V době běhu je zkontrolován uložené informace a jakýkoli příkaz, který není platný způsobí, že výjimka za běhu.

Výsledek nejvíce dynamické operace je samotný `dynamic`. Například, pokud ukazatel myši nad rámec použití `testSum` v následujícím příkladu, technologie IntelliSense zobrazí typ **dynamické testSum (lokální proměnná)**.

[!code-csharp[CsProgGuideTypes#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#51)]

Ve kterých je výsledek operace `dynamic` patří:

* Převody z `dynamic` do jiného typu.
* Volá konstruktor, které zahrnují argumenty typu `dynamic`.

Například typ `testInstance` v následující deklaraci je `ExampleClass`, nikoli `dynamic`:

[!code-csharp[CsProgGuideTypes#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#52)]

Příklady převodu jsou uvedeny v následující části "Převody".

## <a name="conversions"></a>Převody

Převody mezi dynamických objektů a dalších typů je snadné. To umožňuje vývojářům přepínat mezi dynamické a nedynamickou chování.

Libovolný objekt lze převést na dynamický typ implicitně, jak je znázorněno v následujícím příkladu.

[!code-csharp[CsProgGuideTypes#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#53)]

Naopak implicitní převod může dynamicky uplatňují na libovolný výraz typu `dynamic`.

[!code-csharp[CsProgGuideTypes#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#54)]

## <a name="overload-resolution-with-arguments-of-type-dynamic"></a>Řešení s argumenty typu dynamické přetížení

Řešení přetížení dojde za běhu místo v době kompilace, pokud jeden nebo více argumentů ve volání metody typ `dynamic`, nebo pokud je příjemce volání metody typu `dynamic`. V následujícím příkladu Pokud dostupná jenom `exampleMethod2` přijmout argument řetězce je definována metoda odesílání `d1` jako argument nezpůsobí chybu kompilátoru, ale to způsobit výjimku za běhu. Řešení přetížení se nezdaří za běhu, protože typ za běhu `d1` je `int`, a `exampleMethod2` vyžaduje řetězec.

[!code-csharp[CsProgGuideTypes#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#55)]

## <a name="dynamic-language-runtime"></a>Runtime modul dynamického jazyka

Dynamické jazykovým modulem runtime (DLR) je nová rozhraní API v [!INCLUDE[net_v40_short](~/includes/net-v40-short-md.md)]. Poskytuje infrastrukturu, která podporuje `dynamic` typu v jazyce C# a také provádění dynamických programovacích jazyků, jako je například IronPython a IronRuby. Další informace o DLR najdete v tématu [přehled dynamického modulu Runtime jazyka](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).

## <a name="com-interop"></a>zprostředkovatel komunikace s objekty COM

[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] obsahuje několik funkcí, které vylepšují prostředí spolupráce se rozhraní API modelu COM, jako je například rozhraní API automatizace sady Office. Mezi vylepšení patří použití `dynamic` typ a [pojmenované a nepovinné argumenty](../classes-and-structs/named-and-optional-arguments.md).

Mnoho metod modelu COM povolit variace v typy argumentů a návratový typ podle určení typů jako `object`. To je nezbytné explicitní přetypování hodnoty tak, aby zajistěte ve spolupráci se silnými typy proměnných v jazyce C#. Pokud kompilujete pomocí [/Link (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/link-compiler-option.md) možnost zavedení `dynamic` typ umožňuje přistupovat ke všem výskytů `object` v signaturách modelu COM jako by byly typu `dynamic`a tím současně aby se předešlo velkou část přetypování. Například následující příkazy kontrastu, jak získat přístup k buňku v tabulce s Microsoft Office Excel `dynamic` typ a bez `dynamic` typu.

[!code-csharp[csOfficeWalkthrough#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#12)]

[!code-csharp[csOfficeWalkthrough#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#13)]

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[dynamic](../../language-reference/keywords/dynamic.md)|Popisuje použití `dynamic` – klíčové slovo.|
|[Přehled DLR (Dynamic Language Runtime)](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)|Přehled DLR, což je prostředí modulu runtime, který přidá sadu služeb pro dynamické jazyky common language runtime (CLR).|
|[Návod: Vytváření a používání dynamických objektů](walkthrough-creating-and-using-dynamic-objects.md)|Obsahuje podrobné pokyny pro vytvoření vlastní dynamický objekt a pro vytvoření projektu, který přistupuje `IronPython` knihovny.|
|[Postupy: Přístup k objektům Interop sady Office pomocí funkcí Visual C#](../interop/how-to-access-office-onterop-objects.md)|Ukazuje, jak vytvořit projekt, který používá pojmenovaných a nepovinných argumentů `dynamic` typ a další vylepšení, které usnadňují přístup k objektům rozhraní API Office.|