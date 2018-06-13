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
ms.openlocfilehash: 9e8de7a1b5de580ca768ec0dfbcbfab2d8cb6271
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573484"
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a>Postupy: Odstraňování souborů a adresářů v izolovaném úložišti
Můžete odstranit adresářů a souborů v souboru izolovaného úložiště. Názvy souborů a adresářů v rámci úložiště, jsou závislé na operačním systému a je zadána jako relativní vůči kořenovému adresáři virtuálním souborovém systému. Nejsou malá a velká písmena v operačních systémech Windows.  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> Třída poskytuje dvě metody pro odstranění adresářů a souborů: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> a <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>. <xref:System.IO.IsolatedStorage.IsolatedStorageException> Je vyvolána výjimka, pokud se pokusíte odstranit soubor nebo adresář, který neexistuje. Pokud zahrnete zástupný znak v názvu, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> vyvolá <xref:System.IO.IsolatedStorage.IsolatedStorageException> výjimka, a <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> vyvolá <xref:System.ArgumentException> výjimka.  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> Metoda selže, pokud adresář obsahuje nějaké soubory nebo podadresáře. Můžete použít <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> a <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> metody se načíst existující soubory a adresáře. Další informace o hledání virtuálním souborovém systému úložiště najdete v tématu [postupy: hledání existujících souborů a adresářů v izolovaném úložišti](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu vytvoří a odstraní několik adresářů a souborů.  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>  
 [Izolované úložiště](../../../docs/standard/io/isolated-storage.md)
