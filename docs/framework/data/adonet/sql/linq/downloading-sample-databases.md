---
title: Získání ukázkových databází pro ukázky kódu ADO.NET
description: Stažení ukázkových databází používaných pro ukázky kódu v dokumentaci k rozhraní ADO.NET, jakož i nástroje SQL Server a správu
ms.date: 10/18/2018
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 9779300288135cb9332a028d547ce55a07e89471
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188388"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a>Získání ukázkových databází pro ukázky kódu ADO.NET

Počet ukázky a návody v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dokumentaci použít ukázkové databáze a serveru SQL Server Express. Tyto produkty zdarma si můžete stáhnout z Microsoftu.

## <a name="get-the-northwind-sample-database"></a>Získat ukázkovou databázi Northwind

Stažení ukázkové databáze Northwind na následující stránce na webu Microsoft Download Center:

[Ukázkové databáze Pubs a Northwind](https://go.microsoft.com/fwlink?linkid=64296)

Po stažení souboru poklikejte na soubor k extrahování databází a skripty. Ve výchozím nastavení jsou soubory nainstalovaného ve složce `<drive>:\SQL Server 2000 Sample Databases`.

Než použijete databázi Northwind, budete muset znovu vytvořit databázi na instanci systému SQL Server s použitím [SQL Server Management Studio](#get_ssms) nebo něco podobného pro spuštění `instnwnd.sql` soubor skriptu v instalační složce Nástroje.

## <a name="get-the-adventureworks-sample-database"></a>Získat ukázkovou databází AdventureWorks

Stáhněte si ukázkovou databází AdventureWorks z následující úložiště GitHub:

[Ukázkových databází AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

Po stažení zálohy databáze (\*.bak) souborech, obnovení zálohy do instance systému SQL Server pomocí SQL Server Management Studio (SSMS). Zobrazit [získat SQL Server Management Studio](#get_ssms).

## <a name="get_sql"></a> Získat SQL Server Express

SQL Server Express je zdarma, základní edice systému SQL Server, který je možné znovu distribuovat s aplikací. Stáhněte SQL Server Express z následující stránky:
  
[Edice SQL serveru Express](https://www.microsoft.com/sql-server/sql-server-editions-express)

Pokud používáte [sady Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB je součástí bezplatné Community edition, stejně jako edice Professional a vyšší.  

## <a name="get_ssms"></a> Získat SQL Server Management Studio
Pokud chcete zobrazit nebo upravit databázi, kterou jste stáhli, můžete použít SQL Server Management Studio (SSMS). SSMS stáhněte z následující stránky:

[Stáhněte si SQL Server Management Studio (SSMS)](/sql/ssms/download-sql-server-management-studio-ssms) 

Můžete také zobrazit a spravovat databáze v prostředí integrovaného vývojového (prostředí IDE) sady Visual Studio. V [sady Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), připojte se k databázi z **Průzkumník objektů systému SQL Server**, nebo vytvoření datového připojení k databázi v **Průzkumníka serveru**. Otevření těchto podoken explorer z **zobrazení** nabídky.
  
## <a name="see-also"></a>Viz také:

- [Začínáme](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
