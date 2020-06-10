---
title: 'Postupy: kopírování adresářů'
description: Podívejte se, jak kopírovat adresáře pomocí vstupně-výstupních tříd, které synchronně kopírují obsah adresáře do jiného umístění.
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
ms.openlocfilehash: 65fe28c90a6cd6f0b3c8c32da19c1d9603900670
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662586"
---
# <a name="how-to-copy-directories"></a>Postupy: kopírování adresářů
Toto téma ukazuje, jak použít třídy v/v k synchronnímu zkopírování obsahu adresáře do jiného umístění.

Příklad asynchronního kopírování souborů najdete v tématu [asynchronní vstupně-výstupní operace se soubory](asynchronous-file-i-o.md).

Tento příklad kopíruje podadresáře nastavením `copySubDirs` `DirectoryCopy` metody na `true` . `DirectoryCopy`Metoda rekurzivně kopíruje podadresáře tím, že zavolá sebe sama do každého podadresáře, dokud nebudete moci kopírovat.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="see-also"></a>Viz také

- <xref:System.IO.FileInfo>
- <xref:System.IO.DirectoryInfo>
- <xref:System.IO.FileStream>
- [Vstup/výstup souborů a streamů](index.md)
- [Obecné vstupně-výstupní úlohy](common-i-o-tasks.md)
- [Asynchronní souborový vstup-výstup](asynchronous-file-i-o.md)
