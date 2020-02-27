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
ms.openlocfilehash: 7d80099fcfcba58cd863004ba7faf0bafa3abd09
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628017"
---
# <a name="memory-mapped-files"></a>Soubory mapované paměti
Soubor mapované paměti obsahuje obsah souboru ve virtuální paměti. Toto mapování mezi souborem a prostorem paměti umožňuje aplikaci, včetně více procesů, pro úpravu souboru čtením a zápisem přímo do paměti. Počínaje .NET Framework 4 můžete použít spravovaný kód pro přístup k souborům mapovaným do paměti stejným způsobem jako nativní funkce systému Windows přistupující k souborům mapovaným do paměti, jak je popsáno v tématu [Správa souborů mapovaných](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10))do paměti.  
  
 Existují dva typy souborů mapovaných do paměti:  
  
- Trvalá paměťově mapované soubory  
  
     Trvalé soubory jsou soubory mapované paměti, které jsou přidruženy ke zdrojovému souboru na disku. Až poslední proces dokončí práci se souborem, data se uloží do zdrojového souboru na disku. Tyto soubory mapované paměti jsou vhodné pro práci s extrémně velkými zdrojovými soubory.  
  
- Netrvalá paměťově mapované soubory  
  
     Netrvalé soubory jsou soubory mapované paměti, které nejsou přidruženy k souboru na disku. Až poslední proces dokončí práci se souborem, data se ztratí a soubor se uvolní uvolňováním paměti. Tyto soubory jsou vhodné pro vytváření sdílené paměti pro komunikaci mezi procesy (IPC).  
  
