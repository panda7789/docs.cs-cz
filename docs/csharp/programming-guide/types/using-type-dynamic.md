---
title: Použití typu dynamický průvodce C# programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic [C#], about dynamic type
- dynamic type [C#]
ms.assetid: 3828989d-c967-4a51-b948-857ebc8fdf26
ms.openlocfilehash: 4141c64ff6dbbec60b53a41862a4273df6ef51ab
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588345"
---
# <a name="using-type-dynamic-c-programming-guide"></a>Použití typu Dynamic (C# Průvodce programováním)

C#4 zavádí nový typ, `dynamic`. Typ je statický typ, ale objekt typu `dynamic` obchází kontrolu statického typu. Ve většině případů funguje jako typ `object`. V době kompilace se předpokládá, že element, který `dynamic` je zadán jako, má podporovat jakoukoli operaci. Proto nemusíte mít obavy o tom, zda objekt získá svou hodnotu z rozhraní API modelu COM, z dynamického jazyka, jako je například Ironpythonu, z HTML model DOM (Document Object Model) (DOM), z reflexe nebo z jiného důvodu v programu. Pokud však kód není platný, jsou chyby zachyceny za běhu.

Například pokud metoda `exampleMethod1` instance v následujícím kódu má pouze jeden parametr, kompilátor rozpozná, že první volání metody, `ec.exampleMethod1(10, 4)`, není platné, protože obsahuje dva argumenty. Volání způsobí chybu kompilátoru. Druhé volání metody, `dynamic_ec.exampleMethod1(10, 4)`, není zkontrolováno kompilátorem, protože `dynamic_ec` typ je `dynamic`. Proto není hlášena žádná chyba kompilátoru. Tato chyba ale neumožňuje bez omezení řídicího oznámení. Je zachycena v době běhu a způsobuje výjimku za běhu.

[!code-csharp[CsProgGuideTypes#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#50)]

[!code-csharp[CsProgGuideTypes#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#56)]

Role kompilátoru v těchto příkladech je zabalit informace o tom, co jednotlivé příkazy navrhují k objektu nebo výrazu, který je zadán jako `dynamic`. V době spuštění jsou zkontrolovány uložené informace a jakýkoli příkaz, který není platný, způsobuje výjimku za běhu.

Výsledek většiny dynamických operací je sám sebou `dynamic`. Například pokud umístíte ukazatel myši na použití `testSum` v následujícím příkladu, technologie IntelliSense zobrazí typ **(místní proměnná) dynamického testSum**.

[!code-csharp[CsProgGuideTypes#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#51)]

Operace, ve kterých výsledek `dynamic` nezahrnuje:

* Převody z `dynamic` na jiný typ.
* Volání konstruktoru, která obsahují argumenty typu `dynamic`.

Například typ `testInstance` v následující `ExampleClass`deklaraci `dynamic`není:

[!code-csharp[CsProgGuideTypes#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#52)]

Příklady převodu jsou uvedeny v následující části "převody".

## <a name="conversions"></a>Převody

Převody mezi dynamickými objekty a dalšími typy jsou jednoduché. To umožňuje vývojáři přepínat mezi dynamickým a nedynamickým chováním.

Libovolný objekt lze převést na dynamický typ implicitně, jak je znázorněno v následujících příkladech.

[!code-csharp[CsProgGuideTypes#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#53)]

Naopak implicitní převod lze dynamicky použít na jakýkoli výraz typu `dynamic`.

[!code-csharp[CsProgGuideTypes#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#54)]

## <a name="overload-resolution-with-arguments-of-type-dynamic"></a>Rozlišení přetěžování s argumenty typu Dynamic

K rozlišení přetěžování dochází za běhu místo v době kompilace, pokud jeden nebo více argumentů ve volání metody má typ `dynamic`, nebo pokud je příjemce volání metody typu. `dynamic` V následujícím příkladu, pokud je jediná dostupná `exampleMethod2` metoda definována pro převzetí řetězcového argumentu, odeslání `d1` jako argumentu nezpůsobí chybu kompilátoru, ale vyvolá výjimku za běhu. Rozlišení přetěžování `d1` se v době běhu nezdařilo, protože typ modulu `int`runtime je `exampleMethod2` a vyžaduje řetězec.

[!code-csharp[CsProgGuideTypes#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#55)]

## <a name="dynamic-language-runtime"></a>Modul runtime jazyka Dynamic

Modul dynamického jazyka (DLR) je nové rozhraní API v .NET Framework 4. Poskytuje infrastrukturu, která podporuje `dynamic` typ v C#a také implementaci dynamických programovacích jazyků, jako je ironpythonu a IronRuby. Další informace o DLR najdete v tématu [Přehled dynamického jazykového modulu runtime](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).

## <a name="com-interop"></a>zprostředkovatel komunikace s objekty COM

C#4 zahrnuje několik funkcí, které zlepšují možnosti spolupráce s rozhraními API modelu COM, jako jsou třeba rozhraní API pro automatizaci systému Office. Mezi vylepšení jsou použití `dynamic` typu a pojmenovaných a nepovinných [argumentů](../classes-and-structs/named-and-optional-arguments.md).

Mnoho metod modelu COM umožňuje variace typů argumentů a návratového typu určením typů jako `object`. To vyžadovalo explicitní přetypování hodnot pro koordinaci s proměnnými se silnými typy C#v. Pokud kompilujete pomocí možnosti [/Link (C# možnosti kompilátoru)](../../language-reference/compiler-options/link-compiler-option.md) , `dynamic` zavedení typu vám umožní nakládat s výskyty `object` v podpisech com, jako kdyby byly typu `dynamic`, a tak vyhnout se mnohem z přetypování. Například následující příkazy kontrastují přístup k buňce v systém Microsoft Office excelové tabulce s `dynamic` typem a `dynamic` bez typu.

[!code-csharp[csOfficeWalkthrough#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#12)]

[!code-csharp[csOfficeWalkthrough#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#13)]

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[dynamic](../../language-reference/keywords/dynamic.md)|Popisuje použití `dynamic` klíčového slova.|
|[Přehled DLR (Dynamic Language Runtime)](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)|Poskytuje přehled o DLR, což je běhové prostředí, které přidává sadu služeb pro dynamické jazyky do modulu CLR (Common Language Runtime).|
|[Návod: Vytváření a používání dynamických objektů](walkthrough-creating-and-using-dynamic-objects.md)|Poskytuje podrobné pokyny pro vytvoření vlastního dynamického objektu a pro vytvoření projektu, který přistupuje `IronPython` k knihovně.|
|[Postupy: Přístup k objektům Interop Office pomocí C# vizuálních funkcí](../interop/how-to-access-office-onterop-objects.md)|Ukazuje, jak vytvořit projekt, který používá pojmenované a nepovinné argumenty, `dynamic` typ a další vylepšení, která usnadňují přístup k objektům rozhraní Office API.|
