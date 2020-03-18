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
ms.openlocfilehash: ec4de3e3a139cfcf66f1f6252c03c467f4ccfbc5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75707854"
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a>Postupy: Odstraňování souborů a adresářů v izolovaném úložišti
Adresáře a soubory v izolovaném souboru úložiště můžete odstranit. V rámci úložiště jsou názvy souborů a adresářů závislé na operačním systému a jsou určeny jako relativní ke kořenovému adresáři virtuálního systému souborů. V operačních systémech Windows nerozlišují malá a velká písmena.  
  
 Třída <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> poskytuje dvě metody pro odstranění adresářů <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> a <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>souborů: a . Pokud <xref:System.IO.IsolatedStorage.IsolatedStorageException> se pokusíte odstranit soubor nebo adresář, který neexistuje, je vyvolána výjimka. Pokud do názvu zahrnete <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> zástupný <xref:System.IO.IsolatedStorage.IsolatedStorageException> znak, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> vyvolá výjimku a vyvolá výjimku. <xref:System.ArgumentException>  
  
 Metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> se nezdaří, pokud adresář obsahuje soubory nebo podadresáře. Metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> a <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> můžete použít k načtení existujících souborů a adresářů. Další informace o prohledání virtuálního systému souborů v úložišti naleznete v tématu [How to: Najít existující soubory a adresáře v izolovaném úložišti](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu vytvoří a odstraní několik adresářů a souborů.  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>
- [Izolované úložiště](../../../docs/standard/io/isolated-storage.md)
