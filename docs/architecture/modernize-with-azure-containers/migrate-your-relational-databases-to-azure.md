---
title: Migrace relačních databází do azure
description: Modernizace existujících aplikací .NET pomocí Azure Cloudu a kontejnerů Windows | migrace relačních databází do azure
ms.date: 04/28/2018
ms.openlocfilehash: efd1548c3f74fc27450f4949d71a1c4d61907ba5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73093618"
---
# <a name="migrate-your-relational-databases-to-azure"></a>Migrace relačních databází do azure

Vize: Azure nabízí nejkomplexnější migraci databází.

V Azure můžete migrovat databázové servery přímo do virtuálních počítačů IaaS (čisté výtah a shift) nebo můžete migrovat do Azure SQL Database, pro další výhody. Azure SQL Database nabízí spravované instance a úplné možnosti databáze jako služba (DBaaS). Obrázek 3-1 znázorňuje více cest migrace relační databáze, které jsou k dispozici v Azure.

![Cesty migrace databáze v Azure](./media/image3-1.png)

**Obrázek 3-1.** Cesty migrace databáze v Azure

## <a name="when-to-migrate-to-azure-sql-database-managed-instance"></a>Kdy se má migrovat do spravované instance Azure SQL Database

Ve většině případů bude nejlepší možností, kterou je třeba zvážit při migraci dat do Azure. Pokud migrujete databáze SQL Serveru a potřebujete téměř 100% jistotu, že nebudete muset předělat aplikaci nebo provádět změny v kódu pro data nebo přístup k datům, zvolte funkci Spravované instance azure SQL Database.

Azure SQL Database Managed Instance je nejlepší volbou, pokud máte další požadavky na sql server na úrovni instance funkce nebo požadavky na izolaci nad rámec funkcí poskytovaných ve standardní Azure SQL Database (model jedné databáze). Tento poslední je nejvíce PaaS-orientované volby, ale nenabízí stejné funkce jako tradiční SQL server. Migrace může povrchové tření.

Například organizace, která provedla hluboké investice do funkcí SQL Serveru na úrovni instancí, by měla prospěch z migrace na spravovanou instanci SQL. Příklady funkcí SQL Serveru na úrovni instance zahrnují integraci SQL COMMON Language runtime (CLR), agenta serveru SQL A dotazování mezi databázemi. Podpora těchto funkcí není k dispozici ve standardní Azure SQL Database (model s jednou databází).

Organizace, která pracuje ve vysoce regulovaném oboru a která potřebuje udržovat izolaci z bezpečnostních důvodů, může také mít prospěch z výběru modelu spravované instance SQL.

Spravovaná instance v Azure SQL Database má následující charakteristiky:

- Izolace zabezpečení prostřednictvím virtuální sítě Azure

- Kompatibilita povrchu aplikace s těmito funkcemi:

  - Agent serveru SQL A Profiler serveru SQL Server

  - Odkazy a dotazy mezi databázemi, SQL CLR, replikace, sběr dat (CDC) a service broker

- Velikosti databáze až 35 TB

- Migrace s minimálníprostožnou prostoji s těmito funkcemi:

  - Azure Database Migration Service

  - Nativní zálohování a obnovení a přesouvání protokolu

Díky těmto možnostem nabízí model spravované instance při migraci existujících aplikačních databází do azure SQL database téměř 100 % výhod PaaS pro SQL Server. Spravovaná instance je prostředí serveru SQL Server, ve kterém budete nadále používat možnosti na úrovni instance beze změny návrhu aplikace.

Spravovaná instance je pravděpodobně nejvhodnější pro podniky, které aktuálně používají SQL Server a které vyžadují flexibilitu v zabezpečení sítě v cloudu. Je to jako mít privátní virtuální síť pro vaše SQL databáze.

## <a name="when-to-migrate-to-azure-sql-database"></a>Kdy se má migrovat do azure sql databáze

Jak již bylo zmíněno, standardní Azure SQL Database je plně spravované, relační DBaaS. SQL Database v současné době spravuje miliony produkčních databází napříč 38 datovými centry po celém světě. Podporuje širokou škálu aplikací a úloh, od správy jednoduchých transakčních dat až po řízení nejextrémnějších a nejzákladnějších aplikací, které vyžadují pokročilé zpracování dat v globálním měřítku.

Vzhledem k jeho plné funkce PaaS, lepší ceny a nakonec nižší náklady-měli byste přejít na standardní Azure SQL Database jako "výchozí volba", pokud máte aplikaci, která používá základní, standardní databáze SQL a žádné další funkce instance. Funkce SQL Serveru, jako je integrace SQL CLR, agent SQL Server a dotazování mezi databázemi, nejsou ve standardní azure sql databázi podporovány. Tyto funkce jsou dostupné jenom v modelu spravované instance Azure SQL Database.

Azure SQL Database je jediná inteligentní cloudová databázová služba, která je vytvořená pro vývojáře aplikací. Je to také jediná cloudová databázová služba, která se škáluje za chodu bez prostojů, aby vám pomohla efektivně poskytovat víceklientské aplikace. Azure SQL Database vám nakonec ponechá více času na inovace a urychlí váš čas uvedení na trh. Zabezpečené aplikace a připojení k databázi SQL můžete vytvářet pomocí jazyků a platforem, které upřednostňujete.

Azure SQL Database nabízí následující výhody:

- Integrovaná inteligence (strojové učení), která se učí a přizpůsobuje se vaší aplikaci

- Zřizování databáze na vyžádání

