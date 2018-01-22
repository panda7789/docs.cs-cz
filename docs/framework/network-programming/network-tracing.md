---
title: "Trasování sítě v rozhraní .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 7ef5698300d7d3cb333bc7d58a782c02823718d8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="network-tracing-in-the-net-framework"></a>Trasování sítě v rozhraní .NET Framework
Trasování sítě v rozhraní .NET Framework poskytuje přístup k informacím o vyvoláních metody a přenosech v síti generovaných spravovanou aplikací. Tato funkce je užitečná při ladění aplikací během vývoje a také pro analýzu nasazených aplikací. Výstup poskytovaný trasováním sítě je přizpůsobitelný tak, aby podporoval různé scénáře využití v době vývoje a v produkčním prostředí.  
  
 Chcete-li povolit trasování sítě v rozhraní .NET Framework, musíte vybrat cíl výstupu trasování a přidat nastavení konfigurace trasování sítě do konfiguračního souboru aplikace nebo počítače. Popis konfiguračních souborů a způsob jejich použití naleznete v části [konfigurační soubory](../../../docs/framework/configure-apps/index.md). Informace o tom, jak povolit trasování sítě najdete v tématu [povolení trasování sítě](../../../docs/framework/network-programming/enabling-network-tracing.md). Informace o nastaveních, která je nutné přidat do konfiguračního souboru najdete v tématu [postupy: Konfigurace trasování sítě](../../../docs/framework/network-programming/how-to-configure-network-tracing.md).  
  
 Pokud je povoleno sledování, můžete zaznamenávat informace trasování, který je výstupem **System.Net** třídy. Pokud členy tříd pro práci se sítěmi generují trasovací informace, je v části Poznámky v dokumentaci knihovny tříd .NET Framework uvedena následující poznámka:  
  
> [!NOTE]
>  Tento člen poskytuje trasovací informace, když je ve vaší aplikaci povoleno trasování sítě. Další informace naleznete v tématu Trasování sítě.  
  
## <a name="see-also"></a>Viz také  
 [Povolení trasování sítě](../../../docs/framework/network-programming/enabling-network-tracing.md)  
 [Postupy: Konfigurace trasování sítě](../../../docs/framework/network-programming/how-to-configure-network-tracing.md)  
 [Interpretace trasování sítě](../../../docs/framework/network-programming/interpreting-network-tracing.md)  
 [Úvod do instrumentace a trasování](http://msdn.microsoft.com/library/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)
