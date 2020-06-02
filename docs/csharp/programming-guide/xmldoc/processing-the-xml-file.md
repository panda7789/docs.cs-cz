---
title: Zpracování souboru XML – Průvodce programováním v C#
ms.date: 07/20/2015
helpviewer_keywords:
- XML processing [C#]
- XML [C#], processing
ms.assetid: 60c71193-9dac-4cd3-98c5-100bd0edcc42
ms.openlocfilehash: 1e3d96f9398f2c08ed715111f01987e2d1948439
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287256"
---
# <a name="process-the-xml-file-c-programming-guide"></a>Zpracování souboru XML (Průvodce programováním v C#)

Kompilátor generuje řetězec ID pro každou konstrukci v kódu, který je označen pro generování dokumentace. (Informace o tom, jak označit svůj kód, naleznete v tématu [Doporučené značky pro dokumentační komentáře](./recommended-tags-for-documentation-comments.md).) Řetězec ID jednoznačně identifikuje konstrukci. Programy, které zpracovávají soubor XML, mohou pomocí řetězce ID identifikovat odpovídající metadata nebo položku odrazu .NET, na kterou se dokumentace vztahuje.

## <a name="id-strings"></a>Řetězce ID

Soubor XML není hierarchická reprezentace vašeho kódu. Je to plochý seznam, který má vygenerované ID pro každý prvek.

Kompilátor při generování řetězců ID sleduje následující pravidla:

- Řetězec neobsahuje prázdné znaky.

- První část řetězce určuje druh člena pomocí jednoho znaku následovaný dvojtečkou. Používají se následující typy členů:

    |Znak|Typ člena|Poznámky|
    |---------------|-----------------|-|
    |N|namespace|Do oboru názvů nemůžete přidávat komentáře k dokumentaci, ale můžete na ně cref odkazy, kde se podporují.|
    |T|typ|Typ může být třída, rozhraní, struktura, výčet nebo delegát.|
    |F|pole|
    |P|property|Zahrnuje indexery nebo jiné indexované vlastnosti.|
    |M|method|Obsahuje speciální metody, jako jsou konstruktory a operátory.|
    |E|event|
    |!|řetězec chyby|Zbytek řetězce poskytuje informace o chybě. Kompilátor jazyka C# generuje informace o chybě pro odkazy, které nelze přeložit.|

- Druhá část řetězce je plně kvalifikovaný název položky začínající v kořenu oboru názvů. Název položky, její nadřazené typy a obor názvů jsou odděleny tečkami. Pokud má název položky vlastní tečky, nahradí se znakem hash (#). Předpokládá se, že žádná položka nemá v názvu přímo znak hash. Například plně kvalifikovaný název konstruktoru řetězce je "System. String. #ctor".

- V případě vlastností a metod se následuje seznam parametrů uzavřený v závorkách. Pokud žádné parametry neexistují, nejsou k dispozici žádné závorky. Parametry jsou odděleny čárkami. Kódování každého parametru následuje přímo, jak je zakódováno v signatuře .NET:

  - Základní typy. Běžné typy (ELEMENT_TYPE_CLASS nebo ELEMENT_TYPE_VALUETYPE) jsou reprezentovány jako plně kvalifikovaný název typu.

  - Vnitřní typy (například ELEMENT_TYPE_I4, ELEMENT_TYPE_OBJECT, ELEMENT_TYPE_STRING, ELEMENT_TYPE_TYPEDBYREF a ELEMENT_TYPE_VOID) jsou reprezentovány jako plně kvalifikovaný název odpovídající úplného typu. Například System. Int32 nebo System. TypedReference.

  - ELEMENT_TYPE_PTR je reprezentovaná jako " \* " po změněném typu.

  - ELEMENT_TYPE_BYREF je reprezentovaná jako " \@ " po změněném typu.

  - ELEMENT_TYPE_PINNED je reprezentovaná jako "^" za upraveným typem. Kompilátor jazyka C# toto rozhraní nikdy negeneruje.

  - ELEMENT_TYPE_CMOD_REQ je reprezentovaná jako "&#124;" a plně kvalifikovaný název třídy modifikátoru za upraveným typem. Kompilátor jazyka C# toto rozhraní nikdy negeneruje.

  - ELEMENT_TYPE_CMOD_OPT je reprezentována jako '! ' a plně kvalifikovaný název třídy modifikátoru za upraveným typem.

  - ELEMENT_TYPE_SZARRAY je reprezentována jako "[]" za typem elementu pole.

  - ELEMENT_TYPE_GENERICARRAY je reprezentována jako "[?]" za typem elementu pole. Kompilátor jazyka C# toto rozhraní nikdy negeneruje.

  - ELEMENT_TYPE_ARRAY je reprezentována jako [*lowerbound*: `size` ,*lowerbound*: `size` ], kde je počet čárek-1 a dolní meze a velikost jednotlivých dimenzí, pokud jsou známy, jsou reprezentovány v desítkové soustavě. Pokud není zadaná dolní mez nebo velikost, je vynechána. Pokud je spodní mez a velikost pro konkrétní dimenzi vynechána, je vynechána i znak ': '. Například dvojrozměrné pole s 1 jako dolní meze a nespecifikované velikosti je [1:, 1:].

  - ELEMENT_TYPE_FNPTR je reprezentovaná jako "= FUNC: `type` (*Signature*)", kde `type` je návratový typ a *Signatura* je argumenty metody. Nejsou-li žádné argumenty, jsou vynechány kulaté závorky. Kompilátor jazyka C# toto rozhraní nikdy negeneruje.

  Následující součásti signatur nejsou reprezentovány, protože nejsou používány k odlišení přetížených metod:

  - konvence volání

  - návratový typ

  - ELEMENT_TYPE_SENTINEL

- U operátorů převodu ( `op_Implicit` a `op_Explicit` ) je návratová hodnota metody kódována jako znak ~ následovaný návratovým typem.

- Pro obecné typy je název typu následován zpětným voláním a pak číslem, které označuje počet parametrů obecného typu. Například:

     ``<member name="T:SampleClass`2">``je značka pro typ, který je definován jako `public class SampleClass<T, U>` .

     Pro metody, které přijímají obecné typy jako parametry, jsou parametry obecného typu zadány jako čísla, která začínají značkami zaškrtnutí (například \` 0, \` 1). Každé číslo představuje zápis pole založený na nule pro obecné parametry typu.

## <a name="examples"></a>Příklady

Následující příklady ukazují, jak jsou generovány řetězce ID pro třídu a její členové:

[!code-csharp[csProgGuidePointers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#21)]

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [-doc (možnosti kompilátoru C#)](../../language-reference/compiler-options/doc-compiler-option.md)
- [Komentáře dokumentace XML](./index.md)
