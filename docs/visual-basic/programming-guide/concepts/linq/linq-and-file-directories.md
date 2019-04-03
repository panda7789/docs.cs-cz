---
title: LINQ a souborové adresáře (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 159fd5c3-3926-4071-ae78-d8e423287eb7
ms.openlocfilehash: 56967a82bf63d8421d34af48dcc6384ded85e2ad
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825115"
---
# <a name="linq-and-file-directories-visual-basic"></a>LINQ a souborové adresáře (Visual Basic)
Mnoho operací systému souborů jsou v podstatě dotazy a jsou proto vhodné k přístupu LINQ.  
  
 Všimněte si, že jsou nedestruktivního dotazy v této části. Používají se ke změně obsahu původní soubory nebo složky. To se řídí pravidlo, že dotazů by neměly způsobit žádné vedlejší účinky. Obecně platí jakýkoli kód (včetně dotazů, které provádějí vytvořit / aktualizovat / odstranit operátory), který upravuje zdrojová data by měla být udržovány odděleně od kódu, který se právě dotazuje data.  
  
 Tato část obsahuje následující témata:  
  
 [Postupy: Dotaz pro soubory s konkrétním atributem či názvem (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 Ukazuje, jak budou hledány soubory porovnáním jednoho nebo více vlastností jeho <xref:System.IO.FileInfo> objektu.  
  
 [Postupy: Skupiny souborů podle přípony (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 Ukazuje, jak vrátit skupiny <xref:System.IO.FileInfo> objektu podle přípony názvu souboru.  
  
 [Postupy: Dotaz pro celkový počet bajtů v sadě složek (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)  
 Ukazuje, jak vrátit celkový počet bajtů ve všech souborech v zadaném adresáři stromu.  
  
 [Postupy: Porovnání obsahu dvou složek (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-compare-the-contents-of-two-folders-linq.md)s  
 Ukazuje, jak vrátit všechny soubory, které jsou k dispozici ve dvou zadaných složek a také všechny soubory, které se nacházejí v jedné složce, ale nikoli u druhého.  
  
 [Postupy: Dotaz na největší soubor či soubory v adresářovém stromu (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)  
 Ukazuje, jak vrátit soubor největší nebo nejmenší nebo zadaný počet souborů v adresářovém stromu.  
  
 [Postupy: Dotazu na duplicitní soubory v adresářovém stromu (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)  
 Ukazuje, jak do skupiny pro všechny názvy souborů, které se vyskytují ve více než jedné oblasti ve stromové struktuře zadaný adresář. Také ukazuje, jak k provádění složitějších porovnání založené na vlastní porovnávací metody.  
  
 [Postupy: Dotaz na obsah souborů ve složce (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-the-contents-of-files-in-a-folder-linq.md)  
 Ukazuje, jak k iteraci v rámci složky ve stromové struktuře, otevřete každý soubor a dotazování obsah souboru.  
  
## <a name="comments"></a>Komentáře  
 Při vytváření zdroje dat se přesně reprezentuje obsah systému souborů a zpracovává výjimky, bez výpadku je složitost. Příklady v této části vytvořit snímek kolekce <xref:System.IO.FileInfo> objekty, které představují všechny soubory v zadané kořenové složce a jejích podsložkách. Skutečný stav každého <xref:System.IO.FileInfo> v době mezi kdy začínají i končí provádění dotazu se může změnit. Například můžete vytvořit seznam <xref:System.IO.FileInfo> objektů, který se použije jako zdroj dat. Pokud se pokusíte o přístup k `Length` vlastnost v dotazu <xref:System.IO.FileInfo> objekt se pokusí získat přístup a aktualizujte hodnotu v systému souborů `Length`. Pokud soubor už existuje, zobrazí se <xref:System.IO.FileNotFoundException> v dotazu, i když jste nejsou dotazování systému souborů přímo. Některé dotazy v této části použijte samostatné metodě, která využívá tyto konkrétní výjimky v některých případech. Další možností je udržovat zdroje dat pomocí dynamické aktualizace <xref:System.IO.FileSystemWatcher>.  
  
## <a name="see-also"></a>Viz také:

- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
