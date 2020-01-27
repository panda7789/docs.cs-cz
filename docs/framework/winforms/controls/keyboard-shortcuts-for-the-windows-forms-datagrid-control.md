---
title: Klávesové zkratky pro ovládací prvek DataGrid
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard shortcuts [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], navigation keys
ms.assetid: a01780f9-20d5-4f5f-808f-c790c9a007a5
ms.openlocfilehash: 6693531b8d0e820a68d75bf5da40f4169fd244f2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745035"
---
# <a name="keyboard-shortcuts-for-the-windows-forms-datagrid-control"></a>Klávesové zkratky pro ovládací prvek Windows Forms DataGrid
> [!NOTE]
> Ovládací prvek <xref:System.Windows.Forms.DataGridView> nahrazuje a přidává funkce do ovládacího prvku <xref:System.Windows.Forms.DataGrid>; Nicméně ovládací prvek <xref:System.Windows.Forms.DataGrid> se zachovává pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 V následující tabulce jsou uvedeny klávesové zkratky, které lze použít pro navigaci v rámci ovládacího prvku model Windows Forms <xref:System.Windows.Forms.DataGrid>:  
  
|Akce|Zástupce|  
|------------|--------------|  
|Dokončete zadání buňky a přejděte dolů na další buňku.<br /><br /> Pokud se fokus zaměřuje na odkaz na podřízenou tabulku, přejděte k této tabulce.|NAPIŠTE|  
|Zruší úpravu buňky, pokud je v režimu úprav buňky.<br /><br /> Pokud je výběr v rámečku, zrušte úpravy na řádku.|ESC|  
|Odstraní znak před kurzorem při úpravě buňky.|BACKSPACE|  
|Odstraní znak za vloženým bodem při úpravě buňky.|DELETE|  
|Přesune se na první buňku aktuálního řádku.|DOMOVSKÁ STRÁNKA|  
|Přesune se do poslední buňky na aktuálním řádku.|END|  
|Zvýrazněte znaky v aktuální buňce a umístěte kurzor na konec řádku. Stejné chování jako při dvojitém kliknutí na buňku.|F2|  
|Pokud je fokus na buňce, přejděte na další buňku na řádku.<br /><br /> Pokud je fokus na poslední buňce v řádku, přejděte na odkaz první podřízené tabulky řádku a rozbalte ho.<br /><br /> Pokud je fokus na podřízeném odkazu, přejděte na další podřízený odkaz.<br /><br /> Pokud se fokus zaměřuje na poslední podřízený odkaz, přejdete na první buňku dalšího řádku.|TAB|  
|Pokud je fokus na buňce, přejděte na předchozí buňku na řádku.<br /><br /> Pokud je fokus v první buňce řádku, přejděte na poslední rozbalenou podřízenou tabulku předchozího řádku nebo přejděte na poslední buňku předchozího řádku.<br /><br /> Pokud je fokus na podřízeném odkazu, přejděte na předchozí podřízený odkaz.<br /><br /> Pokud se fokus zaměřuje na první podřízený odkaz, přejdete na poslední buňku předchozího řádku.|SHIFT+TAB|  
|Přesune se na další ovládací prvek v pořadí prvků.|CTRL+TAB|  
|Přesune se na předchozí ovládací prvek v pořadí prvků.|CTRL+SHIFT+TAB|  
|Pokud je v podřízené tabulce, přesuňte se k nadřazené tabulce. Stejné chování jako při kliknutí na tlačítko zpět.|ALT + ŠIPKA VLEVO|  
|Rozbalte odkaz na podřízenou tabulku. Kombinace kláves ALT + Šipka dolů rozbalí všechny odkazy, nikoli pouze ty, které jsou vybrány.|ALT + Šipka dolů nebo CTRL + PLUS – ZNAMÉNKo|  
|Sbalení odkazů na podřízenou tabulku. ALT + šipka nahoru sbalí všechny odkazy, nikoli jenom ty, které jsou vybrané.|ALT + šipka nahoru nebo CTRL + mínus – symbol|  
|Přesune se na nejvzdálenější neprázdnou buňku ve směru šipky.|CTRL + ŠIPKA|  
|Rozšíří výběr jednoho řádku ve směru šipky (Kromě odkazů na podřízené tabulky).|SHIFT + ŠIPKA NAHORU/DOLŮ|  
|Rozšíří výběr na nejvzdálenější neprázdný řádek ve směru šipky (Kromě odkazů na podřízené tabulky).|CTRL + SHIFT + ŠIPKA NAHORU/DOLŮ|  
|Přesune se do levé horní buňky.|CTRL + HOME|  
|Přejděte do pravé dolní buňky.|CTRL + END|  
|Rozšiřuje výběr na horní řádek.|CTRL + SHIFT + HOME|  
|Rozšiřuje výběr na spodní řádek.|CTRL + SHIFT + END|  
|Vyberte aktuální řádek (Kromě odkazů na podřízenou tabulku).|SHIFT + MEZERNÍK|  
|Vyberte celou mřížku (Kromě odkazů na podřízenou tabulku).|CTRL + A|  
|Zobrazí nadřazený řádek, pokud je v podřízené tabulce.|CTRL + PAGEDOWN|  
|Skryje nadřazený řádek, pokud je v podřízené tabulce.|CTRL + PAGE UP|  
|Rozšíří výběr o jednu obrazovku dolů (Kromě odkazů na podřízenou tabulku).|SHIFT + PAGEDOWN|  
|Rozšíří výběr o jednu obrazovku nahoru (Kromě odkazů na podřízenou tabulku).|SHIFT + PAGE UP|  
|Pro aktuální řádek volejte metodu <xref:System.Windows.Forms.DataGrid.EndEdit%2A>.|CTRL + ENTER|  
|Zadejte hodnotu <xref:System.DBNull.Value?displayProperty=nameWithType> v buňce v režimu úprav.|CTRL + 0|  
  
## <a name="see-also"></a>Viz také:

- [Přehled ovládacího prvku DataGrid](datagrid-control-overview-windows-forms.md)
- [Ovládací prvek DataGrid](datagrid-control-windows-forms.md)
