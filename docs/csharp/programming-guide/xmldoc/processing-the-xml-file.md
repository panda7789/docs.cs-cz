---
title: Zpracování souboru XML – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- XML processing [C#]
- XML [C#], processing
ms.assetid: 60c71193-9dac-4cd3-98c5-100bd0edcc42
ms.openlocfilehash: 2c3ba0e12d0d7e6a568c4c3741d99b901fca2722
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75696516"
---
# <a name="processing-the-xml-file-c-programming-guide"></a>Zpracování souboru XML (Průvodce programováním v C#)

Kompilátor generuje řetězec ID pro každou konstrukci v kódu, který je označen pro generování dokumentace. (Informace o tom, jak označit svůj kód, naleznete v tématu [Doporučené značky pro dokumentační komentáře](./recommended-tags-for-documentation-comments.md).) Řetězec ID jednoznačně identifikuje konstrukci. Programy, které zpracovávají soubor XML, mohou použít řetězec ID k identifikaci odpovídající .NET Framework metadat nebo položek reflexe, na které se dokumentace vztahuje.

Soubor XML není hierarchická reprezentace vašeho kódu; Jedná se o nestrukturovaný seznam, který má vygenerované ID pro každý prvek.

Kompilátor při generování řetězců ID sleduje následující pravidla:

- Řetězec neobsahuje prázdné znaky.

- První část řetězce ID identifikuje druh zjištěného člena pomocí jednoho znaku následovaného dvojtečkou. Používají se následující typy členů:

    |Znak|Popis|
    |---------------|-----------------|
    |N|Obor názvů<br /><br /> Do oboru názvů nemůžete přidávat komentáře k dokumentaci, ale můžete na ně cref odkazy, kde se podporují.|
    |T|Typ: třída, rozhraní, struktura, výčet, delegát|
    |F|pole|
    |P|vlastnost (včetně indexerů nebo jiných indexovaných vlastností)|
    |M|Metoda (včetně takových speciálních metod jako konstruktory, operátory a tak dále)|
    |E|event|
    |!|řetězec chyby<br /><br /> Zbytek řetězce poskytuje informace o chybě. C# Kompilátor generuje informace o chybě pro odkazy, které nelze přeložit.|

- Druhá část řetězce je plně kvalifikovaný název položky začínající v kořenu oboru názvů. Název položky, její nadřazené typy a obor názvů jsou odděleny tečkami. Pokud má název položky vlastní tečky, nahradí se znakem hash (#). Předpokládá se, že žádná položka nemá v názvu přímo znak hash. Například plně kvalifikovaný název konstruktoru řetězce by byl "System. String. #ctor".

- V případě vlastností a metod, pokud jsou argumenty metody, seznam argumentů uzavřený v závorkách následuje. Pokud nejsou žádné argumenty, nejsou k dispozici žádné závorky. Argumenty jsou odděleny čárkami. Kódování každého argumentu následuje přímo, jak je kódováno v signatuře .NET Framework:

  - Základní typy. Běžné typy (ELEMENT_TYPE_CLASS nebo ELEMENT_TYPE_VALUETYPE) jsou reprezentovány jako plně kvalifikovaný název typu.

  - Vnitřní typy (například ELEMENT_TYPE_I4, ELEMENT_TYPE_OBJECT, ELEMENT_TYPE_STRING, ELEMENT_TYPE_TYPEDBYREF a ELEMENT_TYPE_VOID) jsou reprezentovány jako plně kvalifikovaný název odpovídající úplného typu. Například System. Int32 nebo System. TypedReference.

  - ELEMENT_TYPE_PTR se reprezentuje jako "\*" za upraveným typem.

  - ELEMENT_TYPE_BYREF se reprezentuje jako "\@" za upraveným typem.

  - ELEMENT_TYPE_PINNED je reprezentovaná jako "^" za upraveným typem. C# Kompilátor to nikdy negeneruje.

  - ELEMENT_TYPE_CMOD_REQ se reprezentuje jako&#124;a plně kvalifikovaný název třídy modifikátoru po změněném typu. C# Kompilátor to nikdy negeneruje.

  - ELEMENT_TYPE_CMOD_OPT je reprezentována jako '! ' a plně kvalifikovaný název třídy modifikátoru za upraveným typem.

  - ELEMENT_TYPE_SZARRAY je reprezentována jako "[]" za typem elementu pole.

  - ELEMENT_TYPE_GENERICARRAY je reprezentována jako "[?]" za typem elementu pole. C# Kompilátor to nikdy negeneruje.

  - ELEMENT_TYPE_ARRAY se reprezentuje jako [*lowerbound*:`size`,*lowerbound*:`size`], kde počet čárek je Rank-1 a dolní meze a velikost každé dimenze, pokud jsou známé, jsou reprezentovány v desítkové soustavě. Pokud není zadaná dolní mez nebo velikost, je tato hodnota jednoduše vynechána. Pokud je spodní mez a velikost pro konkrétní dimenzi vynechána, je vynechána i znak ': '. Například dvojrozměrné pole s 1 jako dolní meze a nespecifikované velikosti je [1:, 1:].

  - ELEMENT_TYPE_FNPTR je reprezentována jako "= FUNC:`type`(*Signature*)", kde `type` je návratový typ a *Signatura* je argumenty metody. Nejsou-li žádné argumenty, jsou vynechány kulaté závorky. C# Kompilátor to nikdy negeneruje.

    Následující komponenty signatur nejsou reprezentovány, protože nejsou nikdy použity pro odlišení přetížených metod:

  - konvence volání

  - návratový typ

  - ELEMENT_TYPE_SENTINEL

- U operátorů převodu (op_Implicit a op_Explicit) je návratová hodnota metody zakódována jako znak ~ následovaný návratovým typem, jak je kódován výše.

- Pro obecné typy je název typu následován zpětným voláním a pak číslem, které označuje počet parametrů obecného typu. Příklad:

     ``<member name="T:SampleClass`2">`` je značka pro typ, který je definován jako `public class SampleClass<T, U>`.

     Pro metody, které přibírají obecné typy jako parametry, jsou parametry obecného typu zadány jako čísla, která začínají značkami zaškrtnutí (například \`0\`1). Každé číslo představující zápis pole založený na nule pro obecné parametry typu.

## <a name="examples"></a>Příklady

Následující příklady znázorňují, jak se generují řetězce ID pro třídu a její členy:

[!code-csharp[csProgGuidePointers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#21)]

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [-doc (C# možnosti kompilátoru)](../../language-reference/compiler-options/doc-compiler-option.md)
- [Dokumentační komentáře XML](./index.md)
