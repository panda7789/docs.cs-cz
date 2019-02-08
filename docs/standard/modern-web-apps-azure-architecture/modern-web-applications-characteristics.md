---
title: Vlastnosti moderních webových aplikací
description: Navrhování moderních webových aplikací pomocí ASP.NET Core a Azure | Vlastnosti moderních webových aplikací
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: eacc66ff5d2c4bfb8d8645bc6bd319eab52437a3
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55828121"
---
# <a name="characteristics-of-modern-web-applications"></a>Vlastnosti moderních webových aplikací

> "… u správné návrhu levně vytvářet funkce. Tento přístup je namáhavý, ale stále úspěšný."  
> _\- Dennis Ritchie_

Moderní webové aplikace mají vyšší očekávání uživatele a větší nároky než kdy dřív. Dnešní webové aplikace se očekává dostupná 24 hodin denně, 7 z kdekoli ve světě a použít z libovolného zařízení, nebo se velikost obrazovky. Webové aplikace musí být zabezpečené, flexibilní a škálovatelnost, aby splňovalo špičky v poptávce. Komplexní scénáře stále, měla by ji zpracovat bohaté možnosti uživatelského prostředí založená na straně klienta pomocí JavaScriptu a efektivně komunikují prostřednictvím webových rozhraní API.

ASP.NET Core je optimalizované pro moderní webové aplikace a cloudové scénáře hostingu. Jeho modulárního návrhu umožňuje aplikacím závisí na pouze funkce, které skutečně používají, zlepšuje výkon a snižuje nutnost hostování požadavky na prostředky a zabezpečení aplikace.

## <a name="reference-application-eshoponweb"></a>Odkaz aplikace: eShopOnWeb

Tento návod obsahuje odkaz na aplikaci, _eShopOnWeb_, který ukazuje některé principy a doporučení. Aplikace je jednoduchá online obchod, který podporuje procházení katalogu košile, hrnky kávy a dalších marketingových položek. Referenční aplikace je záměrně jednoduchý, aby bylo možné je snadno pochopitelný.

**Obrázek 2-1.** eShopOnWeb

![](./media/image2-1.png)

> ### <a name="reference-application"></a>Odkaz na aplikaci
>
> - **eShopOnWeb**  
>   <https://github.com/dotnet/eShopOnWeb>

## <a name="cloud-hosted-and-scalable"></a>Hostované v cloudu a škálovatelné

ASP.NET Core je optimalizováno pro cloudové prostředí (veřejném cloudu, privátního cloudu, libovolný cloud), protože se jedná o nedostatku paměti a vysokou propustností. Menší nároky na místo aplikací ASP.NET Core znamená, že může hostovat více z nich na stejném hardwaru, a platíte za méně prostředků, pokud platit jako můžete pomocí cloudu, který je hostitelem služby. Vyšší propustnost znamená, že může sloužit více zákazníků z aplikace zadaný stejný hardware, což dále snižuje potřebu s investicemi v serverech a infrastruktury hostování.

## <a name="cross-platform"></a>Různé platformy

ASP.NET Core je multiplatformní a můžou běžet na systému Linux, macOS a Windows. Otevře spousta nových možností pro vývoj a nasazení aplikace vytvořené pomocí ASP.NET Core. Kontejnery docker - Linux i Windows - může hostovat aplikace ASP.NET Core, což jim umožní využít výhody [kontejnery a mikroslužby](../microservices-architecture/index.md).

## <a name="modular-and-loosely-coupled"></a>Modulární a volně svázané

Balíčky NuGet jsou prvotřídní občanům v .NET Core a aplikace ASP.NET Core se skládají z mnoha knihoven prostřednictvím balíčku NuGet. Členitost tato funkce pomáhá zajistit pouze závisí na aplikace a nasazení funkce, které skutečně potřebují, omezení jejich nároky na místo a zabezpečení ohrožení zabezpečení plochy.

