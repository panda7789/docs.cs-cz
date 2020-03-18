---
title: Soubory mapované paměti
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- memory-mapped files
- inter-process communication
ms.assetid: a483d1b5-64aa-45b6-86ef-11b859f7f02e
ms.openlocfilehash: 004da94bc7345bdc294562f0e1bedf6f1735adec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159712"
---
# <a name="memory-mapped-files"></a><span data-ttu-id="f2297-102">Soubory mapované paměti</span><span class="sxs-lookup"><span data-stu-id="f2297-102">Memory-Mapped Files</span></span>
<span data-ttu-id="f2297-103">Soubor mapovaný v paměti obsahuje obsah souboru ve virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="f2297-103">A memory-mapped file contains the contents of a file in virtual memory.</span></span> <span data-ttu-id="f2297-104">Toto mapování mezi souborem a paměťovým prostorem umožňuje aplikaci, včetně více procesů, upravit soubor čtením a zápisem přímo do paměti.</span><span class="sxs-lookup"><span data-stu-id="f2297-104">This mapping between a file and memory space enables an application, including multiple processes, to modify the file by reading and writing directly to the memory.</span></span> <span data-ttu-id="f2297-105">Počínaje rozhraním .NET Framework 4 můžete použít spravovaný kód pro přístup k souborům mapovaným v paměti stejným způsobem, jakým nativní funkce systému Windows přistupují k souborům mapovaným v paměti, jak je popsáno v [části Správa souborů mapovaných v paměti](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="f2297-105">Starting with the .NET Framework 4, you can use managed code to access memory-mapped files in the same way that native Windows functions access memory-mapped files, as described in [Managing Memory-Mapped Files](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10)).</span></span>  
  
 <span data-ttu-id="f2297-106">Existují dva typy souborů mapovaných v paměti:</span><span class="sxs-lookup"><span data-stu-id="f2297-106">There are two types of memory-mapped files:</span></span>  
  
- <span data-ttu-id="f2297-107">Soubory mapované v trvalé paměti</span><span class="sxs-lookup"><span data-stu-id="f2297-107">Persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="f2297-108">Trvalé soubory jsou soubory mapované v paměti, které jsou přidruženy ke zdrojovému souboru na disku.</span><span class="sxs-lookup"><span data-stu-id="f2297-108">Persisted files are memory-mapped files that are associated with a source file on a disk.</span></span> <span data-ttu-id="f2297-109">Po dokončení práce se souborem se souborem se data uloží do zdrojového souboru na disku.</span><span class="sxs-lookup"><span data-stu-id="f2297-109">When the last process has finished working with the file, the data is saved to the source file on the disk.</span></span> <span data-ttu-id="f2297-110">Tyto soubory mapované v paměti jsou vhodné pro práci s extrémně velkými zdrojovými soubory.</span><span class="sxs-lookup"><span data-stu-id="f2297-110">These memory-mapped files are suitable for working with extremely large source files.</span></span>  
  
- <span data-ttu-id="f2297-111">Netrvalé soubory mapované v paměti</span><span class="sxs-lookup"><span data-stu-id="f2297-111">Non-persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="f2297-112">Netrvalé soubory jsou soubory mapované v paměti, které nejsou přidruženy k souboru na disku.</span><span class="sxs-lookup"><span data-stu-id="f2297-112">Non-persisted files are memory-mapped files that are not associated with a file on a disk.</span></span> <span data-ttu-id="f2297-113">Po dokončení práce se souborem poslední proces dojde ke ztrátě dat a soubor je uvolněn systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="f2297-113">When the last process has finished working with the file, the data is lost and the file is reclaimed by garbage collection.</span></span> <span data-ttu-id="f2297-114">Tyto soubory jsou vhodné pro vytváření sdílené paměti pro meziprocesovou komunikaci (IPC).</span><span class="sxs-lookup"><span data-stu-id="f2297-114">These files are suitable for creating shared memory for inter-process communications (IPC).</span></span>  
  
