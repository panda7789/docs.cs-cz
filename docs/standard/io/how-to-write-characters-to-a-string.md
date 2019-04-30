---
title: 'Postupy: Zápis znaků do řetězce'
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data streams, writing characters to string
- writing characters to strings
- streams, writing characters to strings
- I/O [.NET Framework], writing characters to strings
ms.assetid: 1222cbeb-0760-44bf-9888-914a2a37174b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb35c61b34fa571f35da6691ebe7fa2516eb2df1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947092"
---
# <a name="how-to-write-characters-to-a-string"></a>Postupy: Zápis znaků do řetězce
Následující příklady kódu zápis znaků synchronně nebo asynchronně z pole znaků do řetězce.  
  
## <a name="example-write-characters-synchronously-in-a-console-app"></a>Příklad: Zápis znaků synchronně v konzolové aplikaci  
 V následujícím příkladu <xref:System.IO.StringWriter> pro zápis synchronně do pěti znaků <xref:System.Text.StringBuilder> objektu. 
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example-write-characters-asynchronously-in-a-wpf-app"></a>Příklad: Zápis znaků asynchronně v aplikaci WPF 
 Následující příklad je kódu na pozadí aplikace WPF. Při načtení okna, v příkladu asynchronně přečte všechny znaky z <xref:System.Windows.Controls.TextBox> ovládací prvek a uloží je v poli. Pak asynchronně zapíše každý znak písmeno, nebo prázdné znaky na samostatném řádku <xref:System.Windows.Controls.TextBlock> ovládacího prvku.  
  
 [!code-csharp[StreamReaderWriter](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[StreamReaderWriter](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO.StringWriter>  
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
- <xref:System.Text.StringBuilder>  
- [Vstupně-výstupních operací souborů a datových proudů](../../../docs/standard/io/index.md)  
- [Asynchronní I/O soubory](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [Postupy: Vytvoření výčtu adresářů a souborů](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [Postupy: Čtení a zápis do nově vytvořeného datového souboru](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Postupy: Otevření a připojení k souboru protokolu](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Postupy: Čtení textu ze souboru](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Postupy: Zápis textu do souboru](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Postupy: Čtení znaků z řetězce](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
