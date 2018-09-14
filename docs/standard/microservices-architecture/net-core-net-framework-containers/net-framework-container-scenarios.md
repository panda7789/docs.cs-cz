---
title: Kdy pro kontejnery Dockeru zvolit .NET Framework
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Kdy pro kontejnery Dockeru zvolit .NET Framework
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/11/2018
ms.openlocfilehash: 9e1ff03421f1a5d23878c74f13423cec9625c4c5
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45609962"
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a>Kdy pro kontejnery Dockeru zvolit .NET Framework

Zatímco .NET Core nabízí významné výhody pro nové aplikace a modelům aplikací, rozhraní .NET Framework budou i nadále dobrou volbou pro mnoho scénářů s existující.

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a>Migrace existujících aplikací přímo do kontejneru systému Windows Server

Můžete chtít použít kontejnery Dockeru jen pro zjednodušení nasazení, i v případě, že nejsou vytváření mikroslužeb. Například možná chcete zlepšit pracovních postupů DevOps s Dockerem – kontejnery vám může poskytnout lépe izolované testovací prostředí a může také eliminovat problémy s nasazením způsobeno chybějícími závislostmi při přesunutí do produkčního prostředí. V takových případech i v případě, že nasazujete monolitické aplikace, je vhodné pro vaše aktuální aplikace rozhraní .NET Framework pomocí Dockeru a kontejnerech Windows.

Ve většině případů pro tento scénář nebude nutné migrovat existující aplikace až po .NET Core; můžete použít kontejnery Dockeru, které zahrnují tradiční rozhraní .NET Framework. Doporučený postup je však použití .NET Core, jak rozšířit existující aplikace, jako je například zápis nová služba v ASP.NET Core.

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>Pomocí knihovny .NET třetích stran nebo není k dispozici balíčky NuGet pro .NET Core

