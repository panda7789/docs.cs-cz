---
title: Asynchronní vzor založený na událostech (EAP)
ms.date: 07/23/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 052773c615bcc4ddb5b735ae8164d44ed70bd935
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61870302"
---
# <a name="event-based-asynchronous-pattern-eap"></a>Asynchronní vzor založený na událostech (EAP)

Existuje mnoho způsobů, jak vystavení asynchronních funkcí pro klientský kód. Asynchronní vzor založený na událostech předepisuje jedním ze způsobů pro třídy zobrazíte asynchronní chování.  
  
> [!NOTE]
> Od verze rozhraní .NET Framework 4, poskytuje Task Parallel Library nový model pro asynchronní a paralelní programování. Další informace najdete v tématu [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md) a [úkolově orientovanou asynchronní vzor (TAP)](task-based-asynchronous-pattern-tap.md).
  
## <a name="in-this-section"></a>V tomto oddílu

 [Přehled asynchronních vzorů založených na událostech](event-based-asynchronous-pattern-overview.md)  
 Popisuje, jak asynchronního vzoru založeného na událostech zpřístupní výhody vícevláknové aplikace při skrytí mnoho složitých problémů vyplývající vícevláknový návrhu.  
  
 [Implementace asynchronního vzoru založeného na událostech](implementing-the-event-based-asynchronous-pattern.md)  
 Popisuje standardizovaný způsob balíček třídu, která obsahuje asynchronní funkce.  
  
 [Osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 Popisuje požadavky na vystavení asynchronních funkcí podle asynchronního vzoru založeného na událostech.  
  
 [Rozhodování, kdy implementovat asynchronní vzor založený na událostech](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 Popisuje, jak určit, kdy měli byste implementovat asynchronní vzor místo založený na událostech <xref:System.IAsyncResult> reprezentována vzor [asynchronního programovacího modelu (APM)](asynchronous-programming-model-apm.md)
  
 [Postupy: Implementace komponenty, která podporuje asynchronní vzor založený na událostech](component-that-supports-the-event-based-asynchronous-pattern.md)  
 Popisuje, jak vytvořit komponentu, která implementuje asynchronního vzoru založeného na událostech. Je implementována pomocí pomocné třídy z <xref:System.ComponentModel?displayProperty=nameWithType> obor názvů, který zajistí, že součást správně funguje v jakékoli aplikačního modelu.  

 [Postupy: Implementace klienta asynchronního vzoru založeného na událostech](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)  
 Popisuje, jak vytvořit klienta, který používá komponenty, která implementuje asynchronního vzoru založeného na událostech.
  
 [Postupy: Použití komponent, které podporují asynchronní vzor založený na událostech](how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 Popisuje způsob použití komponenty, která podporuje asynchronní vzor založený na událostech.  
  
## <a name="reference"></a>Odkaz

 <xref:System.ComponentModel.AsyncOperation>  
 Popisuje <xref:System.ComponentModel.AsyncOperation> třída a obsahuje odkazy na všechny její členy.  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 Popisuje <xref:System.ComponentModel.AsyncOperationManager> třída a obsahuje odkazy na všechny její členy.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Popisuje <xref:System.ComponentModel.BackgroundWorker> komponenty a obsahuje odkazy na všechny její členy.  
  
## <a name="related-sections"></a>Související oddíly

 [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md)  
 Popisuje programovací model pro asynchronní a paralelní operace.  
  
 [Dělení na vlákna](../../../docs/standard/threading/index.md)  
 Popisuje funkce pro multithreading v rozhraní .NET.  
  
## <a name="see-also"></a>Viz také:

- [Doporučené postupy dělení na spravovaná vlákna](../threading/managed-threading-best-practices.md)
- [Události](../events/index.md)
- [Návrhové vzory asynchronního programování](index.md)
