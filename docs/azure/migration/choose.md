---
title: Zvolte správnou možnost hostingu Azure
description: Zjistěte, která cesta migrace Do Azure je vhodná pro vaši ASP.NET webovou aplikaci.
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
# <a name="choose-the-right-azure-hosting-option"></a>Zvolte správnou možnost hostingu Azure

Tento článek obsahuje důležité informace a porovnání mezi více možnostmi, které máte v Azure při migraci existujících aplikací rozhraní .NET Framework z místního do Azure.

Základní oblasti, které je třeba zvážit při migraci existujících aplikací .NET do Azure jsou:

1. Možnosti výpočtu
1. Volby databáze
1. Aspekty vytváření sítí a zabezpečení
1. Aspekty ověřování a autorizace

## <a name="compute-choices"></a>Možnosti výpočtu

Při migraci existujících aplikací rozhraní .NET Framework do Azure máte několik možností. Protože však rozhraní .NET Framework závisí na systému Windows, jsou následující možnosti omezeny na výpočetní služby založené na systému Windows.

V následující tabulce je uvedeno několik porovnání a doporučení, která vám pomohou vybrat správnou cestu k migraci výpočetních prostředků pro stávající aplikaci .NET.

|                 | Virtuální počítače Azure | Azure App Service | Kontejnery Windows |
|-----------------|-----------|-------------------|--------------------|
|Kdy je použít      |<ul><li>Aplikace má silné závislosti na serveru a místních instalacích MSI.</li><li>Chcete nejjednodušší cestu migrace aplikace</li></ul>|Aplikace nemá žádné závislosti na serveru, je to jen čistá ASP.NET webová aplikace (MVC, WebForm) nebo N-Tier aplikace (Web API, WCf) přístup k databázovému serveru. |<ul><li>Aplikace má závislosti na původním serveru, ale tyto závislosti mohou být zahrnuty do bitové kopie systému Docker Windows.</li><li>Chcete aplikaci modernizovat tak, aby byla [připravena na cloudové devOps](../../architecture/modernize-with-azure-containers/modernize-existing-apps-to-cloud-optimized/reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications.md)</li></ul>|
|Výhody &  |<ul><li>Nejjednodušší cesta migrace</li><li>Známé prostředí. Prostředí nasazení je virtuální počítač, takže je podobný místním serverům.</li></ul> |Průběžná údržba PaaS, nejjednodušší způsob správy a škálování aplikací v Azure. |<ul><li>Připravené pro budoucnost, Cloud DevOps-Ready se závislostmi zahrnutými v kontejnerech aplikace.</li><li>Téměř není třeba refaktorovat kód .NET /C#.</li></ul> |
|Nevýhody             |To je IaaS. Údržba je nákladná. Je třeba spravovat infrastrukturu virtuálního počítače o sítích, vyrovnávání zatížení, horizontálnínavýšení kapacity, správě služby IIS a tak dále. |<ul><li>Ne všechny aplikace jsou [podporovány](https://appmigration.microsoft.com/assessment)</li><li>Některé aplikace může být nutné refaktored a dokonce mírně rearchitected, takže podporují Azure App Service.</li></ul> |<ul><li>Křivka učení dovedností dockeru</li><li>Některé změny nastavení konfigurace kódu a aplikace</li></ul>|
|Požadavky |Virtuální počítač se systémem Windows Server se stejnými požadavky jako aplikace pro místní | Požadavky služby Azure App Service zadané v [kontrole připravenosti](https://github.com/Azure/App-Service-Migration-Assistant/wiki/Readiness-Checks). |<ul><li>[Docker Engine – podnik pro Windows Server 2019](https://azuremarketplace.microsoft.com/marketplace/apps/cloud-infrastructure-services.docker-windows-2019)<br />– nebo –</li><li>[Azure Container Service (AKS)](https://azure.microsoft.com/services/container-service/) (To je orchestrátor Kubernetes)<br />– nebo –<li>[Orchestrátor Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)</li></ul> |
|Jak migrovat |Viz [Migrace do virtuálních počítačů Azure](vm.md) | Viz [Migrace služby Azure App Service](app-service.md) | Postupujte podle úvah, scénářů a návodů vysvětlených v [modernizaci existujících aplikací .NET pomocí elektronické knihy Azure a Kontejnery s Windows](https://aka.ms/liftandshiftwithcontainersebook) |

Následující vývojový diagram znázorňuje rozhodovací strom při plánování migrace do Azure pro vaše stávající aplikace rozhraní .NET Framework. Pokud je životaschopný, zkuste možnost A první, ale možnost B je nejjednodušší cesta k provedení.

![Vývojový diagram znázorňující rozhodovací strom hostování](../media/migration/choose/decision-tree.png)

## <a name="database-choices"></a>Volby databáze

Při migraci relačních databází do Azure máte několik možností. Viz [Migrace databáze SQL Serveru do Azure,](sql.md) které vám pomohou vybrat správnou cestu migrace databáze pro stávající aplikaci .NET.

## <a name="networking-and-security-considerations"></a>Aspekty vytváření sítí a zabezpečení

Při nasazování aplikací do veřejného cloudu, jako je Microsoft Azure, můžete chtít izolovat a zabezpečit určité sítě [vytvořením síťových Objektů DMZ](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/), jako je [například DMZ mezi Azure a místním](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-hybrid) nebo [DMZ mezi Azure a internetem](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-dmz). DMZs lze implementovat pomocí [virtuální sítě Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).

Virtuální sítě Azure umožňují:

- Vytvoření hybridní infrastruktury, kterou ovládáte
- Přineste si vlastní IP adresy a DNS servery
- Zabezpečení připojení pomocí sítě IPsec VPN nebo ExpressRoute
- Získání podrobné kontroly nad provozem mezi podsítěmi
- Vytváření sofistikovaných síťových topologie pomocí virtuálních zařízení
- Získejte izolované a vysoce zabezpečené prostředí pro vaše aplikace

Pokud chcete začít vytvářet vlastní virtuální síť, přečtěte si [dokumentaci k virtuální síti Azure](https://docs.microsoft.com/azure/virtual-network/).

## <a name="authentication-and-authorization-considerations-when-migrating-to-azure"></a>Aspekty ověřování a autorizace při migraci do Azure

Hlavním zájmem každé organizace, která se stěhuje do cloudu, je zabezpečení. Většina společností investovala značné množství času, peněz a inženýrství do navrhování a vývoje modelu zabezpečení a je důležité, aby byly schopny využít stávající investice, jako jsou obchody s identitami a řešení pro jednotné přihlašování.

Mnoho existujících podnikových aplikací B2E .NET spuštěných místně používá službu Active Directory pro ověřování a správu identit. Azure AD Connect umožňuje integrovat místní adresáře s Azure Active Directory. Informace o tom, jak začít, najdete [v tématu Integrace místních adresářů pomocí služby Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).

Další plánování související s Azure Active Directory najdete [v tématu Požadavky na identitu pro řešení hybridní identity.](https://docs.microsoft.com/azure/active-directory/active-directory-hybrid-identity-design-considerations-business-needs)

Další volby ověřovacího protokolu jsou [OAuth](https://en.wikipedia.org/wiki/OAuth) a [OpenID](https://en.wikipedia.org/wiki/OpenID), které jsou běžné v aplikacích orientovaných na spotřebitele. Při použití autonomní databáze identit, jako je například databáze ASP.NET Identity SQL zabalené IdentityServer4 pomocí OAuth, žádné připojení k místní databáze nebo adresáře je obvykle vyžadováno.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Migrace webové aplikace ASP.NET do služby Azure App Service](app-service.md)
