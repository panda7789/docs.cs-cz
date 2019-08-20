---
title: LINQ a souborové adresáře (C#)
ms.date: 07/20/2015
ms.assetid: b66c55e4-0f72-44e5-b086-519f9962335c
ms.openlocfilehash: 1d2109fe7f4f907317275188057fa6e5e71b2679
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591974"
---
# <a name="linq-and-file-directories-c"></a>LINQ a souborové adresáře (C#)
Mnohé operace se systémem souborů jsou v podstatě dotazy a jsou proto vhodné pro přístup LINQ.  
  
 Všimněte si, že dotazy v této části nejsou destruktivní. Nepoužívají se ke změně obsahu původních souborů nebo složek. Následuje pravidlo, že dotazy by neměly způsobovat žádné vedlejší účinky. Obecně platí, že jakýkoli kód (včetně dotazů, které provádějí operátory vytvořit/aktualizovat/odstranit), který upravuje zdrojová data, by měl být oddělen od kódu, který data pouze dotazuje.  
  
 Tato část obsahuje následující témata:  
  
 [Postupy: Dotaz na soubory se zadaným atributem nebo názvem (C#)](./how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 Ukazuje, jak hledat soubory prozkoumáním jedné nebo více vlastností jejího <xref:System.IO.FileInfo> objektu.  
  
 [Postupy: Seskupit soubory podle přípony (LINQ) (C#)](./how-to-group-files-by-extension-linq.md)  
 Ukazuje, jak vrátit skupiny <xref:System.IO.FileInfo> objektů na základě přípony názvu souboru.  
  
 [Postupy: Dotaz na celkový počet bajtů v sadě složek (LINQ) (C#)](./how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)  
 Ukazuje, jak vrátit celkový počet bajtů ve všech souborech v zadaném stromu adresářů.  
  
 [Postupy: Porovnat obsah dvou složek (LINQ) (C#) s](./how-to-compare-the-contents-of-two-folders-linq.md)  
 Ukazuje, jak vrátit všechny soubory, které jsou přítomny ve dvou zadaných složkách, a také všechny soubory, které jsou k dispozici v jedné složce, ale ne jiné.  
  
 [Postupy: Dotaz na největší soubor nebo soubory v adresářovém stromu (LINQ) (C#)](./how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)  
 Ukazuje, jak v adresářovém stromu vracet největší nebo nejmenší soubor nebo určený počet souborů.  
  
 [Postupy: Dotaz na duplicitní soubory v adresářovém stromu (LINQ) (C#)](./how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)  
 Ukazuje, jak seskupit všechny názvy souborů, které se vyskytují ve více než jednom umístění v zadaném stromu adresářů. Také ukazuje, jak provádět složitější porovnání na základě vlastní porovnávací metody.  
  
 [Postupy: Dotazování na obsah souborů ve složce (LINQ) (C#)](./how-to-query-the-contents-of-files-in-a-folder-lin.md)  
 Ukazuje, jak iterovat složky ve stromu, otevřít jednotlivé soubory a zadat dotaz na obsah souboru.  
  
## <a name="comments"></a>Komentáře  
 Při vytváření zdroje dat, který přesně představuje obsah systému souborů, je potřeba složitá složitost a dochází k bezproblémovému zpracování výjimek. Příklady v této části vytvoří snímek kolekce <xref:System.IO.FileInfo> objektů, které představují všechny soubory v zadané kořenové složce a všech jejích podsložkách. Skutečný stav každé z nich <xref:System.IO.FileInfo> se může v době mezi začátkem a ukončením dotazu změnit. Můžete například vytvořit seznam <xref:System.IO.FileInfo> objektů, které chcete použít jako zdroj dat. Pokud se pokusíte o přístup `Length` k vlastnosti v dotazu <xref:System.IO.FileInfo> , objekt se pokusí o přístup k systému souborů `Length`za účelem aktualizace hodnoty. Pokud soubor už neexistuje, <xref:System.IO.FileNotFoundException> zobrazí se v dotazu, i když neprovádíte dotazování systému souborů přímo. Některé dotazy v této části používají samostatnou metodu, která v určitých případech spotřebovává tyto konkrétní výjimky. Další možností je udržovat dynamicky aktualizovaný zdroj dat pomocí <xref:System.IO.FileSystemWatcher>.  
  
## <a name="see-also"></a>Viz také:

- [LINQ to Objects (C#)](./linq-to-objects.md)
