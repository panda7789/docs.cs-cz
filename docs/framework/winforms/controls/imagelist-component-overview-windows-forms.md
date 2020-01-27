---
title: Přehled komponenty ImageList
ms.date: 03/30/2017
f1_keywords:
- ImageList
helpviewer_keywords:
- collection controls [Windows Forms], images
- icon list control
- ImageList component [Windows Forms], about ImageList component
ms.assetid: 7e25d89b-5633-40c1-afc3-82e0e301ffa2
ms.openlocfilehash: b46204375cb046d637f4c9e1d888f37d10ea1f57
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728099"
---
# <a name="imagelist-component-overview-windows-forms"></a>ImageList – přehled komponenty (Windows Forms)

Komponenta model Windows Forms <xref:System.Windows.Forms.ImageList> se používá k ukládání obrázků, které mohou být zobrazeny ovládacími prvky. Seznam obrázků umožňuje napsat kód pro jeden konzistentní katalog imagí. Například můžete otáčet obrázky zobrazené ovládacím prvkem <xref:System.Windows.Forms.Button> jednoduše tak, že změníte vlastnost <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> nebo <xref:System.Windows.Forms.ButtonBase.ImageKey%2A>. Můžete také přidružit stejný seznam obrázků k více ovládacím prvkům. Například pokud používáte ovládací prvek <xref:System.Windows.Forms.ListView> a ovládací prvek <xref:System.Windows.Forms.TreeView> k zobrazení stejného seznamu souborů, změna ikony souboru v seznamu obrázků způsobí, že se nová ikona zobrazí v obou zobrazeních.

## <a name="using-imagelist-with-controls"></a>Použití seznamu ImageList s ovládacími prvky

Seznam obrázků můžete použít s libovolným ovládacím prvkem, který má vlastnost `ImageList` – nebo v případě ovládacího prvku <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.ListView.SmallImageList%2A> a <xref:System.Windows.Forms.ListView.LargeImageList%2A> vlastností. Mezi ovládací prvky, které se dají přidružit k seznamu obrázků, patří: <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ToolBar>, <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.RadioButton>a <xref:System.Windows.Forms.Label>. Chcete-li přidružit seznam obrázků k ovládacímu prvku, nastavte vlastnost `ImageList` ovládacího prvku na název <xref:System.Windows.Forms.ImageList> součásti.

## <a name="key-properties"></a>Klíčové vlastnosti

Klíčovou vlastností součásti <xref:System.Windows.Forms.ImageList> je <xref:System.Windows.Forms.ImageList.Images%2A>, která obsahuje obrázky používané přidruženým ovládacím prvkem. Ke každému jednotlivému obrázku může být přistupovaná jeho hodnota indexu nebo jeho klíčem. Vlastnost <xref:System.Windows.Forms.ImageList.ColorDepth%2A> určuje počet barev, pomocí kterých jsou obrázky vykresleny. Obrázek se zobrazí ve stejné velikosti, kterou nastaví vlastnost <xref:System.Windows.Forms.ImageList.ImageSize%2A>. Obrázky, které jsou větší, se škálují tak, aby se vešly.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ImageList>
- [Postupy: Přidání a odebrání obrázků pomocí komponenty Windows Forms ImageList](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
