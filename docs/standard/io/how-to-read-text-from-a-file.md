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
ms.openlocfilehash: 0d8dfae67ede779a611204fb333a19defcaee8e6
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87382123"
---
# <a name="how-to-read-text-from-a-file"></a>Postupy: čtení textu ze souboru
Následující příklady znázorňují způsob synchronního a asynchronního čtení textu z textového souboru pomocí rozhraní .NET pro aplikace klasické pracovní plochy. V obou příkladech můžete při vytváření instance <xref:System.IO.StreamReader> třídy zadat relativní nebo absolutní cestu k souboru.
  
> [!NOTE]
> Tyto příklady kódu se nevztahují na vývoj aplikací pro univerzální platformu Windows (UWP), protože prostředí Windows Runtime poskytuje různé typy datových proudů pro čtení a zápis do souborů. Příklad, který ukazuje, jak číst text ze souboru v aplikaci UWP, najdete v tématu [rychlý Start: čtení a zápis souborů](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)). Příklady, které ukazují, jak převést mezi datovými proudy .NET Framework a prostředí Windows Runtime datových proudů, naleznete v tématu [How to: Convert between .NET Framework Streams and prostředí Windows Runtime Streams](how-to-convert-between-dotnet-streams-and-winrt-streams.md).  
  
## <a name="example-synchronous-read-in-a-console-app"></a>Příklad: synchronní čtení v konzolové aplikaci  
Následující příklad ukazuje synchronní operaci čtení v konzolové aplikaci. Tento příklad otevře textový soubor pomocí čtečky datových proudů, zkopíruje obsah do řetězce a vytvoří výstup řetězce do konzoly.  
  
> [!IMPORTANT]
> Příklad předpokládá, že soubor s názvem *TestFile.txt* již existuje ve stejné složce jako aplikace.  

:::code language="csharp" source="snippets/how-to-read-text-from-a-file/csharp/sync-console/Program.cs":::
:::code language="vb" source="snippets/how-to-read-text-from-a-file/vb/sync-console/Program.vb":::
  
## <a name="example-asynchronous-read-in-a-wpf-app"></a>Příklad: asynchronní čtení v aplikaci WPF
 Následující příklad ukazuje asynchronní operaci čtení v aplikaci Windows Presentation Foundation (WPF).  
  
> [!IMPORTANT]
> Příklad předpokládá, že soubor s názvem *TestFile.txt* již existuje ve stejné složce jako aplikace.  

:::code language="csharp" source="snippets/how-to-read-text-from-a-file/csharp/async-wpf/MainWindow.xaml.cs":::
:::code language="vb" source="snippets/how-to-read-text-from-a-file/vb/async-wpf/MainWindow.xaml.vb":::
  
## <a name="see-also"></a>Viz také:

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
