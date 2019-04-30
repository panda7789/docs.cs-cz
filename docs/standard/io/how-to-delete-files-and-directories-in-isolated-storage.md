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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d05b7fa3010ab089d1a97e9a0516096326fd4bb6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797173"
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a>Postupy: Odstraňování souborů a adresářů v izolovaném úložišti
Můžete odstranit adresářů a souborů v souboru izolovaného úložiště. Názvy souborů a adresářů v rámci úložiště, jsou závislé na operační systém a jsou určené kořeni virtuálním souborovém systému. Nejsou malá a velká písmena v operačních systémech Windows.  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> Třída poskytuje dvě metody pro odstranění adresářů a souborů: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> a <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>. <xref:System.IO.IsolatedStorage.IsolatedStorageException> Je vyvolána výjimka, pokud se pokusíte odstranit soubor nebo adresář, který neexistuje. Pokud zahrnete zástupných znaků v názvu, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> vyvolá <xref:System.IO.IsolatedStorage.IsolatedStorageException> výjimky, a <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> vyvolá <xref:System.ArgumentException> výjimky.  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> Metoda selže, pokud adresář obsahuje všechny soubory a podadresáře. Můžete použít <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> a <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> metody pro načtení existujících souborů a adresářů. Další informace o hledání virtuálním souborovém systému úložiště najdete v tématu [jak: Hledání existujících souborů a adresářů v izolovaném úložišti](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu vytvoří a odstraní několik adresářů a souborů.  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>
- [Izolované úložiště](../../../docs/standard/io/isolated-storage.md)
