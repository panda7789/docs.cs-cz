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
ms.openlocfilehash: 83e8c800dc74d9689f1bfdb506a6b454e87b36ca
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75707867"
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a>Postupy: Vytváření souborů a adresářů v izolovaném úložišti
Po získání izolovaného úložiště můžete vytvářet adresáře a soubory pro ukládání dat. V rámci úložiště jsou zadány názvy souborů a adresářů s ohledem na kořen virtuálního systému souborů.  
  
 Chcete-li vytvořit adresář, použijte metodu instance <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType>. Pokud zadáte podadresář adresáře, který neexistuje, vytvoří se oba adresáře. Pokud zadáte adresář, který již existuje, metoda se vrátí bez vytvoření adresáře a není vyvolána žádná výjimka. Pokud však zadáte název adresáře, který obsahuje neplatné znaky, je vyvolána výjimka <xref:System.IO.IsolatedStorage.IsolatedStorageException>.  
  
 Chcete-li vytvořit soubor, použijte metodu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType>.  
  
 V operačním systému Windows se v názvech souborů a adresářů izolovaného úložiště nerozlišují velká a malá písmena. To znamená, že pokud vytvoříte soubor s názvem `ThisFile.txt`a pak vytvoříte další soubor s názvem `THISFILE.TXT`, vytvoří se pouze jeden soubor. Název souboru uchovává původní velikost písmen pro účely zobrazení.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak vytvořit soubory a adresáře v izolovaném úložišti.  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- [Izolované úložiště](../../../docs/standard/io/isolated-storage.md)
