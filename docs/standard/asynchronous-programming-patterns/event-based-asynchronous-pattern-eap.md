---
title: Asynchronní vzor založený na událostech (EAP)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7811113244d8c5f7d79a55ebb01f04e99e9bd2a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567803"
---
# <a name="event-based-asynchronous-pattern-eap"></a>Asynchronní vzor založený na událostech (EAP)
Existuje několik způsobů, jak vystavit asynchronní funkce kódu klienta. Asynchronní vzor založený na událostech stanovuje jedním ze způsobů pro třídy nabídne asynchronní chování.  
  
> [!NOTE]
>  Od verze [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Task Parallel Library poskytuje nový model pro asynchronní a paralelní programování. Další informace najdete v tématu [paralelní programování](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled asynchronních vzorů založených na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 Popisuje, jak asynchronní vzor založený na událostech zpřístupní výhod vícevláknové aplikace při skrytí mnoho složitých problémů vyplývajících z více vláken návrhu.  
  
 [Implementace asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 Popisuje standardizovaného způsobu balíček třídy, která má asynchronní funkce.  
  
 [Osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 Popisuje požadavky na vystavení asynchronní funkce podle asynchronní vzor založený na událostech.  
  
 [Rozhodování, kdy implementovat asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 Popisuje, jak určit, kdy by měl vybrat implementovat asynchronní vzor místo na základě událostí <xref:System.IAsyncResult> vzor.  
  
 [Návod: Implementace komponenty, která podporuje asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 Ukazuje, jak vytvořit komponentu, která implementuje asynchronní vzor založený na událostech. Je implementována pomocí pomocné třídy z <xref:System.ComponentModel?displayProperty=nameWithType> obor názvů, které zajišťuje, že součást funguje správně v rámci modelu všechny aplikace.  
  
 [Postupy: Použití komponent, které podporují asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 Popisuje způsob použití komponenty, která podporuje asynchronní vzor založený na událostech.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.ComponentModel.AsyncOperation>  
 Popisuje <xref:System.ComponentModel.AsyncOperation> třídy a obsahuje odkazy na všechny její členy.  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 Popisuje <xref:System.ComponentModel.AsyncOperationManager> třídy a obsahuje odkazy na všechny její členy.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Popisuje <xref:System.ComponentModel.BackgroundWorker> součásti a obsahuje odkazy na všechny její členy.  
  
## <a name="related-sections"></a>Související oddíly  
 [Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 Popisuje programovací model pro paralelní a asynchronní operace.  
  
 [Dělení na vlákna](../../../docs/standard/threading/index.md)  
 Popisuje multithreading funkce v rozhraní .NET Framework.  
  
 [Dělení na vlákna](https://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)  
 Popisuje funkce více vláken v jazycích C# a Visual Basic.  
  
## <a name="see-also"></a>Viz také  
 [Doporučené postupy dělení na spravovaná vlákna](../../../docs/standard/threading/managed-threading-best-practices.md)  
 [Události](../../../docs/standard/events/index.md)  
 [Více vláken v součásti](https://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)  
 [Asynchronní vzory návrhu programování](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
