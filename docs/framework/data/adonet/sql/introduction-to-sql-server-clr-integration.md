---
title: Úvod k integraci modulu CLR na SQL Serveru
ms.date: 03/30/2017
ms.assetid: 551d2290-ed80-49be-b377-44b32444da1c
ms.openlocfilehash: fb812a8e524148c507d26ea32e0b4263a4998153
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782261"
---
# <a name="introduction-to-sql-server-clr-integration"></a><span data-ttu-id="994cc-102">Úvod k integraci modulu CLR na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="994cc-102">Introduction to SQL Server CLR Integration</span></span>
<span data-ttu-id="994cc-103">Modul CLR (Common Language Runtime) je srdcem společnosti Microsoft .NET Framework a poskytuje spouštěcí prostředí pro veškerý kód .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="994cc-103">The common language runtime (CLR) is the heart of the Microsoft .NET Framework and provides the execution environment for all .NET Framework code.</span></span> <span data-ttu-id="994cc-104">Kód, který běží v rámci CLR, je označován jako spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="994cc-104">Code that runs within the CLR is referred to as managed code.</span></span> <span data-ttu-id="994cc-105">CLR poskytuje různé funkce a služby, které jsou nezbytné pro spuštění programu, včetně kompilace JIT (just-in-time), přidělování a správě paměti, vynucování bezpečnosti typů, zpracování výjimek, správy vláken a zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="994cc-105">The CLR provides various functions and services required for program execution, including just-in-time (JIT) compilation, allocating and managing memory, enforcing type safety, exception handling, thread management, and security.</span></span>  
  
 <span data-ttu-id="994cc-106">S modulem CLR hostovaným v Microsoft SQL Server (nazývaným integrace CLR) můžete vytvářet uložené procedury, triggery, uživatelsky definované funkce, uživatelsky definované typy a uživatelsky definované agregace ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="994cc-106">With the CLR hosted in Microsoft SQL Server (called CLR integration), you can author stored procedures, triggers, user-defined functions, user-defined types, and user-defined aggregates in managed code.</span></span> <span data-ttu-id="994cc-107">Vzhledem k tomu, že spravovaný kód se zkompiluje do nativního kódu před provedením, můžete v některých scénářích dosáhnout výrazného zvýšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="994cc-107">Because managed code compiles to native code prior to execution, you can achieve significant performance increases in some scenarios.</span></span>  
  
 <span data-ttu-id="994cc-108">Spravovaný kód používá zabezpečení přístupu kódu (CAS), odkazy na kód a domény aplikace, aby se zabránilo sestavením v provádění určitých operací.</span><span class="sxs-lookup"><span data-stu-id="994cc-108">Managed code uses Code Access Security (CAS), code links, and application domains to prevent assemblies from performing certain operations.</span></span> <span data-ttu-id="994cc-109">SQL Server používá CAS ke zvýšení zabezpečení spravovaného kódu a zabránění ohrožení zabezpečení operačního systému nebo databázového serveru.</span><span class="sxs-lookup"><span data-stu-id="994cc-109">SQL Server uses CAS to help secure the managed code and prevent compromise of the operating system or database server.</span></span>  
  
 <span data-ttu-id="994cc-110">Tato část je určena pouze k tomu, aby poskytovala dostatek informací, aby bylo možné začít programovat s SQL Server integrací CLR a není určeno pro komplexní.</span><span class="sxs-lookup"><span data-stu-id="994cc-110">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="994cc-111">Podrobnější informace najdete v tématu verze SQL Server Knihy online pro verzi SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="994cc-111">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="994cc-112">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="994cc-112">**SQL Server Books Online**</span></span>  
  
