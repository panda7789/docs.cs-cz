---
title: SQL Server Compact a LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
ms.openlocfilehash: b5a1a12018bd85cf313c1841e6b67ab2edf67b4a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792533"
---
# <a name="sql-server-compact-and-linq-to-sql"></a><span data-ttu-id="54e1c-102">SQL Server Compact a LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="54e1c-102">SQL Server Compact and LINQ to SQL</span></span>
<span data-ttu-id="54e1c-103">SQL Server Compact je výchozí databáze nainstalovaná se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="54e1c-103">SQL Server Compact is the default database installed with Visual Studio.</span></span> <span data-ttu-id="54e1c-104">Další informace naleznete v tématu [Using SQL Server Compact (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110)).</span><span class="sxs-lookup"><span data-stu-id="54e1c-104">For more information, see [Using SQL Server Compact (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110)).</span></span>  
  
 <span data-ttu-id="54e1c-105">Toto téma popisuje klíčové rozdíly v tématu použití, konfigurace, sady funkcí a rozsahu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podpory.</span><span class="sxs-lookup"><span data-stu-id="54e1c-105">This topic outlines the key differences in usage, configuration, feature sets, and scope of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] support.</span></span>  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a><span data-ttu-id="54e1c-106">Charakteristiky SQL Server Compact ve vztahu k LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="54e1c-106">Characteristics of SQL Server Compact in Relation to LINQ to SQL</span></span>  
 <span data-ttu-id="54e1c-107">Ve výchozím nastavení je SQL Server Compact nainstalován pro všechny edice sady Visual Studio a je proto k dispozici ve vývojovém počítači pro [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]použití s nástrojem.</span><span class="sxs-lookup"><span data-stu-id="54e1c-107">By default, SQL Server Compact is installed for all Visual Studio editions, and is therefore available on the development computer for use with [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="54e1c-108">Ale nasazení aplikace, která používá SQL Server Compact [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , se liší od aplikace SQL Server.</span><span class="sxs-lookup"><span data-stu-id="54e1c-108">But deployment of an application that uses SQL Server Compact and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] differs from that for a SQL Server application.</span></span> <span data-ttu-id="54e1c-109">SQL Server Compact není součástí .NET Framework a proto musí být zabalená do aplikace nebo stažena odděleně od webu společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="54e1c-109">SQL Server Compact is not a part of the .NET Framework, and therefore must be packaged with the application or downloaded separately from the Microsoft site.</span></span>  
  
 <span data-ttu-id="54e1c-110">Všimněte si následujících vlastností:</span><span class="sxs-lookup"><span data-stu-id="54e1c-110">Note the following characteristics:</span></span>  
  
- <span data-ttu-id="54e1c-111">SQL Server Compact je zabalen jako knihovna DLL, kterou lze použít přímo pro soubory databáze (přípona. sdf).</span><span class="sxs-lookup"><span data-stu-id="54e1c-111">SQL Server Compact is packaged as a DLL that can be used against database files (.sdf extension) directly.</span></span>  
  
- <span data-ttu-id="54e1c-112">SQL Server Compact běží ve stejném procesu jako klientská aplikace.</span><span class="sxs-lookup"><span data-stu-id="54e1c-112">SQL Server Compact runs in the same process as the client application.</span></span> <span data-ttu-id="54e1c-113">Efektivita komunikace s SQL Server Compact může být proto výrazně vyšší než komunikace s SQL Server.</span><span class="sxs-lookup"><span data-stu-id="54e1c-113">The efficiency of communication with SQL Server Compact can therefore be significantly higher than communicating with SQL Server.</span></span> <span data-ttu-id="54e1c-114">Na druhé straně SQL Server Compact vyžaduje interoperabilitu mezi spravovaným a nespravovaným kódem a jeho přidruženými náklady.</span><span class="sxs-lookup"><span data-stu-id="54e1c-114">On the other hand, SQL Server Compact does require interoperability between managed and unmanaged code with its attendant costs.</span></span>  
  
- <span data-ttu-id="54e1c-115">Velikost SQL Server Compact DLL je malá.</span><span class="sxs-lookup"><span data-stu-id="54e1c-115">The size of the SQL Server Compact DLL is small.</span></span> <span data-ttu-id="54e1c-116">Tato funkce zmenší celkovou velikost aplikace.</span><span class="sxs-lookup"><span data-stu-id="54e1c-116">This feature reduces the overall application size.</span></span>  
  
- <span data-ttu-id="54e1c-117">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Modul runtime a nástroj příkazového řádku SQLMetal podporují SQL Server Compact.</span><span class="sxs-lookup"><span data-stu-id="54e1c-117">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime and the SQLMetal command-line tool support SQL Server Compact.</span></span>  
  
- <span data-ttu-id="54e1c-118">Návrhář relací objektů nepodporuje SQL Server Compact.</span><span class="sxs-lookup"><span data-stu-id="54e1c-118">The Object Relational Designer does not support SQL Server Compact.</span></span>  
  
## <a name="feature-set"></a><span data-ttu-id="54e1c-119">Sada funkcí</span><span class="sxs-lookup"><span data-stu-id="54e1c-119">Feature Set</span></span>  
 <span data-ttu-id="54e1c-120">Sada funkcí SQL Server Compact je mnohem jednodušší než sada funkcí SQL Server následujícími způsoby, které mohou ovlivnit [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikace:</span><span class="sxs-lookup"><span data-stu-id="54e1c-120">The SQL Server Compact feature set is much simpler than the feature set of SQL Server in the following ways that can affect [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications :</span></span>  
  
- <span data-ttu-id="54e1c-121">SQL Server Compact nepodporuje uložené procedury ani zobrazení.</span><span class="sxs-lookup"><span data-stu-id="54e1c-121">SQL Server Compact does not support stored procedures or views.</span></span>  
  
- <span data-ttu-id="54e1c-122">SQL Server Compact podporuje pouze podmnožinu datových typů a funkcí SQL.</span><span class="sxs-lookup"><span data-stu-id="54e1c-122">SQL Server Compact supports only a subset of data types and SQL functions.</span></span>  
  
- <span data-ttu-id="54e1c-123">SQL Server Compact podporuje pouze podmnožinu konstrukcí SQL.</span><span class="sxs-lookup"><span data-stu-id="54e1c-123">SQL Server Compact supports only a subset of SQL constructs.</span></span>  
  
- <span data-ttu-id="54e1c-124">SQL Server Compact poskytuje jenom minimální Optimalizátor.</span><span class="sxs-lookup"><span data-stu-id="54e1c-124">SQL Server Compact provides only a minimal optimizer.</span></span> <span data-ttu-id="54e1c-125">Je možné, že některé dotazy můžou vyprší časový limit.</span><span class="sxs-lookup"><span data-stu-id="54e1c-125">It is possible that some queries might time out.</span></span>  
  
- <span data-ttu-id="54e1c-126">SQL Server Compact nepodporuje částečnou důvěryhodnost.</span><span class="sxs-lookup"><span data-stu-id="54e1c-126">SQL Server Compact does not support partial trust.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54e1c-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="54e1c-127">See also</span></span>

- [<span data-ttu-id="54e1c-128">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="54e1c-128">Reference</span></span>](reference.md)
