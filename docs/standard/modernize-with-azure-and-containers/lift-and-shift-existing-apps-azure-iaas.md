---
title: Navýšení a posunutí existující aplikace .NET do Azure IaaS (infrastruktura Cloud-Ready)
description: Modernizovat existující aplikace .NET s cloudu Azure a Windows kontejnerů.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 458b1bd1fc9fc24ce43d0926655fe0767aabc43c
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
ms.locfileid: "33956445"
---
# <a name="lift-and-shift-existing-net-apps-to-azure-iaas-cloud-infrastructure-ready"></a>Navýšení a posunutí existující aplikace .NET do Azure IaaS (infrastruktura Cloud-Ready)

> Vizi: jako první krok, a snížit vaše místní investice a celkových nákladů na hardware sítě údržby, jednoduše opětovným hostováním existující aplikace v cloudu.

Před získáním do *jak* Pokud chcete migrovat existující aplikace Azure infrastruktury jako služby (IaaS) platformu, je důležité k analýze důvodů, proč *proč* by chcete provést migraci přímo na IaaS v Azure. Scénář na této úrovni vyspělosti modernizace je v podstatě začít používat virtuální počítače v cloudu, místo nadále používat aktuální, místní infrastrukturu.

Je jiný bod k analýze *proč* chcete migrovat do čistého cloudu IaaS místo jen přidat další pokročilé spravované služby v Azure. Zjistit, co případech může vyžadovat IaaS na prvním místě.

Obrázek 2-1 umisťuje aplikace cloudové infrastruktury připravené pro použití v úrovni vyspělosti modernizace:

![Umístění aplikace připravené pro infrastruktury cloudu](./media/image2-1.png)

> **Obrázek 2-1.** Umístění aplikace připravené pro infrastruktury cloudu

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a>Proč migrovat existující webové aplikace .NET k Azure IaaS

Hlavním důvodem pro migraci do cloudu, i na úrovni počáteční IaaS, je dosáhnout snížení nákladů. Pomocí více spravovaných infrastruktury služby vaší organizace můžete snížit jeho investice do hardwaru údržby, server nebo zřizování virtuálních počítačů a nasazení a správu infrastruktury.

Když provedete rozhodnutí o přesunutí aplikace do cloudu, bude známější hlavním důvodem, proč můžete zvolit IaaS místo pokročilejší možnosti jako PaaS je jednoduše prostředí IaaS. Přesun do prostředí, který je podobný vaše aktuální, v místním prostředí nabízí nižší křivku learning, takže je nejrychlejší cestu do cloudu.

Však trvá nejrychlejší cestu do cloudu neznamená, že získá využívat výhod z mít vaše aplikace běží v cloudu. Některé z organizací bude získat nejvýznamnějších výhody z cloudu migrace na úrovni vyspělosti již přináší optimalizovaných Cloudů a cloudu nativní.

Také se ukázalo, že aplikace budou snadněji modernizovat a rearchitect v budoucnu, pokud je již spuštěn v cloudu i na IaaS. Migrace dat aplikace již bylo dosaženo. Navíc bude mít vaše organizace získávají dovednosti potřebné pro práci v cloudu a k k posunu pro pracuje v "kultury cloudu".

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a>Když k migraci na IaaS místo k PaaS

Další části popisují optimalizovaný pro cloudové aplikace, které jsou nejčastěji založené na platformách PaaS a služby. Tyto aplikace umožňují většina výhody z migraci do cloudu. 

Pokud je vaším cílem je jednoduše pro přesun existujících aplikací do cloudu, nejprve určete existující aplikace, které nebude vyžadovat významné změny spustit v Azure App Service. Tyto aplikace by měla být první kandidáty pro optimalizovaných Cloudů. 

Potom pro aplikace, která stále nelze přesunout do Windows kontejnery a PaaS, jako je aplikační služby nebo orchestrators jako Azure Service Fabric, migrovat do jednoduchého prostý virtuálních počítačích (IaaS). 

Ale mějte na paměti, že správně konfiguraci, zabezpečení a správě virtuálních počítačů vyžaduje mnohem víc času a IT odborných znalosti ve srovnání s použitím PaaS služby v Azure. Pokud uvažujete o virtuálních počítačích Azure, ujistěte se, že byste vzít v úvahu následné údržbě náročnost opravy, aktualizovat a spravovat prostředí virtuálních počítačů. Je virtuální počítače Azure IaaS.

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a>Používat Azure migraci k analýze a migrovat stávající aplikace do Azure

