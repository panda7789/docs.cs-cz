---
title: Dokumentace kódu pomocí komentářů XML
description: Zjistěte, jak váš kód, který se dokumentační komentáře XML dokumentu a generovat soubor dokumentace XML v době kompilace.
ms.date: 02/14/2017
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.openlocfilehash: e211543a6a5cc5f6f29d8c195492b474eb24a38d
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2018
ms.locfileid: "47397056"
---
# <a name="documenting-your-code-with-xml-comments"></a>Dokumentace kódu pomocí komentářů XML

Dokumentační komentáře XML jsou zvláštním druhem komentáře přidané v předchozím kroku definice uživatelem definovaného typu nebo člena.
Jsou speciální, protože mohou být zpracovány kompilátor generuje soubor dokumentace XML v době kompilace.
Soubor XML generované kompilátorem lze distribuovat spolu s sestavení .NET, tak, aby sada Visual Studio a jiná Integrovaná vývojová prostředí pomocí technologie IntelliSense můžete zobrazit rychlé informace o typech nebo členech. Kromě toho lze spustit soubor XML prostřednictvím nástrojů jako [DocFX](https://dotnet.github.io/docfx/) a [Sandcastle](https://github.com/EWSoftware/SHFB) ke generování websites referenční dokumentace rozhraní API.

Dokumentační komentáře XML, stejně jako všechny ostatní komentáře ignorovány kompilátorem.

Soubor XML v době kompilace můžete vygenerovat pomocí jedné z následujících akcí:

- Pokud vyvíjíte aplikaci .NET Core z příkazového řádku, můžete přidat [DocumentationFile element](https://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-properties) k `<PropertyGroup>` část souboru projektu CSPROJ. Následující příklad generuje soubor XML v adresáři projektu se stejným názvem kořenového jako sestavení:

   ```xml
   <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\$(AssemblyName).xml</DocumentationFile>
   ```

   Můžete také zadat přesné absolutní nebo relativní cestu a název souboru XML. Následující příklad generuje soubor XML ve stejném adresáři jako ladicí verze aplikace:

   ```xml
   <DocumentationFile>bin\Debug\netcoreapp2.1\App.xml</DocumentationFile>
   ```

- Pokud vyvíjíte aplikace pomocí sady Visual Studio, klikněte pravým tlačítkem na projekt a vyberte **vlastnosti**. V dialogovém okně Vlastnosti vyberte **sestavení** kartě a zaškrtněte **soubor dokumentace XML**. Můžete také změnit umístění, do které kompilátor zapíše soubor.

- Pokud kompilujete aplikace rozhraní .NET Framework z příkazového řádku, přidejte [/doc – možnost kompilátoru](language-reference/compiler-options/doc-compiler-option.md) při kompilaci.  

Dokumentační komentáře XML používat Trojitá lomítka (`///`) a XML formátovaný text komentáře. Příklad:

[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a>Názorný postup

Projděme si velmi základní matematické knihovny k tomu, aby noví vývojáři pochopit/přispívat a vývojářům třetích stran pomocí dokumentace.

Zde je kód pro jednoduché matematické knihovny:

[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

Ukázka knihovny podporuje čtyři hlavní aritmetické operace `add`, `subtract`, `multiply` a `divide` na `int` a `double` datové typy.

Nyní chcete být schopni vytvořit dokument referenční dokumentace rozhraní API z kódu pro vývojáře třetích stran, kteří používají knihovny ale nemají přístup ke zdrojovému kódu.
Jak jsme už zmínili starší dokumentační značky XML je možné dosáhnout, jste nyní seznámili s standard podporuje kompilátoru značky jazyka C# jazyka XML.

### <a name="ltsummarygt"></a>&lt;Souhrn&gt;

`<summary>` Značka přidá stručné informace o typu nebo členu.
Vám předvedu jeho použití tak, že ji přidáte `Math` třídy definice a první `Add` metody. Můžete použít i pro zbývající část kódu.

[!code-csharp[Summary Tag](../../samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

`<summary>` Značka je velmi důležité, a doporučujeme, abyste ho použili protože obsah není primární zdroj informací pro typ nebo člen v IntelliSense nebo dokument referenční dokumentace rozhraní API.

### <a name="ltremarksgt"></a>&lt;Poznámky&gt;

`<remarks>` Značky doplňuje informace o typech nebo členech, který `<summary>` poskytuje značky. V tomto příkladu budete stačí přidat jej do třídy.

[!code-csharp[Remarks Tag](../../samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

### <a name="ltreturnsgt"></a>&lt;Vrátí&gt;

`<returns>` Značky popisuje vrácenou hodnotu deklarace metody.
Jak předtím následující příklad ukazuje `<returns>` značky na první `Add` metoda. Můžete provést stejný na jiné metody.

[!code-csharp[Returns Tag](../../samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

### <a name="ltvaluegt"></a>&lt;value&gt;

`<value>` Značka je podobný `<returns>` značku, s tím rozdílem, že ji použijete k vlastnosti.
Za předpokladu, že vaše `Math` knihovny měl statickou vlastnost s názvem `PI`, zde je, jak můžete využít tuto značku:

[!code-csharp[Value Tag](../../samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

### <a name="ltexamplegt"></a>&lt;Příklad&gt;

Můžete použít `<example>` značka, které zahrnují příklad v dokumentaci XML.
To zahrnuje použití podřízených `<code>` značky.

[!code-csharp[Example Tag](../../samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

`code` Zachová značka konce řádků a odsazení delší příklady.

### <a name="ltparagt"></a>&lt;para&gt;

Můžete použít `<para>` značku k naformátování obsahu v rámci své nadřazené značky. `<para>` obvykle slouží uvnitř značky, například `<remarks>` nebo `<returns>`, k rozdělení textového na odstavcích.
Obsah můžete naformátovat `<remarks>` značky pro vaší definice třídy.

[!code-csharp[Para Tag](../../samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

### <a name="ltcgt"></a>&lt;c&gt;

Stále na téma formátování, použijte `<c>` značky pro označení část textu jako kód.
Je třeba `<code>` značky, ale vložená. To je užitečné, pokud chcete zobrazit příklad rychlý kód jako součást obsahu na značku.
Umožňuje aktualizovat dokumentaci pro `Math` třídy.

[!code-csharp[C Tag](../../samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

### <a name="ltexceptiongt"></a>&lt;Výjimka&gt;

S použitím `<exception>` značky, informovat vaše vývojáře, metoda může vyvolat specifických výjimek.
Na vaše `Math` knihovny, vidíme, že oba `Add` metody vyvolání výjimky, pokud je splněna určitá podmínka. Není to zřejmé, je však tento celé číslo `Divide` metoda vyvolá také, pokud `b` parametru je nula. Nyní přidáte výjimky dokumentace v této metodě.

[!code-csharp[Exception Tag](../../samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

`cref` Atributu představuje odkaz na výjimku, která je k dispozici z prostředí aktuální kompilace.
To může být libovolný typ definovaný v projektu nebo v odkazovaném sestavení. Kompilátor vydá upozornění, pokud jeho hodnotu nelze přeložit.

### <a name="ltseegt"></a>&lt;V tématu&gt;

`<see>` Značky vám umožní vytvářet prokliknutelný odkaz na stránku dokumentace pro jiný element kódu. V našem dalším příkladu vytvoříme prokliknutelný odkaz mezi těmito dvěma `Add` metody.

[!code-csharp[See Tag](../../samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

`cref` Je **požadované** atribut, který představuje odkaz na typ nebo jeho člen, který je k dispozici z prostředí aktuální kompilace.
To může být libovolný typ definovaný v projektu nebo v odkazovaném sestavení.

### <a name="ltseealsogt"></a>&lt;Viz také&gt;

Můžete použít `<seealso>` značka stejným způsobem provedete `<see>` značky. Jediným rozdílem je, že jeho obsah je obvykle umístěn v části "V části Viz také". Tady přidáme `seealso` značku na celé číslo `Add` metoda odkazovat na jiné metody ve třídě, které přijímají celočíselné parametry:

[!code-csharp[Seealso Tag](../../samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

`cref` Atributu představuje odkaz na typ nebo jeho člen, který je k dispozici z prostředí aktuální kompilace.
To může být libovolný typ definovaný v projektu nebo v odkazovaném sestavení.

### <a name="ltparamgt"></a>&lt;Param&gt;

Můžete použít `<param>` značka, které popisují parametry metody. Tady je příklad, double `Add` metoda: Parametr popisuje značka je zadán v **požadované** `name` atribut.

[!code-csharp[Param Tag](../../samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

### <a name="lttypeparamgt"></a>&lt;typeparam&gt;

Použijete `<typeparam>` označit stejně jako `<param>` značky, ale pro obecný typ nebo metoda deklarace k popisu obecný parametr.
Přidat rychlé obecnou metodu pro vaše `Math` třídy zkontrolujte, jestli jedna množství je větší než druhý.

[!code-csharp[Typeparam Tag](../../samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

### <a name="ltparamrefgt"></a>&lt;paramref&gt;

V některých případech může být uprostřed popisující, co dělá metodu v co může být `<summary>` značku a budete chtít vytvořit odkaz na parametr. `<paramref>` Značky se skvěle hodí pro právě to. Pojďme na základě aktualizace souhrn naše double `Add` metody. Podobně jako `<param>` značky název parametru je zadán v **požadované** `name` atribut.

[!code-csharp[Paramref Tag](../../samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

### <a name="lttypeparamrefgt"></a>&lt;typeparamref&gt;

Použijete `<typeparamref>` označit stejně jako `<paramref>` značky, ale pro obecný typ nebo metoda deklarace k popisu obecný parametr.
Můžete použít stejné obecné metody, které jste dříve vytvořili.

[!code-csharp[Typeparamref Tag](../../samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

### <a name="ltlistgt"></a>&lt;list&gt;

Můžete použít `<list>` značku a informací o formátování dokumentaci jako uspořádaného seznamu, neuspořádaný seznam nebo tabulku.
Ujistěte se, Neseřazený seznam všech matematické operace vaše `Math` knihovna podporuje.

[!code-csharp[List Tag](../../samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

Můžete dělat seřazený seznam nebo tabulku můžete změnit `type` atribut `number` nebo `table`v uvedeném pořadí.

### <a name="putting-it-all-together"></a>Vložení všechno dohromady

Pokud jste postupovali podle tohoto kurzu a v případě potřeby použít značky pro váš kód, váš kód by teď měl vypadat nějak takto:

[!code-csharp[Tagged Library](../../samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

V kódu můžete vygenerovat kompletní s křížovými odkazy kliknout, čímž podrobnou dokumentaci webu. Ale se potýkají s dalším problémem: váš kód přestal těžko čitelný.
Existuje mnoho informace probrat se, že to bude připomínající každý vývojář, který chce, abyste mohli přispívat na tento kód.
Naštěstí je značky XML, které vám to vyřešit:

### <a name="ltincludegt"></a>&lt;Zahrnout&gt;

`<include>` Značky umožňuje odkazovat na komentáře v samostatném souboru jazyka XML, které popisují typy a členy ve zdrojovém kódu, na rozdíl od uvedení dokumentační komentáře přímo v souboru zdrojového kódu.

Teď se chystáte přesunout všechny značky XML do samostatného souboru XML s názvem `docs.xml`. Nebojte se, že název souboru cokoliv, co chcete.

[!code-xml[Sample XML](../../samples/snippets/csharp/concepts/codedoc/include.xml)]

V souboru XML výše uvedené se zobrazí každý člen dokumentační komentáře přímo uvnitř značky s názvem po co dělají. Můžete použít vlastní strategii.
Teď, když máte komentáře XML v samostatném souboru, Podívejme se, jak váš kód lze pracovat pomocí `<include>` značky:

[!code-csharp[Include Tag](../../samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

A že máte: našeho kódu je zpět ke a nebyly ztraceny žádné informace o dokumentaci.

`filename` Atribut představuje název souboru XML, který obsahuje dokumentaci.

`path` Atributu představuje [XPath](https://msdn.microsoft.com/library/ms256115.aspx) dotaz pro `tag name` k dispozici v zadaném `filename`.

`name` Atribut představuje název specifikátor ve značce, který předchází komentáře.

`id` Atribut, který lze použít místo `name` představuje ID značky, které předchází komentáře.

### <a name="user-defined-tags"></a>Uživatelem definované značky

Všechny značky uvedených výše představují ty, které jsou rozpoznány modulem pro kompilátor jazyka C#. Uživatel je však můžete definovat jejich vlastní značky.
Nástroje, jako je Sandcastle přenést podpory pro další značky, jako jsou [ `<event>` ](http://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm), [ `<note>` ](http://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) a dokonce i podporu [dokumentace obory názvů](http://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).
Vlastní nebo nástroje pro generování interní dokumentace lze také pomocí standardních značek a může podporovat více formátů výstupu z HTML do formátu PDF.

## <a name="recommendations"></a>Doporučení

Dokumentace kódu se doporučuje pro mnoho důvodů, proč. Následují některé osvědčené postupy, hlavní scénáře použití a věci, které byste měli znát při použití dokumentace XML značky v kódu jazyka C#.

* Pro účely konzistence musí být zdokumentována všechny veřejně viditelné typy a jejich členy. Pokud musíte to provést, to všechno.
* Soukromé členy můžete rovněž popsány pomocí komentářů XML. Nicméně tato třída zveřejňuje vnitřní (potenciálně důvěrné) fungování své knihovny.
* Minimálně, by měly mít typy a členové `<summary>` značku, protože jeho obsah je potřeba pro technologii IntelliSense.
* Text dokumentace by měly být zapsány pomocí úplných větách končí plně zastaví.
* Částečné třídy jsou plně podporované a informace o dokumentaci se nedá zřetězit do jedna položka u tohoto typu.
* Kompilátor ověří syntaxi `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>` a `<typeparam>` značky.
- Kompilátor ověří parametry, které obsahují cesty k souborům a odkazy na ostatní části kódu.

## <a name="see-also"></a>Viz také:

* [XML – dokumentační komentáře (C# Programming Guide)](programming-guide/xmldoc/xml-documentation-comments.md)
* [Doporučené značky pro dokumentační komentáře (C# Programming Guide)](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
