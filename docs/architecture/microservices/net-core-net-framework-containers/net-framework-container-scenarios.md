---
title: Kdy pro kontejnery Dockeru zvolit .NET Framework
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Kdy zvolit rozhraní .NET Framework pro kontejnery Dockeru
ms.date: 01/30/2020
ms.openlocfilehash: dfb1e8883fc9c3d9235672bc2885858bfb64afa5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77501964"
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a>Kdy pro kontejnery Dockeru zvolit .NET Framework

Zatímco rozhraní .NET Core nabízí významné výhody pro nové aplikace a vzory aplikací, rozhraní .NET Framework bude i nadále dobrou volbou pro mnoho existujících scénářů.

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a>Migrace existujících aplikací přímo do kontejneru Windows Serveru

Můžete chtít použít kontejnery Dockeru pouze pro zjednodušení nasazení, i když nevytváříte mikroslužeb. Například možná chcete zlepšit pracovní postup DevOps s Dockerem – kontejnery vám mohou poskytnout lépe izolované testovací prostředí a mohou také eliminovat problémy s nasazením způsobené chybějícími závislostmi při přesunu do produkčního prostředí. V případech, jako jsou tyto, i v případě, že nasazujete monolitické aplikace, má smysl používat Docker a Windows kontejnery pro aktuální aplikace rozhraní .NET Framework.

Ve většině případů pro tento scénář nebudete muset migrovat existující aplikace do .NET Core; můžete použít kontejnery Dockeru, které obsahují tradiční rozhraní .NET Framework. Doporučeným přístupem je však použití .NET Core při rozšíření existující aplikace, jako je například zápis nové služby v ASP.NET Core.

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>Použití knihoven .NET jiných výrobců nebo balíčků NuGet není k dispozici pro jádro .NET

Knihovny třetích stran rychle přijímají [standard .NET](../../../standard/net-standard.md), který umožňuje sdílení kódu ve všech přípojcích .NET, včetně .NET Core. S rozhraním .NET Standard 2.0 a novějším se kompatibilita povrchu rozhraní API v různých architekturách výrazně zvětšila. Ještě více mohou aplikace .NET Core 2.x a novější aplikace přímo odkazovat na existující knihovny rozhraní .NET Framework (viz [.NET Framework 4.6.1 podporující rozhraní .NET Standard 2.0).](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#net-framework-461-supporting-net-standard-20)

Sada Compatibility [Pack](../../../core/porting/windows-compat-pack.md) pro systém Windows navíc rozšiřuje plochu rozhraní API, která je k dispozici pro rozhraní .NET Standard 2.0 v systému Windows. Tento balíček umožňuje rekompilaci většiny existujícíkód .NET Standard 2.x s malou nebo žádnou změnu, ke spuštění v systému Windows.

I při tomto výjimečném postupu od standardu .NET Standard 2.0 a .NET Core 2.1 však mohou existovat případy, kdy některé balíčky NuGet potřebují ke spuštění systému Windows a nemusí podporovat .NET Core. Pokud jsou tyto balíčky důležité pro vaši aplikaci, budete muset použít rozhraní .NET Framework v kontejnerech systému Windows.

## <a name="using-net-technologies-not-available-for-net-core"></a>Použití technologií .NET není k dispozici pro jádro rozhraní .NET

Některé technologie rozhraní .NET Framework nejsou k dispozici v aktuální verzi rozhraní .NET Core (verze 3.1 od tohoto zápisu). Některé z nich mohou být k dispozici v novějších verzích, ale jiné se nevejdou do nových vzorů aplikací, na které se zaměřuje .NET Core a nemusí být nikdy k dispozici.

V následujícím seznamu je uvedena většina technologií, které nejsou k dispozici v rozhraní .NET Core 3.1:

- ASP.NET webových formulářů. Tato technologie je k dispozici pouze v rozhraní .NET Framework. V současné době neexistují žádné plány přenést ASP.NET webových formulářů do .NET Core.

- Služby WCF. I v případě, [že knihovna WCF-Client](https://github.com/dotnet/wcf) je k dispozici pro využití služeb WCF z .NET Core, od února 2020 je implementace serveru WCF k dispozici pouze v rozhraní .NET Framework. Tento scénář může být považován za budoucí verze .NET Core, existují dokonce i některá rozhraní API, která jsou považována za zahrnutí do [sady Windows Compatibility Pack](../../../core/porting/windows-compat-pack.md).

- Služby související s pracovním postupem. Windows Workflow Foundation (WF), Workflow Services (WCF + WF v jedné službě) a WCF Datové služby (dříve označované jako ADO.NET datové služby) jsou k dispozici pouze v rozhraní .NET Framework. V současné době neexistují žádné plány, aby je do .NET Core.

Kromě technologií uvedených v oficiálním [plánu .NET Core](https://github.com/dotnet/core/blob/master/roadmap.md)mohou být další funkce přeneseny na .NET Core nebo na novou [sjednocenou platformu .NET](https://devblogs.microsoft.com/dotnet/introducing-net-5/). Můžete zvážit účast v diskusích na GitHubu, aby byl váš hlas slyšet. A pokud si myslíte, že něco chybí, zasouborte nový problém v úložišti [GitHub dotnet/runtime.](https://github.com/dotnet/runtime/issues/new)

## <a name="using-a-platform-or-api-that-doesnt-support-net-core"></a>Použití platformy nebo rozhraní API, které nepodporuje .NET Core

Některé platformy Microsoftu a třetích stran nepodporují .NET Core. Například některé služby Azure poskytují sdk, který ještě není k dispozici pro spotřebu na .NET Core. Většina Azure SDK by nakonec portována na .NET Core/Standard, ale některé nemusí z různých důvodů. Dostupné sady Azure SDK najdete na stránce [Nejnovější verze sady Azure SDK.](https://azure.github.io/azure-sdk/releases/latest/index.html)

Do té doby pokud žádná platforma nebo služba v Azure stále nepodporuje .NET Core s klientským rozhraním API, můžete použít ekvivalentní rozhraní REST API ze služby Azure nebo klienta SDK v rozhraní .NET Framework.

### <a name="additional-resources"></a>Další zdroje

- **Základní příručka rozhraní .NET** \
  [https://docs.microsoft.com/dotnet/core/index](../../../core/index.md)

- **Přenesení z rozhraní .NET Framework do jádra rozhraní .NET** \
  [https://docs.microsoft.com/dotnet/core/porting/index](../../../core/porting/index.md)

- **Jádro .NET v průvodci Dockerem** \
  [https://docs.microsoft.com/dotnet/core/docker/introduction](../../../core/docker/introduction.md)

- **Přehled součástí rozhraní .NET** \
  [https://docs.microsoft.com/dotnet/standard/components](../../../standard/components.md)

>[!div class="step-by-step"]
>[Předchozí](net-core-container-scenarios.md)
>[další](container-framework-choice-factors.md)
