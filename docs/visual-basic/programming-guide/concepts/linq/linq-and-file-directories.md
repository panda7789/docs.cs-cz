---
title: LINQ a souborové adresáře
ms.date: 07/20/2015
ms.assetid: 159fd5c3-3926-4071-ae78-d8e423287eb7
ms.openlocfilehash: 9738dc2b07b33b2d96f8134e8418c54aae53e6a1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397516"
---
# <a name="linq-and-file-directories-visual-basic"></a>LINQ a souborové adresáře (Visual Basic)
Mnohé operace se systémem souborů jsou v podstatě dotazy a jsou proto vhodné pro přístup LINQ.  
  
 Všimněte si, že dotazy v této části nejsou destruktivní. Nepoužívají se ke změně obsahu původních souborů nebo složek. Následuje pravidlo, že dotazy by neměly způsobovat žádné vedlejší účinky. Obecně platí, že jakýkoli kód (včetně dotazů, které provádějí operátory vytvořit/aktualizovat/odstranit), který upravuje zdrojová data, by měl být oddělen od kódu, který data pouze dotazuje.  
  
 Tato část obsahuje následující témata:  
  
 [Postupy: dotazování na soubory se zadaným atributem nebo názvem (Visual Basic)](how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 Ukazuje, jak hledat soubory prozkoumáním jedné nebo více vlastností jejího <xref:System.IO.FileInfo> objektu.  
  
 [Postupy: seskupování souborů podle přípony (LINQ) (Visual Basic)](how-to-group-files-by-extension-linq.md)  
 Ukazuje, jak vrátit skupiny <xref:System.IO.FileInfo> objektů na základě přípony názvu souboru.  
  
 [Postupy: vytvoření dotazu na celkový počet bajtů v sadě složek (LINQ) (Visual Basic)](how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)  
 Ukazuje, jak vrátit celkový počet bajtů ve všech souborech v zadaném stromu adresářů.  
  
 [Postupy: porovnání obsahu dvou složek (LINQ) (Visual Basic)](how-to-compare-the-contents-of-two-folders-linq.md)s  
 Ukazuje, jak vrátit všechny soubory, které jsou přítomny ve dvou zadaných složkách, a také všechny soubory, které jsou k dispozici v jedné složce, ale ne jiné.  
  
 [Postupy: vytvoření dotazu na největší soubor nebo soubory ve stromu adresářů (LINQ) (Visual Basic)](how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)  
 Ukazuje, jak v adresářovém stromu vracet největší nebo nejmenší soubor nebo určený počet souborů.  
  
 [Postupy: dotaz na duplicitní soubory v adresářovém stromu (LINQ) (Visual Basic)](how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)  
 Ukazuje, jak seskupit všechny názvy souborů, které se vyskytují ve více než jednom umístění v zadaném stromu adresářů. Také ukazuje, jak provádět složitější porovnání na základě vlastní porovnávací metody.  
  
 [Postup dotazování na obsah souborů ve složce (LINQ) (Visual Basic)](how-to-query-the-contents-of-files-in-a-folder-linq.md)  
 Ukazuje, jak iterovat složky ve stromu, otevřít jednotlivé soubory a zadat dotaz na obsah souboru.  
  
## <a name="comments"></a>Komentáře  
 Při vytváření zdroje dat, který přesně představuje obsah systému souborů, je potřeba složitá složitost a dochází k bezproblémovému zpracování výjimek. Příklady v této části vytvoří snímek kolekce <xref:System.IO.FileInfo> objektů, které představují všechny soubory v zadané kořenové složce a všech jejích podsložkách. Skutečný stav každé z nich <xref:System.IO.FileInfo> se může v době mezi začátkem a ukončením dotazu změnit. Můžete například vytvořit seznam <xref:System.IO.FileInfo> objektů, které chcete použít jako zdroj dat. Pokud se pokusíte o přístup k `Length` vlastnosti v dotazu, <xref:System.IO.FileInfo> objekt se pokusí o přístup k systému souborů za účelem aktualizace hodnoty `Length` . Pokud soubor už neexistuje, zobrazí se <xref:System.IO.FileNotFoundException> v dotazu, i když neprovádíte dotazování systému souborů přímo. Některé dotazy v této části používají samostatnou metodu, která v určitých případech spotřebovává tyto konkrétní výjimky. Další možností je udržovat dynamicky aktualizovaný zdroj dat pomocí <xref:System.IO.FileSystemWatcher> .  
  
## <a name="see-also"></a>Viz také

- [LINQ to Objects (Visual Basic)](linq-to-objects.md)
