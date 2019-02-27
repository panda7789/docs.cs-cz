---
title: 'Postupy: Čtení textu ze souboru'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7330c209ce6514459d3ab1dd58dc1c80b1978a56
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2019
ms.locfileid: "56834950"
---
# <a name="how-to-read-text-from-a-file"></a>Postupy: Čtení textu ze souboru
Následující příklady znázorňují způsob synchronního a asynchronního čtení textu z textového souboru pomocí rozhraní .NET pro aplikace klasické pracovní plochy. V obou příkladech je při vytváření instance třídy <xref:System.IO.StreamReader> třídu, zadejte relativní nebo absolutní cesta k souboru. 
  
> [!NOTE]
> Tyto příklady kódu se nevztahují na vývoj pro aplikace pro Universal Windows (UPW), protože modul Windows Runtime poskytuje různé stream typy pro čtení a zápis do souborů. Příklad, který znázorňuje způsob čtení textu ze souboru v aplikaci UWP, naleznete v tématu [rychlý start: Čtení a zápis do souborů](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)). Příklady, které ukazují, jak k převodu mezi datovými proudy rozhraní .NET Framework a datovými proudy Windows Runtime naleznete v tématu [jak: Převod mezi datovými proudy rozhraní .NET Framework a datovými proudy Windows Runtime](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).  
  
## <a name="example-synchronous-read-in-a-console-app"></a>Příklad: Synchronní číst v konzolové aplikaci  
Následující příklad ukazuje operaci synchronního čtení v rámci konzolové aplikace. Tento příklad otevře textový soubor pomocí čtečku datového proudu, zkopíruje obsah na řetězec a vypíše řetězec do konzoly.  
  
> [!IMPORTANT]
> Příklad předpokládá, že soubor s názvem *TestFile.txt* již existuje ve stejné složce jako aplikace.  

 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example-asynchronous-read-in-a-wpf-app"></a>Příklad: Asynchronní čtení v aplikaci WPF 
 Následující příklad ukazuje operaci asynchronního čtení v aplikaci Windows Presentation Foundation (WPF).  
  
> [!IMPORTANT]
> Příklad předpokládá, že soubor s názvem *TestFile.txt* již existuje ve stejné složce jako aplikace.  

 [!code-csharp[TextFiles](../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.cs)]
 [!code-vb[TextFiles](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [Asynchronní I/O soubory](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [Postupy: Vytváření adresářů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))  
- [Rychlý start: Čtení a zápis do souborů](https://docs.microsoft.com/previous-versions/windows/apps/hh758325%28v=win.10%29)  
- [Postupy: Převod mezi datovými proudy rozhraní .NET Framework a datovými proudy Windows Runtime](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
- [Postupy: Čtení a zápis do nově vytvořeného datového souboru](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Postupy: Otevření a připojení k souboru protokolu](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Postupy: Zápis textu do souboru](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Postupy: Čtení znaků z řetězce](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [Postupy: Zápis znaků do řetězce](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [Vstupně-výstupních operací souborů a datových proudů](../../../docs/standard/io/index.md)
