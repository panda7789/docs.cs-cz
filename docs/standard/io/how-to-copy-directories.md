---
title: 'Postupy: Kopírování adresářů'
ms.date: 03/30/2017
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
ms.openlocfilehash: 1cfe07af216da1c35b093a1ca23e4d48c60a7bfe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-copy-directories"></a>Postupy: Kopírování adresářů
Tento příklad znázorňuje, jakým způsobem lze pomocí vstupně-výstupních tříd synchronně zkopírovat obsah adresáře do jiného umístění. V tomto příkladu může uživatel zadat, zda se mají kopírovat také podadresáře. Při kopírování podadresářů kopíruje metoda uvedená v tomto příkladu rekurzivně podadresáře voláním sebe sama pro jednotlivé následné podadresáře, jsou-li k dispozici.  
  
 Příklad asynchronně kopírování souborů naleznete v části [asynchronní vstup-výstup souboru](../../../docs/standard/io/asynchronous-file-i-o.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IO.FileInfo>  
 <xref:System.IO.DirectoryInfo>  
 <xref:System.IO.FileStream>  
 [Vstup/výstup souborů a streamů](../../../docs/standard/io/index.md)  
 [Obecné vstupně-výstupní úlohy](../../../docs/standard/io/common-i-o-tasks.md)  
 [Asynchronní vstupně-výstupní operace se soubory](../../../docs/standard/io/asynchronous-file-i-o.md)
