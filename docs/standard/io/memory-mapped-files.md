---
title: Soubory mapované paměti
description: Prozkoumejte soubory mapované v paměti v rozhraní .NET, které obsahují obsah souborů ve virtuální paměti a umožňují aplikacím upravovat soubor zápisem přímo do paměti.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- memory-mapped files
- inter-process communication
ms.assetid: a483d1b5-64aa-45b6-86ef-11b859f7f02e
ms.openlocfilehash: db63c15357b0670c55b1174b91b02e2f49a0c4c1
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2020
ms.locfileid: "84661976"
---
# <a name="memory-mapped-files"></a><span data-ttu-id="83f9a-103">Soubory mapované paměti</span><span class="sxs-lookup"><span data-stu-id="83f9a-103">Memory-Mapped Files</span></span>
<span data-ttu-id="83f9a-104">Soubor mapované paměti obsahuje obsah souboru ve virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="83f9a-104">A memory-mapped file contains the contents of a file in virtual memory.</span></span> <span data-ttu-id="83f9a-105">Toto mapování mezi souborem a prostorem paměti umožňuje aplikaci, včetně více procesů, pro úpravu souboru čtením a zápisem přímo do paměti.</span><span class="sxs-lookup"><span data-stu-id="83f9a-105">This mapping between a file and memory space enables an application, including multiple processes, to modify the file by reading and writing directly to the memory.</span></span> <span data-ttu-id="83f9a-106">Počínaje .NET Framework 4 můžete použít spravovaný kód pro přístup k souborům mapovaným do paměti stejným způsobem jako nativní funkce systému Windows přistupující k souborům mapovaným do paměti, jak je popsáno v tématu [Správa souborů mapovaných](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10))do paměti.</span><span class="sxs-lookup"><span data-stu-id="83f9a-106">Starting with the .NET Framework 4, you can use managed code to access memory-mapped files in the same way that native Windows functions access memory-mapped files, as described in [Managing Memory-Mapped Files](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10)).</span></span>  
  
 <span data-ttu-id="83f9a-107">Existují dva typy souborů mapovaných do paměti:</span><span class="sxs-lookup"><span data-stu-id="83f9a-107">There are two types of memory-mapped files:</span></span>  
  
- <span data-ttu-id="83f9a-108">Trvalá paměťově mapované soubory</span><span class="sxs-lookup"><span data-stu-id="83f9a-108">Persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="83f9a-109">Trvalé soubory jsou soubory mapované paměti, které jsou přidruženy ke zdrojovému souboru na disku.</span><span class="sxs-lookup"><span data-stu-id="83f9a-109">Persisted files are memory-mapped files that are associated with a source file on a disk.</span></span> <span data-ttu-id="83f9a-110">Až poslední proces dokončí práci se souborem, data se uloží do zdrojového souboru na disku.</span><span class="sxs-lookup"><span data-stu-id="83f9a-110">When the last process has finished working with the file, the data is saved to the source file on the disk.</span></span> <span data-ttu-id="83f9a-111">Tyto soubory mapované paměti jsou vhodné pro práci s extrémně velkými zdrojovými soubory.</span><span class="sxs-lookup"><span data-stu-id="83f9a-111">These memory-mapped files are suitable for working with extremely large source files.</span></span>  
  
- <span data-ttu-id="83f9a-112">Netrvalá paměťově mapované soubory</span><span class="sxs-lookup"><span data-stu-id="83f9a-112">Non-persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="83f9a-113">Netrvalé soubory jsou soubory mapované paměti, které nejsou přidruženy k souboru na disku.</span><span class="sxs-lookup"><span data-stu-id="83f9a-113">Non-persisted files are memory-mapped files that are not associated with a file on a disk.</span></span> <span data-ttu-id="83f9a-114">Až poslední proces dokončí práci se souborem, data se ztratí a soubor se uvolní uvolňováním paměti.</span><span class="sxs-lookup"><span data-stu-id="83f9a-114">When the last process has finished working with the file, the data is lost and the file is reclaimed by garbage collection.</span></span> <span data-ttu-id="83f9a-115">Tyto soubory jsou vhodné pro vytváření sdílené paměti pro komunikaci mezi procesy (IPC).</span><span class="sxs-lookup"><span data-stu-id="83f9a-115">These files are suitable for creating shared memory for inter-process communications (IPC).</span></span>  
  
