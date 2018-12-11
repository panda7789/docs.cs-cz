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
# <a name="get-the-sample-databases-for-adonet-code-samples"></a><span data-ttu-id="f836e-103">Získání ukázkových databází pro ukázky kódu ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f836e-103">Get the sample databases for ADO.NET code samples</span></span>

<span data-ttu-id="f836e-104">Počet příklady a názorné postupy v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dokumentace ke službě pomocí ukázkových databází systému SQL Server a SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="f836e-104">A number of examples and walkthroughs in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation use sample SQL Server databases and SQL Server Express.</span></span> <span data-ttu-id="f836e-105">Tyto produkty zdarma si můžete stáhnout z Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="f836e-105">You can download these products free of charge from Microsoft.</span></span>

## <a name="get-the-northwind-sample-database-for-sql-server"></a><span data-ttu-id="f836e-106">Získat ukázkové databáze Northwind pro SQL Server</span><span class="sxs-lookup"><span data-stu-id="f836e-106">Get the Northwind sample database for SQL Server</span></span>

<span data-ttu-id="f836e-107">Stáhněte si skript `instnwnd.sql` z následující úložiště GitHub k vytváření a načítání ukázkové databáze Northwind pro SQL Server:</span><span class="sxs-lookup"><span data-stu-id="f836e-107">Download the script `instnwnd.sql` from the following GitHub repository to create and load the Northwind sample database for SQL Server:</span></span>

