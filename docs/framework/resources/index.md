---
title: Prostředky v aplikacích .NET
ms.date: 07/25/2018
helpviewer_keywords:
- deploying applications [.NET Framework], resources
- deploying applications [.NET Core], resources
- application resources
- resource files
- satellite assemblies
- localization
- packaging application resources
- localizing resources
ms.assetid: 8ad495d4-2941-40cf-bf64-e82e85825890
ms.openlocfilehash: f7db871c6643973ab18a5bb6bbfac7ab85a11a76
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75346744"
---
# <a name="resources-in-net-apps"></a>Prostředky v aplikacích .NET

Téměř každá aplikace v produkční kvalitě musí využívat prostředky. Prostředek je všechna nespustitelná data, která jsou logicky nasazená s aplikací. Prostředek může být zobrazen v aplikaci jako chybové zprávy nebo jako součást uživatelského rozhraní. Prostředky mohou obsahovat data v řadě formulářů, včetně řetězců, obrázků a trvalých objektů. (Chcete-li zapsat trvalé objekty do souboru prostředků, musí být objekty serializovatelné.) Ukládání dat v souboru prostředků umožňuje změnit data bez nutnosti opětovné kompilace celé aplikace. Umožňuje také ukládat data na jednom místě a eliminuje potřebu spoléhat se na pevně zakódovaná data uložená na více místech.

Rozhraní .NET Framework a .NET Core poskytují komplexní podporu pro vytváření a lokalizaci prostředků. Kromě toho .NET podporuje jednoduchý model pro balení a nasazování lokalizovaných prostředků.

