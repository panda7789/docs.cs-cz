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
ms.openlocfilehash: 1cf2d7f36dbfffe1c86e32eec5137840837612f4
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208498"
---
# <a name="memory-mapped-files"></a>Soubory mapované paměti
Soubor mapované paměti obsahuje obsah souboru ve virtuální paměti. Toto mapování mezi místo souboru a paměti umožňuje aplikaci, včetně více procesů, upravte soubor pro čtení a zápis přímo na paměť. Od verze [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], spravovaného kódu můžete použít pro přístup k souborům mapované paměti stejným způsobem, že nativní funkce systému Windows přístup k souborům mapované paměti, jak je popsáno v [soubory mapované paměti](https://msdn.microsoft.com/library/ms810613.aspx).  
  
 Existují dva typy soubory mapované paměti:  
  
-   Trvalé soubory mapované paměti  
  
     Trvalé soubory jsou soubory mapované paměti, které jsou přidruženy ke zdrojovému souboru na disku. Při poslední proces dokončí práci se souborem, data uložena ke zdrojovému souboru na disku. Tyto soubory mapované paměti jsou vhodné pro práci s velmi velký zdrojové soubory.  
  
-   Netrvalé soubory mapované paměti  
  
     Netrvalé soubory jsou mapované paměti soubory, které nejsou přidružené souboru na disku. Po dokončení práce se souborem posledního procesu, dojde ke ztrátě dat a soubor je uvolněn systémem uvolňování paměti. Tyto soubory jsou vhodné pro vytvoření sdílené paměti pro meziprocesová komunikace (IPC).  
  
## <a name="processes-views-and-managing-memory"></a>Procesy, zobrazení a správa paměti  
 Soubory mapované paměti můžete sdílet mezi více procesů. Procesy můžete namapovat do stejného souboru mapované paměti pomocí běžný název, který je přiřazen nástrojem proces, který vytvořil soubor.  
  
 Pro práci s soubor mapované paměti, musí vytvořit zobrazení celý soubor mapované paměti nebo jeho část. Můžete také vytvořit více zobrazení do stejné části souboru mapované paměti, a vytvoří tak souběžných paměti. Pro dvě zobrazení zůstaly souběžné mají být vytvořeny ze stejného souboru mapované paměti.  
  
 Více zobrazení může být také nutné v případě, že soubor je větší než velikost místa na logických paměti aplikace, které jsou k dispozici pro mapování (na 32bitový počítač 2 GB) paměti.  
  
 Existují dva typy zobrazení: stream, přístup k zobrazení a zobrazení náhodný přístup. Pomocí zobrazení datových proudů pro sekvenční přístup k souboru. Toto nastavení se doporučuje pro dočasné soubory a IPC. Náhodný přístup zobrazení jsou upřednostněny pro práci s trvalými soubory.  
  
 Soubory mapované paměti jsou přístupné prostřednictvím Správce paměti operačního systému, tak, aby automaticky rozdělen do několika stránek a podle potřeby přístup k souboru. Nemáte zpracovávat správu paměti.  
  
 Následující obrázek ukazuje, jak více procesů může mít několik a překrývající se zobrazení do stejného souboru mapované paměti ve stejnou dobu.  
  
 ![Zobrazuje zobrazení paměti&#45;namapované souboru. ] (../../../docs/standard/io/media/memmappersisted.png "MemMapPersisted")  
Více a překrývající se zobrazení souboru mapované paměti  
  
## <a name="programming-with-memory-mapped-files"></a>Programování s soubory mapované paměti  
 Následující tabulka poskytuje návod pro použití souboru mapované paměti objekty a jejich členové.  
  
|Úloha|Metody nebo vlastnosti, které chcete použít|  
|----------|----------------------------------|  
|K získání <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> objekt, který reprezentuje trvalý soubor mapované paměti ze souboru na disku.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> Metoda.|  
|K získání <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> objekt, který reprezentuje netrvalý soubor mapované paměti (není přidružen k souboru na disku).|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> Metoda.<br /><br /> - nebo -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> Metoda.|  
|K získání <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> objekt existující soubor mapované paměti (trvalé nebo dočasné).|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> Metoda.|  
|K získání <xref:System.IO.UnmanagedMemoryStream> objekt pro sekvenční přístup k souboru mapované paměti zobrazení.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> Metoda.|  
|K získání <xref:System.IO.UnmanagedMemoryAccessor> objekt pro zobrazení náhodný přístup do mapované paměti souboru.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> Metoda.|  
|K získání <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> objekt, který chcete použít s nespravovaným kódem.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> Vlastnost.<br /><br /> - nebo -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> Vlastnost.<br /><br /> - nebo -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> Vlastnost.|  
|Zpoždění přidělování paměti až do zobrazení se vytvoří (netrvalé pouze soubory).<br /><br /> (Chcete-li zjistit aktuální velikost stránky systému, použijte <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> vlastnost.)|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> Metoda s <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> hodnotu.<br /><br /> - nebo -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> metody, které mají <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> výčet jako parametr.|  
  
### <a name="security"></a>Zabezpečení  
 Když vytvoříte soubor mapované paměti pomocí následujících metod, které berou můžete použít přístupová práva <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> výčet jako parametr:  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 Můžete zadat přístupová práva pro otevření existující soubor mapované paměti pomocí <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> metod, které berou <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> jako parametr.  
  
 Kromě toho můžete zahrnout <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> objekt, který obsahuje předdefinovaná pravidla přístupu.  
  
 Chcete-li použít nové nebo změněné pravidel přístupu do souboru mapované paměti, použijte <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> metoda. Pokud chcete získat přístup nebo audit pravidla z existující soubor, použijte <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> metoda.  
  
## <a name="examples"></a>Příklady  
  
### <a name="persisted-memory-mapped-files"></a>Trvalé soubory mapované paměti  
 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> Metody vytvořte soubor mapované paměti z existující soubor na disku.  
  
 Následující příklad vytvoří zobrazení mapované paměti součástí velmi velkých souborů a umožňuje pracovat s její části je.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  
  
 Následující příklad otevře stejný soubor mapované paměti pro jiný proces.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a>Dočasné soubory mapované paměti  
 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> metody vytvořte soubor mapované paměti, který není namapovaná na existující soubor na disku.  
  
 V následujícím příkladu se skládá ze tří oddělených procesů (konzolové aplikace), které zapisují logické hodnoty do souboru mapované paměti. Provedou se následující posloupnost akcí:  
  
1.  `Process A` Vytvoří soubor mapované paměti a zapíše do jeho hodnotu.  
  
2.  `Process B` Otevře soubor mapované paměti a zapíše do jeho hodnotu.  
  
3.  `Process C` Otevře soubor mapované paměti a zapíše do jeho hodnotu.  
  
4.  `Process A` načítá a zobrazuje hodnoty ze souboru mapované paměti.  
  
5.  Po `Process A` po dokončení se souborem mapované paměti, je soubor okamžitě uvolněn systémem uvolňování paměti.  
  
 Pro spuštění tohoto příkladu, postupujte takto:  
  
1.  Kompilace aplikace a otevřete tři okna příkazového řádku.  
  
2.  V prvním okně příkazového řádku spusťte `Process A`.  
  
3.  V druhé okno příkazového řádku, spusťte `Process B`.  
  
4.  Vraťte se do `Process A` a stiskněte klávesu ENTER.  
  
5.  V okně příkazového řádku třetí spustit `Process C`.  
  
6.  Vraťte se do `Process A` a stiskněte klávesu ENTER.  
  
 Výstup `Process A` vypadá takto:  
  
```  
Start Process B and press ENTER to continue.  
Start Process C and press ENTER to continue.  
Process A says: True  
Process B says: False  
Process C says: True  
```  
  
 **Proces A**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/vb/program.vb#1)]  
  
 **Proces B**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/vb/program.vb#1)]  
  
 **Proces C**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/vb/program.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Vstup/výstup souborů a streamů](../../../docs/standard/io/index.md)
