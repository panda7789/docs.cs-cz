---
title: Dokumentace kódu s komentáři XML
description: Naučte se dokumentovat kód pomocí dokumentačních komentářů XML a generovat soubor dokumentace XML v době kompilace.
ms.date: 02/14/2017
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.openlocfilehash: b6744921f4703f53a16b6bdadcfbf375c2fb3332
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70104774"
---
# <a name="documenting-your-code-with-xml-comments"></a>Dokumentace kódu s komentáři XML

Komentáře dokumentace XML jsou zvláštním druhem komentáře, přidané nad definici libovolného uživatelsky definovaného typu nebo člena.
Jsou speciální, protože mohou být zpracovány kompilátorem pro generování souboru dokumentace XML v době kompilace.
Soubor XML generovaný kompilátorem lze distribuovat společně s sestavením .NET tak, aby Visual Studio a jiné prostředí pro vývoj mohli používat technologii IntelliSense k zobrazení rychlých informací o typech nebo členech. Kromě toho lze spustit soubor XML prostřednictvím nástrojů jako [DocFX](https://dotnet.github.io/docfx/) a [Sandcastle](https://github.com/EWSoftware/SHFB) ke generování websites referenční dokumentace rozhraní API.

Komentáře dokumentace XML, stejně jako všechny ostatní komentáře, jsou kompilátorem ignorovány.

Soubor XML můžete vygenerovat v době kompilace jedním z následujících způsobů:

- Pokud vyvíjíte aplikaci pomocí .NET Core z příkazového řádku, můžete přidat [element DocumentationFile](/visualstudio/msbuild/common-msbuild-project-properties) do `<PropertyGroup>` oddílu souboru projektu. csproj. Následující příklad generuje soubor XML v adresáři projektu se stejným kořenovým názvem souboru jako sestavení:

   ```xml
   <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\$(AssemblyName).xml</DocumentationFile>
   ```

   Můžete také zadat přesný absolutní nebo relativní cestu a název souboru XML. Následující příklad vygeneruje soubor XML ve stejném adresáři jako ladicí verze aplikace:

   ```xml
   <DocumentationFile>bin\Debug\netcoreapp2.1\App.xml</DocumentationFile>
   ```

- Pokud vyvíjíte aplikaci pomocí sady Visual Studio, klikněte pravým tlačítkem na projekt a vyberte **vlastnosti**. V dialogovém okně Vlastnosti vyberte kartu **sestavení** a Prohlédněte si **soubor dokumentace XML**. Můžete také změnit umístění, do kterého kompilátor zapisuje soubor.

- Pokud kompilujete .NET Framework aplikaci z příkazového řádku, přidejte při kompilaci [možnost kompilátoru/doc](language-reference/compiler-options/doc-compiler-option.md) .  

Komentáře dokumentace XML používají tři lomítka (`///`) a tělo komentáře ve formátu XML. Příklad:

[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a>Podrobné

Pojďme si projít dokumentací velmi základní knihovny pro matematiku, která usnadňuje novým vývojářům pochopit/přispět a umožnit vývojářům třetích stran použití.

Tady je kód pro jednoduchou knihovnu Math:

[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

Ukázková knihovna podporuje čtyři hlavní aritmetické `add`operace `subtract` `multiply` , `divide` `int` a a datové typy. `double`

Nyní chcete být schopni vytvořit referenční dokument rozhraní API z kódu pro vývojáře třetích stran, kteří používají vaši knihovnu, ale nemají přístup ke zdrojovému kódu.
Jak bylo zmíněno dříve, můžete k tomuto účelu použít Tagy dokumentace XML. Nyní budete zavedeni do standardních značek XML, které C# podporuje kompilátor.

## <a name="summary"></a>\<summary>

`<summary>` Značka přidá stručné informace o typu nebo členu.
Ukážeme jeho použití tím, že ho přidáte do `Math` definice třídy a první `Add` metody. Nebojte se použít pro zbytek kódu.

[!code-csharp[Summary Tag](../../samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

`<summary>` Označení je velmi důležité a doporučujeme, abyste ho zahrnuli, protože jeho obsah je primárním zdrojem informací o typu nebo členu v IntelliSense nebo dokumentu Reference k rozhraním API.

## <a name="remarks"></a>\<Poznámky >

Tag doplňuje informace o typech nebo členech `<summary>` , které poskytuje značka. `<remarks>` V tomto příkladu ho stačí přidat do třídy.

[!code-csharp[Remarks Tag](../../samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

## <a name="returns"></a>\<returns>

`<returns>` Značka popisuje návratovou hodnotu deklarace metody.
Jak dřív, následující příklad ilustruje `<returns>` značku první `Add` metody. Stejný postup můžete provést i pro jiné metody.

[!code-csharp[Returns Tag](../../samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

## <a name="value"></a>\<value>

Značka je podobná `<returns>` značce, s tím rozdílem, že ji použijete pro vlastnosti. `<value>`
Za předpokladu, že vaše `Math` knihovna má zavolanou `PI`statickou vlastnost, použijte tuto značku:

[!code-csharp[Value Tag](../../samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

## <a name="example"></a>\<Příklad >

`<example>` Značku můžete použít k zahrnutí příkladu do XML dokumentace.
To zahrnuje použití podřízené `<code>` značky.

[!code-csharp[Example Tag](../../samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

`code` Značka zachovává zalomení řádků a odsazení po delších příkladech.

## <a name="para"></a>\<para>

Použijete `<para>` značku k formátování obsahu v rámci své nadřazené značky. `<para>`se obvykle používá uvnitř značky, jako `<remarks>` je například nebo `<returns>`, k rozdělení textu do odstavců.
Můžete naformátovat obsah `<remarks>` značky pro definici třídy.

[!code-csharp[Para Tag](../../samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

## <a name="c"></a>\<c>

Stále v tématu formátování, použijte `<c>` značku pro označení části textu jako kódu.
Vypadá to jako `<code>` značka, ale je vložená. Je užitečné, pokud chcete zobrazit rychlý příklad kódu jako součást obsahu značky.
Pojďme aktualizovat dokumentaci pro `Math` třídu.

[!code-csharp[C Tag](../../samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

## <a name="exception"></a>\<> výjimky

Pomocí `<exception>` značky můžete vývojářům informovat o tom, že metoda může vyvolat konkrétní výjimky.
Při hledání v `Math` knihovně vidíte, že obě `Add` metody vyvolávají výjimku, pokud je splněna určitá podmínka. Není tak zřejmé, ale je to, že `Divide` celočíselná metoda vyvolá i v `b` případě, že je parametr nula. Nyní přidejte do této metody dokumentaci k výjimce.

[!code-csharp[Exception Tag](../../samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

`cref` Atribut představuje odkaz na výjimku, která je k dispozici z aktuálního prostředí kompilace.
Může to být libovolný typ definovaný v projektu nebo odkazované sestavení. Kompilátor vydá upozornění, pokud jeho hodnotu nelze vyřešit.

## <a name="see"></a>\<viz >

`<see>` Značka umožňuje vytvořit odkaz s možnostmi kliknutí na stránku dokumentace pro jiný prvek kódu. V našem dalším příkladu vytvoříme odkaz kliknutí mezi těmito dvěma `Add` způsoby.

[!code-csharp[See Tag](../../samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

Je vyžadovaný atribut, který představuje odkaz na typ nebo jeho člen, který je k dispozici z aktuálního prostředí kompilace. `cref`
Může to být libovolný typ definovaný v projektu nebo odkazované sestavení.

## <a name="seealso"></a>\<SeeAlso >

`<seealso>` Značku můžete použít stejným způsobem `<see>` jako značku. Jediným rozdílem je, že jeho obsah je obvykle umístěn v části "viz také". Tady přidáme `seealso` značku na celočíselnou `Add` metodu, která bude odkazovat na jiné metody ve třídě, které přijímají celočíselné parametry:

[!code-csharp[Seealso Tag](../../samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

`cref` Atribut představuje odkaz na typ nebo jeho člen, který je k dispozici z aktuálního prostředí kompilace.
Může to být libovolný typ definovaný v projektu nebo odkazované sestavení.

## <a name="param"></a>\<param>

Použijte `<param>` značku k popisu parametrů metody. Tady je příklad metody Double `Add` : Parametr, který popisuje tag, je určen v **požadovaném** `name` atributu.

[!code-csharp[Param Tag](../../samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

## <a name="typeparam"></a>\<typeparam >

Použijte `<typeparam>` tag stejně jako tag, `<param>` ale pro deklarace obecného typu nebo metody pro popis obecného parametru.
Přidejte do své `Math` třídy rychlou obecnou metodu, abyste zkontrolovali, jestli je jedno množství větší než jiné.

[!code-csharp[Typeparam Tag](../../samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

## <a name="paramref"></a>\<paramref >

Někdy se může stát, že popíšete, co metoda v co by mohla být `<summary>` značka, a můžete chtít vytvořit odkaz na parametr. `<paramref>` Označení je skvělé jenom pro toto. Pojďme aktualizovat souhrn naší metody založené na `Add` zdvojnásobení. Podobně jako `name` značka je název parametru zadán v požadovaném atributu. `<param>`

[!code-csharp[Paramref Tag](../../samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

## <a name="typeparamref"></a>\<typeparamref >

Použijte `<typeparamref>` tag stejně jako tag, `<paramref>` ale pro deklarace obecného typu nebo metody pro popis obecného parametru.
Můžete použít stejnou obecnou metodu, kterou jste vytvořili dříve.

[!code-csharp[Typeparamref Tag](../../samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

## <a name="list"></a>\<seznam >

Pomocí `<list>` značky můžete formátovat informace o dokumentaci jako seřazený seznam, neuspořádaný seznam nebo tabulku.
Vytvořte neuspořádaný seznam každé matematické operace, kterou vaše `Math` knihovna podporuje.

[!code-csharp[List Tag](../../samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

Seřazený seznam nebo tabulku můžete vytvořit tak, že změníte `type` atribut na `number` nebo `table`v uvedeném pořadí.

### <a name="putting-it-all-together"></a>Společné umístění

Pokud jste postupovali podle tohoto kurzu a v případě potřeby použili značky v kódu, váš kód by měl nyní vypadat podobně jako následující:

[!code-csharp[Tagged Library](../../samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

Z kódu můžete vygenerovat podrobný web dokumentace s dalšími odkazy, které lze kliknutím Procházet. Ale máte s ním jiný problém: váš kód se těžko čte.
K dispozici je mnoho informací, které by bylo možné proprosévání, takže se jedná o Nightmare pro každého vývojáře, který chce přispívat k tomuto kódu.
Naštěstí se značka XML, která vám může pomáhat s tímto:

## <a name="include"></a>\<zahrnout >

`<include>` Značka vám umožní odkazovat na komentáře v samostatném souboru XML, který popisuje typy a členy ve zdrojovém kódu, a to na rozdíl od umístění komentářů k dokumentaci přímo do souboru zdrojového kódu.

Nyní budete přesouvat všechny značky XML do samostatného souboru XML s názvem `docs.xml`. Bez ohledu na název souboru si ho pojmenujte.

[!code-xml[Sample XML](../../samples/snippets/csharp/concepts/codedoc/include.xml)]

Ve výše uvedeném kódu XML se komentáře k dokumentaci jednotlivých členů zobrazují přímo uvnitř značky s názvem, a to podle toho, co dělají. Můžete zvolit vlastní strategii.
Teď, když máte komentáře XML v samostatném souboru, Podívejme se, jak je možné váš kód udělat čitelnější pomocí `<include>` značky:

[!code-csharp[Include Tag](../../samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

A tam máte: náš kód je zpátky čitelný a neztratily se žádné informace o dokumentaci.

`file` Atribut představuje název souboru XML obsahujícího dokumentaci.

Atribut představuje dotaz [XPath](../standard/data/xml/xpath-queries-and-namespaces.md) `tag name` na přítomný v zadaném `file`. `path`

`name` Atribut představuje specifikátor názvu ve značce, který předchází komentář.

Atribut, který lze použít `name` místo představuje ID značky, která předchází komentář. `id`

### <a name="user-defined-tags"></a>Uživatelsky definované značky

Všechny značky, které jsou uvedeny výše, představují ty, které jsou rozpoznávány C# kompilátorem. Uživatel však může definovat vlastní značky.
Nástroje jako Sandcastle přinášejí podporu pro další značky [`<event>`](https://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm), [`<note>`](https://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) jako je, a dokonce podporují dokumentující se [obory názvů](https://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).
Je také možné použít vlastní nebo interní nástroje pro tvorbu dokumentace se standardními značkami a více výstupních formátů z formátu HTML do formátu PDF.

## <a name="recommendations"></a>Doporučení

Dokumentování kódu se doporučuje z mnoha důvodů. Níže jsou uvedeny některé osvědčené postupy, obecné scénáře použití a věci, které byste měli znát při použití značek dokumentace XML ve vašem C# kódu.

- V zájmu konzistence by měly být zdokumentovány všechny veřejně viditelné typy a jejich členové. Pokud to musíte udělat, udělejte to vše.
- Soukromé členy lze také zdokumentovat pomocí komentářů XML. To však zpřístupňuje vnitřní (potenciálně důvěrné) pracovní účely vaší knihovny.
- Minimální typy a jejich členové by měli mít `<summary>` značku, protože její obsah je potřebný pro IntelliSense.
- Text dokumentace by měl být napsán pomocí úplných vět končících s úplnými pozastávkami.
- Částečné třídy jsou plně podporovány a informace o dokumentaci budou zřetězeny do jediné položky pro daný typ.
- Kompilátor `<exception>`ověřuje syntaxi značek, `<include>`, `<param>` `<see>`, a.`<seealso>` `<typeparam>`
- Kompilátor ověřuje parametry, které obsahují cesty k souborům a odkazy na jiné části kódu.

## <a name="see-also"></a>Viz také:

- [Komentáře dokumentace XML (C# Průvodce programováním)](programming-guide/xmldoc/index.md)
- [Doporučené značky pro dokumentační komentáře (C# Průvodce programováním)](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
