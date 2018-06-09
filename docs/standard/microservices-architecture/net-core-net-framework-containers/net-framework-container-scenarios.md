---
title: Když zvolit rozhraní .NET Framework pro Docker kontejnery
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Když zvolit rozhraní .NET Framework pro Docker kontejnery
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/07/2018
ms.openlocfilehash: 06b67f702b38202f598745826fa48f1ca97b7282
ms.sourcegitcommit: 6c480773ae896f45af4671fb3e26611a50e4dd81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2018
ms.locfileid: "35251032"
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a>Když zvolit rozhraní .NET Framework pro Docker kontejnery

Když .NET Core nabízí významné výhody pro nové aplikace a aplikace vzory, rozhraní .NET Framework nadále dobrou volbou pro mnoho scénářů s existující.

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a>Migrace stávajících aplikací přímo do kontejneru systému Windows Server

Můžete chtít použít Docker kontejnery právě zjednodušit nasazení, i když nejsou vytváření mikroslužeb. Například možná chcete ke zlepšení pracovní postup DevOps s Docker – kontejnery můžete udělit lépe izolované testovací prostředí a může také odstranit problémy při nasazení nezdařila z důvodu chybějící závislosti při přesunutí v produkčním prostředí. V takových případech i v případě, že nasazujete monolitický aplikací, má smysl pro vaše aktuální aplikace rozhraní .NET Framework používat Docker a kontejnery Windows.

Ve většině případů pro tento scénář nebudete muset migrovat stávající aplikace pro .NET Core; pomocí Docker kontejnery, které zahrnují tradiční rozhraní .NET Framework. Doporučený postup je však použít .NET Core, jak rozšířit existující aplikace, jako je například zápis novou službu v ASP.NET Core.

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>Použití knihovny .NET třetích stran nebo není k dispozici balíčky NuGet pro .NET Core

Třetí strany knihovny se rychle přechodu [.NET Standard](../../net-standard.md), což umožňuje kód sdílení ve všech typů rozhraní .NET, včetně .NET Core. Standardní knihovny rozhraní .NET 2.0 a nad rámec plochy rozhraní API kompatibilitu mezi různé architektury stane podstatně větší a v .NET Core 2.x aplikace můžete také přímo odkazovat na existující knihovny rozhraní .NET Framework (viz [compat Shim](https://github.com/dotnet/standard/blob/master/docs/faq.md#how-does-net-standard-versioning-work)).

Ale i v případě že výjimečných postupu od standardní rozhraní .NET 2.0 a .NET Core 2.0, mohou existovat případy, kdy některé balíčky NuGet, třeba Windows ke spuštění a nemusí podporovat .NET Core. Pokud tyto balíčky jsou důležité pro vaši aplikaci, budete muset použít rozhraní .NET Framework kontejnerům systému Windows.

## <a name="using-net-technologies-not-available-for-net-core"></a>Pomocí technologie .NET, není k dispozici pro .NET Core 

Některé technologie .NET Framework nejsou k dispozici v aktuální verzi .NET Core (verze 2.1 době psaní tohoto textu). Některé z nich bude k dispozici v pozdějších verzích .NET Core (.NET Core 2.x), ale jiné se nevztahují na novou aplikaci vzory cílem .NET Core a mohou být nikdy k dispozici.

Následující seznam obsahuje většinu technologie, které nejsou k dispozici v rozhraní .NET Core 2.1:

-   ASP.NET – webové formuláře. Tato technologie je dostupná pouze na rozhraní .NET Framework. Aktuálně nejsou žádné plány a dovést webových formulářů ASP.NET do .NET Core.

-   Služby WCF. I když [knihovny klienta WCF](https://github.com/dotnet/wcf) je k dispozici pro využívání služeb WCF z .NET Core. od verze mid 2017 implementaci serveru WCF je k dispozici pouze v rozhraní .NET Framework. Tento scénář může považovat za pro budoucí verze .NET Core.

-   Služby související s pracovního postupu. Windows Workflow Foundation (WF), služby pracovních postupů (WCF + WF v jedné službě) a služby WCF Data Services (dříve označované jako ADO.NET Data Services) jsou dostupné jenom na rozhraní .NET Framework. Aktuálně neexistují žádné plány, aby byly na .NET Core.

Kromě technologie uvedené v oficiálním [.NET Core plán](https://github.com/aspnet/Home/wiki/Roadmap), další funkce, může být přesně do .NET Core. Úplný seznam, podívejte se na položky označené jako [port základní](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core) na webu CoreFX GitHub. Všimněte si, že tento seznam nepředstavuje závazek od společnosti Microsoft k poskytování těchto součástí na .NET Core – položky jednoduše zachycení požadavků od komunity. Pokud se zajímáte o některé z těchto komponent uvedených výše, vezměte v úvahu účastní diskusí na Githubu, aby váš hlas můžete buďte vyslyšeni. A pokud se domníváte, že něco chybí, [souboru nového problému v úložišti CoreFX](https://github.com/dotnet/corefx/issues/new).

## <a name="using-a-platform-or-api-that-does-not-support-net-core"></a>Pomocí platformy nebo rozhraní API, která nepodporuje .NET Core

Některé společnosti Microsoft nebo třetích stran platformy .NET Core nepodporují. Například některé služby Azure poskytnout sadu SDK, které dosud nejsou k dispozici pro používání na .NET Core. Toto je dočasný, protože všech služeb Azure se nakonec použijete .NET Core. Například [Azure DocumentDB SDK pro .NET Core](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core/1.2.1) byl vydán jako náhled na 16. listopadu 2016, ale nyní je obecně dostupné (GA) jako stabilní verze.

Do té doby Pokud všechny platformy a služby v Azure stále nepodporuje .NET Core s jeho klientského rozhraní API, můžete ekvivalentní REST API služby Azure nebo klienta SDK na rozhraní .NET Framework.

### <a name="additional-resources"></a>Další zdroje

-   **Příručka pro základní rozhraní .NET**
    [*https://docs.microsoft.com/dotnet/core/index*](../../../core/index.md)

-   **Portování z rozhraní .NET Framework na .NET Core**
    [*https://docs.microsoft.com/dotnet/core/porting/index*](../../../core/porting/index.md)

-   **Průvodce Docker v rozhraní .NET framework**
    [*https://docs.microsoft.com/dotnet/framework/docker/*](../../../framework/docker/index.md)

-   **Přehled součásti rozhraní .NET**
    [*https://docs.microsoft.com/dotnet/standard/components*](../../components.md)




>[!div class="step-by-step"]
[Předchozí] (net – základní – kontejner scenarios.md) [Další] (kontejner framework – volba factors.md)
