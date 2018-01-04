---
title: "Klávesové zkratky pro ovládací prvek Windows Forms DataGrid"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- keyboard shortcuts [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], navigation keys
ms.assetid: a01780f9-20d5-4f5f-808f-c790c9a007a5
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3e80281f3a89737f060804aa5237705386232763
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="keyboard-shortcuts-for-the-windows-forms-datagrid-control"></a>Klávesové zkratky pro ovládací prvek Windows Forms DataGrid
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Řízení nahrazuje a přidá funkce <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> řízení se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte. Další informace najdete v tématu [rozdíly mezi systému Windows Forms DataGridView a DataGrid – ovládací prvky](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Následující tabulka uvádí klávesové zkratky, které lze použít pro navigaci v rámci modelu Windows Forms <xref:System.Windows.Forms.DataGrid> ovládacího prvku:  
  
|Akce|Zástupce|  
|------------|--------------|  
|Dokončete položka buňky a přesunout dolů na další buňku.<br /><br /> Pokud je fokus na odkaz podřízenou tabulku, přejděte na tuto tabulku.|ZADEJTE|  
|Zrušení úprav buňky Pokud v režimu úprav buňky.<br /><br /> Pokud v hranici výběru zrušení úprav na řádek.|ESC|  
|Při úpravě buňku, odstraňte znak před ním.|BACKSPACE|  
|Odstraňte znak za kurzorem při úpravě buňku.|DELETE|  
|Přesuňte do první buňky na aktuálním řádku.|DOMOVSKÉ|  
|Přesuňte poslední buňku na aktuálním řádku.|END|  
|Zvýrazněte znaků v aktuální buňky a umístěte kurzor na konec řádku. Stejné chování jako dvakrát klikněte na buňku.|F2|  
|Pokud je fokus na buňku, přejděte na další buňky v řádku.<br /><br /> Pokud je fokus na poslední buňky v řádku, přesunout do první tabulky odkazů podřízené řádku a rozbalte ho.<br /><br /> Pokud je fokus na podřízené odkaz, přejděte na odkaz na další podřízené.<br /><br /> Pokud je fokus na odkaz poslední podřízené, přejděte na první buňky na další řádek.|KARTA|  
|Pokud je fokus na buňku, přejděte na předchozí buňky v řádku.<br /><br /> Pokud je fokus na první buňky v řádku, přesunout do poslední rozšířené podřízené tabulky odkaz na předchozí řádek nebo přechod na poslední buňky v předchozím řádku.<br /><br /> Pokud je fokus na podřízené odkaz, přejděte na předchozí odkaz podřízené.<br /><br /> Pokud je fokus na první odkaz podřízené, přechod na poslední buňky na předchozí řádek.|SHIFT + TAB|  
|Přesun na další ovládací prvek v pořadí.|CTRL + TAB|  
|Přesun na předchozí ovládací prvek v pořadí.|CTRL + SHIFT + TAB|  
|Přesunout nahoru v nadřazené tabulce Pokud v podřízené tabulce Stejné chování jako při kliknutí na tlačítko Zpět.|ALT + ŠIPKA DOLEVA|  
|Rozbalte podřízené tabulky odkazů. ALT + Šipka dolů rozšíří všechny odkazy, ne jenom ty, které vybraná.|ALT + Šipka dolů nebo CTRL + Plus|  
|Sbalit podřízené tabulky odkazů. ALT + Šipka nahoru sbalí všechny odkazy, ne jenom ty, které vybraná.|ALT + Šipka nahoru nebo CTRL + minus|  
|Přesuňte nejvíce neprázdné buňce ve směru na šipku.|CTRL + ŠIPKA|  
|Rozšíření výběru jeden řádek ve směru šipku (s výjimkou podřízených odkazy tabulky).|ŠIPKA SHIFT + ŠIPKA NAHORU NEBO DOLŮ|  
|Rozšíření výběru na nejvíce neprázdných řádků ve směru šipku (s výjimkou podřízených odkazy tabulky).|CTRL + SHIFT + NAHORU/ŠIPKA DOLŮ|  
|Přejít na levém buňku.|CTRL + HOME|  
|Přesuňte pravém dolním rohu buňky.|CTRL + END|  
|Rozšíření výběru na začátek řádku.|CTRL + SHIFT + HOME|  
|Rozšíření výběru na dolním řádku.|CTRL + SHIFT + END|  
|Vyberte aktuální řádek (s výjimkou podřízených odkazy tabulky).|SHIFT + MEZERNÍK|  
|Vyberte celou mřížky (s výjimkou podřízených odkazy tabulky).|CTRL + A|  
|Zobrazení nadřazené řádek v podřízené tabulce.|CTRL + PAGE DOWN|  
|Skryjte nadřazené řádek v podřízené tabulce.|CTRL + PAGEUP|  
|Rozšíření výběru dolů o jednu obrazovku (bez podřízených odkazy tabulky).|SHIFT + PAGE DOWN|  
|Rozšíření výběru nahoru jednu obrazovku (bez podřízených odkazy tabulky).|SHIFT + PAGEUP|  
|Volání <xref:System.Windows.Forms.DataGrid.EndEdit%2A> metody pro aktuální řádek.|CTRL + ENTER|  
|Zadejte <xref:System.DBNull.Value?displayProperty=nameWithType> hodnotu do buňky v režimu úprav.|CTRL + 0|  
  
## <a name="see-also"></a>Viz také  
 [Přehled ovládacího prvku DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [Ovládací prvek DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
