---
title: Dokumentace kódu pomocí komentářů XML
description: Zjistěte, jak dokumentovat kód pomocí komentářů v dokumentaci XML a vygenerovat soubor dokumentace XML v době kompilace.
ms.date: 01/21/2020
ms.technology: csharp-fundamentals
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.openlocfilehash: 1ed39c4733c36b3932fcb85bf50d4f4c0e53aa6f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146314"
---
# <a name="document-your-code-with-xml-comments"></a>Dokumentování kódu pomocí komentářů XML

Komentáře k dokumentaci XML jsou zvláštním druhem komentáře, který je přidán nad definici libovolného uživatelem definovaného typu nebo člena.
Jsou zvláštní, protože mohou být zpracovány kompilátorem pro generování souboru dokumentace XML v době kompilace.
Soubor XML generovaný kompilátorem lze distribuovat společně s sestavením rozhraní .NET, aby visual studio a další idemohly pomocí technologie IntelliSense zobrazit rychlé informace o typech nebo členech. Soubor XML lze navíc spustit prostřednictvím nástrojů, jako jsou [DocFX](https://dotnet.github.io/docfx/) a [Sandcastle,](https://github.com/EWSoftware/SHFB) které generují referenční webové stránky rozhraní API.

Komentáře dokumentace XML, stejně jako všechny ostatní komentáře, jsou kompilátorem ignorovány.

Soubor XML můžete vygenerovat v době kompilace jedním z následujících akcí:

- Pokud vyvíjíte aplikaci s rozhraním .NET Core z `GenerateDocumentationFile` příkazového `<PropertyGroup>` řádku, můžete přidat prvek do části souboru projektu .csproj. Cestu k souboru dokumentace můžete také zadat přímo pomocí [ `DocumentationFile` elementu](/visualstudio/msbuild/common-msbuild-project-properties). Následující příklad generuje soubor XML v adresáři projektu se stejným kořenovým názvem jako sestavení:

   ```xml
   <GenerateDocumentationFile>true</GenerateDocumentationFile>
   ```

   To odpovídá následujícímu:

   ```xml
   <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\$(AssemblyName).xml</DocumentationFile>
   ```

- Pokud vyvíjíte aplikaci pomocí sady Visual Studio, klepněte pravým tlačítkem myši na projekt a vyberte **příkaz Vlastnosti**. V dialogovém okně vlastností vyberte kartu **Sestavení** a **zkontrolujte soubor dokumentace XML**. Můžete také změnit umístění, do kterého kompilátor zapíše soubor.

- Pokud kompilujete aplikaci rozhraní .NET Framework z příkazového řádku, přidejte při kompilaci [možnost kompilátoru -doc.](language-reference/compiler-options/doc-compiler-option.md)  

Komentáře k dokumentaci XML`///`používají trojitá lomítka ( ) a text komentáře ve formátu XML. Například:

[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a>Názorný postup

Pojďme projít dokumentování velmi základní matematické knihovny, aby bylo snadné pro nové vývojáře pochopit / přispět a pro vývojáře třetích stran k použití.

Zde je kód pro jednoduchou knihovnu matematiky:

[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

Ukázková knihovna podporuje čtyři hlavní`add`aritmetické operace ( , `subtract`, `multiply`, `divide`a ) a `int` `double` datové typy.

Nyní chcete mít možnost vytvořit referenční dokument rozhraní API z vašeho kódu pro vývojáře třetích stran, kteří používají vaši knihovnu, ale nemají přístup ke zdrojovému kódu.
Jak již bylo zmíněno dříve XML dokumentace značky lze použít k dosažení tohoto cíle. Nyní se zobrazí standardní značky XML, které kompilátor Jazyka C# podporuje.

## <a name="summary"></a>\<summary>

Značka `<summary>` přidá stručné informace o typu nebo členu.
Budu demonstrovat jeho použití přidáním `Math` do definice `Add` třídy a první metody. Nebojte se použít na zbytek kódu.

[!code-csharp[Summary Tag](~/samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

Značka `<summary>` je důležitá a doporučujeme ji zahrnout, protože její obsah je primárním zdrojem informací typu nebo člena v aplikaci IntelliSense nebo referenčním dokumentu rozhraní API.

## <a name="remarks"></a>\<poznámky>

Značka `<remarks>` doplňuje informace o typech `<summary>` nebo členech, které značka poskytuje. V tomto příkladu jej přidáte do třídy.

[!code-csharp[Remarks Tag](~/samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

## <a name="returns"></a>\<returns>

Značka `<returns>` popisuje vrácenou hodnotu deklarace metody.
Stejně jako dříve, následující `<returns>` příklad ilustruje `Add` značku na první metodě. Totéž můžete udělat s jinými metodami.

[!code-csharp[Returns Tag](~/samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

## <a name="value"></a>\<value>

Značka `<value>` je podobná `<returns>` značce s tím rozdílem, že ji používáte pro vlastnosti.
Za `Math` předpokladu, že `PI`vaše knihovna měla statickou vlastnost nazvanou , použijte tuto značku takto:

[!code-csharp[Value Tag](~/samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

## <a name="example"></a>\<příklad>

`<example>` Značku slouží k zahrnutí příkladu do dokumentace XML.
To zahrnuje použití `<code>` podřízené značky.

[!code-csharp[Example Tag](~/samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

Značka `code` zachová konce řádků a odsazení pro delší příklady.

## <a name="para"></a>\<para>

`<para>` Značku slouží k formátování obsahu v rámci nadřazené značky. `<para>`se obvykle používá uvnitř značky, například `<remarks>` nebo `<returns>`, k rozdělení textu na odstavce.
Obsah značky `<remarks>` můžete formátovat pro definici třídy.

[!code-csharp[Para Tag](~/samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

## <a name="c"></a>\<c>

Stále na téma formátování, můžete použít `<c>` značku pro označení části textu jako kód.
Je to jako `<code>` značka, ale inline. Je to užitečné, když chcete zobrazit příklad rychlého kódu jako součást obsahu značky.
Pojďme aktualizovat dokumentaci `Math` pro třídu.

[!code-csharp[C Tag](~/samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

## <a name="exception"></a>\<výjimka>

Pomocí značky, `<exception>` dejte vývojářům vědět, že metoda může vyvolat konkrétní výjimky.
Při pohledu na `Math` knihovnu, `Add` uvidíte, že obě metody vyvolat výjimku, pokud je splněna určitá podmínka. Není to však tak zřejmé, `Divide` že celá metoda `b` vyvolá také, pokud je parametr nula. Nyní přidejte dokumentaci výjimky k této metodě.

[!code-csharp[Exception Tag](~/samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

Atribut `cref` představuje odkaz na výjimku, která je k dispozici z aktuálního prostředí kompilace.
Může se jedná o libovolný typ definovaný v projektu nebo odkazované sestavení. Kompilátor vydá upozornění, pokud jeho hodnotu nelze vyřešit.

## <a name="see"></a>\<viz>

Značka `<see>` umožňuje vytvořit odkaz na stránku dokumentace, na který lze kliknout pro jiný prvek kódu. V našem dalším příkladu vytvoříme odkaz, na `Add` který lze kliknout mezi těmito dvěma metodami.

[!code-csharp[See Tag](~/samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

Je `cref` **povinný** atribut, který představuje odkaz na typ nebo jeho člen, který je k dispozici z aktuálního prostředí kompilace.
Může se jedná o libovolný typ definovaný v projektu nebo odkazované sestavení.

## <a name="seealso"></a>\<seealso>

`<seealso>` Značku používáte stejným způsobem jako `<see>` značka. Jediným rozdílem je, že jeho obsah je obvykle umístěn v části "Viz také". Zde přidáme `seealso` značku na metodu `Add` celého čísla, abychom odkazovali na jiné metody ve třídě, které přijímají parametry celého čísla:

[!code-csharp[Seealso Tag](~/samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

Atribut `cref` představuje odkaz na typ nebo jeho člen, který je k dispozici z aktuálního prostředí kompilace.
Může se jedná o libovolný typ definovaný v projektu nebo odkazované sestavení.

## <a name="param"></a>\<param>

`<param>` Značku slouží k popisu parametrů metody. Zde je příklad metody `Add` double: Parametr, který značka popisuje, je zadán v **požadovaném** `name` atributu.

[!code-csharp[Param Tag](~/samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

## <a name="typeparam"></a>\<typeparam>

Značku `<typeparam>` používáte stejně jako značka, `<param>` ale pro obecné deklarace typu nebo metody k popisu obecného parametru.
Přidejte do `Math` třídy rychlou obecnou metodu a zkontrolujte, zda je jedno množství větší než jiné.

[!code-csharp[Typeparam Tag](~/samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

## <a name="paramref"></a>\<paramref>

Někdy můžete být uprostřed popisu toho, co metoda dělá `<summary>` v čem by mohla být značka, a možná budete chtít vytvořit odkaz na parametr. Značka `<paramref>` je skvělá právě pro toto. Pojďme aktualizovat souhrn naší dvojité `Add` metody. Podobně `<param>` jako značka je název parametru zadán v **požadovaném** `name` atributu.

[!code-csharp[Paramref Tag](~/samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

## <a name="typeparamref"></a>\<typeparamref>

Značku `<typeparamref>` používáte stejně jako značka, `<paramref>` ale pro obecné deklarace typu nebo metody k popisu obecného parametru.
Můžete použít stejnou obecnou metodu, kterou jste dříve vytvořili.

[!code-csharp[Typeparamref Tag](~/samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

## <a name="list"></a>\<seznam>

`<list>` Značka slouží k formátování informací o dokumentaci jako uspořádaný seznam, neuspořádaný seznam nebo tabulku. Vytvořte neuspořádaný seznam všech `Math` matematických operací, které vaše knihovna podporuje.

[!code-csharp[List Tag](~/samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

Seřazený seznam nebo tabulku `type` můžete `number` `table`vytvořit změnou atributu nebo .

## <a name="inheritdoc"></a>\<inheritdoc>

`<inheritdoc>` Značku můžete použít k dědění komentářů XML ze základních tříd, rozhraní a podobných metod. Tím se eliminuje nechtěné kopírování a vkládání duplicitních komentářů XML a automaticky udržuje komentáře XML synchronizované.

[!code-csharp-interactive[InheritDoc Tag](~/samples/snippets/csharp/concepts/codedoc/inheritdoc-tag.cs)]

### <a name="put-it-all-together"></a>Spojení všech součástí dohromady

Pokud jste postupovali podle tohoto kurzu a v případě potřeby použili značky na váš kód, váš kód by teď měl vypadat podobně jako následující:

[!code-csharp[Tagged Library](~/samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

Z vašeho kódu můžete vygenerovat podrobný web dokumentace s křížovými odkazy, na které lze kliknout. Ale jste konfrontováni s dalším problémem: váš kód se stal těžko čitelným.
Je tu tolik informací prosít přes to bude noční můra pro každého vývojáře, který chce přispět k tomuto kódu.
Naštěstí existuje značka XML, která vám pomůže s tímto problémem:

## <a name="include"></a>\<patří>

Značka `<include>` umožňuje odkazovat na komentáře v samostatném souboru XML, které popisují typy a členy ve zdrojovém kódu, na rozdíl od umístění komentářů dokumentace přímo do souboru zdrojového kódu.

Nyní přesunete všechny značky XML do samostatného `docs.xml`souboru XML s názvem . Nebojte se pojmenovat soubor, co chcete.

[!code-xml[Sample XML](~/samples/snippets/csharp/concepts/codedoc/include.xml)]

Ve výše uvedeném xml se komentáře dokumentace každého člena zobrazují přímo uvnitř značky pojmenované podle toho, co dělají. Můžete si vybrat vlastní strategii.
Teď, když máte komentáře XML v samostatném souboru, podívejme se, jak `<include>` může být váš kód čitelnější pomocí značky:

[!code-csharp[Include Tag](~/samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

A tady to máte: náš kód je zpět čitelný a žádné informace o dokumentaci nebyly ztraceny.

Atribut `file` představuje název souboru XML obsahujícího dokumentaci.

Atribut `path` představuje dotaz [XPath](../standard/data/xml/xpath-queries-and-namespaces.md) `tag name` k přítomnosti `file`v zadaném .

Atribut `name` představuje specifikátor názvu ve značce, která předchází komentáře.

Atribut, `id` který lze použít místo `name`, představuje ID pro značku, která předchází komentáře.

### <a name="user-defined-tags"></a>Uživatelem definované značky

Všechny výše uvedené značky představují ty, které jsou rozpoznány kompilátorem Jazyka C#. Uživatel však může definovat své vlastní značky.
Nástroje, jako je Sandcastle, [ \<](https://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm) přinášejí podporu pro další značky, jako jsou>událostí a [ \<poznámka>](https://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm), a dokonce podporují [dokumentování jmenných prostorů](https://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).
Vlastní nebo interní nástroje pro generování dokumentace lze také použít se standardními značkami a lze podporovat více výstupních formátů z HTML do PDF.

## <a name="recommendations"></a>Doporučení

Dokumentování kódu se doporučuje z mnoha důvodů. Co bude následovat, jsou některé osvědčené postupy, obecné scénáře případu použití a věci, které byste měli vědět při použití značek dokumentace XML v kódu Jazyka C#.

- Z důvodu konzistence by měly být zdokumentovány všechny veřejně viditelné typy a jejich členy. Když to musíš udělat, udělej to všechno.
- Soukromé členy lze také zdokumentovat pomocí komentářů XML. Tím se však zpřístupní vnitřní (potenciálně důvěrné) fungování knihovny.
- Na minimum, typy a jejich členové `<summary>` by měli mít značku, protože jeho obsah je potřeba pro IntelliSense.
- Text dokumentace by měl být napsán pomocí úplných vět končících úplnými zastávkami.
- Částečné třídy jsou plně podporovány a informace o dokumentaci budou zřetězeny do jedné položky pro tento typ.
- Kompilátor `<exception>`ověří syntaxi značek `<include>` `<param>`, `<see>` `<seealso>`, `<typeparam>` , , a.
- Kompilátor ověřuje parametry, které obsahují cesty k souborům a odkazy na jiné části kódu.

## <a name="see-also"></a>Viz také

- [Dokumentační komentáře XML (Průvodce programováním v C#)](programming-guide/xmldoc/index.md)
- [Doporučené značky pro dokumentační komentáře (Průvodce programováním v C#)](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
