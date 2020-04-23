---
title: Zvolit správnou možnost hostování Azure
description: Zjistěte, kterou cestu migrace do Azure je pro vaši webovou aplikaci v ASP.NET nejvhodnější.
author: CESARDELATORRE
ms.author: cesardl
ms.date: 03/01/2020
ms.openlocfilehash: a8ad946b03f97272cb8685620858af6b21a372dc
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "82072107"
---
# <a name="choose-the-right-azure-hosting-option"></a>Zvolit správnou možnost hostování Azure

Tento článek obsahuje doporučení a porovnání mezi několika možnostmi, které máte v Azure, při migraci stávajících .NET Framework aplikací z místního prostředí do Azure.

Základní oblasti, které je potřeba vzít v úvahu při migraci stávajících aplikací .NET do Azure, jsou:

1. Výběry výpočtů
1. Volby databáze
1. Požadavky na sítě a zabezpečení
1. Pokyny k ověřování a autorizaci

## <a name="compute-choices"></a>Výběry výpočtů

Při migraci stávajících aplikací .NET Framework do Azure máte více možností. Vzhledem k tomu, že .NET Framework závisí na systému Windows, jsou následující možnosti omezeny na výpočetní služby založené na systému Windows.

V následující tabulce je uvedeno několik porovnání a doporučení, která vám pomůžou zvolit správnou výpočetní cestu migrace pro vaši stávající aplikaci .NET.

