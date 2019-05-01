---
title: Získat ukázky kódu ADO.NET ukázkové databáze systému SQL Server
description: Stažení ukázkových databází SQL serveru použité v ukázkách kódu v dokumentaci k rozhraní ADO.NET, jakož i nástroje SQL Server a správu
ms.date: 01/11/2019
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 5580f06f3d28ed6d70f75b619498ac8de7bc3326
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62037931"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a><span data-ttu-id="75c7c-103">Získání ukázkových databází pro ukázky kódu ADO.NET</span><span class="sxs-lookup"><span data-stu-id="75c7c-103">Get the sample databases for ADO.NET code samples</span></span>

<span data-ttu-id="75c7c-104">Počet příklady a názorné postupy v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dokumentace ke službě pomocí ukázkových databází systému SQL Server a SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="75c7c-104">A number of examples and walkthroughs in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation use sample SQL Server databases and SQL Server Express.</span></span> <span data-ttu-id="75c7c-105">Tyto produkty zdarma si můžete stáhnout z Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="75c7c-105">You can download these products free of charge from Microsoft.</span></span>

## <a name="get-the-northwind-sample-database-for-sql-server"></a><span data-ttu-id="75c7c-106">Získat ukázkové databáze Northwind pro SQL Server</span><span class="sxs-lookup"><span data-stu-id="75c7c-106">Get the Northwind sample database for SQL Server</span></span>

<span data-ttu-id="75c7c-107">Stáhněte si skript `instnwnd.sql` z následující úložiště GitHub k vytváření a načítání ukázkové databáze Northwind pro SQL Server:</span><span class="sxs-lookup"><span data-stu-id="75c7c-107">Download the script `instnwnd.sql` from the following GitHub repository to create and load the Northwind sample database for SQL Server:</span></span>

