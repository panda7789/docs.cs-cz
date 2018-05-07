---
title: ImageList – přehled komponenty (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ImageList
helpviewer_keywords:
- collection controls [Windows Forms], images
- icon list control
- ImageList component [Windows Forms], about ImageList component
ms.assetid: 7e25d89b-5633-40c1-afc3-82e0e301ffa2
ms.openlocfilehash: bda9bb71dd2e9b6da2de2444013ed724979f61af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="imagelist-component-overview-windows-forms"></a>ImageList – přehled komponenty (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ImageList> komponenta se používá k ukládání Image, které pak lze zobrazit pomocí ovládacích prvků. Seznam obrázků můžete napsat kód pro jeden a konzistentní katalog bitové kopie. Například můžete otáčení obrázků, na které se zobrazí <xref:System.Windows.Forms.Button> řízení jednoduše tak, že změna na tlačítko <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> nebo <xref:System.Windows.Forms.ButtonBase.ImageKey%2A> vlastnost. Stejný seznam bitové kopie můžete taky přidružit více ovládacích prvků. Například, pokud používáte obě <xref:System.Windows.Forms.ListView> řízení a <xref:System.Windows.Forms.TreeView> ovládací prvek zobrazí stejný seznam souborů, změna na ikonu v seznamu obrázků, které způsobí, že na ikonu Nový se zobrazí v obou zobrazeních.  
  
## <a name="using-imagelist-with-controls"></a>Použití seznamu obrázků s ovládacími prvky  
 Můžete použít seznamu obrázků s libovolný ovládací prvek, který má `ImageList` vlastnost – nebo u <xref:System.Windows.Forms.ListView> řízení, <xref:System.Windows.Forms.ListView.SmallImageList%2A> a <xref:System.Windows.Forms.ListView.LargeImageList%2A> vlastnosti. Ovládací prvky, které může být spojeno s seznamu obrázků zahrnují: <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ToolBar>, <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.RadioButton>, a <xref:System.Windows.Forms.Label> ovládací prvky. Chcete-li přidružit seznamu obrázků s ovládacím prvkem, nastavte ovládacího prvku `ImageList` vlastnost na název <xref:System.Windows.Forms.ImageList> součásti.  
  
## <a name="key-properties"></a>Klíčové vlastnosti  
 Klíčové vlastnosti <xref:System.Windows.Forms.ImageList> součást <xref:System.Windows.Forms.ImageList.Images%2A>, obsahující obrázky, které má být používána přidruženého ovládacího prvku. Každé jednotlivé bitové kopie můžete přistupovat pomocí jeho hodnotu indexu nebo na základě klíče. <xref:System.Windows.Forms.ImageList.ColorDepth%2A> Vlastnost určuje počet barev, které se vykreslují bitové kopie. Bitové kopie budou zobrazeny všechny na stejnou velikost, nastaven <xref:System.Windows.Forms.ImageList.ImageSize%2A> vlastnost. Bitové kopie, které jsou větší se přizpůsobí.  
  
 Pokud používáte [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], máte přístup k rozsáhlé knihovně standardní bitové kopie, které můžete použít ve svých aplikacích.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ImageList>  
 [Postupy: Přidání a odebrání obrázků pomocí komponenty Windows Forms ImageList](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
