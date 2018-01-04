---
title: "Migrace relačních databází do azure"
description: "Modernizovat existující aplikace .NET s cloudu Azure a Windows kontejnery | migrace relačních databází do azure"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 221d8c2b837fb738425e26f3af4da895e4987212
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="migrate-your-relational-databases-to-azure"></a>Migrace relačních databází do azure

Vizi: Azure nabízí nejúplnější migrace databáze.

V Azure můžete migrovat databázové servery přímo do virtuálních počítačů IaaS (čistý navýšení a shift), nebo můžete migrovat do Azure SQL Database pro další výhody. Azure SQL Database nabízí spravované instance a možnosti úplné databáze jako služba (DBaaS). Obrázek 3-1 zobrazuje více relační databáze cesty migrace, které jsou k dispozici v Azure.

![Cesty migrace databáze v Azure](./media/image3-1.png)

> **Obrázek 3-1.** Cesty migrace databáze v Azure

## <a name="when-to-migrate-to-azure-sql-database-managed-instance"></a>Když k migraci na Azure spravované Instance databáze SQL

Ve většině případů bude Azure SQL Database spravované Instance nejlepší možnost vzít v úvahu při migraci dat do Azure. Pokud provádíte migraci databáze systému SQL Server a potřebujete téměř 100 % záruku toho, že nebudete muset přepracování aplikace nebo provést změny dat nebo dat přístupový kód, zvolte funkci spravované Instance databáze SQL Azure.

Azure SQL Database spravované Instance je nejlepší možnost, pokud máte další požadavky pro funkci na úrovni instance systému SQL Server nebo požadavky na izolaci kromě funkcí uvedených v standardní databáze SQL Azure (model jedné databáze). Tato naposledy je volba orientované PaaS, ale nenabízí stejné funkce jako u tradiční SQL server. Migrace může surface frictions.

Organizace, která udělal hloubkové investice v úrovni instance systému SQL Server funkce by například těžit z migrace na spravované Instance systému SQL. Příklady možností úrovni instance systému SQL Server patří SQL common language runtime (CLR) integrace agenta systému SQL Server a mezidatabázové dotazování. Podpora pro tyto funkce nejsou k dispozici v standardní Azure SQL Database (model jednotlivé databáze).

V organizaci, která funguje ve vysoce regulovaná odvětví, které je udržovat izolace z bezpečnostních důvodů, mohou také těžit z Výběr modelu spravovat instanci SQL.

Spravované Instance ve službě Azure SQL Database má následující vlastnosti:

-   Izolace zabezpečení prostřednictvím Azure Virtual Network

-   Prostor kompatibilita aplikací, se tyto funkce:

    -   Agent systému SQL Server a SQL Server Profiler

    -   Mezidatabázové odkazy a dotazy SQL CLR replikace, shromažďování dat změn (CDC) a služby Service Broker

-   Až 35 TB velikosti databáze

-   Migrace výpadky minimální, se tyto funkce:

    -   Služba Azure databáze migrace

    -   Nativní zálohování a obnovení a přesouvání protokolu

S těmito možnostmi když migrujete existující databáze aplikace do Azure SQL Database, spravované Instance modelu nabízí téměř 100 % výhod Paas pro SQL Server. Spravované Instance je prostředí serveru SQL Server, kde můžete pokračovat pomocí možností na úrovni instance beze změny návrhu aplikace.

Spravované Instance je pravděpodobně nejlepší podnikům, které aktuálně používáte SQL Server, a které vyžadují flexibilitu při jejich zabezpečení sítě v cloudu. Je to jako mít privátní virtuální sítě pro vaše databáze SQL.

## <a name="when-to-migrate-to-azure-sql-database"></a>Při migraci do Azure SQL Database 

Jak je uvedeno, standardní Azure SQL Database je plně spravovaná, relační DBaaS. Databáze SQL aktuálně spravuje miliony provozních databází mezi 38 datových centrech po celém světě. Podporuje širokou škálu aplikace a úlohy, Správa přehledné transakčních dat, řízení nejvíce datově náročné, kritické aplikace, které vyžadují pokročilé zpracování dat v globálním měřítku.

Z důvodu jeho úplné funkce PaaS a lepší ceny- a nakonec snížení nákladů – měli byste přejít na standardní databáze SQL Azure "výchozím možnost" Pokud máte aplikaci, že používá databáze systému SQL basic, standard a žádné další instance funkce. Funkce systému SQL Server jako integrace modulu CLR SQL, Agent serveru SQL Server a mezi databázové dotazy nejsou podporovány v standardní databáze SQL Azure. Tyto funkce jsou k dispozici pouze v modelu Azure spravované Instance databáze SQL.

Databáze SQL Azure je pouze inteligentního Cloudová služba databáze, která je sestavená pro vývojáře aplikace. Je také pouze cloudové služby databáze, která se přizpůsobí na průběžně, bez výpadku, můžete efektivně poskytovat víceklientské aplikace. Nakonec Azure SQL Database vám zůstane víc času mohou a ho zrychluje doby uvedení na trh. Můžete vytvářet aplikace, zabezpečení a připojení k vaší databázi SQL pomocí jazyky a platformy, které dáváte přednost.

Azure SQL Database nabízí následující výhody:

-   Vestavěné inteligentní (machine learning), který zjišťuje a přizpůsobuje do vaší aplikace

-   Zřizování databáze na vyžádání

-   Rozsah nabízí pro všechny úlohy

-   99,99 % dostupnost SLA, nulové údržby

-   Geografická replikace a obnovení služby ochrany dat

-   Azure SQL Database bodu v funkce čas obnovení

