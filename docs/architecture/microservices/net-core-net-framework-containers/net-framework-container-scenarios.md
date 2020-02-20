---
title: Kdy pro kontejnery Dockeru zvolit .NET Framework
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Kdy zvolit .NET Framework pro kontejnery Docker
ms.date: 01/30/2020
ms.openlocfilehash: dfb1e8883fc9c3d9235672bc2885858bfb64afa5
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77501964"
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a>Kdy pro kontejnery Dockeru zvolit .NET Framework

I když .NET Core nabízí významné výhody pro nové aplikace a vzory aplikací, .NET Framework bude pro mnoho stávajících scénářů nadále dobrou volbou.

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a>Migrace stávajících aplikací přímo do kontejneru Windows serveru

Kontejnery Docker můžete chtít použít jenom ke zjednodušení nasazení, i když nevytváříte mikroslužby. Například můžete chtít zlepšit pracovní postup DevOps pomocí Docker – kontejnery vám poskytnou lepší izolovaná testovací prostředí a můžou také eliminovat problémy s nasazením způsobené chybějícími závislostmi při přesunu do produkčního prostředí. V takových případech, i když nasazujete aplikaci monolitické, má smysl použít pro vaše aktuální aplikace .NET Framework kontejnery Docker a Windows.

Ve většině případů v tomto scénáři nebudete muset migrovat stávající aplikace do .NET Core; můžete použít kontejnery Docker, které zahrnují tradiční .NET Framework. Doporučený postup je však použití .NET Core při rozšiřování existující aplikace, jako je například zápis nové služby v ASP.NET Core.

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>Používání knihoven .NET nebo balíčků NuGet třetích stran není k dispozici pro .NET Core

Knihovny třetích stran jsou rychle přechodu [.NET Standard](../../../standard/net-standard.md), což umožňuje sdílení kódu napříč všemi typy rozhraní .NET, včetně .NET Core. S .NET Standard 2,0 a novějším je Kompatibilita s plochou rozhraní API napříč různými architekturami výrazně větší. Ještě víc, aplikace .NET Core 2. x a novější můžou přímo odkazovat na stávající knihovny .NET Framework (viz [.NET Framework 4.6.1 podporující .NET Standard 2,0](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#net-framework-461-supporting-net-standard-20)).

[Sada Compatibility Pack systému Windows](../../../core/porting/windows-compat-pack.md) navíc rozšiřuje plochu rozhraní API, která je k dispozici pro .NET Standard 2,0 ve Windows. Tento balíček umožňuje opětovně kompilovat stávající kód, aby .NET Standard 2. x s minimální nebo žádnou úpravou pro spuštění ve Windows.

Nicméně i s výjimečným průběhem od .NET Standard 2,0 a .NET Core 2,1 mohou nastat případy, kdy některé balíčky NuGet potřebují ke spuštění Windows a nemusí podporovat .NET Core. Pokud jsou tyto balíčky pro vaši aplikaci důležité, budete je muset použít .NET Framework v kontejnerech Windows.

## <a name="using-net-technologies-not-available-for-net-core"></a>Používání technologií .NET není k dispozici pro .NET Core

Některé technologie .NET Framework nejsou k dispozici v aktuální verzi .NET Core (verze 3,1 v tomto zápisu). Některé z nich mohou být k dispozici v pozdějších verzích, ale ostatní se nevejdou na nové vzory aplikací zaměřené na rozhraní .NET Core a nemusí být nikdy k dispozici.

Následující seznam obsahuje většinu technologií, které nejsou k dispozici v rozhraní .NET Core 3,1:

- ASP.NET webové formuláře. Tato technologie je k dispozici pouze na .NET Framework. V současné době nejsou k dispozici žádné plány k uvedení webových formulářů ASP.NET do .NET Core.

- Služby WCF. I když je k dispozici [Knihovna WCF-Client](https://github.com/dotnet/wcf) pro využívání služeb WCF od .net Core 2020, je implementace serveru WCF dostupná jenom na .NET Framework. Tento scénář je možné zvážit v budoucích vydáních .NET Core, ale v sadě [Windows Compatibility Pack](../../../core/porting/windows-compat-pack.md)jsou k dispozici i některá rozhraní API, která se považují za zařazování.

- Služby související s pracovním postupem. Programovací model Windows Workflow Foundation (WF), služby pracovních postupů (WCF + WF v jedné službě) a WCF Data Services (dříve označované jako ADO.NET Data Services) jsou k dispozici pouze na .NET Framework. V současné době nejsou k dispozici žádné plány pro jejich uvedení do .NET Core.

Kromě technologií uvedených v oficiálním plánu [.NET Core](https://github.com/dotnet/core/blob/master/roadmap.md)můžou být další funkce předané do .NET Core nebo nové [sjednocené platformy .NET](https://devblogs.microsoft.com/dotnet/introducing-net-5/). Můžete uvažovat o diskuzích na GitHubu, aby bylo možné slyšet váš hlas. A pokud si myslíte, že chybí něco, zapište nový problém do úložiště GitHubu [dotnet/runtime](https://github.com/dotnet/runtime/issues/new) .

## <a name="using-a-platform-or-api-that-doesnt-support-net-core"></a>Použití platformy nebo rozhraní API, které nepodporuje .NET Core

Některé platformy společnosti Microsoft a jiných výrobců nepodporují .NET Core. Některé služby Azure například poskytují sadu SDK, která ještě není dostupná pro využití v .NET Core. Většina Azure SDK by nakonec měla být přesměrovaná na .NET Core/Standard, ale některé z nich nemusí být dostupné. Dostupné sady Azure SDK můžete zobrazit na stránce [nejnovější verze sady Azure SDK](https://azure.github.io/azure-sdk/releases/latest/index.html) .

Pokud však libovolná platforma nebo služba v Azure stále nepodporuje .NET Core s klientským rozhraním API, můžete použít ekvivalentní REST API ze služby Azure nebo klientské sady SDK v .NET Framework.

### <a name="additional-resources"></a>Další zdroje

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
