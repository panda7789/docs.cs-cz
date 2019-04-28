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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d96e223b85178c7f2784a523e5609057d1432488
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61683207"
---
# <a name="best-practices-for-developing-world-ready-applications"></a>Osvědčené postupy pro vývoj globalizovaných aplikací

Tato část popisuje doporučené postupy při vývoji aplikací nasadit kdekoli na světě.

## <a name="globalization-best-practices"></a>Doporučené postupy pro globalizaci

1. Ujistěte se, aplikace kódování Unicode interně.

2. Použití třídy podporující jazykové verze poskytované <xref:System.Globalization> obor názvů pro manipulaci a formátování data.

    - Pro řazení používejte <xref:System.Globalization.SortKey> třídy a <xref:System.Globalization.CompareInfo> třídy.

    - Pro porovnávání řetězců, použijte <xref:System.Globalization.CompareInfo> třídy.

    - Pro formátování data a času, použijte <xref:System.Globalization.DateTimeFormatInfo> třídy.

    - Pro formátování čísel, použijte <xref:System.Globalization.NumberFormatInfo> třídy.

    - Pro gregoriánský kalendář i jiném než gregoriánském kalendáři, použijte <xref:System.Globalization.Calendar> třídy nebo některé z konkrétních implementací kalendáře.

3. Použít nastavení vlastností jazykové verze poskytované <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> třídy ve vhodných situacích. Použití <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> vlastnost pro formátování úlohy, jako je data a času či formátování čísel. Použití <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> vlastnost pro načtení prostředků. Všimněte si, `CurrentCulture` a `CurrentUICulture` vlastnosti můžete nastavit pro vlákno.

4. Umožněte aplikaci číst a zapisovat data do a z různých kódování pomocí tříd kódování v <xref:System.Text> oboru názvů. Nepředpokládejte data ve standardu ASCII. Předpokládejme, že mezinárodní znaky mohou být vloženy kdekoliv může uživatel zadat text. Aplikace například měly přijímat mezinárodní znaky v názvy serverů, adresářů, názvy souborů, uživatelských jmen a adres URL.

5. Při použití <xref:System.Text.UTF8Encoding> tříd, z bezpečnostních důvodů, použijte funkci rozpoznávání chyb nabízenou touto třídou. Zapnutí funkce rozpoznávání chyb, vytvoření instance třídy pomocí konstruktoru, který přijímá `throwOnInvalidBytes` parametr a hodnotu tohoto parametru na `true`.

6. Kdykoli je to možné, zpracovávejte řetězce jako celé řetězce namísto jednotlivých znaků. To je důležité zejména při řazení nebo vyhledání podřetězců. Tím zabráníte problémům spojeným s analýzou kombinovaných znaků. Jednotky text spíše než jednotlivé znaky může také pracovat s použitím <xref:System.Globalization.StringInfo?displayProperty=nameWithType> třídy.

7. Zobrazujte text pomocí tříd poskytovaných oborem <xref:System.Drawing> oboru názvů.

8. Pro konzistenci mezi operačními systémy, nejsou povoleny uživatelskému nastavení přepsat <xref:System.Globalization.CultureInfo>. Použití `CultureInfo` konstruktor, který přijímá `useUserOverride` parametr a nastavte ho na `false`.

9. Otestujte funkčnost aplikace na mezinárodních verzích operačního systému, použitím mezinárodních dat.

