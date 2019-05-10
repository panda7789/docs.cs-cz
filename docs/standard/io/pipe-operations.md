---
title: Operace s pojmenovanými kanály v rozhraní .NET
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
ms.openlocfilehash: 0f02f7a8a327e117b92ef826b8dcd7fc742c9b4c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647812"
---
# <a name="pipe-operations-in-net"></a>Operace s pojmenovanými kanály v rozhraní .NET
Kanály poskytují způsob meziprocesová komunikace. Existují dva druhy kanály:  
  
- Anonymní kanály.  
  
     Anonymní kanály poskytují meziprocesovou komunikaci na místním počítači. Anonymní kanály menší nákladovou režii než pojmenované kanály, ale nabízí omezené služby. Anonymní kanály jsou jednosměrná a nelze použít přes síť. Podporují pouze jednu instanci serveru. Anonymní kanály jsou užitečné pro komunikaci mezi vlákny, nebo mezi nadřazenými a podřízenými procesy, kde popisovače kanálu lze snadno předat podřízený proces při jeho vytvoření.  
  
     V rozhraní .NET, implementovat anonymní kanály pomocí <xref:System.IO.Pipes.AnonymousPipeServerStream> a <xref:System.IO.Pipes.AnonymousPipeClientStream> třídy.  
  
     Zobrazit [jak: Místní meziprocesová komunikace pomocí anonymních kanálů](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).  
  
- Pojmenované kanály.  
  
     Pojmenované kanály poskytují meziprocesovou komunikaci mezi serverem kanálu a jedním nebo několika klienty kanálu. Pojmenované kanály mohou být jednosměrné nebo obousměrné. Tyto mohly podporovat komunikaci založenou na zprávách a povolit víc klientů současně připojit k procesu serveru pomocí kanálu se stejným názvem. Pojmenované kanály podporují také zosobnění, což umožňuje připojujícím se procesům použít vlastní oprávnění na vzdálených serverech.  
  
     V rozhraní .NET, implementovat pojmenované kanály pomocí <xref:System.IO.Pipes.NamedPipeServerStream> a <xref:System.IO.Pipes.NamedPipeClientStream> třídy.  
  
     Zobrazit [jak: Meziprocesová síťová komunikace pomocí pojmenovaných kanálů](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).  
  
## <a name="see-also"></a>Viz také:

- [Vstup/výstup souborů a streamů](../../../docs/standard/io/index.md)
- [Postupy: Místní meziprocesová komunikace pomocí anonymních kanálů](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
- [Postupy: Použití pojmenované kanály meziprocesová síťová komunikace](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
