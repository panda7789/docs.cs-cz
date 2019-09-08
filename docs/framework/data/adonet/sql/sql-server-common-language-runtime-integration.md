---
title: Integrace CLR (Common Language Runtime) na SQL Serveru
ms.date: 03/30/2017
ms.assetid: c7a324c4-160d-44c2-b593-641af06eca61
ms.openlocfilehash: 77b40c6a1576b87d9bb4a7eb4b1ee3df8828b892
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780868"
---
# <a name="sql-server-common-language-runtime-integration"></a><span data-ttu-id="491cf-102">Integrace CLR (Common Language Runtime) na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="491cf-102">SQL Server Common Language Runtime Integration</span></span>
<span data-ttu-id="491cf-103">SQL Server 2005 zavedl integraci komponenty modulu CLR (Common Language Runtime) .NET Framework pro systém Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="491cf-103">SQL Server 2005 introduced the integration of the common language runtime (CLR) component of the .NET Framework for Microsoft Windows.</span></span> <span data-ttu-id="491cf-104">To znamená, že můžete zapisovat uložené procedury, triggery, uživatelsky definované typy, uživatelsky definované funkce, uživatelsky definované agregace a streamovat funkce vracející tabulku pomocí libovolného .NET Framework jazyka, včetně Microsoft Visual Basic .NET a Microsoft. Vizuál C#.</span><span class="sxs-lookup"><span data-stu-id="491cf-104">This means that you can write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, including Microsoft Visual Basic .NET and Microsoft Visual C#.</span></span> <span data-ttu-id="491cf-105"><xref:Microsoft.SqlServer.Server> Obor názvů obsahuje sadu nových aplikačních programovacích rozhraní (API), aby spravovaný kód mohl pracovat s prostředím Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="491cf-105">The <xref:Microsoft.SqlServer.Server> namespace contains a set of new application programming interfaces (APIs) so that managed code can interact with the Microsoft SQL Server environment.</span></span>  
  
 <span data-ttu-id="491cf-106">V této části jsou popsány funkce a chování, které jsou specifické pro SQL Server integraci modulu CLR (Common Language Runtime) a SQL Server specifických rozšíření pro ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="491cf-106">This section describes features and behaviors that are specific to SQL Server common language runtime (CLR) integration and the SQL Server in-process specific extensions to ADO.NET.</span></span>  
  
 <span data-ttu-id="491cf-107">Tato část je určena pouze k tomu, aby poskytovala dostatek informací, aby bylo možné začít programovat s SQL Server integrací CLR a není určeno pro komplexní.</span><span class="sxs-lookup"><span data-stu-id="491cf-107">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="491cf-108">Podrobnější informace najdete v tématu verze SQL Server Knihy online pro verzi SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="491cf-108">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="491cf-109">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="491cf-109">**SQL Server Books Online**</span></span>  
  
1. [<span data-ttu-id="491cf-110">Koncepce programování pro integraci modulu CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="491cf-110">Common Language Runtime (CLR) Integration Programming Concepts</span></span>](https://go.microsoft.com/fwlink/?LinkId=115240)  
  
## <a name="in-this-section"></a><span data-ttu-id="491cf-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="491cf-111">In This Section</span></span>  
 [<span data-ttu-id="491cf-112">Úvod k integraci modulu CLR na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="491cf-112">Introduction to SQL Server CLR Integration</span></span>](introduction-to-sql-server-clr-integration.md)  
 <span data-ttu-id="491cf-113">Poskytuje Úvod do SQL Server integrace modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="491cf-113">Provides an introduction to SQL Server CLR integration.</span></span> <span data-ttu-id="491cf-114">Obsahuje odkazy na další témata.</span><span class="sxs-lookup"><span data-stu-id="491cf-114">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="491cf-115">Uživatelem definované funkce CLR</span><span class="sxs-lookup"><span data-stu-id="491cf-115">CLR User-Defined Functions</span></span>](clr-user-defined-functions.md)  
 <span data-ttu-id="491cf-116">Popisuje, jak implementovat a používat různé typy funkcí CLR: agregační funkce s hodnotami Table, skalární a uživatelsky definované agregační funkce.</span><span class="sxs-lookup"><span data-stu-id="491cf-116">Describes how to implement and use the various types of CLR functions: table-valued, scalar, and user-defined aggregate functions.</span></span>  
  
 [<span data-ttu-id="491cf-117">Uživatelem definované typy CLR</span><span class="sxs-lookup"><span data-stu-id="491cf-117">CLR User-Defined Types</span></span>](clr-user-defined-types.md)  
 <span data-ttu-id="491cf-118">Popisuje, jak implementovat a používat uživatelsky definované typy CLR.</span><span class="sxs-lookup"><span data-stu-id="491cf-118">Describes how to implement and use CLR user-defined types.</span></span> <span data-ttu-id="491cf-119">Obsahuje odkazy na další témata.</span><span class="sxs-lookup"><span data-stu-id="491cf-119">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="491cf-120">Uložené procedury CLR</span><span class="sxs-lookup"><span data-stu-id="491cf-120">CLR Stored Procedures</span></span>](clr-stored-procedures.md)  
 <span data-ttu-id="491cf-121">Popisuje, jak implementovat a používat uložené procedury modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="491cf-121">Describes how to implement and use CLR stored procedures.</span></span> <span data-ttu-id="491cf-122">Obsahuje odkazy na další témata.</span><span class="sxs-lookup"><span data-stu-id="491cf-122">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="491cf-123">Aktivační procedury CLR</span><span class="sxs-lookup"><span data-stu-id="491cf-123">CLR Triggers</span></span>](clr-triggers.md)  
 <span data-ttu-id="491cf-124">Popisuje, jak implementovat a používat triggery modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="491cf-124">Describes how to implement and use CLR triggers.</span></span> <span data-ttu-id="491cf-125">Obsahuje odkazy na další témata.</span><span class="sxs-lookup"><span data-stu-id="491cf-125">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="491cf-126">Kontextové připojení</span><span class="sxs-lookup"><span data-stu-id="491cf-126">The Context Connection</span></span>](the-context-connection.md)  
 <span data-ttu-id="491cf-127">Popisuje připojení kontextu.</span><span class="sxs-lookup"><span data-stu-id="491cf-127">Describes the context connection.</span></span>  
  
 [<span data-ttu-id="491cf-128">Chování ADO.NET specifické pro proces SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="491cf-128">SQL Server In-Process-Specific Behavior of ADO.NET</span></span>](sql-server-in-process-specific-behavior-of-adonet.md)  
 <span data-ttu-id="491cf-129">Popisuje SQL Server v rámci procesu specifická rozšíření ADO.NET a připojení kontextu.</span><span class="sxs-lookup"><span data-stu-id="491cf-129">Describes the SQL Server in-process specific extensions to ADO.NET, and the context connection.</span></span> <span data-ttu-id="491cf-130">Obsahuje odkazy na další témata.</span><span class="sxs-lookup"><span data-stu-id="491cf-130">Provides links to additional topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="491cf-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="491cf-131">See also</span></span>

- [<span data-ttu-id="491cf-132">SQL Server a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="491cf-132">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="491cf-133">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="491cf-133">ADO.NET Overview</span></span>](../ado-net-overview.md)
