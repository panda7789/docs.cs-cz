---
title: 'Postupy: Vytváření souborů a adresářů v izolovaném úložišti'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- directories [.NET Framework], isolated storage
- files [.NET Framework], isolated storage
- isolated storage, creating files and directories
- data stores, creating files and directories
- data storage using isolated storage, creating files and directories
- stores, creating files and directories
- storing data using isolated storage, creating files and directories
ms.assetid: 2ca4d2a4-809b-4f00-bc08-bf4a64d3a5c3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b7fa96e4f28e92e0890acf6ffc105ca11a97d575
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a>Postupy: Vytváření souborů a adresářů v izolovaném úložišti
Po získání izolované úložiště, můžete vytvořit adresářů a souborů pro ukládání dat. V rámci úložiště jsou s ohledem na kořenovém virtuálním souborovém systému zadat názvy souborů a adresářů.  
  
 Chcete-li vytvořit adresář, použijte <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> metodu instance. Když zadáte podadresáři adresář, který neexistuje, vytvoří se oba adresáře. Pokud určíte adresář, který již existuje, vrátí metoda bez vytvoření adresáře a nedojde k výjimce. Ale pokud zadáte název adresáře, který obsahuje neplatné znaky, <xref:System.IO.IsolatedStorage.IsolatedStorageException> je vyvolána výjimka.  
  
 Pokud chcete vytvořit soubor, použijte <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> metoda.  
  
 Operační systém Windows, souboru izolovaného úložiště a adresáře jsou názvy velká a malá písmena. To znamená když vytvoříte soubor s názvem `ThisFile.txt`a pak vytvořte jiný soubor s názvem `THISFILE.TXT`, je vytvořen pouze jeden soubor. Název souboru udržuje jeho původní velká a malá písmena pro účely zobrazení.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje postup vytvoření souborů a adresářů v izolovaném úložišti.  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>  
 [Izolované úložiště](../../../docs/standard/io/isolated-storage.md)
