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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75707867"
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a>Postupy: Vytváření souborů a adresářů v izolovaném úložišti
Po získání izolovaného úložiště můžete vytvořit adresáře a soubory pro ukládání dat. V rámci úložiště jsou názvy souborů a adresářů určeny s ohledem na kořenový adresář virtuálního systému souborů.  
  
 Chcete-li vytvořit adresář, použijte metodu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> instance. Pokud zadáte podadresář adresáře, který neexistuje, budou vytvořeny oba adresáře. Pokud zadáte adresář, který již existuje, metoda se vrátí bez vytvoření adresáře a není vyvolána žádná výjimka. Pokud však zadáte název adresáře, který <xref:System.IO.IsolatedStorage.IsolatedStorageException> obsahuje neplatné znaky, je vyvolána výjimka.  
  
 Chcete-li vytvořit soubor, použijte metodu. <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType>  
  
 V operačním systému Windows izolované úložiště soubor a názvy adresářů jsou malá a velká písmena. To znamená, že pokud `ThisFile.txt`vytvoříte soubor s `THISFILE.TXT`názvem a potom vytvoříte další soubor s názvem , bude vytvořen pouze jeden soubor. Název souboru zachová původní velikost písmen pro účely zobrazení.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak vytvořit soubory a adresáře v izolovaném úložišti.  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- [Izolované úložiště](../../../docs/standard/io/isolated-storage.md)
