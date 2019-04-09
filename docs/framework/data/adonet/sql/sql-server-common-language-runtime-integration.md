---
title: Integrace CLR (Common Language Runtime) na SQL Serveru
ms.date: 03/30/2017
ms.assetid: c7a324c4-160d-44c2-b593-641af06eca61
ms.openlocfilehash: d87f2b89583747b80ef103f419bd9bd2e3b1e0da
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089832"
---
# <a name="sql-server-common-language-runtime-integration"></a><span data-ttu-id="4fef9-102">Integrace CLR (Common Language Runtime) na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="4fef9-102">SQL Server Common Language Runtime Integration</span></span>
<span data-ttu-id="4fef9-103">SQL Server 2005 zavedené integraci běžné součásti modulu runtime (CLR) jazyk rozhraní .NET Framework pro Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="4fef9-103">SQL Server 2005 introduced the integration of the common language runtime (CLR) component of the .NET Framework for Microsoft Windows.</span></span> <span data-ttu-id="4fef9-104">To znamená, že můžete napsat uložené procedury, aktivační události, uživatelem definovaných typů, uživatelem definované funkce, uživatelem definovaných agregacích a datových proudů funkce vracející tabulku pomocí libovolného jazyka, rozhraní .NET Framework, včetně Microsoft Visual Basic .NET a Microsoft Visual C#.</span><span class="sxs-lookup"><span data-stu-id="4fef9-104">This means that you can write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, including Microsoft Visual Basic .NET and Microsoft Visual C#.</span></span> <span data-ttu-id="4fef9-105"><xref:Microsoft.SqlServer.Server> Obor názvů obsahuje sadu nových aplikačních programovacích rozhraní (API) tak, aby spravovaný kód může spolupracovat s prostředím Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4fef9-105">The <xref:Microsoft.SqlServer.Server> namespace contains a set of new application programming interfaces (APIs) so that managed code can interact with the Microsoft SQL Server environment.</span></span>  
  
 <span data-ttu-id="4fef9-106">Tato část popisuje funkce a chování, které jsou specifické pro integrace systému SQL Server common language runtime (CLR) a konkrétní rozšíření v procesu serveru SQL Server pro technologii ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="4fef9-106">This section describes features and behaviors that are specific to SQL Server common language runtime (CLR) integration and the SQL Server in-process specific extensions to ADO.NET.</span></span>  
  
 <span data-ttu-id="4fef9-107">Tato část poskytuje pouze dostatek informací, jak začít programovat díky integraci modulu CLR SQL serveru a není určena být vyčerpávající.</span><span class="sxs-lookup"><span data-stu-id="4fef9-107">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="4fef9-108">Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi SQL serveru, který používáte.</span><span class="sxs-lookup"><span data-stu-id="4fef9-108">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 **<span data-ttu-id="4fef9-109">SQL Server Books Online</span><span class="sxs-lookup"><span data-stu-id="4fef9-109">SQL Server Books Online</span></span>**  
  
