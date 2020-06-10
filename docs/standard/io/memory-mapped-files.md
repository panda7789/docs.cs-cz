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
  
 ![Snímek obrazovky, který zobrazuje zobrazení&#45;namapovaného souboru do paměti](./media/memory-mapped-files/memory-map-persist-file.png)  
  
## <a name="programming-with-memory-mapped-files"></a>Programování s namapovanými soubory paměti  
 Následující tabulka poskytuje návod pro použití objektů souboru mapovaných do paměti a jejich členů.  
  
|Úkol|Metody nebo vlastnosti, které se mají použít|  
|----------|----------------------------------|  
|Chcete-li získat <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> objekt, který představuje trvalý soubor mapované paměti ze souboru na disku.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>Metoda.|  
|Chcete-li získat <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> objekt, který představuje netrvalý soubor mapované paměti (není přidružen k souboru na disku).|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>Metoda.<br /><br /> - nebo -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>Metoda.|  
|Chcete-li získat <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> objekt existujícího souboru mapované paměti (buď trvalá, nebo netrvalá).|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType>Metoda.|  
|Pro získání <xref:System.IO.UnmanagedMemoryStream> objektu pro sekvenční zobrazení k souboru mapované paměti.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType>Metoda.|  
|Chcete-li získat <xref:System.IO.UnmanagedMemoryAccessor> objekt pro zobrazení náhodného přístupu k fie mapované paměti.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType>Metoda.|  
|Pro získání <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> objektu pro použití s nespravovaným kódem.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType>majetek.<br /><br /> - nebo -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>majetek.<br /><br /> - nebo -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>majetek.|  
|Zpoždění přidělení paměti, dokud není vytvořeno zobrazení (pouze netrvalé soubory).<br /><br /> (Chcete-li zjistit aktuální velikost stránky systému, použijte <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> vlastnost.)|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A>Metoda s <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> hodnotou.<br /><br /> - nebo -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A>metody, které mají <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> výčet jako parametr.|  
  
### <a name="security"></a>Zabezpečení  
 Přístupová práva můžete použít při vytváření souboru mapované paměti pomocí následujících metod, které přijímají <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> výčet jako parametr:  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 Můžete zadat přístupová práva pro otevření existujícího souboru mapované paměti pomocí <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> metod, které přijímají <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> jako parametr.  
  
 Kromě toho můžete zahrnout <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> objekt, který obsahuje pravidla předdefinovaného přístupu.  
  
 Chcete-li použít nová nebo změněná pravidla přístupu k souboru mapované paměti, použijte <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> metodu. Chcete-li načíst pravidla přístupu nebo auditu z existujícího souboru, použijte <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> metodu.  
  
## <a name="examples"></a>Příklady  
  
### <a name="persisted-memory-mapped-files"></a>Trvalá paměťově mapované soubory  
 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A>Metody vytvoří soubor mapované paměti z existujícího souboru na disku.  
  
 Následující příklad vytvoří zobrazení mapované paměti, které je součástí velmi velkého souboru a pracuje s jeho částí.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

 Následující příklad otevře stejný soubor mapované paměti pro jiný proces.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a>Netrvalá paměťově mapované soubory  
 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A>Metody a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> vytvoří soubor mapované paměti, který není namapován na existující soubor na disku.  
  
 Následující příklad obsahuje tři samostatné procesy (konzolové aplikace), které zapisují logické hodnoty do souboru mapované paměti. Dojde k následujícímu pořadí akcí:  
  
1. `Process A`Vytvoří soubor mapované paměti a zapíše do něj hodnotu.  
  
2. `Process B`otevře soubor mapované paměti a zapíše do něj hodnotu.  
  
3. `Process C`otevře soubor mapované paměti a zapíše do něj hodnotu.  
  
4. `Process A`přečte a zobrazí hodnoty z souboru mapované paměti.  
  
5. Po `Process A` dokončení souboru mapované paměti je soubor okamžitě uvolněn kolekcí paměti.  
  
 Chcete-li spustit tento příklad, postupujte následovně:  
  
1. Zkompilujte aplikace a otevřete tři okna příkazového řádku.  
  
2. V prvním okně příkazového řádku spusťte příkaz `Process A` .  
  
3. V druhém okně příkazového řádku spusťte příkaz `Process B` .  
  
4. Vraťte se na `Process A` a stiskněte klávesu ENTER.  
  
5. V třetím okně příkazového řádku spusťte příkaz `Process C` .  
  
6. Vraťte se na `Process A` a stiskněte klávesu ENTER.  
  
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

- [Vstupně-výstupní operace se soubory a datovým proudem](index.md)
