---
title: 'Postupy: Vytvoření více podokny uživatelského rozhraní pomocí Windows Forms pomocí návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- user interface [Windows Forms], multipane
- SplitContainer control [Windows Forms], using the designer
- multipane user interface
ms.assetid: c3f9294d-a26c-4198-9242-f237f55f7573
ms.openlocfilehash: 1ad446fde4ccfc9ad9c48e619321deed044f1014
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713771"
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms-using-the-designer"></a>Postupy: Vytvoření více podokny uživatelského rozhraní pomocí Windows Forms pomocí návrháře
V následujícím postupu vytvoříte, který je podobný tomu použitému v aplikaci Microsoft Outlook s více podokny uživatelské rozhraní **složky** seznamu, **zprávy** podokně a **veverziPreview** podokně. Toto uspořádání se dosahuje hlavně prostřednictvím Ukotvování ovládacích prvků ve formuláři.  
  
 Můžete ukotvit ovládacího prvku, zjistíte, které okrajem nadřazeného kontejneru ovládacího prvku je připojen k. Proto pokud nastavíte <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Right>, pravým okrajem ovládacího prvku se ukotven k pravým okrajem jeho nadřazeného ovládacího prvku. Kromě toho ukotvených okrajem ovládacího prvku svou velikost tak, aby odpovídaly u ovládacího prvku kontejneru. Další informace o tom, jak <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnost funguje, najdete v článku [jak: Ukotvování ovládacích prvků ve Windows Forms](how-to-dock-controls-on-windows-forms.md).  
  
 Tento postup se zaměřuje na uspořádání <xref:System.Windows.Forms.SplitContainer> a další ovládací prvky ve formuláři, nikoli na přidání funkce do aplikace, které napodobují aplikace Microsoft Outlook.  
  
 K vytvoření tohoto uživatelského rozhraní, umístěte všechny ovládací prvky v rámci <xref:System.Windows.Forms.SplitContainer> ovládací prvek, který obsahuje <xref:System.Windows.Forms.TreeView> ovládacího prvku na panelu vlevo. Na pravém panelu <xref:System.Windows.Forms.SplitContainer> ovládací prvek obsahuje druhý <xref:System.Windows.Forms.SplitContainer> ovládacím prvkem <xref:System.Windows.Forms.ListView> ovládací prvek výše <xref:System.Windows.Forms.RichTextBox> ovládacího prvku. Tyto <xref:System.Windows.Forms.SplitContainer> ovládací prvky umožňují nezávislé Změna velikosti jiných ovládacích prvků ve formuláři. Můžete upravit postupy v tomto postupu vytváření vlastního uživatelského rozhraní vlastní.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-an-outlook-style-user-interface-at-design-time"></a>Chcete-li vytvořit uživatelské rozhraní Outlooku – vizuální styl v době návrhu  
  
1.  Vytvoření nového projektu aplikace Windows (**souboru** > **nový** > **projektu** > **Visual C#** nebo **jazyka Visual Basic** > **klasický desktopový** > **aplikaci Windows Forms**).  
  
2.  Přetáhněte <xref:System.Windows.Forms.SplitContainer> ovládacího prvku **nástrojů** do formuláře. V **vlastnosti** okno, nastaveno <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.  
  
3.  Přetáhněte <xref:System.Windows.Forms.TreeView> ovládacího prvku **nástrojů** na panelu vlevo <xref:System.Windows.Forms.SplitContainer> ovládacího prvku. V **vlastnosti** okno, nastaveno <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Left> kliknutím na levém panelu v editoru hodnoty zobrazí po kliknutí na šipku dolů.  
  
4.  Přetáhněte další <xref:System.Windows.Forms.SplitContainer> ovládacího prvku **nástrojů**; umístěte ho na pravém panelu <xref:System.Windows.Forms.SplitContainer> jste přidali do svého formuláře ovládací prvek. V **vlastnosti** okno, nastaveno <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill> a <xref:System.Windows.Forms.SplitContainer.Orientation%2A> vlastnost <xref:System.Windows.Forms.Orientation.Horizontal>.  
  
5.  Přetáhněte <xref:System.Windows.Forms.ListView> ovládacího prvku **nástrojů** na horním panelu druhého <xref:System.Windows.Forms.SplitContainer> jste přidali do svého formuláře ovládací prvek. Nastavte <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnost <xref:System.Windows.Forms.ListView> mít pod kontrolou <xref:System.Windows.Forms.DockStyle.Fill>.  
  
6.  Přetáhněte <xref:System.Windows.Forms.RichTextBox> řízení z **nástrojů** dolní panel druhého <xref:System.Windows.Forms.SplitContainer> ovládacího prvku. Nastavte <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnost <xref:System.Windows.Forms.RichTextBox> mít pod kontrolou <xref:System.Windows.Forms.DockStyle.Fill>.  
  
     V tomto okamžiku můžete stisknutím klávesy F5 spusťte aplikaci, formulář se zobrazí na třemi částmi uživatelského rozhraní, podobně jako u aplikace Microsoft Outlook.  
  
    > [!NOTE]
    >  Když umístíte ukazatel myši přes buď příčky v rámci <xref:System.Windows.Forms.SplitContainer> ovládací prvky, můžete změnit velikost vnitřní dimenze.  
  
     Při vývoji aplikace se v tuto chvíli máte vytvořený propracovaná uživatelská rozhraní. Dalším krokem je pokračováním programování aplikací, například připojením <xref:System.Windows.Forms.TreeView> ovládacího prvku a <xref:System.Windows.Forms.ListView> ovládacích prvků pro nějaký druh zdroje dat. Další informace o připojování ovládacích prvků k datům najdete v tématu [datové vazby a Windows Forms](../data-binding-and-windows-forms.md).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.SplitContainer>
- [Ovládací prvek SplitContainer](splitcontainer-control-windows-forms.md)