- [<span data-ttu-id="994cc-113">Přehled integrace modulu CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="994cc-113">Common Language Runtime (CLR) Integration Overview</span></span>](https://go.microsoft.com/fwlink/?LinkId=115242)  
  
## <a name="enabling-clr-integration"></a><span data-ttu-id="994cc-114">Povolení integrace modulu CLR</span><span class="sxs-lookup"><span data-stu-id="994cc-114">Enabling CLR Integration</span></span>  
 <span data-ttu-id="994cc-115">Funkce integrace modulu CLR (Common Language Runtime) je ve výchozím nastavení vypnuta v Microsoft SQL Server a musí být povolena, aby bylo možné použít objekty, které jsou implementovány pomocí integrace modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="994cc-115">The common language runtime (CLR) integration feature is off by default in Microsoft SQL Server, and must be enabled in order to use objects that are implemented using CLR integration.</span></span> <span data-ttu-id="994cc-116">Chcete-li povolit integraci modulu CLR pomocí jazyka Transact- `clr enabled` SQL, použijte `sp_configure` možnost uloženou proceduru, jak je znázorněno níže:</span><span class="sxs-lookup"><span data-stu-id="994cc-116">To enable CLR integration using Transact-SQL, use the `clr enabled` option of the `sp_configure` stored procedure as shown:</span></span>  
  
```  
sp_configure 'clr enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
 <span data-ttu-id="994cc-117">Integraci CLR můžete zakázat nastavením `clr enabled` možnosti na 0.</span><span class="sxs-lookup"><span data-stu-id="994cc-117">You can disable CLR integration by setting the `clr enabled` option to 0.</span></span> <span data-ttu-id="994cc-118">Zakážete-li integraci modulu CLR, SQL Server zastaví provádění všech rutin CLR a uvolní všechny domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="994cc-118">When you disable CLR integration, SQL Server stops executing all CLR routines and unloads all application domains.</span></span>  
  
 <span data-ttu-id="994cc-119">Podrobnější informace najdete v tématu verze SQL Server Knihy online pro verzi SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="994cc-119">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="994cc-120">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="994cc-120">**SQL Server Books Online**</span></span>  
  
- [<span data-ttu-id="994cc-121">Povolení integrace modulu CLR</span><span class="sxs-lookup"><span data-stu-id="994cc-121">Enabling CLR Integration</span></span>](https://go.microsoft.com/fwlink/?LinkId=115230)  
  
## <a name="deploying-a-clr-assembly"></a><span data-ttu-id="994cc-122">Nasazení sestavení CLR</span><span class="sxs-lookup"><span data-stu-id="994cc-122">Deploying a CLR Assembly</span></span>  
 <span data-ttu-id="994cc-123">Až budou metody CLR testovány a ověřeny na testovacím serveru, mohou být distribuovány na provozní servery pomocí skriptu nasazení.</span><span class="sxs-lookup"><span data-stu-id="994cc-123">Once the CLR methods have been tested and verified on the test server, they can be distributed to production servers using a deployment script.</span></span> <span data-ttu-id="994cc-124">Skript nasazení lze vytvořit ručně nebo pomocí SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="994cc-124">The deployment script can be generated manually, or by using SQL Server Management Studio.</span></span> <span data-ttu-id="994cc-125">Podrobnější informace najdete v tématu verze SQL Server Knihy online pro verzi SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="994cc-125">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="994cc-126">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="994cc-126">**SQL Server Books Online**</span></span>  
  
1. [<span data-ttu-id="994cc-127">Nasazení objektů databáze CLR</span><span class="sxs-lookup"><span data-stu-id="994cc-127">Deploying CLR Database Objects</span></span>](https://go.microsoft.com/fwlink/?LinkId=115232)  
  
## <a name="clr-integration-security"></a><span data-ttu-id="994cc-128">Zabezpečení integrace CLR</span><span class="sxs-lookup"><span data-stu-id="994cc-128">CLR Integration Security</span></span>  
 <span data-ttu-id="994cc-129">Model zabezpečení Microsoft SQL Server integrace s modulem CLR (Common Language Runtime) společnosti Microsoft .NET Framework spravuje a zabezpečuje přístup mezi různými typy objektů CLR a objekty mimo CLR spuštěnými v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="994cc-129">The security model of the Microsoft SQL Server integration with the Microsoft .NET Framework common language runtime (CLR) manages and secures access between different types of CLR and non-CLR objects running within SQL Server.</span></span> <span data-ttu-id="994cc-130">Tyto objekty mohou být volány příkazem jazyka Transact-SQL nebo jiným objektem CLR běžícím na serveru.</span><span class="sxs-lookup"><span data-stu-id="994cc-130">These objects may be called by a Transact-SQL statement or another CLR object running in the server.</span></span>  
  
 <span data-ttu-id="994cc-131">Podrobnější informace najdete v tématu verze SQL Server Knihy online pro verzi SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="994cc-131">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="994cc-132">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="994cc-132">**SQL Server Books Online**</span></span>  
  
- [<span data-ttu-id="994cc-133">Zabezpečení integrace CLR</span><span class="sxs-lookup"><span data-stu-id="994cc-133">CLR Integration Security</span></span>](https://go.microsoft.com/fwlink/?LinkId=115234)  
  
## <a name="debugging-a-clr-assembly"></a><span data-ttu-id="994cc-134">Ladění sestavení CLR</span><span class="sxs-lookup"><span data-stu-id="994cc-134">Debugging a CLR Assembly</span></span>  
 <span data-ttu-id="994cc-135">Microsoft SQL Server poskytuje podporu pro ladění objektů Transact-SQL a modulu CLR (Common Language Runtime) v databázi.</span><span class="sxs-lookup"><span data-stu-id="994cc-135">Microsoft SQL Server provides support for debugging Transact-SQL and common language runtime (CLR) objects in the database.</span></span> <span data-ttu-id="994cc-136">Ladění funguje napříč jazyky: uživatelé můžou bezproblémově krokovat objekty CLR z jazyka Transact-SQL a naopak.</span><span class="sxs-lookup"><span data-stu-id="994cc-136">Debugging works across languages: users can step seamlessly into CLR objects from Transact-SQL, and vice versa.</span></span>  
  
 <span data-ttu-id="994cc-137">Podrobnější informace najdete v tématu verze SQL Server Knihy online pro verzi SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="994cc-137">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="994cc-138">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="994cc-138">**SQL Server Books Online**</span></span>  
  
- [<span data-ttu-id="994cc-139">Ladění objektů databáze CLR</span><span class="sxs-lookup"><span data-stu-id="994cc-139">Debugging CLR Database Objects</span></span>](https://go.microsoft.com/fwlink/?LinkId=115236)  
  
## <a name="see-also"></a><span data-ttu-id="994cc-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="994cc-140">See also</span></span>

- [<span data-ttu-id="994cc-141">Zabezpečení přístupu ke kódu a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="994cc-141">Code Access Security and ADO.NET</span></span>](../code-access-security.md)
- [<span data-ttu-id="994cc-142">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="994cc-142">ADO.NET Overview</span></span>](../ado-net-overview.md)
