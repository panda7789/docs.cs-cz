---
title: Blazormodely hostování aplikací
description: Seznamte se s různými způsoby hostování Blazor aplikace, včetně prohlížeče v systému WebAssembly nebo na serveru.
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- WebAssembly
ms.date: 09/11/2019
ms.openlocfilehash: a0d37392a65cfcbff9642476d9fdb1e5c662e66a
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173260"
---
# <a name="blazor-app-hosting-models"></a>Blazormodely hostování aplikací

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Blazoraplikace je možné hostovat ve službě IIS stejně jako aplikace ASP.NET webových formulářů. Blazoraplikace je také možné hostovat jedním z následujících způsobů:

- Na straně klienta v prohlížeči WebAssembly .
- Na straně serveru v aplikaci ASP.NET Core.

## <a name="blazor-webassembly-apps"></a>BlazorWebAssemblyaplikace

BlazorWebAssemblyaplikace se spouštějí přímo v prohlížeči v WebAssembly prostředí .NET runtime založeném na prostředí. BlazorWebAssemblyaplikace fungují podobným způsobem jako u front-endového rozhraní JavaScript, jako je například úhlová nebo reakce. Ale namísto psaní JavaScriptu napíšete jazyk C#. Modul runtime .NET se stáhne spolu s aplikací společně se sestavením aplikace a všemi požadovanými závislostmi. Nevyžadují se žádné moduly plug-in a doplňky prohlížeče.

Stažená sestavení jsou běžná sestavení .NET, podobně jako byste použili v jakékoli jiné aplikaci .NET. Vzhledem k tomu, že modul runtime podporuje .NET Standard, můžete s aplikací použít stávající knihovny .NET Standard Blazor WebAssembly . Tato sestavení se ale pořád spustí v izolovaném prostoru zabezpečení prohlížeče. Některé funkce mohou vyvolat výjimku <xref:System.PlatformNotSupportedException> , jako je například pokus o přístup k systému souborů nebo otevírání libovolných síťových připojení.

Po načtení aplikace se spustí modul runtime .NET a nasměruje se na sestavení aplikace. Spustí se logika spouštění aplikace a vykreslí se kořenové součásti. Blazorvypočítá aktualizace uživatelského rozhraní na základě vykresleného výstupu z komponent. Budou se pak použít aktualizace modelu DOM.

![Blazor WebAssembly](media/hosting-models/blazor-webassembly.png)

BlazorWebAssemblyaplikace spouštějí čistě na straně klienta. Takové aplikace je možné nasadit do statických řešení hostování webů, jako jsou stránky GitHub nebo hostování statických webů Azure. Na serveru vůbec není vyžadováno rozhraní .NET. Přímý odkaz na části aplikace obvykle vyžaduje řešení směrování na serveru. Řešení směrování přesměrovává požadavky do kořenového adresáře aplikace. Toto přesměrování můžete například zpracovat pomocí pravidel pro přepis adres URL ve službě IIS.

Chcete-li získat všechny výhody Blazor a kompletní vývoj webů .NET, hostování Blazor WebAssembly aplikace pomocí ASP.NET Core. Pomocí .NET na straně klienta i serveru můžete snadno sdílet kód a sestavovat aplikaci pomocí jedné konzistentní sady jazyků, rozhraní a nástrojů. Blazorposkytuje vhodné šablony pro nastavení řešení, které obsahuje Blazor WebAssembly aplikaci i hostitelský projekt ASP.NET Core. Po sestavení řešení jsou sestavené statické soubory z Blazor aplikace hostovány aplikací ASP.NET Core s již nastaveným záložním směrováním.

## <a name="blazor-server-apps"></a>BlazorServerové aplikace

