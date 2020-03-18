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
# <a name="memory-mapped-files"></a>Soubory mapované paměti
Soubor mapovaný v paměti obsahuje obsah souboru ve virtuální paměti. Toto mapování mezi souborem a paměťovým prostorem umožňuje aplikaci, včetně více procesů, upravit soubor čtením a zápisem přímo do paměti. Počínaje rozhraním .NET Framework 4 můžete použít spravovaný kód pro přístup k souborům mapovaným v paměti stejným způsobem, jakým nativní funkce systému Windows přistupují k souborům mapovaným v paměti, jak je popsáno v [části Správa souborů mapovaných v paměti](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10)).  
  
 Existují dva typy souborů mapovaných v paměti:  
  
- Soubory mapované v trvalé paměti  
  
     Trvalé soubory jsou soubory mapované v paměti, které jsou přidruženy ke zdrojovému souboru na disku. Po dokončení práce se souborem se souborem se data uloží do zdrojového souboru na disku. Tyto soubory mapované v paměti jsou vhodné pro práci s extrémně velkými zdrojovými soubory.  
  
- Netrvalé soubory mapované v paměti  
  
     Netrvalé soubory jsou soubory mapované v paměti, které nejsou přidruženy k souboru na disku. Po dokončení práce se souborem poslední proces dojde ke ztrátě dat a soubor je uvolněn systémem uvolňování paměti. Tyto soubory jsou vhodné pro vytváření sdílené paměti pro meziprocesovou komunikaci (IPC).  
  
