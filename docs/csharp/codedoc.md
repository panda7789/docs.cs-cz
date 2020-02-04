---
title: Dokumentace kódu s komentáři XML
description: Naučte se dokumentovat kód pomocí dokumentačních komentářů XML a generovat soubor dokumentace XML v době kompilace.
ms.date: 01/21/2020
ms.technology: csharp-fundamentals
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.openlocfilehash: 1ec088db1de7c953bdb20b1129c5fd40f9e31454
ms.sourcegitcommit: feb42222f1430ca7b8115ae45e7a38fc4a1ba623
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/02/2020
ms.locfileid: "76965929"
---
# <a name="document-your-code-with-xml-comments"></a>Dokumentování kódu pomocí komentářů XML

Komentáře dokumentace XML jsou zvláštním druhem komentáře, přidané nad definici libovolného uživatelsky definovaného typu nebo člena.
Jsou speciální, protože mohou být zpracovány kompilátorem pro generování souboru dokumentace XML v době kompilace.
Soubor XML generovaný kompilátorem lze distribuovat společně s sestavením .NET tak, aby Visual Studio a jiné prostředí pro vývoj mohli používat technologii IntelliSense k zobrazení rychlých informací o typech nebo členech. Kromě toho lze spustit soubor XML prostřednictvím nástrojů jako [DocFX](https://dotnet.github.io/docfx/) a [Sandcastle](https://github.com/EWSoftware/SHFB) ke generování websites referenční dokumentace rozhraní API.

Komentáře dokumentace XML, stejně jako všechny ostatní komentáře, jsou kompilátorem ignorovány.

Soubor XML můžete vygenerovat v době kompilace jedním z následujících způsobů:

- Pokud vyvíjíte aplikaci pomocí .NET Core z příkazového řádku, můžete přidat `GenerateDocumentationFile` element do části `<PropertyGroup>` souboru projektu. csproj. Můžete také zadat cestu k souboru dokumentace přímo pomocí [`DocumentationFile` elementu](/visualstudio/msbuild/common-msbuild-project-properties). Následující příklad generuje soubor XML v adresáři projektu se stejným kořenovým názvem souboru jako sestavení:

   ```xml
   <GenerateDocumentationFile>true</GenerateDocumentationFile>
   ```
   
   To je ekvivalentní následujícímu:
   
   ```xml
   <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\$(AssemblyName).xml</DocumentationFile>
   ```

- Pokud vyvíjíte aplikaci pomocí sady Visual Studio, klikněte pravým tlačítkem na projekt a vyberte **vlastnosti**. V dialogovém okně Vlastnosti vyberte kartu **sestavení** a Prohlédněte si **soubor dokumentace XML**. Můžete také změnit umístění, do kterého kompilátor zapisuje soubor.

- Pokud kompilujete .NET Framework aplikaci z příkazového řádku, přidejte při kompilaci [možnost kompilátoru-doc](language-reference/compiler-options/doc-compiler-option.md) .  

Komentáře dokumentace XML používají tři lomítka (`///`) a tělo komentáře ve formátu XML. Příklad:

[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a>Návod

Pojďme si projít dokumentací velmi základní knihovny pro matematiku, abychom novým vývojářům usnadnili pochopení/přispívání a vývojářům třetích stran používat.

Tady je kód pro jednoduchou knihovnu Math:

[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

Ukázková knihovna podporuje čtyři hlavní aritmetické operace (`add`, `subtract`, `multiply`a `divide`) na `int` a `double` datových typech.

Nyní chcete být schopni vytvořit referenční dokument rozhraní API z kódu pro vývojáře třetích stran, kteří používají vaši knihovnu, ale nemají přístup ke zdrojovému kódu.
Jak bylo zmíněno dříve, můžete k tomuto účelu použít Tagy dokumentace XML. Nyní budete zavedeni do standardních značek XML, které C# podporuje kompilátor.

## <a name="summary"></a>\<summary>

Značka `<summary>` přidá stručné informace o typu nebo členu.
Ukážeme jeho použití tím, že ho přidáte do definice `Math` třídy a první `Add` metody. Nebojte se použít pro zbytek kódu.

[!code-csharp[Summary Tag](~/samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

Značka `<summary>` je důležitá a doporučujeme, abyste ji zahrnuli, protože její obsah je primárním zdrojem informací o typu nebo členu v IntelliSense nebo dokumentu Reference k rozhraním API.

## <a name="remarks"></a>\<poznámky >

Značka `<remarks>` doplňuje informace o typech nebo členech, které poskytuje značka `<summary>`. V tomto příkladu ho stačí přidat do třídy.

[!code-csharp[Remarks Tag](~/samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

## <a name="returns"></a>\<returns>

Značka `<returns>` popisuje návratovou hodnotu deklarace metody.
Jak dřív, následující příklad ukazuje značku `<returns>` prvního `Add` metody. Stejný postup můžete provést i pro jiné metody.

[!code-csharp[Returns Tag](~/samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

## <a name="value"></a>\<value>

Značka `<value>` je podobná značce `<returns>`, s tím rozdílem, že ji použijete pro vlastnosti.
Za předpokladu, že vaše knihovna `Math` měla statickou vlastnost nazvanou `PI`, tady je postup použití této značky:

[!code-csharp[Value Tag](~/samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

## <a name="example"></a>\<příklad >

Pomocí značky `<example>` můžete v dokumentaci XML zahrnout příklad.
To zahrnuje použití podřízené značky `<code>`.

[!code-csharp[Example Tag](~/samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

Značka `code` zachovává zalomení řádků a odsazení po delších příkladech.

## <a name="para"></a>\<para>

Použijte značku `<para>` k formátování obsahu v rámci jeho nadřazené značky. `<para>` se obvykle používá uvnitř značky, jako je například `<remarks>` nebo `<returns>`, k rozdělení textu do odstavců.
Můžete naformátovat obsah značky `<remarks>` pro definici třídy.

[!code-csharp[Para Tag](~/samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

## <a name="c"></a>\<c>

Stále v tématu formátování, použijte značku `<c>` pro označení části textu jako kódu.
Vypadá to jako značka `<code>`, ale je vložená. Je užitečné, pokud chcete zobrazit rychlý příklad kódu jako součást obsahu značky.
Pojďme aktualizovat dokumentaci pro třídu `Math`.

[!code-csharp[C Tag](~/samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

## <a name="exception"></a>výjimka \<

Pomocí značky `<exception>` umožníte vývojářům zjistit, že metoda může vyvolávat konkrétní výjimky.
V knihovně `Math` můžete vidět, že obě metody `Add` vyvolávají výjimku, pokud je splněna určitá podmínka. Není tak zřejmé, ale je to, že celočíselná `Divide` metoda vyvolá i v případě, že je parametr `b` nula. Nyní přidejte do této metody dokumentaci k výjimce.

[!code-csharp[Exception Tag](~/samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

Atribut `cref` představuje odkaz na výjimku, která je k dispozici z aktuálního prostředí kompilace.
Může to být libovolný typ definovaný v projektu nebo odkazované sestavení. Kompilátor vydá upozornění, pokud jeho hodnotu nelze vyřešit.

## <a name="see"></a>\<Zobrazit >

Značka `<see>` umožňuje vytvořit odkaz s možnostmi kliknutí na stránku dokumentace pro jiný prvek kódu. V našem dalším příkladu vytvoříme odkaz kliknutí mezi dvěma metodami `Add`.

[!code-csharp[See Tag](~/samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

`cref` je **vyžadovaný** atribut, který představuje odkaz na typ nebo jeho člen, který je k dispozici z aktuálního prostředí kompilace.
Může to být libovolný typ definovaný v projektu nebo odkazované sestavení.

## <a name="seealso"></a>\<SeeAlso >

Značku `<seealso>` používáte stejným způsobem jako značku `<see>`. Jediným rozdílem je, že jeho obsah je obvykle umístěn v části "viz také". Tady přidáme značku `seealso` na celočíselnou `Add` metodu, která bude odkazovat na jiné metody ve třídě, které přijímají celočíselné parametry:

[!code-csharp[Seealso Tag](~/samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

Atribut `cref` představuje odkaz na typ nebo jeho člen, který je k dispozici z aktuálního prostředí kompilace.
Může to být libovolný typ definovaný v projektu nebo odkazované sestavení.

## <a name="param"></a>\<param>

Použijte značku `<param>` k popisu parametrů metody. Zde je příklad na metodě Double `Add`: parametr, který tag popisuje, je určen v atributu **required** `name`.

[!code-csharp[Param Tag](~/samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

## <a name="typeparam"></a>\<typeparam >

Použijete `<typeparam>` tag stejně jako `<param>` tag, ale pro deklarace obecného typu nebo metody pro popis obecného parametru.
Přidejte rychlou obecnou metodu do třídy `Math`, abyste zkontrolovali, jestli je jedno množství větší než jiné.

[!code-csharp[Typeparam Tag](~/samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

## <a name="paramref"></a>\<paramref >

Někdy se může stát, že popíšete, co metoda v co by mohla být značka `<summary>` a můžete chtít vytvořit odkaz na parametr. Označení `<paramref>` je skvělé jenom pro tento. Pojďme aktualizovat souhrn naší metody s dvojitou přesností `Add`. Podobně jako značka `<param>` je název parametru zadán v atributu **required** `name`.

[!code-csharp[Paramref Tag](~/samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

## <a name="typeparamref"></a>\<typeparamref >

Použijete `<typeparamref>` tag stejně jako `<paramref>` tag, ale pro deklarace obecného typu nebo metody pro popis obecného parametru.
Můžete použít stejnou obecnou metodu, kterou jste vytvořili dříve.

[!code-csharp[Typeparamref Tag](~/samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

## <a name="list"></a>seznam \<

Pomocí značky `<list>` můžete formátovat informace o dokumentaci jako seřazený seznam, neuspořádaný seznam nebo tabulku. Vytvořte neuspořádaný seznam každé matematické operace, kterou podporuje knihovna `Math`.

[!code-csharp[List Tag](~/samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

Seřazený seznam nebo tabulku můžete vytvořit tak, že změníte atribut `type` na `number` nebo `table`, v uvedeném pořadí.

## <a name="inheritdoc"></a>\<inheritdoc >

Můžete použít značku `<inheritdoc>` k dědění komentářů XML ze základních tříd, rozhraní a podobných metod. Tím se eliminuje nechtěné kopírování a vkládání duplicitních komentářů XML a automaticky se synchronizují komentáře XML.

[!code-csharp-interactive[InheritDoc Tag](~/samples/snippets/csharp/concepts/codedoc/inheritdoc-tag.cs)]

### <a name="put-it-all-together"></a>Spojení všech součástí dohromady

Pokud jste postupovali podle tohoto kurzu a v případě potřeby použili značky v kódu, váš kód by měl nyní vypadat podobně jako následující:

[!code-csharp[Tagged Library](~/samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

Z kódu můžete vygenerovat podrobný web dokumentace s dalšími odkazy, které lze kliknutím Procházet. Ale máte s ním jiný problém: váš kód se těžko čte.
K dispozici je mnoho informací, které by bylo možné proprosévání, takže se jedná o Nightmare pro každého vývojáře, který chce přispívat k tomuto kódu.
Naštěstí se značka XML, která vám může pomáhat s tímto:

## <a name="include"></a>\<zahrnout >

Značka `<include>` umožňuje odkazování na komentáře v samostatném souboru XML, který popisuje typy a členy ve zdrojovém kódu, na rozdíl od umístění komentářů k dokumentaci přímo do souboru zdrojového kódu.

Nyní se chystáte přesunout všechny značky XML do samostatného souboru XML s názvem `docs.xml`. Bez ohledu na název souboru si ho pojmenujte.

[!code-xml[Sample XML](~/samples/snippets/csharp/concepts/codedoc/include.xml)]

Ve výše uvedeném kódu XML se komentáře k dokumentaci jednotlivých členů zobrazují přímo uvnitř značky s názvem, a to podle toho, co dělají. Můžete zvolit vlastní strategii.
Teď, když máte komentáře XML v samostatném souboru, Podívejme se, jak může být váš kód čitelnější pomocí značky `<include>`:

[!code-csharp[Include Tag](~/samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

A tam máte: náš kód je zpátky čitelný a neztratily se žádné informace o dokumentaci.

Atribut `file` představuje název souboru XML obsahujícího dokumentaci.

Atribut `path` představuje dotaz [XPath](../standard/data/xml/xpath-queries-and-namespaces.md) do `tag name` přítomného v zadaném `file`.

Atribut `name` představuje specifikátor názvu ve značce, která předchází komentář.

Atribut `id`, který lze použít místo `name`, představuje ID značky, která předchází komentář.

### <a name="user-defined-tags"></a>Uživatelsky definované značky

Všechny značky, které jsou uvedeny výše, představují ty, které jsou rozpoznávány C# kompilátorem. Uživatel však může definovat vlastní značky.
Nástroje jako Sandcastle přinášejí podporu pro další značky, jako je například [\<> události](https://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm) a [\<Poznámka >](https://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm), a dokonce podporují [dokumentování názvů](https://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).
Je také možné použít vlastní nebo interní nástroje pro tvorbu dokumentace se standardními značkami a více výstupních formátů z formátu HTML do formátu PDF.

## <a name="recommendations"></a>Doporučení

Dokumentování kódu se doporučuje z mnoha důvodů. Níže jsou uvedeny některé osvědčené postupy, obecné scénáře použití a věci, které byste měli znát při použití značek dokumentace XML ve vašem C# kódu.

- V zájmu konzistence by měly být zdokumentovány všechny veřejně viditelné typy a jejich členové. Pokud to musíte udělat, udělejte to vše.
- Soukromé členy lze také zdokumentovat pomocí komentářů XML. To však zpřístupňuje vnitřní (potenciálně důvěrné) pracovní účely vaší knihovny.
- Minimální typy a jejich členové by měli mít `<summary>` značku, protože její obsah je potřebný pro IntelliSense.
- Text dokumentace by měl být napsán pomocí úplných vět končících s úplnými pozastávkami.
- Částečné třídy jsou plně podporovány a informace o dokumentaci budou zřetězeny do jediné položky pro daný typ.
- Kompilátor ověřuje syntaxi značek `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>`a `<typeparam>`.
- Kompilátor ověřuje parametry, které obsahují cesty k souborům a odkazy na jiné části kódu.

## <a name="see-also"></a>Viz také:

- [Komentáře dokumentace XML (C# Průvodce programováním)](programming-guide/xmldoc/index.md)
- [Doporučené značky pro dokumentační komentáře (C# Průvodce programováním)](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
