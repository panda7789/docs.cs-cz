---
title: Asynchronní vzor založený na událostech (EAP)
ms.date: 07/23/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
ms.openlocfilehash: ee8c90d63478e444b7d25cb7cbb5c969963d7c63
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73130933"
---
# <a name="event-based-asynchronous-pattern-eap"></a>Asynchronní vzor založený na událostech (EAP)

Existuje několik způsobů, jak vystavit asynchronní funkce klientského kódu. Asynchronní vzor založený na událostech předepisuje jeden způsob, jak třídy prezentovat asynchronní chování.  
  
> [!NOTE]
> Počínaje rozhraním .NET Framework 4 poskytuje paralelní knihovna úloh nový model pro asynchronní a paralelní programování. Další informace naleznete v [tématu Paralelní knihovna úloh (TPL)](../parallel-programming/task-parallel-library-tpl.md) a [Asynchronní vzor založený na úlohách (TAP).](task-based-asynchronous-pattern-tap.md)
  
## <a name="in-this-section"></a>V tomto oddílu

 [Přehled asynchronních vzorů založených na událostech](event-based-asynchronous-pattern-overview.md)  
 Popisuje, jak asynchronní vzor založený na událostech zpřístupňuje výhody vícevláknových aplikací a zároveň skrývá mnoho složitých problémů, které jsou vlastní návrhu s více vlákny.  
  
 [Implementace asynchronního vzoru založeného na událostech](implementing-the-event-based-asynchronous-pattern.md)  
 Popisuje standardizovaný způsob, jak zabalit třídu, která má asynchronní funkce.  
  
 [Osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 Popisuje požadavky na vystavení asynchronních funkcí podle asynchronního vzoru založeného na událostech.  
  
 [Rozhodování, kdy implementovat asynchronní vzor založený na událostech](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 Popisuje, jak určit, kdy byste měli zvolit implementaci asynchronního <xref:System.IAsyncResult> vzoru založeného na událostech namísto vzoru reprezentovaného [asynchronním programovacím modelem (APM)](asynchronous-programming-model-apm.md)
  
 [Postupy: Implementace komponenty, která podporuje asynchronní vzor založený na událostech](component-that-supports-the-event-based-asynchronous-pattern.md)  
 Popisuje, jak vytvořit komponentu, která implementuje asynchronní vzor založený na událostech. Je implementována pomocí pomocných tříd z oboru <xref:System.ComponentModel?displayProperty=nameWithType> názvů, což zajišťuje, že komponenta pracuje správně v rámci libovolného modelu aplikace.  

 [Postupy: Implementace klienta asynchronního vzoru založeného na událostech](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)  
 Popisuje, jak vytvořit klienta, který používá komponentu, která implementuje asynchronní vzor založený na událostech.
  
 [Postupy: Použití komponent, které podporují asynchronní vzor založený na událostech](how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 Popisuje použití součásti, která podporuje asynchronní vzorek založený na událostech.  
  
## <a name="reference"></a>Referenční informace

 <xref:System.ComponentModel.AsyncOperation>  
 Popisuje třídu <xref:System.ComponentModel.AsyncOperation> a má odkazy na všechny své členy.  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 Popisuje třídu <xref:System.ComponentModel.AsyncOperationManager> a má odkazy na všechny své členy.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Popisuje <xref:System.ComponentModel.BackgroundWorker> součást a má odkazy na všechny její členy.  
  
## <a name="related-sections"></a>Související oddíly

 [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md)  
 Popisuje programovací model pro asynchronní a paralelní operace.  
  
 [Threading](../../../docs/standard/threading/index.md)  
 Popisuje funkce více vláken v rozhraní .NET.  
  
## <a name="see-also"></a>Viz také

- [Doporučené postupy dělení na spravovaná vlákna](../threading/managed-threading-best-practices.md)
- [Akce](../events/index.md)
- [Asynchronní programovací návrhové vzory](index.md)
