---
title: Zvedněte a shift existujících aplikací .NET do Azure IaaS (infrastruktura připravených pro Cloud)
description: Modernizace stávajících aplikací .NET pomocí cloudu Azure a kontejnery Windows.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: a6c13ba5bfd28cec87df1c021ed1f303d7d1f4f5
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53154382"
---
# <a name="lift-and-shift-existing-net-apps-to-azure-iaas-cloud-infrastructure-ready"></a>Zvedněte a shift existujících aplikací .NET do Azure IaaS (infrastruktura připravených pro Cloud)

> Pro zpracování obrazu: Jako první krok abyste snížili místních investic a celkové náklady na hardware a údržbu sítí, jednoduše opětovným hostováním existující aplikace v cloudu.

Před získáním do *jak* k migraci vašich stávajících aplikací do Azure infrastruktura jako služba (IaaS), je důležité analyzovat důvody *proč* je vhodné k migraci přímo na IaaS v Azure. Scénář na této úrovni vyspělosti modernizaci v podstatě je začít používat virtuální počítače v cloudu zlepšuje nadále používat aktuální místní infrastrukturu.

Je jiný bod k analýze *proč* budete chtít migrovat do čistě cloudových IaaS namísto pouhého přidání další pokročilé spravované služby v Azure. Zjistit, co případech může vyžadovat IaaS na prvním místě.

Obrázek 2 – 1 umístí v úrovni vyspělosti modernizaci aplikací připravených pro Cloud infrastruktury:

![Umístění aplikací připravených pro Cloud infrastruktury](./media/image2-1.png)

> **Obrázek 2-1.** Umístění aplikací připravených pro Cloud infrastruktury

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a>Proč migrovat existující webové aplikace .NET do Azure IaaS

Hlavním důvodem k migraci do cloudu, dokonce i na počáteční úrovni IaaS, je dosáhnout snížení nákladů. Pomocí další služby spravovaná infrastruktura může snížit vaše organizace své investice do hardwaru údržby, server nebo zřizování virtuálních počítačů a nasazení a správu infrastruktury.

Když provedete rozhodnutí ohledně přesunu aplikace do cloudu, bude hlavním důvodem, proč můžete zvolit IaaS místo pokročilejší možnosti jako PaaS je jednoduše prostředí IaaS více do hloubky. Přesun do prostředí, které se podobá vaše aktuální, v místním prostředí nabízí nižší učení křivky, což zajišťuje nejrychlejší cestu do cloudu.

Ale trvá nejrychlejší cestu do cloudu, neznamená, že získáte všechny výhody z vaší aplikace běžící v cloudu s. Každá organizace získají nejvíce velké výhody migrace do cloudu na úrovni vyspělosti už zavedená optimalizovaných pro Cloud a nativní pro Cloud.

Také se ukázalo, že aplikace budou snadněji modernizovat a úprava architektury v budoucnu, pokud už jsou spuštěné v cloudu i na IaaS. Migrace dat aplikaci již bylo dosaženo. Také budou mít vaše organizace získané znalosti potřebné pro práci v cloudu a provedené na posun působí v "cloud jazykovou verzi."

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a>Kdy migrovat na IaaS místo pro PaaS

Následující části popisují aplikace optimalizované pro Cloud, většinou podle PaaS platforem a služeb. Tyto aplikace umožňují většina výhody z migrace do cloudu. 

Pokud je vaším cílem je jednoduše přesun stávajících aplikací do cloudu, nejprve identifikování existujících aplikací, které nepotřebuje podstatné změny ke spuštění ve službě Azure App Service. Tyto aplikace by měla být první kandidáty pro Cloud optimalizovaný. 

Pak pro aplikace, která stále nelze přesunout do kontejnery Windows a PaaS, jako je App Service nebo orchestrátorů, jako je Azure Service Fabric, migrace do jednoduchého prostý virtuálních počítačích (IaaS). 

Ale mějte na paměti, že správně konfiguraci, zabezpečení a správu virtuálních počítačů vyžaduje mnohem více času a znalosti v oboru IT ve srovnání s použitím služby PaaS v Azure. Pokud uvažujete o Azure Virtual Machines, ujistěte se, že vzít v úvahu náročnost průběžné údržby vyžaduje opravu, aktualizovat a spravovat prostředí virtuálních počítačů. Azure Virtual Machines je IaaS.

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a>Pomocí Azure Migrate můžete analyzovat a migrovat existující aplikace do Azure

