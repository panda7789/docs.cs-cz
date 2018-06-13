---
title: Dokumentace kódu s XML – komentáře
description: Informace o dokumentu kódu s XML – dokumentační komentáře a generování souborů dokumentace XML v době kompilace.
ms.date: 02/14/2017
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.openlocfilehash: 1284f179c7debb323ea3bbd302df1f02bf8b31b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218502"
---
# <a name="documenting-your-code-with-xml-comments"></a>Dokumentace kódu s XML – komentáře

Dokumentační komentáře XML je zvláštní druh komentář, přidané v předchozím kroku definici uživatelem definovaný typ nebo člen. Jsou speciální, protože může být zpracována kompilátorem ke generování souborů dokumentace XML v době kompilace.
Kompilátoru vygeneruje soubor XML lze distribuovat souběžně s vaší sestavení .NET, tak, aby Visual Studio a dalších integrovaného vývojového prostředí pomocí technologie IntelliSense můžete zobrazit rychlé informace o typech nebo členy. Kromě toho lze spustit soubor XML prostřednictvím nástrojů, například [DocFX](https://dotnet.github.io/docfx/) a [aplikaci Sandcastle](https://github.com/EWSoftware/SHFB) ke generování weby referenční dokumentace rozhraní API.

Dokumentační komentáře XML, podobně jako všechny ostatní komentáře se ignorují kompilátorem.

Soubor XML můžete vygenerovat v době kompilace pomocí jedné z následujících akcí:

- Pokud vyvíjíte aplikace s .NET Core z příkazového řádku, můžete přidat [DocumentationFile element](http://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-properties) k `<PropertyGroup>` části souboru .csproj projektů. Následující příklad vytvoří soubor XML v adresáři projektu s stejný název kořenového souboru jako sestavení:

   ```xml
   <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\$(AssemblyName).xml</DocumentationFile>
   ```

   Můžete také zadat přesné absolutní nebo relativní cesta a název souboru XML. Následující příklad vytvoří soubor XML ve stejném adresáři jako ladicí verze aplikace:

    ```xml
   <DocumentationFile>bin\Debug\netcoreapp1.0\App.xml</DocumentationFile>
   ```

- Pokud vyvíjíte aplikace pomocí sady Visual Studio, klikněte pravým tlačítkem na projekt a vyberte **vlastnosti**. V dialogovém okně Vlastnosti, vyberte **sestavení** a zkontrolujte **souborů dokumentace XML**. Můžete také změnit umístění, do které kompilátor zapíše soubor. 

- Pokud jsou kompilace rozhraní .NET Framework aplikace z příkazového řádku, přidejte [/doc – možnost kompilátoru](language-reference/compiler-options/doc-compiler-option.md) při kompilaci.  

XML – dokumentační komentáře použít Trojitá lomítka (`///`) a XML formátovaný text komentáře. Příklad:

[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a>Návod

Projděme dokumentace knihovnu velmi základní matematické usnadnili pro nové vývojáře pochopit přispívat a třetích stran vývojářům používat.

Tady je kód pro knihovnu jednoduché matematické:

[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

Ukázka knihovna podporuje čtyři hlavní aritmetické operace `add`, `subtract`, `multiply` a `divide` na `int` a `double` datové typy.

Nyní chcete být schopni vytvořit dokument referenční dokumentace rozhraní API z vašeho kódu pro vývojáře třetích stran, kteří použít knihovnu, ale nemáte přístup ke zdrojovému kódu.
Jako uvedených starší dokumentační značky XML lze použít k dosažení tohoto cíle, můžete nyní zavedl na standardní podporuje kompilátoru značky jazyka C# jazyka XML.

### <a name="ltsummarygt"></a>&lt;Souhrn&gt;

`<summary>` Značka přidá stručné informace o typ nebo člen.
I budete přidáním k předvedení jeho použití `Math` třídy definice a první `Add` metoda. Nebojte se, že platí pro zbytek vašeho kódu.

[!code-csharp[Summary Tag](../../samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

`<summary>` Značka je velmi důležité, a doporučujeme, abyste ho použili vzhledem k tomu, že její obsah není primární zdroj informací pro typ nebo člen v IntelliSense nebo dokument referenční dokumentace rozhraní API.

### <a name="ltremarksgt"></a>&lt;Poznámky&gt;

`<remarks>` Značky doplňuje informace o typech nebo členy, `<summary>` poskytuje značky. V tomto příkladu budete stačí přidat ji do třídy.

[!code-csharp[Remarks Tag](../../samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

### <a name="ltreturnsgt"></a>&lt;Vrátí&gt;

`<returns>` Značky popisuje vrácenou hodnotu deklarace metody.
Jak před, následující příklad ukazuje `<returns>` značky v prvním `Add` metoda. Můžete provést stejný na jiné metody.

[!code-csharp[Returns Tag](../../samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

### <a name="ltvaluegt"></a>&lt;value&gt;

`<value>` Značka je podobná `<returns>` značka, s tím rozdílem, že použijete pro vlastnosti.
Za předpokladu, že vaše `Math` knihovny měl statickou vlastnost s názvem `PI`, zde je, jak použijete tuto značku:

[!code-csharp[Value Tag](../../samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

### <a name="ltexamplegt"></a>&lt;Příklad&gt;

Můžete použít `<example>` značka, které zahrnují příklady v dokumentaci k XML.
To zahrnuje použití podřízených `<code>` značky.

[!code-csharp[Example Tag](../../samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

`code` Značky zachovává konce řádků a odsazení delší příklady.

### <a name="ltparagt"></a>&lt;Para&gt;

Můžete použít `<para>` značky k formátování obsahu v rámci své nadřazené značky. `<para>` obvykle používá uvnitř značky, jako například `<remarks>` nebo `<returns>`, k rozdělení text do odstavcích.
Můžete ho naformátovat obsah `<remarks>` značky pro vaše definice třídy.

[!code-csharp[Para Tag](../../samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

### <a name="ltcgt"></a>&lt;c&gt;

Ještě na téma formátování, můžete použít `<c>` značky pro označení součástí textu jako kód.
Je třeba `<code>` značky, ale vložené. Je vhodné, pokud chcete zobrazit příklad rychlé kódu v rámci obsah značky.
Umožňuje aktualizovat v dokumentaci `Math` třídy.

[!code-csharp[C Tag](../../samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

### <a name="ltexceptiongt"></a>&lt;Výjimka&gt;

Pomocí `<exception>` značky, umožníte vaší vývojáři vědět, že metoda může vyvolat konkrétní výjimky.
Prohlížení vaší `Math` knihovny, můžete uvidíte, že oba `Add` metody vyvolána výjimka, pokud je splněna určitá podmínka. Není proto zřejmé, je ale, že celé číslo `Divide` metoda zjistí také, zda `b` parametr je nulová. Nyní přidejte výjimka dokumentaci k této metodě.

[!code-csharp[Exception Tag](../../samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

`cref` Atribut představuje odkaz na výjimku, která je k dispozici z aktuální prostředí kompilace.
Může to být libovolný typ definovaný v projektu nebo odkazované sestavení. Kompilátor vás upozorní, pokud jeho hodnotu nelze přeložit.

### <a name="ltseegt"></a>&lt;V tématu&gt;

`<see>` Značka umožňuje vytvářet prokliknutelný odkaz na stránku dokumentace pro jiný element kódu. V našem příkladu další vytvoříme prokliknutelný odkaz mezi těmito dvěma `Add` metody.

[!code-csharp[See Tag](../../samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

`cref` Je **požadované** atribut, který představuje odkaz na typ nebo jeho člena, který je k dispozici z aktuální prostředí kompilace. Může to být libovolný typ definovaný v projektu nebo odkazované sestavení.

### <a name="ltseealsogt"></a>&lt;Viz také&gt;

Můžete použít `<seealso>` značky stejným způsobem, jako je provést `<see>` značky. Jediným rozdílem je, že jeho obsah je obvykle umístěny v části "V části Viz také". Zde přidáme `seealso` značky na celé číslo `Add` metoda tak, aby odkazovaly jiných metod ve třídě, které přijímají celé číslo parametry:

[!code-csharp[Seealso Tag](../../samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

`cref` Atribut představuje odkaz na typ nebo jeho člena, který je k dispozici z aktuální prostředí kompilace.
Může to být libovolný typ definovaný v projektu nebo odkazované sestavení.

### <a name="ltparamgt"></a>&lt;Param&gt;

Můžete použít `<param>` značka, které popisují parametry metody. Tady je příklad na dvojitého `Add` metoda: je zadaný parametr popisuje značky v **požadované** `name` atribut.

[!code-csharp[Param Tag](../../samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

### <a name="lttypeparamgt"></a>&lt;typeparam&gt;

Používáte `<typeparam>` značky podobně jako `<param>` značky, ale pro obecný typ nebo metoda deklarace k popisu obecný parametr.
Přidání rychlé obecné metody pro vaše `Math` třídy ke kontrole, pokud jeden množství je větší než jiné.

[!code-csharp[Typeparam Tag](../../samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

### <a name="ltparamrefgt"></a>&lt;paramref&gt;

V některých případech může být uprostřed popisující metodu provádí v co může být `<summary>` značku a budete chtít vytvořit odkaz na parametr. `<paramref>` Značka je skvělá pro právě to. Umožňuje na základě aktualizace souhrn naše dvojitou `Add` metoda. Jako `<param>` značky je zadaný název parametru v **požadované** `name` atribut.

[!code-csharp[Paramref Tag](../../samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

### <a name="lttypeparamrefgt"></a>&lt;typeparamref&gt;

Používáte `<typeparamref>` značky podobně jako `<paramref>` značky, ale pro obecný typ nebo metoda deklarace k popisu obecný parametr.
Můžete použít stejné obecné metody, které jste vytvořili.

[!code-csharp[Typeparamref Tag](../../samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

### <a name="ltlistgt"></a>&lt;list&gt;

Můžete použít `<list>` značky na formát dokumentaci informace jako uspořádaného seznamu, neuspořádaný seznam nebo tabulky.
Ujistěte se, neuspořádaný seznam každé matematické operace vaše `Math` knihovna podporuje.

[!code-csharp[List Tag](../../samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

Můžete nastavit uspořádaný seznam nebo tabulka změnou `type` atribut `number` nebo `table`, v uvedeném pořadí.

### <a name="putting-it-all-together"></a>Třeba umisťovat všechny společně

Pokud jste postupovali podle tohoto kurzu a použili značky v kódu potřeby, váš kód by teď měl vypadat podobně jako následující:

[!code-csharp[Tagged Library](../../samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

Z vašeho kódu můžete vygenerovat podrobnou dokumentaci webu, který je kompletní s prokliknutelný křížové odkazy. Ale se potýkají s dalším problémem: kódu se stal těžko čitelný.
Existuje mnoho informace, které procházet, že to bude při důvodů pro všechny vývojáře, kdo chce podílet se na tento kód. Naštěstí je značky XML, který můžete zpracovat takové:

### <a name="ltincludegt"></a>&lt;Zahrnout&gt;

`<include>` Umožňuje značka odkazovat komentáře v samostatném souboru XML, které popisují typy a členy ve zdrojovém kódu, na rozdíl od umístění dokumentační komentáře ve zdrojovém kódu souboru přímo.

Teď se chystáte přesunout všechny značky XML do samostatného souboru XML s názvem `docs.xml`. Nebojte se, že jste název souboru libovolně.

[!code-xml[Sample XML](../../samples/snippets/csharp/concepts/codedoc/include.xml)]

Ve výše uvedené souboru XML zobrazí dokumentační komentáře každý člen přímo uvnitř značky s názvem po co dělají. Můžete si vlastní strategii. Nyní když máte komentáře XML v samostatném souboru, podíváme se, jak váš kód můžete provést srozumitelnější pomocí `<include>` značky:

[!code-csharp[Include Tag](../../samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

A že máte: Naše kód je zpět do probíhá čtení a žádné informace dokumentace bylo ztraceno. 

`filename` Atribut představuje název souboru XML, který obsahuje v dokumentaci.

`path` Atribut představuje [XPath](https://msdn.microsoft.com/library/ms256115.aspx) dotazy s cílem `tag name` přítomen v zadané `filename`.

`name` Atribut představuje název specifikátor ve značce, která předchází komentáře.

`id` Atribut, který může být použit místo `name` reprezentuje ID pro značku, která předchází komentáře.

### <a name="user-defined-tags"></a>Uživatelem definované značky

Všechny značky uvedených výše představují ty, které jsou rozpoznáno kompilátor jazyka C#. Uživatel je však můžete definovat vlastní značky.
Nástroje, například aplikaci Sandcastle přineste podpory pro další značky [ `<event>` ](http://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm), [ `<note>` ](http://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) a i podpora [dokumentace obory názvů](http://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).
Vlastní nebo nástroje pro generování interní dokumentace lze také standardní značkami a může podporovat více formátů výstup z kódu HTML do PDF.

## <a name="recommendations"></a>Doporučení

Dokumentace kódu se doporučuje z mnoha důvodů. Jaké způsobem jsou některé osvědčené postupy Obecné použijte scénářích případů a další věci, které byste měli vědět, když pomocí dokumentace XML značky v kódu jazyka C#.

* Z důvodu konzistence musí být zdokumentována všechny veřejně viditelný typy a jejich členové. Pokud musíte to provést, proveďte všechny.
* Soukromé členy můžete rovněž popsány pomocí komentáře XML. To však zveřejňuje vnitřního (potenciálně důvěrné) chodu své knihovny.
* Úplné, typy a jejich členové by měl mít minimálně `<summary>` značky, protože jeho obsah je potřeba pro technologii IntelliSense.
* Dokumentace text by měly být zapsány pomocí dokončení věty konče úplné zastaví.
* Částečné třídy jsou plně podporované a dokumentaci informace budou zřetězen do jeden záznam pro tento typ.
* Kompilátor ověřuje syntaxe `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>` a `<typeparam>` značky.
- Kompilátor ověří parametry, které obsahují cesty k souborům a odkazy na další části kódu.

## <a name="see-also"></a>Viz také
[Dokumentační komentáře XML (C# Průvodce programováním)](programming-guide/xmldoc/xml-documentation-comments.md)

[Doporučené značky pro dokumentační komentáře (C# Průvodce programováním)](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
