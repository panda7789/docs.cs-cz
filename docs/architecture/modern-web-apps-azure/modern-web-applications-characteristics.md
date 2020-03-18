---
title: Charakteristika moderních webových aplikací
description: Architekt moderní webové aplikace s ASP.NET core a Azure | Charakteristika moderních webových aplikací
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: d70fa54adeb505fd37807399402281dfda67cf52
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451561"
---
# <a name="characteristics-of-modern-web-applications"></a>Charakteristika moderních webových aplikací

> "… se správným designem, funkce přicházejí levně. Tento přístup je náročný, ale stále se daří."  
> _\-Dennis Ritchie_

Moderní webové aplikace mají vyšší očekávání uživatelů a větší nároky než kdy předtím. Očekává se, že dnešní webové aplikace budou k dispozici 24 hodin denně, 7 dní v 7 dní v zaviditelnosti a budou použitelné prakticky z libovolného zařízení nebo obrazovky. Webové aplikace musí být zabezpečené, flexibilní a škálovatelné, aby splňovaly špičky v poptávce. Stále složitější scénáře by měly být zpracovány bohaté uživatelské prostředí postavené na klientovi pomocí JavaScriptu a efektivně komunikovat prostřednictvím webových rozhraní API.

ASP.NET Core je optimalizovaný pro moderní webové aplikace a cloudové scénáře hostování. Jeho modulární konstrukce umožňuje aplikacím záviset pouze na těch funkcích, které skutečně používají, což zlepšuje zabezpečení a výkon aplikací a zároveň snižuje požadavky na hostingové prostředky.

## <a name="reference-application-eshoponweb"></a>Referenční aplikace: eShopOnWeb

Tyto pokyny zahrnují referenční aplikaci _eShopOnWeb_, která demonstruje některé zásady a doporučení. Aplikace je jednoduchý internetový obchod, který podporuje procházení katalogu košile, hrnky na kávu a další marketingové položky. Referenční aplikace je záměrně jednoduchá, aby bylo snadné pochopit.

![eShopOnWeb](./media/image2-1.png)

**Obrázek 2-1.** eShopOnWeb

> ### <a name="reference-application"></a>Referenční aplikace
>
> - **eShopOnWeb**  
>   <https://github.com/dotnet/eShopOnWeb>

## <a name="cloud-hosted-and-scalable"></a>Hostované a škálovatelné

ASP.NET Core je optimalizovaný pro cloud (veřejný cloud, privátní cloud, jakýkoli cloud), protože má nedostatek paměti a vysokou propustnost. Menší nároky aplikací ASP.NET Core znamenají, že můžete hostovat více z nich na stejném hardwaru a platit za méně prostředků při používání cloudových hostingových služeb s průběžným platbou. Vyšší propustnost znamená, že můžete obsluhovat více zákazníků z aplikace se stejným hardwarem, což dále snižuje potřebu investovat do serverů a hostingové infrastruktury.

## <a name="cross-platform"></a>Příčná platforma

ASP.NET Core je multiplatformní a může běžet na Linuxu, macOS a Windows. To otevírá mnoho nových možností pro vývoj i nasazení aplikací vytvořených pomocí ASP.NET Core. Kontejnery Dockeru – Linux i Windows – můžou hostovat ASP.NET základních aplikacích, což jim umožňuje využívat výhod [kontejnerů a mikroslužeb](../microservices/index.md).

## <a name="modular-and-loosely-coupled"></a>Modulární a volně spojené

Balíčky NuGet jsou prvotřídní občané v .NET Core a ASP.NET základní aplikace se skládají z mnoha knihoven prostřednictvím NuGet. Tato rozlišovací schopnost funkcí pomáhá zajistit, aby aplikace závisely pouze na funkcích, které skutečně vyžadují, a na jejich nasazení byly závislé, což snižuje jejich nároky na plochu a zranitelnost zabezpečení.

