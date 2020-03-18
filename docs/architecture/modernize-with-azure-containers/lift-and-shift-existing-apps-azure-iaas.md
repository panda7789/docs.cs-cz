---
title: Výtah a přesun existujících aplikací .NET na Azure IaaS (Cloud Infrastructure-Ready)
description: Modernizujte existující aplikace .NET pomocí Azure Cloudu a kontejnerů Windows.
ms.date: 04/28/2018
ms.openlocfilehash: c7638a034dbb27baea1b097bdb66175bfb5a71f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73089639"
---
# <a name="lift-and-shift-existing-net-apps-to-azure-iaas-cloud-infrastructure-ready"></a>Výtah a přesun existujících aplikací .NET na Azure IaaS (Cloud Infrastructure-Ready)

> Vize: Chcete-li snížit místní investice a celkové náklady na údržbu hardwaru a sítě, jednoduše hostujte stávající aplikace v cloudu, abyste snížili místní investice a celkové náklady na údržbu hardwaru a sítí.

Než začnete *migrovat* stávající aplikace na platformu Azure infrastructure as service (IaaS), je důležité analyzovat důvody, *proč* byste chtěli migrovat přímo do IaaS v Azure. Scénář na této úrovni vyspělosti modernizace v podstatě je začít používat virtuální počítače v cloudu, namísto pokračování v používání aktuální místní infrastruktury.

Dalším bodem k analýze je *důvod, proč* budete chtít migrovat do čistého cloudu IaaS namísto pouhého přidání pokročilejších spravovaných služeb v Azure. Určete, jaké případy mohou vyžadovat IaaS na prvním místě.

Obrázek 2-1 pozice Cloud Infrastructure-Ready aplikace v úrovních vyspělosti modernizace:

![Aplikace připravené pro umístění cloudové infrastruktury](./media/image2-1.png)

**Obrázek 2-1.** Aplikace připravené pro umístění cloudové infrastruktury

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a>Proč migrovat existující webové aplikace .NET do Azure IaaS

Hlavním důvodem migrace do cloudu, a to i na počáteční úrovni IaaS, je dosažení snížení nákladů. Pomocí více služeb spravované infrastruktury může vaše organizace snížit své investice do údržby hardwaru, zřizování a nasazování a nasazování serveru nebo virtuálních počítačů a správy infrastruktury.

Po rozhodnutí přesunout aplikace do cloudu, hlavním důvodem, proč si můžete vybrat IaaS místo pokročilejších možností, jako je PaaS, je prostě to, že prostředí IaaS bude známější. Přechod do prostředí, které je podobné vašemu aktuálnímu místnímu prostředí, nabízí nižší křivku učení, což z něj činí nejrychlejší cestu do cloudu.

Nejrychlejší cesta ke cloudu však neznamená, že budete mít největší užitek z toho, že vaše aplikace běží v cloudu. Každá organizace získá ty nejvýznamnější výhody migrace z cloudu na již zavedených úrovních vyspělosti optimalizované pro cloud a nativní cloud.

Je také zřejmé, že aplikace jsou snadněji modernizovat a rearchitect v budoucnu, když jsou již spuštěny v cloudu, a to i na IaaS. Migrace dat aplikace již byla dokončena. Vaše organizace také získá dovednosti potřebné pro práci v cloudu a přejde k provozu v "cloudové kultuře".

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a>Kdy migrovat na IaaS místo do PaaS

V dalších částech se popisují aplikace optimalizované pro cloud, které jsou většinou založeny na platformách a službách PaaS. Tyto aplikace vám nejvíce výhod plynouz migrace do cloudu.

Pokud je vaším cílem jednoduše přesunout existující aplikace do cloudu, nejprve identifikujte existující aplikace, které by nevyžadovaly podstatné změny ke spuštění ve službě Azure App Service. Tyto aplikace by měly být prvními kandidáty pro optimalizované pro cloud.

Pak pro aplikace, které stále nelze přesunout do Kontejnery Windows a PaaS, jako je služba App Service nebo orchestrátory, jako je služba Azure Kubernetes, migrovat do jednoduchých prostých virtuálních počítačů (IaaS).

Ale mějte na paměti, že správná konfigurace, zabezpečení a údržba virtuálních počítačů vyžaduje mnohem více času a odborných znalostí V OBLASTI IT ve srovnání s používáním služeb PaaS v Azure. Pokud uvažujete o virtuálních počítačích Azure, ujistěte se, že berete v úvahu probíhající úsilí údržby potřebné k opravě, aktualizaci a správě prostředí virtuálních počítačů. Virtuální počítače Azure je IaaS.

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a>Analýza a migrace stávajících aplikací do Azure pomocí Migrace Azure

