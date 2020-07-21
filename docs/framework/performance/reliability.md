---
title: Spolehlivost
description: Pochopení spolehlivosti v .NET. Chraňte proti asynchronním výjimkám hostitelů spouštěných v rozhraní .NET, například SQL Server.
ms.date: 03/30/2017
helpviewer_keywords:
- SQL Server [.NET Framework]
- managed code, reliability
- reliability [.NET Framework]
- writing reliable code
- code, reliability
ms.assetid: 294aa306-0afe-4cbe-b397-86ba9f1860f8
ms.openlocfilehash: ce9ffbb7f58c2f5dc016c56c0e2ce13b45c30f26
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474251"
---
# <a name="reliability"></a><span data-ttu-id="e229c-104">Spolehlivost</span><span class="sxs-lookup"><span data-stu-id="e229c-104">Reliability</span></span>
<span data-ttu-id="e229c-105">Je důležité, aby kód spuštěný v prostředích serveru, například SQL Server chránit před asynchronními výjimkami.</span><span class="sxs-lookup"><span data-stu-id="e229c-105">It is important that code executing in server environments such as SQL Server protect against asynchronous exceptions.</span></span> <span data-ttu-id="e229c-106">Spolehlivost, jak je popsáno zde, není specifická pro SQL Server, ale k psaní spolehlivého kódu pro libovolného hostitele vykonávajícího prostředí .NET Framework verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="e229c-106">Reliability, as discussed here, is not specific to SQL Server but to writing reliable code for any host executing in a .NET Framework version 2.0 environment.</span></span> <span data-ttu-id="e229c-107">SQL Server je ale první služba, která poskytuje rozsáhlé používání nových funkcí spolehlivosti verze 2,0, takže se používá jako příklad.</span><span class="sxs-lookup"><span data-stu-id="e229c-107">However, SQL Server is the first service making extensive use of the new reliability features of version 2.0, so it is used as an example.</span></span>  
  
 <span data-ttu-id="e229c-108">Kód spuštěný v SQL Server musí řešit přísnější pravidla spolehlivosti než jiné serverové prostředí.</span><span class="sxs-lookup"><span data-stu-id="e229c-108">Code running in SQL Server must deal with more stringent reliability guidelines than other server environments.</span></span> <span data-ttu-id="e229c-109">Důvodem je SQL Server stabilní operace na hranici spotřeby prostředků.</span><span class="sxs-lookup"><span data-stu-id="e229c-109">This is due to SQL Server’s steady operation at the edge of resource consumption.</span></span>  <span data-ttu-id="e229c-110"><xref:System.OutOfMemoryException>a <xref:System.Threading.ThreadAbortException> výjimky nejsou v prostředí SQL Server Neběžné.</span><span class="sxs-lookup"><span data-stu-id="e229c-110"><xref:System.OutOfMemoryException> and <xref:System.Threading.ThreadAbortException> exceptions are not uncommon in the SQL Server environment.</span></span> <span data-ttu-id="e229c-111">Tyto obecné pokyny jsou obecně zaměřené na spolehlivost a další informace o tom, že plně důvěryhodný spravovaný kód může řádně selhat při <xref:System.AppDomain> recyklaci na úrovni, což je primární způsob, jakým server udržuje konzistenci a dostupnost.</span><span class="sxs-lookup"><span data-stu-id="e229c-111">These guidelines in general are focused less on reliability and more on allowing fully trusted managed code to fail gracefully in the face of <xref:System.AppDomain>-level recycling, which is the primary way the server maintains consistency and availability.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e229c-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="e229c-112">In This Section</span></span>  
 [<span data-ttu-id="e229c-113">Programování serveru SQL Server a atributy ochrany hostitele</span><span class="sxs-lookup"><span data-stu-id="e229c-113">SQL Server Programming and Host Protection Attributes</span></span>](sql-server-programming-and-host-protection-attributes.md)  
 <span data-ttu-id="e229c-114">Popisuje, jak <xref:System.Security.Permissions.HostProtectionAttribute> je atribut použit SQL Server k omezení spuštění spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="e229c-114">Describes how the <xref:System.Security.Permissions.HostProtectionAttribute> attribute is used by SQL Server to restrict the execution of managed code.</span></span>  
  
 [<span data-ttu-id="e229c-115">Spolehlivost – doporučené postupy</span><span class="sxs-lookup"><span data-stu-id="e229c-115">Reliability Best Practices</span></span>](reliability-best-practices.md)  
 <span data-ttu-id="e229c-116">Poskytuje pokyny pro psaní kódu, který splňuje požadavky na spolehlivost.</span><span class="sxs-lookup"><span data-stu-id="e229c-116">Provides guidelines for writing code that meets reliability requirements.</span></span>  
  
 [<span data-ttu-id="e229c-117">Oblasti omezeného provádění</span><span class="sxs-lookup"><span data-stu-id="e229c-117">Constrained Execution Regions</span></span>](constrained-execution-regions.md)  
 <span data-ttu-id="e229c-118">Popisuje funkci a chování omezených oblastí provádění (CERs).</span><span class="sxs-lookup"><span data-stu-id="e229c-118">Describes the function and behavior of constrained execution regions (CERs).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e229c-119">Reference</span><span class="sxs-lookup"><span data-stu-id="e229c-119">Reference</span></span>  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
  
 <xref:System.Security.Permissions.HostProtectionResource>
