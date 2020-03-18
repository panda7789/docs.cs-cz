---
title: Operace potrubí v rozhraní .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
ms.openlocfilehash: 693dd1eb0b0b9bb87973eead26a344ed67641e34
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75706553"
---
# <a name="pipe-operations-in-net"></a>Operace potrubí v rozhraní .NET
Potrubí poskytují prostředky pro meziprocesovou komunikaci. Existují dva typy trubek:  
  
- Anonymní trubky.  
  
     Anonymní kanály poskytují meziprocesovou komunikaci na místním počítači. Anonymní kanály vyžadují menší režii než pojmenované kanály, ale nabízejí omezené služby. Anonymní kanály jsou jednosměrné a nelze je používat v síti. Podporují pouze jednu instanci serveru. Anonymní kanály jsou užitečné pro komunikaci mezi podprocesy nebo mezi nadřazené a podřízené procesy, kde popisovače kanálu lze snadno předat podřízenému procesu při jeho vytvoření.  
  
     V rozhraní .NET implementovat anonymní <xref:System.IO.Pipes.AnonymousPipeServerStream> <xref:System.IO.Pipes.AnonymousPipeClientStream> kanály pomocí a třídy.  
  
     Viz [Postup: Použití anonymních kanálů pro místní meziprocesovou komunikaci](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).  
  
- Pojmenované kanály.  
  
     Pojmenované kanály poskytují meziprocesovou komunikaci mezi serverem kanálu a jedním nebo několika klienty kanálu. Pojmenované kanály mohou být jednosměrné nebo duplexní. Podporují komunikaci založenou na textech a umožňují více klientům připojit se současně k procesu serveru pomocí stejného názvu kanálu. Pojmenované kanály také podporují zosobnění, což umožňuje připojovacím procesům používat vlastní oprávnění na vzdálených serverech.  
  
     V rozhraní .NET implementujete <xref:System.IO.Pipes.NamedPipeServerStream> <xref:System.IO.Pipes.NamedPipeClientStream> pojmenované kanály pomocí tříd a.  
  
     Viz [Postup: Použití pojmenovaných kanálů pro meziprocesovou komunikaci v síti](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).  
  
## <a name="see-also"></a>Viz také

- [I/O souborů a proudů](../../../docs/standard/io/index.md)
- [Postupy: Místní meziprocesová komunikace pomocí anonymních kanálů](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
- [Postupy: Meziprocesová síťová komunikace pomocí pojmenovaných kanálů](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
