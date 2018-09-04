---
title: 'Postupy: Zápis textu do souboru'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- writing text to files
- I/O [.NET Framework], writing text to files
- streams, writing text to files
- data streams, writing text to files
ms.assetid: 060cbe06-2adf-4337-9e7b-961a5c840208
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 70b2d04f381fdbc1ae47b1c90649df045e111afa
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43542715"
---
# <a name="how-to-write-text-to-a-file"></a><span data-ttu-id="683ee-102">Postupy: Zápis textu do souboru</span><span class="sxs-lookup"><span data-stu-id="683ee-102">How to: Write Text to a File</span></span>
<span data-ttu-id="683ee-103">Toto téma ukazuje různé způsoby můžete napsat text do souboru pro aplikace .NET Framework nebo [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="683ee-103">This topic shows different ways you can write text to a file for .NET Framework applications or [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span> <span data-ttu-id="683ee-104">Následující třídy a metody se obvykle používají k zápisu textu do souboru:</span><span class="sxs-lookup"><span data-stu-id="683ee-104">The following classes and methods are typically used to write text to a file:</span></span>  
  
-   <span data-ttu-id="683ee-105"><xref:System.IO.StreamWriter> -obsahuje metody pro zápis do souboru synchronně (<xref:System.IO.StreamWriter.Write%2A> nebo <xref:System.IO.TextWriter.WriteLine%2A>) nebo asynchronně (<xref:System.IO.StreamWriter.WriteAsync%2A> a <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span><span class="sxs-lookup"><span data-stu-id="683ee-105"><xref:System.IO.StreamWriter> - it contains methods to write to a file synchronously (<xref:System.IO.StreamWriter.Write%2A> or <xref:System.IO.TextWriter.WriteLine%2A>) or asynchronously (<xref:System.IO.StreamWriter.WriteAsync%2A> and <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span></span>  
  
-   <span data-ttu-id="683ee-106"><xref:System.IO.File> – pro použití s aplikací využívajících rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="683ee-106"><xref:System.IO.File> – to be used with .NET Framework applications.</span></span> <span data-ttu-id="683ee-107">Poskytuje statické metody pro zápis textu do souboru jako <xref:System.IO.File.WriteAllLines%2A> a <xref:System.IO.File.WriteAllText%2A>, nebo přidat text do souboru (<xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A> nebo <xref:System.IO.File.AppendText%2A>).</span><span class="sxs-lookup"><span data-stu-id="683ee-107">It provides static methods to write text to a file such as <xref:System.IO.File.WriteAllLines%2A> and <xref:System.IO.File.WriteAllText%2A>, or to append text to a file (<xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A> or <xref:System.IO.File.AppendText%2A>).</span></span>  
  
-   <span data-ttu-id="683ee-108">[FileIO](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.aspx) – Pokud chcete používat s [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="683ee-108">[FileIO](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.aspx) - to be used with [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span> <span data-ttu-id="683ee-109">Obsahuje asynchronní metody zápisu textu do souboru ([WriteLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writelinesasync.aspx) nebo [WriteTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writetextasync.aspx)) nebo přidat text do souboru ([AppendLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendlinesasync.aspx) nebo [ AppendTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendtextasync.aspx)).</span><span class="sxs-lookup"><span data-stu-id="683ee-109">It contains asynchronous methods to write text to a file ([WriteLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writelinesasync.aspx) or [WriteTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writetextasync.aspx)) or to append text to a file ([AppendLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendlinesasync.aspx) or [AppendTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendtextasync.aspx)).</span></span>  

- <span data-ttu-id="683ee-110"><xref:System.IO.Path> -pro použití na řetězce, které obsahují informace o cestě souboru nebo adresáře.</span><span class="sxs-lookup"><span data-stu-id="683ee-110"><xref:System.IO.Path> - to be used on strings that contain file or directory path information.</span></span> <span data-ttu-id="683ee-111">Obsahuje <xref:System.IO.Path.Combine%2A> metodu, která umožňuje zřetězení řetězců k sestavení cesty k souboru nebo adresáře.</span><span class="sxs-lookup"><span data-stu-id="683ee-111">It contains the <xref:System.IO.Path.Combine%2A> method, which allows concatenation of strings to build a file or directory path.</span></span>


 <span data-ttu-id="683ee-112">Ukázky jsou jednoduché abychom se mohli zaměřit na úloze prováděné.</span><span class="sxs-lookup"><span data-stu-id="683ee-112">The samples have been kept simple in order to focus on the task being performed.</span></span> <span data-ttu-id="683ee-113">Z tohoto důvodu ukázky provést kontrolu minimální chyb a zpracování výjimek, případné.</span><span class="sxs-lookup"><span data-stu-id="683ee-113">For this reason, the samples perform minimal error checking and exception handling, if any.</span></span> <span data-ttu-id="683ee-114">Reálné aplikaci obvykle poskytuje robustnější kontroly chyb a zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="683ee-114">A real-world application generally provides more robust error checking and exception handling.</span></span>  
  
## <a name="example"></a><span data-ttu-id="683ee-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="683ee-115">Example</span></span>  
 <span data-ttu-id="683ee-116">Následující příklad ukazuje, jak synchronně zápis textu do nového souboru pomocí <xref:System.IO.StreamWriter> třídy, jeden řádek v čase.</span><span class="sxs-lookup"><span data-stu-id="683ee-116">The following example shows how to synchronously write text to a new file using the <xref:System.IO.StreamWriter> class, one line at a time.</span></span> <span data-ttu-id="683ee-117">Nový textový soubor se uloží do složky Dokumenty uživatele.</span><span class="sxs-lookup"><span data-stu-id="683ee-117">The new text file is saved to the user's My Documents folder.</span></span> <span data-ttu-id="683ee-118">Protože <xref:System.IO.StreamWriter> objekt je deklarovaný a instance v `using` příkaz, <xref:System.IO.StreamWriter.Dispose%2A> vyvolání metody, které automaticky vyprázdní a zavře datový proud.</span><span class="sxs-lookup"><span data-stu-id="683ee-118">Because the <xref:System.IO.StreamWriter> object is declared and instantiated in a `using` statement, the <xref:System.IO.StreamWriter.Dispose%2A> method is invoked which automatically flushes and closes the stream.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeline)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeline)]  
  
## <a name="example"></a><span data-ttu-id="683ee-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="683ee-119">Example</span></span>  
 <span data-ttu-id="683ee-120">Následující příklad ukazuje, jak připojit text k existující soubor pomocí <xref:System.IO.StreamWriter> třídy.</span><span class="sxs-lookup"><span data-stu-id="683ee-120">The following example shows how to append text to an existing file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="683ee-121">Používá stejný textový soubor z předchozího příkladu.</span><span class="sxs-lookup"><span data-stu-id="683ee-121">It uses the same text file from the previous example.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#appendtext)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#appendtext)]     
  
## <a name="example"></a><span data-ttu-id="683ee-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="683ee-122">Example</span></span>  
 <span data-ttu-id="683ee-123">Následující příklad ukazuje způsob asynchronního zápisu textu do nového souboru pomocí <xref:System.IO.StreamWriter> třídy.</span><span class="sxs-lookup"><span data-stu-id="683ee-123">The following example shows how to asynchronously write text to a new file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="683ee-124">Aby bylo možné vyvolat <xref:System.IO.StreamWriter.WriteAsync%2A> metody volání metody, které musí být v rámci `async` metoda.</span><span class="sxs-lookup"><span data-stu-id="683ee-124">In order to invoke the <xref:System.IO.StreamWriter.WriteAsync%2A> method, the method call needs to be within an `async` method.</span></span> <span data-ttu-id="683ee-125">Nový textový soubor se uloží do složky Dokumenty uživatele.</span><span class="sxs-lookup"><span data-stu-id="683ee-125">The new text file is saved to the user's My Documents folder.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeasync)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeasync)]  
  
## <a name="example"></a><span data-ttu-id="683ee-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="683ee-126">Example</span></span>  
 <span data-ttu-id="683ee-127">Následující příklad ukazuje, jak zápis textu do nového souboru a přidávat nové řádky textu do stejného souboru pomocí <xref:System.IO.File> třídy.</span><span class="sxs-lookup"><span data-stu-id="683ee-127">The following example shows how to write text to a new file and append new lines of text to the same file using the <xref:System.IO.File> class.</span></span> <span data-ttu-id="683ee-128"><xref:System.IO.File.WriteAllText%2A> a <xref:System.IO.File.AppendAllLines%2A> metod otevřete a zavřete soubor automaticky.</span><span class="sxs-lookup"><span data-stu-id="683ee-128">The <xref:System.IO.File.WriteAllText%2A> and <xref:System.IO.File.AppendAllLines%2A> methods open and close the file automatically.</span></span> <span data-ttu-id="683ee-129">Pokud ji zadáte do <xref:System.IO.File.WriteAllText%2A> metoda již existuje, soubor se přepíše.</span><span class="sxs-lookup"><span data-stu-id="683ee-129">If the path you provide to the <xref:System.IO.File.WriteAllText%2A> method already exists, the file will be overwritten.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writefile)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writefile)]  
  
## <a name="example"></a><span data-ttu-id="683ee-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="683ee-130">Example</span></span>  
 <span data-ttu-id="683ee-131">Následující příklad ukazuje, jak asynchronního zápisu vstupu uživatele do textového souboru v [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="683ee-131">The following example shows how to asynchronously write user input to a text file in a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app.</span></span> <span data-ttu-id="683ee-132">Kvůli zabezpečení, otevřete soubor z [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace obvykle vyžaduje použití [FileOpenPicker](https://msdn.microsoft.com/library/windows/apps/windows.storage.pickers.fileopenpicker.aspx) ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="683ee-132">Because of security considerations, opening a file from a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app typically requires the use of a [FileOpenPicker](https://msdn.microsoft.com/library/windows/apps/windows.storage.pickers.fileopenpicker.aspx) control.</span></span> <span data-ttu-id="683ee-133">V tomto příkladu `FileOpenPicker` se vyfiltruje a zobrazí textové soubory.</span><span class="sxs-lookup"><span data-stu-id="683ee-133">In this example, the `FileOpenPicker` is filtered to show text files.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="683ee-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="683ee-134">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 <xref:System.IO.Path>  
 <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="683ee-135">Postupy: Vytvoření výčtu adresářů a souborů</span><span class="sxs-lookup"><span data-stu-id="683ee-135">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [<span data-ttu-id="683ee-136">Postupy: Čtení a zápis do nově vytvořeného datového souboru</span><span class="sxs-lookup"><span data-stu-id="683ee-136">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [<span data-ttu-id="683ee-137">Postupy: Otevření a připojení k souboru protokolu</span><span class="sxs-lookup"><span data-stu-id="683ee-137">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [<span data-ttu-id="683ee-138">Postupy: Čtení textu ze souboru</span><span class="sxs-lookup"><span data-stu-id="683ee-138">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [<span data-ttu-id="683ee-139">Vstup/výstup souborů a streamů</span><span class="sxs-lookup"><span data-stu-id="683ee-139">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