-   Kompatibilita s SQL Server 2016, včetně hybridních a migrace

Standardní databáze SQL Azure je blíž ke PaaS než Azure spravované Instance databáze SQL. Pokuste se použít, pokud je to možné, protože získáte další výhody z spravované cloudu. Ale Azure SQL Database má některé hlavní rozdíly z regulární a místní instance systému SQL Server. V závislosti na vaší stávající aplikaci požadavky na databázi a vaše podnikové požadavky a zásady nemusí být nejlepší volbou při plánování migrace do cloudu.

## <a name="when-to-move-your-original-rdbms-to-a-vm-iaas"></a>Při přesunutí vašeho původního RDBMS k virtuálnímu počítači (IaaS)

Mezi možnosti migrace je přesunout vašeho původního systému správy relačních databází (RDBMS), včetně Oracle, IBM DB2, MySQL, PostgreSQL a SQL Server, podobně jako server, který běží na virtuálním počítači Azure. Pokud máte existující aplikace, které vyžadují nejrychlejší migraci do cloudu s minimálními změnami nebo žádné změny ve všech, může být přímé migrace IaaS v cloudu správného možnost. Nemusí být nejlepší způsob, jak využít výhod všech cloudu, ale je pravděpodobně nejrychlejší počáteční cestu.

V současné době podporuje až do Microsoft Azure [331 různých databázové servery](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/category/databases?page=1&subcategories=databases-all) nasazená jako virtuální počítače IaaS. Jedná se o oblíbených RDBMSes jako SQL Server, Oracle, MySQL, PostgreSQL a IBM DB2 a mnoho dalších databáze NoSQL jako MongoDB, Cassandra, DataStax, MariaDB a Cloudera.

> [!NOTE]
> I když přesunutí vaší RDBMS na virtuální počítač Azure může být nejrychlejší způsob, jak migrovat data do cloudu (protože je IaaS), tento postup vyžaduje významné investice do týmům IT (správce databáze a IT profesionály). Enterprise týmy musí být schopni nastavit a spravovat vysokou dostupnost, zotavení po havárii a opravy pro SQL Server. Také je nutné tento kontext přizpůsobené prostředí, s plná práva pro správu.

## <a name="when-to-migrate-to-sql-server-as-a-vm-iaas"></a>Pokud chcete migrovat do systému SQL Server jako virtuální počítač (IaaS)

Může být několik případů, kde je stále nutné migrovat do systému SQL Server jako regulární virtuální počítač. Příklad scénáře je, pokud budete muset použít SQL Server Reporting Services. Ve většině případů ale Azure SQL Database spravované Instance může poskytnout vše potřebné k migraci z místních serverů SQL, takže migrace virtuálního počítače s SQL Server by mělo být vaší poslední možnost pokusit.

## <a name="use-azure-database-migration-service-to-migrate-your-relational-databases-to-azure"></a>Migrace relačních databází do Azure pomocí služby migrace databáze Azure 

Migrace relační databáze jako SQL Server a Oracle, MySQL do Azure, můžete použít služba migrace databáze Azure, zda je cílová databáze Azure SQL Database, spravované Instance serveru Azure SQL Database nebo SQL Server na virtuálním počítači Azure.

Automatizované pracovní postup, s vytvářením sestav hodnocení, vás provede změny, které je potřeba udělat před zahájením migrace databáze. Jakmile budete připraveni, služba migruje zdrojové databáze Azure.

Vždy, když změníte původní RDBMS, možná budete muset testování. Vám může také muset změnit věty SQL nebo relační objekt mapování (ORM) kód ve vaší aplikaci, v závislosti na výsledcích testování.

Pokud máte jakékoli jiné databáze (například IBM DB2) a požádáte o navýšení a shift přístupu, můžete chtít používat tyto databáze jako virtuální počítače IaaS v Azure, pokud chcete provádět složitější dat migrace. Složitější migrace dat bude vyžadovat další úsilí, protože jste by migrace na jiné databázi typu se schématem a různé programovací knihovny.

Další postupy k migraci databáze pomocí služba migrace databáze Azure najdete v tématu [získat do cloudu s Azure spravované Instance databáze SQL a služba migrace databáze Azure rychlejší](https://channel9.msdn.com/Events/Build/2017/P4008).

## <a name="additional-resources"></a>Další zdroje

-   **Volba cloudového řešení SQL serveru: Azure SQL Database (PaaS) nebo SQL Server na virtuální počítač Azure (IaaS)**

    [https://docs.microsoft.com/Azure/SQL-Database/SQL-Database-paas-vs-SQL-Server-iaas](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas)

-   **Získat rychlejší s Azure SQL DB spravované Instance a služba migrace databáze do cloudu**

    [https://channel9.msdn.com/events/Build/2017/P4008](https://channel9.msdn.com/Events/Build/2017/P4008)

-   **Migrace databáze SQL serveru do databáze SQL v cloudu**

    [https://docs.microsoft.com/Azure/SQL-Database/SQL-Database-cloud-Migrate](https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate)

-   **Databáze Azure SQL**

    [https://Azure.microsoft.com/Services/SQL-Database/?v=16.50](https://azure.microsoft.com/services/sql-database/?v=16.50)

-   **SQL Server na virtuální počítače**

    [https://Azure.microsoft.com/Services/Virtual-Machines/SQL-Server/](https://azure.microsoft.com/services/virtual-machines/sql-server/)

>[!div class="step-by-step"]
[Předchozí](lift-and-shift-existing-apps-azure-iaas.md)
[další](lift-and-shift-existing-apps-devops/index.md)