Migrace do cloudu nemusí být obtížná. Ale mnoho organizací se snaží začít - získat hlubokou viditelnost do prostředí a těsné vzájemné závislosti mezi aplikacemi, úlohami a daty. Bez této viditelnosti může být obtížné naplánovat cestu vpřed. Bez podrobných informací o tom, co je potřeba pro úspěšnou migraci, nemůžete mít ve vaší organizaci správné konverzace. Nevíte dost o potenciálních nákladových výhodách nebo o tom, zda by úlohy mohly pouze převést a posunout nebo by k úspěšné migraci vyžadovaly významné přepracování. Není divu, že mnoho organizací váhá.

[Azure Migrate](https://aka.ms/azuremigrate) je nová služba, která poskytuje pokyny, přehledy a mechanismy potřebné k migraci do Azure. Migrace Azure poskytuje:

- Zjišťování a hodnocení místních virtuálních počítačů

- Integrované mapování závislostí pro zjišťování vícevrstvých aplikací s vysokou spolehlivostí

- Inteligentní přizpůsobení správného nastavení virtuálním počítačům Azure

- Hlášení o kompatibilitě s pokyny pro nápravu potenciálních problémů

- Integrace se službou Azure Database Management Service pro zjišťování a migraci databází

Azure Migrate vám dává jistotu, že vaše úlohy můžete migrovat s minimálním dopadem na podnikání a spustit podle očekávání v Azure. Se správnými nástroji a pokyny můžete dosáhnout maximální návratnosti investic a zároveň zajistit, aby byly splněny kritické potřeby v oblasti výkonu a spolehlivosti.

Obrázek 2-2 ukazuje integrované mapování závislostí pro všechna připojení serverů a aplikací prováděná azure migrate.

![Aplikace připravené pro umístění cloudové infrastruktury](./media/image2-2.png)

**Obrázek 2-2.** Aplikace připravené pro umístění cloudové infrastruktury

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a>Migrace stávajících virtuálních počítačů do virtuálních virtuálních virtuálních počítačů Azure pomocí Azure Site Recovery

Jako součást komplexní [migrace Azure](https://aka.ms/azuremigrate)je [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) nástroj, který můžete použít ke snadné migraci webových aplikací do virtuálních počítačů v Azure. Site Recovery můžete použít k replikaci místních virtuálních počítačů a fyzických serverů do Azure nebo k jejich replikaci do sekundárního místního umístění. Můžete dokonce replikovat úlohu, která běží na podporovaném virtuálním počítači Azure, na místním virtuálním počítači *Hyper-V,* na virtuálním počítači *VMware* nebo na fyzickém serveru Windows nebo Linux. Replikací do Azure se eliminují náklady a složitost spojené s udržováním sekundárního datového centra.

Site Recovery se také provádí speciálně pro hybridní prostředí, která jsou částečně místní a částečně v Azure. Site Recovery pomáhá zajistit kontinuitu podnikání tím, že vaše aplikace, které běží na virtuálních počítačích a místních fyzických serverech, jsou k dispozici, pokud dojde k pádu webu. Replikuje úlohy, které jsou spuštěny na virtuálních počítačích a fyzických serverech, aby zůstaly dostupné v sekundárním umístění, pokud primární lokalita není k dispozici. Po opětovném zprovoznění primární lokality do ní úlohy obnoví.

Obrázek 2-3 ukazuje provádění více migrace virtuálních počítačových sítí pomocí Azure Site Recovery.

![Aplikace připravené pro umístění cloudové infrastruktury](./media/image2-3.png)

**Obrázek 2-3.** Aplikace připravené pro umístění cloudové infrastruktury

### <a name="additional-resources"></a>Další zdroje

- **Datový list migrace Azure**

    <https://aka.ms/azuremigration\_datasheet>

- **Azure Migrate**

    <https://aka.ms/azuremigrate>

- **Centrum migrace Azure**

    <https://azure.microsoft.com/migration/>

- **Migrace do Azure pomocí Site Recovery**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure>

- **Přehled služby Azure Site Recovery**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-overview>

- **Migrace virtuálních počítačů ve službě AWS do virtuálních počítačů Azure**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure>

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](migrate-your-relational-databases-to-azure.md) <!-- Next Chapter -->
