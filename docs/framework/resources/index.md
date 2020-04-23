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
ms.openlocfilehash: 0620cb16c3233f8ba2a665c9c4cb5f44bc5d5e84
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645682"
---
# <a name="resources-in-net-apps"></a>Prostředky v aplikacích .NET

Skoro každá aplikace v produkční kvalitě musí používat prostředky. Prostředek je jakákoli nespustitelná data, která jsou logicky nasazena s aplikací. Prostředek se může v aplikaci zobrazit jako chybové zprávy nebo jako součást uživatelského rozhraní. Prostředky mohou obsahovat data v několika formách, včetně řetězců, obrázků a trvalých objektů. (Pro zápis trvalých objektů do souboru prostředků musí být objekty serializovatelné.) Uložení dat do souboru prostředků umožňuje změnit data, aniž by bylo nutné znovu kompilovat celou aplikaci. Umožňuje také ukládat data do jednoho umístění a eliminovat nutnost spoléhat na pevně zakódované údaje, které jsou uloženy na více místech.

.NET Framework a .NET Core poskytují komplexní podporu pro vytváření a lokalizaci prostředků. Rozhraní .NET navíc podporuje jednoduchý model pro balení a nasazování lokalizovaných prostředků.

Informace o prostředcích v ASP.NET najdete v tématu [Přehled prostředků webové stránky ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/ms227427(v=vs.100)).

## <a name="create-and-localize-resources"></a>Vytváření a lokalizace prostředků

V nelokalizované aplikaci můžete použít soubory prostředků jako úložiště pro data aplikací, zejména pro řetězce, které by jinak byly pevně zakódované v několika umístěních ve zdrojovém kódu. Nejčastěji vytváříte prostředky jako textový soubor (. txt) nebo soubory XML (. resx) a pomocí nástroje [Resgen. exe (generátor souborů prostředků)](../tools/resgen-exe-resource-file-generator.md) je zkompilujete do binárních souborů. Resources. Tyto soubory pak mohou být vloženy do spustitelného souboru aplikace kompilátorem jazyka. Další informace o vytváření prostředků najdete v tématu [vytváření souborů prostředků](creating-resource-files-for-desktop-apps.md).

Prostředky vaší aplikace můžete také lokalizovat pro konkrétní jazykové verze. To umožňuje vytvářet lokalizované (přeložené) verze vašich aplikací. Když vyvíjíte aplikaci, která používá lokalizované prostředky, určíte jazykovou verzi, která slouží jako neutrální nebo záložní jazyková verze, jejíž prostředky jsou používány, pokud nejsou k dispozici žádné vhodné prostředky. Prostředky neutrální jazykové verze se obvykle ukládají ve spustitelném souboru aplikace. Zbývající prostředky pro jednotlivé lokalizované jazykové verze jsou uloženy v samostatných satelitních sestaveních. Další informace naleznete v tématu [Vytváření satelitních sestavení](creating-satellite-assemblies-for-desktop-apps.md).

## <a name="package-and-deploy-resources"></a>Balení a nasazování prostředků

Lokalizované prostředky aplikace nasadíte do [satelitních sestavení](packaging-and-deploying-resources-in-desktop-apps.md). Satelitní sestavení obsahuje prostředky jediné jazykové verze; neobsahuje žádný kód aplikace. V modelu nasazení satelitního sestavení vytvoříte aplikaci s jedním výchozím sestavením (což je obvykle hlavní sestavení) a jedním satelitním sestavením pro každou jazykovou verzi, kterou aplikace podporuje. Vzhledem k tomu, že satelitní sestavení nejsou součástí hlavního sestavení, můžete snadno nahradit nebo aktualizovat prostředky odpovídající konkrétní jazykové verzi, aniž byste museli nahradit hlavní sestavení aplikace.

Pečlivě určete, které prostředky budou vytvářet výchozí sestavení prostředků vaší aplikace. Vzhledem k tomu, že je součástí hlavního sestavení, všechny změny v ní budou vyžadovat, abyste nahradili hlavní sestavení. Pokud nezadáte výchozí prostředek, vyvolá se výjimka, když se [záložní proces prostředku](packaging-and-deploying-resources-in-desktop-apps.md) pokusí ho najít. V dobře navržené aplikaci nesmí použití prostředků nikdy vyvolat výjimku.

Další informace najdete v článku o [balení a nasazení prostředků](packaging-and-deploying-resources-in-desktop-apps.md) .

## <a name="retrieve-resources"></a>Načítání prostředků

V době běhu aplikace načte příslušné lokalizované prostředky na základě vlákna na základě jazykové verze určené <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> vlastností. Hodnota této vlastnosti je odvozena takto:

- Přímým přiřazením <xref:System.Globalization.CultureInfo> objektu, který představuje lokalizovanou jazykovou <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> verzi vlastnosti.

- Pokud není jazyková verze explicitně přiřazena, načtením výchozí jazykové verze uživatelského rozhraní vlákna z <xref:System.Globalization.CultureInfo.DefaultThreadCurrentUICulture%2A?displayProperty=nameWithType> vlastnosti.

- Pokud výchozí jazyková verze uživatelského rozhraní vlákna není explicitně přiřazena, načtením jazykové verze pro aktuálního uživatele v místním počítači. Implementace rozhraní .NET spuštěné v systému Windows provede voláním funkce [`GetUserDefaultUILanguage`](/windows/desktop/api/winnls/nf-winnls-getuserdefaultuilanguage) Windows.

Další informace o nastavení aktuální jazykové verze uživatelského rozhraní naleznete na <xref:System.Globalization.CultureInfo> referenčních stránkách a <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> .

Pak můžete načíst prostředky pro aktuální jazykovou verzi uživatelského rozhraní nebo pro konkrétní jazykovou verzi pomocí <xref:System.Resources.ResourceManager?displayProperty=nameWithType> třídy. I když <xref:System.Resources.ResourceManager> je třída nejčastěji používána pro načítání prostředků, <xref:System.Resources?displayProperty=nameWithType> obor názvů obsahuje další typy, které lze použít k načtení prostředků. Mezi ně patří:

- <xref:System.Resources.ResourceReader> Třída, která umožňuje vytvořit výčet prostředků vložených do sestavení nebo Uložit do samostatného binárního souboru. Resources. To je užitečné, pokud neznáte přesné názvy prostředků, které jsou k dispozici v době běhu.

- <xref:System.Resources.ResXResourceReader> Třída, která umožňuje načtení prostředků ze souboru XML (. resx).

- <xref:System.Resources.ResourceSet> Třída, která umožňuje načíst prostředky konkrétní jazykové verze bez pozorování náhradních pravidel. Prostředky mohou být uloženy v sestavení nebo samostatném binárním souboru. Resources. Můžete také vyvinout <xref:System.Resources.IResourceReader> implementaci, která umožňuje použít <xref:System.Resources.ResourceSet> třídu k načtení prostředků z jiného zdroje.

- <xref:System.Resources.ResXResourceSet> Třída, která umožňuje načíst všechny položky v souboru prostředků XML do paměti.

## <a name="see-also"></a>Viz také

- <xref:System.Globalization.CultureInfo>
- <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType>
- [Vytváření zdrojových souborů](creating-resource-files-for-desktop-apps.md)
- [Zabalení a nasazení prostředků](packaging-and-deploying-resources-in-desktop-apps.md)
- [Vytváření satelitních sestavení](creating-satellite-assemblies-for-desktop-apps.md)
- [Načítání prostředků](retrieving-resources-in-desktop-apps.md)