Rychle využívají knihovny třetích stran [.NET Standard](https://docs.microsoft.com/dotnet/articles/standard/library), což umožňuje sdílení kódu mezi všechny typy .NET, včetně .NET Core. S rozhraním .NET Standard 2.0 knihovny a nad rámec plochy rozhraní API se stal kompatibility přes různá rozhraní výrazně větší a v .NET Core 2.x aplikací můžete také přímo odkazovat na existující knihovny rozhraní .NET Framework (viz [compat překrytí](https://github.com/dotnet/standard/blob/master/docs/netstandard-20/README.md#net-framework-461-supporting-net-standard-20)).

Kromě toho [Windows Compatibility Pack](https://docs.microsoft.com/dotnet/core/porting/windows-compat-pack) vydaná v Listopadu 2017 rozšířit plochy rozhraní API dostupné pro .NET Standard 2.0 na Windows. Tato sada umožňuje rekompilace většina stávajícího kódu pro .NET Standard 2.x s žádné nebo téměř žádné úpravy, a spustit na Windows.

Nicméně i v případě této mimořádné průběh od .NET Standard 2.0 a .NET Core 2.1, mohou existovat případech, kdy některé balíčky NuGet, třeba Windows ke spuštění a nemusí podporovat .NET Core. Pokud tyto balíčky jsou důležité pro vaši aplikaci, je potřeba pomocí rozhraní .NET Framework v kontejnerech Windows.

## <a name="using-net-technologies-not-available-for-net-core"></a>Pomocí technologií .NET, není k dispozici pro .NET Core 

Některé technologie rozhraní .NET Framework nejsou k dispozici v aktuální verzi .NET Core (verze 2.1 v době psaní tohoto textu). Některé z nich bude k dispozici v pozdějších verzích .NET Core (.NET Core 2.x), ale ostatní se nevztahují na novou aplikaci vzory cílí na .NET Core a mohou být nikdy k dispozici.

Následující seznam obsahuje většinu technologie, které nejsou k dispozici v .NET Core 2.x:

-   Webové formuláře ASP.NET. Tato technologie je dostupná pouze na rozhraní .NET Framework. Aktuálně nejsou žádné plány zpřístupnit webových formulářů ASP.NET pro .NET Core.

-   Služby WCF. I když [knihovna klienta WCF](https://github.com/dotnet/wcf) je k dispozici pro využívání služeb WCF v .NET Core, podle střední 2017, implementaci serveru WCF je k dispozici pouze v rozhraní .NET Framework. Tento scénář může považovat za v budoucích verzích .NET Core, existují i některá rozhraní API zařazena [Windows Compatibility Pack](https://docs.microsoft.com/dotnet/core/porting/windows-compat-pack).

-   Související pracovní postup služby. Windows Workflow Foundation (WF), služby pracovních postupů (WCF a WF v jedné službě) a služby WCF Data Services (dříve označované jako služby ADO.NET Data Services) jsou k dispozici pouze v rozhraní .NET Framework. Aktuálně nejsou žádné plány a vrátit je do .NET Core.

Kromě technologie uvedené v oficiální [.NET Core – plán](https://github.com/aspnet/Home/wiki/Roadmap), další funkce může přenést až po .NET Core. Chcete-li zobrazit úplný seznam, podívejte se na položky označené jako [port core](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core) na webu CoreFX GitHub. Všimněte si, že tento seznam nepředstavuje závazek zpřístupnit tyto komponenty pro .NET Core od společnosti Microsoft – položky jednoduše zachytit požadavky od komunity. Pokud vás zajímají některé z těchto komponent uvedených výše, zvažte možnost účasti v diskusích u na Githubu tak, aby vašeho hlasu, jak můžete buďte vyslyšeni. A pokud si myslíte, něco chybí, [soubor nový problém v úložišti CoreFX](https://github.com/dotnet/corefx/issues/new).

Přestože .NET Core 3 (v době psaní tohoto návodu, to je v prací) bude zahrnovat podporu velké množství stávajících rozhraní API .NET Framework, jedná se o desktop orientovaný tak, aktuálně, bez použití ve světě kontejneru.

## <a name="using-a-platform-or-api-that-does-not-support-net-core"></a>Pomocí platformy nebo rozhraní API, která nepodporuje .NET Core

Některé společnosti Microsoft nebo třetích stran platformy .NET Core nepodporují. Například některé služby Azure poskytují sadu SDK, které ještě nejsou k dispozici pro použití v .NET Core. Toto je dočasný, protože všechny služby Azure se nakonec použijete .NET Core. Například [sadu Azure DocumentDB SDK pro .NET Core](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core/1.2.1) byla vydána ve verzi preview na 16. listopadu 2016, ale teď je všeobecně dostupná (GA) jako stabilní verzi.

Do té doby Pokud jakoukoli platformu nebo služby Azure stále nepodporuje .NET Core s jeho klientské rozhraní API, můžete ekvivalentní rozhraní REST API služby Azure nebo klientskou sadou SDK v rozhraní .NET Framework.

### <a name="additional-resources"></a>Další zdroje

-   **Průvodce platformou .NET Core**  
    [https://docs.microsoft.com/dotnet/articles/core/index](https://docs.microsoft.com/dotnet/articles/core/index)

-   **Portování z rozhraní .NET Framework do .NET Core**  
    [https://docs.microsoft.com/dotnet/articles/core/porting/index](https://docs.microsoft.com/dotnet/articles/core/porting/index)

-   **Průvodce rozhraním .NET Framework v Dockeru**  
    [https://docs.microsoft.com/dotnet/articles/framework/docker/](https://docs.microsoft.com/dotnet/articles/framework/docker/)

-   **.NET – přehled komponenty**  
    [*https://docs.microsoft.com/dotnet/standard/components*](../../components.md)




>[!div class="step-by-step"]
[Předchozí](net-core-container-scenarios.md)
[další](container-framework-choice-factors.md)
