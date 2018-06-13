---
title: 'Postupy: Přidávání a odebírání obrázků ImageList pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
ms.openlocfilehash: c85e55b6aef45eea65e6f82269375f80acf71017
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527671"
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a>Postupy: Přidávání a odebírání obrázků ImageList pomocí Návrháře
Můžete přidat Image do <xref:System.Windows.Forms.ImageList> součástí několika různými způsoby. Bitové kopie můžete přidat velmi rychle pomocí inteligentních značek přidružené <xref:System.Windows.Forms.ImageList>, nebo pokud nastavujete na několik dalších vlastností <xref:System.Windows.Forms.ImageList>, možná bude jednodušší přidat bitové kopie v okně Vlastnosti. Můžete také přidat bitové kopie pomocí kódu. Další informace o tom, jak přidat bitové kopie s kódem najdete v tématu [postupy: Přidání nebo odebrání obrázků s komponentou Windows Forms ImageList](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md). Obvykle naplnit <xref:System.Windows.Forms.ImageList> součásti s obrázky, než je přidružena k ovládacímu prvku, ale není to povinné.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-or-remove-images-by-using-the-properties-window"></a>Přidat nebo odebrat pomocí okna Vlastnosti bitové kopie  
  
1.  Vyberte <xref:System.Windows.Forms.ImageList> součást, nebo přidat do formuláře.  
  
2.  V okně vlastností klikněte na tlačítko se třemi tečkami (![– snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) vedle položky <xref:System.Windows.Forms.ImageList.Images%2A> vlastnost.  
  
3.  V **Editor kolekce obrázků**, klikněte na tlačítko **přidat** nebo **odebrat** přidat nebo odebrat ze seznamu obrázků.  
  
### <a name="to-add-or-remove-images-using-the-smart-tag"></a>Přidat nebo odebrat obrázky pomocí inteligentních značek  
  
1.  Vyberte <xref:System.Windows.Forms.ImageList> součást, nebo přidat do formuláře.  
  
2.  Klikněte na inteligentní značky glyfy (![inteligentní značky glyfy](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))  
  
3.  V **ImageList úlohy** dialogové okno, vyberte **zvolte image**.  
  
4.  V **Editor kolekce obrázků** klikněte na tlačítko **přidat** nebo **odebrat** přidat nebo odebrat ze seznamu obrázků.  
  
## <a name="see-also"></a>Viz také  
 [Obrázky, rastrové obrázky a metasoubory](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Návod: Provádění obecných úloh pomocí inteligentních značek v ovládacích prvcích Windows Forms](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md)  
 [Komponenta ImageList](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
