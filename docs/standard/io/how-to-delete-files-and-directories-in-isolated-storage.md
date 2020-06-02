---
title: 'Postupy: Odstraňování souborů a adresářů v izolovaném úložišti'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data storage using isolated storage, deleting files and directories
- directories [.NET Framework], isolated storage
- files [.NET Framework], isolated storage
- isolated storage, deleting files and directories
- data stores, deleting files and directories
- stores, creating files and directories
- deleting files within isolated stage file
- storing data using isolated storage, deleting files and directories
- deleting directories within isolated stage file
ms.assetid: 8fcc0dea-435b-4d40-ba4d-ba056265c202
ms.openlocfilehash: dc84fefbde1177993b17e9ec687a1ef759b74735
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291900"
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a>Postupy: Odstraňování souborů a adresářů v izolovaném úložišti
V souboru izolovaného úložiště můžete odstraňovat adresáře a soubory. V rámci úložiště jsou názvy souborů a adresářů závislé na operačním systému a jsou určené jako relativní ke kořenu virtuálního systému souborů. V operačních systémech Windows nerozlišují velká a malá písmena.  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>Třída poskytuje dvě metody pro odstraňování adresářů a souborů: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> a <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> . <xref:System.IO.IsolatedStorage.IsolatedStorageException>Pokud se pokusíte odstranit soubor nebo adresář, který neexistuje, je vyvolána výjimka. Pokud zahrnete zástupný znak do názvu, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> vyvolá <xref:System.IO.IsolatedStorage.IsolatedStorageException> výjimku a <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> vyvolá <xref:System.ArgumentException> výjimku.  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A>Metoda se nezdařila, pokud adresář obsahuje nějaké soubory nebo podadresáře. Můžete použít <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> metody a k načtení existujících souborů a adresářů. Další informace o hledání ve virtuálním systému souborů v úložišti naleznete v tématu [How to: Find existující soubory a adresáře v izolovaném úložišti](how-to-find-existing-files-and-directories-in-isolated-storage.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu vytvoří a pak odstraní několik adresářů a souborů.  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>
- [Izolované úložiště](isolated-storage.md)
