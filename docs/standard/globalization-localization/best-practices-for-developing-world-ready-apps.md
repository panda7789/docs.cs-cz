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
ms.openlocfilehash: a2cd1039f95a763002922fc2fa24eff77838de80
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141296"
---
# <a name="best-practices-for-developing-world-ready-applications"></a>Osvědčené postupy pro vývoj aplikací připravených pro svět

Tato část popisuje osvědčené postupy, které je třeba dodržovat při vývoji aplikací připravených pro svět.

## <a name="globalization-best-practices"></a>Osvědčené postupy globalizace

1. Vytvořte aplikaci Unicode interně.

2. Pomocí tříd podporujících jazykovou <xref:System.Globalization> verzi poskytovaných oborem názvů můžete manipulovat s daty a formátovat je.

    - Pro řazení použijte <xref:System.Globalization.SortKey> třídu <xref:System.Globalization.CompareInfo> a třídu.

    - Pro porovnání řetězců použijte <xref:System.Globalization.CompareInfo> třídu.

    - Pro formátování data a času <xref:System.Globalization.DateTimeFormatInfo> použijte třídu.

    - Pro číselné formátování použijte <xref:System.Globalization.NumberFormatInfo> třídu.

    - Pro gregoriánské a negregoriánské kalendáře <xref:System.Globalization.Calendar> použijte třídu nebo jednu z konkrétních implementací kalendáře.

3. Použijte nastavení vlastnosti jazykové <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> verze poskytované třídou v příslušných situacích. <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> Vlastnost použijte pro formátování úloh, jako je datum a čas nebo číselné formátování. Pomocí <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> vlastnosti načtěte prostředky. Všimněte `CurrentCulture` si, že vlastnosti a `CurrentUICulture` lze nastavit na vlákno.

4. Umožněte aplikaci číst a zapisovat data do a z různých <xref:System.Text> kódování pomocí tříd kódování v oboru názvů. Nepředpokládejte data ASCII. Předpokládejme, že mezinárodní znaky budou dodány kdekoli, kde může uživatel zadat text. Aplikace by například měla přijímat mezinárodní znaky v názvech serverů, adresářích, názvech souborů, uživatelských jménech a adresách URL.

5. Při použití <xref:System.Text.UTF8Encoding> třídy, z bezpečnostních důvodů, použijte funkci zjišťování chyb, kterou nabízí tato třída. Chcete-li zapnout funkci zjišťování chyb, vytvořte instanci `throwOnInvalidBytes` třídy pomocí konstruktoru, `true`který přebírá parametr a nastavte hodnotu tohoto parametru na .

6. Kdykoli je to možné, zpracovat řetězce jako celé řetězce namísto jako řada jednotlivých znaků. To je obzvláště důležité při řazení nebo hledání podřetězců. Tím se zabrání problémům spojeným s analýzou kombinovaných znaků. Pomocí třídy můžete také pracovat s jednotkami <xref:System.Globalization.StringInfo?displayProperty=nameWithType> textu, nikoli s jedním znakem.

7. Zobrazení textu pomocí tříd poskytovaných oborem <xref:System.Drawing> názvů.

8. Chcete-li provést konzistenci mezi operačními <xref:System.Globalization.CultureInfo>systémy, nepovolit přepsání uživatelských nastavení . Použijte `CultureInfo` konstruktor, který `useUserOverride` přijímá parametr a `false`nastavte jej na .

9. Otestujte funkce aplikace na verzích mezinárodních operačních systémů pomocí mezinárodních dat.

