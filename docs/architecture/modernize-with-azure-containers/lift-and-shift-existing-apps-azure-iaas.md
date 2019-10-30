---
title: Přezvednutí a posunutí stávajících aplikací .NET do Azure IaaS (cloudová infrastruktura – připravená)
description: Modernizovat stávající aplikace .NET pomocí cloudu Azure a kontejnerů Windows.
ms.date: 04/28/2018
ms.openlocfilehash: c7638a034dbb27baea1b097bdb66175bfb5a71f2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73089639"
---
# <a name="lift-and-shift-existing-net-apps-to-azure-iaas-cloud-infrastructure-ready"></a>Přezvednutí a posunutí stávajících aplikací .NET do Azure IaaS (cloudová infrastruktura – připravená)

> Vize: jako první krok můžete snížit svou místní investici a celkové náklady na údržbu hardwaru a sítě, jednoduše znovu hostovat své stávající aplikace v cloudu.

Než *se pustíte do migrace* stávajících aplikací na platformu IaaS (infrastruktura jako služba) Azure, je důležité analyzovat důvody, *Proč* byste chtěli migrovat přímo na IaaS v Azure. Scénář v této úrovni zralosti v podstatě je začít používat virtuální počítače v cloudu a nemusíte dál používat svou stávající místní infrastrukturu.

Dalším bodem k analýze je, *Proč* možná budete chtít migrovat na čistý IaaS Cloud místo pouhého přidávání pokročilejších spravovaných služeb v Azure. Určete, jaké případy můžou na prvním místě vyžadovat IaaS.

Obrázek 2-1 umisťuje aplikace připravené pro cloudovou infrastrukturu do vyspělosti úrovní zralosti:

![Umístění aplikací připravených pro cloudovou infrastrukturu](./media/image2-1.png)

**Obrázek 2-1.** Umístění aplikací připravených pro cloudovou infrastrukturu

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a>Proč migrovat existující webové aplikace .NET do Azure IaaS

Hlavním důvodem pro migraci do cloudu, a to i na počáteční úrovni IaaS, je dosáhnout snížení nákladů. Díky využívání více spravovaných služeb infrastruktury může vaše organizace snížit svou investici do údržby hardwaru, zřizování serverů a nasazení virtuálních počítačů a správy infrastruktury.

Až se rozhodnete přesunout vaše aplikace do cloudu, hlavní důvod, proč byste si měli vybrat IaaS místo pokročilejších možností, jako je PaaS, je jednoduše tím, že prostředí IaaS bude lépe známé. Přesun do prostředí, které je podobné vašemu aktuálnímu, místnímu prostředí nabízí nižší výukovou křivku, která umožňuje nejrychlejší cestu ke cloudu.

Použití nejrychlejší cesty ke cloudu ale neznamená, že získáte největší výhody využívání vašich aplikací v cloudu. Každá organizace bude získávat nejvýznamnější výhody migrace do cloudu v již zavedených cloudově optimalizovaných a cloudových úrovních zralosti.

Také se stala zjevné, že aplikace jsou v budoucnu jednodušší a modernizovat, když už běží v cloudu, a to i na IaaS. Migrace dat aplikací se už dosáhla. Vaše organizace taky získala dovednosti nutné pro práci v cloudu a provedla se tak jejímu fungování v "jazykové verzi cloudu".

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a>Kdy migrovat na IaaS místo na PaaS

V dalších částech se projednávají cloudově optimalizované aplikace, které jsou většinou založené na PaaS platformách a službách. Tyto aplikace vám poskytnou největší výhody migrace do cloudu.

Pokud je vaším cílem jednoduše přesunout stávající aplikace do cloudu, identifikujte nejprve existující aplikace, které nevyžadují, aby se v Azure App Service spouštěla značná úprava. Tyto aplikace by měly být prvním kandidátem optimalizovaného pro Cloud.

Pak u aplikací, které se stále nedají přesunout do kontejnerů Windows a PaaS, jako jsou App Service nebo Orchestration, jako je Azure Kubernetes Service, migrujte na jednoduché virtuální počítače (IaaS).

Mějte ale na paměti, že správná konfigurace, zabezpečení a údržba virtuálních počítačů vyžaduje mnohem více času a odbornost IT v porovnání s používáním služeb PaaS v Azure. Pokud zvažujete Virtual Machines Azure, ujistěte se, že jste přihlédli k probíhajícímu úsilí údržby potřebnému k opravě, aktualizaci a správě prostředí virtuálních počítačů. Azure Virtual Machines je IaaS.

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a>Použití Azure Migrate k analýze a migraci stávajících aplikací do Azure

