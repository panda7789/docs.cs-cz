---
title: Trasování sítě v rozhraní .NET Framework
description: Přečtěte si o trasování sítě v .NET Framework, které poskytuje informace o vyvoláních metod a síťových přenosech pro spravovanou aplikaci.
ms.date: 03/30/2017
helpviewer_keywords:
- debugging [.NET Framework], network tracing
- methods, network tracing
- Networking
- trace enabled debugging
- network tracing, about network tracing
- network tracing
- network, network tracing
- traffic tracing
- tracing [.NET Framework], network
- deploying applications [.NET Framework], network traffic
- capturing network traffic
- Internet, network tracing
- Network Resources
- output, network tracing
- method invocations
ms.assetid: e993b7c3-087f-45d8-9c02-9dded936d804
ms.openlocfilehash: 172f8ce4a50fe9294ee34cf65c0a39eb2f29badc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502246"
---
# <a name="network-tracing-in-the-net-framework"></a>Trasování sítě v rozhraní .NET Framework
Trasování sítě v rozhraní .NET Framework poskytuje přístup k informacím o vyvoláních metody a přenosech v síti generovaných spravovanou aplikací. Tato funkce je užitečná při ladění aplikací během vývoje a také pro analýzu nasazených aplikací. Výstup poskytovaný trasováním sítě je přizpůsobitelný tak, aby podporoval různé scénáře využití v době vývoje a v produkčním prostředí.  
  
 Chcete-li povolit trasování sítě v rozhraní .NET Framework, musíte vybrat cíl výstupu trasování a přidat nastavení konfigurace trasování sítě do konfiguračního souboru aplikace nebo počítače. Popis konfiguračních souborů a způsobu jejich použití najdete v části [konfigurační soubory](../configure-apps/index.md). Informace o tom, jak povolit trasování sítě, najdete v tématu [Povolení trasování sítě](enabling-network-tracing.md). Informace o nastavení, které je třeba přidat do konfiguračního souboru, naleznete v tématu [How to: Configure Network Tracing](how-to-configure-network-tracing.md).  
  
 Pokud je povoleno trasování, můžete zachytit trasovací informace, které jsou výstupem třídy **System.NET** . Pokud členy tříd pro práci se sítěmi generují trasovací informace, je v části Poznámky v dokumentaci knihovny tříd .NET Framework uvedena následující poznámka:  
  
> [!NOTE]
> Tento člen poskytuje trasovací informace, když je ve vaší aplikaci povoleno trasování sítě. Další informace naleznete v tématu Trasování sítě.  
  
## <a name="see-also"></a>Viz také:

- [Povolení trasování sítě](enabling-network-tracing.md)
- [Postupy: Konfigurace trasování sítě](how-to-configure-network-tracing.md)
- [Interpretace trasování sítě](interpreting-network-tracing.md)
- [Trasování a instrumentace aplikací](../debug-trace-profile/tracing-and-instrumenting-applications.md)
