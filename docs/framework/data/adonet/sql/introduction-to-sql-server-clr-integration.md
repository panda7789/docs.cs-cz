---
title: Úvod k integraci modulu CLR na SQL Serveru
ms.date: 03/30/2017
ms.assetid: 551d2290-ed80-49be-b377-44b32444da1c
ms.openlocfilehash: 76c6fb4cb37807f286f1f1f2aeedbdea6c74fe38
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002141"
---
# <a name="introduction-to-sql-server-clr-integration"></a><span data-ttu-id="cb6fe-102">Úvod k integraci modulu CLR na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="cb6fe-102">Introduction to SQL Server CLR Integration</span></span>
<span data-ttu-id="cb6fe-103">Modul CLR (Common Language Runtime) je srdcem společnosti Microsoft .NET Framework a poskytuje spouštěcí prostředí pro veškerý kód .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cb6fe-103">The common language runtime (CLR) is the heart of the Microsoft .NET Framework and provides the execution environment for all .NET Framework code.</span></span> <span data-ttu-id="cb6fe-104">Kód, který běží v rámci CLR, je označován jako spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="cb6fe-104">Code that runs within the CLR is referred to as managed code.</span></span> <span data-ttu-id="cb6fe-105">CLR poskytuje různé funkce a služby, které jsou nezbytné pro spuštění programu, včetně kompilace JIT (just-in-time), přidělování a správě paměti, vynucování bezpečnosti typů, zpracování výjimek, správy vláken a zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="cb6fe-105">The CLR provides various functions and services required for program execution, including just-in-time (JIT) compilation, allocating and managing memory, enforcing type safety, exception handling, thread management, and security.</span></span>  
  
 <span data-ttu-id="cb6fe-106">S modulem CLR hostovaným v Microsoft SQL Server (nazývaným integrace CLR) můžete vytvářet uložené procedury, triggery, uživatelsky definované funkce, uživatelsky definované typy a uživatelsky definované agregace ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="cb6fe-106">With the CLR hosted in Microsoft SQL Server (called CLR integration), you can author stored procedures, triggers, user-defined functions, user-defined types, and user-defined aggregates in managed code.</span></span> <span data-ttu-id="cb6fe-107">Vzhledem k tomu, že spravovaný kód se zkompiluje do nativního kódu před provedením, můžete v některých scénářích dosáhnout výrazného zvýšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="cb6fe-107">Because managed code compiles to native code prior to execution, you can achieve significant performance increases in some scenarios.</span></span>  
  
 <span data-ttu-id="cb6fe-108">Spravovaný kód používá zabezpečení přístupu kódu (CAS), odkazy na kód a domény aplikace, aby se zabránilo sestavením v provádění určitých operací.</span><span class="sxs-lookup"><span data-stu-id="cb6fe-108">Managed code uses Code Access Security (CAS), code links, and application domains to prevent assemblies from performing certain operations.</span></span> <span data-ttu-id="cb6fe-109">SQL Server používá CAS ke zvýšení zabezpečení spravovaného kódu a zabránění ohrožení zabezpečení operačního systému nebo databázového serveru.</span><span class="sxs-lookup"><span data-stu-id="cb6fe-109">SQL Server uses CAS to help secure the managed code and prevent compromise of the operating system or database server.</span></span>  
  
 <span data-ttu-id="cb6fe-110">Tato část je určena pouze k tomu, aby poskytovala dostatek informací, aby bylo možné začít programovat s SQL Server integrací CLR a není určeno pro komplexní.</span><span class="sxs-lookup"><span data-stu-id="cb6fe-110">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="cb6fe-111">Podrobnější informace najdete v tématu verze SQL Server Knihy online pro verzi SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="cb6fe-111">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="cb6fe-112">**SQL Server Knihy online**</span><span class="sxs-lookup"><span data-stu-id="cb6fe-112">**SQL Server Books Online**</span></span>  
  
