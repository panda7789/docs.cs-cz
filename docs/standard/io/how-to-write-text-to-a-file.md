---
title: "Postupy: Zápis textu do souboru"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- writing text to files
- I/O [.NET Framework], writing text to files
- streams, writing text to files
- data streams, writing text to files
ms.assetid: 060cbe06-2adf-4337-9e7b-961a5c840208
caps.latest.revision: "29"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9605e514be380415d3c8b66ed28ae7de0a52ca1e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-text-to-a-file"></a>Postupy: Zápis textu do souboru
Toto téma ukazuje různé způsoby můžete zápis textu do souborů pro aplikace .NET Framework nebo [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace. Následující třídy a metody jsou obvykle používány k zapsání textu do souboru:  
  
-   <xref:System.IO.StreamWriter>-obsahuje metody pro zápis do souboru synchronně (<xref:System.IO.StreamWriter.Write%2A> nebo <xref:System.IO.TextWriter.WriteLine%2A>) nebo asynchronně (<xref:System.IO.StreamWriter.WriteAsync%2A> a <xref:System.IO.StreamWriter.WriteLineAsync%2A>).  
  
-   <xref:System.IO.File>– pro použití s aplikací rozhraní .NET Framework. Poskytuje statické metody pro zápis textu do souboru, jako <xref:System.IO.File.WriteAllLines%2A> a <xref:System.IO.File.WriteAllText%2A>, nebo přidat text do souboru (<xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A> nebo <xref:System.IO.File.AppendText%2A>).  
  
-   [FileIO](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.aspx) – Pokud chcete použít s [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace. Obsahuje asynchronní metody pro zápis textu do souboru ([WriteLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writelinesasync.aspx) nebo [WriteTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writetextasync.aspx)) nebo přidat text do souboru ([AppendLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendlinesasync.aspx) nebo [ AppendTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendtextasync.aspx)).  
  
 Ukázky jsou jednoduché s cílem zaměřit na úkolu během provádění. Z tohoto důvodu ukázky provést kontrolu minimální chyb a výjimek, pokud existuje. Reálné aplikaci obecně poskytuje robustnější Kontrola chyb a výjimek.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak synchronně zápis textu do nového souboru pomocí <xref:System.IO.StreamWriter> třídy, jeden řádek v čase. Nový textový soubor je uložit do složky Dokumenty uživatele. Protože <xref:System.IO.StreamWriter> je deklarovaný a vytvoření instance v objektu `using` příkaz, <xref:System.IO.StreamWriter.Dispose%2A> je volána metoda, které automaticky vyprázdní a zavře datového proudu.  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeline)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeline)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak přidat text do existujícího souboru pomocí <xref:System.IO.StreamWriter> třídy. Používá stejný textový soubor z předchozího příkladu.  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#appendtext)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#appendtext)]     
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pro asynchronní zapsání textu do nového souboru pomocí <xref:System.IO.StreamWriter> třídy. Chcete-li vyvolání <xref:System.IO.StreamWriter.WriteAsync%2A> metoda, volání metody, které musí být v rámci `async` metoda. Nový textový soubor je uložit do složky Dokumenty uživatele.  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeasync)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeasync)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zápis textu do nového souboru a připojit nové řádky textu na stejný soubor pomocí <xref:System.IO.File> třídy. <xref:System.IO.File.WriteAllText%2A> a <xref:System.IO.File.AppendAllLines%2A> metody otevřete a zavřete soubor automaticky. Pokud cesta, která jste zadali do <xref:System.IO.File.WriteAllText%2A> metoda již existuje, soubor se přepíše.  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writefile)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writefile)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pro asynchronní zapsání uživatelský vstup do textového souboru v [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace. Kvůli zabezpečení se otevřením souboru z [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace obvykle vyžaduje použití [FileOpenPicker](http://msdn.microsoft.com/library/windows/apps/windows.storage.pickers.fileopenpicker.aspx) ovládacího prvku. V tomto příkladu `FileOpenPicker` je vyfiltrovány a zobrazí se textových souborů.  
  
```xaml  
<Page  
    x:Class="OpenFileWindowsStore.MainPage"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:local="using:OpenFileWindowsStore"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    mc:Ignorable="d">  
  
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">  
        <Button Content="save text to a file" HorizontalAlignment="Left" Margin="103,417,0,0" VerticalAlignment="Top"   
                Width="329" Height="86" FontSize="35" Click="Button_Click"/>  
        <TextBox Name="UserInputTextBox"  FontSize="18" HorizontalAlignment="Left" Margin="106,146,0,0"   
                 TextWrapping="Wrap" Text="Write some text here, and select a file to write it to." VerticalAlignment="Top"   
                 Height="201" Width="558" AcceptsReturn="True"/>  
        <TextBlock Name="StatusTextBox" HorizontalAlignment="Left" Margin="106,570,0,147" TextWrapping="Wrap" Text="Status:"   
                   VerticalAlignment="Center" Height="51" Width="1074" FontSize="18" />  
    </Grid>  
</Page>  
```  
  
 [!code-csharp[OpenFileWindowsStore#Code](../../../samples/snippets/csharp/VS_Snippets_CLR/openfilewindowsstore/cs/mainpage.xaml.cs#code)]
 [!code-vb[OpenFileWindowsStore#Code](../../../samples/snippets/visualbasic/VS_Snippets_CLR/openfilewindowsstore/vb/mainpage.xaml.vb#code)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IO.StreamWriter>  
 <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>  
 [Postupy: vytvoření výčtu adresářů a souborů](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [Postupy: čtení a zápisu do nově vytvořeného datového souboru](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [Postupy: otevření a připojení k souboru protokolu](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [Postupy: čtení textu ze souboru](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [Souborová služba a datový proud I-O](../../../docs/standard/io/index.md)
