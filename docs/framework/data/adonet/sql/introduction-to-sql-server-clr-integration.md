---
title: Úvod k integraci modulu CLR na SQL Serveru
ms.date: 03/30/2017
ms.assetid: 551d2290-ed80-49be-b377-44b32444da1c
ms.openlocfilehash: dc7d19bf361ed5fcda1fd5edf64eeb5e4ce15a71
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59336808"
---
# <a name="introduction-to-sql-server-clr-integration"></a><span data-ttu-id="ae88e-102">Úvod k integraci modulu CLR na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="ae88e-102">Introduction to SQL Server CLR Integration</span></span>
<span data-ttu-id="ae88e-103">Common language runtime (CLR) je základem rozhraní Microsoft .NET Framework a poskytuje prostředí pro spuštění pro veškerý kód rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ae88e-103">The common language runtime (CLR) is the heart of the Microsoft .NET Framework and provides the execution environment for all .NET Framework code.</span></span> <span data-ttu-id="ae88e-104">Kód, který běží v rámci modulu CLR se označuje jako spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="ae88e-104">Code that runs within the CLR is referred to as managed code.</span></span> <span data-ttu-id="ae88e-105">CLR poskytuje různé funkce a služby potřebné pro spuštění programu, včetně kompilace just-in-time (JIT), přidělování a správu paměti a vynucuje bezpečnost typů, zpracování výjimek, správa vláken a zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="ae88e-105">The CLR provides various functions and services required for program execution, including just-in-time (JIT) compilation, allocating and managing memory, enforcing type safety, exception handling, thread management, and security.</span></span>  
  
 <span data-ttu-id="ae88e-106">S modulem CLR hostované v systému Microsoft SQL Server (označované jako integrace modulu CLR) můžete vytvořit uložené procedury, aktivační události, uživatelem definovaných funkcích, uživatelem definované typy a uživatelem definovaných agregacích ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="ae88e-106">With the CLR hosted in Microsoft SQL Server (called CLR integration), you can author stored procedures, triggers, user-defined functions, user-defined types, and user-defined aggregates in managed code.</span></span> <span data-ttu-id="ae88e-107">Protože spravovaný kód se zkompiluje do nativního kódu před provedením, můžete dosáhnout zvýšení výkonu v některých scénářích.</span><span class="sxs-lookup"><span data-stu-id="ae88e-107">Because managed code compiles to native code prior to execution, you can achieve significant performance increases in some scenarios.</span></span>  
  
 <span data-ttu-id="ae88e-108">Spravovat kód používá zabezpečení přístupu kódu (CAS), odkazů na kód a aplikační domény, aby se zabránilo sestavení z provádění některých operací.</span><span class="sxs-lookup"><span data-stu-id="ae88e-108">Managed code uses Code Access Security (CAS), code links, and application domains to prevent assemblies from performing certain operations.</span></span> <span data-ttu-id="ae88e-109">Aby zabezpečení spravovaného kódu a nedošlo k ohrožení zabezpečení operačního systému nebo na serveru databáze používá systém SQL Server certifikační Autority.</span><span class="sxs-lookup"><span data-stu-id="ae88e-109">SQL Server uses CAS to help secure the managed code and prevent compromise of the operating system or database server.</span></span>  
  
 <span data-ttu-id="ae88e-110">Tato část poskytuje pouze dostatek informací, jak začít programovat díky integraci modulu CLR SQL serveru a není určena být vyčerpávající.</span><span class="sxs-lookup"><span data-stu-id="ae88e-110">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="ae88e-111">Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi SQL serveru, který používáte.</span><span class="sxs-lookup"><span data-stu-id="ae88e-111">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="ae88e-112">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="ae88e-112">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="ae88e-113">Integrace přehled modelu Common Language Runtime (CLR)</span><span class="sxs-lookup"><span data-stu-id="ae88e-113">Common Language Runtime (CLR) Integration Overview</span></span>](https://go.microsoft.com/fwlink/?LinkId=115242)  
  
## <a name="enabling-clr-integration"></a><span data-ttu-id="ae88e-114">Povolení integrace modulu CLR</span><span class="sxs-lookup"><span data-stu-id="ae88e-114">Enabling CLR Integration</span></span>  
 <span data-ttu-id="ae88e-115">Běžné funkce integrace language runtime (CLR) je vypnuto ve výchozím nastavení v systému Microsoft SQL Server a musí být povolené, aby bylo možné používat objekty, které jsou implementovány pomocí integrace modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="ae88e-115">The common language runtime (CLR) integration feature is off by default in Microsoft SQL Server, and must be enabled in order to use objects that are implemented using CLR integration.</span></span> <span data-ttu-id="ae88e-116">Chcete-li povolit integraci modulu CLR pomocí příkazů jazyka Transact-SQL, použijte `clr enabled` možnost `sp_configure` uložené procedury, jak je znázorněno:</span><span class="sxs-lookup"><span data-stu-id="ae88e-116">To enable CLR integration using Transact-SQL, use the `clr enabled` option of the `sp_configure` stored procedure as shown:</span></span>  
  
```  
sp_configure 'clr enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
 <span data-ttu-id="ae88e-117">Integrace modulu CLR může zakázat nastavením `clr enabled` možnost na hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="ae88e-117">You can disable CLR integration by setting the `clr enabled` option to 0.</span></span> <span data-ttu-id="ae88e-118">Při zakázání integrace modulu CLR SQL serveru zastaví provádění všechny rutiny v modulu CLR a uvolní všechny aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="ae88e-118">When you disable CLR integration, SQL Server stops executing all CLR routines and unloads all application domains.</span></span>  
  
 <span data-ttu-id="ae88e-119">Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi SQL serveru, který používáte.</span><span class="sxs-lookup"><span data-stu-id="ae88e-119">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="ae88e-120">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="ae88e-120">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="ae88e-121">Povolení integrace modulu CLR</span><span class="sxs-lookup"><span data-stu-id="ae88e-121">Enabling CLR Integration</span></span>](https://go.microsoft.com/fwlink/?LinkId=115230)  
  
## <a name="deploying-a-clr-assembly"></a><span data-ttu-id="ae88e-122">Nasazení sestavení CLR</span><span class="sxs-lookup"><span data-stu-id="ae88e-122">Deploying a CLR Assembly</span></span>  
 <span data-ttu-id="ae88e-123">Jakmile základě metod modulu CLR byly testovány a ověřit na testovací server, můžete distribuovat do provozní servery s použitím skriptu nasazení.</span><span class="sxs-lookup"><span data-stu-id="ae88e-123">Once the CLR methods have been tested and verified on the test server, they can be distributed to production servers using a deployment script.</span></span> <span data-ttu-id="ae88e-124">Skript nasazení můžete vygenerovat ručně nebo pomocí SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="ae88e-124">The deployment script can be generated manually, or by using SQL Server Management Studio.</span></span> <span data-ttu-id="ae88e-125">Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi SQL serveru, který používáte.</span><span class="sxs-lookup"><span data-stu-id="ae88e-125">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="ae88e-126">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="ae88e-126">**SQL Server Books Online**</span></span>  
  
1. [<span data-ttu-id="ae88e-127">Nasazení modulu CLR databázové objekty</span><span class="sxs-lookup"><span data-stu-id="ae88e-127">Deploying CLR Database Objects</span></span>](https://go.microsoft.com/fwlink/?LinkId=115232)  
  
## <a name="clr-integration-security"></a><span data-ttu-id="ae88e-128">Zabezpečení integrace CLR</span><span class="sxs-lookup"><span data-stu-id="ae88e-128">CLR Integration Security</span></span>  
 <span data-ttu-id="ae88e-129">Model zabezpečení integrace systému Microsoft SQL Server pomocí rozhraní Microsoft .NET Framework common language runtime (CLR) spravuje a chrání přístup mezi různými typy objektů CLR a modulu CLR v rámci serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ae88e-129">The security model of the Microsoft SQL Server integration with the Microsoft .NET Framework common language runtime (CLR) manages and secures access between different types of CLR and non-CLR objects running within SQL Server.</span></span> <span data-ttu-id="ae88e-130">Tyto objekty mohou být volány příkazu jazyka Transact-SQL nebo jiný objekt CLR spuštěná na serveru.</span><span class="sxs-lookup"><span data-stu-id="ae88e-130">These objects may be called by a Transact-SQL statement or another CLR object running in the server.</span></span>  
  
 <span data-ttu-id="ae88e-131">Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi SQL serveru, který používáte.</span><span class="sxs-lookup"><span data-stu-id="ae88e-131">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="ae88e-132">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="ae88e-132">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="ae88e-133">Zabezpečení integrace CLR</span><span class="sxs-lookup"><span data-stu-id="ae88e-133">CLR Integration Security</span></span>](https://go.microsoft.com/fwlink/?LinkId=115234)  
  
## <a name="debugging-a-clr-assembly"></a><span data-ttu-id="ae88e-134">Ladění sestavení CLR</span><span class="sxs-lookup"><span data-stu-id="ae88e-134">Debugging a CLR Assembly</span></span>  
 <span data-ttu-id="ae88e-135">Microsoft SQL Server poskytuje podporu pro ladění jazyka Transact-SQL a common language runtime (CLR) objekty v databázi.</span><span class="sxs-lookup"><span data-stu-id="ae88e-135">Microsoft SQL Server provides support for debugging Transact-SQL and common language runtime (CLR) objects in the database.</span></span> <span data-ttu-id="ae88e-136">Ladění napříč jazyky funguje: uživatelé můžou kroku bez problémů do CLR objekty z příkazů jazyka Transact-SQL a naopak.</span><span class="sxs-lookup"><span data-stu-id="ae88e-136">Debugging works across languages: users can step seamlessly into CLR objects from Transact-SQL, and vice versa.</span></span>  
  
 <span data-ttu-id="ae88e-137">Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi SQL serveru, který používáte.</span><span class="sxs-lookup"><span data-stu-id="ae88e-137">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="ae88e-138">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="ae88e-138">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="ae88e-139">Ladění CLR databázové objekty</span><span class="sxs-lookup"><span data-stu-id="ae88e-139">Debugging CLR Database Objects</span></span>](https://go.microsoft.com/fwlink/?LinkId=115236)  
  
## <a name="see-also"></a><span data-ttu-id="ae88e-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae88e-140">See also</span></span>

- [<span data-ttu-id="ae88e-141">Zabezpečení přístupu ke kódu a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ae88e-141">Code Access Security and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/code-access-security.md)
- [<span data-ttu-id="ae88e-142">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="ae88e-142">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
