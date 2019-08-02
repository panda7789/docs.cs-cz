---
title: Migrace relačních databází do Azure
description: Modernizovat stávající aplikace .NET pomocí cloudu Azure a kontejnerů Windows | migrace relačních databází do Azure
ms.date: 04/28/2018
ms.openlocfilehash: 3d4f03e61144bb6a442a50916d7fd024d38ec611
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68677045"
---
# <a name="migrate-your-relational-databases-to-azure"></a>Migrace relačních databází do Azure

Vidění Azure nabízí nejkomplexnější migraci databáze.

V Azure můžete své databázové servery migrovat přímo do virtuálních počítačů s IaaS (čistý výtah a Shift), případně můžete migrovat na Azure SQL Database a získat další výhody. Azure SQL Database nabízí možnost Managed instance a úplné možnosti databáze jako služby (DBaaS). Obrázek 3-1 ukazuje několik cest k migraci relačních databází, které jsou k dispozici v Azure.

![Cesty migrace databáze v Azure](./media/image3-1.png)

> **Obrázek 3-1.** Cesty migrace databáze v Azure

## <a name="when-to-migrate-to-azure-sql-database-managed-instance"></a>Kdy migrovat na Azure SQL Database spravovanou instanci

Ve většině případů bude Azure SQL Database spravovaná instance nejlepší volbou při migraci dat do Azure. Pokud migrujete SQL Server databáze a potřebujete skoro 100% jistotu, že nebudete muset měnit architekt vaší aplikace nebo provádět změny dat nebo kódu přístupu k datům, vyberte funkci spravované instance Azure SQL Database.

Azure SQL Database spravovaná instance je nejlepší volbou, pokud máte další požadavky na funkce SQL Server na úrovni instance nebo požadavky na izolaci nad rámec funkcí poskytovaných standardním Azure SQL Database (jeden databázový model). Toto poslední PaaS možnosti, ale nenabízí stejné funkce jako tradiční SQL Server. Migrace může povrchovat tření.

Například organizace, která provedla hloubkové investice do možností SQL Server na úrovni instance, by mohla těžit z migrace do spravované instance SQL. Příklady možností SQL Server na úrovni instance zahrnují integraci modulu CLR (Common Language Runtime), SQL Server agenta a dotazování mezi databázemi. Podpora těchto funkcí není dostupná ve standardních Azure SQL Database (model jedné databáze).

Organizace, která pracuje s vysoce regulovaným průmyslem a který potřebuje zachovat izolaci z hlediska zabezpečení, může také těžit z výběru modelu spravované instance SQL.

Spravovaná instance v Azure SQL Database má následující vlastnosti:

- Izolace zabezpečení prostřednictvím Azure Virtual Network

- Kompatibilita povrchu aplikace s těmito funkcemi:

  - Agent SQL Server a SQL Server Profiler

  - Odkazy a dotazy na více databází, SQL CLR, replikace, Change Data Capture (CDC) a Service Broker

- Velikost databáze až do 35 TB

- Migrace s minimálními výpadky s těmito funkcemi:

  - Azure Database Migration Service

  - Nativní zálohování a obnovení a přesouvání protokolů

S těmito možnostmi se při migraci stávajících aplikačních databází do Azure SQL Database nabízí model spravované instance téměř 100% výhod služby PaaS for SQL Server. Spravovaná instance je SQL Server prostředí, ve kterém budete nadále používat možnosti na úrovni instance beze změny návrhu aplikace.

Spravovaná instance je pravděpodobně nejvhodnější pro podniky, které aktuálně používají SQL Server a které vyžadují flexibilitu v zabezpečení sítě v cloudu. Vypadá to, že máte privátní virtuální síť pro databáze SQL.

## <a name="when-to-migrate-to-azure-sql-database"></a>Kdy migrovat na Azure SQL Database

Jak je uvedeno, standardní Azure SQL Database je plně spravovaná relační DBaaS. SQL Database aktuálně spravuje miliony produkčních databází v různých datových centrech 38 po celém světě. Podporuje širokou škálu aplikací a úloh, od správy přímočarých transakčních dat až po řízení nejdůležitějších aplikací náročných na data, které vyžadují pokročilé zpracování dat v globálním měřítku.

Z důvodu svých úplných funkcí PaaS, lepší ceny a nakonec nižší náklady – byste měli přejít na standardní Azure SQL Database jako výchozí možnost, pokud máte aplikaci, která používá základní, standardní databáze SQL a žádné další funkce instance. SQL Server funkce jako integrace modulu SQL CLR, Agent SQL Server a dotazování mezi databázemi nejsou podporovány ve standardním Azure SQL Database. Tyto funkce jsou k dispozici pouze v Azure SQL Database modelu spravované instance.

Azure SQL Database je jediná inteligentní cloudová databázová služba vytvořená pro vývojáře aplikací. Je to také jediná cloudová databázová služba, která se průběžně škáluje bez výpadků, což vám umožní efektivně doručovat víceklientské aplikace. V konečném případě vám Azure SQL Database zaznamená více času na inovace a zrychluje váš čas na uvedení na trh. Můžete vytvářet zabezpečené aplikace a připojovat se k vaší databázi SQL pomocí jazyků a platforem, které dáváte přednost.

Azure SQL Database nabízí následující výhody:

- Integrované inteligentní funkce (Machine Learning), které se učí a přizpůsobí vaší aplikaci

- Zřizování databáze na vyžádání

- Rozsah nabídek pro všechny úlohy

