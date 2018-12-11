---
title: Migrace relačních databází do azure
description: Modernizace stávajících aplikací .NET pomocí cloudu Azure a kontejnery Windows | migrace relačních databází do azure
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: a2aedc9729c674a7b4958506b90c285e54d8d724
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153758"
---
# <a name="migrate-your-relational-databases-to-azure"></a>Migrace relačních databází do azure

Pro zpracování obrazu: Azure nabízí nejkomplexnější migrace databáze.

V Azure můžete migrovat vaše databázové servery přímo do virtuálních počítačů IaaS (čistě výtah a posunout), nebo můžete migrovat do služby Azure SQL Database, nabízí další výhody. Azure SQL Database nabízí spravované instance a možnosti úplné database-as-a-service (DBaaS). Obrázek 3-1 zobrazuje více relační databáze cesty migrace jsou dostupné v Azure.

![Cesty migrace databáze v Azure](./media/image3-1.png)

> **Obrázek 3-1.** Cesty migrace databáze v Azure

## <a name="when-to-migrate-to-azure-sql-database-managed-instance"></a>Kdy migrovat do Azure SQL Database Managed Instance

Ve většině případů bude Azure SQL Database Managed Instance je nejlepší možnost vzít v úvahu při migraci dat do Azure. Pokud provádíte migraci databází systému SQL Server a potřebujete téměř 100 % záruku, že nebudete muset úprava architektury aplikace nebo provést změny dat nebo kód přístupu k datům, zvolte funkci Azure SQL Database Managed Instance.

Pokud máte další požadavky pro funkci na úrovni instance systému SQL Server nebo požadavky na izolaci nad rámec funkcí v Azure SQL Database úrovně standard (model s izolovanými databázemi), Azure SQL Database Managed Instance je nejlepší možností. Tento poslední z nich je volba orientované PaaS, ale nenabízí stejné funkce jako u tradiční SQL serveru. Migrace může přinášet frictions.

Například organizace, který má k hloubkové investice do funkce na úrovni instance serveru SQL Server, budou těžit z migrace na spravované instanci SQL. Příklady možností na úrovni instance serveru SQL Server SQL common language runtime (CLR) integraci agenta systému SQL Server a dotazování napříč databázemi. Podpora pro tyto funkce není k dispozici v SQL Database úrovně standard Azure (jeden databázový model).

Organizace, který pracuje ve vysoce regulované odvětví a které je potřeba udržovat izolaci z bezpečnostních důvodů také by mohlo prospět Výběr modelu spravované instanci SQL.

Ve službě Azure SQL Database Managed Instance má následující vlastnosti:

- Izolace zabezpečení pomocí Azure Virtual Network

- Zařízení surface kompatibility aplikací, s těmito funkcemi:

  - Agent systému SQL Server a SQL Server Profiler

  - Mezidatabázové dotazy SQL CLR a odkazy na replikaci, změnit data capture (CDC) a služby Service Broker

- Databáze velikosti až 35 TB

- Migrace s minimální výpadků, s těmito funkcemi:

  - Azure Database Migration Service

  - Nativní zálohování a obnovení a přesouvání protokolu

S těmito možnostmi při migraci stávajících databází aplikace ke službě Azure SQL Database Managed Instance model nabízí téměř 100 % výhody Paas pro SQL Server. Managed Instance je prostředí serveru SQL Server, kde můžete pokračovat pomocí možností na úrovni instance beze změny návrhu vaší aplikace.

Managed Instance je pravděpodobně nejvhodnější pro podniky, které aktuálně používáte SQL Server, a které vyžadují flexibilitu při jejich zabezpečení sítě v cloudu. Je to jako mít privátní virtuální sítě pro vaše databáze SQL.

## <a name="when-to-migrate-to-azure-sql-database"></a>Kdy migrovat do služby Azure SQL Database

Jak už bylo zmíněno, standardní Azure SQL Database je plně spravovaná, relační DBaaS. SQL Database spravuje miliony provozních databází, aktuálně v 38 datových centrech po celém světě. Podporuje širokou škálu aplikací a úloh, od správy jednoduché transakčních dat, podpora nejvíce oborovými výzkumníky, kritické aplikace, které vyžadují pokročilé zpracování dat v globálním měřítku.

Z důvodu jeho funkcemi PaaS lépe ceny – a nakonec snížit náklady na-byste měli přejít na standardní Azure SQL Database jako zvoleného"Výchozí" Pokud máte aplikaci, že používá basic, standard a databázím SQL, žádné další instanci funkce. Funkce SQL serveru jako integrace modulu CLR SQL Agent systému SQL Server a dotazování napříč databázemi nejsou podporovány ve standardní databázi SQL Azure. Tyto funkce jsou k dispozici pouze v modelu Azure SQL Database Managed Instance.

Azure SQL Database je pouze inteligentní Cloudová databázová služba, která je vytvořená pro vývojáře aplikací. Je také jediným Cloudová databázová služba, která se škáluje na průběžné, bez jakýchkoli prostojů, abychom vám efektivně doručovat víceklientské aplikace. Nakonec Azure SQL Database opustí, více času na inovace a zrychluje dobu uvedení na trh. Můžete vytvářet zabezpečené aplikace a připojení k SQL database s použitím jazyků a platforem, které dáváte přednost.

Azure SQL Database nabízí následující výhody:

- Integrované inteligentní funkce (strojové učení), která se učí a adaptuje se pro vaši aplikaci

- Zřízení databáze na vyžádání

- Rozsah nabídky pro všechny úlohy

- dostupnost 99,99 % smlouva SLA, žádná Údržba díky samosprávě

