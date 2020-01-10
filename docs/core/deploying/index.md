---
title: Nasazení aplikace .NET Core
description: Přečtěte si o způsobech nasazení aplikace .NET Core.
ms.date: 12/03/2018
ms.openlocfilehash: 41c5285f2a9ddf38e4be7326bd5cba1c58370fe7
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740820"
---
# <a name="net-core-application-deployment"></a>Nasazení aplikace .NET Core

Pro aplikace .NET Core můžete vytvořit tři typy nasazení:

- Nasazení závislé na rozhraní. Jak naznačuje název, nasazení závislé na rozhraní (FDD) spoléhá na přítomnost sdílené verze .NET Core v rámci systému v cílovém systému. Vzhledem k tomu, že je rozhraní .NET Core již přítomno, aplikace je také přenosná mezi instalacemi rozhraní .NET Core. Vaše aplikace obsahuje pouze vlastní kód a všechny závislosti třetích stran, které jsou mimo knihovny .NET Core. FDDs obsahují soubory *. dll* , které lze spustit pomocí [nástroje dotnet](../tools/dotnet.md) z příkazového řádku. Například `dotnet app.dll` spouští aplikaci s názvem `app`.

- Samostatné nasazení. Na rozdíl od FDD, samostatné nasazení (SCD) nespoléhá na přítomnost sdílených komponent v cílovém systému. Všechny komponenty, včetně knihoven .NET Core a modulu runtime .NET Core, jsou součástí aplikace a jsou izolované od jiných aplikací .NET Core. SCDs obsahují spustitelný soubor (například *App. exe* na platformách systému Windows pro aplikaci s názvem `app`), která je Přejmenovaná verze hostitele .NET Core specifická pro konkrétní platformu a soubor *. dll* (například *App. dll*), což je skutečná aplikace.

- Spustitelné soubory závislé na rozhraní. Vytvoří spustitelný soubor, který běží na cílové platformě. Podobně jako FDDs, spustitelné soubory závislé na rozhraních (FDE) jsou specifické pro platformu a nejsou samostatně obsaženy. Tato nasazení se pořád spoléhají na přítomnost sdílené systémové verze .NET Core, která se má spustit. Na rozdíl od SCD vaše aplikace obsahuje jenom váš kód a všechny závislosti třetích stran, které jsou mimo knihovny .NET Core. FDEs vyprodukuje spustitelný soubor, který běží na cílové platformě.

## <a name="framework-dependent-deployments-fdd"></a>Nasazení závislá na rozhraní (FDD)

V případě FDD nasadíte jenom své aplikace a závislosti třetích stran. Vaše aplikace bude používat verzi .NET Core, která je k dispozici v cílovém systému. Toto je výchozí model nasazení pro .NET Core a aplikace ASP.NET Core, které cílí na .NET Core.

### <a name="why-create-a-framework-dependent-deployment"></a>Proč vytvořit nasazení závislé na rozhraní?

Nasazení FDD má několik výhod:

- Nemusíte definovat cílové operační systémy, na které bude aplikace .NET Core běžet předem. Vzhledem k tomu, že .NET Core používá společný formát PE pro spustitelné soubory a knihovny bez ohledu na operační systém, může .NET Core spustit vaši aplikaci bez ohledu na základní operační systém. Další informace o formátu souboru PE naleznete v tématu [Formát souboru sestavení .NET](../../standard/assembly/file-format.md).

- Velikost balíčku pro nasazení je malá. Nasadíte jenom svou aplikaci a její závislosti, ne samotné .NET Core.

- Pokud přepíšete, FDDs použije nejnovější službu, která je v cílovém systému nainstalovaná. To umožňuje vaší aplikaci používat nejnovější opravenou verzi modulu runtime .NET Core. 

- Více aplikací používá stejnou instalaci .NET Core, což snižuje nároky na místo na disku a využití paměti v hostitelských systémech.

K dispozici je také několik nevýhody:

