---
title: "Postupy: Kopírování adresářů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 43e9027c1dbfc831f598991374c22434e01fe7ff
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
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
