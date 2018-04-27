---
title: Charakteristika moderních webových aplikací
description: Architektury moderních webových aplikací pomocí ASP.NET Core a Azure | charakteristika moderních webových aplikací
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4f12b6860f1c4efe0f55cae4fefd8cd5f4539095
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="characteristics-of-modern-web-applications"></a>Charakteristika moderních webových aplikací

> "… v návrhu správné funkce levné pocházet. Tento přístup je náročnou, ale stále úspěšná."  
> _\- Dennis Ritchie_

## <a name="summary"></a>Souhrn

Moderních webových aplikací mít vyšší očekávání uživatele a větší nároky na než kdy dřív. Dnešní webové aplikace se měl být k dispozici 24 hodin denně 7 z kdekoliv ve světě a dá se použít z libovolného zařízení nebo velikost obrazovky. Webové aplikace musí být zabezpečené, flexibilní a škálovatelné pro splnění požadavků na špičky. Komplexní scénáře stále, měla by ji zpracovat bohaté uživatelského prostředí, které jsou vytvořené na straně klienta pomocí jazyka JavaScript a efektivně komunikaci prostřednictvím webových rozhraní API.

ASP.NET Core je optimalizovaná pro moderní webové aplikace a scénáře hostingu cloudu. Modulární návrh umožňuje aplikacím závisí na jenom ty funkce, které ve skutečnosti používají, vylepšení zabezpečení aplikací a výkonu při současném snížení hostování požadavky na prostředky.

## <a name="reference-application-eshoponweb"></a>Referenční aplikace: eShopOnWeb

V tomto návodu obsahuje odkaz na aplikaci, *eShopOnWeb*, který ukazuje některé principy a doporučení. Aplikace je jednoduchý online úložiště, které podporuje projdete katalog košile, hrnky kávy a další marketing položky. Odkaz na aplikaci je záměrně jednoduchá, aby bylo možné snadno pochopit.

**Obrázek 2-1.** eShopOnWeb

![](./media/image2-1.png)

> ### <a name="reference-application"></a>Odkaz na aplikaci
> - **eShopOnWeb**  
> <https://github.com/dotnet/eShopOnWeb>

## <a name="cloud-hosted-and-scalable"></a>Hostovaných v cloudu a škálovatelné

ASP.NET Core je optimalizovaná pro cloudu (veřejný cloud, privátního cloudu, žádné cloudu), protože se jedná o nedostatku paměti a vysokou propustností. Menší nároky na aplikace ASP.NET Core znamená můžete hostovat některých z nich na stejném hardwaru a platíte za méně prostředků při použití platím jako můžete přejít cloudových hostitelských služeb. Vyšší propustnost znamená, že může sloužit více zákazníků z aplikace, zadaný stejný hardware, dále snižuje potřeba investovat do servery a hostování infrastrukturu.

## <a name="cross-platform"></a>Různé platformy

ASP.NET Core je napříč platformami a můžete spustit na Linux a systému MacOS, jakož i Windows. Otevře se mnoho nové možnosti pro vývoj a nasazení aplikace vytvořené s ASP.NET Core. Docker kontejnery, které obvykle běží Linux dnes, může hostovat aplikace ASP.NET Core, což jim umožní využívat výhody [kontejnery a mikroslužeb](../microservices-architecture/index.md).

## <a name="modular-and-loosely-coupled"></a>Modulární a volně párované

Balíčky NuGet jsou prvotřídní občanů v .NET Core a ASP.NET Core aplikace se skládají z mnoha knihovny prostřednictvím balíčku NuGet. Tato členitost funkce pomáhá zajistit pouze závisí na aplikace a nasazení funkce, kterou ve skutečnosti vyžadují, snižuje jejich nároky a zabezpečení ohrožení zabezpečení útoku.

Jádro ASP.NET také plně podporuje vkládání závislostí interně i na úrovni aplikace. Rozhraní může mít několik implementací, které můžete odložit podle potřeby. Vkládání závislostí umožňuje aplikacím volně několika do těchto rozhraní je snadněji rozšířit, udržovat a testování.

## <a name="easily-tested-with-automated-tests"></a>Snadno testovány s automatizované testy

