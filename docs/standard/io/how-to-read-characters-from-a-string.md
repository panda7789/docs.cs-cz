---
title: 'Postupy: Čtení znaků z řetězce'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e890e4172e645e9919ea88ec5835aaed7432c0c6
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835197"
---
# <a name="how-to-read-characters-from-a-string"></a>Postupy: Čtení znaků z řetězce
Následující příklady kódu ukazují, jak ke čtení znaků z řetězce synchronně nebo asynchronně.  
  
## <a name="example-read-characters-synchronously"></a>Příklad: Čtení znaků synchronně 
 Tento příklad načte 13 znaků synchronně z řetězce, uloží je v poli a zobrazí je. Příklad poté načte zbývající znaky v řetězci, uloží je do pole, počínaje šestého prvku a zobrazí obsah pole.  
  
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example-read-characters-asynchronously"></a>Příklad: Asynchronně číst datové části znaků  
 Následující příklad je kódu na pozadí aplikace WPF. Při načtení okna, v příkladu asynchronně přečte všechny znaky z <xref:System.Windows.Controls.TextBox> ovládací prvek a uloží je v poli. Pak asynchronně zapíše každý znak písmeno, nebo prázdné znaky na samostatném řádku <xref:System.Windows.Controls.TextBlock> ovládacího prvku.  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO.StringReader>  
- <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>  
- [Asynchronní I/O soubory](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [Postupy: Vytváření adresářů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))  
- [Postupy: Čtení a zápis do nově vytvořeného datového souboru](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Postupy: Otevření a připojení k souboru protokolu](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Postupy: Čtení textu ze souboru](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Postupy: Zápis textu do souboru](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Postupy: Zápis znaků do řetězce](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [Vstupně-výstupních operací souborů a datových proudů](../../../docs/standard/io/index.md)
