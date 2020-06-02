---
title: 'Postupy: Odstraňování úložišť v izolovaném úložišti'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- stores, deleting
- data stores, deleting
- deleting stores
- removing stores
- isolated storage, deleting stores
- storing data using isolated storage, deleting stores
- data storage using isolated storage, deleting stores
ms.assetid: 3947e333-5af6-4601-b2f1-24d4d6129cf3
ms.openlocfilehash: 885dc8e3ca0ea99de460cee7dd093b061f916388
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291887"
---
# <a name="how-to-delete-stores-in-isolated-storage"></a>Postupy: Odstraňování úložišť v izolovaném úložišti
<xref:System.IO.IsolatedStorage.IsolatedStorageFile>Třída poskytuje dvě metody pro odstranění souborů izolovaného úložiště:  
  
- Metoda instance <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> nepřijímá žádné argumenty a neodstraní úložiště, které ho volá. Pro tuto operaci nejsou požadována žádná oprávnění. Jakýkoli kód, který má přístup k úložišti, může odstranit všechna data, která v něm jsou.  
  
- Statická metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> přebírá <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> hodnotu výčtu a odstraní všechna úložiště pro uživatele, který spouští kód. Tato operace vyžaduje <xref:System.Security.Permissions.IsolatedStorageFilePermission> oprávnění pro tuto <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> hodnotu.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje použití statických a instančních <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> metod. Třída získá dvě obchody; jeden je izolovaný pro uživatele a sestavení a druhý je izolovaný pro uživatele, doménu a sestavení. Pak se odstraní úložiště uživatel, doména a sestavení voláním <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> metody souboru izolovaného úložiště `isoStore1` . Všechna zbývající úložiště pro uživatele pak budou odstraněna voláním statické metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> .  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Izolované úložiště](isolated-storage.md)
