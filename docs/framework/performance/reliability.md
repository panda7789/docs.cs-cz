---
title: Spolehlivost
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server [.NET Framework]
- managed code, reliability
- reliability [.NET Framework]
- writing reliable code
- code, reliability
ms.assetid: 294aa306-0afe-4cbe-b397-86ba9f1860f8
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3329bff14d2ab395fecfde0f26942b7cb1b9640e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="reliability"></a><span data-ttu-id="7ddcb-102">Spolehlivost</span><span class="sxs-lookup"><span data-stu-id="7ddcb-102">Reliability</span></span>
<span data-ttu-id="7ddcb-103">Je důležité, aby spuštění kódu v serverových prostředích, jako je SQL Server ochranu proti asynchronní výjimky.</span><span class="sxs-lookup"><span data-stu-id="7ddcb-103">It is important that code executing in server environments such as SQL Server protect against asynchronous exceptions.</span></span> <span data-ttu-id="7ddcb-104">Spolehlivost, jak je popsáno v tomto poli, není specifická pro SQL Server, ale pro zápis spolehlivého kódu pro všechny hostitele v rozhraní .NET Framework verze 2.0 prostředí.</span><span class="sxs-lookup"><span data-stu-id="7ddcb-104">Reliability, as discussed here, is not specific to SQL Server but to writing reliable code for any host executing in a .NET Framework version 2.0 environment.</span></span> <span data-ttu-id="7ddcb-105">SQL Server je však první služba, která rozsáhlé používat nových funkcí verze 2.0, tak se používá jako příklad.</span><span class="sxs-lookup"><span data-stu-id="7ddcb-105">However, SQL Server is the first service making extensive use of the new reliability features of version 2.0, so it is used as an example.</span></span>  
  
 <span data-ttu-id="7ddcb-106">Kód spuštěný v systému SQL Server musí řešit přísnější pokyny spolehlivost než ostatní serverových prostředích.</span><span class="sxs-lookup"><span data-stu-id="7ddcb-106">Code running in SQL Server must deal with more stringent reliability guidelines than other server environments.</span></span> <span data-ttu-id="7ddcb-107">Toto je z důvodu konstantní operace systému SQL Server na hranici spotřeby prostředků.</span><span class="sxs-lookup"><span data-stu-id="7ddcb-107">This is due to SQL Server’s steady operation at the edge of resource consumption.</span></span>  <span data-ttu-id="7ddcb-108"><xref:System.OutOfMemoryException>a <xref:System.Threading.ThreadAbortException> výjimky nejsou v prostředí systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7ddcb-108"><xref:System.OutOfMemoryException> and <xref:System.Threading.ThreadAbortException> exceptions are not uncommon in the SQL Server environment.</span></span> <span data-ttu-id="7ddcb-109">Tyto pokyny jsou obecně cílených menší na spolehlivost a další na povolení plně důvěryhodný pro spravovaný kód k selhání řádně face z <xref:System.AppDomain>-úroveň recyklace, která je primární server udržuje konzistence a dostupnost způsobem.</span><span class="sxs-lookup"><span data-stu-id="7ddcb-109">These guidelines in general are focused less on reliability and more on allowing fully trusted managed code to fail gracefully in the face of <xref:System.AppDomain>-level recycling, which is the primary way the server maintains consistency and availability.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7ddcb-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="7ddcb-110">In This Section</span></span>  
 [<span data-ttu-id="7ddcb-111">Programování serveru SQL Server a atributy ochrany hostitele</span><span class="sxs-lookup"><span data-stu-id="7ddcb-111">SQL Server Programming and Host Protection Attributes</span></span>](../../../docs/framework/performance/sql-server-programming-and-host-protection-attributes.md)  
 <span data-ttu-id="7ddcb-112">Popisuje, jak <xref:System.Security.Permissions.HostProtectionAttribute> atribut se systémem SQL Server používá k omezení spuštění spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="7ddcb-112">Describes how the <xref:System.Security.Permissions.HostProtectionAttribute> attribute is used by SQL Server to restrict the execution of managed code.</span></span>  
  
 [<span data-ttu-id="7ddcb-113">Spolehlivost – doporučené postupy</span><span class="sxs-lookup"><span data-stu-id="7ddcb-113">Reliability Best Practices</span></span>](../../../docs/framework/performance/reliability-best-practices.md)  
 <span data-ttu-id="7ddcb-114">Obsahuje pokyny pro psaní kódu, který splňuje požadavky na spolehlivost.</span><span class="sxs-lookup"><span data-stu-id="7ddcb-114">Provides guidelines for writing code that meets reliability requirements.</span></span>  
  
 [<span data-ttu-id="7ddcb-115">Oblasti omezeného provádění</span><span class="sxs-lookup"><span data-stu-id="7ddcb-115">Constrained Execution Regions</span></span>](../../../docs/framework/performance/constrained-execution-regions.md)  
 <span data-ttu-id="7ddcb-116">Popisuje funkce a chování omezené oblasti provádění (CERs).</span><span class="sxs-lookup"><span data-stu-id="7ddcb-116">Describes the function and behavior of constrained execution regions (CERs).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7ddcb-117">Odkaz</span><span class="sxs-lookup"><span data-stu-id="7ddcb-117">Reference</span></span>  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
  
 <xref:System.Security.Permissions.HostProtectionResource>
