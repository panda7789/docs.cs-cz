---
title: "Postupy: Příprava na vyčerpání volného prostoru pomocí izolovaného úložiště"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data stores, quotas
- isolated storage, quotas
- quanitity of isolated storage used
- limit on isolated storage used
- stores, quotas
- stores, out of space conditions
- data storage using isolated storage, quotas
- storing data using isolated storage, quotas
- space remaining in isolated storage
- data stores, out of space conditions
- storing data using isolated storage, out of space conditions
- quotas for isolated storage
- isolated storage, out of space conditions
- data storage using isolated storage, out of space conditions
ms.assetid: e35d4535-3732-421e-b1a3-37412e036145
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e04b4b85b9a14e842c94226017fcd903ad1cbb40
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-anticipate-out-of-space-conditions-with-isolated-storage"></a>Postupy: Příprava na vyčerpání volného prostoru pomocí izolovaného úložiště
Kód, který používá izolované úložiště je omezen [kvóty](../../../docs/standard/io/isolated-storage.md#quotas) , určuje maximální velikost datového oddílu, ve kterém izolované úložiště souborů a adresářů neexistuje. Kvóta je definován pomocí zásad zabezpečení a konfigurovat správci. Pokud maximální povolená velikost je překročena při pokusu o zápis dat, <xref:System.IO.IsolatedStorage.IsolatedStorageException> je vyvolána výjimka, a operace se nezdaří. To pomáhá zabránit nebezpečné útoky odmítnutí služby, které by mohly způsobit aplikace odmítala požadavků z důvodu zaplnění datového úložiště.  
  
 Můžete určit, zda je pokus o zápis, pravděpodobně selžou z tohoto důvodu <xref:System.IO.IsolatedStorage.IsolatedStorage> třída poskytuje tři vlastnosti jen pro čtení: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>, a <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>. Tyto vlastnosti můžete použít k určení, zda zápis do úložiště způsobí, že maximální povolená velikost úložiště bude překročena. Mějte na paměti, která izolované úložiště je přístupná souběžně; Proto když můžete vypočítat množství paměti zbývající úložiště, v prostoru úložiště by mohly spotřebovat čas pokusu o zápis do úložiště. Můžete ale maximální velikost úložiště sloužící k určení, zda horní limit na úložiště k dispozici je chystáte dostupný.  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> Vlastnost závisí na důkazy od sestavení správně fungovat. Z tohoto důvodu by tato vlastnost načíst pouze na <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objekty, které byly vytvořeny pomocí <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, nebo <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metoda. <xref:System.IO.IsolatedStorage.IsolatedStorageFile>objekty, které byly vytvořeny jiným způsobem (například objekty, které byly vráceny z <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> metoda), nevrátí přesné maximální velikost.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu získá izolované úložiště, vytvoří několik souborů a načte <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> vlastnost. Zbývající místo je uveden v bajtech.  
  
 [!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
 [!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
 [!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [Izolované úložiště](../../../docs/standard/io/isolated-storage.md)  
 [Postupy: Získávání úložišť pro izolované úložiště](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)
