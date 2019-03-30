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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ebd54afb312de0796b5a96b3d41f1e98dd97bd1b
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654351"
---
# <a name="memory-mapped-files"></a><span data-ttu-id="6cb9a-102">Soubory mapované paměti</span><span class="sxs-lookup"><span data-stu-id="6cb9a-102">Memory-Mapped Files</span></span>
<span data-ttu-id="6cb9a-103">Soubor mapovaných do paměti obsahuje obsah souboru ve virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-103">A memory-mapped file contains the contents of a file in virtual memory.</span></span> <span data-ttu-id="6cb9a-104">Toto mapování mezi prostoru soubor a paměť umožňuje aplikaci, včetně více procesů, upravte soubor tak, že čtení a zápis přímo na paměť.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-104">This mapping between a file and memory space enables an application, including multiple processes, to modify the file by reading and writing directly to the memory.</span></span> <span data-ttu-id="6cb9a-105">Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], spravovaný kód můžete použít pro přístup k souborům mapované paměti stejným způsobem, že nativní funkce Windows přístup k souborům mapované paměti, jak je popsáno v [soubory mapované paměti](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="6cb9a-105">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use managed code to access memory-mapped files in the same way that native Windows functions access memory-mapped files, as described in [Managing Memory-Mapped Files](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10)).</span></span>  
  
 <span data-ttu-id="6cb9a-106">Existují dva typy souborů mapovaných do paměti:</span><span class="sxs-lookup"><span data-stu-id="6cb9a-106">There are two types of memory-mapped files:</span></span>  
  
-   <span data-ttu-id="6cb9a-107">Trvalé soubory mapované paměti</span><span class="sxs-lookup"><span data-stu-id="6cb9a-107">Persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="6cb9a-108">Trvalé soubory jsou soubory mapované paměti, které jsou přidruženy ke zdrojovému souboru na disku.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-108">Persisted files are memory-mapped files that are associated with a source file on a disk.</span></span> <span data-ttu-id="6cb9a-109">Po dokončení práce se souborem posledního procesu, data uložena do zdrojového souboru na disku.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-109">When the last process has finished working with the file, the data is saved to the source file on the disk.</span></span> <span data-ttu-id="6cb9a-110">Tyto soubory mapované paměti jsou vhodné pro práci s velmi velký zdrojové soubory.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-110">These memory-mapped files are suitable for working with extremely large source files.</span></span>  
  
-   <span data-ttu-id="6cb9a-111">Netrvalé soubory mapované paměti</span><span class="sxs-lookup"><span data-stu-id="6cb9a-111">Non-persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="6cb9a-112">Netrvalé soubory jsou soubory mapované paměti, které nejsou přiřazeny k souboru na disku.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-112">Non-persisted files are memory-mapped files that are not associated with a file on a disk.</span></span> <span data-ttu-id="6cb9a-113">Po dokončení práce se souborem posledního procesu, dojde ke ztrátě dat a soubor je uvolněn systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-113">When the last process has finished working with the file, the data is lost and the file is reclaimed by garbage collection.</span></span> <span data-ttu-id="6cb9a-114">Tyto soubory jsou vhodné pro vytvoření sdílené paměti pro meziprocesové komunikace (IPC).</span><span class="sxs-lookup"><span data-stu-id="6cb9a-114">These files are suitable for creating shared memory for inter-process communications (IPC).</span></span>  
  
