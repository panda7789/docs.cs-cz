---
title: Doporučené postupy pro vývoj aplikací připravených k použití
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- global applications, best practices
- world-ready applications, best practices
- globalization [.NET Framework], best practices
- international applications [.NET Framework], best practices
ms.assetid: f08169c7-aad8-4ec3-9a21-9ebd3b89986c
ms.openlocfilehash: f0e5ccf999b6aa96b6317b88e25f3cd9d9fbc899
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279877"
---
# <a name="best-practices-for-developing-world-ready-applications"></a>Osvědčené postupy pro vývoj aplikací připravených pro použití ve světě

Tato část popisuje osvědčené postupy, které je třeba provést při vývoji aplikací připravených pro použití ve světě.

## <a name="globalization-best-practices"></a>Osvědčené postupy globalizace

1. Zajistěte, aby byla aplikace Unicode interně.

2. Použijte třídy podporující jazykovou verzi poskytované <xref:System.Globalization> oborem názvů k manipulaci s daty a jejich formátování.

    - Pro řazení použijte <xref:System.Globalization.SortKey> třídu a <xref:System.Globalization.CompareInfo> třídu.

    - Pro porovnávání řetězců použijte <xref:System.Globalization.CompareInfo> třídu.

    - Pro formátování data a času použijte <xref:System.Globalization.DateTimeFormatInfo> třídu.

    - Pro formátování čísel použijte <xref:System.Globalization.NumberFormatInfo> třídu.

    - U gregoriánských a negregoriánských kalendářů použijte <xref:System.Globalization.Calendar> třídu nebo jednu z konkrétních implementací kalendáře.

3. Použijte nastavení vlastností jazykové verze poskytované <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> třídou v příslušných situacích. Použijte <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> vlastnost pro formátování úkolů, jako je datum a čas nebo formátování čísel. <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType>K načtení prostředků použijte vlastnost. Všimněte si, `CurrentCulture` že `CurrentUICulture` vlastnosti a lze nastavit na vlákno.

4. Umožněte vaší aplikaci číst a zapisovat data z různých kódování pomocí tříd kódování v <xref:System.Text> oboru názvů. Nepředpokládají data ASCII. Předpokládá, že mezinárodní znaky budou dodány kdekoliv, kde může uživatel zadat text. Například aplikace by měla přijímat mezinárodní znaky v názvech serverů, adresářích, názvech souborů, uživatelských jménech a adresách URL.

5. Při použití <xref:System.Text.UTF8Encoding> třídy z bezpečnostních důvodů použijte funkci detekce chyb, kterou nabízí tato třída. Chcete-li zapnout funkci detekce chyb, vytvořte instanci třídy pomocí konstruktoru, který převezme `throwOnInvalidBytes` parametr a nastavte hodnotu tohoto parametru na `true` .

6. Kdykoli je to možné, zpracujte řetězce jako celé řetězce namísto řady jednotlivých znaků. To je obzvláště důležité při řazení nebo hledání podřetězců. Tím zabráníte problémům spojeným s analýzou kombinovaných znaků. Můžete také pracovat s jednotkami textu namísto jednotlivých znaků pomocí <xref:System.Globalization.StringInfo?displayProperty=nameWithType> třídy.

7. Zobrazí text pomocí tříd poskytovaných <xref:System.Drawing> oborem názvů.

8. Pro konzistenci mezi operačními systémy nepovolujte uživatelské nastavení k přepsání <xref:System.Globalization.CultureInfo> . Použijte `CultureInfo` konstruktor, který přijímá `useUserOverride` parametr a nastavte jej na `false` .

9. Otestujte funkčnost aplikace na mezinárodních verzích operačního systému pomocí mezinárodních dat.