## <a name="processes-views-and-managing-memory"></a><span data-ttu-id="f2297-115">Procesy, zobrazení a správa paměti</span><span class="sxs-lookup"><span data-stu-id="f2297-115">Processes, Views, and Managing Memory</span></span>  
 <span data-ttu-id="f2297-116">Soubory mapované v paměti lze sdílet ve více procesech.</span><span class="sxs-lookup"><span data-stu-id="f2297-116">Memory-mapped files can be shared across multiple processes.</span></span> <span data-ttu-id="f2297-117">Procesy lze mapovat na stejný soubor mapovaný v paměti pomocí běžného názvu, který je přiřazen procesem, který soubor vytvořil.</span><span class="sxs-lookup"><span data-stu-id="f2297-117">Processes can map to the same memory-mapped file by using a common name that is assigned by the process that created the file.</span></span>  
  
 <span data-ttu-id="f2297-118">Chcete-li pracovat se souborem mapovaným v paměti, musíte vytvořit zobrazení celého souboru mapovaného v paměti nebo jeho části.</span><span class="sxs-lookup"><span data-stu-id="f2297-118">To work with a memory-mapped file, you must create a view of the entire memory-mapped file or a part of it.</span></span> <span data-ttu-id="f2297-119">Můžete také vytvořit více zobrazení do stejné části souboru mapované paměti, čímž se vytvoří souběžná paměť.</span><span class="sxs-lookup"><span data-stu-id="f2297-119">You can also create multiple views to the same part of the memory-mapped file, thereby creating concurrent memory.</span></span> <span data-ttu-id="f2297-120">Aby dvě zobrazení zůstala souběžná, musí být vytvořena ze stejného souboru mapovaného v paměti.</span><span class="sxs-lookup"><span data-stu-id="f2297-120">For two views to remain concurrent, they have to be created from the same memory-mapped file.</span></span>  
  
 <span data-ttu-id="f2297-121">Více zobrazení může být také nezbytné, pokud je soubor větší než velikost logického paměťového prostoru aplikace, který je k dispozici pro mapování paměti (2 GB v 32bitovém počítači).</span><span class="sxs-lookup"><span data-stu-id="f2297-121">Multiple views may also be necessary if the file is greater than the size of the application’s logical memory space available for memory mapping (2 GB on a 32-bit computer).</span></span>  
  
 <span data-ttu-id="f2297-122">Existují dva typy zobrazení: zobrazení přístupu k datovému proudu a zobrazení s náhodným přístupem.</span><span class="sxs-lookup"><span data-stu-id="f2297-122">There are two types of views: stream access view and random access view.</span></span> <span data-ttu-id="f2297-123">Použití zobrazení přístupu datových proudů pro sekvenční přístup k souboru; To je doporučeno pro netrvalé soubory a IPC.</span><span class="sxs-lookup"><span data-stu-id="f2297-123">Use stream access views for sequential access to a file; this is recommended for non-persisted files and IPC.</span></span> <span data-ttu-id="f2297-124">Zobrazení náhodného přístupu jsou upřednostňována pro práci s trvalými soubory.</span><span class="sxs-lookup"><span data-stu-id="f2297-124">Random access views are preferred for working with persisted files.</span></span>  
  
 <span data-ttu-id="f2297-125">Soubory mapované v paměti jsou přístupné prostřednictvím správce paměti operačního systému, takže soubor je automaticky rozdělen na několik stránek a přistupovat podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="f2297-125">Memory-mapped files are accessed through the operating system’s memory manager, so the file is automatically partitioned into a number of pages and accessed as needed.</span></span> <span data-ttu-id="f2297-126">Není třeba zpracovávat správu paměti sami.</span><span class="sxs-lookup"><span data-stu-id="f2297-126">You do not have to handle the memory management yourself.</span></span>  
  
 <span data-ttu-id="f2297-127">Následující obrázek znázorňuje, jak může mít více procesů více a překrývající se zobrazení do stejného souboru mapovaného v paměti současně.</span><span class="sxs-lookup"><span data-stu-id="f2297-127">The following illustration shows how multiple processes can have multiple and overlapping views to the same memory-mapped file at the same time.</span></span>

 <span data-ttu-id="f2297-128">Následující obrázek znázorňuje více a překrývaných zobrazení do souboru mapovaného v paměti:</span><span class="sxs-lookup"><span data-stu-id="f2297-128">The following image shows multiple and overlapped views to a memory-mapped file:</span></span>  
  
 ![Snímek obrazovky, který zobrazuje zobrazení do paměti&#45;mapovaný soubor.](./media/memory-mapped-files/memory-map-persist-file.png)  
  
## <a name="programming-with-memory-mapped-files"></a><span data-ttu-id="f2297-130">Programování se soubory mapovanými v paměti</span><span class="sxs-lookup"><span data-stu-id="f2297-130">Programming with Memory-Mapped Files</span></span>  
 <span data-ttu-id="f2297-131">Následující tabulka obsahuje průvodce pro použití objektů souborů mapovaných v paměti a jejich členů.</span><span class="sxs-lookup"><span data-stu-id="f2297-131">The following table provides a guide for using memory-mapped file objects and their members.</span></span>  
  
|<span data-ttu-id="f2297-132">Úkol</span><span class="sxs-lookup"><span data-stu-id="f2297-132">Task</span></span>|<span data-ttu-id="f2297-133">Metody nebo vlastnosti, které mají být</span><span class="sxs-lookup"><span data-stu-id="f2297-133">Methods or properties to use</span></span>|  
|----------|----------------------------------|  
|<span data-ttu-id="f2297-134">Chcete-li <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> získat objekt, který představuje trvalý soubor mapovaný v paměti ze souboru na disku.</span><span class="sxs-lookup"><span data-stu-id="f2297-134">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a persisted memory-mapped file from a file on disk.</span></span>|<span data-ttu-id="f2297-135"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>Metoda.</span><span class="sxs-lookup"><span data-stu-id="f2297-135"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="f2297-136">Chcete-li <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> získat objekt, který představuje netrvalý soubor mapovaný v paměti (není přidružen k souboru na disku).</span><span class="sxs-lookup"><span data-stu-id="f2297-136">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a non-persisted memory-mapped file (not associated with a file on disk).</span></span>|<span data-ttu-id="f2297-137"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>Metoda.</span><span class="sxs-lookup"><span data-stu-id="f2297-137"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> method.</span></span><br /><br /> <span data-ttu-id="f2297-138">- nebo -</span><span class="sxs-lookup"><span data-stu-id="f2297-138">- or -</span></span><br /><br /> <span data-ttu-id="f2297-139"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>Metoda.</span><span class="sxs-lookup"><span data-stu-id="f2297-139"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="f2297-140">Chcete-li <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> získat objekt existujícího souboru mapované ho u paměti (trvalé nebo netrvalé).</span><span class="sxs-lookup"><span data-stu-id="f2297-140">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object of an existing memory-mapped file (either persisted or non-persisted).</span></span>|<span data-ttu-id="f2297-141"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType>Metoda.</span><span class="sxs-lookup"><span data-stu-id="f2297-141"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="f2297-142">Chcete-li <xref:System.IO.UnmanagedMemoryStream> získat objekt pro postupně přístupné zobrazení souboru mapované paměti.</span><span class="sxs-lookup"><span data-stu-id="f2297-142">To obtain a <xref:System.IO.UnmanagedMemoryStream> object for a sequentially accessed view to the memory-mapped file.</span></span>|<span data-ttu-id="f2297-143"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType>Metoda.</span><span class="sxs-lookup"><span data-stu-id="f2297-143"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="f2297-144">Chcete-li <xref:System.IO.UnmanagedMemoryAccessor> získat objekt pro zobrazení náhodného přístupu k paměti mapované fie.</span><span class="sxs-lookup"><span data-stu-id="f2297-144">To obtain a <xref:System.IO.UnmanagedMemoryAccessor> object for a random access view to a memory-mapped fie.</span></span>|<span data-ttu-id="f2297-145"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType>Metoda.</span><span class="sxs-lookup"><span data-stu-id="f2297-145"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="f2297-146">Chcete-li <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> získat objekt pro použití s nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="f2297-146">To obtain a <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> object to use with unmanaged code.</span></span>|<span data-ttu-id="f2297-147"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType>Vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f2297-147"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="f2297-148">- nebo -</span><span class="sxs-lookup"><span data-stu-id="f2297-148">- or -</span></span><br /><br /> <span data-ttu-id="f2297-149"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>Vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f2297-149"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="f2297-150">- nebo -</span><span class="sxs-lookup"><span data-stu-id="f2297-150">- or -</span></span><br /><br /> <span data-ttu-id="f2297-151"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>Vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f2297-151"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span>|  
|<span data-ttu-id="f2297-152">Zpoždění přidělování paměti, dokud není vytvořeno zobrazení (pouze netrvalé soubory).</span><span class="sxs-lookup"><span data-stu-id="f2297-152">To delay allocating memory until a view is created (non-persisted files only).</span></span><br /><br /> <span data-ttu-id="f2297-153">(Chcete-li určit aktuální velikost <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> systémové stránky, použijte vlastnost.)</span><span class="sxs-lookup"><span data-stu-id="f2297-153">(To determine the current system page size, use the <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> property.)</span></span>|<span data-ttu-id="f2297-154"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A>s hodnotou. <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f2297-154"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> method with the <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> value.</span></span><br /><br /> <span data-ttu-id="f2297-155">- nebo -</span><span class="sxs-lookup"><span data-stu-id="f2297-155">- or -</span></span><br /><br /> <span data-ttu-id="f2297-156"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A>metody, které <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> mají výčet jako parametr.</span><span class="sxs-lookup"><span data-stu-id="f2297-156"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods that have a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> enumeration as a parameter.</span></span>|  
  
### <a name="security"></a><span data-ttu-id="f2297-157">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="f2297-157">Security</span></span>  
 <span data-ttu-id="f2297-158">Přístupová práva můžete použít při vytváření souboru mapovaného v paměti <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> pomocí následujících metod, které berou výčet jako parametr:</span><span class="sxs-lookup"><span data-stu-id="f2297-158">You can apply access rights when you create a memory-mapped file, by using the following methods that take a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> enumeration as a parameter:</span></span>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="f2297-159">Můžete zadat přístupová práva pro otevření existujícího souboru mapovaného v paměti pomocí <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> metod, které berou <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> jako parametr.</span><span class="sxs-lookup"><span data-stu-id="f2297-159">You can specify access rights for opening an existing memory-mapped file by using the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> methods that take an <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> as a parameter.</span></span>  
  
 <span data-ttu-id="f2297-160">Kromě toho můžete zahrnout <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> objekt, který obsahuje předdefinovaná pravidla přístupu.</span><span class="sxs-lookup"><span data-stu-id="f2297-160">In addition, you can include a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> object that contains predefined access rules.</span></span>  
  
 <span data-ttu-id="f2297-161">Chcete-li použít nová nebo změněná pravidla přístupu <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> k souboru mapovanému v paměti, použijte metodu.</span><span class="sxs-lookup"><span data-stu-id="f2297-161">To apply new or changed access rules to a memory-mapped file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> method.</span></span> <span data-ttu-id="f2297-162">Chcete-li načíst pravidla přístupu nebo <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> auditu z existujícího souboru, použijte metodu.</span><span class="sxs-lookup"><span data-stu-id="f2297-162">To retrieve access or audit rules from an existing file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="f2297-163">Příklady</span><span class="sxs-lookup"><span data-stu-id="f2297-163">Examples</span></span>  
  
### <a name="persisted-memory-mapped-files"></a><span data-ttu-id="f2297-164">Trvalé soubory mapované v paměti</span><span class="sxs-lookup"><span data-stu-id="f2297-164">Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="f2297-165">Metody <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> vytvoří soubor mapovaný v paměti z existujícího souboru na disku.</span><span class="sxs-lookup"><span data-stu-id="f2297-165">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> methods create a memory-mapped file from an existing file on disk.</span></span>  
  
 <span data-ttu-id="f2297-166">Následující příklad vytvoří zobrazení mapované paměti části extrémně velkého souboru a manipuluje s jeho částí.</span><span class="sxs-lookup"><span data-stu-id="f2297-166">The following example creates a memory-mapped view of a part of an extremely large file and manipulates a portion of it.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

 <span data-ttu-id="f2297-167">Následující příklad otevře stejný soubor mapovaný v paměti pro jiný proces.</span><span class="sxs-lookup"><span data-stu-id="f2297-167">The following example opens the same memory-mapped file for another process.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a><span data-ttu-id="f2297-168">Netrvalé soubory mapované v paměti</span><span class="sxs-lookup"><span data-stu-id="f2297-168">Non-Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="f2297-169">Metody <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> a vytvoří soubor mapovaný v paměti, který není mapován na existující soubor na disku.</span><span class="sxs-lookup"><span data-stu-id="f2297-169">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> and <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods create a memory-mapped file that is not mapped to an existing file on disk.</span></span>  
  
 <span data-ttu-id="f2297-170">Následující příklad se skládá ze tří samostatných procesů (konzolové aplikace), které zapisují logické hodnoty do souboru mapovaného v paměti.</span><span class="sxs-lookup"><span data-stu-id="f2297-170">The following example consists of three separate processes (console applications) that write Boolean values to a memory-mapped file.</span></span> <span data-ttu-id="f2297-171">Dochází k následující posloupnosti akcí:</span><span class="sxs-lookup"><span data-stu-id="f2297-171">The following sequence of actions occur:</span></span>  
  
1. <span data-ttu-id="f2297-172">`Process A`vytvoří soubor mapovaný v paměti a zapíše do něj hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f2297-172">`Process A` creates the memory-mapped file and writes a value to it.</span></span>  
  
2. <span data-ttu-id="f2297-173">`Process B`otevře soubor mapovaný v paměti a zapíše do něj hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f2297-173">`Process B` opens the memory-mapped file and writes a value to it.</span></span>  
  
3. <span data-ttu-id="f2297-174">`Process C`otevře soubor mapovaný v paměti a zapíše do něj hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f2297-174">`Process C` opens the memory-mapped file and writes a value to it.</span></span>  
  
4. <span data-ttu-id="f2297-175">`Process A`přečte a zobrazí hodnoty ze souboru mapovaného v paměti.</span><span class="sxs-lookup"><span data-stu-id="f2297-175">`Process A` reads and displays the values from the memory-mapped file.</span></span>  
  
5. <span data-ttu-id="f2297-176">Po `Process A` dokončení s mapovaným souborem paměti je soubor okamžitě uvolněn systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="f2297-176">After `Process A` is finished with the memory-mapped file, the file is immediately reclaimed by garbage collection.</span></span>  
  
 <span data-ttu-id="f2297-177">Chcete-li spustit tento příklad, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="f2297-177">To run this example, do the following:</span></span>  
  
1. <span data-ttu-id="f2297-178">Zkompilujte aplikace a otevřete tři okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="f2297-178">Compile the applications and open three Command Prompt windows.</span></span>  
  
2. <span data-ttu-id="f2297-179">V prvním okně příkazového `Process A`řádku spusťte .</span><span class="sxs-lookup"><span data-stu-id="f2297-179">In the first Command Prompt window, run `Process A`.</span></span>  
  
3. <span data-ttu-id="f2297-180">V druhém okně příkazového `Process B`řádku spusťte .</span><span class="sxs-lookup"><span data-stu-id="f2297-180">In the second Command Prompt window, run `Process B`.</span></span>  
  
4. <span data-ttu-id="f2297-181">Vraťte `Process A` se a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="f2297-181">Return to `Process A` and press ENTER.</span></span>  
  
5. <span data-ttu-id="f2297-182">Ve třetím okně příkazového `Process C`řádku spusťte .</span><span class="sxs-lookup"><span data-stu-id="f2297-182">In the third Command Prompt window, run `Process C`.</span></span>  
  
6. <span data-ttu-id="f2297-183">Vraťte `Process A` se a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="f2297-183">Return to `Process A` and press ENTER.</span></span>  
  
 <span data-ttu-id="f2297-184">Výstup `Process A` je následující:</span><span class="sxs-lookup"><span data-stu-id="f2297-184">The output of `Process A` is as follows:</span></span>  
  
```console  
Start Process B and press ENTER to continue.  
Start Process C and press ENTER to continue.  
Process A says: True  
Process B says: False  
Process C says: True  
```  
  
 <span data-ttu-id="f2297-185">**Proces A**</span><span class="sxs-lookup"><span data-stu-id="f2297-185">**Process A**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/vb/program.vb#1)]  
  
 <span data-ttu-id="f2297-186">**Proces B**</span><span class="sxs-lookup"><span data-stu-id="f2297-186">**Process B**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/vb/program.vb#1)]  
  
 <span data-ttu-id="f2297-187">**Proces C**</span><span class="sxs-lookup"><span data-stu-id="f2297-187">**Process C**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f2297-188">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2297-188">See also</span></span>

- [<span data-ttu-id="f2297-189">I/O souborů a proudů</span><span class="sxs-lookup"><span data-stu-id="f2297-189">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
