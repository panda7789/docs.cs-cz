---
title: "Postupy: Čtení textu ze souboru"
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
- streams, reading text from files
- reading text files
- reading data, text files
- data streams, reading text from files
- I/O [.NET Framework], reading text from files
ms.assetid: ed180baa-dfc6-4c69-a725-46e87edafb27
caps.latest.revision: "23"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6097d6dc2120e2e76ad2403b896c492dfb799c64
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-read-text-from-a-file"></a>Postupy: Čtení textu ze souboru
Následující příklady znázorňují způsob synchronního a asynchronního čtení textu z textového souboru pomocí rozhraní .NET pro aplikace klasické pracovní plochy. V obou příkladech, při vytváření instance <xref:System.IO.StreamReader> třídu, zadejte relativní nebo absolutní cesta k souboru. Následující příklady předpokládají, že soubor s názvem TestFile.txt je uložen ve stejné složce jako aplikace.  
  
 Tyto příklady kódu nelze použít pro vývoj aplikací pro Windows Store, protože modul Windows Runtime poskytuje různé typy datových proudů pro čtení souborů a zápis do souborů. Příklad, který ukazuje, jak čtení textu ze souborů v kontextu aplikace pro Windows Store, naleznete v části [rychlý start: čtení a zápis souborů](http://msdn.microsoft.com/library/windows/apps/hh758325.aspx). Příklady, které ukazují, jak pro převod mezi datové proudy rozhraní .NET Framework a Windows runtime proudy najdete v tématu [postupy: převod mezi rozhraní .NET Framework datové proudy a datové proudy Windows Runtime](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).  
  
## <a name="example"></a>Příklad  
 První příklad ukazuje operaci synchronního čtení v rámci konzolové aplikace. V tomto příkladu je textový soubor otevřít pomocí čtečku datového proudu, obsah se zkopírují na řetězec a řetězec je výstup do konzoly.  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example"></a>Příklad  
 Druhý příklad ukazuje operaci asynchronního čtení v rámci aplikace Windows Presentation Foundation (WPF).  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source6.cs#6)]
 [!code-vb[Conceptual.BasicIO.TextFiles#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source6.vb#6)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 [Asynchronní vstupně-výstupní operace se soubory](../../../docs/standard/io/asynchronous-file-i-o.md)  
 [NIB: Postupy: vytvoření seznamu adresářů](http://msdn.microsoft.com/en-us/4d2772b1-b991-4532-a8a6-6ef733277e69)  
 [Rychlý úvod: Čtení a zápis souborů](http://msdn.microsoft.com/library/windows/apps/hh758325.aspx)  
 [Postupy: Převádění mezi streamy rozhraní .NET Framework a streamy prostředí Windows Runtime](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
 [Postupy: Čtení a zápis do nově vytvořeného datového souboru](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [Postupy: Otevření a připojení k souboru protokolu](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [Postupy: Zápis textu do souboru](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [Postupy: Čtení znaků z řetězce](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
 [Postupy: Zápis znaků do řetězce](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [Souborová služba a datový proud I-O](../../../docs/standard/io/index.md)
