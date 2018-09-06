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
ms.openlocfilehash: fdc12091a377a118dc533e5f299fa4833af64baf
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43879663"
---
# <a name="pipe-operations-in-the-net-framework"></a>Operace s pojmenovanými kanály v rozhraní .NET Framework
Kanály poskytují způsob meziprocesová komunikace. Existují dva druhy kanály:  
  
-   Anonymní kanály.  
  
     Anonymní kanály poskytují meziprocesovou komunikaci na místním počítači. Anonymní kanály menší nákladovou režii než pojmenované kanály, ale nabízí omezené služby. Anonymní kanály jsou jednosměrná a nelze použít přes síť. Podporují pouze jednu instanci serveru. Anonymní kanály jsou užitečné pro komunikaci mezi vlákny, nebo mezi nadřazenými a podřízenými procesy, kde popisovače kanálu lze snadno předat podřízený proces při jeho vytvoření.  
  
     V rozhraní .NET Framework, implementovat anonymní kanály pomocí <xref:System.IO.Pipes.AnonymousPipeServerStream> a <xref:System.IO.Pipes.AnonymousPipeClientStream> třídy.  
  
     Zobrazit [postupy: místní meziprocesová komunikace pomocí anonymních kanálů](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).  
  
-   Pojmenované kanály.  
  
     Pojmenované kanály poskytují meziprocesovou komunikaci mezi serverem kanálu a jedním nebo několika klienty kanálu. Pojmenované kanály mohou být jednosměrné nebo obousměrné. Tyto mohly podporovat komunikaci založenou na zprávách a povolit víc klientů současně připojit k procesu serveru pomocí kanálu se stejným názvem. Pojmenované kanály podporují také zosobnění, což umožňuje připojujícím se procesům použít vlastní oprávnění na vzdálených serverech.  
  
     V rozhraní .NET Framework, implementovat pojmenované kanály pomocí <xref:System.IO.Pipes.NamedPipeServerStream> a <xref:System.IO.Pipes.NamedPipeClientStream> třídy.  
  
     Zobrazit [postupy: meziprocesová síťová komunikace pomocí pojmenovaných kanálů](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).  
  
## <a name="see-also"></a>Viz také:

- [Vstup/výstup souborů a streamů](../../../docs/standard/io/index.md)  
- [Postupy: Místní meziprocesová komunikace pomocí anonymních kanálů](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)  
- [Postupy: Meziprocesová síťová komunikace pomocí pojmenovaných kanálů](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
