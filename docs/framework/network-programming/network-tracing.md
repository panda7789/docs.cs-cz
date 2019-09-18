---
title: Trasování sítě v rozhraní .NET Framework
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
ms.openlocfilehash: afb9c3a04258b543e373b6973e576f71f90d7003
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047597"
---
# <a name="network-tracing-in-the-net-framework"></a>Trasování sítě v rozhraní .NET Framework
Trasování sítě v rozhraní .NET Framework poskytuje přístup k informacím o vyvoláních metody a přenosech v síti generovaných spravovanou aplikací. Tato funkce je užitečná při ladění aplikací během vývoje a také pro analýzu nasazených aplikací. Výstup poskytovaný trasováním sítě je přizpůsobitelný tak, aby podporoval různé scénáře využití v době vývoje a v produkčním prostředí.  
  
 Chcete-li povolit trasování sítě v rozhraní .NET Framework, musíte vybrat cíl výstupu trasování a přidat nastavení konfigurace trasování sítě do konfiguračního souboru aplikace nebo počítače. Popis konfiguračních souborů a způsobu jejich použití najdete v části [konfigurační soubory](../configure-apps/index.md). Informace o tom, jak povolit trasování sítě, najdete v tématu [Povolení trasování sítě](enabling-network-tracing.md). Informace o nastavení, které je třeba přidat do konfiguračního souboru, najdete v tématu [How to: Nakonfigurujte trasování](how-to-configure-network-tracing.md)sítě.  
  
 Pokud je povoleno trasování, můžete zachytit trasovací informace, které jsou výstupem třídy **System.NET** . Pokud členy tříd pro práci se sítěmi generují trasovací informace, je v části Poznámky v dokumentaci knihovny tříd .NET Framework uvedena následující poznámka:  
  
> [!NOTE]
> Tento člen poskytuje trasovací informace, když je ve vaší aplikaci povoleno trasování sítě. Další informace naleznete v tématu Trasování sítě.  
  
## <a name="see-also"></a>Viz také:

- [Povolení trasování sítě](enabling-network-tracing.md)
- [Postupy: Konfigurace trasování sítě](how-to-configure-network-tracing.md)
- [Interpretace trasování sítě](interpreting-network-tracing.md)
- [Trasování a instrumentace aplikací](../debug-trace-profile/tracing-and-instrumenting-applications.md)
