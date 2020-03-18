---
title: Zpracování souboru XML – programovací příručka Jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- XML processing [C#]
- XML [C#], processing
ms.assetid: 60c71193-9dac-4cd3-98c5-100bd0edcc42
ms.openlocfilehash: bc72cade9ce6edddb88d741a3424405bba0a7ad8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793383"
---
# <a name="processing-the-xml-file-c-programming-guide"></a>Zpracování souboru XML (průvodce programováním jazyka C#)

Kompilátor generuje řetězec ID pro každou konstrukci v kódu, který je označen pro generování dokumentace. (Informace o tom, jak označit kód, naleznete [v tématu Doporučené značky pro komentáře k dokumentaci](./recommended-tags-for-documentation-comments.md).) Řetězec ID jednoznačně identifikuje konstrukci. Programy, které zpracovávají soubor XML, mohou použít řetězec ID k identifikaci odpovídající položky metadat/reflexe rozhraní .NET Framework, na kterou se vztahuje dokumentace.

Soubor XML není hierarchickou reprezentací kódu. jedná se o plochý seznam, který má vygenerované ID pro každý prvek.

Kompilátor dodržuje následující pravidla při generování řetězců ID:

- V řetězci není žádné prázdné místo.

- První část řetězce ID identifikuje druh člena, který je identifikován, pomocí jednoho znaku následovaného dvojtečkou. Používají se následující typy členů:

    |Znak|Popis|
    |---------------|-----------------|
    |Ne|Obor názvů<br /><br /> Do oboru názvů nelze přidávat komentáře k dokumentaci, ale můžete na ně vytvořit odkazy na cref, pokud je podporováno.|
    |T|typ: třída, rozhraní, struktura, výčet nebo delegát|
    |F|pole|
    |P|vlastnost (včetně indexerů nebo jiných indexovaných vlastností)|
    |M|(včetně takových speciálních metod, jako jsou konstruktory, operátory a tak dále)|
    |E|event|
    |!|chybový řetězec<br /><br /> Zbytek řetězce obsahuje informace o chybě. Kompilátor Jazyka C# generuje informace o chybě pro odkazy, které nelze přeložit.|

- Druhá část řetězce je plně kvalifikovaný název položky, počínaje kořenem oboru názvů. Název položky, její ohraničující typ (typy) a obor názvů jsou odděleny tečkami. Pokud název samotné položky má tečky, jsou nahrazeny znakem hash ('#'). Předpokládá se, že žádná položka nemá znak hash přímo v jeho názvu. Například plně kvalifikovaný název konstruktoru String by "System.String.#ctor".

- Pro vlastnosti a metody, pokud existují argumenty metody, následuje seznam argumentů uzavřený v závorcích. Pokud neexistují žádné argumenty, jsou přítomny žádné závorky. Argumenty jsou odděleny čárkami. Kódování každého argumentu přímo následuje podle toho, jak je kódován v podpisu rozhraní .NET Framework:

  - Základní typy. Pravidelné typy (ELEMENT_TYPE_CLASS nebo ELEMENT_TYPE_VALUETYPE) jsou reprezentovány jako plně kvalifikovaný název typu.

  - Vnitřní typy (například ELEMENT_TYPE_I4, ELEMENT_TYPE_OBJECT, ELEMENT_TYPE_STRING, ELEMENT_TYPE_TYPEDBYREF a ELEMENT_TYPE_VOID) jsou reprezentovány jako plně kvalifikovaný název odpovídajícího úplného typu. Například System.Int32 nebo System.TypedReference.

  - ELEMENT_TYPE_PTR je reprezentována jako '\*" za změněný typ.

  - ELEMENT_TYPE_BYREF je reprezentovánjako '\@' následující změněný typ.

  - ELEMENT_TYPE_PINNED je reprezentován jako ^' za změněný typ. Kompilátor Jazyka C# nikdy generuje toto.

  - ELEMENT_TYPE_CMOD_REQ je reprezentován jako "&#124;" a plně kvalifikovaný název modifikátortřídy, následující změněný typ. Kompilátor Jazyka C# nikdy generuje toto.

  - ELEMENT_TYPE_CMOD_OPT je reprezentován jako '!' a plně kvalifikovaný název modifikátortřídy, následující změněný typ.

  - ELEMENT_TYPE_SZARRAY je reprezentován jako "[]" za typem prvku pole.

  - ELEMENT_TYPE_GENERICARRAY je reprezentován jako "[?]" za typem prvku pole. Kompilátor Jazyka C# nikdy generuje toto.

  - ELEMENT_TYPE_ARRAY je reprezentovánjako`size`[*lowerbound*: ,*lowerbound*:`size`], kde počet čárek je pořadí - 1 a dolní hranice a velikost každé dimenze, pokud jsou známy, jsou reprezentovány v desítkové min. Pokud není zadána dolní mez nebo velikost, je jednoduše vynechána. Pokud jsou dolní mez a velikost pro určitou dimenzi vynechány, je vynecháno také ":". Například dvourozměrné pole s 1 jako dolní hranice a nespecifikované velikosti je [1:,1:].

  - ELEMENT_TYPE_FNPTR je reprezentován jako`type`"=FUNC: `type` (*podpis*)", kde je návratový typ a *podpis* je argumenty metody. Pokud neexistují žádné argumenty, závorky jsou vynechány. Kompilátor Jazyka C# nikdy generuje toto.

    Následující součásti podpisu nejsou reprezentovány, protože se nikdy nepoužívají k rozlišování přetížených metod:

  - Konvenci

  - návratový typ

  - ELEMENT_TYPE_SENTINEL

- Pouze pro operátory převodu (op_Implicit a op_Explicit) je vrácená hodnota metody kódována jako '~' následovaná návratovým typem, jak je kódováno výše.

- U obecných typů následuje název typu backtick a potom číslo, které označuje počet parametrů obecného typu. Například:

     ``<member name="T:SampleClass`2">``je značka pro typ, který `public class SampleClass<T, U>`je definován jako .

     Pro metody, které berou obecné typy jako parametry, jsou parametry obecného \`typu\`určeny jako čísla, která jsou označena zpětnými značkami (například 0, 1). Každé číslo představující zápis pole s nulou pro obecné parametry typu.

## <a name="examples"></a>Příklady

Následující příklady ukazují, jak by byly generovány řetězce ID pro třídu a její členy:

[!code-csharp[csProgGuidePointers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#21)]

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [-doc (možnosti kompilátoru Jazyka C#)](../../language-reference/compiler-options/doc-compiler-option.md)
- [Komentáře dokumentace XML](./index.md)
