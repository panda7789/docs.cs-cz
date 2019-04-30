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
# <a name="reliability"></a>Spolehlivost
Je důležité, že spuštění kódu v serverových prostředích, jako je SQL Server chránit proti asynchronní výjimky. Spolehlivost, jak je popsáno zde není specifická pro systém SQL Server, ale na zápis spolehlivého kódu pro všechny hostitele, provádí se v rozhraní .NET Framework verze 2.0 prostředí. SQL Server je však první služba, která rozsáhlé využít nové funkce spolehlivost verze 2.0, tak se používá jako příklad.  
  
 Kód spuštěný v systému SQL Server musí čelit přísnější pravidla spolehlivosti než jiné prostředí serveru. To je způsobeno nepřetržitý provoz systému SQL Server na hraničních zařízeních spotřeby prostředků.  <xref:System.OutOfMemoryException> a <xref:System.Threading.ThreadAbortException> výjimky nejsou výjimkou v prostředí systému SQL Server. Tyto pokyny jsou obecně cílené méně na spolehlivost a další na povolení plně důvěryhodné spravovaného kódu do řádně selhat z face <xref:System.AppDomain>– úroveň recyklaci, což je hlavní způsob, jak server udržuje konzistenci a dostupnost.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Programování serveru SQL Server a atributy ochrany hostitele](../../../docs/framework/performance/sql-server-programming-and-host-protection-attributes.md)  
 Popisuje, jak <xref:System.Security.Permissions.HostProtectionAttribute> atribut systému SQL Server používá k omezení spuštění spravovaného kódu.  
  
 [Spolehlivost – doporučené postupy](../../../docs/framework/performance/reliability-best-practices.md)  
 Obsahuje pokyny pro psaní kódu, který splňuje požadavky na spolehlivost.  
  
 [Oblasti omezeného provádění](../../../docs/framework/performance/constrained-execution-regions.md)  
 Popisuje funkce a chování oblasti omezeného provádění (CERs).  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
  
 <xref:System.Security.Permissions.HostProtectionResource>
