---
title: "Postupy: Čtení a zápis do nově vytvořeného datového souboru"
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
- cpp
helpviewer_keywords:
- streams, reading and writing data
- BinaryReader class, examples
- I/O [.NET Framework], reading data
- I/O [.NET Framework], writing data
- BinaryWriter class, examples
ms.assetid: e209d949-31e8-44ea-8e38-87f9093f3093
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 04ded71a23ba4cabab0a22e0d66c1084a726d8c8
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a>Postupy: Čtení a zápis do nově vytvořeného datového souboru
Třídy <xref:System.IO.BinaryWriter> a <xref:System.IO.BinaryReader?displayProperty=nameWithType> se používají spíše pro zápis a čtení dat než řetězců znaků. Následující příklad znázorňuje, jakým způsobem lze zapisovat a číst data z nového prázdného datového proudu souboru nazvaného `Test.data`. Po vytvoření datového souboru v aktuálním adresáři jsou vytvořeny přidružené objekty <xref:System.IO.BinaryWriter> a <xref:System.IO.BinaryReader> a objekt <xref:System.IO.BinaryWriter> se používá k zápisu celých čísel 0 až 10 do `Test.data`, čímž je ukazatel souboru ponechán na konci souboru. Po nastavení ukazatele souboru zpět na začátek přečte objekt <xref:System.IO.BinaryReader> zadaný obsah.  
  
## <a name="example"></a>Příklad  
 [!code-cpp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CPP/source6.cpp#7)]
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Pokud data `Test.data` již v aktuálním adresáři existují, je vyvolána výjimka <xref:System.IO.IOException>. Chcete-li vytvořit nový soubor bez vyvolání výjimky, je třeba při inicializaci datového proudu souboru použít vždy volbu režimu souboru <xref:System.IO.FileMode.Create?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IO.BinaryReader>  
 <xref:System.IO.BinaryWriter>  
 <xref:System.IO.FileStream>  
 <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
 <xref:System.IO.SeekOrigin>  
 [Postupy: Vytvoření výčtu adresářů a souborů](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [Postupy: Otevření a připojení k souboru protokolu](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [Postupy: Čtení textu ze souboru](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [Postupy: Zápis textu do souboru](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [Postupy: Čtení znaků z řetězce](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
 [Postupy: Zápis znaků do řetězce](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [Souborová služba a datový proud I-O](../../../docs/standard/io/index.md)
