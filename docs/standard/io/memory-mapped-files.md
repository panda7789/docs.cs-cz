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
ms.openlocfilehash: f7bda02e1862740e6a6328835367a6a5e9929033
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59328306"
---
# <a name="memory-mapped-files"></a>Soubory mapované paměti
Soubor mapovaných do paměti obsahuje obsah souboru ve virtuální paměti. Toto mapování mezi prostoru soubor a paměť umožňuje aplikaci, včetně více procesů, upravte soubor tak, že čtení a zápis přímo na paměť. Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], spravovaný kód můžete použít pro přístup k souborům mapované paměti stejným způsobem, že nativní funkce Windows přístup k souborům mapované paměti, jak je popsáno v [soubory mapované paměti](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10)).  
  
 Existují dva typy souborů mapovaných do paměti:  
  
-   Trvalé soubory mapované paměti  
  
     Trvalé soubory jsou soubory mapované paměti, které jsou přidruženy ke zdrojovému souboru na disku. Po dokončení práce se souborem posledního procesu, data uložena do zdrojového souboru na disku. Tyto soubory mapované paměti jsou vhodné pro práci s velmi velký zdrojové soubory.  
  
-   Netrvalé soubory mapované paměti  
  
     Netrvalé soubory jsou soubory mapované paměti, které nejsou přiřazeny k souboru na disku. Po dokončení práce se souborem posledního procesu, dojde ke ztrátě dat a soubor je uvolněn systémem uvolňování paměti. Tyto soubory jsou vhodné pro vytvoření sdílené paměti pro meziprocesové komunikace (IPC).  
  
