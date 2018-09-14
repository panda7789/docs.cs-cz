---
title: LINQ a souborové adresáře (C#)
ms.date: 07/20/2015
ms.assetid: b66c55e4-0f72-44e5-b086-519f9962335c
ms.openlocfilehash: 4bdd21cf4d8558f140b265f195368082964c34c4
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45514882"
---
# <a name="linq-and-file-directories-c"></a>LINQ a souborové adresáře (C#)
Mnoho operací systému souborů jsou v podstatě dotazy a jsou proto vhodné k přístupu LINQ.  
  
 Všimněte si, že jsou nedestruktivního dotazy v této části. Používají se ke změně obsahu původní soubory nebo složky. To se řídí pravidlo, že dotazů by neměly způsobit žádné vedlejší účinky. Obecně platí jakýkoli kód (včetně dotazů, které provádějí vytvořit / aktualizovat / odstranit operátory), který upravuje zdrojová data by měla být udržovány odděleně od kódu, který se právě dotazuje data.  
  
 Tato část obsahuje následující témata:  
  
 [Postupy: dotaz na soubory s konkrétním atributem či názvem (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 Ukazuje, jak budou hledány soubory porovnáním jednoho nebo více vlastností jeho <xref:System.IO.FileInfo> objektu.  
  
 [Postupy: seskupování souborů podle přípony (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 Ukazuje, jak vrátit skupiny <xref:System.IO.FileInfo> objektu podle přípony názvu souboru.  
  
 [Postupy: dotaz pro celkový počet bajtů v sadě složek (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)  
 Ukazuje, jak vrátit celkový počet bajtů ve všech souborech v zadaném adresáři stromu.  
  
 [Postupy: porovnání obsahu dvou složek (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-compare-the-contents-of-two-folders-linq.md)s  
 Ukazuje, jak vrátit všechny soubory, které jsou k dispozici ve dvou zadaných složek a také všechny soubory, které se nacházejí v jedné složce, ale nikoli u druhého.  
  
 [Postupy: dotazování na největší soubor či soubory v adresářovém stromu (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)  
 Ukazuje, jak vrátit soubor největší nebo nejmenší nebo zadaný počet souborů v adresářovém stromu.  
  
 [Postupy: dotazu na duplicitní soubory v adresářovém stromu (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)  
 Ukazuje, jak do skupiny pro všechny názvy souborů, které se vyskytují ve více než jedné oblasti ve stromové struktuře zadaný adresář. Také ukazuje, jak k provádění složitějších porovnání založené na vlastní porovnávací metody.  
  
 [Postupy: dotazování na obsah souborů ve složce (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-the-contents-of-files-in-a-folder-lin.md)  
 Ukazuje, jak k iteraci v rámci složky ve stromové struktuře, otevřete každý soubor a dotazování obsah souboru.  
  
## <a name="comments"></a>Komentáře  
 Při vytváření zdroje dat se přesně reprezentuje obsah systému souborů a zpracovává výjimky, bez výpadku je složitost. Příklady v této části vytvořit snímek kolekce <xref:System.IO.FileInfo> objekty, které představují všechny soubory v zadané kořenové složce a jejích podsložkách. Skutečný stav každého <xref:System.IO.FileInfo> v době mezi kdy začínají i končí provádění dotazu se může změnit. Například můžete vytvořit seznam <xref:System.IO.FileInfo> objektů, který se použije jako zdroj dat. Pokud se pokusíte o přístup k `Length` vlastnost v dotazu <xref:System.IO.FileInfo> objekt se pokusí získat přístup a aktualizujte hodnotu v systému souborů `Length`. Pokud soubor už existuje, zobrazí se <xref:System.IO.FileNotFoundException> v dotazu, i když jste nejsou dotazování systému souborů přímo. Některé dotazy v této části použijte samostatné metodě, která využívá tyto konkrétní výjimky v některých případech. Další možností je udržovat zdroje dat pomocí dynamické aktualizace <xref:System.IO.FileSystemWatcher>.  
  
## <a name="see-also"></a>Viz také

- [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
