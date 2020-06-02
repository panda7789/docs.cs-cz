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
ms.openlocfilehash: b74bf62dabe24765e07ffa6820cc1675122a9122
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288547"
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a>Postupy: Vytváření souborů a adresářů v izolovaném úložišti
Po získání izolovaného úložiště můžete vytvářet adresáře a soubory pro ukládání dat. V rámci úložiště jsou zadány názvy souborů a adresářů s ohledem na kořen virtuálního systému souborů.  
  
 Chcete-li vytvořit adresář, použijte <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> metodu instance. Pokud zadáte podadresář adresáře, který neexistuje, vytvoří se oba adresáře. Pokud zadáte adresář, který již existuje, metoda se vrátí bez vytvoření adresáře a není vyvolána žádná výjimka. Pokud však zadáte název adresáře, který obsahuje neplatné znaky, <xref:System.IO.IsolatedStorage.IsolatedStorageException> je vyvolána výjimka.  
  
 Chcete-li vytvořit soubor, použijte <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> metodu.  
  
 V operačním systému Windows se v názvech souborů a adresářů izolovaného úložiště nerozlišují velká a malá písmena. To znamená, že pokud vytvoříte soubor s názvem `ThisFile.txt` a pak vytvoříte jiný soubor s názvem `THISFILE.TXT` , vytvoří se pouze jeden soubor. Název souboru uchovává původní velikost písmen pro účely zobrazení.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak vytvořit soubory a adresáře v izolovaném úložišti.  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- [Izolované úložiště](isolated-storage.md)
