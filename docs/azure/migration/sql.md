---
title: Migrace databáze SQL Serveru do Azure
description: Zjistěte, jak migrovat databázi SQL Serveru z místního SQL Serveru do Azure.
ms.topic: how-to
ms.date: 11/15/2017
ms.openlocfilehash: dac35970f2d77e232c2ee1a5e3a1f6e7bfec2317
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2020
ms.locfileid: "82072093"
---
# <a name="migrate-a-sql-server-database-to-azure"></a>Migrace databáze SQL Serveru do Azure

Tento krátký článek obsahuje stručný přehled dvou možností pro migraci databáze SQL Serveru do Azure.

Azure má dvě primární možnosti pro migraci produkční databáze SQL Serveru:

1. [SQL Server na virtuálních počítačích Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-iaas-overview): Instance SQL Serveru nainstalovaná a hostovaná na virtuálním počítači SWindows spuštěném v Azure, označovaná také jako Infrastruktura jako služba (IaaS).
2. [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview): Plně spravovaná služba Azure v databázi SQL, známá také jako platforma jako služba (PaaS).

Oba přicházejí s klady a zápory, které budete muset vyhodnotit před migrací.

## <a name="get-started"></a>Začínáme

V závislosti na tom, kterou službu používáte, budou užitečné následující průvodce migrací:

* [Migrace databáze SQL Serveru na SQL Server ve virtuálním počítači Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-migrate-sql)
* [Migrace databáze SQL Serveru do služby Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-migrate-your-sql-server-database)

Kromě toho následující odkazy na koncepční obsah vám pomůže lépe porozumět virtuálním mům:

* [Vysoká dostupnost a zotavení po havárii pro SQL Server v Azure Virtual Machines](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-high-availability-dr)
* [Osvědčené postupy z hlediska výkonu pro SQL Server na Azure Virtual Machines](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-performance)
* [Modely aplikací a vývojové strategie pro SQL Server v Azure Virtual Machines](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-app-patterns-dev-strategies)

A následující odkazy vám pomohou lépe porozumět Azure SQL Database:

* [Vytváření a správa databázových serverů a databází Azure SQL](https://docs.microsoft.com/azure/sql-database/sql-database-servers-databases)
* [Jednotky databázových transakcí (DTU) a elastické databázové transakční jednotky (eDTU)](https://docs.microsoft.com/azure/sql-database/sql-database-what-is-a-dtu)
* [Omezení prostředků databáze Azure SQL](https://docs.microsoft.com/azure/sql-database/sql-database-resource-limits)

## <a name="choosing-iaas-or-paas"></a>Výběr IaaS nebo PaaS

Při vyhodnocování, kam migrovat databázi, zjistěte, zda je pro vás vhodnější IaaS nebo PaaS.

**Zvolte SQL Server ve virtuálních počítačích Azure, pokud:**

* Hledáte "výtah a posun" databáze a aplikace s minimálními až žádné změny.
* Dáváte přednost mít plnou kontrolu nad databázovým serverem a virtuálním počítačem, na který běží.
* Již máte licence SQL Server a Windows Server, které chcete použít.

**Databázi Azure SQL zvolte, pokud:**

* Chcete modernizovat své aplikace a migrujete, abyste používali jiné služby PaaS v Azure.
* Nechcete spravovat databázový server a virtuální počítač, na který běží.
* Nemáte licence SQL Server nebo Windows Server nebo máte v úmyslu nechat licence, jejichž platnost vyprší.

Následující tabulka popisuje rozdíly mezi jednotlivými službami na základě sady scénářů.

| Scénář | SQL Server ve virtuálních počítačích Azure | Azure SQL Database |
|----------|-------------------------|--------------------|
| Migrace | Vyžaduje minimální změny v databázi. | Může vyžadovat změny v databázi, pokud používáte funkce, které nejsou k dispozici v Azure SQL, jak je určeno [Pomocníkem pro migraci dat](https://www.microsoft.com/download/details.aspx?id=53595), nebo pokud máte jiné závislosti, jako jsou místně nainstalované spustitelné soubory.|
| Správa dostupnosti, obnovení a upgradů | Dostupnost a obnovení jsou konfigurovány ručně. Upgrady lze automatizovat pomocí [škálovacích sad virtuálních vn](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade). | Automaticky spravováno za vás. |
| Základní konfigurace operačního systému | Ruční konfigurace. | Automaticky spravováno za vás. |
| Správa velikosti databáze | Podporuje až 64 TB úložiště na instanci serveru SQL Server. | Podporuje úložiště 4 TB před nutností horizontálního oddílu. |
| Řízení nákladů | Musíte spravovat náklady na licence serveru SQL Server, náklady na licence na Windows Server a náklady na virtuální počítač (na základě jader, paměti RAM a úložiště). | Je nutné spravovat náklady na služby (na základě [eDTU nebo DTU](https://docs.microsoft.com/azure/sql-database/sql-database-what-is-a-dtu), úložiště a počet databází, pokud používáte elastický fond). Musíte také spravovat náklady na jakoukoli sla. |

Další informace o rozdílech mezi nimi najdete v článku Volba možnosti CloudSQL Server: [Azure SQL Database nebo SQL Server na virtuálních počítačích Azure](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas).

## <a name="faq"></a>Nejčastější dotazy

* **Můžu dál používat nástroje, jako je SQL Server Management Studio a SQL Server Reporting Services (SSRS) s SQL Server em v Azure Virtuální počítače nebo Azure SQL Database?**

    Ano! Všechny nástroje Microsoft SQL fungují s oběma službami. SSRS však není součástí Azure SQL Database a doporučuje se, abyste ho spouštěli ve virtuálním počítači Azure a pak ho najeli na instanci databáze.

* **Chci jít PaaS, ale nejsem si jistý, jestli moje databáze je kompatibilní. Existují nástroje, které vám pomohou?**

    Ano. [Pomocník pro migraci dat](https://www.microsoft.com/download/details.aspx?id=53595) je nástroj, který se používá jako součást migrace do Azure SQL Database. [Služba migrace databáze Azure](https://azure.microsoft.com/campaigns/database-migration/) je služba preview, kterou můžete použít pro IaaS nebo PaaS.

* **Mohu odhadnout náklady?**

    Ano. [Cenová kalkulačka Azure](https://azure.microsoft.com/pricing/calculator/) se dá použít pro odhad nákladů na všechny služby Azure, včetně virtuálních počítačů a databázových služeb.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Zvolte správnou možnost hostingu Azure](choose.md)