Migrace do cloudu nemusí být obtížné. Spousta organizací ale bojovat začít – získat hlubokou viditelnost prostředí a těsné vzájemné závislosti mezi aplikacemi, úlohami a daty. Bez této viditelnosti může být obtížné naplánovat cestu s přesměrováním. Bez podrobných informací o tom, co je potřeba k úspěšné migraci, nemůžete mít ve vaší organizaci správné konverzace. Neznáte dostatek informací o potenciálních cenových výhodách nebo o tom, jestli úlohy mohly způsobit, že se úspěšně migrují a že by vyžadovaly významnou přepracování. Nemusíte nic váhají o mnoha organizacích.

[Azure Migrate](https://aka.ms/azuremigrate) je nová služba, která poskytuje pokyny, přehledy a mechanismy potřebné k tomu, aby vám pomohla při migraci do Azure. Azure Migrate poskytuje:

- Zjišťování a hodnocení místních virtuálních počítačů

- Předdefinované mapování závislostí pro vysoce spolehlivé zjišťování vícevrstvých aplikací

- Inteligentní správná velikost na virtuální počítače Azure

- Vytváření sestav kompatibility s pokyny pro oprava potenciální problémy

- Integrace se službou správy Azure Database pro zjišťování a migraci databází

Azure Migrate vám poskytne jistotu, že vaše úlohy se můžou migrovat s minimálním dopadem na firmu a v Azure běžet podle očekávání. Díky správným nástrojům a návodům můžete dosáhnout maximální návratnosti investic a přitom zajistit splnění nejdůležitějších potřeb výkonu a spolehlivosti.

Obrázek 2-2 ukazuje integrované mapování závislostí pro všechna připojení serverů a aplikací prováděná nástrojem Azure Migrate.

![Umístění aplikací připravených pro cloudovou infrastrukturu](./media/image2-2.png)

**Obrázek 2-2.** Umístění aplikací připravených pro cloudovou infrastrukturu

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a>Migrace stávajících virtuálních počítačů do virtuálních počítačů Azure pomocí Azure Site Recovery

V rámci komplexního [Azure Migrate](https://aka.ms/azuremigrate)je [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) nástroj, který můžete použít ke snadné migraci webových aplikací do virtuálních počítačů v Azure. Site Recovery můžete použít k replikaci místních virtuálních počítačů a fyzických serverů do Azure nebo k jejich replikaci do sekundárního místního umístění. Můžete dokonce replikovat úlohy, které běží na podporovaném virtuálním počítači Azure, na místním virtuálním počítači s *technologií Hyper-V* , na virtuálním počítači *VMware* nebo na fyzickém serveru se systémem Windows nebo Linux. Replikace do Azure eliminuje náklady a složitost údržby sekundárního datového centra.

Site Recovery je taky určený konkrétně pro hybridní prostředí, která jsou částečně místní a částečně v Azure. Site Recovery pomáhá zajistit kontinuitu podnikových aplikací tím, že udržuje aplikace běžící na virtuálních počítačích a místních fyzických serverech k dispozici v případě, že dojde k výpadku webu. Replikuje úlohy spuštěné na virtuálních počítačích a fyzických serverech tak, aby zůstaly dostupné v sekundárním umístění, pokud není primární lokalita k dispozici. Po opětovném spuštění a opětovném spuštění obnoví úlohy do primární lokality.

Obrázek 2-3 ukazuje spuštění několika migrací virtuálních počítačů pomocí Azure Site Recovery.

![Umístění aplikací připravených pro cloudovou infrastrukturu](./media/image2-3.png)

**Obrázek 2-3.** Umístění aplikací připravených pro cloudovou infrastrukturu

### <a name="additional-resources"></a>Další zdroje

- **Azure Migrate datový list**

    <https://aka.ms/azuremigration\_datasheet>

- **Azure Migrate**

    <https://aka.ms/azuremigrate>

- **Centrum migrace Azure**

    <https://azure.microsoft.com/migration/>

- **Migrace do Azure pomocí Site Recovery**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure>

- **Přehled služby Azure Site Recovery**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-overview>

- **Migrace virtuálních počítačů v AWS do virtuálních počítačů Azure**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure>

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[Další](migrate-your-relational-databases-to-azure.md) <!-- Next Chapter -->
