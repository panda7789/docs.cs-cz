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
# <a name="get-the-sample-databases-for-adonet-code-samples"></a><span data-ttu-id="1d842-103">Získat ukázkové databáze pro ukázky kódu ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1d842-103">Get the sample databases for ADO.NET code samples</span></span>

<span data-ttu-id="1d842-104">Několik příkladů a návodů v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dokumentaci použít ukázkové databáze serveru SQL Server a SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="1d842-104">A number of examples and walkthroughs in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation use sample SQL Server databases and SQL Server Express.</span></span> <span data-ttu-id="1d842-105">Tyto produkty si můžete stáhnout zdarma od společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1d842-105">You can download these products free of charge from Microsoft.</span></span>

## <a name="get-the-northwind-sample-database-for-sql-server"></a><span data-ttu-id="1d842-106">Získání ukázkové databáze Northwind pro SQL Server</span><span class="sxs-lookup"><span data-stu-id="1d842-106">Get the Northwind sample database for SQL Server</span></span>

<span data-ttu-id="1d842-107">Stáhněte `instnwnd.sql` si skript z následujícího úložiště GitHub a vytvořte a načtěte ukázkovou databázi Northwind pro SQL Server:</span><span class="sxs-lookup"><span data-stu-id="1d842-107">Download the script `instnwnd.sql` from the following GitHub repository to create and load the Northwind sample database for SQL Server:</span></span>

