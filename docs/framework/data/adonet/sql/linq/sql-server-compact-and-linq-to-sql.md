---
title: SQL Server Compact a LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
ms.openlocfilehash: db3f7aef082d965dc27b69f5a966ff038c0ffac0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61917849"
---
# <a name="sql-server-compact-and-linq-to-sql"></a><span data-ttu-id="f335b-102">SQL Server Compact a LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="f335b-102">SQL Server Compact and LINQ to SQL</span></span>
<span data-ttu-id="f335b-103">SQL Server Compact je výchozí databáze nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f335b-103">SQL Server Compact is the default database installed with Visual Studio.</span></span> <span data-ttu-id="f335b-104">Další informace najdete v tématu [pomocí SQL Server Compact (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110)).</span><span class="sxs-lookup"><span data-stu-id="f335b-104">For more information, see [Using SQL Server Compact (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110)).</span></span>  
  
 <span data-ttu-id="f335b-105">Toto téma popisuje hlavní rozdíly ve využití, konfiguraci, sady funkcí a rozsah [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporovat.</span><span class="sxs-lookup"><span data-stu-id="f335b-105">This topic outlines the key differences in usage, configuration, feature sets, and scope of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] support.</span></span>  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a><span data-ttu-id="f335b-106">Vlastnosti systému SQL Server Compact ve vztahu k LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="f335b-106">Characteristics of SQL Server Compact in Relation to LINQ to SQL</span></span>  
 <span data-ttu-id="f335b-107">Ve výchozím nastavení, SQL Server Compact se nainstaluje pro všechny edice sady Visual Studio a proto je k dispozici na na vývojovém počítači pro použití s [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f335b-107">By default, SQL Server Compact is installed for all Visual Studio editions, and is therefore available on the development computer for use with [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="f335b-108">Nasazení aplikace, která používá SQL Server Compact, ale a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] se liší od pro aplikaci systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f335b-108">But deployment of an application that uses SQL Server Compact and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] differs from that for a SQL Server application.</span></span> <span data-ttu-id="f335b-109">SQL Server Compact není součástí rozhraní .NET Framework a proto musí být zabalené aplikace nebo stáhnout samostatně z webu společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f335b-109">SQL Server Compact is not a part of the .NET Framework, and therefore must be packaged with the application or downloaded separately from the Microsoft site.</span></span>  
  
 <span data-ttu-id="f335b-110">Mějte na paměti následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="f335b-110">Note the following characteristics:</span></span>  
  
- <span data-ttu-id="f335b-111">SQL Server Compact je zabalený jako knihovnu DLL, která se dá použít pro soubory databáze (s příponou .sdf) přímo.</span><span class="sxs-lookup"><span data-stu-id="f335b-111">SQL Server Compact is packaged as a DLL that can be used against database files (.sdf extension) directly.</span></span>  
  
- <span data-ttu-id="f335b-112">SQL Server Compact běží ve stejném procesu jako klientská aplikace.</span><span class="sxs-lookup"><span data-stu-id="f335b-112">SQL Server Compact runs in the same process as the client application.</span></span> <span data-ttu-id="f335b-113">Efektivitu komunikaci s SQL serverem Compact, proto může být výrazně vyšší než komunikaci se serverem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f335b-113">The efficiency of communication with SQL Server Compact can therefore be significantly higher than communicating with SQL Server.</span></span> <span data-ttu-id="f335b-114">Na druhé straně SQL Server Compact vyžaduje vzájemná funkční spolupráce mezi spravovaným a nespravovaným kódem s jeho odebrání dodatečné náklady.</span><span class="sxs-lookup"><span data-stu-id="f335b-114">On the other hand, SQL Server Compact does require interoperability between managed and unmanaged code with its attendant costs.</span></span>  
  
- <span data-ttu-id="f335b-115">Velikost SQL Server Compact knihovny DLL je malá.</span><span class="sxs-lookup"><span data-stu-id="f335b-115">The size of the SQL Server Compact DLL is small.</span></span> <span data-ttu-id="f335b-116">Tato funkce snižuje velikost celkového aplikace.</span><span class="sxs-lookup"><span data-stu-id="f335b-116">This feature reduces the overall application size.</span></span>  
  
- <span data-ttu-id="f335b-117">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Modulu runtime a nástroje příkazového řádku SQLMetal podporu systému SQL Server Compact.</span><span class="sxs-lookup"><span data-stu-id="f335b-117">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime and the SQLMetal command-line tool support SQL Server Compact.</span></span>  
  
- <span data-ttu-id="f335b-118">[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] Nepodporuje SQL Server Compact.</span><span class="sxs-lookup"><span data-stu-id="f335b-118">The [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] does not support SQL Server Compact.</span></span>  
  
## <a name="feature-set"></a><span data-ttu-id="f335b-119">Sada funkcí</span><span class="sxs-lookup"><span data-stu-id="f335b-119">Feature Set</span></span>  
 <span data-ttu-id="f335b-120">SQL Server Compact sada funkcí je mnohem jednodušší než sadě funkcí systému SQL Server následujícími způsoby, které můžou ovlivnit [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikace:</span><span class="sxs-lookup"><span data-stu-id="f335b-120">The SQL Server Compact feature set is much simpler than the feature set of SQL Server in the following ways that can affect [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications :</span></span>  
  
- <span data-ttu-id="f335b-121">SQL Server Compact nepodporuje uložené procedury nebo zobrazení.</span><span class="sxs-lookup"><span data-stu-id="f335b-121">SQL Server Compact does not support stored procedures or views.</span></span>  
  
- <span data-ttu-id="f335b-122">SQL Server Compact podporuje jenom určité podmnožiny datových typů a funkcí SQL.</span><span class="sxs-lookup"><span data-stu-id="f335b-122">SQL Server Compact supports only a subset of data types and SQL functions.</span></span>  
  
- <span data-ttu-id="f335b-123">SQL Server Compact podporuje pouze podmnožinu SQL konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="f335b-123">SQL Server Compact supports only a subset of SQL constructs.</span></span>  
  
- <span data-ttu-id="f335b-124">SQL Server Compact obsahuje pouze minimální optimalizace.</span><span class="sxs-lookup"><span data-stu-id="f335b-124">SQL Server Compact provides only a minimal optimizer.</span></span> <span data-ttu-id="f335b-125">Je možné, že několik dotazů může být vypršení časového limitu.</span><span class="sxs-lookup"><span data-stu-id="f335b-125">It is possible that some queries might time out.</span></span>  
  
- <span data-ttu-id="f335b-126">SQL Server Compact nepodporuje částečným vztahem důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="f335b-126">SQL Server Compact does not support partial trust.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f335b-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f335b-127">See also</span></span>

- [<span data-ttu-id="f335b-128">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="f335b-128">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
