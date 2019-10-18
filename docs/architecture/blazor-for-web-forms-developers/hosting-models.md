---
title: Modely hostování aplikací Blazor
description: Seznamte se s různými způsoby hostování aplikace v Blazor, včetně prohlížeče na webovém sestavení nebo na serveru.
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 82628976bcb1f1cee3089aa25488396af44d0f1a
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72520297"
---
# <a name="blazor-app-hosting-models"></a>Modely hostování aplikací Blazor

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Aplikace Blazor se dají hostovat ve službě IIS stejně jako aplikace webových formulářů ASP.NET. Aplikace Blazor lze také hostovat jedním z následujících způsobů:

- Klientská strana v prohlížeči na webovém sestavení.
- Na straně serveru v aplikaci ASP.NET Core. 

## <a name="blazor-webassembly-apps"></a>Blazor aplikace WebAssembly

Blazor aplikace WebAssembly se spouštějí přímo v prohlížeči v prostředí .NET runtime založeném na WebAssembly. Blazor aplikace WebAssembly funguje podobným způsobem jako front-endové rozhraní JavaScript, jako je například úhlová nebo reakce. Ale namísto psaní JavaScriptu napíšete C#. Modul runtime .NET se stáhne spolu s aplikací společně se sestavením aplikace a všemi požadovanými závislostmi. Nevyžadují se žádné moduly plug-in a doplňky prohlížeče. 

Stažená sestavení jsou běžná sestavení .NET, podobně jako byste použili v jakékoli jiné aplikaci .NET. Vzhledem k tomu, že modul runtime podporuje .NET Standard, můžete použít existující knihovny .NET Standard s vaší aplikací Blazor WebAssembly. Tato sestavení se ale pořád spustí v izolovaném prostoru zabezpečení prohlížeče. Některé funkce mohou vyvolat <xref:System.PlatformNotSupportedException>, jako je například pokus o přístup k systému souborů nebo otevírání libovolných síťových připojení. 

Po načtení aplikace se spustí modul runtime .NET a nasměruje se na sestavení aplikace. Spustí se logika spouštění aplikace a vykreslí se kořenové součásti. Blazor vypočítá aktualizace uživatelského rozhraní na základě vykresleného výstupu z komponent. Budou se pak použít aktualizace modelu DOM.

![Blazor WebAssembly](media/hosting-models/blazor-webassembly.png)

Blazor aplikace WebAssembly spouštějí čistě na straně klienta. Takové aplikace je možné nasadit do statických řešení hostování webů, jako jsou stránky GitHub nebo hostování statických webů Azure. Na serveru vůbec není vyžadováno rozhraní .NET. Přímý odkaz na části aplikace obvykle vyžaduje řešení směrování na serveru. Řešení směrování přesměrovává požadavky do kořenového adresáře aplikace. Toto přesměrování můžete například zpracovat pomocí pravidel pro přepis adres URL ve službě IIS.

Pokud chcete získat všechny výhody Blazor a plného zásobníku pro web .NET, hostování vaší aplikace Blazor WebAssembly pomocí ASP.NET Core. Pomocí .NET na straně klienta i serveru můžete snadno sdílet kód a sestavovat aplikaci pomocí jedné konzistentní sady jazyků, rozhraní a nástrojů. Blazor poskytuje praktické šablony pro nastavení řešení, které obsahuje aplikaci Blazor WebAssembly a projekt hostitele ASP.NET Core. Po sestavení řešení jsou sestavené statické soubory z aplikace Blazor hostovány aplikací ASP.NET Core s již nastaveným záložním směrováním.

## <a name="blazor-server-apps"></a>Serverové aplikace Blazor

