---
title: Spolehlivost
ms.date: 03/30/2017
helpviewer_keywords:
- SQL Server [.NET Framework]
- managed code, reliability
- reliability [.NET Framework]
- writing reliable code
- code, reliability
ms.assetid: 294aa306-0afe-4cbe-b397-86ba9f1860f8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: acb84c6617cdffabfe276895f81e7df2b04bb8bb
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046239"
---
# <a name="reliability"></a><span data-ttu-id="2a0bf-102">Spolehlivost</span><span class="sxs-lookup"><span data-stu-id="2a0bf-102">Reliability</span></span>
<span data-ttu-id="2a0bf-103">Je důležité, aby kód spuštěný v prostředích serveru, například SQL Server chránit před asynchronními výjimkami.</span><span class="sxs-lookup"><span data-stu-id="2a0bf-103">It is important that code executing in server environments such as SQL Server protect against asynchronous exceptions.</span></span> <span data-ttu-id="2a0bf-104">Spolehlivost, jak je popsáno zde, není specifická pro SQL Server, ale k psaní spolehlivého kódu pro libovolného hostitele vykonávajícího prostředí .NET Framework verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="2a0bf-104">Reliability, as discussed here, is not specific to SQL Server but to writing reliable code for any host executing in a .NET Framework version 2.0 environment.</span></span> <span data-ttu-id="2a0bf-105">SQL Server je ale první služba, která poskytuje rozsáhlé používání nových funkcí spolehlivosti verze 2,0, takže se používá jako příklad.</span><span class="sxs-lookup"><span data-stu-id="2a0bf-105">However, SQL Server is the first service making extensive use of the new reliability features of version 2.0, so it is used as an example.</span></span>  
  
 <span data-ttu-id="2a0bf-106">Kód spuštěný v SQL Server musí řešit přísnější pravidla spolehlivosti než jiné serverové prostředí.</span><span class="sxs-lookup"><span data-stu-id="2a0bf-106">Code running in SQL Server must deal with more stringent reliability guidelines than other server environments.</span></span> <span data-ttu-id="2a0bf-107">Důvodem je SQL Server stabilní operace na hranici spotřeby prostředků.</span><span class="sxs-lookup"><span data-stu-id="2a0bf-107">This is due to SQL Server’s steady operation at the edge of resource consumption.</span></span>  <span data-ttu-id="2a0bf-108"><xref:System.OutOfMemoryException>a <xref:System.Threading.ThreadAbortException> výjimky nejsou v prostředí SQL Server Neběžné.</span><span class="sxs-lookup"><span data-stu-id="2a0bf-108"><xref:System.OutOfMemoryException> and <xref:System.Threading.ThreadAbortException> exceptions are not uncommon in the SQL Server environment.</span></span> <span data-ttu-id="2a0bf-109">Tyto obecné pokyny jsou obecně zaměřené na spolehlivost a další informace o tom, že plně důvěryhodný spravovaný kód může řádně selhat při <xref:System.AppDomain>recyklaci na úrovni, což je primární způsob, jakým server udržuje konzistenci a dostupnost.</span><span class="sxs-lookup"><span data-stu-id="2a0bf-109">These guidelines in general are focused less on reliability and more on allowing fully trusted managed code to fail gracefully in the face of <xref:System.AppDomain>-level recycling, which is the primary way the server maintains consistency and availability.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2a0bf-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2a0bf-110">In This Section</span></span>  
 [<span data-ttu-id="2a0bf-111">Programování serveru SQL Server a atributy ochrany hostitele</span><span class="sxs-lookup"><span data-stu-id="2a0bf-111">SQL Server Programming and Host Protection Attributes</span></span>](sql-server-programming-and-host-protection-attributes.md)  
 <span data-ttu-id="2a0bf-112">Popisuje, <xref:System.Security.Permissions.HostProtectionAttribute> jak je atribut použit SQL Server k omezení spuštění spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="2a0bf-112">Describes how the <xref:System.Security.Permissions.HostProtectionAttribute> attribute is used by SQL Server to restrict the execution of managed code.</span></span>  
  
 [<span data-ttu-id="2a0bf-113">Spolehlivost – doporučené postupy</span><span class="sxs-lookup"><span data-stu-id="2a0bf-113">Reliability Best Practices</span></span>](reliability-best-practices.md)  
 <span data-ttu-id="2a0bf-114">Poskytuje pokyny pro psaní kódu, který splňuje požadavky na spolehlivost.</span><span class="sxs-lookup"><span data-stu-id="2a0bf-114">Provides guidelines for writing code that meets reliability requirements.</span></span>  
  
 [<span data-ttu-id="2a0bf-115">Oblasti omezeného provádění</span><span class="sxs-lookup"><span data-stu-id="2a0bf-115">Constrained Execution Regions</span></span>](constrained-execution-regions.md)  
 <span data-ttu-id="2a0bf-116">Popisuje funkci a chování omezených oblastí provádění (CERs).</span><span class="sxs-lookup"><span data-stu-id="2a0bf-116">Describes the function and behavior of constrained execution regions (CERs).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2a0bf-117">Reference</span><span class="sxs-lookup"><span data-stu-id="2a0bf-117">Reference</span></span>  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
  
 <xref:System.Security.Permissions.HostProtectionResource>
