---
title: Kdy pro kontejnery Dockeru zvolit .NET Framework
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Kdy zvolit .NET Framework pro kontejnery Docker
ms.date: 01/07/2019
ms.openlocfilehash: 579e1a475b1ce96d98d7a2c521c1296e17b9f42e
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740961"
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a>Kdy pro kontejnery Dockeru zvolit .NET Framework

I když .NET Core nabízí významné výhody pro nové aplikace a vzory aplikací, .NET Framework bude pro mnoho stávajících scénářů nadále dobrou volbou.

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a>Migrace stávajících aplikací přímo do kontejneru Windows serveru

Kontejnery Docker můžete chtít použít jenom ke zjednodušení nasazení, i když nevytváříte mikroslužby. Například můžete chtít zlepšit pracovní postup DevOps pomocí Docker – kontejnery vám poskytnou lepší izolovaná testovací prostředí a můžou také eliminovat problémy s nasazením způsobené chybějícími závislostmi při přesunu do produkčního prostředí. V takových případech, i když nasazujete aplikaci monolitické, má smysl použít pro vaše aktuální aplikace .NET Framework kontejnery Docker a Windows.

Ve většině případů v tomto scénáři nebudete muset migrovat stávající aplikace do .NET Core; můžete použít kontejnery Docker, které zahrnují tradiční .NET Framework. Doporučený postup je však použití .NET Core při rozšiřování existující aplikace, jako je například zápis nové služby v ASP.NET Core.

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>Používání knihoven .NET nebo balíčků NuGet třetích stran není k dispozici pro .NET Core

Knihovny třetích stran rychle přechodu [.NET Standard](../../../standard/net-standard.md), což umožňuje sdílení kódu napříč všemi typy rozhraní .NET, včetně .NET Core. Díky .NET Standard knihovně 2,0 a nad rámec kompatibility povrchu rozhraní API napříč různými architekturami se výrazně zvětšuje a aplikace .NET Core 2. x můžou přímo odkazovat na stávající knihovny .NET Framework (viz [.NET Framework 4.6.1 podporující .NET Standard 2,0](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#net-framework-461-supporting-net-standard-20)).

Kromě toho se [Sada Windows Compatibility Pack](../../../core/porting/windows-compat-pack.md) vydala v listopadu 2017, aby rozšířila plochu rozhraní API dostupnou pro .NET Standard 2,0 ve Windows. Tento balíček umožňuje opětovně kompilovat stávající kód, aby .NET Standard 2. x s minimální nebo žádnou úpravou pro spuštění ve Windows.

Nicméně i s výjimečným průběhem od .NET Standard 2,0 a .NET Core 2,1 mohou nastat případy, kdy některé balíčky NuGet potřebují ke spuštění Windows a nemusí podporovat .NET Core. Pokud jsou tyto balíčky pro vaši aplikaci důležité, budete je muset použít .NET Framework v kontejnerech Windows.

## <a name="using-net-technologies-not-available-for-net-core"></a>Používání technologií .NET není k dispozici pro .NET Core

Některé technologie .NET Framework nejsou k dispozici v aktuální verzi .NET Core (verze 2,2 v tomto zápisu). Některé z nich budou dostupné v novějších verzích .NET Core (.NET Core 2. x), ale ostatní se nevztahují na nové vzory aplikací, na které cílí .NET Core, a nemusí být nikdy dostupné.

V následujícím seznamu jsou uvedeny většinu technologií, které nejsou k dispozici v rozhraní .NET Core 2. x:

- ASP.NET webové formuláře. Tato technologie je k dispozici pouze na .NET Framework. V současné době nejsou k dispozici žádné plány k uvedení webových formulářů ASP.NET do .NET Core.

- Služby WCF. I v případě, že je k dispozici [Knihovna WCF-Client](https://github.com/dotnet/wcf) pro využívání služeb WCF od .NET Core, od střední 2017 je implementace serveru WCF dostupná jenom na .NET Framework. Tento scénář je možné zvážit v budoucích vydáních .NET Core, ale v sadě [Windows Compatibility Pack](../../../core/porting/windows-compat-pack.md)jsou k dispozici i některá rozhraní API, která se považují za zařazování.

- Služby související s pracovním postupem. Programovací model Windows Workflow Foundation (WF), služby pracovních postupů (WCF + WF v jedné službě) a WCF Data Services (dříve označované jako ADO.NET Data Services) jsou k dispozici pouze na .NET Framework. V současné době nejsou k dispozici žádné plány pro jejich uvedení do .NET Core.

Kromě technologií uvedených v oficiálním plánu [.NET Core](https://github.com/aspnet/Home/wiki/Roadmap)můžou být další funkce přepravované na .NET Core. Úplný seznam najdete v položkách označených jako [port-to-Core](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core) na webu GitHubu CoreFX. Všimněte si, že tento seznam nepředstavuje závazek společnosti Microsoft, aby tyto komponenty byly součástí .NET Core – položky jednoduše zachycují žádosti od komunity. Pokud se zajímáte o některou z výše uvedených součástí, zvažte účast v diskusích na GitHubu, aby bylo možné slyšet váš hlas. A pokud si myslíte, že něco chybí, zajistěte prosím [Nový problém v běhovém úložišti](https://github.com/dotnet/runtime/issues/new).

I když rozhraní .NET Core 3 (v době psaní tohoto zápisu je v sadě Works), bude zahrnovat podporu pro mnoho existujících .NET Framework rozhraní API. to znamená, že v současné době nejsou k dispozici v kontejneru na světě.

## <a name="using-a-platform-or-api-that-does-not-support-net-core"></a>Použití platformy nebo rozhraní API, které nepodporuje .NET Core

Některé platformy společnosti Microsoft nebo třetích stran nepodporují .NET Core. Některé služby Azure například poskytují sadu SDK, která ještě není dostupná pro využití v .NET Core. To je dočasné, protože všechny služby Azure nakonec budou používat .NET Core. Například [sada Azure DocumentDB SDK pro .NET Core](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core) byla vydaná jako verze Preview 16. listopadu 2016, ale teď je všeobecně dostupná (GA) jako stabilní verze.

Pokud však libovolná platforma nebo služba v Azure stále nepodporuje .NET Core s klientským rozhraním API, můžete použít ekvivalentní REST API ze služby Azure nebo klientské sady SDK v .NET Framework.

### <a name="additional-resources"></a>Další materiály a zdroje informací

- **Průvodce .NET Core** \
  [https://docs.microsoft.com/dotnet/core/index](../../../core/index.md)

- **Přenos z .NET Framework do .NET Core** \
  [https://docs.microsoft.com/dotnet/core/porting/index](../../../core/porting/index.md)

- **Průvodce rozhraním .NET Core v docker** \
  [https://docs.microsoft.com/dotnet/core/docker/introduction](../../../core/docker/introduction.md)

- **Přehled komponent .net** \
  [https://docs.microsoft.com/dotnet/standard/components](../../../standard/components.md)

>[!div class="step-by-step"]
>[Předchozí](net-core-container-scenarios.md)
>[Další](container-framework-choice-factors.md)
