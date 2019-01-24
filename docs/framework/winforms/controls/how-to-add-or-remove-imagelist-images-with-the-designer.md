---
title: 'Postupy: Přidávání a odebírání obrázků ImageList pomocí návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
ms.openlocfilehash: f03ad1735d7da450d6ebc10c227e3f2bbb41a3d8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688139"
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a>Postupy: Přidávání a odebírání obrázků ImageList pomocí návrháře
Můžete přidat Image do <xref:System.Windows.Forms.ImageList> součástí několika různými způsoby. Lze také přidat obrázky velmi rychle s využitím inteligentních značek přidružené <xref:System.Windows.Forms.ImageList>, nebo pokud nastavujete na několik dalších vlastností <xref:System.Windows.Forms.ImageList>, pravděpodobně pro vás bude pohodlnější přidání imagí pomocí okna Vlastnosti. Můžete také přidat obrázky pomocí kódu. Další informace o tom, jak přidat obrázky s kódem, najdete v části [jak: Přidání a odebrání obrázků se Windows Forms ImageList – komponenta](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md). Obvykle naplnit <xref:System.Windows.Forms.ImageList> komponentu s obrázky předtím, než je přidružena k ovládacímu prvku, ale tento krok není povinný.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-or-remove-images-by-using-the-properties-window"></a>K přidávání a odebírání obrázků pomocí okna Vlastnosti  
  
1.  Vyberte <xref:System.Windows.Forms.ImageList> komponenty, nebo přidejte jej do formuláře.  
  
2.  V okně Vlastnosti klikněte na tlačítko se třemi tečkami (![snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) vedle položky <xref:System.Windows.Forms.ImageList.Images%2A> vlastnost.  
  
3.  V **Editor kolekce obrázků**, klikněte na tlačítko **přidat** nebo **odebrat** k přidávání a odebírání obrázků ze seznamu.  
  
### <a name="to-add-or-remove-images-using-the-smart-tag"></a>Přidání nebo odebrání obrázků s využitím inteligentních značek  
  
1.  Vyberte <xref:System.Windows.Forms.ImageList> komponenty, nebo přidejte jej do formuláře.  
  
2.  Klikněte na inteligentní označit piktogram (![piktogram inteligentní](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))  
  
3.  V **ImageList úlohy** dialogu **zvolte image**.  
  
4.  V **Editor kolekce Images** klikněte na tlačítko **přidat** nebo **odebrat** k přidávání a odebírání obrázků ze seznamu.  
  
## <a name="see-also"></a>Viz také:
- [Obrázky, rastrové obrázky a metasoubory](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
- [Návod: Provádění obecných úloh pomocí inteligentních značek na Windows Forms ovládací prvky](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md)
- [Komponenta ImageList](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