Aplikace ASP.NET Core podporují testování částí a jejich volné párování a podpora pro závislosti injekce usnadňuje Prohodit riziko z hlediska infrastruktury s falešných implementace pro účely testování. ASP.NET Core také dodává TestServer, který slouží k hostiteli aplikace v paměti. Funkčních testů můžete pak zkontrolujte požadavky na tento server v paměti výkonu zásobník úplné aplikací (včetně middleware, směrování, model vazby, filtry, atd.) a získat odpověď, všechny za zlomek času by byly třeba k hostování aplikace na skutečné serveru a provádět požadavky prostřednictvím síťovou vrstvou. Tyto testy jsou obzvláště snadno k zápisu a cenné pro rozhraní API, která jsou stále důležité v moderních webových aplikací.

## <a name="traditional-and-spa-behaviors-supported"></a>Tradiční a chování SPA podporováno

Tradiční webových aplikací mít podílejí málo chování klienta, ale místo toho máte spoléhali na serveru pro navigaci, dotazů a aktualizace, které aplikace může být nutné provést. Každé nové operace provedené uživatelem by přeložit na webový požadavek, výsledkem je načtěte celou stránku v prohlížeči koncového uživatele. Classic architektury Model-View-Controller (MVC) stejný přístup, obvykle s každý nový požadavek na odpovídající jiný řadič akce, který pak bude pracovat s modelem a vrátit zobrazení. Některé jednotlivých operací na danou stránku může být rozšířené o funkci AJAX (asynchronní JavaScript a XML), ale přehled architektury aplikace používá mnoho různých zobrazení MVC a adresy URL koncových bodů.

Jednostránkové aplikace (SPA), naopak zahrnovat velmi málo načtení dynamicky generovaném stránky na straně serveru (pokud existuje). Mnoho SPA jsou inicializovány v rámci statický soubor HTML, který načte potřebné knihovny JavaScript spuštění a spuštění aplikace. Tyto aplikace zkontrolujte velkou využití webových rozhraní API pro potřeby jejich dat a může poskytnout dojde mnohem širší uživatele.

Mnoho webových aplikací zahrnují kombinaci chování tradiční webové aplikace (obvykle pro obsah) a SPA (pro interaktivity). Jádro ASP.NET podporuje MVC a webových rozhraní API ve stejné aplikaci, pomocí stejné sady nástrojů a základní knihovny framework.

## <a name="simple-development-and-deployment"></a>Jednoduchý vývoj a nasazení

Aplikace ASP.NET Core lze zapsat pomocí jednoduchého textové editory a rozhraní příkazového řádku nebo plnohodnotné vývojové prostředí jako v aplikaci Visual Studio. Obvykle se monolitický aplikace nasadí do jednoho koncového bodu. Nasazení lze snadno automatizovat proběhnout jako součást průběžnou integraci (CI) a nastavené průběžné doručování (CD) kanálu. Kromě tradičních CI/CD nástroje Windows Azure je integrovaná podpora pro úložiště git a můžete automaticky nasadit aktualizace, jako jsou vytvářeny zadaný git větev nebo značky.

## <a name="traditional-aspnet-and-web-forms"></a>Tradiční ASP.NET a webové formuláře

Kromě ASP.NET Core, tradiční ASP.NET 4.x je stále výkonné a spolehlivé platforma pro vytváření webových aplikací. Technologie ASP.NET podporuje vývoj modely MVC a webového rozhraní API a také webových formulářů, které je vhodné řešení pro vývoj aplikací bohaté na stránce a funkce ekosystém bohaté komponenty jiných výrobců. Windows Azure má dlouhodobě podpory pro aplikace ASP.NET 4.x a celá řada vývojářů obeznámeni s tuto platformu.

> ### <a name="references--modern-web-applications"></a>Odkazy – moderních webových aplikací
> - **Úvod do ASP.NET Core**  
> <https://docs.microsoft.com/aspnet/core/>
> - **Šest klíč výhody z ASP.NET Core které různé a lepší**  
> <https://blog.trigent.com/six-key-benefits-of-asp-net-core-1-0-which-make-it-different-better/>
> - **Testování v ASP.NET Core**  
> <https://docs.microsoft.com/aspnet/core/testing/>

>[!div class="step-by-step"]
[Předchozí] (index.md) [Další] (choose-between-traditional-web-and-single-page-apps.md)
