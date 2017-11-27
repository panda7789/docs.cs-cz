---
title: "LINQ a souborové adresáře (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 159fd5c3-3926-4071-ae78-d8e423287eb7
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 470ad8e783eb05cc56949982b2d2d79d5aaefdc2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="linq-and-file-directories-visual-basic"></a>LINQ a souborové adresáře (Visual Basic)
Mnoho operace souborového systému jsou v podstatě dotazy a jsou proto vhodné řešení pro LINQ přístup.  
  
 Všimněte si, že dotazy v této části jsou bez destruktivní. Nejsou používány k změnit obsah původní soubory nebo složky. To odpovídá pravidlo, že dotazy by nemělo způsobit žádné vedlejší účinky. Obecně platí kód (včetně dotazů, které provádějí vytvořit / aktualizovat / odstranit operátory), který mění data zdroj by měl být udržovány odděleně od kód, který se právě dotazuje data.  
  
 Tato část obsahuje následující témata:  
  
 [Postupy: dotaz pro soubory s konkrétním atributem či názvem (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 Ukazuje, jak hledat soubory kontrolou jedné nebo více vlastností jeho <xref:System.IO.FileInfo> objektu.  
  
 [Postupy: seskupování souborů podle přípony (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 Ukazuje, jak vrátit skupiny <xref:System.IO.FileInfo> objektu podle přípony názvu souboru.  
  
 [Postupy: dotaz na celkový počet bajtů v sadě složek (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)  
 Ukazuje, jak vracet celkový počet bajtů na všechny soubory v zadané adresářovém stromu.  
  
 [Postupy: porovnání obsahu dvou složek (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-compare-the-contents-of-two-folders-linq.md)s  
 Ukazuje, jak vrátit všechny soubory, které se nacházejí v dvě zadané složky a také všechny soubory, které se nacházejí v jedné složce, ale ne na druhou.  
  
 [Postupy: dotazování na největší soubor či soubory v adresářovém stromu (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)  
 Ukazuje, jak vrátit souboru nejvyšší nebo nejnižší nebo zadaný počet soubory v adresářovém stromu.  
  
 [Postupy: dotazu na duplicitní soubory v adresářovém stromu (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)  
 Ukazuje, jak do skupiny pro všechny názvy souborů, které se vyskytují ve více než jedno umístění ve stromu zadaný adresář. Také ukazuje, jak provádět složitější porovnání založené na vlastní porovnávací funkci.  
  
 [Postupy: dotazu na obsah souborů ve složce (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-the-contents-of-files-in-a-folder-linq.md)  
 Ukazuje, jak k iteraci v rámci složky ve stromu, každý soubor otevřete a dotaz na jeho obsah.  
  
## <a name="comments"></a>Komentáře  
 Součástí procesu vytváření zdroje dat, který přesně reprezentuje obsah systému souborů a řádně ošetřuje výjimky je některé složitost. Příklady v této části vytvořit snímek kolekce <xref:System.IO.FileInfo> objekty, které představuje všechny soubory v zadané kořenové složce a jejích podsložkách. Skutečný stav jednotlivých <xref:System.IO.FileInfo> může změnit v době mezi při zahájení a ukončení provádění dotazu. Například můžete vytvořit seznam <xref:System.IO.FileInfo> objekty, které chcete použít jako zdroj dat. Pokud se pokusíte přístup `Length` vlastnost v dotazu, <xref:System.IO.FileInfo> objekt se pokusí o přístup a aktualizujte hodnotu v systému souborů `Length`. Pokud soubor již existuje, zobrazí se <xref:System.IO.FileNotFoundException> v dotazu, i když jste nejsou systému souborů přímým dotazováním. Některé dotazy v této části použijte samostatné metodu, která využívá tyto konkrétní výjimky v určitých případech. Další možností je udržovat dynamicky aktualizují v modulu zdroje dat <xref:System.IO.FileSystemWatcher>.  
  
## <a name="see-also"></a>Viz také  
 [LINQ na objekty (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
