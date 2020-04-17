---
title: Získání ukázkových databází serveru SQL Server pro ukázky kódu ADO.NET
description: Stáhněte si ukázkové databáze serveru SQL Server použité v ukázkách kódu v dokumentaci ADO.NET, stejně jako sql server a nástroje pro správu
ms.date: 01/11/2019
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 3449f502834f449f5023bd52457d45ffaf9b0fa1
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607981"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a>Získat ukázkové databáze pro ukázky kódu ADO.NET

Několik příkladů a návodů v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dokumentaci použít ukázkové databáze serveru SQL Server a SQL Server Express. Tyto produkty si můžete stáhnout zdarma od společnosti Microsoft.

## <a name="get-the-northwind-sample-database-for-sql-server"></a>Získání ukázkové databáze Northwind pro SQL Server

Stáhněte `instnwnd.sql` si skript z následujícího úložiště GitHub a vytvořte a načtěte ukázkovou databázi Northwind pro SQL Server:

[Ukázkové databáze Northwind a pubs pro Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

Před použitím databáze Northwind je třeba spustit stažený `instnwnd.sql` soubor skriptu k opětovnému vytvoření databáze na instanci serveru SQL Server pomocí sql server management [studio](#get_ssms) nebo podobný nástroj. Postupujte podle pokynů v souboru Readme v úložišti.

> [!TIP]
> Pokud hledáte databázi Northwind pro aplikaci Microsoft Access, přečtěte si informace [o instalaci ukázkové databáze Northwind pro aplikaci Microsoft Access](#northwind_access).

## <a name="get-the-northwind-sample-database-for-microsoft-access"></a><a name="northwind_access"></a>Získání ukázkové databáze Northwind pro aplikaci Microsoft Access

Ukázková databáze Northwind pro aplikaci Microsoft Access není k dispozici v centru pro stahování Microsoft Download Center. Chcete-li aplikaci Northwind nainstalovat přímo z aplikace Access, proveďte následující akce:

1. Otevřít přístup.

1. Do pole **Hledat online šablony** zadejte **Northwind** a pak vyberte **Enter**.

1. Na obrazovce s výsledky vyberte **možnost Northwind**. Otevře se nové okno s popisem databáze Northwind.

1. V novém okně zadejte v textovém poli **Název souboru** název souboru pro kopii databáze Northwind.

1. Vyberte **Vytvořit**. Aplikace Access stáhne databázi Northwind a připraví soubor.

1. Po dokončení tohoto procesu se databáze otevře s úvodní obrazovkou.

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a>Získání ukázkové databáze AdventureWorks pro SQL Server

Stáhněte si ukázkovou databázi AdventureWorks pro SQL Server z následujícího úložiště GitHub:

[Ukázkové databáze AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

Po stažení jednoho ze souborů\*zálohy databáze ( .bak) obnovit zálohu do instance SQL Server pomocí SQL Server Management Studio (SSMS). Viz [Získání sql server management studio](#get_ssms).

## <a name="get-sql-server-management-studio"></a><a name="get_ssms"></a>Získat aplikaci SQL Server Management Studio
Pokud chcete zobrazit nebo upravit databázi, kterou jste stáhli, můžete použít SQL Server Management Studio (SSMS). Stáhněte si SSMS z následující stránky:

[Stažení SQL Server Management Studia (SSMS)](/sql/ssms/download-sql-server-management-studio-ssms)

Můžete také zobrazit a spravovat databáze v integrovaném vývojovém prostředí sady Visual Studio (IDE). V [sadě Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)se připojte k databázi z **průzkumníka objektů serveru SQL Server**nebo vytvořte datové připojení k databázi v **Průzkumníkovi serveru**. Otevřete tato podokna průzkumníků z nabídky **Zobrazení.**

## <a name="get-sql-server-express"></a><a name="get_sql"></a>Získat SQL Server Express

SQL Server Express je bezplatná edice sql serveru základní úrovně, kterou můžete dále distribuovat s aplikacemi. Stáhněte sql server express z následující stránky:
  
[Edice SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)

Pokud používáte [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019), SQL Server Express LocalDB je součástí bezplatné verze Společenství sady Visual Studio, stejně jako professional a vyšší edice.  

## <a name="see-also"></a>Viz také

- [Začínáme](getting-started.md)