## <a name="processes-views-and-managing-memory"></a>Procesy, zobrazení a správa paměti  
 Soubory mapované paměti lze sdílet mezi několika procesy. Procesy lze namapovat na stejný soubor mapované paměti pomocí běžného názvu, který je přiřazen procesem, který soubor vytvořil.  
  
 Chcete-li pracovat se souborem mapované paměti, je nutné vytvořit zobrazení celého souboru mapované paměti nebo jeho části. Můžete také vytvořit více zobrazení do stejné části souboru mapované paměti, čímž vytvoříte souběžnou paměť. Aby dvě zobrazení zůstaly souběžně, je nutné je vytvořit ze stejného souboru mapované paměti.  
  
 V případě, že je soubor větší než velikost logické paměti, která je k dispozici pro mapování paměti (2 GB na 32 počítači), může být také nutné použít více zobrazení.  
  
 K dispozici jsou dva typy zobrazení: zobrazení datového proudu a zobrazení náhodného přístupu. Pro sekvenční přístup k souboru použijte zobrazení přístupu ke službě Stream. Tento postup se doporučuje u souborů, které nejsou trvale uložené, a IPC. Zobrazení náhodného přístupu jsou upřednostňována pro práci s trvalými soubory.  
  
 Soubory mapované paměti jsou k dispozici prostřednictvím Správce paměti operačního systému, takže soubor je automaticky rozdělený na několik stránek a v případě potřeby je k dispozici. Správu paměti není nutné zpracovávat sami.  
  
 Následující ilustrace znázorňuje, jak více procesů může mít více a překrývajících se zobrazení do stejného souboru mapované paměti ve stejnou dobu.

 Následující obrázek ukazuje více a překrývajících se zobrazení do souboru mapované paměti:  
  
 ![Snímek obrazovky, který zobrazuje zobrazení souboru&#45;mapované paměti.](./media/memory-mapped-files/memory-map-persist-file.png)  
  
## <a name="programming-with-memory-mapped-files"></a>Programování s namapovanými soubory paměti  
 Následující tabulka poskytuje návod pro použití objektů souboru mapovaných do paměti a jejich členů.  
  
|Úkol|Metody nebo vlastnosti, které se mají použít|  
|----------|----------------------------------|  
|Chcete-li získat objekt <xref:System.IO.MemoryMappedFiles.MemoryMappedFile>, který představuje trvalý soubor mapované paměti ze souboru na disku.|Metoda <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>.|  
|Chcete-li získat objekt <xref:System.IO.MemoryMappedFiles.MemoryMappedFile>, který představuje netrvalý soubor mapované paměti (není přidružen k souboru na disku).|Metoda <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>.<br /><br /> ani<br /><br /> Metoda <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>.|  
|Chcete-li získat objekt <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> existujícího souboru mapované paměti (buď trvalá, nebo netrvalá).|Metoda <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType>.|  
|Chcete-li získat objekt <xref:System.IO.UnmanagedMemoryStream> pro sekvenční zobrazení k souboru mapované paměti.|Metoda <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType>.|  
|Chcete-li získat objekt <xref:System.IO.UnmanagedMemoryAccessor> pro zobrazení náhodného přístupu k fie mapované paměti.|Metoda <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType>.|  
|Chcete-li získat objekt <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> pro použití s nespravovaným kódem.|vlastnost <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType>.<br /><br /> ani<br /><br /> vlastnost <xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>.<br /><br /> ani<br /><br /> vlastnost <xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>.|  
|Zpoždění přidělení paměti, dokud není vytvořeno zobrazení (pouze netrvalé soubory).<br /><br /> (Chcete-li zjistit aktuální velikost stránky systému, použijte vlastnost <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType>.)|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> metoda s hodnotou <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType><br /><br /> ani<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> metody, které mají <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> výčtu jako parametr.|  
  
### <a name="security"></a>Zabezpečení  
 Můžete použít přístupová práva při vytváření souboru mapované paměti pomocí následujících metod, které přijímají výčet <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> jako parametr:  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 Můžete zadat přístupová práva pro otevření existujícího souboru mapované paměti pomocí <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> metody, které jako parametr přebírají <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights>.  
  
 Kromě toho můžete zahrnout objekt <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity>, který obsahuje pravidla předdefinovaného přístupu.  
  
 Chcete-li použít nová nebo změněná pravidla přístupu k souboru mapované paměti, použijte metodu <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A>. Chcete-li načíst pravidla přístupu nebo auditu z existujícího souboru, použijte metodu <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A>.  
  
## <a name="examples"></a>Příklady  
  
### <a name="persisted-memory-mapped-files"></a>Trvalá paměťově mapované soubory  
 Metody <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> vytvoří soubor mapované paměti z existujícího souboru na disku.  
  
 Následující příklad vytvoří zobrazení mapované paměti, které je součástí velmi velkého souboru a pracuje s jeho částí.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  
 
[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

 Následující příklad otevře stejný soubor mapované paměti pro jiný proces.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a>Netrvalá paměťově mapované soubory  
 Metody <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> vytvoří soubor mapované paměti, který není namapován na existující soubor na disku.  
  
 Následující příklad obsahuje tři samostatné procesy (konzolové aplikace), které zapisují logické hodnoty do souboru mapované paměti. Dojde k následujícímu pořadí akcí:  
  
1. `Process A` vytvoří soubor mapované paměti a zapíše do něj hodnotu.  
  
2. `Process B` otevře soubor mapované paměti a zapíše do něj hodnotu.  
  
3. `Process C` otevře soubor mapované paměti a zapíše do něj hodnotu.  
  
4. `Process A` čte a zobrazuje hodnoty z souboru mapované paměti.  
  
5. Po dokončení `Process A` souborem mapované paměti je soubor okamžitě uvolněn uvolňováním paměti.  
  
 Chcete-li spustit tento příklad, postupujte následovně:  
  
1. Zkompilujte aplikace a otevřete tři okna příkazového řádku.  
  
2. V prvním okně příkazového řádku spusťte `Process A`.  
  
3. V druhém okně příkazového řádku spusťte `Process B`.  
  
4. Vraťte se do `Process A` a stiskněte klávesu ENTER.  
  
5. V třetím okně příkazového řádku spusťte `Process C`.  
  
6. Vraťte se do `Process A` a stiskněte klávesu ENTER.  
  
 Výstup `Process A` je následující:  
  
```console  
Start Process B and press ENTER to continue.  
Start Process C and press ENTER to continue.  
Process A says: True  
Process B says: False  
Process C says: True  
```  
  
 **Zpracování**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/vb/program.vb#1)]  
  
 **Zpracování B**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/vb/program.vb#1)]  
  
 **Zpracování C**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/vb/program.vb#1)]  
  
## <a name="see-also"></a>Viz také

- [Vstup/výstup souborů a streamů](../../../docs/standard/io/index.md)