Informace o prostředcích v ASP.NET naleznete v [tématu ASP.NET Přehled zdrojů webové stránky](https://docs.microsoft.com/previous-versions/aspnet/ms227427(v=vs.100)).

## <a name="create-and-localize-resources"></a>Vytváření a lokalizaci prostředků

V nelokalizované aplikaci můžete použít soubory prostředků jako úložiště pro data aplikací, zejména pro řetězce, které by jinak mohly být pevně zakódované ve více umístěních ve zdrojovém kódu. Nejčastěji vytváříte prostředky jako soubory textu (.txt) nebo XML (.resx) a pomocí [resgen.exe (Resource File Generator)](../tools/resgen-exe-resource-file-generator.md) je zkompilujete do binárních souborů .resources. Tyto soubory pak mohou být vloženy do spustitelného souboru aplikace kompilátorem jazyka. Další informace o vytváření prostředků naleznete v [tématu Creating Resource Files](creating-resource-files-for-desktop-apps.md).

Můžete také lokalizovat prostředky aplikace pro konkrétní jazykové verze. To vám umožní vytvářet lokalizované (přeložené) verze aplikací. Při vývoji aplikace, která používá lokalizované prostředky, určíte jazykovou verzi, která slouží jako neutrální nebo záložní jazyková verze, jejíž prostředky se používají, pokud nejsou k dispozici žádné vhodné prostředky. Prostředky neutrální jazykové verze jsou obvykle uloženy ve spustitelném souboru aplikace. Zbývající prostředky pro jednotlivé lokalizované jazykové verze jsou uloženy v samostatných satelitních sestaveních. Další informace naleznete [v tématu Vytváření satelitních sestavení](creating-satellite-assemblies-for-desktop-apps.md).

## <a name="package-and-deploy-resources"></a>Balení a nasazování prostředků

Lokalizované prostředky aplikací nasadíte v [satelitních sestaveních](packaging-and-deploying-resources-in-desktop-apps.md). Satelitní sestavení obsahuje prostředky jedné jazykové verze; neobsahuje žádný kód aplikace. V modelu nasazení satelitní sestavení vytvoříte aplikaci s jedním výchozím sestavením (což je obvykle hlavní sestavení) a jedno satelitní sestavení pro každou jazykovou verzi, kterou aplikace podporuje. Vzhledem k tomu, že satelitní sestavení nejsou součástí hlavního sestavení, můžete snadno nahradit nebo aktualizovat prostředky odpovídající konkrétní jazykové verzi bez nahrazení hlavního sestavení aplikace.

Pečlivě určete, které prostředky budou tvořeny výchozí sestavení prostředků aplikace. Vzhledem k tomu, že je součástí hlavní sestavy, budou všechny změny v ní vyžadovat výměnu hlavní sestavy. Pokud nezadáte výchozí prostředek, bude vyvolána výjimka, když se [proces záložního prostředku](packaging-and-deploying-resources-in-desktop-apps.md) pokusí najít. V dobře navržené aplikaci by použití prostředků nikdy nemělo vyvolat výjimku.

Další informace naleznete v článku [Balení a nasazení prostředků.](packaging-and-deploying-resources-in-desktop-apps.md)

## <a name="retrieve-resources"></a>Načítání prostředků

Za běhu aplikace načte příslušné lokalizované prostředky na základě vlákna na <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> základě jazykové verze určené vlastností. Tato hodnota vlastnosti je odvozena takto:

- Přímým přiřazením <xref:System.Globalization.CultureInfo> objektu, který představuje lokalizovanou jazykovou verzi vlastnosti. <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType>

- Pokud jazyková verze není explicitně přiřazena, načtením <xref:System.Globalization.CultureInfo.DefaultThreadCurrentUICulture%2A?displayProperty=nameWithType> výchozí verze uživatelského rozhraní vlákna z vlastnosti.

- Pokud není explicitně přiřazena výchozí jazyková verze uživatelského rozhraní vlákna, načtením jazykové verze pro aktuálního uživatele v místním počítači. Implementace rozhraní .NET spuštěné v systému Windows to provést voláním funkce systému Windows. [`GetUserDefaultUILanguage`](/windows/desktop/api/winnls/nf-winnls-getuserdefaultuilanguage)

Další informace o nastavení aktuální jazykové verze <xref:System.Globalization.CultureInfo> <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> uj.

Potom můžete načíst prostředky pro aktuální jazykovou verzi uj. <xref:System.Resources.ResourceManager?displayProperty=nameWithType> Přestože <xref:System.Resources.ResourceManager> se třída nejčastěji používá pro <xref:System.Resources?displayProperty=nameWithType> načítání prostředků, obor názvů obsahuje další typy, které můžete použít k načtení prostředků. Mezi ně patří:

- Třída, <xref:System.Resources.ResourceReader> která umožňuje vytvořit výčet prostředků vložených do sestavení nebo uložených v samostatném binárním souboru .resources. Je užitečné, pokud neznáte přesné názvy prostředků, které jsou k dispozici za běhu.

- Třída, <xref:System.Resources.ResXResourceReader> která umožňuje načíst prostředky ze souboru XML (.resx).

- Třída, <xref:System.Resources.ResourceSet> která umožňuje načíst prostředky konkrétní jazykové verze bez dodržování záložních pravidel. Prostředky mohou být uloženy v sestavení nebo samostatném binárním souboru .resources. Můžete také vyvinout implementaci, <xref:System.Resources.IResourceReader> která <xref:System.Resources.ResourceSet> umožňuje použít třídu k načtení prostředků z jiného zdroje.

- Třída, <xref:System.Resources.ResXResourceSet> která umožňuje načíst všechny položky v souboru prostředků XML do paměti.

## <a name="see-also"></a>Viz také

- <xref:System.Globalization.CultureInfo>
- <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType>
- [Základy vytváření aplikací](../../standard/application-essentials.md)
- [Vytváření zdrojových souborů](creating-resource-files-for-desktop-apps.md)
- [Zabalení a nasazení prostředků](packaging-and-deploying-resources-in-desktop-apps.md)
- [Vytváření satelitních sestavení](creating-satellite-assemblies-for-desktop-apps.md)
- [Načítání prostředků](retrieving-resources-in-desktop-apps.md)
