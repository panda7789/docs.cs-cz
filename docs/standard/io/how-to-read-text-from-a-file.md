---
title: 'Postupy: Čtení textu ze souboru'
ms.date: 06/19/2018
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2ffc8c88f01ba10bceb4f768f38ae9b1dcc4148e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43422172"
---
# <a name="how-to-read-text-from-a-file"></a>Postupy: Čtení textu ze souboru
Následující příklady znázorňují způsob synchronního a asynchronního čtení textu z textového souboru pomocí rozhraní .NET pro aplikace klasické pracovní plochy. V obou příkladech je při vytváření instance třídy <xref:System.IO.StreamReader> třídu, zadejte relativní nebo absolutní cesta k souboru. Následující příklady předpokládají, že soubor s názvem TestFile.txt je uložen ve stejné složce jako aplikace.  
  
 Tyto příklady kódu se nevztahují na vývoj pro Windows Store Apps, protože modul Windows Runtime poskytuje různé stream typy pro čtení a zápis do souborů. Příklad, který znázorňuje způsob čtení textu ze souboru v aplikaci Windows Store, naleznete v tématu [rychlý start: čtení a zápis do souborů](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)). Příklady, které ukazují, jak k převodu mezi datovými proudy rozhraní .NET Framework a datovými proudy Windows runtime naleznete v tématu [postupy: převod mezi streamy rozhraní .NET Framework a datovými proudy Windows Runtime](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje operaci synchronního čtení v rámci konzolové aplikace. V tomto příkladu textový soubor se otevře pomocí čtečku datového proudu obsahu se zkopírují do řetězce a řetězce je výstup do konzoly.  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje operaci asynchronního čtení v aplikaci Windows Presentation Foundation (WPF).  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source6.cs#6)]
 [!code-vb[Conceptual.BasicIO.TextFiles#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source6.vb#6)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 [Asynchronní vstupně-výstupní operace se soubory](../../../docs/standard/io/asynchronous-file-i-o.md)  
 [NIB: Postupy: vytvoření adresářů](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69)  
 [Rychlý start: Čtení a zápis do souborů](https://msdn.microsoft.com/library/windows/apps/hh758325.aspx)  
 [Postupy: Převádění mezi streamy rozhraní .NET Framework a streamy prostředí Windows Runtime](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
 [Postupy: Čtení a zápis do nově vytvořeného datového souboru](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [Postupy: Otevření a připojení k souboru protokolu](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [Postupy: Zápis textu do souboru](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [Postupy: Čtení znaků z řetězce](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
 [Postupy: Zápis znaků do řetězce](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [Vstup/výstup souborů a streamů](../../../docs/standard/io/index.md)
