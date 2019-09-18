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
# <a name="reliability"></a>Spolehlivost
Je důležité, aby kód spuštěný v prostředích serveru, například SQL Server chránit před asynchronními výjimkami. Spolehlivost, jak je popsáno zde, není specifická pro SQL Server, ale k psaní spolehlivého kódu pro libovolného hostitele vykonávajícího prostředí .NET Framework verze 2,0. SQL Server je ale první služba, která poskytuje rozsáhlé používání nových funkcí spolehlivosti verze 2,0, takže se používá jako příklad.  
  
 Kód spuštěný v SQL Server musí řešit přísnější pravidla spolehlivosti než jiné serverové prostředí. Důvodem je SQL Server stabilní operace na hranici spotřeby prostředků.  <xref:System.OutOfMemoryException>a <xref:System.Threading.ThreadAbortException> výjimky nejsou v prostředí SQL Server Neběžné. Tyto obecné pokyny jsou obecně zaměřené na spolehlivost a další informace o tom, že plně důvěryhodný spravovaný kód může řádně selhat při <xref:System.AppDomain>recyklaci na úrovni, což je primární způsob, jakým server udržuje konzistenci a dostupnost.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Programování serveru SQL Server a atributy ochrany hostitele](sql-server-programming-and-host-protection-attributes.md)  
 Popisuje, <xref:System.Security.Permissions.HostProtectionAttribute> jak je atribut použit SQL Server k omezení spuštění spravovaného kódu.  
  
 [Spolehlivost – doporučené postupy](reliability-best-practices.md)  
 Poskytuje pokyny pro psaní kódu, který splňuje požadavky na spolehlivost.  
  
 [Oblasti omezeného provádění](constrained-execution-regions.md)  
 Popisuje funkci a chování omezených oblastí provádění (CERs).  
  
## <a name="reference"></a>Reference  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
  
 <xref:System.Security.Permissions.HostProtectionResource>
