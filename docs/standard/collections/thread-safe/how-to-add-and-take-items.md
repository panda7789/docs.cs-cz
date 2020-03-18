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
ms.openlocfilehash: 3f4270d2ec71421bad8974a3e5cd8f1d65db3b74
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711295"
---
# <a name="how-to-add-and-take-items-individually-from-a-blockingcollection"></a>Postupy: Přidávání odebírání jednotlivých položek v BlockingCollection
Tento příklad ukazuje, jak přidat <xref:System.Collections.Concurrent.BlockingCollection%601> a odebrat položky z blokování a neblokující způsobem. Další informace <xref:System.Collections.Concurrent.BlockingCollection%601>naleznete v tématu [BlockingCollection Overview](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).  
  
 Příklad, jak <xref:System.Collections.Concurrent.BlockingCollection%601> výčet, dokud není prázdný a žádné další prvky budou přidány, naleznete v [tématu: Použití ForEach odebrat položky v BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).
  
## <a name="example"></a>Příklad  
 Tento první příklad ukazuje, jak přidat a přijmout položky tak, aby operace bude blokovat, pokud kolekce je buď dočasně prázdný (při převzetí) nebo na maximální kapacitu (při přidávání), nebo pokud uplynula zadaná doba časového limitu. Všimněte si, že blokování na maximální kapacitu je povoleno pouze v případě, že BlockingCollection byla vytvořena s maximální kapacitou zadanou v konstruktoru.  
  
 [!code-csharp[CDS_BlockingCollection#01](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example01.cs#01)]
 [!code-vb[CDS_BlockingCollection#01](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/simpleblocking.vb#01)]  
  
## <a name="example"></a>Příklad  
 Tento druhý příklad ukazuje, jak přidat a přijmout položky tak, aby operace nebudou blokovat. Pokud není k dispozici žádná položka, bylo dosaženo maximální kapacity v ohraničené kolekci <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> nebo uplynulčasový limit, vrátí operace nebo false. To umožňuje vlákno provést některé další užitečné práce na chvíli a zkuste to znovu později buď načíst novou položku, nebo zkuste přidat stejnou položku, která nemohla být přidána dříve. Program také ukazuje, jak implementovat zrušení <xref:System.Collections.Concurrent.BlockingCollection%601>při přístupu k .  
  
 [!code-csharp[CDS_BlockingCollection#02](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example02.cs#02)]
 [!code-vb[CDS_BlockingCollection#02](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/nonblockingbc.vb#02)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [BlockingCollection – přehled](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)
