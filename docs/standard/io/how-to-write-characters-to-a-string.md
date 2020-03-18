---
title: 'Postup: Zápis znaků do řetězce'
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
ms.openlocfilehash: ecbfa2de2c21ff79df269f74eeddfa0738e7e25c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160274"
---
# <a name="how-to-write-characters-to-a-string"></a>Postup: Zápis znaků do řetězce
Následující příklady kódu zapisují znaky synchronně nebo asynchronně z pole znaků do řetězce.  
  
## <a name="example-write-characters-synchronously-in-a-console-app"></a>Příklad: Zápis znaků synchronně v konzolové aplikaci  
 Následující příklad používá <xref:System.IO.StringWriter> k zápisu pět znaků <xref:System.Text.StringBuilder> synchronně do objektu.
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example-write-characters-asynchronously-in-a-wpf-app"></a>Příklad: Zápis znaků asynchronně v aplikaci WPF
 Dalším příkladem je kód za wpf aplikace. Při načtení okna příklad asynchronně přečte <xref:System.Windows.Controls.TextBox> všechny znaky z ovládacího prvku a uloží je do pole. Potom asynchronně zapíše každé písmeno nebo prázdné místo znak <xref:System.Windows.Controls.TextBlock> na samostatný řádek ovládacího prvku.  
  
 [!code-csharp[StreamReaderWriter](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[StreamReaderWriter](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO.StringWriter>  
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
- <xref:System.Text.StringBuilder>  
- [Vstupně-tono-videa](../../../docs/standard/io/index.md)  
- [Vstupně-nosný soubor asynchronní soubor](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [Postup: Výčet adresářů a souborů](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [Postup: Čtení a zápis do nově vytvořeného datového souboru](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Postup: Otevření a připojení k souboru protokolu](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Postup: Čtení textu ze souboru](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Postup: Zápis textu do souboru](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Postup: Čtení znaků z řetězce](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
