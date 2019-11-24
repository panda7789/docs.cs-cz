---
title: Události Trasování událostí pro Windows v CLR (Common Language Runtime)
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: 5bb9b6a2-7b57-4aea-8809-32b28bc73e88
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83246f42275425bca48530915c7bf5c19f3b9f04
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447675"
---
# <a name="etw-events-in-the-common-language-runtime"></a>Události Trasování událostí pro Windows v CLR (Common Language Runtime)
The common language runtime (CLR) provides useful event tracing for Windows (ETW) diagnostic information through a large variety of debugging and profiling events. CLR ETW events leverage the Windows ETW tracing system to augment the existing profiling and debugging support provided by the common language runtime.  
  
 More information about ETW is available in the [Improve Debugging and Performance Tuning with ETW](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw) article. Information about Xperf can be found in the entry [Windows Performance Toolkit - Xperf](https://blogs.msdn.microsoft.com/ntdebugging/2008/04/03/windows-performance-toolkit-xperf/) in the NTDebugging blog.  
  
 The .NET Framework 4 or later is required for all the events described in the event topics. The Windows Vista operating system is the minimum supported client, and Windows Server 2008 is the minimum supported server.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Řízení přihlašování rozhraní .NET Framework](controlling-logging.md)  
 Describes the tools and commands for capturing and viewing ETW events.  
  
 [Poskytovatelé Trasování událostí pro Windows v CLR](clr-etw-providers.md)  
 Provides information about the runtime and rundown providers, and how you can use them for ETW data collection.  
  
 [Klíčová slova a úrovně Trasování událostí pro Windows v CLR](clr-etw-keywords-and-levels.md)  
 Describes the keywords for the Runtime and Rundown providers that enable the filtering of events by category.  
  
 [Události Trasování událostí pro Windows v CLR](clr-etw-events.md)  
 Provides detailed information about CLR ETW events, their keywords, levels, and event data.  
  
## <a name="see-also"></a>Viz také:

- [Trasování událostí pro Windows – události v rozhraní .NET Framework](etw-events.md)
