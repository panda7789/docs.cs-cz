---
title: 'Postup: Čtení znaků z řetězce'
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reading characters from strings
- data streams, reading characters from string
- I/O [.NET Framework], reading characters from strings
- reading data, strings
- streams, reading characters from string
ms.assetid: 27ea5e52-6db8-42d8-980a-50bcfc7fd270
ms.openlocfilehash: ed267ad62e46f6216c94906df1bcefb0684ab51b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155760"
---
# <a name="how-to-read-characters-from-a-string"></a>Postup: Čtení znaků z řetězce
Následující příklady kódu ukazují, jak číst znaky synchronně nebo asynchronně z řetězce.  
  
## <a name="example-read-characters-synchronously"></a>Příklad: Synchronní čtení znaků
 Tento příklad přečte 13 znaků synchronně z řetězce, uloží je do pole a zobrazí je. Příklad pak přečte zbytek znaků v řetězci, uloží je do pole začínající na šestý prvek a zobrazí obsah pole.  
  
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example-read-characters-asynchronously"></a>Příklad: Čtení znaků asynchronně  
 Dalším příkladem je kód za wpf aplikace. Při načtení okna příklad asynchronně přečte <xref:System.Windows.Controls.TextBox> všechny znaky z ovládacího prvku a uloží je do pole. Potom asynchronně zapíše každé písmeno nebo prázdné místo znak <xref:System.Windows.Controls.TextBlock> na samostatný řádek ovládacího prvku.  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO.StringReader>  
- <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>  
- [Vstupně-nosný soubor asynchronní soubor](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [Postup: Vytvoření výpisu adresáře](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))  
- [Postup: Čtení a zápis do nově vytvořeného datového souboru](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Postup: Otevření a připojení k souboru protokolu](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Postup: Čtení textu ze souboru](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Postup: Zápis textu do souboru](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Postup: Zápis znaků do řetězce](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [Vstupně-tono-videa](../../../docs/standard/io/index.md)
