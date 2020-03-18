---
title: 'Postup: Čtení textu ze souboru'
ms.date: 01/03/2019
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
ms.openlocfilehash: 8676e5f0acd0646b4854df7dde060ec15548ec3e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155721"
---
# <a name="how-to-read-text-from-a-file"></a>Postup: Čtení textu ze souboru
Následující příklady znázorňují způsob synchronního a asynchronního čtení textu z textového souboru pomocí rozhraní .NET pro aplikace klasické pracovní plochy. V obou příkladech při vytváření instance <xref:System.IO.StreamReader> třídy zadáte relativní nebo absolutní cestu k souboru.
  
> [!NOTE]
> Tyto příklady kódu se nevztahují na vývoj aplikací pro univerzální Windows (UPW), protože prostředí Windows Runtime poskytuje různé typy datových proudů pro čtení a zápis do souborů. Příklad, který ukazuje, jak číst text ze souboru v aplikaci UPW, najdete v [tématu Úvodní příručka: Čtení a zápis souborů](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)). Příklady, které ukazují, jak převést mezi datovými proudy rozhraní .NET Framework a datovými proudy prostředí Windows Runtime, naleznete v [tématu How to: Convert between .NET Framework streams and Windows Runtime streams](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).  
  
## <a name="example-synchronous-read-in-a-console-app"></a>Příklad: Synchronní čtení v konzolové aplikaci  
Následující příklad ukazuje synchronní operaci čtení v rámci konzolové aplikace. Tento příklad otevře textový soubor pomocí čtečky datových proudů, zkopíruje obsah do řetězce a výstupy řetězec do konzoly.  
  
> [!IMPORTANT]
> Příklad předpokládá, že soubor s názvem *TestFile.txt* již existuje ve stejné složce jako aplikace.  

 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example-asynchronous-read-in-a-wpf-app"></a>Příklad: Asynchronní čtení v aplikaci WPF
 Následující příklad ukazuje asynchronní operaci čtení v aplikaci WPF (Windows Presentation Foundation).  
  
> [!IMPORTANT]
> Příklad předpokládá, že soubor s názvem *TestFile.txt* již existuje ve stejné složce jako aplikace.  

 [!code-csharp[TextFiles](../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.cs)]
 [!code-vb[TextFiles](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [Vstupně-nosný soubor asynchronní soubor](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [Postup: Vytvoření výpisu adresáře](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))  
- [Úvodní příručka: Čtení a zápis souborů](https://docs.microsoft.com/previous-versions/windows/apps/hh758325%28v=win.10%29)  
- [Postup: Převod mezi datovými proudy rozhraní .NET Framework a Datovými proudy prostředí Windows Runtime](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
- [Postup: Čtení a zápis do nově vytvořeného datového souboru](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Postup: Otevření a připojení k souboru protokolu](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Postup: Zápis textu do souboru](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Postup: Čtení znaků z řetězce](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [Postup: Zápis znaků do řetězce](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [Vstupně-tono-videa](../../../docs/standard/io/index.md)
