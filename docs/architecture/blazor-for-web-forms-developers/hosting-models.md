---
title: Blazor app hosting modely
description: Naučte se různé způsoby hostování aplikace Blazor, a to i v prohlížeči na WebAssembly nebo na serveru.
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 77a022b01efba01038790c9601ea03f315a28fdf
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607929"
---
# <a name="blazor-app-hosting-models"></a>Blazor app hosting modely

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Aplikace Blazor mohou být hostovány ve službě IIS stejně jako aplikace ASP.NET webových formulářů. Aplikace Blazor mohou být také hostovány jedním z následujících způsobů:

- Na straně klienta v prohlížeči na WebAssembly.
- Na straně serveru v aplikaci ASP.NET Core.

## <a name="blazor-webassembly-apps"></a>Aplikace Blazor WebAssembly

Aplikace Blazor WebAssembly se spouštějí přímo v prohlížeči na runtime .NET založeném na webové sestavě. Aplikace Blazor WebAssembly fungují podobně jako front-end javascriptové architektury jako Angular nebo React. Nicméně, místo psaní JavaScript upíšete C #. Běh .NET runtime se stáhne s aplikací spolu s sestavení aplikace a všechny požadované závislosti. Nejsou vyžadovány žádné pluginy prohlížeče nebo rozšíření.

Stažená sestavení jsou normální sestavení rozhraní .NET, stejně jako v jakékoli jiné aplikaci .NET. Vzhledem k tomu, že runtime podporuje standard .NET, můžete použít existující knihovny .NET Standard s aplikací Blazor WebAssembly. Tato sestavení se však budou stále spouštět v izolovaném prostoru zabezpečení prohlížeče. Některé funkce mohou <xref:System.PlatformNotSupportedException>vyvolat , jako je pokus o přístup k systému souborů nebo otevření libovolných síťových připojení.

Když se aplikace načte, spustí se zaběhu .NET a zobrazí se na sestavení aplikace. Spustí se logika spuštění aplikace a vykreslí se kořenové součásti. Blazor vypočítá aktualizace ui na základě vykresleného výstupu z komponent. Aktualizace DOM jsou pak použity.

![Blazor WebAssembly](media/hosting-models/blazor-webassembly.png)

Aplikace Blazor WebAssembly běží čistě na straně klienta. Takové aplikace se dá nasadit do řešení pro hostování statických webů, jako jsou stránky GitHub nebo Azure Static Web Hosting. Rozhraní .NET není na serveru vůbec vyžadováno. Přímé propojení s částmi aplikace obvykle vyžaduje řešení směrování na serveru. Řešení směrování přesměruje požadavky do kořenového adresáře aplikace. Toto přesměrování lze například zpracovat pomocí pravidel přepisování adres URL ve službě IIS.

Chcete-li získat všechny výhody blazoru a vývoji webu .NET v plném zásobníku, hostujte svou aplikaci Blazor WebAssembly s ASP.NET Core. Pomocí rozhraní .NET na straně klienta i serveru můžete snadno sdílet kód a vytvářet aplikaci pomocí jedné konzistentní sady jazyků, architektur a nástrojů. Blazor poskytuje pohodlné šablony pro nastavení řešení, které obsahuje jak aplikaci Blazor WebAssembly, tak ASP.NET hostitelský projekt Core. Když je řešení sestaveno, vytvořené statické soubory z aplikace Blazor jsou hostovány aplikací ASP.NET Core s již nastaveným záložním směrováním.

## <a name="blazor-server-apps"></a>Aplikace Blazor Server