Navrácení z diskuze [architektury Blazor](architecture-comparison.md#blazor) , kterou komponenty Blazor, vykreslují výstup do zprostředkující abstrakce s názvem `RenderTree`. Blazor Framework pak porovná, co bylo vykresleno s dříve vykreslenou. Rozdíly jsou aplikovány na model DOM. Komponenty Blazor jsou odděleny od způsobu použití jejich vykresleného výstupu. V důsledku toho nemusí být samotné komponenty spouštěny ve stejném procesu jako proces aktualizace uživatelského rozhraní. Ve skutečnosti je nemusíte spouštět na stejném počítači.

V aplikacích Blazor Server se komponenty na serveru spouštějí místo na straně klienta v prohlížeči. Události uživatelského rozhraní, které se vyskytují v prohlížeči, se odesílají na server přes připojení v reálném čase. Události jsou odesílány do správných instancí součásti. Komponenty vykreslí a vypočtené rozdíly uživatelského rozhraní jsou serializovány a odesílány do prohlížeče, kde jsou aplikovány na model DOM.

![Blazor Server](media/hosting-models/blazor-server.png)

Model hostování serveru Blazor může být známý při použití ASP.NET AJAX a ovládacího prvku <xref:System.Web.UI.UpdatePanel>. Ovládací prvek `UpdatePanel` zpracovává použití částečných aktualizací stránky v reakci na události triggeru na stránce. Když se aktivuje, `UpdatePanel` požádá o částečnou aktualizaci a pak ji použije bez nutnosti aktualizovat stránku. Stav uživatelského rozhraní je spravován pomocí `ViewState`. Aplikace Blazor serveru se mírně liší v tom, že aplikace vyžaduje aktivní připojení k klientovi. Kromě toho je veškerý stav uživatelského rozhraní udržován na serveru. Kromě těchto rozdílů jsou tyto dva modely koncepčně podobné.

## <a name="how-to-choose-the-right-blazor-hosting-model"></a>Jak vybrat správný model hostování Blazor

Jak je popsáno v [dokumentaci modelu hostování Blazor](https://docs.microsoft.com/aspnet/core/blazor/hosting-models#server-side), různé modely hostování Blazor mají různé kompromisy.

Model hostování WebAssembly Blazor má následující výhody:

- Neexistuje žádná závislost na straně serveru .NET. Aplikace po stažení do klienta plně funguje.
- Prostředky a možnosti klienta jsou plně využité.
- Práce je ze serveru převedena na klienta.
- Pro hostování aplikace není vyžadován ASP.NET Core webový server. Jsou možné scénáře nasazení bez serveru (například poskytování aplikace z CDN).

Downsides modelu hostování Blazor WebAssembly je:

- Možnosti prohlížeče omezují aplikaci.
- Je vyžadován klientský hardware a software (například podpora WebAssembly).
- Velikost ke stažení je větší a aplikace trvá déle, než se načtou.
- Podpora modulu runtime .NET a nástrojů je méně vyspělá. Existují například omezení pro [.NET Standard](../../standard/net-standard.md) podporu a ladění.

Naopak model hostování serveru Blazor nabízí následující výhody:

- Velikost ke stažení je mnohem menší než u aplikace na straně klienta a aplikace se načítá mnohem rychleji.
- Aplikace plně využívá možnosti serveru, včetně použití jakýchkoli rozhraní API kompatibilních s .NET Core.
- Rozhraní .NET Core na serveru se používá ke spuštění aplikace, takže stávající nástroje .NET, jako je ladění, fungují podle očekávání.
- Podporují se tenké klienty. Například aplikace na straně serveru fungují s prohlížeči, které nepodporují WebAssembly a na zařízeních s omezením prostředků.
- Základ pro .NET/C# kód aplikace, včetně kódu komponenty aplikace, není obsluhován klientům.

Downsides pro model hostování serveru Blazor:

- Vyšší latence uživatelského rozhraní. Každá interakce uživatele zahrnuje směrování sítě.
- Neexistuje žádná podpora offline. Pokud připojení klienta neproběhne úspěšně, aplikace přestane fungovat.
- Pro aplikace s mnoha uživateli je škálovatelnost náročná. Server musí spravovat více připojení klientů a zpracovávat stav klienta.
- Pro obsluhu aplikace je vyžadován ASP.NET Core Server. Scénáře nasazení bez serveru nejsou možné. Nemůžete například obsluhovat aplikaci ze sítě CDN.

Předchozí seznam kompromisů může být zastrašování, ale váš hostující model lze později změnit. Bez ohledu na vybraný model hostování Blazor je model komponent *stejný*. V zásadě lze použít stejné součásti s modelem hostování. Kód vaší aplikace se nezmění. je však dobrým zvykem zavést abstrakce, aby komponenty zůstaly hostující model-nezávislá. Abstrakce umožňují, aby vaše aplikace snadněji přijímala jiný model hostování.

## <a name="deploy-your-app"></a>Nasazení aplikace

Aplikace webových formulářů ASP.NET se obvykle hostují ve službě IIS na počítači nebo v clusteru s Windows serverem. Aplikace Blazor můžou také:

- Být hostovány službou IIS, buď jako statické soubory, nebo jako aplikace ASP.NET Core.
- Využijte flexibilitu ASP.NET Core pro hostování na různých platformách a serverových infrastrukturách. Můžete například hostovat aplikaci Blazor pomocí [Nginx](/aspnet/core/host-and-deploy/linux-nginx) nebo [Apache](/aspnet/core/host-and-deploy/linux-apache) v systému Linux. Další informace o tom, jak publikovat a nasazovat aplikace Blazor, najdete v dokumentaci k [hostování a nasazení](/aspnet/core/host-and-deploy/blazor/) Blazor.

V další části se podíváme na to, jak se nastavují projekty pro Blazor aplikace pro WebAssembly a Blazor Server.

>[!div class="step-by-step"]
>[Předchozí](architecture-comparison.md)
>[Další](project-structure.md)
