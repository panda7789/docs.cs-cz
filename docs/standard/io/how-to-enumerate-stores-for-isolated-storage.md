---
title: "Postupy: Vytvoření výčtu úložišť pro izolované úložiště"
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
helpviewer_keywords:
- enumerating stores
- data storage using isolated storage, enumerating stores
- storing data using isolated storage, enumerating stores
- stores, enumerating
- isolated storage, enumerating stores
- data stores, enumerating
ms.assetid: 0fcf279a-f241-48f0-8034-2e3d331f1fcb
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7c4fa63c5c7f966831a55c9103c9ba58cfa621d6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-enumerate-stores-for-isolated-storage"></a>Postupy: Vytvoření výčtu úložišť pro izolované úložiště
Můžete vytvořit výčet všech izolovaných úložišť pro aktuálního uživatele pomocí <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> statickou metodu. Tato metoda přebírá <xref:System.IO.IsolatedStorage.IsolatedStorageScope> hodnotu a vrátí <xref:System.IO.IsolatedStorage.IsolatedStorageFile> enumerátor. K vytvoření výčtu úložišť, musí mít <xref:System.Security.Permissions.IsolatedStorageFilePermission> oprávnění, která určuje <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> hodnotu. Když zavoláte <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> metoda s <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> hodnotu, vrátí pole <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objekty, které jsou definovány pro aktuálního uživatele.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu získá obchodu, která je izolovaná podle uživatele a sestavení, vytvoří několik souborů a načte tyto soubory pomocí <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> metoda.  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [Izolované úložiště](../../../docs/standard/io/isolated-storage.md)