Připomeňme si z diskuse [o architektuře Blazor,](architecture-comparison.md#blazor) že komponenty Blazor uváznou svůj výstup do mezilehlé abstrakce nazývané `RenderTree`. Architektura Blazor pak porovnává to, co bylo vykresleno, s tím, co bylo dříve vykresleno. Rozdíly jsou použity na DOM. Komponenty Blazor jsou odděleny od způsobu použití jejich vykresleného výstupu. V důsledku toho samotné součásti nemusí běžet ve stejném procesu jako proces aktualizace uj. Ve skutečnosti ani nemusí běžet na stejném stroji.

V aplikacích Blazor Server jsou komponenty spuštěny na serveru namísto klienta v prohlížeči. Události ui, ke kterým dochází v prohlížeči jsou odesílány na server přes připojení v reálném čase. Události jsou odesílány do instance správné součásti. Vykreslování součástí a vypočtené rozdíl ui je serializován a odeslán do prohlížeče, kde je použita na DOM.

![Blazor Server](media/hosting-models/blazor-server.png)

Hostingový model Blazor Server může znít povědomě, <xref:System.Web.UI.UpdatePanel> pokud jste použili ASP.NET AJAX a ovládací prvek. Ovládací `UpdatePanel` prvek zpracovává použití částečné aktualizace stránky v reakci na události aktivační události na stránce. Při aktivaci `UpdatePanel` požaduje částečnou aktualizaci a pak ji použije bez nutnosti aktualizace stránky. Stav ui je spravován `ViewState`pomocí . Aplikace Blazor Server se mírně liší v tom, že aplikace vyžaduje aktivní spojení s klientem. Kromě toho je na serveru udržován veškerý stav ui. Kromě těchto rozdílů jsou oba modely koncepčně podobné.

## <a name="how-to-choose-the-right-blazor-hosting-model"></a>Jak si vybrat ten správný model hostingu Blazor

Jak je popsáno v [blazorhostingovém modelu dokumentů](/aspnet/core/blazor/hosting-models), různé modely hostingu Blazor mají různé kompromisy.

Hostingový model Blazor WebAssembly má následující výhody:

- Neexistuje žádná závislost na straně serveru .NET. Aplikace je plně funkční po stažení do klienta.
- Klientské prostředky a možnosti jsou plně využity.
- Práce je převedena ze serveru na klienta.
- K hostování aplikace není vyžadován ASP.NET webový server Core. Scénáře nasazení bez serveru jsou možné (například obsluha aplikace z CDN).

Nevýhody hostingového modelu Blazor WebAssembly jsou:

- Možnosti prohlížeče omezují aplikaci.
- Je vyžadován schopný hardware a software klienta (například podpora webassemblyu).
- Velikost stahování je větší a načítání aplikací trvá déle.
- Doba běhu .NET a podpora nástrojů je méně vyspělá. Například existují omezení v [.NET Standard](../../standard/net-standard.md) podporu a ladění.

Naopak model hostingu Blazor Server nabízí následující výhody:

- Velikost stahování je mnohem menší než aplikace na straně klienta a aplikace se načte mnohem rychleji.
- Aplikace plně využívá možnosti serveru, včetně použití všech rozhraní API kompatibilních s jádrem .NET.
- Jádro .NET na serveru se používá ke spuštění aplikace, takže existující nástroje .NET, jako je ladění, fungují podle očekávání.
- Tenké klienti jsou podporovány. Aplikace na straně serveru například pracují s prohlížeči, které nepodporují webovou sestavu, a na zařízeních s omezenými prostředky.
- Základ kódu aplikace .NET/C#, včetně kódu komponenty aplikace, se klientům nezobrazuje.

Nevýhody modelu hostingu Blazor Server jsou:

- Vyšší latence ui. Každá interakce uživatele zahrnuje síťový směrování.
- Neexistuje žádná offline podpora. Pokud se připojení klienta nezdaří, aplikace přestane fungovat.
- Škálovatelnost je náročná pro aplikace s mnoha uživateli. Server musí spravovat více klientských připojení a zpracovávat stav klienta.
- K poskytování aplikace je vyžadován ASP.NET základní server. Scénáře nasazení bez serveru nejsou možné. Aplikaci například nelze obsluhovat z sítě CDN.

Předchozí seznam kompromisů může být zastrašující, ale váš model hostování může být později změněn. Bez ohledu na vybraný model hostování Blazor je model *komponenty stejný*. V zásadě lze stejné komponenty použít s jedním modelem hostování. Kód aplikace se nezmění. je však vhodné zavést abstrakce tak, aby vaše komponenty zůstat hostování modelu agnostik. Abstrakce umožňují vaší aplikaci snadněji přijmout jiný model hostování.

## <a name="deploy-your-app"></a>Nasazení aplikace

ASP.NET aplikace webových formulářů jsou obvykle hostovány ve službě IIS v počítači nebo clusteru se systémem Windows Server. Aplikace Blazor mohou také:

- Hostujte ve službě IIS, buď jako statické soubory, nebo jako ASP.NET aplikace Core.
- Využijte ASP.NET flexibilitu core, aby bylo hostováno na různých platformách a serverových infrastrukturách. Můžete například hostovat aplikaci Blazor pomocí [Nginx](/aspnet/core/host-and-deploy/linux-nginx) nebo [Apache](/aspnet/core/host-and-deploy/linux-apache) na Linuxu. Další informace o tom, jak publikovat a nasazovat aplikace Blazor, najdete v dokumentaci k [hostování a nasazení](/aspnet/core/host-and-deploy/blazor/) Blazor.

V další části se podíváme na to, jak jsou nastaveny projekty pro aplikace Blazor WebAssembly a Blazor Server.

>[!div class="step-by-step"]
>[Předchozí](architecture-comparison.md)
>[další](project-structure.md)