- Geografická replikace a obnovení služby ochrany dat

- Azure SQL Database bod obnovení funkce

- Kompatibilita s SQL serverem 2016, včetně hybridních a migrace

Standardní Azure SQL Database je blíže k PaaS než Azure SQL Database Managed Instance. Upřednostňují standardní Azure SQL Database, protože ze spravovaného cloudu dostanete další výhody. Ale Azure SQL Database má několik klíčových rozdílů v pravidelných a místní instance systému SQL Server. V závislosti na vaší stávající databáze podle požadavků vaší aplikace a vaše podnikové požadavky a zásady nemusí být nejlepší volbou při plánování migrace do cloudu.

## <a name="when-to-move-your-original-rdbms-to-a-vm-iaas"></a>Kdy se má přesunout váš původním relační databázový systém na virtuálním počítači (IaaS)

Jednou z možností migrace je přesunout váš původním relační databázový systém (RDBMS), včetně Oracle, IBM DB2, MySQL, PostgreSQL nebo SQL Server, podobně jako server, na kterém běží na Virtuálním počítači Azure. Pokud máte aplikace požadující nejrychlejší migrace do cloudu s minimálními změnami nebo žádnými změnami vůbec přímé migrace na IaaS v cloudu může být reálnou možnost. Nejlepší způsob, jak využít výhod všech cloudu nemusí být, ale je pravděpodobně nejrychlejší počáteční cesty.

V současné době podporuje Microsoft Azure do [331 jiné databázové servery](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/category/databases?page=1&subcategories=databases-all) nasazená jako virtuální počítače IaaS. Patří mezi ně oblíbených relační databázový systém, jako je SQL Server, Oracle, MySQL, PostgreSQL a IBM DB2 a mnoha dalších databáze NoSQL jako MongoDB Cassandra, DataStax, MariaDB a Cloudera.

> [!NOTE]
> Ačkoli přesunutí vaše relační databázový systém na Virtuálním počítači Azure může být nejrychlejší způsob, jak migrovat data do cloudu (protože je IaaS), tento přístup vyžaduje značné investice při vaše týmy IT (správci databází a IT Profesionálové). Enterprise týmy musí být schopni nastavit a spravovat vysokou dostupnost, zotavení po havárii a opravy pro SQL Server. Tento kontext musí také přizpůsobené prostředí s úplnými právy.

## <a name="when-to-migrate-to-sql-server-as-a-vm-iaas"></a>Kdy migrovat do systému SQL Server jako virtuální počítač (IaaS)

Může existovat několik případů, kdy stále potřebujete migrovat na SQL Server jako regulární virtuální počítač. Příklad scénáře je, pokud budete muset použít SQL Server Reporting Services. Ve většině případů však Azure SQL Database Managed Instance můžete zadat všechno, co je potřeba migrovat z místních SQL serverech, migrace do virtuálního počítače s SQL serverem by tak měly být vaší poslední možnost vyzkoušet.

## <a name="use-azure-database-migration-service-to-migrate-your-relational-databases-to-azure"></a>Migrace relačních databází do Azure pomocí Azure Database Migration Service 

Azure Database Migration Service můžete použít k migraci do Azure, relační databáze jako SQL Server, Oracle nebo MySQL, jestli je cílová databáze Azure SQL Database, Azure SQL Database Managed Instance nebo SQL Server na Virtuálním počítači Azure.

Automatizovaný workflow, generování sestav posouzení, vás provede změny, které je třeba provést před zahájením migrace databáze. Až budete připravení, služba migraci zdrojové databáze do Azure.

Pokaždé, když změníte původní relační databázový systém, můžete potřebovat k testování. Potřebujete také změnit věty SQL nebo kód objektově-relační mapování (ORM) určené ve vaší aplikaci, v závislosti na výsledcích testování.

Pokud máte jakékoli jiné databáze (například IBM DB2) a pokud se rozhodnete výtah a posunout přístup, můžete chtít pokračovat v používání těchto databází jako virtuální počítače IaaS v Azure, pokud se nechcete provádět složitější data migrace. Složitější data migrace bude vyžadovat další úsilí, protože jste by migrace na jinou databázi typu se nové schéma a různé programovací knihovny.

Zjistěte, jak migrovat databáze s využitím Azure Database Migration Service, najdete v článku [na cloud rychleji s využitím Azure SQL Database Managed Instance a Azure Database Migration Service](https://channel9.msdn.com/Events/Build/2017/P4008).

## <a name="additional-resources"></a>Další zdroje

- **Volba cloudového řešení systému SQL Server: Azure SQL Database (PaaS) nebo SQL Server na virtuálním počítači Azure (IaaS)**

    [https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas)

- **Na cloud rychleji s využitím Azure SQL DB mi a Database Migration Service**

    [https://channel9.msdn.com/Events/Build/2017/P4008](https://channel9.msdn.com/Events/Build/2017/P4008)

- **Migrace databáze SQL serveru do služby SQL Database v cloudu**

    [https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate](https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate)

- **Azure SQL Database**

    [https://azure.microsoft.com/services/sql-database/?v=16.50](https://azure.microsoft.com/services/sql-database/?v=16.50)

- **SQL Server na virtuálních počítačích**

    [https://azure.microsoft.com/services/virtual-machines/sql-server/](https://azure.microsoft.com/services/virtual-machines/sql-server/)

>[!div class="step-by-step"]
>[Předchozí](lift-and-shift-existing-apps-azure-iaas.md)
>[další](modernize-existing-apps-to-cloud-optimized/index.md)