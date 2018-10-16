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
# <a name="get-the-sample-databases-for-adonet-code-samples"></a><span data-ttu-id="c3545-103">Získání ukázkových databází pro ukázky kódu ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c3545-103">Get the sample databases for ADO.NET code samples</span></span>

<span data-ttu-id="c3545-104">Počet ukázky a návody v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dokumentaci použít ukázkové databáze a serveru SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="c3545-104">A number of samples and walkthroughs in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation use sample databases and SQL Server Express.</span></span> <span data-ttu-id="c3545-105">Tyto produkty zdarma si můžete stáhnout z Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="c3545-105">You can download these products free of charge from Microsoft.</span></span>

## <a name="get-the-adventureworks-sample-database"></a><span data-ttu-id="c3545-106">Získat ukázkovou databází AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="c3545-106">Get the AdventureWorks sample database</span></span>

<span data-ttu-id="c3545-107">Stáhněte si ukázkovou databází AdventureWorks z následující úložiště GitHub:</span><span class="sxs-lookup"><span data-stu-id="c3545-107">Download the AdventureWorks sample database from the following GitHub repository:</span></span>

[<span data-ttu-id="c3545-108">Ukázkových databází AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="c3545-108">AdventureWorks sample databases</span></span>](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

<span data-ttu-id="c3545-109">Po stažení zálohy databáze (\*.bak) souborech, obnovení zálohy do instance systému SQL Server pomocí SQL Server Management Studio (SSMS).</span><span class="sxs-lookup"><span data-stu-id="c3545-109">After you download one of the database backup (\*.bak) files, restore the backup to an instance of SQL Server by using SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="c3545-110">Zobrazit [získat SQL Server Management Studio](#get_ssms).</span><span class="sxs-lookup"><span data-stu-id="c3545-110">See [Get SQL Server Management Studio](#get_ssms).</span></span>

## <a name="get-the-northwind-sample-database"></a><span data-ttu-id="c3545-111">Získat ukázkovou databázi Northwind</span><span class="sxs-lookup"><span data-stu-id="c3545-111">Get the Northwind sample database</span></span>

<span data-ttu-id="c3545-112">Stažení ukázkové databáze Northwind na následující stránce na webu Microsoft Download Center:</span><span class="sxs-lookup"><span data-stu-id="c3545-112">Download the Northwind sample database from the following page in the Microsoft Download Center:</span></span>

[<span data-ttu-id="c3545-113">Ukázkové databáze Pubs a Northwind</span><span class="sxs-lookup"><span data-stu-id="c3545-113">Northwind and Pubs Sample Databases</span></span>](https://go.microsoft.com/fwlink?linkid=64296)

<span data-ttu-id="c3545-114">Po stažení souboru poklikejte na soubor k extrahování databází a skripty.</span><span class="sxs-lookup"><span data-stu-id="c3545-114">After the file has downloaded, double-click the file to extract the databases and scripts.</span></span> <span data-ttu-id="c3545-115">Ve výchozím nastavení jsou soubory nainstalovaného ve složce `<drive>:\SQL Server 2000 Sample Databases`.</span><span class="sxs-lookup"><span data-stu-id="c3545-115">By default, the files are installed in the folder `<drive>:\SQL Server 2000 Sample Databases`.</span></span>

<span data-ttu-id="c3545-116">Před použitím databáze Northwind, musíte udělat jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="c3545-116">Before you can use the Northwind database, you have to do one of the following things:</span></span>

- <span data-ttu-id="c3545-117">Znovu vytvořit databázi na instanci systému SQL Server spuštěním `instnwnd.sql` soubor skriptu v instalační složce Nástroje.</span><span class="sxs-lookup"><span data-stu-id="c3545-117">Recreate the database on an instance of SQL Server by running the `instnwnd.sql` script file in the installation folder.</span></span>

- <span data-ttu-id="c3545-118">Připojit `northwnd.mdf` soubor k odpovídajícímu `*.ldf` souboru protokolu určeného k instanci systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c3545-118">Attach the `northwnd.mdf` file with its corresponding `*.ldf` log file to an instance of SQL Server.</span></span>

## <a name="get_sql"></a> <span data-ttu-id="c3545-119">Získat SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="c3545-119">Get SQL Server Express</span></span>

<span data-ttu-id="c3545-120">SQL Server Express je zdarma, základní edice systému SQL Server, který je možné znovu distribuovat s aplikací.</span><span class="sxs-lookup"><span data-stu-id="c3545-120">SQL Server Express is a free, entry-level edition of SQL Server that you can redistribute with applications.</span></span> <span data-ttu-id="c3545-121">Stáhněte SQL Server Express z následující stránky:</span><span class="sxs-lookup"><span data-stu-id="c3545-121">Download SQL Server Express from the following page:</span></span>
  
[<span data-ttu-id="c3545-122">Edice SQL serveru Express</span><span class="sxs-lookup"><span data-stu-id="c3545-122">SQL Server Express Editions</span></span>](https://www.microsoft.com/sql-server/sql-server-editions-express)

<span data-ttu-id="c3545-123">Pokud používáte [sady Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB je součástí Community edition, stejně jako edice Professional a vyšší.</span><span class="sxs-lookup"><span data-stu-id="c3545-123">If you're using [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB is included in the Community edition as well as the Professional and higher editions.</span></span>  

## <a name="get_ssms"></a> <span data-ttu-id="c3545-124">Získat SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c3545-124">Get SQL Server Management Studio</span></span>
<span data-ttu-id="c3545-125">Pokud chcete zobrazit nebo upravit databázi, kterou jste stáhli, můžete použít SQL Server Management Studio (SSMS).</span><span class="sxs-lookup"><span data-stu-id="c3545-125">If you want to view or modify a database that you've downloaded, you can use SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="c3545-126">SSMS stáhněte z následující stránky:</span><span class="sxs-lookup"><span data-stu-id="c3545-126">Download SSMS from the following page:</span></span>

[<span data-ttu-id="c3545-127">Stáhněte si SQL Server Management Studio (SSMS)</span><span class="sxs-lookup"><span data-stu-id="c3545-127">Download SQL Server Management Studio (SSMS)</span></span>](/sql/ssms/download-sql-server-management-studio-ssms) 

<span data-ttu-id="c3545-128">Můžete také zobrazit a spravovat databáze v prostředí integrovaného vývojového (prostředí IDE) sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c3545-128">You can also view and manage databases in the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="c3545-129">V [sady Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), připojte se k databázi z **Průzkumník objektů systému SQL Server**, nebo vytvoření datového připojení k databázi v **Průzkumníka serveru**.</span><span class="sxs-lookup"><span data-stu-id="c3545-129">In [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), connect to the database from **SQL Server Object Explorer**, or create a Data Connection to the database in **Server Explorer**.</span></span> <span data-ttu-id="c3545-130">Otevření těchto podoken explorer z **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="c3545-130">Open these explorer panes from the **View** menu.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c3545-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c3545-131">See also</span></span>

- [<span data-ttu-id="c3545-132">Začínáme</span><span class="sxs-lookup"><span data-stu-id="c3545-132">Getting Started</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
