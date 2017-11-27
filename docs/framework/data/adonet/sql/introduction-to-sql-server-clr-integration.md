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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ab9dad1031979169aee99a7bb6bc5fe409954e9a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="introduction-to-sql-server-clr-integration"></a><span data-ttu-id="cc0f4-102">Úvod do integrace modulu CLR SQL serveru</span><span class="sxs-lookup"><span data-stu-id="cc0f4-102">Introduction to SQL Server CLR Integration</span></span>
<span data-ttu-id="cc0f4-103">Common language runtime (CLR) jsou srdcem rozhraní Microsoft .NET Framework a poskytuje prostředí pro spuštění pro všechny kód rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cc0f4-103">The common language runtime (CLR) is the heart of the Microsoft .NET Framework and provides the execution environment for all .NET Framework code.</span></span> <span data-ttu-id="cc0f4-104">Kód, který běží v rámci modulu CLR se označuje jako spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="cc0f4-104">Code that runs within the CLR is referred to as managed code.</span></span> <span data-ttu-id="cc0f4-105">Modul CLR poskytuje různé funkce a služby jsou nezbytné pro spuštění programu, včetně kompilace za běhu (JIT), přidělování a správě paměti, vynucování bezpečnost typů, výjimek, vlákno správy a zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="cc0f4-105">The CLR provides various functions and services required for program execution, including just-in-time (JIT) compilation, allocating and managing memory, enforcing type safety, exception handling, thread management, and security.</span></span>  
  
 <span data-ttu-id="cc0f4-106">Pomocí modulu CLR hostované v systému Microsoft SQL Server (označovaný jako integrace modulu CLR) můžete vytvořit uložené procedury, triggery, uživatelem definovaných funkcích, uživatelem definované typy a uživatelem definovaných agregacích ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="cc0f4-106">With the CLR hosted in Microsoft SQL Server (called CLR integration), you can author stored procedures, triggers, user-defined functions, user-defined types, and user-defined aggregates in managed code.</span></span> <span data-ttu-id="cc0f4-107">Protože spravovaný kód zkompiluje do nativního kódu před spuštění, můžete dosáhnout zvýšení výkonu v některých scénářích.</span><span class="sxs-lookup"><span data-stu-id="cc0f4-107">Because managed code compiles to native code prior to execution, you can achieve significant performance increases in some scenarios.</span></span>  
  
 <span data-ttu-id="cc0f4-108">Spravovaný kód používá zabezpečení přístupu kódu (CAS), odkazů na kód a aplikační domény, aby se zabránilo sestavení z provádění některých operací.</span><span class="sxs-lookup"><span data-stu-id="cc0f4-108">Managed code uses Code Access Security (CAS), code links, and application domains to prevent assemblies from performing certain operations.</span></span> <span data-ttu-id="cc0f4-109">SQL Server používá k zabezpečení spravovaného kódu a nedošlo k ohrožení zabezpečení operačního systému nebo na serveru databáze certifikační Autority.</span><span class="sxs-lookup"><span data-stu-id="cc0f4-109">SQL Server uses CAS to help secure the managed code and prevent compromise of the operating system or database server.</span></span>  
  
 <span data-ttu-id="cc0f4-110">Tato část poskytuje jenom dostatek informací, abyste mohli začít programování s integrace modulu CLR SQL serveru a není určen jako komplexní.</span><span class="sxs-lookup"><span data-stu-id="cc0f4-110">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="cc0f4-111">Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi systému SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="cc0f4-111">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="cc0f4-112">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="cc0f4-112">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="cc0f4-113">Běžné Přehled integrace Language Runtime (CLR)</span><span class="sxs-lookup"><span data-stu-id="cc0f4-113">Common Language Runtime (CLR) Integration Overview</span></span>](http://go.microsoft.com/fwlink/?LinkId=115242)  
  
## <a name="enabling-clr-integration"></a><span data-ttu-id="cc0f4-114">Povolení integrace modulu CLR</span><span class="sxs-lookup"><span data-stu-id="cc0f4-114">Enabling CLR Integration</span></span>  
 <span data-ttu-id="cc0f4-115">Běžné funkce integrace language runtime (CLR) ve výchozím nastavení v systému Microsoft SQL Server a musí být povolena, aby bylo možné používat objekty, které jsou implementovány pomocí integrace modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="cc0f4-115">The common language runtime (CLR) integration feature is off by default in Microsoft SQL Server, and must be enabled in order to use objects that are implemented using CLR integration.</span></span> <span data-ttu-id="cc0f4-116">Pokud chcete povolit integraci modulu CLR pomocí jazyka Transact-SQL, použijte `clr enabled` možnost `sp_configure` uložené procedury, jak je znázorněno:</span><span class="sxs-lookup"><span data-stu-id="cc0f4-116">To enable CLR integration using Transact-SQL, use the `clr enabled` option of the `sp_configure` stored procedure as shown:</span></span>  
  
```  
sp_configure 'clr enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
 <span data-ttu-id="cc0f4-117">Integrace modulu CLR můžete zakázat nastavením `clr enabled` možnost na hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="cc0f4-117">You can disable CLR integration by setting the `clr enabled` option to 0.</span></span> <span data-ttu-id="cc0f4-118">Pokud zakážete integrace modulu CLR, SQL Server zastaví provádění všechny rutiny modulu CLR a uvolní všechny domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="cc0f4-118">When you disable CLR integration, SQL Server stops executing all CLR routines and unloads all application domains.</span></span>  
  
 <span data-ttu-id="cc0f4-119">Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi systému SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="cc0f4-119">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="cc0f4-120">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="cc0f4-120">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="cc0f4-121">Povolení integrace modulu CLR</span><span class="sxs-lookup"><span data-stu-id="cc0f4-121">Enabling CLR Integration</span></span>](http://go.microsoft.com/fwlink/?LinkId=115230)  
  
## <a name="deploying-a-clr-assembly"></a><span data-ttu-id="cc0f4-122">Nasazení sestavení CLR</span><span class="sxs-lookup"><span data-stu-id="cc0f4-122">Deploying a CLR Assembly</span></span>  
 <span data-ttu-id="cc0f4-123">Jakmile metod modulu CLR byly testovány a ověřit na testovacím serveru, lze rozdělit na produkční servery pomocí skriptu nasazení.</span><span class="sxs-lookup"><span data-stu-id="cc0f4-123">Once the CLR methods have been tested and verified on the test server, they can be distributed to production servers using a deployment script.</span></span> <span data-ttu-id="cc0f4-124">Skript nasazení lze vytvořit ručně nebo pomocí SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="cc0f4-124">The deployment script can be generated manually, or by using SQL Server Management Studio.</span></span> <span data-ttu-id="cc0f4-125">Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi systému SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="cc0f4-125">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="cc0f4-126">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="cc0f4-126">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="cc0f4-127">Nasazení databázové objekty CLR</span><span class="sxs-lookup"><span data-stu-id="cc0f4-127">Deploying CLR Database Objects</span></span>](http://go.microsoft.com/fwlink/?LinkId=115232)  
  
## <a name="clr-integration-security"></a><span data-ttu-id="cc0f4-128">Zabezpečení integrace modulu CLR</span><span class="sxs-lookup"><span data-stu-id="cc0f4-128">CLR Integration Security</span></span>  
 <span data-ttu-id="cc0f4-129">Model zabezpečení integrace systému Microsoft SQL Server pomocí rozhraní Microsoft .NET Framework common language runtime (CLR) spravuje a zabezpečuje přístupu mezi různé typy CLR a bez CLR objektů, které jsou spuštěné v systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="cc0f4-129">The security model of the Microsoft SQL Server integration with the Microsoft .NET Framework common language runtime (CLR) manages and secures access between different types of CLR and non-CLR objects running within SQL Server.</span></span> <span data-ttu-id="cc0f4-130">Tyto objekty může volat příkazu Transact-SQL nebo jiný objekt CLR běžícího na serveru.</span><span class="sxs-lookup"><span data-stu-id="cc0f4-130">These objects may be called by a Transact-SQL statement or another CLR object running in the server.</span></span>  
  
 <span data-ttu-id="cc0f4-131">Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi systému SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="cc0f4-131">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="cc0f4-132">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="cc0f4-132">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="cc0f4-133">Zabezpečení integrace modulu CLR</span><span class="sxs-lookup"><span data-stu-id="cc0f4-133">CLR Integration Security</span></span>](http://go.microsoft.com/fwlink/?LinkId=115234)  
  
## <a name="debugging-a-clr-assembly"></a><span data-ttu-id="cc0f4-134">Ladění sestavení CLR</span><span class="sxs-lookup"><span data-stu-id="cc0f4-134">Debugging a CLR Assembly</span></span>  
 <span data-ttu-id="cc0f4-135">Microsoft SQL Server poskytuje podporu pro ladění jazyka Transact-SQL a common language runtime (CLR) objekty v databázi.</span><span class="sxs-lookup"><span data-stu-id="cc0f4-135">Microsoft SQL Server provides support for debugging Transact-SQL and common language runtime (CLR) objects in the database.</span></span> <span data-ttu-id="cc0f4-136">Ladění funguje napříč jazyky: uživatelé mohou kroku bezproblémově do CLR objekty z jazyka Transact-SQL a naopak.</span><span class="sxs-lookup"><span data-stu-id="cc0f4-136">Debugging works across languages: users can step seamlessly into CLR objects from Transact-SQL, and vice versa.</span></span>  
  
 <span data-ttu-id="cc0f4-137">Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi systému SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="cc0f4-137">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="cc0f4-138">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="cc0f4-138">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="cc0f4-139">Ladění databázové objekty CLR</span><span class="sxs-lookup"><span data-stu-id="cc0f4-139">Debugging CLR Database Objects</span></span>](http://go.microsoft.com/fwlink/?LinkId=115236)  
  
## <a name="see-also"></a><span data-ttu-id="cc0f4-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="cc0f4-140">See Also</span></span>  
 [<span data-ttu-id="cc0f4-141">Vytváření objektů serveru SQL Server 2005 ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="cc0f4-141">Creating SQL Server 2005 Objects In Managed Code</span></span>](http://msdn.microsoft.com/en-us/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [<span data-ttu-id="cc0f4-142">Zabezpečení přístupu kódu a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="cc0f4-142">Code Access Security and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/code-access-security.md)  
 [<span data-ttu-id="cc0f4-143">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="cc0f4-143">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
