---
title: Asynchronní vzor založený na událostech (EAP)
ms.date: 07/23/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
ms.openlocfilehash: 604e7a944579a284004817009b06c11b268d5daf
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289431"
---
# <a name="event-based-asynchronous-pattern-eap"></a>Asynchronní vzor založený na událostech (EAP)

Existuje několik způsobů, jak vystavit asynchronní funkce pro klientský kód. Asynchronní vzor založený na událostech předepisuje jeden způsob, jakým třídy představují asynchronní chování.  
  
> [!NOTE]
> Počínaje .NET Framework 4 poskytuje úloha paralelní knihovna nový model pro asynchronní a paralelní programování. Další informace naleznete v tématu [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md) a [asynchronní vzor založený na úlohách (klepněte)](task-based-asynchronous-pattern-tap.md).
  
## <a name="in-this-section"></a>V tomto oddílu

 [Přehled asynchronních vzorů založených na událostech](event-based-asynchronous-pattern-overview.md)  
 Popisuje, jak asynchronní vzor založený na událostech zpřístupňuje výhody vícevláknových aplikací a zároveň skrývá mnoho složitých problémů, které jsou v podstatě vícevláknového návrhu.  
  
 [Implementace asynchronního vzoru založeného na událostech](implementing-the-event-based-asynchronous-pattern.md)  
 Popisuje standardizovaný způsob, jak zabalit třídu, která obsahuje asynchronní funkce.  
  
 [Osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 Popisuje požadavky pro vystavení asynchronních funkcí podle asynchronního vzoru založeného na událostech.  
  
 [Rozhodování, kdy implementovat asynchronní vzor založený na událostech](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 Popisuje, jak určit, kdy se má použít asynchronní vzor založený na událostech namísto <xref:System.IAsyncResult> vzoru reprezentovaného [asynchronním programovacím modelem (APM)](asynchronous-programming-model-apm.md) .
  
 [Postupy: Implementace komponenty, která podporuje asynchronní vzor založený na událostech](component-that-supports-the-event-based-asynchronous-pattern.md)  
 Popisuje, jak vytvořit komponentu, která implementuje asynchronní vzor založený na událostech. Je implementováno pomocí pomocných tříd z <xref:System.ComponentModel?displayProperty=nameWithType> oboru názvů, který zajišťuje správné fungování komponenty v jakémkoli modelu aplikace.  

 [Postupy: Implementace klienta asynchronního vzoru založeného na událostech](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)  
 Popisuje, jak vytvořit klienta, který používá komponentu, která implementuje asynchronní vzor založený na událostech.
  
 [Postupy: Použití komponent, které podporují asynchronní vzor založený na událostech](how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 Popisuje způsob použití komponenty, která podporuje asynchronní vzor založený na událostech.  
  
## <a name="reference"></a>Odkaz

 <xref:System.ComponentModel.AsyncOperation>  
 Popisuje <xref:System.ComponentModel.AsyncOperation> třídu a má odkazy na všechny její členy.  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 Popisuje <xref:System.ComponentModel.AsyncOperationManager> třídu a má odkazy na všechny její členy.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Popisuje <xref:System.ComponentModel.BackgroundWorker> součást a má odkazy na všechny její členy.  
  
## <a name="related-sections"></a>Související oddíly

 [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md)  
 Popisuje programovací model pro asynchronní a paralelní operace.  
  
 [Dělení na vlákna](../threading/index.md)  
 Popisuje funkce multithreadingu v rozhraní .NET.  
  
## <a name="see-also"></a>Viz také

- [Doporučené postupy dělení na spravovaná vlákna](../threading/managed-threading-best-practices.md)
- [Události](../events/index.md)
- [Vzory návrhu asynchronního programování](index.md)
