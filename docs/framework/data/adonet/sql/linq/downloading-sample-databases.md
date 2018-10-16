---
title: Získání ukázkových databází pro ukázky kódu ADO.NET
description: Stažení ukázkových databází používaných pro ukázky kódu v dokumentaci k rozhraní ADO.NET, jakož i nástroje SQL Server a správu
ms.date: 10/12/2018
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 75ae1895d683b669f51b33130fc2f47010e39814
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2018
ms.locfileid: "49347500"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a>Získání ukázkových databází pro ukázky kódu ADO.NET

Počet ukázky a návody v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dokumentaci použít ukázkové databáze a serveru SQL Server Express. Tyto produkty zdarma si můžete stáhnout z Microsoftu.

## <a name="get-the-adventureworks-sample-database"></a>Získat ukázkovou databází AdventureWorks

Stáhněte si ukázkovou databází AdventureWorks z následující úložiště GitHub:

[Ukázkových databází AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

Po stažení zálohy databáze (\*.bak) souborech, obnovení zálohy do instance systému SQL Server pomocí SQL Server Management Studio (SSMS). Zobrazit [získat SQL Server Management Studio](#get_ssms).

## <a name="get-the-northwind-sample-database"></a>Získat ukázkovou databázi Northwind

Stažení ukázkové databáze Northwind na následující stránce na webu Microsoft Download Center:

[Ukázkové databáze Pubs a Northwind](https://go.microsoft.com/fwlink?linkid=64296)

Po stažení souboru poklikejte na soubor k extrahování databází a skripty. Ve výchozím nastavení jsou soubory nainstalovaného ve složce `<drive>:\SQL Server 2000 Sample Databases`.

Před použitím databáze Northwind, musíte udělat jednu z následujících akcí:

- Znovu vytvořit databázi na instanci systému SQL Server spuštěním `instnwnd.sql` soubor skriptu v instalační složce Nástroje.

- Připojit `northwnd.mdf` soubor k odpovídajícímu `*.ldf` souboru protokolu určeného k instanci systému SQL Server.

## <a name="get_sql"></a> Získat SQL Server Express

SQL Server Express je zdarma, základní edice systému SQL Server, který je možné znovu distribuovat s aplikací. Stáhněte SQL Server Express z následující stránky:
  
[Edice SQL serveru Express](https://www.microsoft.com/sql-server/sql-server-editions-express)

Pokud používáte [sady Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB je součástí Community edition, stejně jako edice Professional a vyšší.  

## <a name="get_ssms"></a> Získat SQL Server Management Studio
Pokud chcete zobrazit nebo upravit databázi, kterou jste stáhli, můžete použít SQL Server Management Studio (SSMS). SSMS stáhněte z následující stránky:

[Stáhněte si SQL Server Management Studio (SSMS)](/sql/ssms/download-sql-server-management-studio-ssms) 

Můžete také zobrazit a spravovat databáze v prostředí integrovaného vývojového (prostředí IDE) sady Visual Studio. V [sady Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), připojte se k databázi z **Průzkumník objektů systému SQL Server**, nebo vytvoření datového připojení k databázi v **Průzkumníka serveru**. Otevření těchto podoken explorer z **zobrazení** nabídky.
  
## <a name="see-also"></a>Viz také:

- [Začínáme](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