10. Pokud je rozhodnutí o zabezpečení založeno na výsledku porovnání řetězců nebo operaci změny velikosti písmen, pomocí operace s řetězci nezávislé na jazykové verzi. Tento postup zajišťuje, že výsledek není ovlivněn hodnotou z `CultureInfo.CurrentCulture`. Najdete v článku ["Řetězec porovnání, které používají aktuální jazykovou verzi"](../../../docs/standard/base-types/best-practices-strings.md#string-comparisons-that-use-the-current-culture) část [osvědčené postupy pro používání řetězců](../../../docs/standard/base-types/best-practices-strings.md) příklad, který ukazuje, jak jazykové řetězce může vést k porovnání nekonzistentní výsledky.

## <a name="localization-best-practices"></a>Doporučené postupy pro lokalizaci

1. Přesuňte všechny lokalizovatelné prostředky do oddělených knihoven DLL určených pouze prostředků. Lokalizovatelné prostředky zahrnují prvky uživatelského rozhraní, jako je například řetězce, chybové zprávy, dialogová okna, nabídky a prostředky vložených objektů.

2. To není napevno do kódu řetězce nebo prostředky uživatelského rozhraní.

3. Neumísťujte nelokalizovatelné prostředky do knihovny DLL pouze prostředků. Toto mate překladatele.

4. Proveďte složené řetězce, které jsou vytvořeny v době běhu ze spojených frází. Složené řetězce se obtížně lokalizují, protože často předpokládají anglický gramatický slovosled, který se nedá použít u všech jazycích.

5. Vyhněte se dvojznačným konstrukcím, jako je například "Prázdná složka", kdy lze řetězce přeložit odlišně v závislosti na gramatických rolích součástí řetězce. Například "empty" může být příkaz nebo přídavné jméno, což může vést k odlišnému překladu do jazyků, jako je například italština nebo francouzština.

6. Vyhněte se používání obrázků a ikon, které obsahují text ve vaší aplikaci. Je náročné je lokalizovat.

7. Vyhraďte dostatek místa pro delší řetězce v uživatelském rozhraní. V některých jazycích mohou věty vyžadovat o 50-75 procent více prostoru než potřebovat v jiných jazycích.

8. Použití <xref:System.Resources.ResourceManager?displayProperty=nameWithType> třída pro načítání prostředků podle jazykové verze.

9. Použití [sady Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) vytváření formulářů Windows dialogových tak mohly být lokalizovány pomocí [Windows Forms Resource Editor (Winres.exe)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md). Nevytvářejte ručně kód dialogových oken modelu Windows Forms.

10. Zajistěte profesionální lokalizaci (překlad).

11. Úplný popis vytváření a lokalizace prostředků naleznete v tématu [prostředky v aplikacích](../../../docs/framework/resources/index.md).

## <a name="globalization-best-practices-for-aspnet-applications"></a>Doporučené postupy pro globalizaci aplikací technologie ASP.NET

1. Explicitně nastavit <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> a <xref:System.Globalization.CultureInfo.CurrentCulture%2A> vlastnosti ve vaší aplikaci. Nespoléhejte na výchozí hodnoty.

2. Mějte na paměti, že aplikace ASP.NET jsou spravované aplikace a proto můžete použít stejné třídy jako jiné spravované aplikace pro načítání, zobrazování a manipulaci s informacemi na základě jazykové verze.

3. Mějte na paměti, že můžete zadat následující tři typy kódování v technologii ASP.NET:

    - requestEncoding určuje kódování přijímané z prohlížeče klienta.

    - responseEncoding určuje kódování odesílané do prohlížeče klienta. Ve většině případů toto kódování mělo být stejné jako requestEncoding.

    - fileEncoding určuje výchozí kódování pro .aspx, .asmx a .asax souborů.

4. Zadejte hodnoty pro atributy requestEncoding, responseEncoding, fileEncoding, culture a uiCulture na následujících třech místech v aplikaci technologie ASP.NET:

    - V oddíle globalizace v souboru Web.config. Tento soubor je externí aplikace technologie ASP.NET. Další informace najdete v tématu [ \<globalization > prvek](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hy4kkhe0(v=vs.100)).

    - V direktivě stránky. Všimněte si, že když se aplikace nachází na stránce, soubor již byl načten. Proto je příliš pozdě zadat fileEncoding a requestEncoding. V direktivě stránky lze zadat pouze uiCulture, Culture a responseEncoding.

    - Programově v kódu aplikace. Toto nastavení se může lišit dle požadavku. Jak u direktivy stránky, době aplikace je dosaženo kódu je příliš pozdě zadat fileEncoding a requestEncoding. V kódu aplikace lze zadat pouze uiCulture, Culture a responseEncoding.

5. Všimněte si, že hodnotu uiCulture lze nastavit v prohlížeči jazyk přijímaný.

## <a name="see-also"></a>Viz také:

- [Globalizace a lokalizace](../../../docs/standard/globalization-localization/index.md)
- [Prostředky v desktopových aplikacích](../../../docs/framework/resources/index.md)
