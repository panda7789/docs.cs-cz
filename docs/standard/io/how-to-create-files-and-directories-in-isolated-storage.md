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
ms.openlocfilehash: 08beb44fdb58ab1c1d53f70ac0653348b96fcb18
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44078858"
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a>Postupy: Vytváření souborů a adresářů v izolovaném úložišti
Po získání izolovaného úložiště, můžete vytvořit adresářů a souborů k ukládání dat. V rámci úložiště jsou zadané názvy souborů a adresářů s ohledem na kořenovém virtuálním souborovém systému.  
  
 Chcete-li vytvořit adresář, použijte <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> metodu instance. Pokud zadáte podadresáře adresáře, který neexistuje, vytvoří se oba adresáře. Pokud určíte adresář, který již existuje, metoda vrátí bez vytvoření adresáře a není vyvolána žádná výjimka. Nicméně, pokud zadáte název adresáře, který obsahuje neplatné znaky, <xref:System.IO.IsolatedStorage.IsolatedStorageException> je vyvolána výjimka.  
  
 Chcete-li vytvořit soubor, použijte <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> metody.  
  
 V operačním systému Windows, izolované úložiště souboru a adresáře názvy jsou malá a velká písmena. To znamená pokud vytvoříte soubor s názvem `ThisFile.txt`a pak vytvořte jiný soubor s názvem `THISFILE.TXT`, je vytvořen pouze jeden soubor. Název souboru udržuje jeho původní malých a velkých písmen pro účely zobrazení.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak vytváření souborů a adresářů v izolovaném úložišti.  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>  
- [Izolované úložiště](../../../docs/standard/io/isolated-storage.md)
