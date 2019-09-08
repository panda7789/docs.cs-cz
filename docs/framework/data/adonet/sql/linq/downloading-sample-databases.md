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
# <a name="get-the-sample-databases-for-adonet-code-samples"></a><span data-ttu-id="aceda-103">Získání ukázkových databází pro ukázky kódu ADO.NET</span><span class="sxs-lookup"><span data-stu-id="aceda-103">Get the sample databases for ADO.NET code samples</span></span>

<span data-ttu-id="aceda-104">V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dokumentaci se používá několik příkladů a návodů, které používají ukázkové SQL Server databáze a SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="aceda-104">A number of examples and walkthroughs in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation use sample SQL Server databases and SQL Server Express.</span></span> <span data-ttu-id="aceda-105">Zdarma si můžete stáhnout tyto produkty od Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="aceda-105">You can download these products free of charge from Microsoft.</span></span>

## <a name="get-the-northwind-sample-database-for-sql-server"></a><span data-ttu-id="aceda-106">Získat ukázkovou databázi Northwind pro SQL Server</span><span class="sxs-lookup"><span data-stu-id="aceda-106">Get the Northwind sample database for SQL Server</span></span>

<span data-ttu-id="aceda-107">Stáhněte si skript `instnwnd.sql` z následujícího úložiště GitHubu, abyste vytvořili a načetli ukázkovou databázi Northwind pro SQL Server:</span><span class="sxs-lookup"><span data-stu-id="aceda-107">Download the script `instnwnd.sql` from the following GitHub repository to create and load the Northwind sample database for SQL Server:</span></span>

