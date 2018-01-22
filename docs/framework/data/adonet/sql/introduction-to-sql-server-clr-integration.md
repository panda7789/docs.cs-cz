---
title: "Úvod do integrace modulu CLR SQL serveru"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 551d2290-ed80-49be-b377-44b32444da1c
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b551ec612b6d1901640ca5f2f1d116a98a8131cd
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="introduction-to-sql-server-clr-integration"></a><span data-ttu-id="e89f6-102">Úvod do integrace modulu CLR SQL serveru</span><span class="sxs-lookup"><span data-stu-id="e89f6-102">Introduction to SQL Server CLR Integration</span></span>
<span data-ttu-id="e89f6-103">Common language runtime (CLR) jsou srdcem rozhraní Microsoft .NET Framework a poskytuje prostředí pro spuštění pro všechny kód rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e89f6-103">The common language runtime (CLR) is the heart of the Microsoft .NET Framework and provides the execution environment for all .NET Framework code.</span></span> <span data-ttu-id="e89f6-104">Kód, který běží v rámci modulu CLR se označuje jako spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="e89f6-104">Code that runs within the CLR is referred to as managed code.</span></span> <span data-ttu-id="e89f6-105">Modul CLR poskytuje různé funkce a služby jsou nezbytné pro spuštění programu, včetně kompilace za běhu (JIT), přidělování a správě paměti, vynucování bezpečnost typů, výjimek, vlákno správy a zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e89f6-105">The CLR provides various functions and services required for program execution, including just-in-time (JIT) compilation, allocating and managing memory, enforcing type safety, exception handling, thread management, and security.</span></span>  
  
 <span data-ttu-id="e89f6-106">Pomocí modulu CLR hostované v systému Microsoft SQL Server (označovaný jako integrace modulu CLR) můžete vytvořit uložené procedury, triggery, uživatelem definovaných funkcích, uživatelem definované typy a uživatelem definovaných agregacích ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="e89f6-106">With the CLR hosted in Microsoft SQL Server (called CLR integration), you can author stored procedures, triggers, user-defined functions, user-defined types, and user-defined aggregates in managed code.</span></span> <span data-ttu-id="e89f6-107">Protože spravovaný kód zkompiluje do nativního kódu před spuštění, můžete dosáhnout zvýšení výkonu v některých scénářích.</span><span class="sxs-lookup"><span data-stu-id="e89f6-107">Because managed code compiles to native code prior to execution, you can achieve significant performance increases in some scenarios.</span></span>  
  
 <span data-ttu-id="e89f6-108">Spravovaný kód používá zabezpečení přístupu kódu (CAS), odkazů na kód a aplikační domény, aby se zabránilo sestavení z provádění některých operací.</span><span class="sxs-lookup"><span data-stu-id="e89f6-108">Managed code uses Code Access Security (CAS), code links, and application domains to prevent assemblies from performing certain operations.</span></span> <span data-ttu-id="e89f6-109">SQL Server používá k zabezpečení spravovaného kódu a nedošlo k ohrožení zabezpečení operačního systému nebo na serveru databáze certifikační Autority.</span><span class="sxs-lookup"><span data-stu-id="e89f6-109">SQL Server uses CAS to help secure the managed code and prevent compromise of the operating system or database server.</span></span>  
  
 <span data-ttu-id="e89f6-110">Tato část poskytuje jenom dostatek informací, abyste mohli začít programování s integrace modulu CLR SQL serveru a není určen jako komplexní.</span><span class="sxs-lookup"><span data-stu-id="e89f6-110">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="e89f6-111">Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi systému SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="e89f6-111">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="e89f6-112">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="e89f6-112">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="e89f6-113">Běžné Přehled integrace Language Runtime (CLR)</span><span class="sxs-lookup"><span data-stu-id="e89f6-113">Common Language Runtime (CLR) Integration Overview</span></span>](http://go.microsoft.com/fwlink/?LinkId=115242)  
  
## <a name="enabling-clr-integration"></a><span data-ttu-id="e89f6-114">Povolení integrace modulu CLR</span><span class="sxs-lookup"><span data-stu-id="e89f6-114">Enabling CLR Integration</span></span>  
 <span data-ttu-id="e89f6-115">Běžné funkce integrace language runtime (CLR) ve výchozím nastavení v systému Microsoft SQL Server a musí být povolena, aby bylo možné používat objekty, které jsou implementovány pomocí integrace modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="e89f6-115">The common language runtime (CLR) integration feature is off by default in Microsoft SQL Server, and must be enabled in order to use objects that are implemented using CLR integration.</span></span> <span data-ttu-id="e89f6-116">Pokud chcete povolit integraci modulu CLR pomocí jazyka Transact-SQL, použijte `clr enabled` možnost `sp_configure` uložené procedury, jak je znázorněno:</span><span class="sxs-lookup"><span data-stu-id="e89f6-116">To enable CLR integration using Transact-SQL, use the `clr enabled` option of the `sp_configure` stored procedure as shown:</span></span>  
  
```  
sp_configure 'clr enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
 <span data-ttu-id="e89f6-117">Integrace modulu CLR můžete zakázat nastavením `clr enabled` možnost na hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="e89f6-117">You can disable CLR integration by setting the `clr enabled` option to 0.</span></span> <span data-ttu-id="e89f6-118">Pokud zakážete integrace modulu CLR, SQL Server zastaví provádění všechny rutiny modulu CLR a uvolní všechny domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="e89f6-118">When you disable CLR integration, SQL Server stops executing all CLR routines and unloads all application domains.</span></span>  
  
 <span data-ttu-id="e89f6-119">Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi systému SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="e89f6-119">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="e89f6-120">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="e89f6-120">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="e89f6-121">Povolení integrace modulu CLR</span><span class="sxs-lookup"><span data-stu-id="e89f6-121">Enabling CLR Integration</span></span>](http://go.microsoft.com/fwlink/?LinkId=115230)  
  
## <a name="deploying-a-clr-assembly"></a><span data-ttu-id="e89f6-122">Nasazení sestavení CLR</span><span class="sxs-lookup"><span data-stu-id="e89f6-122">Deploying a CLR Assembly</span></span>  
 <span data-ttu-id="e89f6-123">Jakmile metod modulu CLR byly testovány a ověřit na testovacím serveru, lze rozdělit na produkční servery pomocí skriptu nasazení.</span><span class="sxs-lookup"><span data-stu-id="e89f6-123">Once the CLR methods have been tested and verified on the test server, they can be distributed to production servers using a deployment script.</span></span> <span data-ttu-id="e89f6-124">Skript nasazení lze vytvořit ručně nebo pomocí SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="e89f6-124">The deployment script can be generated manually, or by using SQL Server Management Studio.</span></span> <span data-ttu-id="e89f6-125">Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi systému SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="e89f6-125">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="e89f6-126">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="e89f6-126">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="e89f6-127">Nasazení databázové objekty CLR</span><span class="sxs-lookup"><span data-stu-id="e89f6-127">Deploying CLR Database Objects</span></span>](http://go.microsoft.com/fwlink/?LinkId=115232)  
  
## <a name="clr-integration-security"></a><span data-ttu-id="e89f6-128">Zabezpečení integrace modulu CLR</span><span class="sxs-lookup"><span data-stu-id="e89f6-128">CLR Integration Security</span></span>  
 <span data-ttu-id="e89f6-129">Model zabezpečení integrace systému Microsoft SQL Server pomocí rozhraní Microsoft .NET Framework common language runtime (CLR) spravuje a zabezpečuje přístupu mezi různé typy CLR a bez CLR objektů, které jsou spuštěné v systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e89f6-129">The security model of the Microsoft SQL Server integration with the Microsoft .NET Framework common language runtime (CLR) manages and secures access between different types of CLR and non-CLR objects running within SQL Server.</span></span> <span data-ttu-id="e89f6-130">Tyto objekty může volat příkazu Transact-SQL nebo jiný objekt CLR běžícího na serveru.</span><span class="sxs-lookup"><span data-stu-id="e89f6-130">These objects may be called by a Transact-SQL statement or another CLR object running in the server.</span></span>  
  
 <span data-ttu-id="e89f6-131">Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi systému SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="e89f6-131">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="e89f6-132">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="e89f6-132">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="e89f6-133">Zabezpečení integrace modulu CLR</span><span class="sxs-lookup"><span data-stu-id="e89f6-133">CLR Integration Security</span></span>](http://go.microsoft.com/fwlink/?LinkId=115234)  
  
## <a name="debugging-a-clr-assembly"></a><span data-ttu-id="e89f6-134">Ladění sestavení CLR</span><span class="sxs-lookup"><span data-stu-id="e89f6-134">Debugging a CLR Assembly</span></span>  
 <span data-ttu-id="e89f6-135">Microsoft SQL Server poskytuje podporu pro ladění jazyka Transact-SQL a common language runtime (CLR) objekty v databázi.</span><span class="sxs-lookup"><span data-stu-id="e89f6-135">Microsoft SQL Server provides support for debugging Transact-SQL and common language runtime (CLR) objects in the database.</span></span> <span data-ttu-id="e89f6-136">Ladění funguje napříč jazyky: uživatelé mohou kroku bezproblémově do CLR objekty z jazyka Transact-SQL a naopak.</span><span class="sxs-lookup"><span data-stu-id="e89f6-136">Debugging works across languages: users can step seamlessly into CLR objects from Transact-SQL, and vice versa.</span></span>  
  
 <span data-ttu-id="e89f6-137">Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi systému SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="e89f6-137">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="e89f6-138">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="e89f6-138">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="e89f6-139">Ladění databázové objekty CLR</span><span class="sxs-lookup"><span data-stu-id="e89f6-139">Debugging CLR Database Objects</span></span>](http://go.microsoft.com/fwlink/?LinkId=115236)  
  
## <a name="see-also"></a><span data-ttu-id="e89f6-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="e89f6-140">See Also</span></span>  
 [<span data-ttu-id="e89f6-141">Vytváření objektů serveru SQL Server 2005 ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="e89f6-141">Creating SQL Server 2005 Objects In Managed Code</span></span>](http://msdn.microsoft.com/library/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [<span data-ttu-id="e89f6-142">Zabezpečení přístupu ke kódu a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e89f6-142">Code Access Security and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/code-access-security.md)  
 [<span data-ttu-id="e89f6-143">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="e89f6-143">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