- Řada nabídek pro všechny úlohy

- 99.99% dostupnost SLA, nulová údržba

- Geografické replikace a obnovení služeb pro ochranu dat

- Funkce Azure SQL Database Point in Time Restore

- Kompatibilita se SQL Serverem 2016, včetně hybridních a migrace

Standardní Azure SQL Database je blíže k PaaS než Azure SQL Database Spravované instance. Preferujte standardní Azure SQL Database, protože získáte další výhody ze spravovaného cloudu. Azure SQL Database má však některé klíčové rozdíly od běžných a místních instancí SQL Serveru. V závislosti na požadavcích na databázi vaší stávající aplikace a vašich podnikových požadavcích a zásadách nemusí být při plánování migrace do cloudu tou nejlepší volbou.

## <a name="when-to-move-your-original-rdbms-to-a-vm-iaas"></a>Kdy přesunout původní RDBMS do virtuálního počítače (IaaS)

Jednou z možností migrace je přesunutí původního systému správy relačních databází (RDBMS), včetně Oracle, IBM DB2, MySQL, PostgreSQL nebo SQL Server, na podobný server, který běží na virtuálním počítači Azure. Pokud máte existující aplikace, které vyžadují nejrychlejší migraci do cloudu s minimálními změnami nebo vůbec žádné změny, může být přímá migrace na IaaS v cloudu spravedlivou volbou. Nemusí to být nejlepší způsob, jak využít výhod cloudu, ale je to pravděpodobně nejrychlejší počáteční cesta.

V současné době Microsoft Azure podporuje až [331 různých databázových serverů nasazených](https://azuremarketplace.microsoft.com/marketplace/apps/category/databases?page=1&subcategories=databases-all) jako virtuální počítače IaaS. Patří mezi ně populární RDBMS jako SQL Server, Oracle, MySQL, PostgreSQL a IBM DB2 a mnoho dalších databází NoSQL, jako jsou MongoDB, Cassandra, DataStax, MariaDB a Cloudera.

> [!NOTE]
> I když přesunutí RDBMS do virtuálního počítače Azure může být nejrychlejší způsob, jak migrovat data do cloudu (protože je IaaS), tento přístup vyžaduje významné investice do it týmů (správci databáze a IT profesionálové). Podnikové týmy musí být schopny nastavit a spravovat vysokou dostupnost, zotavení po havárii a opravy pro SQL Server. Tento kontext také potřebuje přizpůsobené prostředí s úplnými právy správce.

## <a name="when-to-migrate-to-sql-server-as-a-vm-iaas"></a>Kdy migrovat na SQL Server jako virtuální modul (IaaS)

Může být několik případů, kdy stále potřebujete migrovat na SQL Server jako běžný virtuální modul. Příklad scénáře je, pokud potřebujete použít SQL Server Reporting Services. Ve většině případů však Azure SQL Database Managed Instance můžete poskytnout vše, co potřebujete k migraci z místních serverů SQL, takže migrace na virtuální počítač SQL Server by měla být vaše poslední možnost vyzkoušet.

## <a name="use-azure-database-migration-service-to-migrate-your-relational-databases-to-azure"></a>Migrace relačních databází do Azure pomocí služby Azure Database Migration Service

Pomocí služby Migrace databáze Azure můžete migrovat relační databáze, jako jsou SQL Server, Oracle a MySQL, do Azure, ať už je cílovou databází Azure SQL Database, Azure SQL Database Managed Instance nebo SQL Server na virtuálním počítači Azure.

Automatizovaný pracovní postup s vykazováním hodnocení vás provede změnami, které je třeba provést před migrací databáze. Až budete připraveni, služba migruje zdrojovou databázi do Azure.

Při každé změně původnírdbms, možná budete muset znovu otestovat. V závislosti na výsledcích testování může být také nutné změnit věty SQL nebo kód ORM (Object-Relational Mapping) v aplikaci.

Pokud máte jinou databázi (například IBM DB2) a rozhodnete se pro přístup výtahu a posunu, můžete pokračovat v používání těchto databází jako virtuálních monů IaaS v Azure, pokud nejste ochotni provést složitější migraci dat. Složitější migrace dat bude vyžadovat další úsilí, protože byste se stěhovali do jiného typu databáze s novým schématem a různými programovacími knihovnami.

Informace o migraci databází pomocí služby Migrace databáze Azure najdete v tématu [Rychlejší přístup ke cloudu pomocí služby Azure SQL Database Managed Instance a Azure Database Migration Service](https://channel9.msdn.com/Events/Build/2017/P4008).

## <a name="additional-resources"></a>Další zdroje

- **Zvolte možnost cloudového SQL Serveru: Azure SQL Database (PaaS) nebo SQL Server na virtuálním počítači Azure (IaaS)**

    <https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas>

- **Rychlejší přístup ke cloudu díky spravované instanci Azure SQL DB a službě migrace databáze**

    <https://channel9.msdn.com/Events/Build/2017/P4008>

- **Migrace databáze systému SQL Server do služby SQL Database v cloudu**

    <https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate>

- **Databáze Azure SQL**

    <https://azure.microsoft.com/services/sql-database/?v=16.50>

- **SQL Server na virtuálních počítačích**

    <https://azure.microsoft.com/services/virtual-machines/sql-server/>

> [!div class="step-by-step"]
> [Předchozí](lift-and-shift-existing-apps-azure-iaas.md)
> [další](modernize-existing-apps-to-cloud-optimized/index.md) <!-- Next Chapter -->
