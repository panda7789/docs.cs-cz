---
title: 'Postupy: Přidávání a odebírání obrázků ImageList pomocí návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
ms.openlocfilehash: 370bd05ac014b625d9581cc285daf6724f459b73
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723742"
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a>Postupy: Přidávání a odebírání obrázků ImageList pomocí návrháře
Můžete přidat Image do <xref:System.Windows.Forms.ImageList> součástí několika různými způsoby. Lze také přidat obrázky velmi rychle s využitím inteligentních značek přidružené <xref:System.Windows.Forms.ImageList>, nebo pokud nastavujete na několik dalších vlastností <xref:System.Windows.Forms.ImageList>, pravděpodobně pro vás bude pohodlnější přidání imagí pomocí okna Vlastnosti. Můžete také přidat obrázky pomocí kódu. Další informace o tom, jak přidat obrázky s kódem, najdete v části [jak: Přidání a odebrání obrázků se Windows Forms ImageList – komponenta](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md). Obvykle naplnit <xref:System.Windows.Forms.ImageList> komponentu s obrázky předtím, než je přidružena k ovládacímu prvku, ale tento krok není povinný.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-or-remove-images-by-using-the-properties-window"></a>K přidávání a odebírání obrázků pomocí okna Vlastnosti  
  
1.  Vyberte <xref:System.Windows.Forms.ImageList> komponenty, nebo přidejte jej do formuláře.  
  
2.  V okně Vlastnosti klikněte na tlačítko se třemi tečkami (![snímek obrazovky VisualStudioEllipsesButton](../media/vbellipsesbutton.png "vbEllipsesButton")) vedle položky <xref:System.Windows.Forms.ImageList.Images%2A> vlastnost.  
  
3.  V **Editor kolekce obrázků**, klikněte na tlačítko **přidat** nebo **odebrat** k přidávání a odebírání obrázků ze seznamu.  
  
### <a name="to-add-or-remove-images-using-the-smart-tag"></a>Přidání nebo odebrání obrázků s využitím inteligentních značek  
  
1.  Vyberte <xref:System.Windows.Forms.ImageList> komponenty, nebo přidejte jej do formuláře.  
  
2.  Klikněte na inteligentní označit piktogram (![piktogram inteligentní](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))  
  
3.  V **ImageList úlohy** dialogu **zvolte image**.  
  
4.  V **Editor kolekce Images** klikněte na tlačítko **přidat** nebo **odebrat** k přidávání a odebírání obrázků ze seznamu.  
  
## <a name="see-also"></a>Viz také:
- [Obrázky, rastrové obrázky a metasoubory](../advanced/images-bitmaps-and-metafiles.md)
- [Návod: Provádění obecných úloh pomocí inteligentních značek na Windows Forms ovládací prvky](performing-common-tasks-using-smart-tags-on-wf-controls.md)
- [Komponenta ImageList](imagelist-component-windows-forms.md)
