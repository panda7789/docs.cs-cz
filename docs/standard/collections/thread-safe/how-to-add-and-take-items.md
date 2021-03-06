---
title: 'Postupy: Přidávání odebírání jednotlivých položek v BlockingCollection'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, blocking dictionary
ms.assetid: 38f2f3d8-15e5-4bf4-9c83-2b5b6f22bad1
ms.openlocfilehash: f895be4c20a0cccad23e27db3d488355a614cbfc
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287884"
---
# <a name="how-to-add-and-take-items-individually-from-a-blockingcollection"></a>Postupy: Přidávání odebírání jednotlivých položek v BlockingCollection
Tento příklad ukazuje, jak přidat a odebrat položky z a <xref:System.Collections.Concurrent.BlockingCollection%601> v blokujícím a neblokujícím způsobem. Další informace o <xref:System.Collections.Concurrent.BlockingCollection%601> naleznete v tématu [BlockingCollection – přehled](blockingcollection-overview.md).  
  
 Příklad, jak vytvořit výčet a <xref:System.Collections.Concurrent.BlockingCollection%601> dokud není prázdný a další prvky nebudou přidány, naleznete v tématu [How to: use foreach k odebrání položek v blokujícícollection](how-to-use-foreach-to-remove.md).
  
## <a name="example"></a>Příklad  
 Tento první příklad ukazuje, jak přidat a převzít položky tak, že operace budou blokovat, pokud je kolekce buď dočasně prázdná (při pořízení), nebo s maximální kapacitou (při přidávání), nebo pokud uplynula doba platnosti. Všimněte si, že blokování na maximální kapacitě je povoleno pouze v případě, že je kolekce BlockingCollection vytvořena s maximální kapacitou zadanou v konstruktoru.  
  
 [!code-csharp[CDS_BlockingCollection#01](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example01.cs#01)]
 [!code-vb[CDS_BlockingCollection#01](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/simpleblocking.vb#01)]  
  
## <a name="example"></a>Příklad  
 Tento druhý příklad ukazuje, jak přidat a převzít položky, aby operace neblokovaly. Pokud není k dispozici žádná položka, byla dosažena maximální kapacita v vázané kolekci nebo vypršel časový limit, <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operace nebo vrátí hodnotu false. To umožňuje, aby vlákno v průběhu chvilku provedlo nějakou další užitečnou práci, a potom to zkuste znovu později načíst novou položku nebo se pokusit přidat stejnou položku, kterou nebylo možné přidat dříve. Program také ukazuje, jak implementovat zrušení při přístupu k <xref:System.Collections.Concurrent.BlockingCollection%601> .  
  
 [!code-csharp[CDS_BlockingCollection#02](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example02.cs#02)]
 [!code-vb[CDS_BlockingCollection#02](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/nonblockingbc.vb#02)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [BlockingCollection – přehled](blockingcollection-overview.md)