[<span data-ttu-id="1d842-108">Ukázkové databáze Northwind a pubs pro Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="1d842-108">Northwind and pubs sample databases for Microsoft SQL Server</span></span>](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

<span data-ttu-id="1d842-109">Před použitím databáze Northwind je třeba spustit stažený `instnwnd.sql` soubor skriptu k opětovnému vytvoření databáze na instanci serveru SQL Server pomocí sql server management [studio](#get_ssms) nebo podobný nástroj.</span><span class="sxs-lookup"><span data-stu-id="1d842-109">Before you can use the Northwind database, you have to run the downloaded `instnwnd.sql` script file to recreate the database on an instance of SQL Server by using [SQL Server Management Studio](#get_ssms) or a similar tool.</span></span> <span data-ttu-id="1d842-110">Postupujte podle pokynů v souboru Readme v úložišti.</span><span class="sxs-lookup"><span data-stu-id="1d842-110">Follow the instructions in the Readme file in the repository.</span></span>

> [!TIP]
> <span data-ttu-id="1d842-111">Pokud hledáte databázi Northwind pro aplikaci Microsoft Access, přečtěte si informace [o instalaci ukázkové databáze Northwind pro aplikaci Microsoft Access](#northwind_access).</span><span class="sxs-lookup"><span data-stu-id="1d842-111">If you're looking for the Northwind database for Microsoft Access, see [Install the Northwind sample database for Microsoft Access](#northwind_access).</span></span>

## <a name="get-the-northwind-sample-database-for-microsoft-access"></a><a name="northwind_access"></a><span data-ttu-id="1d842-112">Získání ukázkové databáze Northwind pro aplikaci Microsoft Access</span><span class="sxs-lookup"><span data-stu-id="1d842-112">Get the Northwind sample database for Microsoft Access</span></span>

<span data-ttu-id="1d842-113">Ukázková databáze Northwind pro aplikaci Microsoft Access není k dispozici v centru pro stahování Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="1d842-113">The Northwind sample database for Microsoft Access is not available on the Microsoft Download Center.</span></span> <span data-ttu-id="1d842-114">Chcete-li aplikaci Northwind nainstalovat přímo z aplikace Access, proveďte následující akce:</span><span class="sxs-lookup"><span data-stu-id="1d842-114">To install Northwind directly from within Access, do the following things:</span></span>

1. <span data-ttu-id="1d842-115">Otevřít přístup.</span><span class="sxs-lookup"><span data-stu-id="1d842-115">Open Access.</span></span>

1. <span data-ttu-id="1d842-116">Do pole **Hledat online šablony** zadejte **Northwind** a pak vyberte **Enter**.</span><span class="sxs-lookup"><span data-stu-id="1d842-116">Enter **Northwind** in the **Search for Online Templates** box, and then select **Enter**.</span></span>

1. <span data-ttu-id="1d842-117">Na obrazovce s výsledky vyberte **možnost Northwind**.</span><span class="sxs-lookup"><span data-stu-id="1d842-117">On the results screen, select **Northwind**.</span></span> <span data-ttu-id="1d842-118">Otevře se nové okno s popisem databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="1d842-118">A new window opens with a description of the Northwind database.</span></span>

1. <span data-ttu-id="1d842-119">V novém okně zadejte v textovém poli **Název souboru** název souboru pro kopii databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="1d842-119">In the new window, in the **File Name** text box, provide a filename for your copy of the Northwind database.</span></span>

1. <span data-ttu-id="1d842-120">Vyberte **Vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="1d842-120">Select **Create**.</span></span> <span data-ttu-id="1d842-121">Aplikace Access stáhne databázi Northwind a připraví soubor.</span><span class="sxs-lookup"><span data-stu-id="1d842-121">Access downloads the Northwind database and prepares the file.</span></span>

1. <span data-ttu-id="1d842-122">Po dokončení tohoto procesu se databáze otevře s úvodní obrazovkou.</span><span class="sxs-lookup"><span data-stu-id="1d842-122">When this process is complete, the database opens with a Welcome screen.</span></span>

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a><span data-ttu-id="1d842-123">Získání ukázkové databáze AdventureWorks pro SQL Server</span><span class="sxs-lookup"><span data-stu-id="1d842-123">Get the AdventureWorks sample database for SQL Server</span></span>

<span data-ttu-id="1d842-124">Stáhněte si ukázkovou databázi AdventureWorks pro SQL Server z následujícího úložiště GitHub:</span><span class="sxs-lookup"><span data-stu-id="1d842-124">Download the AdventureWorks sample database for SQL Server from the following GitHub repository:</span></span>

[<span data-ttu-id="1d842-125">Ukázkové databáze AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="1d842-125">AdventureWorks sample databases</span></span>](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

<span data-ttu-id="1d842-126">Po stažení jednoho ze souborů\*zálohy databáze ( .bak) obnovit zálohu do instance SQL Server pomocí SQL Server Management Studio (SSMS).</span><span class="sxs-lookup"><span data-stu-id="1d842-126">After you download one of the database backup (\*.bak) files, restore the backup to an instance of SQL Server by using SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="1d842-127">Viz [Získání sql server management studio](#get_ssms).</span><span class="sxs-lookup"><span data-stu-id="1d842-127">See [Get SQL Server Management Studio](#get_ssms).</span></span>

## <a name="get-sql-server-management-studio"></a><a name="get_ssms"></a><span data-ttu-id="1d842-128">Získat aplikaci SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1d842-128">Get SQL Server Management Studio</span></span>
<span data-ttu-id="1d842-129">Pokud chcete zobrazit nebo upravit databázi, kterou jste stáhli, můžete použít SQL Server Management Studio (SSMS).</span><span class="sxs-lookup"><span data-stu-id="1d842-129">If you want to view or modify a database that you've downloaded, you can use SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="1d842-130">Stáhněte si SSMS z následující stránky:</span><span class="sxs-lookup"><span data-stu-id="1d842-130">Download SSMS from the following page:</span></span>

[<span data-ttu-id="1d842-131">Stažení SQL Server Management Studia (SSMS)</span><span class="sxs-lookup"><span data-stu-id="1d842-131">Download SQL Server Management Studio (SSMS)</span></span>](/sql/ssms/download-sql-server-management-studio-ssms)

<span data-ttu-id="1d842-132">Můžete také zobrazit a spravovat databáze v integrovaném vývojovém prostředí sady Visual Studio (IDE).</span><span class="sxs-lookup"><span data-stu-id="1d842-132">You can also view and manage databases in the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="1d842-133">V [sadě Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)se připojte k databázi z **průzkumníka objektů serveru SQL Server**nebo vytvořte datové připojení k databázi v **Průzkumníkovi serveru**.</span><span class="sxs-lookup"><span data-stu-id="1d842-133">In [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019), connect to the database from **SQL Server Object Explorer**, or create a Data Connection to the database in **Server Explorer**.</span></span> <span data-ttu-id="1d842-134">Otevřete tato podokna průzkumníků z nabídky **Zobrazení.**</span><span class="sxs-lookup"><span data-stu-id="1d842-134">Open these explorer panes from the **View** menu.</span></span>

## <a name="get-sql-server-express"></a><a name="get_sql"></a><span data-ttu-id="1d842-135">Získat SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="1d842-135">Get SQL Server Express</span></span>

<span data-ttu-id="1d842-136">SQL Server Express je bezplatná edice sql serveru základní úrovně, kterou můžete dále distribuovat s aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="1d842-136">SQL Server Express is a free, entry-level edition of SQL Server that you can redistribute with applications.</span></span> <span data-ttu-id="1d842-137">Stáhněte sql server express z následující stránky:</span><span class="sxs-lookup"><span data-stu-id="1d842-137">Download SQL Server Express from the following page:</span></span>
  
[<span data-ttu-id="1d842-138">Edice SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="1d842-138">SQL Server Express Edition</span></span>](https://www.microsoft.com/sql-server/sql-server-editions-express)

<span data-ttu-id="1d842-139">Pokud používáte [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019), SQL Server Express LocalDB je součástí bezplatné verze Společenství sady Visual Studio, stejně jako professional a vyšší edice.</span><span class="sxs-lookup"><span data-stu-id="1d842-139">If you're using [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019), SQL Server Express LocalDB is included in the free Community edition of Visual Studio, as well as the Professional and higher editions.</span></span>  

## <a name="see-also"></a><span data-ttu-id="1d842-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="1d842-140">See also</span></span>

- [<span data-ttu-id="1d842-141">Začínáme</span><span class="sxs-lookup"><span data-stu-id="1d842-141">Getting Started</span></span>](getting-started.md)
