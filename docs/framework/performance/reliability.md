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
ms.openlocfilehash: 3b00ba0fdf732a864fb4fb757c6012a3d36740b2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949289"
---
# <a name="reliability"></a><span data-ttu-id="19efb-102">Spolehlivost</span><span class="sxs-lookup"><span data-stu-id="19efb-102">Reliability</span></span>
<span data-ttu-id="19efb-103">Je důležité, že spuštění kódu v serverových prostředích, jako je SQL Server chránit proti asynchronní výjimky.</span><span class="sxs-lookup"><span data-stu-id="19efb-103">It is important that code executing in server environments such as SQL Server protect against asynchronous exceptions.</span></span> <span data-ttu-id="19efb-104">Spolehlivost, jak je popsáno zde není specifická pro systém SQL Server, ale na zápis spolehlivého kódu pro všechny hostitele, provádí se v rozhraní .NET Framework verze 2.0 prostředí.</span><span class="sxs-lookup"><span data-stu-id="19efb-104">Reliability, as discussed here, is not specific to SQL Server but to writing reliable code for any host executing in a .NET Framework version 2.0 environment.</span></span> <span data-ttu-id="19efb-105">SQL Server je však první služba, která rozsáhlé využít nové funkce spolehlivost verze 2.0, tak se používá jako příklad.</span><span class="sxs-lookup"><span data-stu-id="19efb-105">However, SQL Server is the first service making extensive use of the new reliability features of version 2.0, so it is used as an example.</span></span>  
  
 <span data-ttu-id="19efb-106">Kód spuštěný v systému SQL Server musí čelit přísnější pravidla spolehlivosti než jiné prostředí serveru.</span><span class="sxs-lookup"><span data-stu-id="19efb-106">Code running in SQL Server must deal with more stringent reliability guidelines than other server environments.</span></span> <span data-ttu-id="19efb-107">To je způsobeno nepřetržitý provoz systému SQL Server na hraničních zařízeních spotřeby prostředků.</span><span class="sxs-lookup"><span data-stu-id="19efb-107">This is due to SQL Server’s steady operation at the edge of resource consumption.</span></span>  <span data-ttu-id="19efb-108"><xref:System.OutOfMemoryException> a <xref:System.Threading.ThreadAbortException> výjimky nejsou výjimkou v prostředí systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="19efb-108"><xref:System.OutOfMemoryException> and <xref:System.Threading.ThreadAbortException> exceptions are not uncommon in the SQL Server environment.</span></span> <span data-ttu-id="19efb-109">Tyto pokyny jsou obecně cílené méně na spolehlivost a další na povolení plně důvěryhodné spravovaného kódu do řádně selhat z face <xref:System.AppDomain>– úroveň recyklaci, což je hlavní způsob, jak server udržuje konzistenci a dostupnost.</span><span class="sxs-lookup"><span data-stu-id="19efb-109">These guidelines in general are focused less on reliability and more on allowing fully trusted managed code to fail gracefully in the face of <xref:System.AppDomain>-level recycling, which is the primary way the server maintains consistency and availability.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="19efb-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="19efb-110">In This Section</span></span>  
 [<span data-ttu-id="19efb-111">Programování serveru SQL Server a atributy ochrany hostitele</span><span class="sxs-lookup"><span data-stu-id="19efb-111">SQL Server Programming and Host Protection Attributes</span></span>](../../../docs/framework/performance/sql-server-programming-and-host-protection-attributes.md)  
 <span data-ttu-id="19efb-112">Popisuje, jak <xref:System.Security.Permissions.HostProtectionAttribute> atribut systému SQL Server používá k omezení spuštění spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="19efb-112">Describes how the <xref:System.Security.Permissions.HostProtectionAttribute> attribute is used by SQL Server to restrict the execution of managed code.</span></span>  
  
 [<span data-ttu-id="19efb-113">Spolehlivost – doporučené postupy</span><span class="sxs-lookup"><span data-stu-id="19efb-113">Reliability Best Practices</span></span>](../../../docs/framework/performance/reliability-best-practices.md)  
 <span data-ttu-id="19efb-114">Obsahuje pokyny pro psaní kódu, který splňuje požadavky na spolehlivost.</span><span class="sxs-lookup"><span data-stu-id="19efb-114">Provides guidelines for writing code that meets reliability requirements.</span></span>  
  
 [<span data-ttu-id="19efb-115">Oblasti omezeného provádění</span><span class="sxs-lookup"><span data-stu-id="19efb-115">Constrained Execution Regions</span></span>](../../../docs/framework/performance/constrained-execution-regions.md)  
 <span data-ttu-id="19efb-116">Popisuje funkce a chování oblasti omezeného provádění (CERs).</span><span class="sxs-lookup"><span data-stu-id="19efb-116">Describes the function and behavior of constrained execution regions (CERs).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="19efb-117">Odkaz</span><span class="sxs-lookup"><span data-stu-id="19efb-117">Reference</span></span>  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
  
 <xref:System.Security.Permissions.HostProtectionResource>
