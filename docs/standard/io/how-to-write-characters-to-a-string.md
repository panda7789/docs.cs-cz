---
title: 'Postupy: zápis znaků do řetězce'
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
ms.openlocfilehash: 04fc21c452258a88292a886d952353ac55573121
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288248"
---
# <a name="how-to-write-characters-to-a-string"></a>Postupy: zápis znaků do řetězce
Následující příklady kódu píší synchronně nebo asynchronně z pole znaků do řetězce.  
  
## <a name="example-write-characters-synchronously-in-a-console-app"></a>Příklad: synchronní zápis znaků v konzolové aplikaci  
 Následující příklad používá <xref:System.IO.StringWriter> k zápisu pěti znaků synchronně do <xref:System.Text.StringBuilder> objektu.
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example-write-characters-asynchronously-in-a-wpf-app"></a>Příklad: asynchronní zápis znaků v aplikaci WPF
 Dalším příkladem je kód za aplikací WPF. Při načtení okna příklad asynchronně načítá všechny znaky z <xref:System.Windows.Controls.TextBox> ovládacího prvku a ukládá je do pole. Potom asynchronně zapisuje každé písmeno nebo prázdné znaky na samostatný řádek <xref:System.Windows.Controls.TextBlock> ovládacího prvku.  
  
 [!code-csharp[StreamReaderWriter](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[StreamReaderWriter](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO.StringWriter>  
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
- <xref:System.Text.StringBuilder>  
- [Vstup/výstup souborů a streamů](index.md)  
- [Asynchronní souborový vstup-výstup](asynchronous-file-i-o.md)  
- [Postupy: zobrazení výčtu adresářů a souborů](how-to-enumerate-directories-and-files.md)  
- [Postupy: čtení a zápis do nově vytvořeného datového souboru](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Postupy: otevření a připojení k souboru protokolu](how-to-open-and-append-to-a-log-file.md)  
- [Postupy: čtení textu ze souboru](how-to-read-text-from-a-file.md)  
- [Postupy: zápis textu do souboru](how-to-write-text-to-a-file.md)  
- [Postupy: čtení znaků z řetězce](how-to-read-characters-from-a-string.md)