Odvolání z diskuze o [ Blazor architektuře](architecture-comparison.md#blazor) , které Blazor komponenty vykreslují svůj výstup do mezilehlé abstrakce s názvem `RenderTree` . BlazorRozhraní pak porovná, co bylo vykresleno s dříve vykreslenou. Rozdíly jsou aplikovány na model DOM. Blazorkomponenty jsou odděleny od způsobu, jakým je použit jejich Vykreslený výstup. V důsledku toho nemusí být samotné komponenty spouštěny ve stejném procesu jako proces aktualizace uživatelského rozhraní. Ve skutečnosti je nemusíte spouštět na stejném počítači.

V Blazor serverových aplikacích se komponenty spouští na serveru místo na straně klienta v prohlížeči. Události uživatelského rozhraní, které se vyskytují v prohlížeči, se odesílají na server přes připojení v reálném čase. Události jsou odesílány do správných instancí součásti. Komponenty vykreslí a vypočtené rozdíly uživatelského rozhraní jsou serializovány a odesílány do prohlížeče, kde jsou aplikovány na model DOM.

![BlazorWebServer](media/hosting-models/blazor-server.png)

BlazorModel hostování serveru může být známý v případě, že jste použili ASP.NET AJAX a <xref:System.Web.UI.UpdatePanel> ovládací prvek. `UpdatePanel`Ovládací prvek zpracovává použití částečných aktualizací stránky v reakci na události triggeru na stránce. Když se aktivuje, `UpdatePanel` vyžádá částečnou aktualizaci a pak ji použije bez nutnosti aktualizovat stránku. Stav uživatelského rozhraní je spravován pomocí `ViewState` . BlazorServerové aplikace se mírně liší v tom, že aplikace vyžaduje aktivní připojení k klientovi. Kromě toho je veškerý stav uživatelského rozhraní udržován na serveru. Kromě těchto rozdílů jsou tyto dva modely koncepčně podobné.

## <a name="how-to-choose-the-right-blazor-hosting-model"></a>Jak vybrat správný Blazor model hostování

Jak je popsáno v [ Blazor dokumentaci k hostujícímu modelu](/aspnet/core/blazor/hosting-models), různé Blazor modely hostování mají různé kompromisy.

Blazor WebAssembly Hostující model má následující výhody:

- Neexistuje žádná závislost na straně serveru .NET. Aplikace po stažení do klienta plně funguje.
- Prostředky a možnosti klienta jsou plně využité.
- Práce je ze serveru převedena na klienta.
- Pro hostování aplikace není vyžadován ASP.NET Core webový server. Jsou možné scénáře nasazení bez serveru (například poskytování aplikace z CDN).

Downsides Blazor WebAssembly modelu hostování:

- Možnosti prohlížeče omezují aplikaci.
- Je vyžadován klientský hardware a software (například WebAssembly Podpora).
- Velikost ke stažení je větší a aplikace trvá déle, než se načtou.
- Podpora modulu runtime .NET a nástrojů je méně vyspělá. Existují například omezení pro [.NET Standard](../../standard/net-standard.md) podporu a ladění.

Naopak Blazor model hostování serveru nabízí následující výhody:

- Velikost ke stažení je mnohem menší než u aplikace na straně klienta a aplikace se načítá mnohem rychleji.
- Aplikace plně využívá možnosti serveru, včetně použití jakýchkoli rozhraní API kompatibilních s .NET Core.
- Rozhraní .NET Core na serveru se používá ke spuštění aplikace, takže stávající nástroje .NET, jako je ladění, fungují podle očekávání.
- Podporují se tenké klienty. Například aplikace na straně serveru fungují s prohlížeči, které nepodporují WebAssembly a na zařízeních s omezenými prostředky.
- Základ kódu pro .NET/C# aplikace, včetně kódu komponenty aplikace, není obsluhován klientům.

Downsides pro Blazor model hostování serveru:

- Vyšší latence uživatelského rozhraní. Každá interakce uživatele zahrnuje směrování sítě.
- Neexistuje žádná podpora offline. Pokud připojení klienta neproběhne úspěšně, aplikace přestane fungovat.
- Pro aplikace s mnoha uživateli je škálovatelnost náročná. Server musí spravovat více připojení klientů a zpracovávat stav klienta.
- Pro obsluhu aplikace je vyžadován ASP.NET Core Server. Scénáře nasazení bez serveru nejsou možné. Nemůžete například obsluhovat aplikaci ze sítě CDN.

Předchozí seznam kompromisů může být zastrašování, ale váš hostující model lze později změnit. Bez ohledu na Blazor vybraný model hostování je model komponent *stejný*. V zásadě lze použít stejné součásti s modelem hostování. Kód vaší aplikace se nezmění. je však dobrým zvykem zavést abstrakce, aby komponenty zůstaly hostující model-nezávislá. Abstrakce umožňují, aby vaše aplikace snadněji přijímala jiný model hostování.

## <a name="deploy-your-app"></a>Nasazení aplikace

Aplikace webových formulářů ASP.NET se obvykle hostují ve službě IIS na počítači nebo v clusteru s Windows serverem. Blazoraplikace můžou také:

- Být hostovány službou IIS, buď jako statické soubory, nebo jako aplikace ASP.NET Core.
- Využijte flexibilitu ASP.NET Core pro hostování na různých platformách a serverových infrastrukturách. Můžete například hostovat Blazor aplikaci pomocí [Nginx](/aspnet/core/host-and-deploy/linux-nginx) nebo [Apache](/aspnet/core/host-and-deploy/linux-apache) v systému Linux. Další informace o tom, jak publikovat a nasazovat Blazor aplikace, najdete v Blazor dokumentaci k [hostování a nasazení](/aspnet/core/host-and-deploy/blazor/) .

V další části se podíváme na to, jak se Blazor WebAssembly Blazor nastavují projekty pro a serverové aplikace.

>[!div class="step-by-step"]
>[Předchozí](architecture-comparison.md) 
> [Další](project-structure.md)
