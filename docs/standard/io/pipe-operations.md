---
title: Operace s pojmenovanými kanály v rozhraní .NET Framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1e0d2747abbacf766ddeda6f41404d8701cbc273
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574363"
---
# <a name="pipe-operations-in-the-net-framework"></a>Operace s pojmenovanými kanály v rozhraní .NET Framework
Kanály poskytují prostředek pro komunikaci mezi procesy. Existují dva typy kanály:  
  
-   Anonymní kanály.  
  
     Anonymní kanály poskytují meziprocesovou komunikaci na místním počítači. Anonymní kanály vyžadují menší režii než pojmenované kanály, ale nabízí omezené služby. Anonymní kanály jsou jednosměrná a nelze je použít přes síť. Podporují pouze jednu instanci serveru. Anonymní kanály jsou užitečné pro komunikaci mezi vlákny nebo mezi nadřazenými a podřízenými procesy kde obslužné rutiny lze snadno předat podřízeného procesu při jeho vytvoření.  
  
     V rozhraní .NET Framework, můžete implementovat anonymní kanály pomocí <xref:System.IO.Pipes.AnonymousPipeServerStream> a <xref:System.IO.Pipes.AnonymousPipeClientStream> třídy.  
  
     V tématu [postupy: místní meziprocesová komunikace pomocí anonymních kanálů](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).  
  
-   Pojmenované kanály.  
  
     Pojmenované kanály poskytují meziprocesovou komunikaci mezi serverem kanálu a jedním nebo několika klienty kanálu. Pojmenované kanály mohou být jednosměrné nebo duplexní. Budou podporovat komunikaci na základě zpráv a povolit více klientů najednou připojit k procesu serveru pomocí kanálu se stejným názvem. Pojmenované kanály také podporují zosobnění, které umožňuje připojování procesy používat vlastní oprávnění na vzdálených serverech.  
  
     V rozhraní .NET Framework, můžete implementovat pojmenované kanály pomocí <xref:System.IO.Pipes.NamedPipeServerStream> a <xref:System.IO.Pipes.NamedPipeClientStream> třídy.  
  
     V tématu [postupy: meziprocesová síťová komunikace pomocí pojmenovaných kanálů](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).  
  
## <a name="see-also"></a>Viz také  
 [Vstup/výstup souborů a streamů](../../../docs/standard/io/index.md)  
 [Postupy: Místní meziprocesová komunikace pomocí anonymních kanálů](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)  
 [Postupy: Meziprocesová síťová komunikace pomocí pojmenovaných kanálů](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
