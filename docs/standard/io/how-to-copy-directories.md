---
title: 'Postup: Kopírování adresářů'
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
ms.openlocfilehash: 5d40db7f902dac8bd6bbdc1510be8e56a321be30
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159452"
---
# <a name="how-to-copy-directories"></a>Postup: Kopírování adresářů
Toto téma ukazuje, jak používat vstupně-v třídy synchronně kopírovat obsah adresáře do jiného umístění.

Příklad asynchronní kopie souboru naleznete [v tématu V/V. asynchronního souboru](../../../docs/standard/io/asynchronous-file-i-o.md).

Tento příklad zkopíruje podadresáře `DirectoryCopy` nastavením `true` `copySubDirs` metody na . Metoda `DirectoryCopy` rekurzivně zkopíruje podadresáře voláním sebe sama v každém podadresáři, dokud nejsou k dispozici žádné další kopírování.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="see-also"></a>Viz také

- <xref:System.IO.FileInfo>
- <xref:System.IO.DirectoryInfo>
- <xref:System.IO.FileStream>
- [Vstupně-tono-videa](../../../docs/standard/io/index.md)
- [Běžné vstupně-no úkoly](../../../docs/standard/io/common-i-o-tasks.md)
- [Vstupně-nosný soubor asynchronní soubor](../../../docs/standard/io/asynchronous-file-i-o.md)
