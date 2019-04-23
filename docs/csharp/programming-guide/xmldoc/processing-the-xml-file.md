---
title: Zpracování souboru XML - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML processing [C#]
- XML [C#], processing
ms.assetid: 60c71193-9dac-4cd3-98c5-100bd0edcc42
ms.openlocfilehash: 5b643b9f736169bb4450bb357cc35fee35e155c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59976297"
---
# <a name="processing-the-xml-file-c-programming-guide"></a>Zpracování souboru XML (Průvodce programováním v C#)

Kompilátor generuje řetězec ID pro každý konstrukce ve vašem kódu, který je označený ke generování dokumentace. (Informace o tom, jak označit kódu najdete v tématu [doporučené značky pro dokumentační komentáře](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md).) Řetězec ID jednoznačně identifikuje konstrukce. Programy, které zpracování souboru XML slouží k identifikaci odpovídající položka metadat/reflexe rozhraní .NET Framework, která se použije v dokumentaci k ID řetězce.

 Soubor XML není Hierarchická reprezentace kódu; je plochý seznam, který má vygenerované ID pro každý prvek.

 Při generování ID řetězce, kompilátor dodržuje následující pravidla:

- Žádné prázdné místo je v řetězci.

- První část řetězec ID identifikuje typ členu je označen jako jeden znak následovaný dvojtečkou. Se používají následující typy členů:

    |Znak|Popis|
    |---------------|-----------------|
    |N|– obor názvů<br /><br /> Dokumentační komentáře nelze přidat do oboru názvů, ale může být cref odkazy, pokud je podporována.|
    |T|Typ: třída, rozhraní, struktury, výčtu, delegát|
    |F|pole|
    |P|vlastnosti (včetně indexery nebo jiných indexované vlastnosti)|
    |M|(včetně speciálních metod, jako konstruktory, operátory a tak dále) – metoda|
    |E|event|
    |!|Text chyby<br /><br /> Zbývající řetězec poskytuje informace o této chybě. Kompilátor jazyka C# generuje informace o chybě pro odkazy, které nelze rozpoznat.|

- Druhá část řetězce je plně kvalifikovaný název položky, počínaje kořenový obor názvů. Název položky, jeho nadřazené typy a obor názvů jsou odděleny tečkami. Pokud má název samotné položky období, budou nahrazeny jako znak hash (#). Předpokládá se, že nemá žádná položka znak hash přímo ve svém názvu. Plně kvalifikovaný název konstruktoru řetězec by být například "System.String.#ctor".

- Vlastnosti a metody Pokud jsou argumenty metody, uzavřený do závorek seznamu argumentů se řídí. Pokud neexistují žádné argumenty, jsou k dispozici žádné závorky. Argumenty jsou odděleny čárkami. Kódování každý argument následuje přímo jak je zakódovaný v rozhraní .NET Framework podpisu:

  - Základní typy. Pravidelné typy (za řetězcem ELEMENT_TYPE_CLASS nebo ELEMENT_TYPE_VALUETYPE) jsou reprezentovány ve formě plně kvalifikovaný název typu.

  - Vnitřní typy (například ELEMENT_TYPE_I4 ELEMENT_TYPE_OBJECT, ELEMENT_TYPE_STRING, ELEMENT_TYPE_TYPEDBYREF. a ELEMENT_TYPE_VOID) jsou reprezentovány ve formě plně kvalifikovaný název typu odpovídající úplné. Například System.Int32 nebo System.TypedReference.

  - Typ ELEMENT_TYPE_PTR je vyjádřena jako "\*" následující typ změny.

  - ELEMENT_TYPE_BYREF je vyjádřena jako "\@' následující typ změny.

  - ELEMENT_TYPE_PINNED je vyjádřena jako ' ^' následující typ změny. Kompilátor jazyka C# vygeneruje nikdy to.

  - ELEMENT_TYPE_CMOD_REQ je vyjádřena jako "&#124;" a plně kvalifikovaný název třídy modifikátor následující typ změny. Kompilátor jazyka C# vygeneruje nikdy to.

  - ELEMENT_TYPE_CMOD_OPT je vyjádřena jako '!' a plně kvalifikovaný název třídy modifikátor následující typ změny.

  - ELEMENT_TYPE_SZARRAY je reprezentován jako "[]" za typ prvku pole.

  - "[?]" Představuje ELEMENT_TYPE_GENERICARRAY následující typ prvku pole. Kompilátor jazyka C# vygeneruje nikdy to.

  - ELEMENT_TYPE_ARRAY je vyjádřena jako [*dolní hranice*:`size`,*dolní hranice*:`size`] kde je počet čárkami pořadí - 1 a dolní meze a velikosti jednotlivých rozměrů, pokud známé, jsou reprezentovány v desítkové soustavě. Pokud není zadán dolní mez nebo velikost, je jednoduše vynechán. Pokud jsou vynechány dolní mez a velikosti pro konkrétní dimenzi, ":" je také vynechán. Je třeba 2rozměrné pole s 1 jako dolní mez a neurčené formáty [1:, 1:].

  - Typ ELEMENT_TYPE_FNPTR je reprezentován jako "= FUNC:`type`(*podpis*)", kde `type` je návratový typ a *podpis* je argumenty metody. Pokud neexistují žádné argumenty, jsou vynechány závorky. Kompilátor jazyka C# vygeneruje nikdy to.

    Následující součásti podpis nejsou zastoupeny, protože se používají nikdy odlišující přetížené metody:

  - Konvence volání

  - Návratový typ

  - ELEMENT_TYPE_SENTINEL

- Pro převod operátorů pouze (op_Implicit a op_Explicit –), návratová hodnota metody kódovaná jako ' ~ "následované návratovým typem, formátu kódování výše.

- Pro obecné typy je název typu následovaný prvními a potom číslo určující počet parametrů obecného typu. Příklad:

     ``<member name="T:SampleClass`2">`` je značka pro typ, který je definován jako `public class SampleClass<T, U>`.

     Pro metody, přičemž obecné typy jako parametry, parametry obecného typu jsou zadané jako čísla začíná zpětných apostrofů (například \`0,\`1). Každé číslo představující zápis založený na nule pole pro parametry obecného typu.

## <a name="examples"></a>Příklady

Následující příklady ukazují, jak ID řetězce pro třídu a její členy by se vygenerovala:

[!code-csharp[csProgGuidePointers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#21)]

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [/ DOC (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)
- [Dokumentační komentáře XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
