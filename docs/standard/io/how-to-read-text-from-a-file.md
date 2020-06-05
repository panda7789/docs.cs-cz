---
title: 'Postupy: čtení textu ze souboru'
description: V tomto článku najdete příklady způsobu synchronního nebo asynchronního čtení textu z textového souboru pomocí třídy StreamReader v rozhraní .NET pro aplikace klasické pracovní plochy.
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
ms.openlocfilehash: cbdeab3e907b34b6658eef7228fa6567ae198b08
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447053"
---
# <a name="how-to-read-text-from-a-file"></a>Postupy: čtení textu ze souboru
Následující příklady znázorňují způsob synchronního a asynchronního čtení textu z textového souboru pomocí rozhraní .NET pro aplikace klasické pracovní plochy. V obou příkladech můžete při vytváření instance <xref:System.IO.StreamReader> třídy zadat relativní nebo absolutní cestu k souboru.
  
> [!NOTE]
> Tyto příklady kódu se nevztahují na vývoj aplikací pro univerzální platformu Windows (UWP), protože prostředí Windows Runtime poskytuje různé typy datových proudů pro čtení a zápis do souborů. Příklad, který ukazuje, jak číst text ze souboru v aplikaci UWP, najdete v tématu [rychlý Start: čtení a zápis souborů](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)). Příklady, které ukazují, jak převést mezi datovými proudy .NET Framework a prostředí Windows Runtime datových proudů, naleznete v tématu [How to: Convert between .NET Framework Streams and prostředí Windows Runtime Streams](how-to-convert-between-dotnet-streams-and-winrt-streams.md).  
  
## <a name="example-synchronous-read-in-a-console-app"></a>Příklad: synchronní čtení v konzolové aplikaci  
Následující příklad ukazuje synchronní operaci čtení v konzolové aplikaci. Tento příklad otevře textový soubor pomocí čtečky datových proudů, zkopíruje obsah do řetězce a vytvoří výstup řetězce do konzoly.  
  
> [!IMPORTANT]
> V příkladu se předpokládá, že soubor s názvem *Testfile. txt* už existuje ve stejné složce jako aplikace.  

 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example-asynchronous-read-in-a-wpf-app"></a>Příklad: asynchronní čtení v aplikaci WPF
 Následující příklad ukazuje asynchronní operaci čtení v aplikaci Windows Presentation Foundation (WPF).  
  
> [!IMPORTANT]
> V příkladu se předpokládá, že soubor s názvem *Testfile. txt* už existuje ve stejné složce jako aplikace.  

 [!code-csharp[TextFiles](../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.cs)]
 [!code-vb[TextFiles](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [Asynchronní souborový vstup-výstup](asynchronous-file-i-o.md)  
- [Postupy: vytvoření seznamu adresářů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))  
- [Rychlý Start: čtení a zápis souborů](https://docs.microsoft.com/previous-versions/windows/apps/hh758325%28v=win.10%29)  
- [Postupy: převod mezi .NET Frameworkmi proudy a datovými proudy prostředí Windows Runtime](how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
- [Postupy: čtení a zápis do nově vytvořeného datového souboru](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Postupy: otevření a připojení k souboru protokolu](how-to-open-and-append-to-a-log-file.md)  
- [Postupy: zápis textu do souboru](how-to-write-text-to-a-file.md)  
- [Postupy: čtení znaků z řetězce](how-to-read-characters-from-a-string.md)  
- [Postupy: zápis znaků do řetězce](how-to-write-characters-to-a-string.md)  
- [Vstup/výstup souborů a streamů](index.md)