10. Je-li rozhodnutí o zabezpečení založeno na výsledku porovnání řetězců nebo operaci změny velikosti písmen, použijte operaci s řetězci nezávislou na jazykové verzi. Tento postup zajišťuje, že výsledek není ovlivněn hodnotou `CultureInfo.CurrentCulture` . Viz ["porovnání řetězců, které používají aktuální jazykovou verzi"](../base-types/best-practices-strings.md#string-comparisons-that-use-the-current-culture) v tématu [osvědčené postupy pro použití řetězců](../base-types/best-practices-strings.md) pro příklad, který ukazuje, jak porovnávání řetězců závislé na jazykové verzi může způsobit nekonzistentní výsledky.

## <a name="localization-best-practices"></a>Osvědčené postupy lokalizace

1. Přesuňte všechny lokalizovatelné prostředky do samostatných knihoven DLL pouze prostředků. Lokalizovatelné prostředky zahrnují prvky uživatelského rozhraní, jako jsou například řetězce, chybové zprávy, dialogová okna, nabídky a prostředky vloženého objektu.

2. Nenekódujte pevně řetězce nebo prostředky uživatelského rozhraní.

3. Neumísťujte nelokalizovatelné prostředky do knihoven DLL pouze prostředků. To způsobuje nejasnost pro překladatele.

4. Nepoužívejte složené řetězce, které jsou vytvořeny v době běhu ze zřetězených frází. Složené řetězce je obtížné lokalizovat, protože často předpokládají anglickou gramatickou objednávku, která se nevztahuje na všechny jazyky.

5. Vyhněte se nejednoznačným konstrukcím, jako je "prázdná složka", kde lze řetězce přeložit různě v závislosti na gramatických rolích komponent řetězce. Například "Empty" může být buď operace, nebo adjektivum, což může vést k různým překlady v jazycích, jako je italština nebo francouzština.

6. Vyhněte se použití obrázků a ikon, které obsahují text v aplikaci. Je náročné je lokalizovat.

7. Povolí dostatek místa pro rozšíření řetězců v uživatelském rozhraní na délku. V některých jazycích můžou fráze vyžadovat 50-75 procent více místa, než potřebují v jiných jazycích.

8. Použijte <xref:System.Resources.ResourceManager?displayProperty=nameWithType> třídu pro načtení prostředků na základě jazykové verze.

9. Pomocí sady [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) můžete vytvářet model Windows Forms dialogová okna, aby je bylo možné lokalizovat pomocí [editoru model Windows Forms prostředků (Winres. exe)](../../framework/tools/winres-exe-windows-forms-resource-editor.md). Nevytvářejte kód model Windows Forms dialogová okna ručně.

10. Uspořádejte pro profesionální lokalizaci (překlad).

11. Úplný popis vytváření a lokalizace prostředků najdete v tématu [prostředky v aplikacích](../../framework/resources/index.md).

## <a name="globalization-best-practices-for-aspnet-applications"></a>Osvědčené postupy globalizace pro aplikace ASP.NET

1. Explicitně nastavte <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> vlastnosti a <xref:System.Globalization.CultureInfo.CurrentCulture%2A> ve vaší aplikaci. Nespoléhá se na výchozí hodnoty.

2. Všimněte si, že aplikace ASP.NET jsou spravované aplikace, a proto mohou používat stejné třídy jako jiné spravované aplikace pro načítání, zobrazování a manipulaci s informacemi na základě jazykové verze.

3. Mějte na paměti, že v ASP.NET můžete zadat následující tři typy kódování:

    - requestEncoding určuje kódování přijaté z prohlížeče klienta.

    - responseEncoding určuje kódování, které se odešle do prohlížeče klienta. Ve většině případů by toto kódování mělo být stejné, jako je určeno pro requestEncoding.

    - Kódování souboru určuje výchozí kódování pro analýzu souborů. aspx,. asmx a. asax.

4. Zadejte hodnoty pro atributy requestEncoding, responseEncoding, Encoding, Culture a uiCulture na následujících třech místech aplikace ASP.NET:

    - V sekci globalizace v souboru Web. config. Tento soubor je z aplikace ASP.NET externí. Další informace naleznete v tématu [ \<globalization> element](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hy4kkhe0(v=vs.100)).

    - V direktivě stránky. Všimněte si, že když je aplikace na stránce, soubor již byl přečten. Proto je příliš pozdě zadat kódování a requestEncoding. V direktivě stránky lze zadat pouze uiCulture, Culture a responseEncoding.

    - Programově v kódu aplikace. Toto nastavení se může u jednotlivých požadavků lišit. Stejně jako u direktivy stránky, v době, kdy je dosaženo kódu aplikace, je příliš pozdě zadat kódování a requestEncoding. V kódu aplikace lze zadat pouze uiCulture, Culture a responseEncoding.

5. Všimněte si, že hodnota uiCulture může být nastavena na jazyk přijmout prohlížeč.

## <a name="see-also"></a>Viz také

- [Globalizace a lokalizace](index.md)
- [Prostředky v aplikacích klasické pracovní plochy](../../framework/resources/index.md)