Migrace do cloudu nemusí být obtížná. Ale Začínáme - k Získejte podrobné informace o prostředí a těsné vzájemné závislosti mezi aplikací, úloh a dat je řada organizací velmi obtížné. Bez viditelnost může být obtížné pro plán cesty vpřed. Bez podrobných informací o jaké jsou požadavky pro úspěšné migrace nemůže mít správným konverzacím ve vaší organizaci. Dostatek o potenciálních úsporách, nákladů neznáte nebo zda úlohy může právě lift and shift nebo by vyžadovaly výrazné přepracování migrace úspěšně. Žádné wonder, že mnoho organizací váhání.

[Azure Migrate](https://aka.ms/azuremigrate) je nová služba, která poskytuje pokyny, přehledy a mechanizmy, které potřebuje pomoc při migraci do Azure. Azure Migrate nabízí:

- Zjišťování a posouzení místních virtuálních počítačů

- Mapování závislostí integrované bez obav zjišťování vícevrstvých aplikací

- Inteligentní nastavení správné velikosti virtuálních počítačů Azure

- Kompatibility, vytváření sestav s pokyny pro napravení možných problémů

- Integrace se službou správy databáze Azure pro databázi zjišťování a migrace

Azure Migrate zajišťuje vaše úlohy migrace s minimálním dopadem na podnikání a spustit podle očekávání v Azure. Správných nástrojů a pokynů můžete dosáhnout maximální návratnosti investic současným tento kritické výkon a splnění požadavků spolehlivost.

Obrázek 2-2 ukazuje mapování integrované závislostí pro všechna připojení serveru a aplikace provádí Azure Migrate.

![Umístění aplikací připravených pro Cloud infrastruktury](./media/image2-2.png)

> **Obrázek 2-2.** Umístění aplikací připravených pro Cloud infrastruktury

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a>Pomocí Azure Site Recovery můžete migrovat vaše stávající virtuální počítače na virtuální počítače Azure

Jako součást end-to-end [Azure Migrate](https://aka.ms/azuremigrate), [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) je nástroj, který vám umožní snadno migrovat vaše webové aplikace do virtuálních počítačů v Azure. Můžete pomocí Site Recovery pro replikaci místních virtuálních počítačů a fyzických serverů do Azure, nebo chcete replikovat do sekundárního místního umístění. Můžete dokonce replikovat úlohu, která běží na podporovaném virtuálním počítači Azure, na místní *Hyper-V* virtuálního počítače, na *VMware* virtuálního počítače, nebo na fyzickém serveru Windows nebo Linux. Replikace do Azure se eliminují náklady a složitost spojené s udržováním sekundárního datového centra.

Site Recovery je rovněž speciálně pro hybridní prostředí, které jsou částečně místně a částečně v Azure. Site Recovery pomáhá zajistit kontinuitu udržováním vašimi aplikacemi, které běží na virtuálních počítačích a místní fyzické servery, které jsou k dispozici Pokud web přestane fungovat. Replikuje úlohy spuštěné na virtuálních počítačích a fyzických serverů tak, aby zůstaly dostupné i v nějakém sekundárním umístění Pokud primární lokalita není k dispozici. Do ní úlohy obnoví primární lokality, když je a znovu spustit.

Obrázek 2 – 3 ukazuje spuštění několika migrací virtuálních počítačů pomocí Azure Site Recovery.

![Umístění aplikací připravených pro Cloud infrastruktury](./media/image2-3.png)

> **Obrázek 2 – 3.** Umístění aplikací připravených pro Cloud infrastruktury

### <a name="additional-resources"></a>Další zdroje

- **Azure Migrate datový list**

    [https://aka.ms/azuremigration\_datasheet](https://aka.ms/azuremigration\_datasheet)

- **Azure Migrate**

    [http://azuremigrationcenter.com/](http://azuremigrationcenter.com/)

- **Migrace do Azure pomocí Site Recovery**

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure](https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure)

- **Přehled služby Azure Site Recovery**

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-overview](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)

- **Migrace virtuálních počítačů v AWS do virtuálních počítačů Azure**

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure](https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure)

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](migrate-your-relational-databases-to-azure.md)