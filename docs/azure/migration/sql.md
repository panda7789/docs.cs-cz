---
title: Migrace databáze SQL Serveru do Azure
description: Naučte se migrovat databázi SQL Server z místního SQL Server do Azure.
ms.topic: how-to
ms.date: 05/27/2020
ms.openlocfilehash: ed5d6ef9395dca14d8e0ecba82d3fc18cb3d629a
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241445"
---
# <a name="migrate-a-sql-server-database-to-azure"></a>Migrace databáze SQL Serveru do Azure

Tento článek poskytuje stručný přehled dvou možností migrace databáze SQL Server do Azure. Azure má tři primární možnosti migrace provozní databáze SQL Server. Tento článek se zaměřuje na tyto dvě možnosti:

1. [SQL Server na virtuálních počítačích Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-iaas-overview): instance SQL Server nainstalovaná a hostovaná na virtuálním počítači s Windows, který běží v Azure, označovaný také jako infrastruktura jako služba (IaaS).
2. [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview): plně spravovaná služba Azure SQL Database, která se označuje také jako platforma jako služba (PaaS).

Oba přicházejí s využitím specialistů i nevýhody, které budete muset před migrací vyhodnotit. Třetí možností je [Azure SQL Database spravované instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance).

## <a name="get-started"></a>Začínáme

Následující příručky k migraci budou užitečné v závislosti na používané službě:

* [Migrace databáze SQL Serveru na SQL Server ve virtuálním počítači Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-migrate-sql)
* [Migrace databáze SQL Serveru do služby Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-migrate-your-sql-server-database)

Následující odkazy na koncepční obsah vám navíc pomůžou lépe porozumět virtuálním počítačům:

* [Vysoká dostupnost a zotavení po havárii pro SQL Server v Azure Virtual Machines](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-high-availability-dr)
* [Osvědčené postupy z hlediska výkonu pro SQL Server na Azure Virtual Machines](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-performance)
* [Modely aplikací a vývojové strategie pro SQL Server v Azure Virtual Machines](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-app-patterns-dev-strategies)

Následující odkazy vám pomůžou pochopit Azure SQL Database lépe:

* [Vytváření a Správa Azure SQL Databasech serverů a databází](https://docs.microsoft.com/azure/sql-database/sql-database-servers-databases)
* [Jednotky transakcí databáze (DTU) a jednotky elastické databázové transakce (eDTU)](https://docs.microsoft.com/azure/sql-database/sql-database-what-is-a-dtu)
* [Azure SQL Database omezení prostředků](https://docs.microsoft.com/azure/sql-database/sql-database-resource-limits)

## <a name="choosing-iaas-or-paas"></a>Výběr IaaS nebo PaaS

Při hodnocení, kam chcete databázi migrovat, určete, jestli je pro vás vhodnější IaaS nebo PaaS.

**Ve virtuálních počítačích Azure vyberte SQL Server, pokud:**

* Chystáte se "nazvednutí a posunutí" databáze a aplikací s minimálním počtem změn.
* Upřednostňujete úplnou kontrolu nad databázovým serverem a virtuálním počítačem, na kterém běží.
* Už máte SQL Server a licence k Windows serveru, které chcete používat.

**Databázi Azure SQL zvolte, pokud:**

* Hledáte modernizovat své aplikace a migrujete na používání dalších služeb PaaS v Azure.
* Nechcete spravovat databázový server a virtuální počítač, na kterém běží.
* Nemáte licence SQL Server nebo Windows Server nebo máte v úmyslu nechat licence, jejichž platnost vyprší.

Následující tabulka popisuje rozdíly mezi jednotlivými službami v závislosti na sadě scénářů.

| Scénář | SQL Server ve virtuálních počítačích Azure | Azure SQL Database |
|----------|-------------------------|--------------------|
| Migrace | Vyžaduje minimální změny v databázi. | Může vyžadovat změny v databázi, pokud používáte funkce, které nejsou k dispozici v Azure SQL, podle určení [Data Migration Assistant](https://www.microsoft.com/download/details.aspx?id=53595), nebo pokud máte jiné závislosti, jako jsou místně instalované spustitelné soubory.|
| Správa dostupnosti, obnovení a upgradů | Dostupnost a obnovení jsou konfigurovány ručně. Upgrady je možné automatizovat pomocí [VM Scale Sets](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade). | Automaticky se spravuje. |
| Základní konfigurace operačního systému | Ruční konfigurace | Automaticky se spravuje. |
| Správa velikosti databáze | Podporuje až 256 TB úložiště na instanci SQL Server. | Podporuje 8 TB úložiště před tím, než bude potřeba horizontální oddíl. |
| Správa nákladů | Musíte spravovat licenční náklady na SQL Server, licenční náklady na Windows Server a náklady na virtuální počítače (na základě jader, paměti RAM a úložiště). | Pokud používáte elastický fond, musíte spravovat náklady na službu (na základě [eDTU nebo DTU](https://docs.microsoft.com/azure/sql-database/sql-database-what-is-a-dtu), úložiště a počtu databází). Je také nutné spravovat náklady na smlouvu SLA. |

Další informace o rozdílech mezi těmito dvěma postupy najdete v tématu [Volba správné možnosti nasazení v Azure SQL](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas).

## <a name="faq"></a>Časté otázky

* **Můžu dál používat nástroje, jako je SQL Server Management Studio a SQL Server Reporting Services (SSRS) s SQL Server ve virtuálních počítačích Azure nebo Azure SQL Database?**

    Ano. Všechny nástroje Microsoft SQL Tool fungují s oběma službami. Služba SSRS není součástí Azure SQL Database, ale doporučujeme ji spustit ve virtuálním počítači Azure a pak ji nasměrovat na instanci databáze.

* **Chci přejít na PaaS, ale nejste si jistí, jestli je databáze kompatibilní. Jsou k dispozici nástroje pro usnadnění?**

    Ano. [Data Migration Assistant](https://www.microsoft.com/download/details.aspx?id=53595) je nástroj, který se používá jako součást migrace na Azure SQL Database. [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/) je služba ve verzi Preview, kterou můžete použít buď pro IaaS, nebo pro PaaS.

* **Můžu odhadnout náklady?**

    Ano. [Kalkulačka cen Azure](https://azure.microsoft.com/pricing/calculator/) se dá využít k odhadování nákladů na všechny služby Azure, včetně virtuálních počítačů a databázových služeb.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Zvolit správnou možnost hostování Azure](choose.md)
