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
ms.openlocfilehash: a634cb87a5f25b520e5fe6fd5b39eae861120a28
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278685"
---
# <a name="pipe-operations-in-net"></a>Operace kanálu v .NET
Kanály poskytují prostředky pro komunikaci mezi procesy. Existují dva typy kanálů:  
  
- Anonymní kanály.  
  
     Anonymní kanály poskytují meziprocesovou komunikaci na místním počítači. Anonymní kanály vyžadují menší režii než pojmenované kanály, ale nabízejí omezené služby. Anonymní kanály jsou jednosměrné a nelze je použít přes síť. Podporují jenom jednu instanci serveru. Anonymní kanály jsou užitečné pro komunikaci mezi vlákny nebo mezi nadřazenými a podřízenými procesy, kde je možné obslužné rutiny kanálu snadno předat podřízenému procesu při jeho vytvoření.  
  
     V rozhraní .NET implementujete anonymní kanály pomocí <xref:System.IO.Pipes.AnonymousPipeServerStream> <xref:System.IO.Pipes.AnonymousPipeClientStream> tříd a.  
  
     Viz [Postupy: použití anonymních kanálů pro místní komunikaci mezi procesy](how-to-use-anonymous-pipes-for-local-interprocess-communication.md).  
  
- Pojmenované kanály.  
  
     Pojmenované kanály poskytují meziprocesovou komunikaci mezi serverem kanálu a jedním nebo několika klienty kanálu. Pojmenované kanály můžou být jednosměrné nebo duplexní. Podporují komunikaci založenou na zprávách a umožňují více klientům současně se současně připojit k procesu serveru pomocí stejného názvu kanálu. Pojmenované kanály také podporují zosobnění, které umožňuje připojujícím se procesům používat na vzdálených serverech vlastní oprávnění.  
  
     V rozhraní .NET implementujete pojmenované kanály pomocí <xref:System.IO.Pipes.NamedPipeServerStream> <xref:System.IO.Pipes.NamedPipeClientStream> tříd a.  
  
     Viz [Postupy: použití pojmenovaných kanálů pro komunikaci mezi procesy sítě](how-to-use-named-pipes-for-network-interprocess-communication.md).  
  
## <a name="see-also"></a>Viz také

- [Vstupně-výstupní operace se soubory a datovým proudem](index.md)
- [Postupy: Místní meziprocesová komunikace pomocí anonymních kanálů](how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
- [Postupy: Meziprocesová síťová komunikace pomocí pojmenovaných kanálů](how-to-use-named-pipes-for-network-interprocess-communication.md)