- [<span data-ttu-id="cb6fe-113">Přehled integrace modulu CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="cb6fe-113">Common Language Runtime (CLR) Integration Overview</span></span>](https://go.microsoft.com/fwlink/?LinkId=115242)  
  
## <a name="enabling-clr-integration"></a><span data-ttu-id="cb6fe-114">Povolení integrace modulu CLR</span><span class="sxs-lookup"><span data-stu-id="cb6fe-114">Enabling CLR Integration</span></span>  
 <span data-ttu-id="cb6fe-115">Funkce integrace modulu CLR (Common Language Runtime) je ve výchozím nastavení vypnuta v Microsoft SQL Server a musí být povolena, aby bylo možné použít objekty, které jsou implementovány pomocí integrace modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="cb6fe-115">The common language runtime (CLR) integration feature is off by default in Microsoft SQL Server, and must be enabled in order to use objects that are implemented using CLR integration.</span></span> <span data-ttu-id="cb6fe-116">Chcete-li povolit integraci modulu CLR pomocí jazyka Transact-SQL, použijte možnost `clr enabled` uložené procedury `sp_configure`, jak je znázorněno níže:</span><span class="sxs-lookup"><span data-stu-id="cb6fe-116">To enable CLR integration using Transact-SQL, use the `clr enabled` option of the `sp_configure` stored procedure as shown:</span></span>  
  
```sql  
sp_configure 'clr enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
 <span data-ttu-id="cb6fe-117">Integraci modulu CLR můžete zakázat nastavením možnosti `clr enabled` na hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="cb6fe-117">You can disable CLR integration by setting the `clr enabled` option to 0.</span></span> <span data-ttu-id="cb6fe-118">Zakážete-li integraci modulu CLR, SQL Server zastaví provádění všech rutin CLR a uvolní všechny domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="cb6fe-118">When you disable CLR integration, SQL Server stops executing all CLR routines and unloads all application domains.</span></span>  
  
 <span data-ttu-id="cb6fe-119">Podrobnější informace najdete v tématu verze SQL Server Knihy online pro verzi SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="cb6fe-119">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="cb6fe-120">**SQL Server Knihy online**</span><span class="sxs-lookup"><span data-stu-id="cb6fe-120">**SQL Server Books Online**</span></span>  
  
- [<span data-ttu-id="cb6fe-121">Povolení integrace modulu CLR</span><span class="sxs-lookup"><span data-stu-id="cb6fe-121">Enabling CLR Integration</span></span>](https://go.microsoft.com/fwlink/?LinkId=115230)  
  
## <a name="deploying-a-clr-assembly"></a><span data-ttu-id="cb6fe-122">Nasazení sestavení CLR</span><span class="sxs-lookup"><span data-stu-id="cb6fe-122">Deploying a CLR Assembly</span></span>  
 <span data-ttu-id="cb6fe-123">Až budou metody CLR testovány a ověřeny na testovacím serveru, mohou být distribuovány na provozní servery pomocí skriptu nasazení.</span><span class="sxs-lookup"><span data-stu-id="cb6fe-123">Once the CLR methods have been tested and verified on the test server, they can be distributed to production servers using a deployment script.</span></span> <span data-ttu-id="cb6fe-124">Skript nasazení lze vytvořit ručně nebo pomocí SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="cb6fe-124">The deployment script can be generated manually, or by using SQL Server Management Studio.</span></span> <span data-ttu-id="cb6fe-125">Podrobnější informace najdete v tématu verze SQL Server Knihy online pro verzi SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="cb6fe-125">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="cb6fe-126">**SQL Server Knihy online**</span><span class="sxs-lookup"><span data-stu-id="cb6fe-126">**SQL Server Books Online**</span></span>  
  
1. [<span data-ttu-id="cb6fe-127">Nasazení objektů databáze CLR</span><span class="sxs-lookup"><span data-stu-id="cb6fe-127">Deploying CLR Database Objects</span></span>](https://go.microsoft.com/fwlink/?LinkId=115232)  
  
## <a name="clr-integration-security"></a><span data-ttu-id="cb6fe-128">Zabezpečení integrace CLR</span><span class="sxs-lookup"><span data-stu-id="cb6fe-128">CLR Integration Security</span></span>  
 <span data-ttu-id="cb6fe-129">Model zabezpečení Microsoft SQL Server integrace s modulem CLR (Common Language Runtime) společnosti Microsoft .NET Framework spravuje a zabezpečuje přístup mezi různými typy objektů CLR a objekty mimo CLR spuštěnými v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="cb6fe-129">The security model of the Microsoft SQL Server integration with the Microsoft .NET Framework common language runtime (CLR) manages and secures access between different types of CLR and non-CLR objects running within SQL Server.</span></span> <span data-ttu-id="cb6fe-130">Tyto objekty mohou být volány příkazem jazyka Transact-SQL nebo jiným objektem CLR běžícím na serveru.</span><span class="sxs-lookup"><span data-stu-id="cb6fe-130">These objects may be called by a Transact-SQL statement or another CLR object running in the server.</span></span>  
  
 <span data-ttu-id="cb6fe-131">Podrobnější informace najdete v tématu verze SQL Server Knihy online pro verzi SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="cb6fe-131">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="cb6fe-132">**SQL Server Knihy online**</span><span class="sxs-lookup"><span data-stu-id="cb6fe-132">**SQL Server Books Online**</span></span>  
  
- [<span data-ttu-id="cb6fe-133">Zabezpečení integrace CLR</span><span class="sxs-lookup"><span data-stu-id="cb6fe-133">CLR Integration Security</span></span>](https://go.microsoft.com/fwlink/?LinkId=115234)  
  
## <a name="debugging-a-clr-assembly"></a><span data-ttu-id="cb6fe-134">Ladění sestavení CLR</span><span class="sxs-lookup"><span data-stu-id="cb6fe-134">Debugging a CLR Assembly</span></span>  
 <span data-ttu-id="cb6fe-135">Microsoft SQL Server poskytuje podporu pro ladění objektů Transact-SQL a modulu CLR (Common Language Runtime) v databázi.</span><span class="sxs-lookup"><span data-stu-id="cb6fe-135">Microsoft SQL Server provides support for debugging Transact-SQL and common language runtime (CLR) objects in the database.</span></span> <span data-ttu-id="cb6fe-136">Ladění funguje napříč jazyky: uživatelé můžou bezproblémově krokovat objekty CLR z jazyka Transact-SQL a naopak.</span><span class="sxs-lookup"><span data-stu-id="cb6fe-136">Debugging works across languages: users can step seamlessly into CLR objects from Transact-SQL, and vice versa.</span></span>  
  
 <span data-ttu-id="cb6fe-137">Podrobnější informace najdete v tématu verze SQL Server Knihy online pro verzi SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="cb6fe-137">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="cb6fe-138">**SQL Server Knihy online**</span><span class="sxs-lookup"><span data-stu-id="cb6fe-138">**SQL Server Books Online**</span></span>  
  
- [<span data-ttu-id="cb6fe-139">Ladění objektů databáze CLR</span><span class="sxs-lookup"><span data-stu-id="cb6fe-139">Debugging CLR Database Objects</span></span>](https://go.microsoft.com/fwlink/?LinkId=115236)  
  
## <a name="see-also"></a><span data-ttu-id="cb6fe-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cb6fe-140">See also</span></span>

- [<span data-ttu-id="cb6fe-141">Zabezpečení přístupu ke kódu a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="cb6fe-141">Code Access Security and ADO.NET</span></span>](../code-access-security.md)
- [<span data-ttu-id="cb6fe-142">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="cb6fe-142">ADO.NET Overview</span></span>](../ado-net-overview.md)