[<span data-ttu-id="f836e-108">Ukázkové databáze Northwind a pubs pro Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="f836e-108">Northwind and pubs sample databases for Microsoft SQL Server</span></span>](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

<span data-ttu-id="f836e-109">Než použijete databázi Northwind, musíte spustit na stažený `instnwnd.sql` soubor skriptu znovu vytvořit databázi na instanci systému SQL Server s použitím [SQL Server Management Studio](#get_ssms) nebo něco podobného.</span><span class="sxs-lookup"><span data-stu-id="f836e-109">Before you can use the Northwind database, you have to run the downloaded `instnwnd.sql` script file to recreate the database on an instance of SQL Server by using [SQL Server Management Studio](#get_ssms) or a similar tool.</span></span> <span data-ttu-id="f836e-110">Postupujte podle pokynů v souboru Readme v úložišti.</span><span class="sxs-lookup"><span data-stu-id="f836e-110">Follow the instructions in the Readme file in the repository.</span></span>

> [!TIP]
> <span data-ttu-id="f836e-111">Pokud hledáte databázi Northwind pro aplikaci Microsoft Access, přečtěte si téma [instalace ukázkové databáze Northwind pro aplikaci Microsoft Access](#northwind_access).</span><span class="sxs-lookup"><span data-stu-id="f836e-111">If you're looking for the Northwind database for Microsoft Access, see [Install the Northwind sample database for Microsoft Access](#northwind_access).</span></span>

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a><span data-ttu-id="f836e-112">Získat ukázkovou databází AdventureWorks pro SQL Server</span><span class="sxs-lookup"><span data-stu-id="f836e-112">Get the AdventureWorks sample database for SQL Server</span></span>

<span data-ttu-id="f836e-113">Stáhněte si ukázkovou databází AdventureWorks pro SQL Server z následující úložiště GitHub:</span><span class="sxs-lookup"><span data-stu-id="f836e-113">Download the AdventureWorks sample database for SQL Server from the following GitHub repository:</span></span>

[<span data-ttu-id="f836e-114">Ukázkových databází AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="f836e-114">AdventureWorks sample databases</span></span>](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

<span data-ttu-id="f836e-115">Po stažení zálohy databáze (\*.bak) souborech, obnovení zálohy do instance systému SQL Server pomocí SQL Server Management Studio (SSMS).</span><span class="sxs-lookup"><span data-stu-id="f836e-115">After you download one of the database backup (\*.bak) files, restore the backup to an instance of SQL Server by using SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="f836e-116">Zobrazit [získat SQL Server Management Studio](#get_ssms).</span><span class="sxs-lookup"><span data-stu-id="f836e-116">See [Get SQL Server Management Studio](#get_ssms).</span></span>

## <a name="get_sql"></a> <span data-ttu-id="f836e-117">Získat SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="f836e-117">Get SQL Server Express</span></span>

<span data-ttu-id="f836e-118">SQL Server Express je zdarma, základní edice systému SQL Server, který je možné znovu distribuovat s aplikací.</span><span class="sxs-lookup"><span data-stu-id="f836e-118">SQL Server Express is a free, entry-level edition of SQL Server that you can redistribute with applications.</span></span> <span data-ttu-id="f836e-119">Stáhněte SQL Server Express z následující stránky:</span><span class="sxs-lookup"><span data-stu-id="f836e-119">Download SQL Server Express from the following page:</span></span>
  
[<span data-ttu-id="f836e-120">SQL Server Express Edition</span><span class="sxs-lookup"><span data-stu-id="f836e-120">SQL Server Express Edition</span></span>](https://www.microsoft.com/sql-server/sql-server-editions-express)

<span data-ttu-id="f836e-121">Pokud používáte [sady Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB je součástí sady Visual Studio bezplatná edice Community, jakož i edice Professional a vyšší.</span><span class="sxs-lookup"><span data-stu-id="f836e-121">If you're using [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB is included in the free Community edition of Visual Studio, as well as the Professional and higher editions.</span></span>  

## <a name="get_ssms"></a> <span data-ttu-id="f836e-122">Získat SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f836e-122">Get SQL Server Management Studio</span></span>
<span data-ttu-id="f836e-123">Pokud chcete zobrazit nebo upravit databázi, kterou jste stáhli, můžete použít SQL Server Management Studio (SSMS).</span><span class="sxs-lookup"><span data-stu-id="f836e-123">If you want to view or modify a database that you've downloaded, you can use SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="f836e-124">SSMS stáhněte z následující stránky:</span><span class="sxs-lookup"><span data-stu-id="f836e-124">Download SSMS from the following page:</span></span>

[<span data-ttu-id="f836e-125">Stáhněte si SQL Server Management Studio (SSMS)</span><span class="sxs-lookup"><span data-stu-id="f836e-125">Download SQL Server Management Studio (SSMS)</span></span>](/sql/ssms/download-sql-server-management-studio-ssms) 

<span data-ttu-id="f836e-126">Můžete také zobrazit a spravovat databáze v prostředí integrovaného vývojového (prostředí IDE) sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f836e-126">You can also view and manage databases in the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="f836e-127">V [sady Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), připojte se k databázi z **Průzkumník objektů systému SQL Server**, nebo vytvoření datového připojení k databázi v **Průzkumníka serveru**.</span><span class="sxs-lookup"><span data-stu-id="f836e-127">In [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), connect to the database from **SQL Server Object Explorer**, or create a Data Connection to the database in **Server Explorer**.</span></span> <span data-ttu-id="f836e-128">Otevření těchto podoken explorer z **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="f836e-128">Open these explorer panes from the **View** menu.</span></span>

## <a name="northwind_access"></a> <span data-ttu-id="f836e-129">Instalace ukázkové databáze Northwind pro aplikaci Microsoft Access</span><span class="sxs-lookup"><span data-stu-id="f836e-129">Install the Northwind sample database for Microsoft Access</span></span>

<span data-ttu-id="f836e-130">Ukázkové databázi Northwind pro aplikaci Microsoft Access není k dispozici na webu Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="f836e-130">The Northwind sample database for Microsoft Access is not available on the Microsoft Download Center.</span></span> <span data-ttu-id="f836e-131">Pokud chcete nainstalovat Northwind přímo z aplikace Access, proveďte následující akce:</span><span class="sxs-lookup"><span data-stu-id="f836e-131">To install Northwind directly from within Access, do the following things:</span></span>

1. <span data-ttu-id="f836e-132">Otevřete Access.</span><span class="sxs-lookup"><span data-stu-id="f836e-132">Open Access.</span></span>

1. <span data-ttu-id="f836e-133">Zadejte **Northwind** v **hledat Online šablony** a potom vyberte **Enter**.</span><span class="sxs-lookup"><span data-stu-id="f836e-133">Enter **Northwind** in the **Search for Online Templates** box, and then select **Enter**.</span></span>

1. <span data-ttu-id="f836e-134">V okně výsledků vyberte **Northwind**.</span><span class="sxs-lookup"><span data-stu-id="f836e-134">On the results screen, select **Northwind**.</span></span> <span data-ttu-id="f836e-135">Otevře se nové okno s popisem databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="f836e-135">A new window opens with a description of the Northwind database.</span></span>

1. <span data-ttu-id="f836e-136">V novém okně v **název_souboru** textové pole, zadejte název souboru pro kopii databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="f836e-136">In the new window, in the **File Name** text box, provide a filename for your copy of the Northwind database.</span></span>

1. <span data-ttu-id="f836e-137">Vyberte **Vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="f836e-137">Select **Create**.</span></span> <span data-ttu-id="f836e-138">Přístup k databázi Northwind stáhne a připraví soubor.</span><span class="sxs-lookup"><span data-stu-id="f836e-138">Access downloads the Northwind database and prepares the file.</span></span>

1. <span data-ttu-id="f836e-139">Po dokončení tohoto procesu se otevře databáze úvodní obrazovka.</span><span class="sxs-lookup"><span data-stu-id="f836e-139">When this process is complete, the database opens with a Welcome screen.</span></span>

## <a name="see-also"></a><span data-ttu-id="f836e-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f836e-140">See also</span></span>

- [<span data-ttu-id="f836e-141">Začínáme</span><span class="sxs-lookup"><span data-stu-id="f836e-141">Getting Started</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
