---
title: Získat ukázky kódu ADO.NET ukázkové databáze systému SQL Server
description: Stažení ukázkových databází SQL serveru použité v ukázkách kódu v dokumentaci k rozhraní ADO.NET, jakož i nástroje SQL Server a správu
ms.date: 10/18/2018
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 8ab65f992c9cf2b65271a237fa06eb96e358ae6a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153485"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a>Získání ukázkových databází pro ukázky kódu ADO.NET

Počet příklady a názorné postupy v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dokumentace ke službě pomocí ukázkových databází systému SQL Server a SQL Server Express. Tyto produkty zdarma si můžete stáhnout z Microsoftu.

## <a name="get-the-northwind-sample-database-for-sql-server"></a>Získat ukázkové databáze Northwind pro SQL Server

Stáhněte si skript `instnwnd.sql` z následující úložiště GitHub k vytváření a načítání ukázkové databáze Northwind pro SQL Server:

[Ukázkové databáze Northwind a pubs pro Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

Než použijete databázi Northwind, musíte spustit na stažený `instnwnd.sql` soubor skriptu znovu vytvořit databázi na instanci systému SQL Server s použitím [SQL Server Management Studio](#get_ssms) nebo něco podobného. Postupujte podle pokynů v souboru Readme v úložišti.

> [!TIP]
> Pokud hledáte databázi Northwind pro aplikaci Microsoft Access, přečtěte si téma [instalace ukázkové databáze Northwind pro aplikaci Microsoft Access](#northwind_access).

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a>Získat ukázkovou databází AdventureWorks pro SQL Server

Stáhněte si ukázkovou databází AdventureWorks pro SQL Server z následující úložiště GitHub:

[Ukázkových databází AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

Po stažení zálohy databáze (\*.bak) souborech, obnovení zálohy do instance systému SQL Server pomocí SQL Server Management Studio (SSMS). Zobrazit [získat SQL Server Management Studio](#get_ssms).

## <a name="get_sql"></a> Získat SQL Server Express

SQL Server Express je zdarma, základní edice systému SQL Server, který je možné znovu distribuovat s aplikací. Stáhněte SQL Server Express z následující stránky:
  
[SQL Server Express Edition](https://www.microsoft.com/sql-server/sql-server-editions-express)

Pokud používáte [sady Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB je součástí sady Visual Studio bezplatná edice Community, jakož i edice Professional a vyšší.  

## <a name="get_ssms"></a> Získat SQL Server Management Studio
Pokud chcete zobrazit nebo upravit databázi, kterou jste stáhli, můžete použít SQL Server Management Studio (SSMS). SSMS stáhněte z následující stránky:

[Stáhněte si SQL Server Management Studio (SSMS)](/sql/ssms/download-sql-server-management-studio-ssms) 

Můžete také zobrazit a spravovat databáze v prostředí integrovaného vývojového (prostředí IDE) sady Visual Studio. V [sady Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), připojte se k databázi z **Průzkumník objektů systému SQL Server**, nebo vytvoření datového připojení k databázi v **Průzkumníka serveru**. Otevření těchto podoken explorer z **zobrazení** nabídky.

## <a name="northwind_access"></a> Instalace ukázkové databáze Northwind pro aplikaci Microsoft Access

Ukázkové databázi Northwind pro aplikaci Microsoft Access není k dispozici na webu Microsoft Download Center. Pokud chcete nainstalovat Northwind přímo z aplikace Access, proveďte následující akce:

1. Otevřete Access.

1. Zadejte **Northwind** v **hledat Online šablony** a potom vyberte **Enter**.

1. V okně výsledků vyberte **Northwind**. Otevře se nové okno s popisem databázi Northwind.

1. V novém okně v **název_souboru** textové pole, zadejte název souboru pro kopii databáze Northwind.

1. Vyberte **Vytvořit**. Přístup k databázi Northwind stáhne a připraví soubor.

1. Po dokončení tohoto procesu se otevře databáze úvodní obrazovka.

## <a name="see-also"></a>Viz také:

- [Začínáme](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
