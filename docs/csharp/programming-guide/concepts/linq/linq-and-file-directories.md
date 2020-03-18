---
title: Linq a adresáře souborů (C#)
ms.date: 07/20/2015
ms.assetid: b66c55e4-0f72-44e5-b086-519f9962335c
ms.openlocfilehash: fe503584e7d14e8d1dd281eb644f0723782feb4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714630"
---
# <a name="linq-and-file-directories-c"></a>Linq a adresáře souborů (C#)

Mnoho operací systému souborů jsou v podstatě dotazy a jsou proto vhodné pro přístup LINQ.  
  
 Dotazy v této části jsou nedestruktivní. Nepoužívají se ke změně obsahu původních souborů nebo složek. Toto pravidlo, že dotazy by neměly způsobit žádné vedlejší účinky. Obecně platí, že jakýkoli kód (včetně dotazů, které provádějí operátory create / update / delete), který upravuje zdrojová data, by měl být oddělen od kódu, který pouze dotazuje data.  
  
 Tato část obsahuje následující témata:  
  
 [Jak dotazovat na soubory se zadaným atributem nebo názvem (C#)](./how-to-query-for-files-with-a-specified-attribute-or-name.md)\
 Ukazuje, jak vyhledávat soubory kontrolou jedné nebo <xref:System.IO.FileInfo> více vlastností jeho objektu.  
  
 [Jak seskupit soubory podle přípony (LINQ) (C#)](./how-to-group-files-by-extension-linq.md)\
 Ukazuje, jak vrátit <xref:System.IO.FileInfo> skupiny objektů na základě jejich přípony názvu souboru.  
  
 [Jak dotazovat na celkový počet bajtů v sadě složek (LINQ) (C#)](./how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)\
 Ukazuje, jak vrátit celkový počet bajtů ve všech souborech v zadaném adresářovém stromu.  
  
 [Jak porovnat obsah dvou složek (LINQ) (C#)](./how-to-compare-the-contents-of-two-folders-linq.md)s  
 Ukazuje, jak vrátit všechny soubory, které jsou přítomny ve dvou zadaných složkách a také všechny soubory, které jsou přítomny v jedné složce, ale ne v druhé.  
  
 [Jak dotazovat na největší soubor nebo soubory ve stromu adresářů (LINQ) (C#)](./how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)\
 Ukazuje, jak vrátit největší nebo nejmenší soubor nebo zadaný počet souborů ve stromu adresářů.  
  
 [Jak dotazovat duplicitní soubory ve stromu adresářů (LINQ) (C#)](./how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)\
 Ukazuje, jak seskupit pro všechny názvy souborů, které se vyskytují ve více než jednom umístění v zadaném adresářovém stromu. Také ukazuje, jak provádět složitější porovnání na základě vlastní porovnávání.  
  
 [Jak dotazovat obsah souborů ve složce (LINQ) (C#)](./how-to-query-the-contents-of-files-in-a-folder-lin.md)\
 Ukazuje, jak itetovat složky ve stromu, otevřít každý soubor a dotazovat se na obsah souboru.  
  
## <a name="comments"></a>Komentáře  
 Při vytváření zdroje dat, který přesně reprezentuje obsah systému souborů a řádně zpracovává výjimky, je spojena s určitou složitostí. Příklady v této části vytvořit <xref:System.IO.FileInfo> snímek kolekce objektů, které představuje všechny soubory v zadané kořenové složce a všechny jeho podsložky. Skutečný stav každého <xref:System.IO.FileInfo> z nich může změnit v době mezi zahájením a ukončením provádění dotazu. Můžete například vytvořit seznam <xref:System.IO.FileInfo> objektů, které chcete použít jako zdroj dat. Pokud se pokusíte `Length` o přístup k <xref:System.IO.FileInfo> vlastnosti v dotazu, objekt se `Length`pokusí o přístup k systému souborů aktualizovat hodnotu . Pokud soubor již neexistuje, získáte <xref:System.IO.FileNotFoundException> dotaz, i když nejste dotazování systému souborů přímo. Některé dotazy v této části používají samostatnou metodu, která v některých případech využívá tyto konkrétní výjimky. Další možností je dynamicky aktualizovat zdroj dat <xref:System.IO.FileSystemWatcher>pomocí .  
  
## <a name="see-also"></a>Viz také

- [LINQ na objekty (C#)](./linq-to-objects.md)
