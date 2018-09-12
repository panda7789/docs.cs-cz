---
title: Thread.Suspend, kolekce paměti a bezpečné body
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- suspending threads
- safe points
- threading [.NET Framework], suspending
- threading [.NET Framework], garbage collection
- garbage collection, threads
ms.assetid: e8f58e17-2714-4821-802a-f8eb3b2baa62
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fc3af01167fe97b701bdb0c7bc37af02d8e8a77c
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44511903"
---
# <a name="threadsuspend-garbage-collection-and-safe-points"></a>Thread.Suspend, kolekce paměti a bezpečné body
Při volání <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> ve vlákně, systém zjistí, že se požaduje pozastavení vlákna a umožňuje spuštění, dokud nedosáhne bezpečné bod před skutečně pozastavení vlákna vlákna. Bod bezpečné pro vlákna je bod v jeho spuštění, na které uvolňování paměti kolekce provést.  
  
 Po dosažení bod bezpečné, modul runtime zaručuje, že pozastaveného vlákna nebude provádět žádný další krok ve spravovaném kódu. Vlákno provádění mimo spravovaný kód je vždy bezpečné pro uvolnění paměti a provádění pokračuje, dokud se pokusí pokračovat v provádění spravovaného kódu.  
  
> [!NOTE]
>  Aby bylo možné provádět uvolňování paměti, modul runtime musí pozastavit všechna vlákna kromě vlákna provádění v kolekci. Každé vlákno musí být převeden do bezpečného bodu předtím, než je možné ho pozastavit.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Thread>  
- <xref:System.GC>  
- [Dělení na vlákna](../../../docs/standard/threading/index.md)  
- [Automatická správa paměti](../../../docs/standard/automatic-memory-management.md)
