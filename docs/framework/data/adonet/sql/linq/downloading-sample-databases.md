---
title: Získat ukázkovou SQL Server databáze pro ukázky kódu ADO.NET
description: Stáhněte si ukázkové SQL Server databáze používané v ukázkách kódu v dokumentaci k ADO.NET a také SQL Server a nástroje pro správu.
ms.date: 01/11/2019
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 60566041ff4f99e96c9aee052dbcc17b5e5da9e5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794026"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a>Získání ukázkových databází pro ukázky kódu ADO.NET

V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dokumentaci se používá několik příkladů a návodů, které používají ukázkové SQL Server databáze a SQL Server Express. Zdarma si můžete stáhnout tyto produkty od Microsoftu.

## <a name="get-the-northwind-sample-database-for-sql-server"></a>Získat ukázkovou databázi Northwind pro SQL Server

Stáhněte si skript `instnwnd.sql` z následujícího úložiště GitHubu, abyste vytvořili a načetli ukázkovou databázi Northwind pro SQL Server:

[Ukázkové databáze Northwind a pubs pro Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

Předtím, než budete moci použít databázi Northwind, je nutné spustit stažený `instnwnd.sql` soubor skriptu pro opětovné vytvoření databáze na instanci SQL Server pomocí [SQL Server Management Studio](#get_ssms) nebo podobného nástroje. Postupujte podle pokynů v souboru Readme v úložišti.

> [!TIP]
> Pokud hledáte databázi Northwind pro Microsoft Access, přečtěte si téma [Instalace ukázkové databáze Northwind pro Microsoft Access](#northwind_access).

## <a name="northwind_access"></a>Získat ukázkovou databázi Northwind pro Microsoft Access

Ukázková databáze Northwind pro Microsoft Access není k dispozici na webu Microsoft Download Center. Chcete-li nainstalovat Northwind přímo z aplikace Access, proveďte následující akce:

1. Otevřete přístup.

1. Do pole **Hledat online šablony** zadejte **Northwind** a pak vyberte **zadat**.

1. Na obrazovce výsledky vyberte **Northwind**. Otevře se nové okno s popisem databáze Northwind.

1. V novém okně v textovém poli **název souboru** zadejte název souboru pro vaši kopii databáze Northwind.

1. Vyberte **Vytvořit**. Přístup stáhne databázi Northwind a soubor připraví.

1. Po dokončení tohoto procesu se databáze otevře s úvodní obrazovkou.

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a>Získat ukázkovou databázi AdventureWorks pro SQL Server

Stáhněte si ukázkovou databázi AdventureWorks pro SQL Server z následujícího úložiště GitHub:

[Ukázkové databáze AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

Po stažení jednoho ze souborů zálohy databáze (\*. bak) obnovte zálohu na instanci SQL Server pomocí SQL Server Management Studio (SSMS). Viz [získat SQL Server Management Studio](#get_ssms).

## <a name="get_ssms"></a>Získat SQL Server Management Studio
Pokud chcete zobrazit nebo upravit databázi, kterou jste stáhli, můžete použít SQL Server Management Studio (SSMS). Stáhněte si SSMS z následující stránky:

[Stáhnout SQL Server Management Studio (SSMS)](/sql/ssms/download-sql-server-management-studio-ssms) 

Databáze můžete zobrazit a spravovat také v integrovaném vývojovém prostředí (IDE) sady Visual Studio. V [aplikaci Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)se připojte k databázi z **Průzkumník objektů systému SQL Server**nebo vytvořte datové připojení k databázi v **Průzkumník serveru**. Otevřete tyto podokna Průzkumníka z nabídky **zobrazení** .

## <a name="get_sql"></a>Získat SQL Server Express

SQL Server Express je bezplatná edice SQL Server na úrovni vstupu, kterou můžete distribuovat s aplikacemi. Stažení SQL Server Express z následující stránky:
  
[SQL Server Express Edition](https://www.microsoft.com/sql-server/sql-server-editions-express)

Pokud používáte sadu [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB je součástí bezplatné edice Community sady Visual Studio a také v edicích Professional a vyšší.  

## <a name="see-also"></a>Viz také:

- [Začínáme](getting-started.md)