ASP.NET Core také plně podporuje [vkládání závislostí](https://deviq.com/dependency-injection/), a to jak interně, tak na úrovni aplikace. Rozhraní může mít více implementací, které lze vyměnit podle potřeby. Vkládání závislostí umožňuje aplikacím volně spárovat s těmito rozhraními, nikoli konkrétní implementace, což usnadňuje jejich rozšíření, údržbu a testování.

## <a name="easily-tested-with-automated-tests"></a>Snadno testovatelné pomocí automatizovaných testů

ASP.NET základní aplikace podporují testování částí a jejich volné párování a podpora vkládání závislostí usnadňuje výměnu problémů infrastruktury s falešnými implementacemi pro testovací účely. ASP.NET Core je také dodáván s TestServer, který lze použít k hostování aplikací v paměti. Funkční testy pak mohou pokládat požadavky na tento server v paměti, provádět celý zásobník aplikací (včetně middlewaru, směrování, vázání modelu, filtrů atd.) a přijímat odpovědi, to vše ve zlomku času, který by trvalo hostování aplikace na skutečném serveru a pořazují požadavky prostřednictvím síťové vrstvy. Tyto testy jsou obzvláště snadno psát, a cenné, pro rozhraní API, které jsou stále důležitější v moderních webových aplikacích.

## <a name="traditional-and-spa-behaviors-supported"></a>Tradiční a SPA chování podporováno

Tradiční webové aplikace zahrnovaly malé chování na straně klienta, ale místo toho se spoléhali na server pro veškerou navigaci, dotazy a aktualizace, které aplikace může potřebovat provést. Každá nová operace provedená uživatelem by byla přeložena do nového webového požadavku, přičemž výsledkem je opětovné načtení celé stránky v prohlížeči koncového uživatele. Klasické model-View-Controller (MVC) architektury obvykle postupujte podle tohoto přístupu, s každým novým požadavkem odpovídající jinou akci kontroleru, který by zase pracovat s modelem a vrátit zobrazení. Některé jednotlivé operace na dané stránce mohou být rozšířeny o funkci AJAX (Asynchronní JavaScript a XML), ale celková architektura aplikace používala mnoho různých zobrazení MVC a koncových bodů adres URL. Kromě toho ASP.NET Core MVC také podporuje Razor Pages, což je jednodušší způsob, jak uspořádat stránky ve stylu MVC.

Aplikace s jednou stránkou (SPA) naopak zahrnují velmi málo dynamicky generovaných načtených stránek na straně serveru (pokud existuje). Mnoho srabů je inicializováno v rámci statického souboru HTML, který načte potřebné knihovny JavaScriptu pro spuštění a spuštění aplikace. Tyto aplikace umožňují velké využití webových rozhraní API pro jejich potřeby dat a mohou poskytovat mnohem bohatší uživatelské prostředí.

Mnoho webových aplikací zahrnuje kombinaci tradiční chování webových aplikací (obvykle pro obsah) a SPA (pro interaktivitu). ASP.NET Core podporuje mvc (zobrazení nebo stránky založené na) a webové rozhraní API ve stejné aplikaci, pomocí stejné sady nástrojů a podkladových knihoven architektury.

## <a name="simple-development-and-deployment"></a>Jednoduchý vývoj a nasazení

ASP.NET základní aplikace lze psát pomocí jednoduchých textových editorů a rozhraní příkazového řádku nebo plně vybavených vývojových prostředí, jako je Visual Studio. Monolitické aplikace se obvykle nasazují do jednoho koncového bodu. Nasazení lze snadno automatizovat, aby se vyskytovalo jako součást kanálu průběžné integrace (CI) a průběžného doručování (CD). Kromě tradičních nástrojů CI/CD má Microsoft Azure integrovanou podporu pro úložiště git a může automaticky nasazovat aktualizace tak, jak jsou prováděny do zadané větve git nebo značky. Azure DevOps poskytuje plně vybavený kanál sestavení a nasazení CI/CD a akce GitHub udávají další možnost pro projekty hostované v této oblasti.

## <a name="traditional-aspnet-and-web-forms"></a>Tradiční ASP.NET a webové formuláře

Kromě ASP.NET Core je tradiční ASP.NET 4.x i nadále robustní a spolehlivou platformou pro vytváření webových aplikací. ASP.NET podporuje vývojové modely MVC a Web API, stejně jako webové formuláře, které jsou vhodné pro vývoj bohatých aplikací založených na stránce a jsou vybaveny bohatým ekosystémem komponent třetích stran. Microsoft Azure má skvělou dlouhodobou podporu pro ASP.NET 4.x aplikace a mnoho vývojářů je obeznámeno s touto platformou.

## <a name="blazor"></a>Blazor

Blazor je součástí ASP.NET Core 3.0 a novější. Poskytuje nový mechanismus pro vytváření bohatých interaktivních webových klientských aplikací pomocí Razor, C# a ASP.NET Core. Nabízí další řešení, které je třeba zvážit při vývoji moderních webových aplikací. Existují dvě verze Blazor, aby zvážila: server-side a client-side.

Server-side Blazor byl propuštěn v roce 2019 s ASP.NET Core 3.0. Jak již název napovídá, běží na serveru a vykresluje změny klientského dokumentu zpět do prohlížeče v síti. Blazor na straně serveru poskytuje bohaté prostředí pro klienty bez nutnosti javascriptu na straně klienta a bez nutnosti samostatného načítání stránek pro každou interakci klientské stránky. Změny na načtené stránce jsou požadovány a zpracovány serverem a poté odeslány zpět klientovi pomocí SignalR.

Blazor na straně klienta bude vydán v roce 2020 a eliminuje potřebu vykreslovat změny na serveru. Místo toho bude využívat WebAssembly ke spuštění kódu .NET v rámci klienta. Klient může stále volat rozhraní API na server v případě potřeby požadovat data, ale všechny chování na straně klienta běží v klientovi prostřednictvím WebAssembly, který je již podporován všemi hlavními prohlížeči a je pouze knihovna Javascript.

> ### <a name="references--modern-web-applications"></a>Reference – Moderní webové aplikace
>
> - **Úvod do ASP.NET Core**  
>   <https://docs.microsoft.com/aspnet/core/>
> - **Testování v ASP.NET jádru**  
>   <https://docs.microsoft.com/aspnet/core/testing/>
> - **Blazor - Začínáme**  
>   <https://blazor.net/docs/get-started.html>

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](choose-between-traditional-web-and-single-page-apps.md)