|                 | Virtuální počítače Azure | Azure App Service | Kontejnery Windows |
|-----------------|-----------|-------------------|--------------------|
|Kdy je použít      |<ul><li>Aplikace má silné závislosti na instalaci serveru a místních. msi.</li><li>Chcete nejjednodušší cestu k migraci aplikace</li></ul>|Aplikace nemá žádné závislosti na serveru, jedná se pouze o čistě ASP.NET webovou aplikaci (MVC, WebForm) nebo N-vrstvou aplikaci (webové rozhraní API, WCf) přistupující k databázovému serveru. |<ul><li>Aplikace má závislosti na původním serveru, ale tyto závislosti mohou být zahrnuty v imagi Docker Windows.</li><li>Chcete aplikaci modernizovat, aby byla [cloudová DevOps připravená](../../architecture/modernize-with-azure-containers/modernize-existing-apps-to-cloud-optimized/reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications.md)</li></ul>|
|Výhody & výhodách  |<ul><li>Nejjednodušší cesta k migraci</li><li>Známé prostředí. Prostředí nasazení je virtuální počítač, takže je podobný místním serverům.</li></ul> |Průběžná údržba PaaS, nejjednodušší způsob, jak spravovat a škálovat aplikace v Azure. |<ul><li>Připraveno pro budoucnost, cloudové DevOps – připravené závislosti, které jsou součástí kontejnerů aplikace.</li><li>Skoro není potřeba Refaktorovat kód .NET/C #.</li></ul> |
|Nevýhody             |Je IaaS. Údržba je nákladná. Musíte spravovat infrastrukturu virtuálního počítače o sítích, nástroji pro vyrovnávání zatížení, škálování na více instancí, správě služby IIS atd. |<ul><li>Ne všechny aplikace jsou [podporovány](https://appmigration.microsoft.com/assessment) .</li><li>Některé aplikace může být potřeba Refaktorovat a dokonce trochu měnit její architekturu, aby podporovaly Azure App Service.</li></ul> |<ul><li>Křivka výukového kurzu Docker</li><li>Některé změny nastavení kódu a konfigurace aplikace</li></ul>|
|Požadavky |Virtuální počítač s Windows serverem se stejnými požadavky než aplikace pro místní prostředí | Azure App Service požadavky určené v [kontrolách připravenosti](https://github.com/Azure/App-Service-Migration-Assistant/wiki/Readiness-Checks). |<ul><li>[Docker Engine – Enterprise pro Windows Server 2019](https://azuremarketplace.microsoft.com/marketplace/apps/cloud-infrastructure-services.docker-windows-2019)<br />– nebo –</li><li>[Azure Container Service (AKS)](https://azure.microsoft.com/services/container-service/) (to je Kubernetes Orchestrator)<br />– nebo –<li>[Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) Orchestrator</li></ul> |
|Jak migrovat |Viz [migrace do Azure Virtual Machines](vm.md) | Viz [migrace Azure App Service](app-service.md) | Postupovat podle pokynů, scénářů a návodů, které jsou vysvětleny ve [stávajících aplikacích .NET modernizaci pomocí Azure a kontejnerů Windows – kniha](https://aka.ms/liftandshiftwithcontainersebook) |

Při plánování migrace do Azure pro stávající aplikace .NET Framework znázorňuje následující vývojový diagram rozhodovací strom. Pokud je to možné, vyzkoušejte si možnost jako první, ale možnost B je nejjednodušší cesta, která se má provést.

![Vývojový diagram znázorňující rozhodovací strom hostování](../media/migration/choose/decision-tree.png)

## <a name="database-choices"></a>Volby databáze

Při migraci relačních databází do Azure máte více možností. V tématu [migrace databáze SQL Server do Azure](sql.md) vám pomůžou zvolit správnou cestu migrace databáze pro existující aplikaci .NET.

## <a name="networking-and-security-considerations"></a>Požadavky na sítě a zabezpečení

Při nasazování aplikací do veřejného cloudu, jako je Microsoft Azure, můžete chtít izolovat a zabezpečit určité sítě [vytvořením sítě zóny DMZ](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/), jako je [DMZ mezi Azure a místním](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-hybrid) prostředím nebo [DMZ mezi Azure a internetem](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-dmz). Zóny DMZ se dá implementovat s [Azure Virtual Network](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).

Virtuální sítě Azure umožňují:

- Sestavení hybridní infrastruktury, kterou ovládáte
- Přineste si vlastní IP adresy a servery DNS
- Zabezpečení připojení pomocí protokolu IPsec VPN nebo ExpressRoute
- Získat podrobnou kontrolu nad přenosem mezi podsítěmi
- Vytváření propracovaných síťových topologií pomocí virtuálních zařízení
- Získejte izolované a vysoce zabezpečené prostředí pro vaše aplikace.

Pokud chcete začít vytvářet vlastní virtuální síť, přečtěte si [dokumentaci k Azure Virtual Network](https://docs.microsoft.com/azure/virtual-network/).

## <a name="authentication-and-authorization-considerations-when-migrating-to-azure"></a>Pokyny k ověřování a autorizaci při migraci do Azure

Nejdůležitějším problémem každé organizace, která přesouvá do cloudu, je zabezpečení. Většina společností investovala značnou dobu, peníze a strojírenství při navrhování a vývoji modelu zabezpečení a je důležité, aby mohli využívat stávající investice, jako jsou úložiště identit a řešení jednotného přihlašování.

Řada stávajících aplikací .NET B2E Enterprise běžících místně používá službu Active Directory pro ověřování a správu identit. Azure AD Connect umožňuje integrovat místní adresáře s Azure Active Directory. Informace o tom, jak začít, najdete v tématu [Integrace místních adresářů s Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).

Další plánování týkající se Azure Active Directory najdete v tématu [požadavky na identitu pro vaše řešení hybridní identity](https://docs.microsoft.com/azure/active-directory/active-directory-hybrid-identity-design-considerations-business-needs) .

Mezi další možnosti protokolu pro ověřování patří [OAuth](https://en.wikipedia.org/wiki/OAuth) a [OpenID](https://en.wikipedia.org/wiki/OpenID), které jsou běžné v aplikacích určených pro uživatele. Při použití autonomních databází identity, jako je například ASP.NET Identity SQL Database zabalená IdentityServer4 pomocí OAuth, se obvykle nevyžaduje žádné připojení k místním databázím ani adresářům.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Migrace webové aplikace v ASP.NET na Azure App Service](app-service.md)