## <a name="processes-views-and-managing-memory"></a>Procesy, zobrazení a správa paměti  
 Soubory mapované paměti mohou být sdílena několika procesy. Procesy můžete namapovat na stejný soubor mapovaných do paměti pomocí běžný název, který je přiřazen podle procesu, který vytvořil soubor.  
  
 Pro práci se souborem mapovaných do paměti, musí vytvořit zobrazení celého souboru mapované paměti nebo jeho část. Můžete také vytvořit více zobrazení do stejné části souborů mapovaných do paměti a tím vytváření souběžných paměti. Dvě zobrazení zůstat souběžných mají být vytvořené ze stejného souboru mapovaných do paměti.  
  
 Více zobrazení může být také nutné v případě, že soubor je větší než velikost logického paměťový prostor vaší aplikace k dispozici pro mapování (na 32bitových počítačích 2 GB) paměti.  
  
 Existují dva typy zobrazení: datový proud stream přístup k zobrazení a zobrazení náhodný přístup. Použití zobrazení datových proudů pro sekvenční přístup k souboru. To se doporučuje pro dočasné soubory a IPC. Náhodný přístup zobrazení jsou upřednostňované pro práci s trvalými soubory.  
  
 Soubory mapované paměti jsou přístupné prostřednictvím Správce paměti operačního systému, takže soubor automaticky je rozdělen do několika stránek a přístup podle potřeby. Není potřeba zpracovávat správu paměti.  
  
 Následující obrázek znázorňuje způsob více procesů může mít více a překrývající se zobrazení stejné souborů mapovaných do paměti ve stejnou dobu.

 Následující obrázek ukazuje několik a překrývající se zobrazení souboru mapovaných do paměti:  
  
 ![Snímek obrazovky zobrazující zobrazení paměti&#45;namapované souboru.](./media/memory-mapped-files/memory-map-persist-file.png)  
  
## <a name="programming-with-memory-mapped-files"></a>Programování s soubory mapované paměti  
 Následující tabulka obsahuje návod pro použití souborů mapovaných do paměti objektů a jejich členy.  
  
|Úloha|Metody nebo vlastnosti, které chcete použít|  
|----------|----------------------------------|  
|Získání <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> objekt, který reprezentuje trvalých souborů mapovaných do paměti ze souboru na disku.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> Metoda.|  
|Získání <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> objekt, který reprezentuje netrvalé souborů mapovaných do paměti (není přidružené k souboru na disku).|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> Metoda.<br /><br /> - nebo -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> Metoda.|  
|Získání <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> objekt existující soubor mapovaných do paměti (trvalá nebo netrvalé).|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> Metoda.|  
|Získání <xref:System.IO.UnmanagedMemoryStream> objekt pro sekvenční přístup k zobrazení souborů mapovaných do paměti.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> Metoda.|  
|Získání <xref:System.IO.UnmanagedMemoryAccessor> objekt pro náhodný přístup zobrazení mapované paměti soubor.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> Metoda.|  
|Získání <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> objekt pro použití s nespravovaným kódem.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> Vlastnost.<br /><br /> - nebo -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> Vlastnost.<br /><br /> - nebo -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> Vlastnost.|  
|Zpoždění přidělování paměti až do zobrazení je vytvořit (dočasný pouze soubory).<br /><br /> (Chcete-li zjistit aktuální velikost systémové stránky, použijte <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> vlastnosti.)|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> Metoda s <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> hodnotu.<br /><br /> - nebo -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> metody, které mají <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> výčet jako parametr.|  
  
### <a name="security"></a>Zabezpečení  
 Oprávnění můžete použít při vytváření souboru mapovaných do paměti pomocí následujících metod, které provést <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> výčet jako parametr:  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 Můžete zadat přístupová práva k otevření existujícího souboru mapovaných do paměti pomocí <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> metodám, které přebírají <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> jako parametr.  
  
 Kromě toho můžete zahrnout <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> objekt, který obsahuje předdefinovaná pravidla přístupu.  
  
 Chcete-li použít nové nebo změněné pravidel přístupu do souboru mapovaných do paměti, použijte <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> metody. Pokud chcete získat přístup nebo auditovat pravidla z existujícího souboru, použijte <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> metody.  
  
## <a name="examples"></a>Příklady  
  
### <a name="persisted-memory-mapped-files"></a>Trvalé soubory mapované paměti  
 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> Metody vytvořit soubor mapované paměti z existujícího souboru na disku.  
  
 Následující příklad vytvoří zobrazení součástí velmi velkých souborů mapovaných do paměti a manipuluje s jejich část.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  
  
 Následující příklad otevře stejné souborů mapovaných do paměti pro jiný proces.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a>Netrvalé soubory mapované paměti  
 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> metody vytvořit soubor mapovaných do paměti, který není namapovaná na existující soubor na disku.  
  
 Následující příklad se skládá ze tří samostatné procesy (konzolové aplikace), které zápis logické hodnoty do souboru mapovaných do paměti. Dojde k následující posloupnost akcí:  
  
1. `Process A` Vytvoří soubor mapovaných do paměti a zapíše do jeho hodnotu.  
  
2. `Process B` Otevře soubor mapovaných do paměti a zapíše do jeho hodnotu.  
  
3. `Process C` Otevře soubor mapovaných do paměti a zapíše do jeho hodnotu.  
  
4. `Process A` načte a zobrazí hodnoty ze souborů mapovaných do paměti.  
  
5. Po `Process A` bylo dokončeno s souborů mapovaných do paměti soubor okamžitě uvolněn systémem uvolňování paměti.  
  
 Chcete-li spustit tento příklad, postupujte takto:  
  
1. Zkompilujte aplikaci a otevřít tři okna příkazového řádku.  
  
2. V prvním okně příkazového řádku, spusťte `Process A`.  
  
3. V druhém okně příkazového řádku, spusťte `Process B`.  
  
4. Vraťte se na `Process A` a stiskněte klávesu ENTER.  
  
5. V okně příkazového řádku třetí spusťte `Process C`.  
  
6. Vraťte se na `Process A` a stiskněte klávesu ENTER.  
  
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
  
 **Process C**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/vb/program.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Vstup/výstup souborů a streamů](../../../docs/standard/io/index.md)