Migrace do cloudu nemusí být obtížné. Ale čtením řada organizací Začínáme - získat podrobně je prozkoumat do prostředí a úzkou vzájemné závislosti mezi aplikace, úlohy a data. Bez viditelnost může být obtížné plánování cesty vpřed. Bez podrobné informace o jaké jsou požadavky pro úspěšné migrace nemůže mít správné konverzace v rámci vaší organizace. Nevíte, dostatek o potenciálně náklady výhody, nebo zda zatížení může právě navýšení a shift nebo by vyžadovaly významné přepracování migrace úspěšně. Není divu, že proto váhají řada organizací.

[Azure migrací](https://aka.ms/azuremigrate) je nová služba, která poskytuje pokyny, přehledy a mechanismy pro potřeby pomoc při migraci na Azure. Poskytuje Azure migrací:

- Zjišťování a vyhodnocení místní virtuální počítače

- Mapování integrované závislostí pro zjišťování vysokou spolehlivostí vícevrstvé aplikace

- Inteligentní správné nastavení velikosti virtuálních počítačů Azure

- Kompatibility, vytváření sestav s pokyny pro nekompatibilních potenciálních problémů

- Integrace se službou správy databáze Azure pro zjišťování databáze a migrace

Azure migrací získáte jistotu, který můžete úlohy migrace s minimálním dopadem na podnikání a spouštějí se podle očekávání v Azure. Nástroje a pokyny můžete dosáhnout maximální návratnost investic, přičemž musí být zajištěno této důležité výkonu a splnění potřeb spolehlivost.

Obrázek 2-2 je znázorněný mapování předdefinované závislostí pro všechna připojení serveru a aplikace provádí migraci Azure.

![Umístění aplikace připravené pro infrastruktury cloudu](./media/image2-2.png)

> **Obrázek 2-2.** Umístění aplikace připravené pro infrastruktury cloudu

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a>Pomocí Azure Site Recovery k migraci existujících virtuálních počítačů na virtuálních počítačích Azure

Jako součást začátku do konce [Azure migrovat](https://aka.ms/azuremigrate), [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) je nástroj, který vám pomůže snadno migraci vašich webových aplikací do virtuálních počítačů v Azure. Site Recovery můžete replikovat místní virtuální počítače a fyzické servery do Azure, nebo replikovat do sekundárního místního umístění. Dokonce můžete replikovat úlohy, která běží na podporované virtuální počítač Azure, na místní *technologie Hyper-V* virtuálních počítačů na *VMware* virtuálních počítačů, nebo na fyzickém serveru systému Windows nebo Linux. Replikaci do Azure se eliminuje náklady a složitost Správa do sekundárního datacentra.

Site Recovery se provádí také speciálně pro hybridní prostředí, které jsou částečně místně a částečně v Azure. Site Recovery pomáhá zajistit kontinuitu podnikových procesů tak vaše aplikace, které běží na virtuálních počítačích a místní fyzických serverů, které jsou k dispozici Pokud lokality ocitne mimo provoz. Replikuje úlohy, které jsou spuštěny na virtuální počítače a fyzické servery tak, aby zůstaly dostupné v sekundárního umístění, pokud primární lokalita není k dispozici. Obnoví úlohy primární lokality, když je a znovu spustit.

Obrázek 2 – 3 ukazuje spuštění několika migrací virtuálních počítačů pomocí Azure Site Recovery.

![Umístění aplikace připravené pro infrastruktury cloudu](./media/image2-3.png)

> **Obrázek 2 – 3.** Umístění aplikace připravené pro infrastruktury cloudu

### <a name="additional-resources"></a>Další zdroje

- **Datový list migrovat Azure**

    [https://aka.ms/azuremigration\_Datový list](https://aka.ms/azuremigration\_datasheet)

- **Migrace Azure**

    [http://azuremigrationcenter.com/](http://azuremigrationcenter.com/)

- **Migrace do Azure pomocí Site Recovery**

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure](https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure)

- **Přehled služby Azure Site Recovery**

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-overview](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)

- **Migrace virtuálních počítačů v AWS a virtuální počítače Azure**

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure](https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure)

>[!div class="step-by-step"]
[Předchozí](index.md)
[další](migrate-your-relational-databases-to-azure.md)
