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
# <a name="how-to-write-text-to-a-file"></a><span data-ttu-id="a3b6d-102">Postupy: Zápis textu do souboru</span><span class="sxs-lookup"><span data-stu-id="a3b6d-102">How to: Write Text to a File</span></span>
<span data-ttu-id="a3b6d-103">Toto téma ukazuje různé způsoby můžete zápis textu do souborů pro aplikace .NET Framework nebo [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="a3b6d-103">This topic shows different ways you can write text to a file for .NET Framework applications or [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span> <span data-ttu-id="a3b6d-104">Následující třídy a metody jsou obvykle používány k zapsání textu do souboru:</span><span class="sxs-lookup"><span data-stu-id="a3b6d-104">The following classes and methods are typically used to write text to a file:</span></span>  
  
-   <span data-ttu-id="a3b6d-105"><xref:System.IO.StreamWriter>-obsahuje metody pro zápis do souboru synchronně (<xref:System.IO.StreamWriter.Write%2A> nebo <xref:System.IO.TextWriter.WriteLine%2A>) nebo asynchronně (<xref:System.IO.StreamWriter.WriteAsync%2A> a <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span><span class="sxs-lookup"><span data-stu-id="a3b6d-105"><xref:System.IO.StreamWriter> - it contains methods to write to a file synchronously (<xref:System.IO.StreamWriter.Write%2A> or <xref:System.IO.TextWriter.WriteLine%2A>) or asynchronously (<xref:System.IO.StreamWriter.WriteAsync%2A> and <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span></span>  
  
-   <span data-ttu-id="a3b6d-106"><xref:System.IO.File>– pro použití s aplikací rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a3b6d-106"><xref:System.IO.File> – to be used with .NET Framework applications.</span></span> <span data-ttu-id="a3b6d-107">Poskytuje statické metody pro zápis textu do souboru, jako <xref:System.IO.File.WriteAllLines%2A> a <xref:System.IO.File.WriteAllText%2A>, nebo přidat text do souboru (<xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A> nebo <xref:System.IO.File.AppendText%2A>).</span><span class="sxs-lookup"><span data-stu-id="a3b6d-107">It provides static methods to write text to a file such as <xref:System.IO.File.WriteAllLines%2A> and <xref:System.IO.File.WriteAllText%2A>, or to append text to a file (<xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A> or <xref:System.IO.File.AppendText%2A>).</span></span>  
  
-   <span data-ttu-id="a3b6d-108">[FileIO](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.aspx) – Pokud chcete použít s [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="a3b6d-108">[FileIO](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.aspx) - to be used with [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span> <span data-ttu-id="a3b6d-109">Obsahuje asynchronní metody pro zápis textu do souboru ([WriteLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writelinesasync.aspx) nebo [WriteTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writetextasync.aspx)) nebo přidat text do souboru ([AppendLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendlinesasync.aspx) nebo [ AppendTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendtextasync.aspx)).</span><span class="sxs-lookup"><span data-stu-id="a3b6d-109">It contains asynchronous methods to write text to a file ([WriteLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writelinesasync.aspx) or [WriteTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writetextasync.aspx)) or to append text to a file ([AppendLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendlinesasync.aspx) or [AppendTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendtextasync.aspx)).</span></span>  
  
 <span data-ttu-id="a3b6d-110">Ukázky jsou jednoduché s cílem zaměřit na úkolu během provádění.</span><span class="sxs-lookup"><span data-stu-id="a3b6d-110">The samples have been kept simple in order to focus on the task being performed.</span></span> <span data-ttu-id="a3b6d-111">Z tohoto důvodu ukázky provést kontrolu minimální chyb a výjimek, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="a3b6d-111">For this reason, the samples perform minimal error checking and exception handling, if any.</span></span> <span data-ttu-id="a3b6d-112">Reálné aplikaci obecně poskytuje robustnější Kontrola chyb a výjimek.</span><span class="sxs-lookup"><span data-stu-id="a3b6d-112">A real-world application generally provides more robust error checking and exception handling.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3b6d-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="a3b6d-113">Example</span></span>  
 <span data-ttu-id="a3b6d-114">Následující příklad ukazuje, jak synchronně zápis textu do nového souboru pomocí <xref:System.IO.StreamWriter> třídy, jeden řádek v čase.</span><span class="sxs-lookup"><span data-stu-id="a3b6d-114">The following example shows how to synchronously write text to a new file using the <xref:System.IO.StreamWriter> class, one line at a time.</span></span> <span data-ttu-id="a3b6d-115">Nový textový soubor je uložit do složky Dokumenty uživatele.</span><span class="sxs-lookup"><span data-stu-id="a3b6d-115">The new text file is saved to the user's My Documents folder.</span></span> <span data-ttu-id="a3b6d-116">Protože <xref:System.IO.StreamWriter> je deklarovaný a vytvoření instance v objektu `using` příkaz, <xref:System.IO.StreamWriter.Dispose%2A> je volána metoda, které automaticky vyprázdní a zavře datového proudu.</span><span class="sxs-lookup"><span data-stu-id="a3b6d-116">Because the <xref:System.IO.StreamWriter> object is declared and instantiated in a `using` statement, the <xref:System.IO.StreamWriter.Dispose%2A> method is invoked which automatically flushes and closes the stream.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeline)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeline)]  
  
## <a name="example"></a><span data-ttu-id="a3b6d-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="a3b6d-117">Example</span></span>  
 <span data-ttu-id="a3b6d-118">Následující příklad ukazuje, jak přidat text do existujícího souboru pomocí <xref:System.IO.StreamWriter> třídy.</span><span class="sxs-lookup"><span data-stu-id="a3b6d-118">The following example shows how to append text to an existing file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="a3b6d-119">Používá stejný textový soubor z předchozího příkladu.</span><span class="sxs-lookup"><span data-stu-id="a3b6d-119">It uses the same text file from the previous example.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#appendtext)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#appendtext)]     
  
## <a name="example"></a><span data-ttu-id="a3b6d-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="a3b6d-120">Example</span></span>  
 <span data-ttu-id="a3b6d-121">Následující příklad ukazuje, jak pro asynchronní zapsání textu do nového souboru pomocí <xref:System.IO.StreamWriter> třídy.</span><span class="sxs-lookup"><span data-stu-id="a3b6d-121">The following example shows how to asynchronously write text to a new file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="a3b6d-122">Chcete-li vyvolání <xref:System.IO.StreamWriter.WriteAsync%2A> metoda, volání metody, které musí být v rámci `async` metoda.</span><span class="sxs-lookup"><span data-stu-id="a3b6d-122">In order to invoke the <xref:System.IO.StreamWriter.WriteAsync%2A> method, the method call needs to be within an `async` method.</span></span> <span data-ttu-id="a3b6d-123">Nový textový soubor je uložit do složky Dokumenty uživatele.</span><span class="sxs-lookup"><span data-stu-id="a3b6d-123">The new text file is saved to the user's My Documents folder.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeasync)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeasync)]  
  
## <a name="example"></a><span data-ttu-id="a3b6d-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="a3b6d-124">Example</span></span>  
 <span data-ttu-id="a3b6d-125">Následující příklad ukazuje, jak zápis textu do nového souboru a připojit nové řádky textu na stejný soubor pomocí <xref:System.IO.File> třídy.</span><span class="sxs-lookup"><span data-stu-id="a3b6d-125">The following example shows how to write text to a new file and append new lines of text to the same file using the <xref:System.IO.File> class.</span></span> <span data-ttu-id="a3b6d-126"><xref:System.IO.File.WriteAllText%2A> a <xref:System.IO.File.AppendAllLines%2A> metody otevřete a zavřete soubor automaticky.</span><span class="sxs-lookup"><span data-stu-id="a3b6d-126">The <xref:System.IO.File.WriteAllText%2A> and <xref:System.IO.File.AppendAllLines%2A> methods open and close the file automatically.</span></span> <span data-ttu-id="a3b6d-127">Pokud cesta, která jste zadali do <xref:System.IO.File.WriteAllText%2A> metoda již existuje, soubor se přepíše.</span><span class="sxs-lookup"><span data-stu-id="a3b6d-127">If the path you provide to the <xref:System.IO.File.WriteAllText%2A> method already exists, the file will be overwritten.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writefile)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writefile)]  
  
## <a name="example"></a><span data-ttu-id="a3b6d-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="a3b6d-128">Example</span></span>  
 <span data-ttu-id="a3b6d-129">Následující příklad ukazuje, jak pro asynchronní zapsání uživatelský vstup do textového souboru v [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="a3b6d-129">The following example shows how to asynchronously write user input to a text file in a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app.</span></span> <span data-ttu-id="a3b6d-130">Kvůli zabezpečení se otevřením souboru z [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace obvykle vyžaduje použití [FileOpenPicker](http://msdn.microsoft.com/library/windows/apps/windows.storage.pickers.fileopenpicker.aspx) ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="a3b6d-130">Because of security considerations, opening a file from a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app typically requires the use of a [FileOpenPicker](http://msdn.microsoft.com/library/windows/apps/windows.storage.pickers.fileopenpicker.aspx) control.</span></span> <span data-ttu-id="a3b6d-131">V tomto příkladu `FileOpenPicker` je vyfiltrovány a zobrazí se textových souborů.</span><span class="sxs-lookup"><span data-stu-id="a3b6d-131">In this example, the `FileOpenPicker` is filtered to show text files.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a3b6d-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="a3b6d-132">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="a3b6d-133">Postupy: vytvoření výčtu adresářů a souborů</span><span class="sxs-lookup"><span data-stu-id="a3b6d-133">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [<span data-ttu-id="a3b6d-134">Postupy: čtení a zápisu do nově vytvořeného datového souboru</span><span class="sxs-lookup"><span data-stu-id="a3b6d-134">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [<span data-ttu-id="a3b6d-135">Postupy: otevření a připojení k souboru protokolu</span><span class="sxs-lookup"><span data-stu-id="a3b6d-135">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [<span data-ttu-id="a3b6d-136">Postupy: čtení textu ze souboru</span><span class="sxs-lookup"><span data-stu-id="a3b6d-136">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [<span data-ttu-id="a3b6d-137">Souborová služba a datový proud I-O</span><span class="sxs-lookup"><span data-stu-id="a3b6d-137">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
