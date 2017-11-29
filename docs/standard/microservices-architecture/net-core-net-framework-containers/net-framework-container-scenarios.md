---
title: "Když zvolit rozhraní .NET Framework pro Docker kontejnery"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Když zvolit rozhraní .NET Framework pro Docker kontejnery"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 1bf1f055f040e7f3dc575b7a04140ebf0c599f98
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a>Když zvolit rozhraní .NET Framework pro Docker kontejnery

Když .NET Core nabízí významné výhody pro nové aplikace a aplikace vzory, rozhraní .NET Framework nadále dobrou volbou pro mnoho scénářů s existující.

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a>Migrace stávajících aplikací přímo do kontejneru systému Windows Server

Můžete chtít použít Docker kontejnery právě zjednodušit nasazení, i když nejsou vytváření mikroslužeb. Například možná chcete ke zlepšení pracovní postup DevOps s Docker – kontejnery můžete udělit lépe izolované testovací prostředí a může také odstranit problémy při nasazení nezdařila z důvodu chybějící závislosti při přesunutí v produkčním prostředí. V takových případech i v případě, že nasazujete monolitický aplikací, má smysl pro vaše aktuální aplikace rozhraní .NET Framework používat Docker a kontejnery Windows.

Ve většině případů pro tento scénář nebudete muset migrovat stávající aplikace pro .NET Core; pomocí Docker kontejnery, které zahrnují tradiční rozhraní .NET Framework. Doporučený postup je však použít .NET Core, jak rozšířit existující aplikace, jako je například zápis novou službu v ASP.NET Core.

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>Použití knihovny .NET třetích stran nebo není k dispozici balíčky NuGet pro .NET Core

Třetí strany knihovny se rychle přechodu [.NET Standard](https://docs.microsoft.com/dotnet/standard/net-standard), což umožňuje kód sdílení ve všech typů rozhraní .NET, včetně .NET Core. Standardní knihovny rozhraní .NET 2.0 a nad rámec plochy rozhraní API kompatibilitu mezi různé architektury stane podstatně větší a v rozhraní .NET 2.0 základní aplikací také přímo odkazovat existující knihovny rozhraní .NET Framework (viz [compat Shim](https://github.com/dotnet/standard/blob/master/docs/faq.md#how-does-net-standard-versioning-work)).

Ale i v případě že výjimečných postupu od standardní rozhraní .NET 2.0 a .NET Core 2.0, mohou existovat případy, kdy některé balíčky NuGet, třeba Windows ke spuštění a nemusí podporovat .NET Core. Pokud tyto balíčky jsou důležité pro vaši aplikaci, budete muset použít rozhraní .NET Framework kontejnerům systému Windows.

## <a name="usingnet-technologies-not-available-for-net-core"></a>Technologie Using.NET není k dispozici pro .NET Core 

Některé technologie .NET Framework nejsou k dispozici v aktuální verzi .NET Core (verze 2.0 době psaní tohoto textu). Některé z nich bude k dispozici v pozdějších verzích .NET Core (.NET Core 2.x), ale jiné se nevztahují na novou aplikaci vzory cílem .NET Core a mohou být nikdy k dispozici.

Následující seznam obsahuje většinu technologie, které nejsou k dispozici v rozhraní .NET 2.0 jádra:

-   ASP.NET – webové formuláře. Tato technologie je dostupná pouze na rozhraní .NET Framework. Aktuálně nejsou žádné plány a dovést webových formulářů ASP.NET do .NET Core.

-   Služby WCF. I když [knihovny klienta WCF](https://github.com/dotnet/wcf) je k dispozici pro využívání služeb WCF z .NET Core. od verze mid 2017 implementaci serveru WCF je k dispozici pouze v rozhraní .NET Framework. Tento scénář může považovat za pro budoucí verze .NET Core.

-   Služby související s pracovního postupu. Windows Workflow Foundation (WF), služby pracovních postupů (WCF + WF v jedné službě) a služby WCF Data Services (dříve označované jako ADO.NET Data Services) jsou dostupné jenom na rozhraní .NET Framework. Aktuálně neexistují žádné plány, aby byly na .NET Core.

Kromě technologie uvedené v oficiálním [.NET Core plán](https://github.com/aspnet/Home/wiki/Roadmap), další funkce, může být přesně do .NET Core. Úplný seznam, podívejte se na položky označené jako [port základní](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core) na webu CoreFX GitHub. Všimněte si, že tento seznam nepředstavuje závazek od společnosti Microsoft k poskytování těchto součástí na .NET Core – položky jednoduše zachycení požadavků od komunity. Pokud se zajímáte o některé z těchto komponent uvedených výše, vezměte v úvahu účastní diskusí na Githubu, aby váš hlas můžete buďte vyslyšeni. A pokud se domníváte, že něco chybí, [souboru nového problému v úložišti CoreFX](https://github.com/dotnet/corefx/issues/new).

## <a name="using-a-platform-or-api-that-does-not-support-net-core"></a>Pomocí platformy nebo rozhraní API, která nepodporuje .NET Core

Některé společnosti Microsoft nebo třetích stran platformy .NET Core nepodporují. Například některé služby Azure poskytnout sadu SDK, které dosud nejsou k dispozici pro používání na .NET Core. Toto je dočasný, protože všech služeb Azure se nakonec použijete .NET Core. Například [Azure DocumentDB SDK pro .NET Core](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core/1.2.1) byl vydán jako náhled na 16. listopadu 2016, ale nyní je obecně dostupné (GA) jako stabilní verze.

Do té doby Pokud všechny platformy a služby v Azure stále nepodporuje .NET Core s jeho klientského rozhraní API, můžete ekvivalentní REST API služby Azure nebo klienta SDK na rozhraní .NET Framework.

### <a name="additional-resources"></a>Další zdroje

-   **.NET core průvodce**
    [*https://docs.microsoft.com/dotnet/core/index*](https://docs.microsoft.com/dotnet/core/index)

-   **Portování z rozhraní .NET Framework na .NET Core**
    [*https://docs.microsoft.com/dotnet/core/porting/index*](https://docs.microsoft.com/dotnet/core/porting/index)

-   **Rozhraní .NET framework na Průvodce Docker**
    [*https://docs.microsoft.com/dotnet/framework/docker/*](https://docs.microsoft.com/dotnet/framework/docker/)

-   **Přehled součásti rozhraní .NET**
    [*https://docs.microsoft.com/dotnet/standard/components*](https://docs.microsoft.com/dotnet/standard/components)




>[!div class="step-by-step"]
[Předchozí] (net – základní – kontejner scenarios.md) [Další] (kontejner framework – volba factors.md)
