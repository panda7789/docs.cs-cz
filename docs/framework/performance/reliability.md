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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395408"
---
# <a name="reliability"></a>Spolehlivost
Je důležité, aby spuštění kódu v serverových prostředích, jako je SQL Server ochranu proti asynchronní výjimky. Spolehlivost, jak je popsáno v tomto poli, není specifická pro SQL Server, ale pro zápis spolehlivého kódu pro všechny hostitele v rozhraní .NET Framework verze 2.0 prostředí. SQL Server je však první služba, která rozsáhlé používat nových funkcí verze 2.0, tak se používá jako příklad.  
  
 Kód spuštěný v systému SQL Server musí řešit přísnější pokyny spolehlivost než ostatní serverových prostředích. Toto je z důvodu konstantní operace systému SQL Server na hranici spotřeby prostředků.  <xref:System.OutOfMemoryException> a <xref:System.Threading.ThreadAbortException> výjimky nejsou v prostředí systému SQL Server. Tyto pokyny jsou obecně cílených menší na spolehlivost a další na povolení plně důvěryhodný pro spravovaný kód k selhání řádně face z <xref:System.AppDomain>-úroveň recyklace, která je primární server udržuje konzistence a dostupnost způsobem.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Programování serveru SQL Server a atributy ochrany hostitele](../../../docs/framework/performance/sql-server-programming-and-host-protection-attributes.md)  
 Popisuje, jak <xref:System.Security.Permissions.HostProtectionAttribute> atribut se systémem SQL Server používá k omezení spuštění spravovaného kódu.  
  
 [Spolehlivost – doporučené postupy](../../../docs/framework/performance/reliability-best-practices.md)  
 Obsahuje pokyny pro psaní kódu, který splňuje požadavky na spolehlivost.  
  
 [Oblasti omezeného provádění](../../../docs/framework/performance/constrained-execution-regions.md)  
 Popisuje funkce a chování omezené oblasti provádění (CERs).  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
  
 <xref:System.Security.Permissions.HostProtectionResource>