1.  [<span data-ttu-id="4fef9-110">Běžné koncepty programování integrace Language Runtime (CLR)</span><span class="sxs-lookup"><span data-stu-id="4fef9-110">Common Language Runtime (CLR) Integration Programming Concepts</span></span>](https://go.microsoft.com/fwlink/?LinkId=115240)  
  
## <a name="in-this-section"></a><span data-ttu-id="4fef9-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="4fef9-111">In This Section</span></span>  
 [<span data-ttu-id="4fef9-112">Úvod k integraci modulu CLR na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="4fef9-112">Introduction to SQL Server CLR Integration</span></span>](../../../../../docs/framework/data/adonet/sql/introduction-to-sql-server-clr-integration.md)  
 <span data-ttu-id="4fef9-113">Poskytuje úvod do integrace modulu CLR SQL serveru.</span><span class="sxs-lookup"><span data-stu-id="4fef9-113">Provides an introduction to SQL Server CLR integration.</span></span> <span data-ttu-id="4fef9-114">Obsahuje odkazy na další témata.</span><span class="sxs-lookup"><span data-stu-id="4fef9-114">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="4fef9-115">Uživatelem definované funkce CLR</span><span class="sxs-lookup"><span data-stu-id="4fef9-115">CLR User-Defined Functions</span></span>](../../../../../docs/framework/data/adonet/sql/clr-user-defined-functions.md)  
 <span data-ttu-id="4fef9-116">Popisuje, jak implementovat a použít různé typy funkce CLR: agregační funkce vracející tabulku, skalární a definovaný uživatelem.</span><span class="sxs-lookup"><span data-stu-id="4fef9-116">Describes how to implement and use the various types of CLR functions: table-valued, scalar, and user-defined aggregate functions.</span></span>  
  
 [<span data-ttu-id="4fef9-117">Uživatelem definované typy CLR</span><span class="sxs-lookup"><span data-stu-id="4fef9-117">CLR User-Defined Types</span></span>](../../../../../docs/framework/data/adonet/sql/clr-user-defined-types.md)  
 <span data-ttu-id="4fef9-118">Popisuje, jak implementovat a použít uživatelem definované typy CLR.</span><span class="sxs-lookup"><span data-stu-id="4fef9-118">Describes how to implement and use CLR user-defined types.</span></span> <span data-ttu-id="4fef9-119">Obsahuje odkazy na další témata.</span><span class="sxs-lookup"><span data-stu-id="4fef9-119">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="4fef9-120">Uložené procedury CLR</span><span class="sxs-lookup"><span data-stu-id="4fef9-120">CLR Stored Procedures</span></span>](../../../../../docs/framework/data/adonet/sql/clr-stored-procedures.md)  
 <span data-ttu-id="4fef9-121">Popisuje, jak implementovat a používat CLR uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="4fef9-121">Describes how to implement and use CLR stored procedures.</span></span> <span data-ttu-id="4fef9-122">Obsahuje odkazy na další témata.</span><span class="sxs-lookup"><span data-stu-id="4fef9-122">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="4fef9-123">Aktivační procedury CLR</span><span class="sxs-lookup"><span data-stu-id="4fef9-123">CLR Triggers</span></span>](../../../../../docs/framework/data/adonet/sql/clr-triggers.md)  
 <span data-ttu-id="4fef9-124">Popisuje, jak implementovat a použít aktivační procedury modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="4fef9-124">Describes how to implement and use CLR triggers.</span></span> <span data-ttu-id="4fef9-125">Obsahuje odkazy na další témata.</span><span class="sxs-lookup"><span data-stu-id="4fef9-125">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="4fef9-126">Kontextové připojení</span><span class="sxs-lookup"><span data-stu-id="4fef9-126">The Context Connection</span></span>](../../../../../docs/framework/data/adonet/sql/the-context-connection.md)  
 <span data-ttu-id="4fef9-127">Popisuje připojení kontextu.</span><span class="sxs-lookup"><span data-stu-id="4fef9-127">Describes the context connection.</span></span>  
  
 [<span data-ttu-id="4fef9-128">Chování ADO.NET specifické pro proces SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="4fef9-128">SQL Server In-Process-Specific Behavior of ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-in-process-specific-behavior-of-adonet.md)  
 <span data-ttu-id="4fef9-129">Popisuje rozšíření konkrétní v procesu systému SQL Server, ADO.NET a připojení kontextu.</span><span class="sxs-lookup"><span data-stu-id="4fef9-129">Describes the SQL Server in-process specific extensions to ADO.NET, and the context connection.</span></span> <span data-ttu-id="4fef9-130">Obsahuje odkazy na další témata.</span><span class="sxs-lookup"><span data-stu-id="4fef9-130">Provides links to additional topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fef9-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4fef9-131">See also</span></span>

- [<span data-ttu-id="4fef9-132">SQL Server a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4fef9-132">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)
- [<span data-ttu-id="4fef9-133">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="4fef9-133">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
