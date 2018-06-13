---
title: 'Povolení JIT – ladění Attach '
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 67db256f4c328b12d6cc30abfbe5d5ccc12e8b0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397829"
---
# <a name="enabling-jit-attach-debugging"></a>Povolení JIT – ladění Attach 
JIT – připojené ladění je fráze používají k popisu připojení ladicího programu procesu, když dojde k chybám, nebo ji můžete aktivovat konkrétní metody nebo funkce.  
  
 JIT – připojené ladění se používá za následujících podmínek chyby:  
  
-   Nezpracované výjimky (v nativního a spravovaného kódu).  
  
-   <xref:System.Environment.FailFast%2A?displayProperty=nameWithType> Metoda nebo [RaiseFailFastException](http://go.microsoft.com/fwlink/?LinkId=182107) – funkce (rodiny Windows 7).  
  
-   Závažné chyby za běhu.  
  
 JIT – připojené ladění se aktivuje také při volání těchto metod a funkce:  
  
-   <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> Metoda.  
  
-   <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> Metoda.  
  
-   [Debugbreak –](http://go.microsoft.com/fwlink/?LinkId=182106) – funkce (Win32).  
  
 Před [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], rozhraní .NET Framework poskytuje klíče registru samostatné pro řízení chování nativní a spravovaná ladicí programy. Od verze [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], je ovládací prvek konsolidovány do klíče registru jednu: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug. Hodnoty, které můžete nastavit pro tento klíč určit, zda je volána ladicí program a pokud ano, zda je volána, dialogové okno, které vyžaduje interakci uživatele. Informace o nastavení tohoto klíče registru najdete v tématu [konfigurace automatické ladění](http://go.microsoft.com/fwlink/?LinkId=181767).  
  
## <a name="see-also"></a>Viz také  
 [Ladění, trasování a profilace](../../../docs/framework/debug-trace-profile/index.md)  
 [Usnadnění ladění obrázku](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)  
 [Povolení profilace](http://msdn.microsoft.com/library/3b669676-f0e0-4ebf-8674-68986dd2020d)
