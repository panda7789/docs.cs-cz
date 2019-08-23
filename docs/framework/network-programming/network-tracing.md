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
ms.openlocfilehash: 3d556bc3b8746fe2d05a8e225b91ecf59bd404fd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963932"
---
# <a name="network-tracing-in-the-net-framework"></a>Trasování sítě v rozhraní .NET Framework
Trasování sítě v rozhraní .NET Framework poskytuje přístup k informacím o vyvoláních metody a přenosech v síti generovaných spravovanou aplikací. Tato funkce je užitečná při ladění aplikací během vývoje a také pro analýzu nasazených aplikací. Výstup poskytovaný trasováním sítě je přizpůsobitelný tak, aby podporoval různé scénáře využití v době vývoje a v produkčním prostředí.  
  
 Chcete-li povolit trasování sítě v rozhraní .NET Framework, musíte vybrat cíl výstupu trasování a přidat nastavení konfigurace trasování sítě do konfiguračního souboru aplikace nebo počítače. Popis konfiguračních souborů a způsobu jejich použití najdete v části [konfigurační soubory](../../../docs/framework/configure-apps/index.md). Informace o tom, jak povolit trasování sítě, najdete v tématu [Povolení trasování sítě](../../../docs/framework/network-programming/enabling-network-tracing.md). Informace o nastavení, které je třeba přidat do konfiguračního souboru, najdete v tématu [How to: Nakonfigurujte trasování](../../../docs/framework/network-programming/how-to-configure-network-tracing.md)sítě.  
  
 Pokud je povoleno trasování, můžete zachytit trasovací informace, které jsou výstupem třídy **System.NET** . Pokud členy tříd pro práci se sítěmi generují trasovací informace, je v části Poznámky v dokumentaci knihovny tříd .NET Framework uvedena následující poznámka:  
  
> [!NOTE]
> Tento člen poskytuje trasovací informace, když je ve vaší aplikaci povoleno trasování sítě. Další informace naleznete v tématu Trasování sítě.  
  
## <a name="see-also"></a>Viz také:

- [Povolení trasování sítě](../../../docs/framework/network-programming/enabling-network-tracing.md)
- [Postupy: Konfigurace trasování sítě](../../../docs/framework/network-programming/how-to-configure-network-tracing.md)
- [Interpretace trasování sítě](../../../docs/framework/network-programming/interpreting-network-tracing.md)
- [Trasování a instrumentace aplikací](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
