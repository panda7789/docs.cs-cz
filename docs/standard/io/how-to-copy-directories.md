---
title: 'Postupy: Kopírování adresářů'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 57e2b61fb8fef37234dc10885752f92e5f9b1330
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671067"
---
# <a name="how-to-copy-directories"></a>Postupy: Kopírování adresářů
Toto téma ukazuje, jak používat vstupně-výstupních tříd synchronně zkopírovat obsah adresáře do jiného umístění. 

Příklad asynchronního kopírování najdete v tématu [vstupně-výstupní asynchronní](../../../docs/standard/io/asynchronous-file-i-o.md). 

Tento příklad zkopíruje podadresáře tak, že nastavíte `copySubDirs` z `DirectoryCopy` metodu `true`. `DirectoryCopy` Metoda rekurzivně zkopíruje podadresáře voláním sebe sama pro každý podadresář až nebudou existovat žádná další ke kopírování.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO.FileInfo>
- <xref:System.IO.DirectoryInfo>
- <xref:System.IO.FileStream>
- [Vstupně-výstupních operací souborů a datových proudů](../../../docs/standard/io/index.md)
- [Běžné vstupně-výstupní úlohy](../../../docs/standard/io/common-i-o-tasks.md)
- [Asynchronní I/O soubory](../../../docs/standard/io/asynchronous-file-i-o.md)