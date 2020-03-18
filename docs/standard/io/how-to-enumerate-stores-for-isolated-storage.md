---
title: 'Postupy: Vytvoření výčtu úložišť pro izolované úložiště'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: 3ba38093e9e978c89cdb2bb7a584ed9e04c1096d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75707525"
---
# <a name="how-to-enumerate-stores-for-isolated-storage"></a>Postupy: Vytvoření výčtu úložišť pro izolované úložiště
Můžete vytvořit výčet všech izolovaných úložišť pro <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> aktuálního uživatele pomocí statické metody. Tato metoda <xref:System.IO.IsolatedStorage.IsolatedStorageScope> přebírá hodnotu <xref:System.IO.IsolatedStorage.IsolatedStorageFile> a vrátí čítač výčtu. Chcete-li vytvořit výčet úložišť, musíte <xref:System.Security.Permissions.IsolatedStorageFilePermission> mít <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> oprávnění, které určuje hodnotu. Pokud zavoláte <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> metodu <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> s hodnotou, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> vrátí pole objektů, které jsou definovány pro aktuálního uživatele.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu získá úložiště, které je izolováno uživatelem a sestavením, vytvoří <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> několik souborů a načte tyto soubory pomocí metody.  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Izolované úložiště](../../../docs/standard/io/isolated-storage.md)
