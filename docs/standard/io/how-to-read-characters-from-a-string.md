---
title: 'Postupy: čtení znaků z řetězce'
description: Naučte se číst znaky z řetězce v .NET. Zobrazit příklady znaku synchronního a asynchronního čtení.
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
ms.openlocfilehash: 40ff144e0899f3560805a31fa76f391afaeccd67
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594839"
---
# <a name="how-to-read-characters-from-a-string"></a>Postupy: čtení znaků z řetězce
Následující příklady kódu znázorňují, jak číst znaky synchronně nebo asynchronně z řetězce.  
  
## <a name="example-read-characters-synchronously"></a>Příklad: synchronní čtení znaků
 Tento příklad načte 13 znaků synchronně z řetězce, uloží je do pole a zobrazí je. Příklad přečte zbytek znaků v řetězci, uloží je do pole začínajícího na šestém prvku a zobrazí obsah pole.  
  
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example-read-characters-asynchronously"></a>Příklad: asynchronní čtení znaků  
 Dalším příkladem je kód za aplikací WPF. Při načtení okna příklad asynchronně načítá všechny znaky z <xref:System.Windows.Controls.TextBox> ovládacího prvku a ukládá je do pole. Potom asynchronně zapisuje každé písmeno nebo prázdné znaky na samostatný řádek <xref:System.Windows.Controls.TextBlock> ovládacího prvku.  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO.StringReader>  
- <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>  
- [Asynchronní souborový vstup-výstup](asynchronous-file-i-o.md)  
- [Postupy: vytvoření seznamu adresářů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))  
- [Postupy: čtení a zápis do nově vytvořeného datového souboru](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Postupy: otevření a připojení k souboru protokolu](how-to-open-and-append-to-a-log-file.md)  
- [Postupy: čtení textu ze souboru](how-to-read-text-from-a-file.md)  
- [Postupy: zápis textu do souboru](how-to-write-text-to-a-file.md)  
- [Postupy: zápis znaků do řetězce](how-to-write-characters-to-a-string.md)  
- [Vstup/výstup souborů a streamů](index.md)
