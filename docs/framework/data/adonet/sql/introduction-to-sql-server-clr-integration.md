---
title: Úvod k integraci modulu CLR na SQL Serveru
description: Integrace CLR s SQL Server podporuje uložené procedury, triggery, uživatelsky definované funkce, uživatelsky definované typy a uživatelsky definované agregace ve spravovaném kódu.
ms.date: 03/30/2017
ms.assetid: 551d2290-ed80-49be-b377-44b32444da1c
ms.openlocfilehash: fa2ef68792d09cf94b3e0680a14bd79f9b593999
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286427"
---
# <a name="introduction-to-sql-server-clr-integration"></a><span data-ttu-id="9419d-103">Úvod k integraci modulu CLR na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="9419d-103">Introduction to SQL Server CLR Integration</span></span>
<span data-ttu-id="9419d-104">Modul CLR (Common Language Runtime) je srdcem společnosti Microsoft .NET Framework a poskytuje spouštěcí prostředí pro veškerý kód .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9419d-104">The common language runtime (CLR) is the heart of the Microsoft .NET Framework and provides the execution environment for all .NET Framework code.</span></span> <span data-ttu-id="9419d-105">Kód, který běží v rámci CLR, je označován jako spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="9419d-105">Code that runs within the CLR is referred to as managed code.</span></span> <span data-ttu-id="9419d-106">CLR poskytuje různé funkce a služby, které jsou nezbytné pro spuštění programu, včetně kompilace JIT (just-in-time), přidělování a správě paměti, vynucování bezpečnosti typů, zpracování výjimek, správy vláken a zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="9419d-106">The CLR provides various functions and services required for program execution, including just-in-time (JIT) compilation, allocating and managing memory, enforcing type safety, exception handling, thread management, and security.</span></span>  
  
 <span data-ttu-id="9419d-107">S modulem CLR hostovaným v Microsoft SQL Server (nazývaným integrace CLR) můžete vytvářet uložené procedury, triggery, uživatelsky definované funkce, uživatelsky definované typy a uživatelsky definované agregace ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="9419d-107">With the CLR hosted in Microsoft SQL Server (called CLR integration), you can author stored procedures, triggers, user-defined functions, user-defined types, and user-defined aggregates in managed code.</span></span> <span data-ttu-id="9419d-108">Vzhledem k tomu, že spravovaný kód se zkompiluje do nativního kódu před provedením, můžete v některých scénářích dosáhnout výrazného zvýšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="9419d-108">Because managed code compiles to native code prior to execution, you can achieve significant performance increases in some scenarios.</span></span>  
  
 <span data-ttu-id="9419d-109">Spravovaný kód používá zabezpečení přístupu kódu (CAS), odkazy na kód a domény aplikace, aby se zabránilo sestavením v provádění určitých operací.</span><span class="sxs-lookup"><span data-stu-id="9419d-109">Managed code uses Code Access Security (CAS), code links, and application domains to prevent assemblies from performing certain operations.</span></span> <span data-ttu-id="9419d-110">SQL Server používá CAS ke zvýšení zabezpečení spravovaného kódu a zabránění ohrožení zabezpečení operačního systému nebo databázového serveru.</span><span class="sxs-lookup"><span data-stu-id="9419d-110">SQL Server uses CAS to help secure the managed code and prevent compromise of the operating system or database server.</span></span>  
  
 <span data-ttu-id="9419d-111">Tato část je určena pouze k tomu, aby poskytovala dostatek informací, aby bylo možné začít programovat s SQL Server integrací CLR a není určeno pro komplexní.</span><span class="sxs-lookup"><span data-stu-id="9419d-111">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="9419d-112">Podrobnější informace najdete v tématu verze SQL Server Knihy online pro verzi SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="9419d-112">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="9419d-113">**Dokumentace SQL Serveru**</span><span class="sxs-lookup"><span data-stu-id="9419d-113">**SQL Server documentation**</span></span>  
  
- [<span data-ttu-id="9419d-114">Přehled integrace modulu CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="9419d-114">Common Language Runtime (CLR) Integration Overview</span></span>](/sql/relational-databases/clr-integration/common-language-runtime-integration-overview)  
  
## <a name="enabling-clr-integration"></a><span data-ttu-id="9419d-115">Povolení integrace modulu CLR</span><span class="sxs-lookup"><span data-stu-id="9419d-115">Enabling CLR Integration</span></span>  
 <span data-ttu-id="9419d-116">Funkce integrace modulu CLR (Common Language Runtime) je ve výchozím nastavení vypnuta v Microsoft SQL Server a musí být povolena, aby bylo možné použít objekty, které jsou implementovány pomocí integrace modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="9419d-116">The common language runtime (CLR) integration feature is off by default in Microsoft SQL Server, and must be enabled in order to use objects that are implemented using CLR integration.</span></span> <span data-ttu-id="9419d-117">Chcete-li povolit integraci modulu CLR pomocí jazyka Transact-SQL, použijte `clr enabled` možnost `sp_configure` uloženou proceduru, jak je znázorněno níže:</span><span class="sxs-lookup"><span data-stu-id="9419d-117">To enable CLR integration using Transact-SQL, use the `clr enabled` option of the `sp_configure` stored procedure as shown:</span></span>  
  