[<span data-ttu-id="75c7c-108">Ukázkové databáze Northwind a pubs pro Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="75c7c-108">Northwind and pubs sample databases for Microsoft SQL Server</span></span>](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

<span data-ttu-id="75c7c-109">Než použijete databázi Northwind, musíte spustit na stažený `instnwnd.sql` soubor skriptu znovu vytvořit databázi na instanci systému SQL Server s použitím [SQL Server Management Studio](#get_ssms) nebo něco podobného.</span><span class="sxs-lookup"><span data-stu-id="75c7c-109">Before you can use the Northwind database, you have to run the downloaded `instnwnd.sql` script file to recreate the database on an instance of SQL Server by using [SQL Server Management Studio](#get_ssms) or a similar tool.</span></span> <span data-ttu-id="75c7c-110">Postupujte podle pokynů v souboru Readme v úložišti.</span><span class="sxs-lookup"><span data-stu-id="75c7c-110">Follow the instructions in the Readme file in the repository.</span></span>

> [!TIP]
> <span data-ttu-id="75c7c-111">Pokud hledáte databázi Northwind pro aplikaci Microsoft Access, přečtěte si téma [instalace ukázkové databáze Northwind pro aplikaci Microsoft Access](#northwind_access).</span><span class="sxs-lookup"><span data-stu-id="75c7c-111">If you're looking for the Northwind database for Microsoft Access, see [Install the Northwind sample database for Microsoft Access](#northwind_access).</span></span>

## <a name="northwind_access"></a> <span data-ttu-id="75c7c-112">Získat ukázkové databáze Northwind pro aplikaci Microsoft Access</span><span class="sxs-lookup"><span data-stu-id="75c7c-112">Get the Northwind sample database for Microsoft Access</span></span>

<span data-ttu-id="75c7c-113">Ukázkové databázi Northwind pro aplikaci Microsoft Access není k dispozici na webu Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="75c7c-113">The Northwind sample database for Microsoft Access is not available on the Microsoft Download Center.</span></span> <span data-ttu-id="75c7c-114">Pokud chcete nainstalovat Northwind přímo z aplikace Access, proveďte následující akce:</span><span class="sxs-lookup"><span data-stu-id="75c7c-114">To install Northwind directly from within Access, do the following things:</span></span>

1. <span data-ttu-id="75c7c-115">Otevřete Access.</span><span class="sxs-lookup"><span data-stu-id="75c7c-115">Open Access.</span></span>

1. <span data-ttu-id="75c7c-116">Zadejte **Northwind** v **hledat Online šablony** a potom vyberte **Enter**.</span><span class="sxs-lookup"><span data-stu-id="75c7c-116">Enter **Northwind** in the **Search for Online Templates** box, and then select **Enter**.</span></span>

1. <span data-ttu-id="75c7c-117">V okně výsledků vyberte **Northwind**.</span><span class="sxs-lookup"><span data-stu-id="75c7c-117">On the results screen, select **Northwind**.</span></span> <span data-ttu-id="75c7c-118">Otevře se nové okno s popisem databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="75c7c-118">A new window opens with a description of the Northwind database.</span></span>

1. <span data-ttu-id="75c7c-119">V novém okně v **název_souboru** textové pole, zadejte název souboru pro kopii databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="75c7c-119">In the new window, in the **File Name** text box, provide a filename for your copy of the Northwind database.</span></span>

1. <span data-ttu-id="75c7c-120">Vyberte **Vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="75c7c-120">Select **Create**.</span></span> <span data-ttu-id="75c7c-121">Přístup k databázi Northwind stáhne a připraví soubor.</span><span class="sxs-lookup"><span data-stu-id="75c7c-121">Access downloads the Northwind database and prepares the file.</span></span>

1. <span data-ttu-id="75c7c-122">Po dokončení tohoto procesu se otevře databáze úvodní obrazovka.</span><span class="sxs-lookup"><span data-stu-id="75c7c-122">When this process is complete, the database opens with a Welcome screen.</span></span>

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a><span data-ttu-id="75c7c-123">Získat ukázkovou databází AdventureWorks pro SQL Server</span><span class="sxs-lookup"><span data-stu-id="75c7c-123">Get the AdventureWorks sample database for SQL Server</span></span>

<span data-ttu-id="75c7c-124">Stáhněte si ukázkovou databází AdventureWorks pro SQL Server z následující úložiště GitHub:</span><span class="sxs-lookup"><span data-stu-id="75c7c-124">Download the AdventureWorks sample database for SQL Server from the following GitHub repository:</span></span>

[<span data-ttu-id="75c7c-125">Ukázkových databází AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="75c7c-125">AdventureWorks sample databases</span></span>](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

<span data-ttu-id="75c7c-126">Po stažení zálohy databáze (\*.bak) souborech, obnovení zálohy do instance systému SQL Server pomocí SQL Server Management Studio (SSMS).</span><span class="sxs-lookup"><span data-stu-id="75c7c-126">After you download one of the database backup (\*.bak) files, restore the backup to an instance of SQL Server by using SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="75c7c-127">Zobrazit [získat SQL Server Management Studio](#get_ssms).</span><span class="sxs-lookup"><span data-stu-id="75c7c-127">See [Get SQL Server Management Studio](#get_ssms).</span></span>

## <a name="get_ssms"></a> <span data-ttu-id="75c7c-128">Získat SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="75c7c-128">Get SQL Server Management Studio</span></span>
<span data-ttu-id="75c7c-129">Pokud chcete zobrazit nebo upravit databázi, kterou jste stáhli, můžete použít SQL Server Management Studio (SSMS).</span><span class="sxs-lookup"><span data-stu-id="75c7c-129">If you want to view or modify a database that you've downloaded, you can use SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="75c7c-130">SSMS stáhněte z následující stránky:</span><span class="sxs-lookup"><span data-stu-id="75c7c-130">Download SSMS from the following page:</span></span>

[<span data-ttu-id="75c7c-131">Stáhněte si SQL Server Management Studio (SSMS)</span><span class="sxs-lookup"><span data-stu-id="75c7c-131">Download SQL Server Management Studio (SSMS)</span></span>](/sql/ssms/download-sql-server-management-studio-ssms) 

<span data-ttu-id="75c7c-132">Můžete také zobrazit a spravovat databáze v prostředí integrovaného vývojového (prostředí IDE) sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="75c7c-132">You can also view and manage databases in the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="75c7c-133">V [sady Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), připojte se k databázi z **Průzkumník objektů systému SQL Server**, nebo vytvoření datového připojení k databázi v **Průzkumníka serveru**.</span><span class="sxs-lookup"><span data-stu-id="75c7c-133">In [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), connect to the database from **SQL Server Object Explorer**, or create a Data Connection to the database in **Server Explorer**.</span></span> <span data-ttu-id="75c7c-134">Otevření těchto podoken explorer z **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="75c7c-134">Open these explorer panes from the **View** menu.</span></span>

## <a name="get_sql"></a> <span data-ttu-id="75c7c-135">Get SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="75c7c-135">Get SQL Server Express</span></span>

<span data-ttu-id="75c7c-136">SQL Server Express je zdarma, základní edice systému SQL Server, který je možné znovu distribuovat s aplikací.</span><span class="sxs-lookup"><span data-stu-id="75c7c-136">SQL Server Express is a free, entry-level edition of SQL Server that you can redistribute with applications.</span></span> <span data-ttu-id="75c7c-137">Stáhněte SQL Server Express z následující stránky:</span><span class="sxs-lookup"><span data-stu-id="75c7c-137">Download SQL Server Express from the following page:</span></span>
  
[<span data-ttu-id="75c7c-138">SQL Server Express Edition</span><span class="sxs-lookup"><span data-stu-id="75c7c-138">SQL Server Express Edition</span></span>](https://www.microsoft.com/sql-server/sql-server-editions-express)

<span data-ttu-id="75c7c-139">Pokud používáte [sady Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB je součástí sady Visual Studio bezplatná edice Community, jakož i edice Professional a vyšší.</span><span class="sxs-lookup"><span data-stu-id="75c7c-139">If you're using [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB is included in the free Community edition of Visual Studio, as well as the Professional and higher editions.</span></span>  

## <a name="see-also"></a><span data-ttu-id="75c7c-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="75c7c-140">See also</span></span>

- [<span data-ttu-id="75c7c-141">Začínáme</span><span class="sxs-lookup"><span data-stu-id="75c7c-141">Getting Started</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
