---
title: Operace kanálu v .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
ms.openlocfilehash: 693dd1eb0b0b9bb87973eead26a344ed67641e34
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706553"
---
# <a name="pipe-operations-in-net"></a>Operace kanálu v .NET
Kanály poskytují prostředky pro komunikaci mezi procesy. Existují dva typy kanálů:  
  
- Anonymní kanály.  
  
     Anonymní kanály poskytují meziprocesovou komunikaci na místním počítači. Anonymní kanály vyžadují menší režii než pojmenované kanály, ale nabízejí omezené služby. Anonymní kanály jsou jednosměrné a nelze je použít přes síť. Podporují jenom jednu instanci serveru. Anonymní kanály jsou užitečné pro komunikaci mezi vlákny nebo mezi nadřazenými a podřízenými procesy, kde je možné obslužné rutiny kanálu snadno předat podřízenému procesu při jeho vytvoření.  
  
     V rozhraní .NET implementujete anonymní kanály pomocí tříd <xref:System.IO.Pipes.AnonymousPipeServerStream> a <xref:System.IO.Pipes.AnonymousPipeClientStream>.  
  
     Viz [Postupy: použití anonymních kanálů pro místní komunikaci mezi procesy](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).  
  
- Pojmenované kanály.  
  
     Pojmenované kanály poskytují meziprocesovou komunikaci mezi serverem kanálu a jedním nebo několika klienty kanálu. Pojmenované kanály můžou být jednosměrné nebo duplexní. Podporují komunikaci založenou na zprávách a umožňují více klientům současně se současně připojit k procesu serveru pomocí stejného názvu kanálu. Pojmenované kanály také podporují zosobnění, které umožňuje připojujícím se procesům používat na vzdálených serverech vlastní oprávnění.  
  
     V rozhraní .NET implementujete pojmenované kanály pomocí tříd <xref:System.IO.Pipes.NamedPipeServerStream> a <xref:System.IO.Pipes.NamedPipeClientStream>.  
  
     Viz [Postupy: použití pojmenovaných kanálů pro komunikaci mezi procesy sítě](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).  
  
## <a name="see-also"></a>Viz také:

- [Vstup/výstup souborů a datových proudů](../../../docs/standard/io/index.md)
- [Postupy: Místní meziprocesová komunikace pomocí anonymních kanálů](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
- [Postupy: Meziprocesová síťová komunikace pomocí pojmenovaných kanálů](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
