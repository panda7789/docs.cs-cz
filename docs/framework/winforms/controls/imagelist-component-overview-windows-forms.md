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
ms.openlocfilehash: 1ce9ced0c7e6bc13d5cdf331135590ba48c624fb
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48844914"
---
# <a name="imagelist-component-overview-windows-forms"></a>ImageList – přehled komponenty (Windows Forms)

Windows Forms <xref:System.Windows.Forms.ImageList> komponenty se používá k ukládání imagí, které lze zobrazit ovládací prvky. Seznam obrázků umožňuje napsat kód pro jediné, jednotné katalog imagí. Například můžete otáčení obrázků zobrazeného ve <xref:System.Windows.Forms.Button> ovládacího prvku na tlačítko Změnit <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> nebo <xref:System.Windows.Forms.ButtonBase.ImageKey%2A> vlastnost. Stejný seznam obrázků můžete taky přidružit více ovládacích prvků. Například, pokud používáte obě <xref:System.Windows.Forms.ListView> ovládacího prvku a <xref:System.Windows.Forms.TreeView> způsobí, že ovládací prvek pro zobrazení seznamu souborů, změna souboru ikony v seznamu obrázků na novou ikonu se zobrazí v obou zobrazeních.

## <a name="using-imagelist-with-controls"></a>Pomocí seznamu obrázků s ovládacími prvky

Seznam obrázků můžete použít u každého ovládacího prvku, který má `ImageList` vlastnost – nebo v případě třídy <xref:System.Windows.Forms.ListView> ovládacího prvku, <xref:System.Windows.Forms.ListView.SmallImageList%2A> a <xref:System.Windows.Forms.ListView.LargeImageList%2A> vlastnosti. Ovládací prvky, které mohou být spojeny s seznamu obrázků zahrnují: <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ToolBar>, <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.RadioButton>, a <xref:System.Windows.Forms.Label> ovládací prvky. Přidružení seznamu obrázků s ovládacím prvkem, nastavit u tohoto prvku `ImageList` vlastnost na název <xref:System.Windows.Forms.ImageList> komponenty.

## <a name="key-properties"></a>Vlastnosti klíče

Klíčové vlastnosti <xref:System.Windows.Forms.ImageList> komponenta je <xref:System.Windows.Forms.ImageList.Images%2A>, který obsahuje obrázky používané přidružený ovládací prvek. Každé jednotlivé image je možný podle jeho hodnoty indexu nebo podle jeho klíče. <xref:System.Windows.Forms.ImageList.ColorDepth%2A> Vlastnost určuje počet barev, které se vykreslují bitové kopie. Bitové kopie budou zobrazeny všechny na stejnou velikost, nastavením <xref:System.Windows.Forms.ImageList.ImageSize%2A> vlastnost. Bitové kopie, které jsou větší se přizpůsobí.

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.ImageList>
- [Postupy: Přidání a odebrání obrázků pomocí komponenty Windows Forms ImageList](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)