## <a name="processes-views-and-managing-memory"></a><span data-ttu-id="6cb9a-115">Procesy, zobrazení a správa paměti</span><span class="sxs-lookup"><span data-stu-id="6cb9a-115">Processes, Views, and Managing Memory</span></span>  
 <span data-ttu-id="6cb9a-116">Soubory mapované paměti mohou být sdílena několika procesy.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-116">Memory-mapped files can be shared across multiple processes.</span></span> <span data-ttu-id="6cb9a-117">Procesy můžete namapovat na stejný soubor mapovaných do paměti pomocí běžný název, který je přiřazen podle procesu, který vytvořil soubor.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-117">Processes can map to the same memory-mapped file by using a common name that is assigned by the process that created the file.</span></span>  
  
 <span data-ttu-id="6cb9a-118">Pro práci se souborem mapovaných do paměti, musí vytvořit zobrazení celého souboru mapované paměti nebo jeho část.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-118">To work with a memory-mapped file, you must create a view of the entire memory-mapped file or a part of it.</span></span> <span data-ttu-id="6cb9a-119">Můžete také vytvořit více zobrazení do stejné části souborů mapovaných do paměti a tím vytváření souběžných paměti.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-119">You can also create multiple views to the same part of the memory-mapped file, thereby creating concurrent memory.</span></span> <span data-ttu-id="6cb9a-120">Dvě zobrazení zůstat souběžných mají být vytvořené ze stejného souboru mapovaných do paměti.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-120">For two views to remain concurrent, they have to be created from the same memory-mapped file.</span></span>  
  
 <span data-ttu-id="6cb9a-121">Více zobrazení může být také nutné v případě, že soubor je větší než velikost logického paměťový prostor vaší aplikace k dispozici pro mapování (na 32bitových počítačích 2 GB) paměti.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-121">Multiple views may also be necessary if the file is greater than the size of the application’s logical memory space available for memory mapping (2 GB on a 32-bit computer).</span></span>  
  
 <span data-ttu-id="6cb9a-122">Existují dva typy zobrazení: datový proud stream přístup k zobrazení a zobrazení náhodný přístup.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-122">There are two types of views: stream access view and random access view.</span></span> <span data-ttu-id="6cb9a-123">Použití zobrazení datových proudů pro sekvenční přístup k souboru. To se doporučuje pro dočasné soubory a IPC.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-123">Use stream access views for sequential access to a file; this is recommended for non-persisted files and IPC.</span></span> <span data-ttu-id="6cb9a-124">Náhodný přístup zobrazení jsou upřednostňované pro práci s trvalými soubory.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-124">Random access views are preferred for working with persisted files.</span></span>  
  
 <span data-ttu-id="6cb9a-125">Soubory mapované paměti jsou přístupné prostřednictvím Správce paměti operačního systému, takže soubor automaticky je rozdělen do několika stránek a přístup podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-125">Memory-mapped files are accessed through the operating system’s memory manager, so the file is automatically partitioned into a number of pages and accessed as needed.</span></span> <span data-ttu-id="6cb9a-126">Není potřeba zpracovávat správu paměti.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-126">You do not have to handle the memory management yourself.</span></span>  
  
 <span data-ttu-id="6cb9a-127">Následující obrázek znázorňuje způsob více procesů může mít více a překrývající se zobrazení stejné souborů mapovaných do paměti ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-127">The following illustration shows how multiple processes can have multiple and overlapping views to the same memory-mapped file at the same time.</span></span>

 <span data-ttu-id="6cb9a-128">Následující obrázek ukazuje několik a překrývající se zobrazení souboru mapovaných do paměti:</span><span class="sxs-lookup"><span data-stu-id="6cb9a-128">The following image shows multiple and overlapped views to a memory-mapped file:</span></span>  
  
 ![Snímek obrazovky zobrazující zobrazení paměti&#45;namapované souboru.](./media/memory-mapped-files/memory-map-persist-file.png)  
  
## <a name="programming-with-memory-mapped-files"></a><span data-ttu-id="6cb9a-130">Programování s soubory mapované paměti</span><span class="sxs-lookup"><span data-stu-id="6cb9a-130">Programming with Memory-Mapped Files</span></span>  
 <span data-ttu-id="6cb9a-131">Následující tabulka obsahuje návod pro použití souborů mapovaných do paměti objektů a jejich členy.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-131">The following table provides a guide for using memory-mapped file objects and their members.</span></span>  
  
|<span data-ttu-id="6cb9a-132">Úloha</span><span class="sxs-lookup"><span data-stu-id="6cb9a-132">Task</span></span>|<span data-ttu-id="6cb9a-133">Metody nebo vlastnosti, které chcete použít</span><span class="sxs-lookup"><span data-stu-id="6cb9a-133">Methods or properties to use</span></span>|  
|----------|----------------------------------|  
|<span data-ttu-id="6cb9a-134">Získání <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> objekt, který reprezentuje trvalých souborů mapovaných do paměti ze souboru na disku.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-134">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a persisted memory-mapped file from a file on disk.</span></span>|<span data-ttu-id="6cb9a-135"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> Metoda.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-135"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="6cb9a-136">Získání <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> objekt, který reprezentuje netrvalé souborů mapovaných do paměti (není přidružené k souboru na disku).</span><span class="sxs-lookup"><span data-stu-id="6cb9a-136">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a non-persisted memory-mapped file (not associated with a file on disk).</span></span>|<span data-ttu-id="6cb9a-137"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> Metoda.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-137"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> method.</span></span><br /><br /> <span data-ttu-id="6cb9a-138">- nebo -</span><span class="sxs-lookup"><span data-stu-id="6cb9a-138">- or -</span></span><br /><br /> <span data-ttu-id="6cb9a-139"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> Metoda.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-139"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="6cb9a-140">Získání <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> objekt existující soubor mapovaných do paměti (trvalá nebo netrvalé).</span><span class="sxs-lookup"><span data-stu-id="6cb9a-140">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object of an existing memory-mapped file (either persisted or non-persisted).</span></span>|<span data-ttu-id="6cb9a-141"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> Metoda.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-141"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="6cb9a-142">Získání <xref:System.IO.UnmanagedMemoryStream> objekt pro sekvenční přístup k zobrazení souborů mapovaných do paměti.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-142">To obtain a <xref:System.IO.UnmanagedMemoryStream> object for a sequentially accessed view to the memory-mapped file.</span></span>|<span data-ttu-id="6cb9a-143"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> Metoda.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-143"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="6cb9a-144">Získání <xref:System.IO.UnmanagedMemoryAccessor> objekt pro náhodný přístup zobrazení mapované paměti soubor.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-144">To obtain a <xref:System.IO.UnmanagedMemoryAccessor> object for a random access view to a memory-mapped fie.</span></span>|<span data-ttu-id="6cb9a-145"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> Metoda.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-145"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="6cb9a-146">Získání <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> objekt pro použití s nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-146">To obtain a <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> object to use with unmanaged code.</span></span>|<span data-ttu-id="6cb9a-147"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> Vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-147"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="6cb9a-148">- nebo -</span><span class="sxs-lookup"><span data-stu-id="6cb9a-148">- or -</span></span><br /><br /> <span data-ttu-id="6cb9a-149"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> Vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-149"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="6cb9a-150">- nebo -</span><span class="sxs-lookup"><span data-stu-id="6cb9a-150">- or -</span></span><br /><br /> <span data-ttu-id="6cb9a-151"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> Vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-151"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span>|  
|<span data-ttu-id="6cb9a-152">Zpoždění přidělování paměti až do zobrazení je vytvořit (dočasný pouze soubory).</span><span class="sxs-lookup"><span data-stu-id="6cb9a-152">To delay allocating memory until a view is created (non-persisted files only).</span></span><br /><br /> <span data-ttu-id="6cb9a-153">(Chcete-li zjistit aktuální velikost systémové stránky, použijte <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> vlastnosti.)</span><span class="sxs-lookup"><span data-stu-id="6cb9a-153">(To determine the current system page size, use the <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> property.)</span></span>|<span data-ttu-id="6cb9a-154"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> Metoda s <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-154"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> method with the <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> value.</span></span><br /><br /> <span data-ttu-id="6cb9a-155">- nebo -</span><span class="sxs-lookup"><span data-stu-id="6cb9a-155">- or -</span></span><br /><br /> <span data-ttu-id="6cb9a-156"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> metody, které mají <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> výčet jako parametr.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-156"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods that have a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> enumeration as a parameter.</span></span>|  
  
### <a name="security"></a><span data-ttu-id="6cb9a-157">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="6cb9a-157">Security</span></span>  
 <span data-ttu-id="6cb9a-158">Oprávnění můžete použít při vytváření souboru mapovaných do paměti pomocí následujících metod, které provést <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> výčet jako parametr:</span><span class="sxs-lookup"><span data-stu-id="6cb9a-158">You can apply access rights when you create a memory-mapped file, by using the following methods that take a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> enumeration as a parameter:</span></span>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="6cb9a-159">Můžete zadat přístupová práva k otevření existujícího souboru mapovaných do paměti pomocí <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> metodám, které přebírají <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> jako parametr.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-159">You can specify access rights for opening an existing memory-mapped file by using the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> methods that take an <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> as a parameter.</span></span>  
  
 <span data-ttu-id="6cb9a-160">Kromě toho můžete zahrnout <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> objekt, který obsahuje předdefinovaná pravidla přístupu.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-160">In addition, you can include a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> object that contains predefined access rules.</span></span>  
  
 <span data-ttu-id="6cb9a-161">Chcete-li použít nové nebo změněné pravidel přístupu do souboru mapovaných do paměti, použijte <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-161">To apply new or changed access rules to a memory-mapped file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> method.</span></span> <span data-ttu-id="6cb9a-162">Pokud chcete získat přístup nebo auditovat pravidla z existujícího souboru, použijte <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-162">To retrieve access or audit rules from an existing file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="6cb9a-163">Příklady</span><span class="sxs-lookup"><span data-stu-id="6cb9a-163">Examples</span></span>  
  
### <a name="persisted-memory-mapped-files"></a><span data-ttu-id="6cb9a-164">Trvalé soubory mapované paměti</span><span class="sxs-lookup"><span data-stu-id="6cb9a-164">Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="6cb9a-165"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> Metody vytvořit soubor mapované paměti z existujícího souboru na disku.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-165">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> methods create a memory-mapped file from an existing file on disk.</span></span>  
  
 <span data-ttu-id="6cb9a-166">Následující příklad vytvoří zobrazení součástí velmi velkých souborů mapovaných do paměti a manipuluje s jejich část.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-166">The following example creates a memory-mapped view of a part of an extremely large file and manipulates a portion of it.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  
  
 <span data-ttu-id="6cb9a-167">Následující příklad otevře stejné souborů mapovaných do paměti pro jiný proces.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-167">The following example opens the same memory-mapped file for another process.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a><span data-ttu-id="6cb9a-168">Netrvalé soubory mapované paměti</span><span class="sxs-lookup"><span data-stu-id="6cb9a-168">Non-Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="6cb9a-169"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> metody vytvořit soubor mapovaných do paměti, který není namapovaná na existující soubor na disku.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-169">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> and <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods create a memory-mapped file that is not mapped to an existing file on disk.</span></span>  
  
 <span data-ttu-id="6cb9a-170">Následující příklad se skládá ze tří samostatné procesy (konzolové aplikace), které zápis logické hodnoty do souboru mapovaných do paměti.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-170">The following example consists of three separate processes (console applications) that write Boolean values to a memory-mapped file.</span></span> <span data-ttu-id="6cb9a-171">Dojde k následující posloupnost akcí:</span><span class="sxs-lookup"><span data-stu-id="6cb9a-171">The following sequence of actions occur:</span></span>  
  
1.  <span data-ttu-id="6cb9a-172">`Process A` Vytvoří soubor mapovaných do paměti a zapíše do jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-172">`Process A` creates the memory-mapped file and writes a value to it.</span></span>  
  
2.  <span data-ttu-id="6cb9a-173">`Process B` Otevře soubor mapovaných do paměti a zapíše do jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-173">`Process B` opens the memory-mapped file and writes a value to it.</span></span>  
  
3.  <span data-ttu-id="6cb9a-174">`Process C` Otevře soubor mapovaných do paměti a zapíše do jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-174">`Process C` opens the memory-mapped file and writes a value to it.</span></span>  
  
4.  <span data-ttu-id="6cb9a-175">`Process A` načte a zobrazí hodnoty ze souborů mapovaných do paměti.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-175">`Process A` reads and displays the values from the memory-mapped file.</span></span>  
  
5.  <span data-ttu-id="6cb9a-176">Po `Process A` bylo dokončeno s souborů mapovaných do paměti soubor okamžitě uvolněn systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-176">After `Process A` is finished with the memory-mapped file, the file is immediately reclaimed by garbage collection.</span></span>  
  
 <span data-ttu-id="6cb9a-177">Chcete-li spustit tento příklad, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="6cb9a-177">To run this example, do the following:</span></span>  
  
1.  <span data-ttu-id="6cb9a-178">Zkompilujte aplikaci a otevřít tři okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-178">Compile the applications and open three Command Prompt windows.</span></span>  
  
2.  <span data-ttu-id="6cb9a-179">V prvním okně příkazového řádku, spusťte `Process A`.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-179">In the first Command Prompt window, run `Process A`.</span></span>  
  
3.  <span data-ttu-id="6cb9a-180">V druhém okně příkazového řádku, spusťte `Process B`.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-180">In the second Command Prompt window, run `Process B`.</span></span>  
  
4.  <span data-ttu-id="6cb9a-181">Vraťte se na `Process A` a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-181">Return to `Process A` and press ENTER.</span></span>  
  
5.  <span data-ttu-id="6cb9a-182">V okně příkazového řádku třetí spusťte `Process C`.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-182">In the third Command Prompt window, run `Process C`.</span></span>  
  
6.  <span data-ttu-id="6cb9a-183">Vraťte se na `Process A` a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="6cb9a-183">Return to `Process A` and press ENTER.</span></span>  
  
 <span data-ttu-id="6cb9a-184">Výstup `Process A` vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="6cb9a-184">The output of `Process A` is as follows:</span></span>  
  
```  
Start Process B and press ENTER to continue.  
Start Process C and press ENTER to continue.  
Process A says: True  
Process B says: False  
Process C says: True  
```  
  
 <span data-ttu-id="6cb9a-185">**Proces A**</span><span class="sxs-lookup"><span data-stu-id="6cb9a-185">**Process A**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/vb/program.vb#1)]  
  
 <span data-ttu-id="6cb9a-186">**Proces B**</span><span class="sxs-lookup"><span data-stu-id="6cb9a-186">**Process B**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/vb/program.vb#1)]  
  
 <span data-ttu-id="6cb9a-187">**Process C**</span><span class="sxs-lookup"><span data-stu-id="6cb9a-187">**Process C**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6cb9a-188">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6cb9a-188">See also</span></span>

- [<span data-ttu-id="6cb9a-189">Vstup/výstup souborů a streamů</span><span class="sxs-lookup"><span data-stu-id="6cb9a-189">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