- Vaše aplikace může běžet pouze v případě, že je v hostitelském systému již nainstalována verze .NET Core vaší aplikace [nebo novější verze](../versions/selection.md#framework-dependent-apps-roll-forward).

- Je možné, že se modul runtime a knihovny .NET Core mění bez vašeho vědomí v budoucích verzích. Ve výjimečných případech to může změnit chování vaší aplikace.

## <a name="self-contained-deployments-scd"></a>Samostatně obsažená nasazení (SCD)

Pro samostatně nasazené nasazení nasadíte aplikaci a všechny požadované závislosti třetích stran spolu s verzí rozhraní .NET Core, kterou jste použili k sestavení aplikace. Vytvoření SCD neobsahuje [nativní závislosti .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) na různých platformách, takže musí být přítomné před spuštěním aplikace. Další informace o vazbách verzí za běhu naleznete v článku [vázání verzí v .NET Core](../versions/selection.md).

Počínaje platformou .NET Core 2,1 SDK (verze 2.1.300) .NET Core podporuje *přeposlání verze opravy*. Když vytvoříte samostatné nasazení, nástroje .NET Core automaticky zahrnují nejnovější provozní modul runtime verze .NET Core, na kterou cílí vaše aplikace. (Nejnovější obsluhované běhové prostředí zahrnuje opravy zabezpečení a další opravy chyb.) Modul runtime služby nemusí být přítomen v systému sestavení; automaticky se stáhne z NuGet.org. Další informace, včetně pokynů k odsouhlasení z aktualizace verze patch, najdete v tématu [nasazení modulu runtime s automatickým](runtime-patch-selection.md)zahrnutím.

Nasazení FDD a SCD používají samostatné spustitelné soubory hostitele, takže můžete podepsat spustitelný soubor hostitele pro SCD s vaším podpisem vydavatele.

### <a name="why-deploy-a-self-contained-deployment"></a>Proč nasadit samostatně zahrnuté nasazení?

Nasazení samostatně zahrnutého nasazení má dvě hlavní výhody:

- Máte jenom kontrolu nad verzí .NET Core, která je nasazená s vaší aplikací. .NET Core se dá obsluhovat jenom vámi.

- Můžete si být jistí, že cílový systém může spustit aplikaci .NET Core, protože poskytujete verzi .NET Core, na které bude běžet.

Má také řadu nevýhod:

- Vzhledem k tomu, že je .NET Core součástí balíčku pro nasazení, musíte vybrat cílové platformy, pro které sestavíte balíčky nasazení předem.

- Velikost balíčku pro nasazení je poměrně velká, protože musíte zahrnout rozhraní .NET Core i aplikace a její závislosti třetích stran.

  Od .NET Core 2,0 můžete zmenšit velikost nasazení v systémech Linux o přibližně 28 MB pomocí [*režimu invariantní globalizace*](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).NET Core. Rozhraní .NET Core v systému Linux obvykle spoléhá na [ICU knihovny](http://icu-project.org) pro podporu globalizace. V režimu invariant nejsou knihovny součástí vašeho nasazení a všechny jazykové verze se chovají jako [invariantní jazyková verze](xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType).

- Nasazením mnoha samostatných aplikací .NET Core do systému můžete využívat značné množství místa na disku, protože každá aplikace duplikuje soubory .NET Core.

## <a name="framework-dependent-executables-fde"></a>Spustitelné soubory závislé na rozhraních (FDE)

Počínaje .NET Core 2,2 můžete nasadit aplikaci jako FDE spolu se všemi požadovanými závislostmi třetích stran. Vaše aplikace bude používat verzi .NET Core, která je nainstalovaná v cílovém systému.

### <a name="why-deploy-a-framework-dependent-executable"></a>Proč nasadit spustitelný soubor závislý na rozhraní?

Nasazení aplikace FDE má několik výhod:

- Velikost balíčku pro nasazení je malá. Nasadíte jenom svou aplikaci a její závislosti, ne samotné .NET Core.

- Více aplikací používá stejnou instalaci .NET Core, což snižuje nároky na místo na disku a využití paměti v hostitelských systémech.

- Vaše aplikace se dá spustit voláním publikovaného spustitelného souboru bez nutnosti vyvolat nástroj `dotnet` přímo.

K dispozici je také několik nevýhody:

- Vaše aplikace může běžet pouze v případě, že je v hostitelském systému již nainstalována verze .NET Core vaší aplikace [nebo novější verze](../versions/selection.md#framework-dependent-apps-roll-forward).

- Je možné, že se modul runtime a knihovny .NET Core mění bez vašeho vědomí v budoucích verzích. Ve výjimečných případech to může změnit chování vaší aplikace.

- Aplikaci musíte publikovat pro každou cílovou platformu.

## <a name="step-by-step-examples"></a>Podrobné příklady

Podrobné příklady nasazení aplikací .NET Core pomocí nástrojů rozhraní příkazového řádku najdete v tématu [nasazení aplikací .NET Core pomocí nástrojů rozhraní](deploy-with-cli.md)příkazového řádku. Podrobné příklady nasazení aplikací .NET Core pomocí sady Visual Studio najdete v tématu [nasazení aplikací .NET Core pomocí sady Visual Studio](deploy-with-vs.md). 

## <a name="see-also"></a>Viz také:

- [Nasazení aplikací .NET Core pomocí nástrojů rozhraní příkazového řádku](deploy-with-cli.md)
- [Nasazení aplikací .NET Core pomocí sady Visual Studio](deploy-with-vs.md)
- [Balíčky, metabalíčky a architektury](../packages.md)
- [Katalog identifikátorů runtime .NET Core (RID)](../rid-catalog.md)