```sql  
sp_configure 'clr enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
 <span data-ttu-id="9419d-118">Integraci CLR můžete zakázat nastavením `clr enabled` Možnosti na 0.</span><span class="sxs-lookup"><span data-stu-id="9419d-118">You can disable CLR integration by setting the `clr enabled` option to 0.</span></span> <span data-ttu-id="9419d-119">Zakážete-li integraci modulu CLR, SQL Server zastaví provádění všech rutin CLR a uvolní všechny domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="9419d-119">When you disable CLR integration, SQL Server stops executing all CLR routines and unloads all application domains.</span></span>  
  
 <span data-ttu-id="9419d-120">Podrobnější informace najdete v tématu verze SQL Server Knihy online pro verzi SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="9419d-120">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="9419d-121">**Dokumentace SQL Serveru**</span><span class="sxs-lookup"><span data-stu-id="9419d-121">**SQL Server documentation**</span></span>  
  
- [<span data-ttu-id="9419d-122">Povolení integrace modulu CLR</span><span class="sxs-lookup"><span data-stu-id="9419d-122">Enabling CLR Integration</span></span>](/sql/relational-databases/clr-integration/clr-integration-enabling)  
  
## <a name="deploying-a-clr-assembly"></a><span data-ttu-id="9419d-123">Nasazení sestavení CLR</span><span class="sxs-lookup"><span data-stu-id="9419d-123">Deploying a CLR Assembly</span></span>  
 <span data-ttu-id="9419d-124">Až budou metody CLR testovány a ověřeny na testovacím serveru, mohou být distribuovány na provozní servery pomocí skriptu nasazení.</span><span class="sxs-lookup"><span data-stu-id="9419d-124">Once the CLR methods have been tested and verified on the test server, they can be distributed to production servers using a deployment script.</span></span> <span data-ttu-id="9419d-125">Skript nasazení lze vytvořit ručně nebo pomocí SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="9419d-125">The deployment script can be generated manually, or by using SQL Server Management Studio.</span></span> <span data-ttu-id="9419d-126">Podrobnější informace najdete v dokumentaci verze SQL Server pro verzi SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="9419d-126">For more detailed information, see the version of SQL Server documentation for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="9419d-127">**Dokumentace SQL Serveru**</span><span class="sxs-lookup"><span data-stu-id="9419d-127">**SQL Server documentation**</span></span>  
  
1. [<span data-ttu-id="9419d-128">Nasazení objektů databáze CLR</span><span class="sxs-lookup"><span data-stu-id="9419d-128">Deploying CLR Database Objects</span></span>](/sql/relational-databases/clr-integration/deploying-clr-database-objects)  
  
## <a name="clr-integration-security"></a><span data-ttu-id="9419d-129">Zabezpečení integrace CLR</span><span class="sxs-lookup"><span data-stu-id="9419d-129">CLR Integration Security</span></span>  
 <span data-ttu-id="9419d-130">Model zabezpečení Microsoft SQL Server integrace s modulem CLR (Common Language Runtime) společnosti Microsoft .NET Framework spravuje a zabezpečuje přístup mezi různými typy objektů CLR a objekty mimo CLR spuštěnými v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9419d-130">The security model of the Microsoft SQL Server integration with the Microsoft .NET Framework common language runtime (CLR) manages and secures access between different types of CLR and non-CLR objects running within SQL Server.</span></span> <span data-ttu-id="9419d-131">Tyto objekty mohou být volány příkazem jazyka Transact-SQL nebo jiným objektem CLR běžícím na serveru.</span><span class="sxs-lookup"><span data-stu-id="9419d-131">These objects may be called by a Transact-SQL statement or another CLR object running in the server.</span></span>  
  
 <span data-ttu-id="9419d-132">Podrobnější informace najdete v tématu verze SQL Server Knihy online pro verzi SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="9419d-132">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="9419d-133">**Dokumentace SQL Serveru**</span><span class="sxs-lookup"><span data-stu-id="9419d-133">**SQL Server documentation**</span></span>  
  
- [<span data-ttu-id="9419d-134">Zabezpečení integrace CLR</span><span class="sxs-lookup"><span data-stu-id="9419d-134">CLR Integration Security</span></span>](/sql/relational-databases/clr-integration/security/clr-integration-security)  
  
## <a name="debugging-a-clr-assembly"></a><span data-ttu-id="9419d-135">Ladění sestavení CLR</span><span class="sxs-lookup"><span data-stu-id="9419d-135">Debugging a CLR Assembly</span></span>  
 <span data-ttu-id="9419d-136">Microsoft SQL Server poskytuje podporu pro ladění objektů Transact-SQL a modulu CLR (Common Language Runtime) v databázi.</span><span class="sxs-lookup"><span data-stu-id="9419d-136">Microsoft SQL Server provides support for debugging Transact-SQL and common language runtime (CLR) objects in the database.</span></span> <span data-ttu-id="9419d-137">Ladění funguje napříč jazyky: uživatelé můžou bezproblémově krokovat objekty CLR z jazyka Transact-SQL a naopak.</span><span class="sxs-lookup"><span data-stu-id="9419d-137">Debugging works across languages: users can step seamlessly into CLR objects from Transact-SQL, and vice versa.</span></span>  
  
 <span data-ttu-id="9419d-138">Podrobnější informace najdete v tématu verze SQL Server Knihy online pro verzi SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="9419d-138">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="9419d-139">**Dokumentace SQL Serveru**</span><span class="sxs-lookup"><span data-stu-id="9419d-139">**SQL Server documentation**</span></span>  
  
- [<span data-ttu-id="9419d-140">Ladění objektů databáze CLR</span><span class="sxs-lookup"><span data-stu-id="9419d-140">Debugging CLR Database Objects</span></span>](/sql/relational-databases/clr-integration/debugging-clr-database-objects)  
  
## <a name="see-also"></a><span data-ttu-id="9419d-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="9419d-141">See also</span></span>

- [<span data-ttu-id="9419d-142">Zabezpečení přístupu ke kódu a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9419d-142">Code Access Security and ADO.NET</span></span>](../code-access-security.md)
- [<span data-ttu-id="9419d-143">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9419d-143">ADO.NET Overview</span></span>](../ado-net-overview.md)
