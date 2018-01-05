---
title: SQL Server Compact a technologie LINQ to SQL
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 2717a94228dc1be8da0d84179201747d60c896a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="sql-server-compact-and-linq-to-sql"></a><span data-ttu-id="44e7a-102">SQL Server Compact a technologie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="44e7a-102">SQL Server Compact and LINQ to SQL</span></span>
<span data-ttu-id="44e7a-103">Systém SQL Server Compact je databáze výchozí nainstalované s Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="44e7a-103">SQL Server Compact is the default database installed with Visual Studio.</span></span> <span data-ttu-id="44e7a-104">Další informace najdete v tématu [PAVE přes pomocí systému SQL Server Compact (Visual Studio)](http://msdn.microsoft.com/en-us/13320dd1-94e5-4077-bf76-8df253695ccc).</span><span class="sxs-lookup"><span data-stu-id="44e7a-104">For more information, see [PAVE OVER Using SQL Server Compact (Visual Studio)](http://msdn.microsoft.com/en-us/13320dd1-94e5-4077-bf76-8df253695ccc).</span></span>  
  
 <span data-ttu-id="44e7a-105">Toto téma popisuje hlavní rozdíly ve využití, konfiguraci, sady funkcí a oboru [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporovat.</span><span class="sxs-lookup"><span data-stu-id="44e7a-105">This topic outlines the key differences in usage, configuration, feature sets, and scope of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] support.</span></span>  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a><span data-ttu-id="44e7a-106">Vlastnosti systému SQL Server Compact ve vztahu k technologie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="44e7a-106">Characteristics of SQL Server Compact in Relation to LINQ to SQL</span></span>  
 <span data-ttu-id="44e7a-107">Ve výchozím nastavení, je pro všechny nainstalován systém SQL Server Compact [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] edice a proto je k dispozici na vývojovém počítači pro použití s [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="44e7a-107">By default, SQL Server Compact is installed for all [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] editions, and is therefore available on the development computer for use with [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="44e7a-108">Nasazení aplikace, která používá systém SQL Server Compact, ale a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] se liší od pro [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="44e7a-108">But deployment of an application that uses SQL Server Compact and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] differs from that for a [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] application.</span></span> <span data-ttu-id="44e7a-109">Systém SQL Server Compact není součástí rozhraní .NET Framework a proto musí být zabalené aplikace nebo samostatně stáhnout z webu společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="44e7a-109">SQL Server Compact is not a part of the .NET Framework, and therefore must be packaged with the application or downloaded separately from the Microsoft site.</span></span>  
  
 <span data-ttu-id="44e7a-110">Vezměte na vědomí následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="44e7a-110">Note the following characteristics:</span></span>  
  
-   <span data-ttu-id="44e7a-111">Systém SQL Server Compact je zabalené jako knihovnu DLL, kterou lze použít pro soubory databáze (rozšíření SDF) přímo.</span><span class="sxs-lookup"><span data-stu-id="44e7a-111">SQL Server Compact is packaged as a DLL that can be used against database files (.sdf extension) directly.</span></span>  
  
-   <span data-ttu-id="44e7a-112">Systém SQL Server Compact běží v rámci jednoho procesu jako klientská aplikace.</span><span class="sxs-lookup"><span data-stu-id="44e7a-112">SQL Server Compact runs in the same process as the client application.</span></span> <span data-ttu-id="44e7a-113">Efektivitu komunikace se službou SQL Server Compact proto může být výrazně vyšší než komunikaci s [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="44e7a-113">The efficiency of communication with SQL Server Compact can therefore be significantly higher than communicating with [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="44e7a-114">Systém SQL Server Compact na druhé straně vyžadují spolupráci mezi spravovanými a nespravovanými kódu pomocí jeho náklady z toho plynoucí.</span><span class="sxs-lookup"><span data-stu-id="44e7a-114">On the other hand, SQL Server Compact does require interoperability between managed and unmanaged code with its attendant costs.</span></span>  
  
-   <span data-ttu-id="44e7a-115">Velikost je SQL Server Compact DLL je malá.</span><span class="sxs-lookup"><span data-stu-id="44e7a-115">The size of the SQL Server Compact DLL is small.</span></span> <span data-ttu-id="44e7a-116">Tato funkce snižuje velikost celkové aplikace.</span><span class="sxs-lookup"><span data-stu-id="44e7a-116">This feature reduces the overall application size.</span></span>  
  
-   <span data-ttu-id="44e7a-117">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Runtime a nástroj příkazového řádku na SQLMetal podporují systém SQL Server Compact.</span><span class="sxs-lookup"><span data-stu-id="44e7a-117">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime and the SQLMetal command-line tool support SQL Server Compact.</span></span>  
  
-   <span data-ttu-id="44e7a-118">[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] Nepodporuje systém SQL Server Compact.</span><span class="sxs-lookup"><span data-stu-id="44e7a-118">The [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] does not support SQL Server Compact.</span></span>  
  
## <a name="feature-set"></a><span data-ttu-id="44e7a-119">Sada funkcí</span><span class="sxs-lookup"><span data-stu-id="44e7a-119">Feature Set</span></span>  
 <span data-ttu-id="44e7a-120">Systém SQL Server Compact sada funkcí je mnohem jednodušší než funkce sadu [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] následujícími způsoby, které můžou ovlivnit [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikace:</span><span class="sxs-lookup"><span data-stu-id="44e7a-120">The SQL Server Compact feature set is much simpler than the feature set of [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] in the following ways that can affect [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications :</span></span>  
  
-   <span data-ttu-id="44e7a-121">Systém SQL Server Compact nepodporuje uložené procedury nebo zobrazení.</span><span class="sxs-lookup"><span data-stu-id="44e7a-121">SQL Server Compact does not support stored procedures or views.</span></span>  
  
-   <span data-ttu-id="44e7a-122">Systém SQL Server Compact podporuje jenom podmnožinu funkcí SQL a datových typů.</span><span class="sxs-lookup"><span data-stu-id="44e7a-122">SQL Server Compact supports only a subset of data types and SQL functions.</span></span>  
  
-   <span data-ttu-id="44e7a-123">Systém SQL Server Compact podporuje pouze podmnožinu konstrukce SQL.</span><span class="sxs-lookup"><span data-stu-id="44e7a-123">SQL Server Compact supports only a subset of SQL constructs.</span></span>  
  
-   <span data-ttu-id="44e7a-124">Systém SQL Server Compact poskytuje jenom minimální pro optimalizaci.</span><span class="sxs-lookup"><span data-stu-id="44e7a-124">SQL Server Compact provides only a minimal optimizer.</span></span> <span data-ttu-id="44e7a-125">Je možné, že některé dotazy může vypršení časového limitu.</span><span class="sxs-lookup"><span data-stu-id="44e7a-125">It is possible that some queries might time out.</span></span>  
  
-   <span data-ttu-id="44e7a-126">Systém SQL Server Compact nepodporuje částečnou důvěryhodností.</span><span class="sxs-lookup"><span data-stu-id="44e7a-126">SQL Server Compact does not support partial trust.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44e7a-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="44e7a-127">See Also</span></span>  
 [<span data-ttu-id="44e7a-128">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="44e7a-128">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