ASP.NET Core také plně podporuje [injektáž závislostí](https://deviq.com/dependency-injection/), interně i na úrovni aplikace, úroveň. Rozhraní může mít několik implementací, které mohou být odloženy podle potřeby. Injektáž závislostí umožňuje aplikacím volně spojit do těchto rozhraní, spíše než konkrétní implementace, takže se jednodušeji rozšířit, údržbu a testování.

## <a name="easily-tested-with-automated-tests"></a>Snadno testovat pomocí automatizovaných testů

Podpora aplikací ASP.NET Core pro testování částí a jejich volné párování a podpora pro vkládání závislostí umožňuje snadno přepínat starostí o infrastrukturu s falešnou implementace pro účely testování. ASP.NET Core se také dodává TestServer, který slouží k hostování aplikací v paměti. Funkční testy lze pak proveďte požadavky na tento server v paměti, výkonu zásobníku celou aplikaci (včetně middleware, směrování, model vazby, filtry atd.) a získat odpověď, všechny za zlomek času by to obnášelo pro hostování aplikace skutečný serveru a vytvářet požadavky přes síťové vrstvy. Tyto testy jsou obzvláště usnadňují zápis a cenné pro rozhraní API, které jsou nabývá na důležitosti v moderních webových aplikací.

## <a name="traditional-and-spa-behaviors-supported"></a>Tradiční i SPA chování podporována

Tradiční webových aplikací zahrnovaly trochu chování na straně klienta, ale místo toho mají spoléhal na serveru pro navigaci, dotazů a aktualizace, které aplikace může být nutné provést. Každé nové operace provedené uživatelem by byl přeložen do webového požadavku, s výsledkem se znova načíst celou stránku v prohlížeči koncového uživatele. Klasické architektury Model-View-Controller (MVC) obvykle použijte tento přístup se každý nový požadavek na odpovídající akce jiný kontroler, který pak bude pracovat s modelem a vrátit zobrazení. Některé jednotlivé operace na dané stránce může rozšířeného s funkcí AJAX (asynchronní JavaScript a XML), ale architektury aplikace používá mnoho různých zobrazení MVC a koncové body adres URL. ASP.NET Core MVC dále podporuje také stránky Razor, jednodušší způsob, jak uspořádat stránky MVC – vizuální styl.

Jednostránkové aplikace (SPA), oproti tomu obsahují velmi málo načtení dynamicky generované stránky na straně serveru (pokud existuje). Mnoho SPA jsou inicializovány v rámci statický soubor HTML, který načítá potřebné knihovny jazyka JavaScript a spustíte aplikaci. Tyto aplikace vytvořit silná využití webových rozhraní API pro potřeby svých dat a může poskytnout že mnohem bohatší uživatelské prostředí.

Mnoho webových aplikací zahrnují kombinaci tradiční aplikace chování (obvykle pro obsah) a webových SPA (pro interaktivitu). ASP.NET Core podporuje obě MVC (zobrazení nebo stránku na základě) a webová rozhraní API ve stejné aplikaci, pomocí stejné sady nástrojů a základní knihovny rozhraní.

## <a name="simple-development-and-deployment"></a>Jednoduchý vývoj a nasazení

Aplikace ASP.NET Core může být napsán pomocí jednoduchého textových editorů a rozhraní příkazového řádku nebo plnohodnotné vývojové prostředí, jako je Visual Studio. Monolitické aplikace se obvykle nasazují do jednoho koncového bodu. Nasazení je možné snadno automatizovat jako součást průběžné integrace (CI) a kanál průběžného doručování (CD). Kromě tradičních nástrojů CI/CD Windows Azure je integrovaná podpora pro úložiště git a můžete automaticky nasazovat aktualizace, protože byly provedeny na zadané git pobočku nebo značku.

## <a name="traditional-aspnet-and-web-forms"></a>Tradiční ASP.NET a webových formulářů

Kromě ASP.NET Core, tradiční ASP.NET 4.x i nadále robustní a spolehlivou platformu pro vytváření webových aplikací. Podporuje technologie ASP.NET MVC a webového rozhraní API vývoje modelů, stejně jako webových formulářů, které je vhodné řešení pro vývoj bohaté možnosti aplikací založených na stránky a funkce ekosystému bohaté komponenty třetích stran. Windows Azure nabízí skvělou dlouhodobě podporu pro aplikace ASP.NET 4.x a celá řada vývojářů obeznámeni s touto platformou.

> ### <a name="references--modern-web-applications"></a>Odkazy – moderních webových aplikací
>
> - **Úvod do ASP.NET Core**  
>   <https://docs.microsoft.com/aspnet/core/>
> - **Šest klíč výhody z ASP.NET Core umožňují různé a lepší**  
>   <https://blog.trigent.com/six-key-benefits-of-asp-net-core-1-0-which-make-it-different-better/>
> - **Testování v ASP.NET Core**  
>   <https://docs.microsoft.com/aspnet/core/testing/>

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](choose-between-traditional-web-and-single-page-apps.md)