## <a name="processes-views-and-managing-memory"></a><span data-ttu-id="83f9a-116">Procesy, zobrazení a správa paměti</span><span class="sxs-lookup"><span data-stu-id="83f9a-116">Processes, Views, and Managing Memory</span></span>  
 <span data-ttu-id="83f9a-117">Soubory mapované paměti lze sdílet mezi několika procesy.</span><span class="sxs-lookup"><span data-stu-id="83f9a-117">Memory-mapped files can be shared across multiple processes.</span></span> <span data-ttu-id="83f9a-118">Procesy lze namapovat na stejný soubor mapované paměti pomocí běžného názvu, který je přiřazen procesem, který soubor vytvořil.</span><span class="sxs-lookup"><span data-stu-id="83f9a-118">Processes can map to the same memory-mapped file by using a common name that is assigned by the process that created the file.</span></span>  
  
 <span data-ttu-id="83f9a-119">Chcete-li pracovat se souborem mapované paměti, je nutné vytvořit zobrazení celého souboru mapované paměti nebo jeho části.</span><span class="sxs-lookup"><span data-stu-id="83f9a-119">To work with a memory-mapped file, you must create a view of the entire memory-mapped file or a part of it.</span></span> <span data-ttu-id="83f9a-120">Můžete také vytvořit více zobrazení do stejné části souboru mapované paměti, čímž vytvoříte souběžnou paměť.</span><span class="sxs-lookup"><span data-stu-id="83f9a-120">You can also create multiple views to the same part of the memory-mapped file, thereby creating concurrent memory.</span></span> <span data-ttu-id="83f9a-121">Aby dvě zobrazení zůstaly souběžně, je nutné je vytvořit ze stejného souboru mapované paměti.</span><span class="sxs-lookup"><span data-stu-id="83f9a-121">For two views to remain concurrent, they have to be created from the same memory-mapped file.</span></span>  
  
 <span data-ttu-id="83f9a-122">V případě, že je soubor větší než velikost logické paměti, která je k dispozici pro mapování paměti (2 GB na 32 počítači), může být také nutné použít více zobrazení.</span><span class="sxs-lookup"><span data-stu-id="83f9a-122">Multiple views may also be necessary if the file is greater than the size of the application’s logical memory space available for memory mapping (2 GB on a 32-bit computer).</span></span>  
  
 <span data-ttu-id="83f9a-123">K dispozici jsou dva typy zobrazení: zobrazení datového proudu a zobrazení náhodného přístupu.</span><span class="sxs-lookup"><span data-stu-id="83f9a-123">There are two types of views: stream access view and random access view.</span></span> <span data-ttu-id="83f9a-124">Pro sekvenční přístup k souboru použijte zobrazení přístupu ke službě Stream. Tento postup se doporučuje u souborů, které nejsou trvale uložené, a IPC.</span><span class="sxs-lookup"><span data-stu-id="83f9a-124">Use stream access views for sequential access to a file; this is recommended for non-persisted files and IPC.</span></span> <span data-ttu-id="83f9a-125">Zobrazení náhodného přístupu jsou upřednostňována pro práci s trvalými soubory.</span><span class="sxs-lookup"><span data-stu-id="83f9a-125">Random access views are preferred for working with persisted files.</span></span>  
  
 <span data-ttu-id="83f9a-126">Soubory mapované paměti jsou k dispozici prostřednictvím Správce paměti operačního systému, takže soubor je automaticky rozdělený na několik stránek a v případě potřeby je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="83f9a-126">Memory-mapped files are accessed through the operating system’s memory manager, so the file is automatically partitioned into a number of pages and accessed as needed.</span></span> <span data-ttu-id="83f9a-127">Správu paměti není nutné zpracovávat sami.</span><span class="sxs-lookup"><span data-stu-id="83f9a-127">You do not have to handle the memory management yourself.</span></span>  
  
 <span data-ttu-id="83f9a-128">Následující ilustrace znázorňuje, jak více procesů může mít více a překrývajících se zobrazení do stejného souboru mapované paměti ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="83f9a-128">The following illustration shows how multiple processes can have multiple and overlapping views to the same memory-mapped file at the same time.</span></span>

 <span data-ttu-id="83f9a-129">Následující obrázek ukazuje více a překrývajících se zobrazení do souboru mapované paměti:</span><span class="sxs-lookup"><span data-stu-id="83f9a-129">The following image shows multiple and overlapped views to a memory-mapped file:</span></span>  
  
 ![Snímek obrazovky, který zobrazuje zobrazení&#45;namapovaného souboru do paměti](./media/memory-mapped-files/memory-map-persist-file.png)  
  
## <a name="programming-with-memory-mapped-files"></a><span data-ttu-id="83f9a-131">Programování s namapovanými soubory paměti</span><span class="sxs-lookup"><span data-stu-id="83f9a-131">Programming with Memory-Mapped Files</span></span>  
 <span data-ttu-id="83f9a-132">Následující tabulka poskytuje návod pro použití objektů souboru mapovaných do paměti a jejich členů.</span><span class="sxs-lookup"><span data-stu-id="83f9a-132">The following table provides a guide for using memory-mapped file objects and their members.</span></span>  
  
|<span data-ttu-id="83f9a-133">Úkol</span><span class="sxs-lookup"><span data-stu-id="83f9a-133">Task</span></span>|<span data-ttu-id="83f9a-134">Metody nebo vlastnosti, které se mají použít</span><span class="sxs-lookup"><span data-stu-id="83f9a-134">Methods or properties to use</span></span>|  
|----------|----------------------------------|  
|<span data-ttu-id="83f9a-135">Chcete-li získat <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> objekt, který představuje trvalý soubor mapované paměti ze souboru na disku.</span><span class="sxs-lookup"><span data-stu-id="83f9a-135">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a persisted memory-mapped file from a file on disk.</span></span>|<span data-ttu-id="83f9a-136"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>Metoda.</span><span class="sxs-lookup"><span data-stu-id="83f9a-136"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="83f9a-137">Chcete-li získat <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> objekt, který představuje netrvalý soubor mapované paměti (není přidružen k souboru na disku).</span><span class="sxs-lookup"><span data-stu-id="83f9a-137">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a non-persisted memory-mapped file (not associated with a file on disk).</span></span>|<span data-ttu-id="83f9a-138"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>Metoda.</span><span class="sxs-lookup"><span data-stu-id="83f9a-138"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> method.</span></span><br /><br /> <span data-ttu-id="83f9a-139">- nebo -</span><span class="sxs-lookup"><span data-stu-id="83f9a-139">- or -</span></span><br /><br /> <span data-ttu-id="83f9a-140"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>Metoda.</span><span class="sxs-lookup"><span data-stu-id="83f9a-140"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="83f9a-141">Chcete-li získat <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> objekt existujícího souboru mapované paměti (buď trvalá, nebo netrvalá).</span><span class="sxs-lookup"><span data-stu-id="83f9a-141">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object of an existing memory-mapped file (either persisted or non-persisted).</span></span>|<span data-ttu-id="83f9a-142"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType>Metoda.</span><span class="sxs-lookup"><span data-stu-id="83f9a-142"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="83f9a-143">Pro získání <xref:System.IO.UnmanagedMemoryStream> objektu pro sekvenční zobrazení k souboru mapované paměti.</span><span class="sxs-lookup"><span data-stu-id="83f9a-143">To obtain a <xref:System.IO.UnmanagedMemoryStream> object for a sequentially accessed view to the memory-mapped file.</span></span>|<span data-ttu-id="83f9a-144"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType>Metoda.</span><span class="sxs-lookup"><span data-stu-id="83f9a-144"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="83f9a-145">Chcete-li získat <xref:System.IO.UnmanagedMemoryAccessor> objekt pro zobrazení náhodného přístupu k fie mapované paměti.</span><span class="sxs-lookup"><span data-stu-id="83f9a-145">To obtain a <xref:System.IO.UnmanagedMemoryAccessor> object for a random access view to a memory-mapped fie.</span></span>|<span data-ttu-id="83f9a-146"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType>Metoda.</span><span class="sxs-lookup"><span data-stu-id="83f9a-146"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="83f9a-147">Pro získání <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> objektu pro použití s nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="83f9a-147">To obtain a <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> object to use with unmanaged code.</span></span>|<span data-ttu-id="83f9a-148"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType>majetek.</span><span class="sxs-lookup"><span data-stu-id="83f9a-148"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="83f9a-149">- nebo -</span><span class="sxs-lookup"><span data-stu-id="83f9a-149">- or -</span></span><br /><br /> <span data-ttu-id="83f9a-150"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>majetek.</span><span class="sxs-lookup"><span data-stu-id="83f9a-150"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="83f9a-151">- nebo -</span><span class="sxs-lookup"><span data-stu-id="83f9a-151">- or -</span></span><br /><br /> <span data-ttu-id="83f9a-152"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>majetek.</span><span class="sxs-lookup"><span data-stu-id="83f9a-152"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span>|  
|<span data-ttu-id="83f9a-153">Zpoždění přidělení paměti, dokud není vytvořeno zobrazení (pouze netrvalé soubory).</span><span class="sxs-lookup"><span data-stu-id="83f9a-153">To delay allocating memory until a view is created (non-persisted files only).</span></span><br /><br /> <span data-ttu-id="83f9a-154">(Chcete-li zjistit aktuální velikost stránky systému, použijte <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> vlastnost.)</span><span class="sxs-lookup"><span data-stu-id="83f9a-154">(To determine the current system page size, use the <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> property.)</span></span>|<span data-ttu-id="83f9a-155"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A>Metoda s <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> hodnotou.</span><span class="sxs-lookup"><span data-stu-id="83f9a-155"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> method with the <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> value.</span></span><br /><br /> <span data-ttu-id="83f9a-156">- nebo -</span><span class="sxs-lookup"><span data-stu-id="83f9a-156">- or -</span></span><br /><br /> <span data-ttu-id="83f9a-157"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A>metody, které mají <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> výčet jako parametr.</span><span class="sxs-lookup"><span data-stu-id="83f9a-157"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods that have a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> enumeration as a parameter.</span></span>|  
  
### <a name="security"></a><span data-ttu-id="83f9a-158">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="83f9a-158">Security</span></span>  
 <span data-ttu-id="83f9a-159">Přístupová práva můžete použít při vytváření souboru mapované paměti pomocí následujících metod, které přijímají <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> výčet jako parametr:</span><span class="sxs-lookup"><span data-stu-id="83f9a-159">You can apply access rights when you create a memory-mapped file, by using the following methods that take a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> enumeration as a parameter:</span></span>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="83f9a-160">Můžete zadat přístupová práva pro otevření existujícího souboru mapované paměti pomocí <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> metod, které přijímají <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> jako parametr.</span><span class="sxs-lookup"><span data-stu-id="83f9a-160">You can specify access rights for opening an existing memory-mapped file by using the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> methods that take an <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> as a parameter.</span></span>  
  
 <span data-ttu-id="83f9a-161">Kromě toho můžete zahrnout <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> objekt, který obsahuje pravidla předdefinovaného přístupu.</span><span class="sxs-lookup"><span data-stu-id="83f9a-161">In addition, you can include a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> object that contains predefined access rules.</span></span>  
  
 <span data-ttu-id="83f9a-162">Chcete-li použít nová nebo změněná pravidla přístupu k souboru mapované paměti, použijte <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="83f9a-162">To apply new or changed access rules to a memory-mapped file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> method.</span></span> <span data-ttu-id="83f9a-163">Chcete-li načíst pravidla přístupu nebo auditu z existujícího souboru, použijte <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="83f9a-163">To retrieve access or audit rules from an existing file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="83f9a-164">Příklady</span><span class="sxs-lookup"><span data-stu-id="83f9a-164">Examples</span></span>  
  
### <a name="persisted-memory-mapped-files"></a><span data-ttu-id="83f9a-165">Trvalá paměťově mapované soubory</span><span class="sxs-lookup"><span data-stu-id="83f9a-165">Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="83f9a-166"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A>Metody vytvoří soubor mapované paměti z existujícího souboru na disku.</span><span class="sxs-lookup"><span data-stu-id="83f9a-166">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> methods create a memory-mapped file from an existing file on disk.</span></span>  
  
 <span data-ttu-id="83f9a-167">Následující příklad vytvoří zobrazení mapované paměti, které je součástí velmi velkého souboru a pracuje s jeho částí.</span><span class="sxs-lookup"><span data-stu-id="83f9a-167">The following example creates a memory-mapped view of a part of an extremely large file and manipulates a portion of it.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

 <span data-ttu-id="83f9a-168">Následující příklad otevře stejný soubor mapované paměti pro jiný proces.</span><span class="sxs-lookup"><span data-stu-id="83f9a-168">The following example opens the same memory-mapped file for another process.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a><span data-ttu-id="83f9a-169">Netrvalá paměťově mapované soubory</span><span class="sxs-lookup"><span data-stu-id="83f9a-169">Non-Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="83f9a-170"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A>Metody a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> vytvoří soubor mapované paměti, který není namapován na existující soubor na disku.</span><span class="sxs-lookup"><span data-stu-id="83f9a-170">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> and <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods create a memory-mapped file that is not mapped to an existing file on disk.</span></span>  
  
 <span data-ttu-id="83f9a-171">Následující příklad obsahuje tři samostatné procesy (konzolové aplikace), které zapisují logické hodnoty do souboru mapované paměti.</span><span class="sxs-lookup"><span data-stu-id="83f9a-171">The following example consists of three separate processes (console applications) that write Boolean values to a memory-mapped file.</span></span> <span data-ttu-id="83f9a-172">Dojde k následujícímu pořadí akcí:</span><span class="sxs-lookup"><span data-stu-id="83f9a-172">The following sequence of actions occur:</span></span>  
  
1. <span data-ttu-id="83f9a-173">`Process A`Vytvoří soubor mapované paměti a zapíše do něj hodnotu.</span><span class="sxs-lookup"><span data-stu-id="83f9a-173">`Process A` creates the memory-mapped file and writes a value to it.</span></span>  
  
2. <span data-ttu-id="83f9a-174">`Process B`otevře soubor mapované paměti a zapíše do něj hodnotu.</span><span class="sxs-lookup"><span data-stu-id="83f9a-174">`Process B` opens the memory-mapped file and writes a value to it.</span></span>  
  
3. <span data-ttu-id="83f9a-175">`Process C`otevře soubor mapované paměti a zapíše do něj hodnotu.</span><span class="sxs-lookup"><span data-stu-id="83f9a-175">`Process C` opens the memory-mapped file and writes a value to it.</span></span>  
  
4. <span data-ttu-id="83f9a-176">`Process A`přečte a zobrazí hodnoty z souboru mapované paměti.</span><span class="sxs-lookup"><span data-stu-id="83f9a-176">`Process A` reads and displays the values from the memory-mapped file.</span></span>  
  
5. <span data-ttu-id="83f9a-177">Po `Process A` dokončení souboru mapované paměti je soubor okamžitě uvolněn kolekcí paměti.</span><span class="sxs-lookup"><span data-stu-id="83f9a-177">After `Process A` is finished with the memory-mapped file, the file is immediately reclaimed by garbage collection.</span></span>  
  
 <span data-ttu-id="83f9a-178">Chcete-li spustit tento příklad, postupujte následovně:</span><span class="sxs-lookup"><span data-stu-id="83f9a-178">To run this example, do the following:</span></span>  
  
1. <span data-ttu-id="83f9a-179">Zkompilujte aplikace a otevřete tři okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="83f9a-179">Compile the applications and open three Command Prompt windows.</span></span>  
  
2. <span data-ttu-id="83f9a-180">V prvním okně příkazového řádku spusťte příkaz `Process A` .</span><span class="sxs-lookup"><span data-stu-id="83f9a-180">In the first Command Prompt window, run `Process A`.</span></span>  
  
3. <span data-ttu-id="83f9a-181">V druhém okně příkazového řádku spusťte příkaz `Process B` .</span><span class="sxs-lookup"><span data-stu-id="83f9a-181">In the second Command Prompt window, run `Process B`.</span></span>  
  
4. <span data-ttu-id="83f9a-182">Vraťte se na `Process A` a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="83f9a-182">Return to `Process A` and press ENTER.</span></span>  
  
5. <span data-ttu-id="83f9a-183">V třetím okně příkazového řádku spusťte příkaz `Process C` .</span><span class="sxs-lookup"><span data-stu-id="83f9a-183">In the third Command Prompt window, run `Process C`.</span></span>  
  
6. <span data-ttu-id="83f9a-184">Vraťte se na `Process A` a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="83f9a-184">Return to `Process A` and press ENTER.</span></span>  
  
 <span data-ttu-id="83f9a-185">Výstup `Process A` je následující:</span><span class="sxs-lookup"><span data-stu-id="83f9a-185">The output of `Process A` is as follows:</span></span>  
  
```console  
Start Process B and press ENTER to continue.  
Start Process C and press ENTER to continue.  
Process A says: True  
Process B says: False  
Process C says: True  
```  
  
 <span data-ttu-id="83f9a-186">**Zpracování**</span><span class="sxs-lookup"><span data-stu-id="83f9a-186">**Process A**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/vb/program.vb#1)]  
  
 <span data-ttu-id="83f9a-187">**Zpracování B**</span><span class="sxs-lookup"><span data-stu-id="83f9a-187">**Process B**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/vb/program.vb#1)]  
  
 <span data-ttu-id="83f9a-188">**Zpracování C**</span><span class="sxs-lookup"><span data-stu-id="83f9a-188">**Process C**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="83f9a-189">Viz také</span><span class="sxs-lookup"><span data-stu-id="83f9a-189">See also</span></span>

- [<span data-ttu-id="83f9a-190">Vstupně-výstupní operace se soubory a datovým proudem</span><span class="sxs-lookup"><span data-stu-id="83f9a-190">File and Stream I/O</span></span>](index.md)