[<span data-ttu-id="aceda-108">Ukázkové databáze Northwind a pubs pro Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="aceda-108">Northwind and pubs sample databases for Microsoft SQL Server</span></span>](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

<span data-ttu-id="aceda-109">Předtím, než budete moci použít databázi Northwind, je nutné spustit stažený `instnwnd.sql` soubor skriptu pro opětovné vytvoření databáze na instanci SQL Server pomocí [SQL Server Management Studio](#get_ssms) nebo podobného nástroje.</span><span class="sxs-lookup"><span data-stu-id="aceda-109">Before you can use the Northwind database, you have to run the downloaded `instnwnd.sql` script file to recreate the database on an instance of SQL Server by using [SQL Server Management Studio](#get_ssms) or a similar tool.</span></span> <span data-ttu-id="aceda-110">Postupujte podle pokynů v souboru Readme v úložišti.</span><span class="sxs-lookup"><span data-stu-id="aceda-110">Follow the instructions in the Readme file in the repository.</span></span>

> [!TIP]
> <span data-ttu-id="aceda-111">Pokud hledáte databázi Northwind pro Microsoft Access, přečtěte si téma [Instalace ukázkové databáze Northwind pro Microsoft Access](#northwind_access).</span><span class="sxs-lookup"><span data-stu-id="aceda-111">If you're looking for the Northwind database for Microsoft Access, see [Install the Northwind sample database for Microsoft Access](#northwind_access).</span></span>

## <a name="northwind_access"></a><span data-ttu-id="aceda-112">Získat ukázkovou databázi Northwind pro Microsoft Access</span><span class="sxs-lookup"><span data-stu-id="aceda-112">Get the Northwind sample database for Microsoft Access</span></span>

<span data-ttu-id="aceda-113">Ukázková databáze Northwind pro Microsoft Access není k dispozici na webu Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="aceda-113">The Northwind sample database for Microsoft Access is not available on the Microsoft Download Center.</span></span> <span data-ttu-id="aceda-114">Chcete-li nainstalovat Northwind přímo z aplikace Access, proveďte následující akce:</span><span class="sxs-lookup"><span data-stu-id="aceda-114">To install Northwind directly from within Access, do the following things:</span></span>

1. <span data-ttu-id="aceda-115">Otevřete přístup.</span><span class="sxs-lookup"><span data-stu-id="aceda-115">Open Access.</span></span>

1. <span data-ttu-id="aceda-116">Do pole **Hledat online šablony** zadejte **Northwind** a pak vyberte **zadat**.</span><span class="sxs-lookup"><span data-stu-id="aceda-116">Enter **Northwind** in the **Search for Online Templates** box, and then select **Enter**.</span></span>

1. <span data-ttu-id="aceda-117">Na obrazovce výsledky vyberte **Northwind**.</span><span class="sxs-lookup"><span data-stu-id="aceda-117">On the results screen, select **Northwind**.</span></span> <span data-ttu-id="aceda-118">Otevře se nové okno s popisem databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="aceda-118">A new window opens with a description of the Northwind database.</span></span>

1. <span data-ttu-id="aceda-119">V novém okně v textovém poli **název souboru** zadejte název souboru pro vaši kopii databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="aceda-119">In the new window, in the **File Name** text box, provide a filename for your copy of the Northwind database.</span></span>

1. <span data-ttu-id="aceda-120">Vyberte **Vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="aceda-120">Select **Create**.</span></span> <span data-ttu-id="aceda-121">Přístup stáhne databázi Northwind a soubor připraví.</span><span class="sxs-lookup"><span data-stu-id="aceda-121">Access downloads the Northwind database and prepares the file.</span></span>

1. <span data-ttu-id="aceda-122">Po dokončení tohoto procesu se databáze otevře s úvodní obrazovkou.</span><span class="sxs-lookup"><span data-stu-id="aceda-122">When this process is complete, the database opens with a Welcome screen.</span></span>

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a><span data-ttu-id="aceda-123">Získat ukázkovou databázi AdventureWorks pro SQL Server</span><span class="sxs-lookup"><span data-stu-id="aceda-123">Get the AdventureWorks sample database for SQL Server</span></span>

<span data-ttu-id="aceda-124">Stáhněte si ukázkovou databázi AdventureWorks pro SQL Server z následujícího úložiště GitHub:</span><span class="sxs-lookup"><span data-stu-id="aceda-124">Download the AdventureWorks sample database for SQL Server from the following GitHub repository:</span></span>

[<span data-ttu-id="aceda-125">Ukázkové databáze AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="aceda-125">AdventureWorks sample databases</span></span>](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

<span data-ttu-id="aceda-126">Po stažení jednoho ze souborů zálohy databáze (\*. bak) obnovte zálohu na instanci SQL Server pomocí SQL Server Management Studio (SSMS).</span><span class="sxs-lookup"><span data-stu-id="aceda-126">After you download one of the database backup (\*.bak) files, restore the backup to an instance of SQL Server by using SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="aceda-127">Viz [získat SQL Server Management Studio](#get_ssms).</span><span class="sxs-lookup"><span data-stu-id="aceda-127">See [Get SQL Server Management Studio](#get_ssms).</span></span>

## <a name="get_ssms"></a><span data-ttu-id="aceda-128">Získat SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="aceda-128">Get SQL Server Management Studio</span></span>
<span data-ttu-id="aceda-129">Pokud chcete zobrazit nebo upravit databázi, kterou jste stáhli, můžete použít SQL Server Management Studio (SSMS).</span><span class="sxs-lookup"><span data-stu-id="aceda-129">If you want to view or modify a database that you've downloaded, you can use SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="aceda-130">Stáhněte si SSMS z následující stránky:</span><span class="sxs-lookup"><span data-stu-id="aceda-130">Download SSMS from the following page:</span></span>

[<span data-ttu-id="aceda-131">Stáhnout SQL Server Management Studio (SSMS)</span><span class="sxs-lookup"><span data-stu-id="aceda-131">Download SQL Server Management Studio (SSMS)</span></span>](/sql/ssms/download-sql-server-management-studio-ssms) 

<span data-ttu-id="aceda-132">Databáze můžete zobrazit a spravovat také v integrovaném vývojovém prostředí (IDE) sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="aceda-132">You can also view and manage databases in the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="aceda-133">V [aplikaci Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)se připojte k databázi z **Průzkumník objektů systému SQL Server**nebo vytvořte datové připojení k databázi v **Průzkumník serveru**.</span><span class="sxs-lookup"><span data-stu-id="aceda-133">In [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), connect to the database from **SQL Server Object Explorer**, or create a Data Connection to the database in **Server Explorer**.</span></span> <span data-ttu-id="aceda-134">Otevřete tyto podokna Průzkumníka z nabídky **zobrazení** .</span><span class="sxs-lookup"><span data-stu-id="aceda-134">Open these explorer panes from the **View** menu.</span></span>

## <a name="get_sql"></a><span data-ttu-id="aceda-135">Získat SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="aceda-135">Get SQL Server Express</span></span>

<span data-ttu-id="aceda-136">SQL Server Express je bezplatná edice SQL Server na úrovni vstupu, kterou můžete distribuovat s aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="aceda-136">SQL Server Express is a free, entry-level edition of SQL Server that you can redistribute with applications.</span></span> <span data-ttu-id="aceda-137">Stažení SQL Server Express z následující stránky:</span><span class="sxs-lookup"><span data-stu-id="aceda-137">Download SQL Server Express from the following page:</span></span>
  
[<span data-ttu-id="aceda-138">SQL Server Express Edition</span><span class="sxs-lookup"><span data-stu-id="aceda-138">SQL Server Express Edition</span></span>](https://www.microsoft.com/sql-server/sql-server-editions-express)

<span data-ttu-id="aceda-139">Pokud používáte sadu [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB je součástí bezplatné edice Community sady Visual Studio a také v edicích Professional a vyšší.</span><span class="sxs-lookup"><span data-stu-id="aceda-139">If you're using [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB is included in the free Community edition of Visual Studio, as well as the Professional and higher editions.</span></span>  

## <a name="see-also"></a><span data-ttu-id="aceda-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aceda-140">See also</span></span>

- [<span data-ttu-id="aceda-141">Začínáme</span><span class="sxs-lookup"><span data-stu-id="aceda-141">Getting Started</span></span>](getting-started.md)
