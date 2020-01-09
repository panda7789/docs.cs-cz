---
title: 'Postupy: kopírování adresářů'
ms.date: 12/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- directory copying
- I/O [.NET Framework], copying directories
- subdirectory copying
- copying directories
- directories [.NET Framework], copying
ms.assetid: 5a969765-e5f8-4b4e-977e-90e2b0a1fe3c
ms.openlocfilehash: 223e83a5ff6a73825985ec4e3b6b601fb196fe5e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75707897"
---
# <a name="how-to-copy-directories"></a>Postupy: kopírování adresářů
Toto téma ukazuje, jak použít třídy v/v k synchronnímu zkopírování obsahu adresáře do jiného umístění. 

Příklad asynchronního kopírování souborů najdete v tématu [asynchronní vstupně-výstupní operace se soubory](../../../docs/standard/io/asynchronous-file-i-o.md). 

Tento příklad kopíruje podadresáře nastavením `copySubDirs` metody `DirectoryCopy` na `true`. Metoda `DirectoryCopy` rekurzivně kopíruje podadresáře tím, že se zavolá sám na každý podadresář, dokud nebudete moci kopírovat.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO.FileInfo>
- <xref:System.IO.DirectoryInfo>
- <xref:System.IO.FileStream>
- [Vstupně-výstupní operace se soubory a datovým proudem](../../../docs/standard/io/index.md)
- [Běžné vstupně-výstupní úlohy](../../../docs/standard/io/common-i-o-tasks.md)
- [I/O asynchronní soubory](../../../docs/standard/io/asynchronous-file-i-o.md)
