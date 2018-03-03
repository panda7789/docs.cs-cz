---
title: "Soubory mapované paměti"
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
- memory-mapped files
- inter-process communiation
ms.assetid: a483d1b5-64aa-45b6-86ef-11b859f7f02e
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 99aefdaf3d38dc5506bf785c8ba4a9b457cc7bf7
ms.sourcegitcommit: ba765893e3efcece67d99fd6d5ce0074b050d1d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/02/2018
---
# <a name="memory-mapped-files"></a><span data-ttu-id="3f48a-102">Soubory mapované paměti</span><span class="sxs-lookup"><span data-stu-id="3f48a-102">Memory-Mapped Files</span></span>
<span data-ttu-id="3f48a-103">Soubor mapované paměti obsahuje obsah souboru ve virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="3f48a-103">A memory-mapped file contains the contents of a file in virtual memory.</span></span> <span data-ttu-id="3f48a-104">Toto mapování mezi místo souboru a paměti umožňuje aplikaci, včetně více procesů, upravte soubor pro čtení a zápis přímo na paměť.</span><span class="sxs-lookup"><span data-stu-id="3f48a-104">This mapping between a file and memory space enables an application, including multiple processes, to modify the file by reading and writing directly to the memory.</span></span> <span data-ttu-id="3f48a-105">Od verze [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], spravovaného kódu můžete použít pro přístup k souborům mapované paměti stejným způsobem, že nativní funkce systému Windows přístup k souborům mapované paměti, jak je popsáno v [soubory mapované paměti](https://msdn.microsoft.com/library/ms810613.aspx).</span><span class="sxs-lookup"><span data-stu-id="3f48a-105">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use managed code to access memory-mapped files in the same way that native Windows functions access memory-mapped files, as described in [Managing Memory-Mapped Files](https://msdn.microsoft.com/library/ms810613.aspx).</span></span>  
  
 <span data-ttu-id="3f48a-106">Existují dva typy soubory mapované paměti:</span><span class="sxs-lookup"><span data-stu-id="3f48a-106">There are two types of memory-mapped files:</span></span>  
  
-   <span data-ttu-id="3f48a-107">Trvalé soubory mapované paměti</span><span class="sxs-lookup"><span data-stu-id="3f48a-107">Persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="3f48a-108">Trvalé soubory jsou soubory mapované paměti, které jsou přidruženy ke zdrojovému souboru na disku.</span><span class="sxs-lookup"><span data-stu-id="3f48a-108">Persisted files are memory-mapped files that are associated with a source file on a disk.</span></span> <span data-ttu-id="3f48a-109">Při poslední proces dokončí práci se souborem, data uložena ke zdrojovému souboru na disku.</span><span class="sxs-lookup"><span data-stu-id="3f48a-109">When the last process has finished working with the file, the data is saved to the source file on the disk.</span></span> <span data-ttu-id="3f48a-110">Tyto soubory mapované paměti jsou vhodné pro práci s velmi velký zdrojové soubory.</span><span class="sxs-lookup"><span data-stu-id="3f48a-110">These memory-mapped files are suitable for working with extremely large source files.</span></span>  
  
-   <span data-ttu-id="3f48a-111">Netrvalé soubory mapované paměti</span><span class="sxs-lookup"><span data-stu-id="3f48a-111">Non-persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="3f48a-112">Netrvalé soubory jsou mapované paměti soubory, které nejsou přidružené souboru na disku.</span><span class="sxs-lookup"><span data-stu-id="3f48a-112">Non-persisted files are memory-mapped files that are not associated with a file on a disk.</span></span> <span data-ttu-id="3f48a-113">Po dokončení práce se souborem posledního procesu, dojde ke ztrátě dat a soubor je uvolněn systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="3f48a-113">When the last process has finished working with the file, the data is lost and the file is reclaimed by garbage collection.</span></span> <span data-ttu-id="3f48a-114">Tyto soubory jsou vhodné pro vytvoření sdílené paměti pro meziprocesová komunikace (IPC).</span><span class="sxs-lookup"><span data-stu-id="3f48a-114">These files are suitable for creating shared memory for inter-process communications (IPC).</span></span>  
  
## <a name="processes-views-and-managing-memory"></a><span data-ttu-id="3f48a-115">Procesy, zobrazení a správa paměti</span><span class="sxs-lookup"><span data-stu-id="3f48a-115">Processes, Views, and Managing Memory</span></span>  
 <span data-ttu-id="3f48a-116">Soubory mapované paměti můžete sdílet mezi více procesů.</span><span class="sxs-lookup"><span data-stu-id="3f48a-116">Memory-mapped files can be shared across multiple processes.</span></span> <span data-ttu-id="3f48a-117">Procesy můžete namapovat do stejného souboru mapované paměti pomocí běžný název, který je přiřazen nástrojem proces, který vytvořil soubor.</span><span class="sxs-lookup"><span data-stu-id="3f48a-117">Processes can map to the same memory-mapped file by using a common name that is assigned by the process that created the file.</span></span>  
  
 <span data-ttu-id="3f48a-118">Pro práci s soubor mapované paměti, musí vytvořit zobrazení celý soubor mapované paměti nebo jeho část.</span><span class="sxs-lookup"><span data-stu-id="3f48a-118">To work with a memory-mapped file, you must create a view of the entire memory-mapped file or a part of it.</span></span> <span data-ttu-id="3f48a-119">Můžete také vytvořit více zobrazení do stejné části souboru mapované paměti, a vytvoří tak souběžných paměti.</span><span class="sxs-lookup"><span data-stu-id="3f48a-119">You can also create multiple views to the same part of the memory-mapped file, thereby creating concurrent memory.</span></span> <span data-ttu-id="3f48a-120">Pro dvě zobrazení zůstaly souběžné mají být vytvořeny ze stejného souboru mapované paměti.</span><span class="sxs-lookup"><span data-stu-id="3f48a-120">For two views to remain concurrent, they have to be created from the same memory-mapped file.</span></span>  
  
 <span data-ttu-id="3f48a-121">Více zobrazení může být také nutné v případě, že soubor je větší než velikost místa na logických paměti aplikace, které jsou k dispozici pro mapování (na 32bitový počítač 2 GB) paměti.</span><span class="sxs-lookup"><span data-stu-id="3f48a-121">Multiple views may also be necessary if the file is greater than the size of the application’s logical memory space available for memory mapping (2 GB on a 32-bit computer).</span></span>  
  
 <span data-ttu-id="3f48a-122">Existují dva typy zobrazení: stream, přístup k zobrazení a zobrazení náhodný přístup.</span><span class="sxs-lookup"><span data-stu-id="3f48a-122">There are two types of views: stream access view and random access view.</span></span> <span data-ttu-id="3f48a-123">Pomocí zobrazení datových proudů pro sekvenční přístup k souboru. Toto nastavení se doporučuje pro dočasné soubory a IPC.</span><span class="sxs-lookup"><span data-stu-id="3f48a-123">Use stream access views for sequential access to a file; this is recommended for non-persisted files and IPC.</span></span> <span data-ttu-id="3f48a-124">Náhodný přístup zobrazení jsou upřednostněny pro práci s trvalými soubory.</span><span class="sxs-lookup"><span data-stu-id="3f48a-124">Random access views are preferred for working with persisted files.</span></span>  
  
 <span data-ttu-id="3f48a-125">Soubory mapované paměti jsou přístupné prostřednictvím Správce paměti operačního systému, tak, aby automaticky rozdělen do několika stránek a podle potřeby přístup k souboru.</span><span class="sxs-lookup"><span data-stu-id="3f48a-125">Memory-mapped files are accessed through the operating system’s memory manager, so the file is automatically partitioned into a number of pages and accessed as needed.</span></span> <span data-ttu-id="3f48a-126">Nemáte zpracovávat správu paměti.</span><span class="sxs-lookup"><span data-stu-id="3f48a-126">You do not have to handle the memory management yourself.</span></span>  
  
 <span data-ttu-id="3f48a-127">Následující obrázek ukazuje, jak více procesů může mít několik a překrývající se zobrazení do stejného souboru mapované paměti ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="3f48a-127">The following illustration shows how multiple processes can have multiple and overlapping views to the same memory-mapped file at the same time.</span></span>  
  
 <span data-ttu-id="3f48a-128">![Zobrazení ukazuje na paměťově & č. 45; mapovaný soubor. ] (../../../docs/standard/io/media/memmappersisted.png "MemMapPersisted")</span><span class="sxs-lookup"><span data-stu-id="3f48a-128">![Shows views to a memory&#45;mapped file.](../../../docs/standard/io/media/memmappersisted.png "MemMapPersisted")</span></span>  
<span data-ttu-id="3f48a-129">Více a překrývající se zobrazení souboru mapované paměti</span><span class="sxs-lookup"><span data-stu-id="3f48a-129">Multiple and overlapped views to a memory-mapped file</span></span>  
  
## <a name="programming-with-memory-mapped-files"></a><span data-ttu-id="3f48a-130">Programování s soubory mapované paměti</span><span class="sxs-lookup"><span data-stu-id="3f48a-130">Programming with Memory-Mapped Files</span></span>  
 <span data-ttu-id="3f48a-131">Následující tabulka poskytuje návod pro použití souboru mapované paměti objekty a jejich členové.</span><span class="sxs-lookup"><span data-stu-id="3f48a-131">The following table provides a guide for using memory-mapped file objects and their members.</span></span>  
  
|<span data-ttu-id="3f48a-132">Úloha</span><span class="sxs-lookup"><span data-stu-id="3f48a-132">Task</span></span>|<span data-ttu-id="3f48a-133">Metody nebo vlastnosti, které chcete použít</span><span class="sxs-lookup"><span data-stu-id="3f48a-133">Methods or properties to use</span></span>|  
|----------|----------------------------------|  
|<span data-ttu-id="3f48a-134">K získání <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> objekt, který reprezentuje trvalý soubor mapované paměti ze souboru na disku.</span><span class="sxs-lookup"><span data-stu-id="3f48a-134">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a persisted memory-mapped file from a file on disk.</span></span>|<span data-ttu-id="3f48a-135"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> Metoda.</span><span class="sxs-lookup"><span data-stu-id="3f48a-135"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="3f48a-136">K získání <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> objekt, který reprezentuje netrvalý soubor mapované paměti (není přidružen k souboru na disku).</span><span class="sxs-lookup"><span data-stu-id="3f48a-136">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a non-persisted memory-mapped file (not associated with a file on disk).</span></span>|<span data-ttu-id="3f48a-137"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> Metoda.</span><span class="sxs-lookup"><span data-stu-id="3f48a-137"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> method.</span></span><br /><br /> <span data-ttu-id="3f48a-138">- nebo -</span><span class="sxs-lookup"><span data-stu-id="3f48a-138">- or -</span></span><br /><br /> <span data-ttu-id="3f48a-139"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> Metoda.</span><span class="sxs-lookup"><span data-stu-id="3f48a-139"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="3f48a-140">K získání <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> objekt existující soubor mapované paměti (trvalé nebo dočasné).</span><span class="sxs-lookup"><span data-stu-id="3f48a-140">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object of an existing memory-mapped file (either persisted or non-persisted).</span></span>|<span data-ttu-id="3f48a-141"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> Metoda.</span><span class="sxs-lookup"><span data-stu-id="3f48a-141"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="3f48a-142">K získání <xref:System.IO.UnmanagedMemoryStream> objekt pro sekvenční přístup k souboru mapované paměti zobrazení.</span><span class="sxs-lookup"><span data-stu-id="3f48a-142">To obtain a <xref:System.IO.UnmanagedMemoryStream> object for a sequentially accessed view to the memory-mapped file.</span></span>|<span data-ttu-id="3f48a-143"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> Metoda.</span><span class="sxs-lookup"><span data-stu-id="3f48a-143"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="3f48a-144">K získání <xref:System.IO.UnmanagedMemoryAccessor> objekt pro zobrazení náhodný přístup do mapované paměti souboru.</span><span class="sxs-lookup"><span data-stu-id="3f48a-144">To obtain a <xref:System.IO.UnmanagedMemoryAccessor> object for a random access view to a memory-mapped fie.</span></span>|<span data-ttu-id="3f48a-145"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> Metoda.</span><span class="sxs-lookup"><span data-stu-id="3f48a-145"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="3f48a-146">K získání <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> objekt, který chcete použít s nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="3f48a-146">To obtain a <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> object to use with unmanaged code.</span></span>|<span data-ttu-id="3f48a-147"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> Vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3f48a-147"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="3f48a-148">- nebo -</span><span class="sxs-lookup"><span data-stu-id="3f48a-148">- or -</span></span><br /><br /> <span data-ttu-id="3f48a-149"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> Vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3f48a-149"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="3f48a-150">- nebo -</span><span class="sxs-lookup"><span data-stu-id="3f48a-150">- or -</span></span><br /><br /> <span data-ttu-id="3f48a-151"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> Vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3f48a-151"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span>|  
|<span data-ttu-id="3f48a-152">Zpoždění přidělování paměti až do zobrazení se vytvoří (netrvalé pouze soubory).</span><span class="sxs-lookup"><span data-stu-id="3f48a-152">To delay allocating memory until a view is created (non-persisted files only).</span></span><br /><br /> <span data-ttu-id="3f48a-153">(Chcete-li zjistit aktuální velikost stránky systému, použijte <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> vlastnost.)</span><span class="sxs-lookup"><span data-stu-id="3f48a-153">(To determine the current system page size, use the <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> property.)</span></span>|<span data-ttu-id="3f48a-154"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> Metoda s <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3f48a-154"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> method with the <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> value.</span></span><br /><br /> <span data-ttu-id="3f48a-155">- nebo -</span><span class="sxs-lookup"><span data-stu-id="3f48a-155">- or -</span></span><br /><br /> <span data-ttu-id="3f48a-156"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> metody, které mají <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> výčet jako parametr.</span><span class="sxs-lookup"><span data-stu-id="3f48a-156"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods that have a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> enumeration as a parameter.</span></span>|  
  
### <a name="security"></a><span data-ttu-id="3f48a-157">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="3f48a-157">Security</span></span>  
 <span data-ttu-id="3f48a-158">Když vytvoříte soubor mapované paměti pomocí následujících metod, které berou můžete použít přístupová práva <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> výčet jako parametr:</span><span class="sxs-lookup"><span data-stu-id="3f48a-158">You can apply access rights when you create a memory-mapped file, by using the following methods that take a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> enumeration as a parameter:</span></span>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="3f48a-159">Můžete zadat přístupová práva pro otevření existující soubor mapované paměti pomocí <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> metod, které berou <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> jako parametr.</span><span class="sxs-lookup"><span data-stu-id="3f48a-159">You can specify access rights for opening an existing memory-mapped file by using the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> methods that take an <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> as a parameter.</span></span>  
  
 <span data-ttu-id="3f48a-160">Kromě toho můžete zahrnout <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> objekt, který obsahuje předdefinovaná pravidla přístupu.</span><span class="sxs-lookup"><span data-stu-id="3f48a-160">In addition, you can include a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> object that contains predefined access rules.</span></span>  
  
 <span data-ttu-id="3f48a-161">Chcete-li použít nové nebo změněné pravidel přístupu do souboru mapované paměti, použijte <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="3f48a-161">To apply new or changed access rules to a memory-mapped file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> method.</span></span> <span data-ttu-id="3f48a-162">Pokud chcete získat přístup nebo audit pravidla z existující soubor, použijte <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="3f48a-162">To retrieve access or audit rules from an existing file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="3f48a-163">Příklady</span><span class="sxs-lookup"><span data-stu-id="3f48a-163">Examples</span></span>  
  
### <a name="persisted-memory-mapped-files"></a><span data-ttu-id="3f48a-164">Trvalé soubory mapované paměti</span><span class="sxs-lookup"><span data-stu-id="3f48a-164">Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="3f48a-165"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> Metody vytvořte soubor mapované paměti z existující soubor na disku.</span><span class="sxs-lookup"><span data-stu-id="3f48a-165">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> methods create a memory-mapped file from an existing file on disk.</span></span>  
  
 <span data-ttu-id="3f48a-166">Následující příklad vytvoří zobrazení mapované paměti součástí velmi velkých souborů a umožňuje pracovat s její části je.</span><span class="sxs-lookup"><span data-stu-id="3f48a-166">The following example creates a memory-mapped view of a part of an extremely large file and manipulates a portion of it.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  
  
 <span data-ttu-id="3f48a-167">Následující příklad otevře stejný soubor mapované paměti pro jiný proces.</span><span class="sxs-lookup"><span data-stu-id="3f48a-167">The following example opens the same memory-mapped file for another process.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a><span data-ttu-id="3f48a-168">Dočasné soubory mapované paměti</span><span class="sxs-lookup"><span data-stu-id="3f48a-168">Non-Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="3f48a-169"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> metody vytvořte soubor mapované paměti, který není namapovaná na existující soubor na disku.</span><span class="sxs-lookup"><span data-stu-id="3f48a-169">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> and <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods create a memory-mapped file that is not mapped to an existing file on disk.</span></span>  
  
 <span data-ttu-id="3f48a-170">V následujícím příkladu se skládá ze tří oddělených procesů (konzolové aplikace), které zapisují logické hodnoty do souboru mapované paměti.</span><span class="sxs-lookup"><span data-stu-id="3f48a-170">The following example consists of three separate processes (console applications) that write Boolean values to a memory-mapped file.</span></span> <span data-ttu-id="3f48a-171">Provedou se následující posloupnost akcí:</span><span class="sxs-lookup"><span data-stu-id="3f48a-171">The following sequence of actions occur:</span></span>  
  
1.  <span data-ttu-id="3f48a-172">`Process A` Vytvoří soubor mapované paměti a zapíše do jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3f48a-172">`Process A` creates the memory-mapped file and writes a value to it.</span></span>  
  
2.  <span data-ttu-id="3f48a-173">`Process B` Otevře soubor mapované paměti a zapíše do jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3f48a-173">`Process B` opens the memory-mapped file and writes a value to it.</span></span>  
  
3.  <span data-ttu-id="3f48a-174">`Process C` Otevře soubor mapované paměti a zapíše do jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3f48a-174">`Process C` opens the memory-mapped file and writes a value to it.</span></span>  
  
4.  <span data-ttu-id="3f48a-175">`Process A` načítá a zobrazuje hodnoty ze souboru mapované paměti.</span><span class="sxs-lookup"><span data-stu-id="3f48a-175">`Process A` reads and displays the values from the memory-mapped file.</span></span>  
  
5.  <span data-ttu-id="3f48a-176">Po `Process A` po dokončení se souborem mapované paměti, je soubor okamžitě uvolněn systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="3f48a-176">After `Process A` is finished with the memory-mapped file, the file is immediately reclaimed by garbage collection.</span></span>  
  
 <span data-ttu-id="3f48a-177">Pro spuštění tohoto příkladu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="3f48a-177">To run this example, do the following:</span></span>  
  
1.  <span data-ttu-id="3f48a-178">Kompilace aplikace a otevřete tři okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="3f48a-178">Compile the applications and open three Command Prompt windows.</span></span>  
  
2.  <span data-ttu-id="3f48a-179">V prvním okně příkazového řádku spusťte `Process A`.</span><span class="sxs-lookup"><span data-stu-id="3f48a-179">In the first Command Prompt window, run `Process A`.</span></span>  
  
3.  <span data-ttu-id="3f48a-180">V druhé okno příkazového řádku, spusťte `Process B`.</span><span class="sxs-lookup"><span data-stu-id="3f48a-180">In the second Command Prompt window, run `Process B`.</span></span>  
  
4.  <span data-ttu-id="3f48a-181">Vraťte se do `Process A` a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="3f48a-181">Return to `Process A` and press ENTER.</span></span>  
  
5.  <span data-ttu-id="3f48a-182">V okně příkazového řádku třetí spustit `Process C`.</span><span class="sxs-lookup"><span data-stu-id="3f48a-182">In the third Command Prompt window, run `Process C`.</span></span>  
  
6.  <span data-ttu-id="3f48a-183">Vraťte se do `Process A` a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="3f48a-183">Return to `Process A` and press ENTER.</span></span>  
  
 <span data-ttu-id="3f48a-184">Výstup `Process A` vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="3f48a-184">The output of `Process A` is as follows:</span></span>  
  
```  
Start Process B and press ENTER to continue.  
Start Process C and press ENTER to continue.  
Process A says: True  
Process B says: False  
Process C says: True  
```  
  
 <span data-ttu-id="3f48a-185">**Proces A**</span><span class="sxs-lookup"><span data-stu-id="3f48a-185">**Process A**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/vb/program.vb#1)]  
  
 <span data-ttu-id="3f48a-186">**Proces B**</span><span class="sxs-lookup"><span data-stu-id="3f48a-186">**Process B**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/vb/program.vb#1)]  
  
 <span data-ttu-id="3f48a-187">**Proces C**</span><span class="sxs-lookup"><span data-stu-id="3f48a-187">**Process C**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="3f48a-188">Viz také</span><span class="sxs-lookup"><span data-stu-id="3f48a-188">See Also</span></span>  
 [<span data-ttu-id="3f48a-189">Souborová služba a datový proud I-O</span><span class="sxs-lookup"><span data-stu-id="3f48a-189">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