- 99,99% dostupnost smlouvy SLA, nulová údržba

- Geografické replikace a obnovení služeb pro ochranu dat

- Funkce obnovení Azure SQL Databaseho bodu v čase

- Kompatibilita s SQL Server 2016, včetně hybridních a migračních

Standardní Azure SQL Database je blíž k PaaS než Azure SQL Database Managed instance. Preferovat standardní Azure SQL Database, protože získáte více výhod ze spravovaného cloudu. Azure SQL Database ale některé klíčové rozdíly od běžných a místních SQL Server instancí. V závislosti na tom, jaké jsou požadavky na databázi vaší aplikace a požadavky na podnik a zásady, nemusí být při plánování migrace do cloudu nejlepší volbou.

## <a name="when-to-move-your-original-rdbms-to-a-vm-iaas"></a>Kdy přesunout původní RDBMS do virtuálního počítače (IaaS)

Jednou z možností migrace je přesunout původní systém pro správu relačních databází (RDBMS), včetně Oracle, IBM DB2, MySQL, PostgreSQL nebo SQL Server, na podobný server, který běží na virtuálním počítači Azure. Pokud máte existující aplikace, které vyžadují nejrychlejší migraci do cloudu s minimálními změnami, nebo žádné změny, přímá migrace do IaaS v cloudu může být reálnou možností. Nemusí se jednat o nejlepší způsob, jak využít výhod všech výhod cloudu, ale je to pravděpodobně nejrychlejší počáteční cesta.

V současné době Microsoft Azure podporuje až [331 různých databázových serverů](https://azuremarketplace.microsoft.com/marketplace/apps/category/databases?page=1&subcategories=databases-all) nasazených jako virtuální počítače s IaaS. Patří sem oblíbené RDBMS, jako jsou SQL Server, Oracle, MySQL, PostgreSQL a IBM DB2, a mnoho dalších NoSQL databází, jako je MongoDB, Cassandra, DataStax, MariaDB a Cloudera.

> [!NOTE]
> I když přesunutí RDBMS do virtuálního počítače Azure může být nejrychlejší způsob, jak migrovat data do cloudu (protože je IaaS), tento přístup vyžaduje významnou investici do vašich IT týmů (správců databází a IT specialistů). Podnikové týmy musí být schopné nastavit a spravovat vysokou dostupnost, zotavení po havárii a opravy pro SQL Server. Tento kontext také potřebuje vlastní prostředí s úplnými právy správce.

## <a name="when-to-migrate-to-sql-server-as-a-vm-iaas"></a>Kdy migrovat na SQL Server jako virtuální počítač (IaaS)

Může existovat několik případů, kdy stále potřebujete migrovat na SQL Server jako běžný virtuální počítač. Příkladem scénáře je, že je třeba použít SQL Server Reporting Services. Ve většině případů může ale Azure SQL Database spravovaná instance poskytnout vše, co potřebujete k migraci z místních serverů SQL, takže by migrace na SQL Server VM měla být vaše poslední možnost, kterou si můžete vyzkoušet.

## <a name="use-azure-database-migration-service-to-migrate-your-relational-databases-to-azure"></a>Použití Azure Database Migration Service k migraci relačních databází do Azure 

Pomocí Azure Database Migration Service můžete migrovat relační databáze jako SQL Server, Oracle a MySQL do Azure, ať už máte cílovou databázi Azure SQL Database, Azure SQL Database spravovanou instanci nebo SQL Server na virtuálním počítači Azure.

Automatizovaný pracovní postup s vytvářením sestav hodnocení vás provede změnami, které je třeba provést před migrací databáze. Až budete připraveni, služba migruje zdrojovou databázi do Azure.

Pokaždé, když změníte původní RDBMS, možná budete muset test otestovat. V závislosti na výsledcích testování možná budete muset změnit také věty SQL nebo kód ORM (Object-relační mapování) ve vaší aplikaci.

Pokud máte nějakou jinou databázi (například IBM DB2) a zaberete přístup ke zvedání a posunu, možná budete chtít tyto databáze v Azure dál používat jako virtuální počítače s IaaS, pokud nejste ochotni provést složitější migraci dat. Složitější migrace dat bude vyžadovat další úsilí, protože migrujete na jiný typ databáze s novým schématem a různými programovacími knihovnami.

Informace o tom, jak migrovat databáze pomocí Azure Database Migration Service, najdete v článku [rychlejší přístup do cloudu pomocí Azure SQL Database spravované instance a Azure Database Migration Service](https://channel9.msdn.com/Events/Build/2017/P4008).

## <a name="additional-resources"></a>Další zdroje

- **Vyberte možnost cloudového SQL Server: Azure SQL Database (PaaS) nebo SQL Server na virtuálním počítači Azure (IaaS)**

    <https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas>

- **Získejte rychlejší přístup do cloudu pomocí spravované instance Azure SQL DB a Database Migration Service**

    <https://channel9.msdn.com/Events/Build/2017/P4008>

- **Migrace databáze SQL serveru do služby SQL Database v cloudu**

    <https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate>

- **Azure SQL Database**

    <https://azure.microsoft.com/services/sql-database/?v=16.50>

- **SQL Server na virtuálních počítačích**

    <https://azure.microsoft.com/services/virtual-machines/sql-server/>

> [!div class="step-by-step"]
> [Předchozí](lift-and-shift-existing-apps-azure-iaas.md)Další
> [](modernize-existing-apps-to-cloud-optimized/index.md)