10. Pokud rozhodnutí o zabezpečení je založena na výsledku porovnání řetězců nebo případ operace, použijte operaci řetězce necitlivé na jazykové verzi. Tento postup zajišťuje, že výsledek není ovlivněn `CultureInfo.CurrentCulture`hodnotou . Naleznete [v části "Porovnání řetězců, které používají aktuální jazykovou verzi"](../../../docs/standard/base-types/best-practices-strings.md#string-comparisons-that-use-the-current-culture) [doporučené postupy pro použití řetězce](../../../docs/standard/base-types/best-practices-strings.md) příklad, který ukazuje, jak porovnání řetězců citlivých na jazykovou verzi může způsobit nekonzistentní výsledky.

## <a name="localization-best-practices"></a>Doporučené postupy lokalizace

1. Přesuňte všechny lokalizovatelné prostředky do samostatných knihoven DLL pouze pro prostředky. Lokalizovatelné prostředky zahrnují prvky uživatelského rozhraní, jako jsou řetězce, chybové zprávy, dialogová okna, nabídky a prostředky vložených objektů.

2. Nepoužívejte pevně zakódované řetězce nebo prostředky uživatelského rozhraní.

3. Nevložte nelokalizovatelné prostředky do knihoven DLL pouze pro prostředky. To způsobuje zmatek pro překladatele.

4. Nepoužívejte složené řetězce, které jsou vytvořeny za běhu z zřetězených frází. Složené řetězce je obtížné lokalizovat, protože často předpokládají anglické gramatické pořadí, které se nevztahuje na všechny jazyky.

5. Vyhněte se nejednoznačné konstrukce, jako je například "Prázdná složka", kde řetězce mohou být přeloženy odlišně v závislosti na gramatické role komponent řetězce. Například "prázdný" může být sloveso nebo přídavné jméno, což může vést k různým překladům v jazycích, jako je například italština nebo francouzština.

6. Nepoužívejte obrázky a ikony, které obsahují text v aplikaci. Jsou drahé lokalizovat.

7. Ponechte dostatek místa pro délku řetězců rozšířit v uživatelském rozhraní. V některých jazycích mohou fráze vyžadovat o 50–75 procent více místa, než potřebují v jiných jazycích.

8. Pomocí <xref:System.Resources.ResourceManager?displayProperty=nameWithType> třídy načtěte prostředky založené na jazykové verzi.

9. Pomocí [sady Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) můžete vytvořit dialogová okna formulářů systému Windows, aby mohla být lokalizována pomocí [Editoru prostředků windows forms (Winres.exe).](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md) Dialogová okna Formuláře systému Windows nekódujte ručně.

10. Zajistit profesionální lokalizaci (překlad).

11. Úplný popis vytváření a lokalizace prostředků naleznete v tématu [Prostředky v aplikacích](../../../docs/framework/resources/index.md).

## <a name="globalization-best-practices-for-aspnet-applications"></a>Osvědčené postupy globalizace pro ASP.NET aplikace

1. Explicitně <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> nastavte <xref:System.Globalization.CultureInfo.CurrentCulture%2A> vlastnosti a ve vaší aplikaci. Nespoléhejte na výchozí hodnoty.

2. Všimněte si, že ASP.NET aplikace jsou spravované aplikace, a proto můžete použít stejné třídy jako jiné spravované aplikace pro načítání, zobrazení a manipulaci s informacemi na základě jazykové verze.

3. Uvědomte si, že můžete zadat následující tři typy kódování v ASP.NET:

    - requestEncoding určuje kódování přijaté z prohlížeče klienta.

    - responseEncoding určuje kódování, které má být odesláno do prohlížeče klienta. Ve většině situací by toto kódování mělo být stejné jako kódování určené pro requestEncoding.

    - fileEncoding určuje výchozí kódování pro analýzu souborů ASPX, ASMX a ASAX.

4. Zadejte hodnoty pro atributy requestEncoding, responseEncoding, fileEncoding, culture a uiCulture na následujících třech místech v ASP.NET aplikaci:

    - V části globalizace souboru Web.config. Tento soubor je mimo aplikaci ASP.NET. Další informace naleznete v [ \<tématu globalizace> Element](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hy4kkhe0(v=vs.100)).

    - V direktivě stránky. Všimněte si, že když je aplikace na stránce, soubor již byl přečten. Proto je příliš pozdě zadat fileEncoding a requestEncoding. Pouze uiCulture, Kultura a responseEncoding lze zadat v direktivě stránky.

    - Programově v kódu aplikace. Toto nastavení se může lišit podle požadavku. Stejně jako u direktivy stránky, v době, kdy je dosaženo kódu aplikace je příliš pozdě zadat fileEncoding a requestEncoding. V kódu aplikace lze zadat pouze uiCulture, Culture a responseEncoding.

5. Všimněte si, že hodnotu uiCulture lze nastavit na jazyk pro přijetí prohlížeče.

## <a name="see-also"></a>Viz také

- [Globalizace a lokalizace](../../../docs/standard/globalization-localization/index.md)
- [Prostředky v aplikacích klasické pracovní plochy](../../../docs/framework/resources/index.md)