## <a name="processes-views-and-managing-memory"></a>Procesy, zobrazení a správa paměti  
 Soubory mapované v paměti lze sdílet ve více procesech. Procesy lze mapovat na stejný soubor mapovaný v paměti pomocí běžného názvu, který je přiřazen procesem, který soubor vytvořil.  
  
 Chcete-li pracovat se souborem mapovaným v paměti, musíte vytvořit zobrazení celého souboru mapovaného v paměti nebo jeho části. Můžete také vytvořit více zobrazení do stejné části souboru mapované paměti, čímž se vytvoří souběžná paměť. Aby dvě zobrazení zůstala souběžná, musí být vytvořena ze stejného souboru mapovaného v paměti.  
  
 Více zobrazení může být také nezbytné, pokud je soubor větší než velikost logického paměťového prostoru aplikace, který je k dispozici pro mapování paměti (2 GB v 32bitovém počítači).  
  
 Existují dva typy zobrazení: zobrazení přístupu k datovému proudu a zobrazení s náhodným přístupem. Použití zobrazení přístupu datových proudů pro sekvenční přístup k souboru; To je doporučeno pro netrvalé soubory a IPC. Zobrazení náhodného přístupu jsou upřednostňována pro práci s trvalými soubory.  
  
 Soubory mapované v paměti jsou přístupné prostřednictvím správce paměti operačního systému, takže soubor je automaticky rozdělen na několik stránek a přistupovat podle potřeby. Není třeba zpracovávat správu paměti sami.  
  
 Následující obrázek znázorňuje, jak může mít více procesů více a překrývající se zobrazení do stejného souboru mapovaného v paměti současně.

 Následující obrázek znázorňuje více a překrývaných zobrazení do souboru mapovaného v paměti:  
  
 ![Snímek obrazovky, který zobrazuje zobrazení do paměti&#45;mapovaný soubor.](./media/memory-mapped-files/memory-map-persist-file.png)  
  
## <a name="programming-with-memory-mapped-files"></a>Programování se soubory mapovanými v paměti  
 Následující tabulka obsahuje průvodce pro použití objektů souborů mapovaných v paměti a jejich členů.  
  
|Úkol|Metody nebo vlastnosti, které mají být|  
|----------|----------------------------------|  
|Chcete-li <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> získat objekt, který představuje trvalý soubor mapovaný v paměti ze souboru na disku.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>Metoda.|  
|Chcete-li <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> získat objekt, který představuje netrvalý soubor mapovaný v paměti (není přidružen k souboru na disku).|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>Metoda.<br /><br /> - nebo -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>Metoda.|  
|Chcete-li <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> získat objekt existujícího souboru mapované ho u paměti (trvalé nebo netrvalé).|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType>Metoda.|  
|Chcete-li <xref:System.IO.UnmanagedMemoryStream> získat objekt pro postupně přístupné zobrazení souboru mapované paměti.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType>Metoda.|  
|Chcete-li <xref:System.IO.UnmanagedMemoryAccessor> získat objekt pro zobrazení náhodného přístupu k paměti mapované fie.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType>Metoda.|  
|Chcete-li <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> získat objekt pro použití s nespravovaný kód.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType>Vlastnost.<br /><br /> - nebo -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>Vlastnost.<br /><br /> - nebo -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>Vlastnost.|  
|Zpoždění přidělování paměti, dokud není vytvořeno zobrazení (pouze netrvalé soubory).<br /><br /> (Chcete-li určit aktuální velikost <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> systémové stránky, použijte vlastnost.)|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A>s hodnotou. <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType><br /><br /> - nebo -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A>metody, které <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> mají výčet jako parametr.|  
  
### <a name="security"></a>Zabezpečení  
 Přístupová práva můžete použít při vytváření souboru mapovaného v paměti <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> pomocí následujících metod, které berou výčet jako parametr:  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 Můžete zadat přístupová práva pro otevření existujícího souboru mapovaného v paměti pomocí <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> metod, které berou <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> jako parametr.  
  
 Kromě toho můžete zahrnout <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> objekt, který obsahuje předdefinovaná pravidla přístupu.  
  
 Chcete-li použít nová nebo změněná pravidla přístupu <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> k souboru mapovanému v paměti, použijte metodu. Chcete-li načíst pravidla přístupu nebo <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> auditu z existujícího souboru, použijte metodu.  
  
## <a name="examples"></a>Příklady  
  
### <a name="persisted-memory-mapped-files"></a>Trvalé soubory mapované v paměti  
 Metody <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> vytvoří soubor mapovaný v paměti z existujícího souboru na disku.  
  
 Následující příklad vytvoří zobrazení mapované paměti části extrémně velkého souboru a manipuluje s jeho částí.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

 Následující příklad otevře stejný soubor mapovaný v paměti pro jiný proces.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a>Netrvalé soubory mapované v paměti  
 Metody <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> a vytvoří soubor mapovaný v paměti, který není mapován na existující soubor na disku.  
  
 Následující příklad se skládá ze tří samostatných procesů (konzolové aplikace), které zapisují logické hodnoty do souboru mapovaného v paměti. Dochází k následující posloupnosti akcí:  
  
1. `Process A`vytvoří soubor mapovaný v paměti a zapíše do něj hodnotu.  
  
2. `Process B`otevře soubor mapovaný v paměti a zapíše do něj hodnotu.  
  
3. `Process C`otevře soubor mapovaný v paměti a zapíše do něj hodnotu.  
  
4. `Process A`přečte a zobrazí hodnoty ze souboru mapovaného v paměti.  
  
5. Po `Process A` dokončení s mapovaným souborem paměti je soubor okamžitě uvolněn systémem uvolňování paměti.  
  
 Chcete-li spustit tento příklad, postupujte takto:  
  
1. Zkompilujte aplikace a otevřete tři okna příkazového řádku.  
  
2. V prvním okně příkazového `Process A`řádku spusťte .  
  
3. V druhém okně příkazového `Process B`řádku spusťte .  
  
4. Vraťte `Process A` se a stiskněte klávesu ENTER.  
  
5. Ve třetím okně příkazového `Process C`řádku spusťte .  
  
6. Vraťte `Process A` se a stiskněte klávesu ENTER.  
  
 Výstup `Process A` je následující:  
  
```console  
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

- [I/O souborů a proudů](../../../docs/standard/io/index.md)
