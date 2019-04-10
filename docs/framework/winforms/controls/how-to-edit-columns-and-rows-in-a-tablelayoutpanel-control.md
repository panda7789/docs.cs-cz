---
title: 'Postupy: Úpravy sloupců a řádků v ovládacím prvku TableLayoutPanel'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
ms.openlocfilehash: eb194052ecd78d585f251789730a1f9855c509d9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201959"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a>Postupy: Úpravy sloupců a řádků v ovládacím prvku TableLayoutPanel
Můžete použít editor kolekce <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku, volá se **styly sloupců a řádků** dialogovém okně Upravit řádky a sloupce ovládacích prvků.  
  
> [!NOTE]
>  Pokud chcete ovládací prvek na více řádcích nebo sloupcích, nastavte `RowSpan` a `ColumnSpan` vlastnosti na ovládacím prvku. Další informace najdete v tématu [názorný postup: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).  
>   
>  Pokud chcete ovládací prvek v rámci buňky zarovnat nebo pokud chcete roztáhnout v rámci buňky, pomocí ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost. Další informace najdete v tématu [názorný postup: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).  
>   
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-edit-rows-and-columns"></a>Chcete-li upravit řádky a sloupce  
  
1.  Přetáhněte <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku **nástrojů** do formuláře.  
  
2.  Klikněte na tlačítko <xref:System.Windows.Forms.TableLayoutPanel> piktogram inteligentní značky ovládacího prvku (![piktogram inteligentní](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) a vyberte **upravit řádky a sloupce** otevřít  **Styly sloupců a řádků** dialogové okno. Můžete také pravým tlačítkem myši kliknete na <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek a vyberte **upravit řádky a sloupce** z místní nabídky.  
  
3.  Chcete-li přidat nebo odebrat sloupce, vyberte **sloupce** z **typ člena** rozevíracího seznamu.  
  
4.  Chcete-li přidat nebo odebrat řádky, vyberte **řádky** z **typ člena** rozevíracího seznamu.  
  
5.  Klikněte na tlačítko **přidat** a přidejte na konec řádku nebo sloupce **člen** seznamu.  
  
6.  Klikněte na tlačítko **vložit** tlačítko pro přidání řádku nebo sloupce před aktuálně vybrané položky v seznamu.  
  
7.  Pokud přidáváte řádku nebo sloupce, vyberte **typ velikosti** pro nový řádek nebo sloupec. Další informace naleznete v tématu <xref:System.Windows.Forms.SizeType>.  
  
8.  K odebrání řádku nebo sloupce, klikněte na tlačítko **odebrat** tlačítko Odstranit aktuálně vybrané položky v **člen** seznamu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.SizeType>
- [Ovládací prvek TableLayoutPanel](tablelayoutpanel-control-windows-forms.md)
