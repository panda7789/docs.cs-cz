---
title: 'Postupy: Vytváření uživatelského rozhraní s více podokny s Windows Forms pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- user interface [Windows Forms], multipane
- SplitContainer control [Windows Forms], using the designer
- multipane user interface
ms.assetid: c3f9294d-a26c-4198-9242-f237f55f7573
ms.openlocfilehash: 97888a77dfc731be591d5f0284e87f45ef7dc437
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930170"
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms-using-the-designer"></a>Postupy: Vytváření uživatelského rozhraní s více podokny s Windows Forms pomocí Návrháře
V následujícím postupu vytvoříte uživatelské rozhraní s více podokny, které je podobné jako v aplikaci Microsoft Outlook, seznam **složek** , podokno **zprávy** a podokno **náhledu** . Toto uspořádání se dosahuje hlavně prostřednictvím ovládacích prvků docking s formulářem.

 Při ukotvení ovládacího prvku určíte, na který okraj nadřazeného kontejneru je ovládací prvek připevněný. Proto pokud nastavíte <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnost na <xref:System.Windows.Forms.DockStyle.Right>, pravý okraj ovládacího prvku bude ukotven k pravému okraji svého nadřazeného ovládacího prvku. Kromě toho je ukotvená hrana ovládacího prvku změněna tak, aby odpovídala jeho ovládacímu prvku kontejneru. Další informace o tom, jak <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnost funguje, naleznete [v tématu How to: Ukotvit ovládací prvky na](how-to-dock-controls-on-windows-forms.md)model Windows Forms.

 Tento postup se zaměřuje na uspořádání <xref:System.Windows.Forms.SplitContainer> a dalších ovládacích prvků ve formuláři, nikoli při přidávání funkcí, které aplikaci napodobují Microsoft Outlook.

 Chcete-li vytvořit toto uživatelské rozhraní, umístěte všechny ovládací prvky do <xref:System.Windows.Forms.SplitContainer> ovládacího prvku, který <xref:System.Windows.Forms.TreeView> obsahuje ovládací prvek na levém panelu. Panel <xref:System.Windows.Forms.SplitContainer> na pravé straně ovládacího prvku obsahuje druhý <xref:System.Windows.Forms.SplitContainer> ovládací prvek <xref:System.Windows.Forms.RichTextBox> s <xref:System.Windows.Forms.ListView> ovládacím prvkem nad rámec ovládacího prvku. Tyto <xref:System.Windows.Forms.SplitContainer> ovládací prvky umožňují nezávislé změny velikosti ostatních ovládacích prvků ve formuláři. Techniky v tomto postupu můžete přizpůsobit a vytvořit vlastní uživatelská rozhraní.

## <a name="to-create-an-outlook-style-user-interface-at-design-time"></a>Vytvoření uživatelského rozhraní ve stylu aplikace Outlook v době návrhu

1. Vytvoření nového projektu aplikace pro Windows (**soubor** > **nového** > **projektu** > **Visual C#**  nebo**klasický Desktop** **Visual Basic** >  >  **Model Windows Forms aplikace**).

2. Přetáhněte ovládací prvek z **panelu nástrojů** do formuláře. <xref:System.Windows.Forms.SplitContainer> V okně **vlastnosti** nastavte <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnost na <xref:System.Windows.Forms.DockStyle.Fill>hodnotu.

3. Přetáhněte ovládací prvek ze **sady nástrojů** na panel na levé <xref:System.Windows.Forms.SplitContainer> straně ovládacího prvku. <xref:System.Windows.Forms.TreeView> V okně **vlastnosti** nastavte <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnost na <xref:System.Windows.Forms.DockStyle.Left> hodnotu kliknutím na levý panel v editoru hodnot, který se zobrazí po kliknutí na šipku dolů.

4. Přetáhněte jiný <xref:System.Windows.Forms.SplitContainer> ovládací prvek ze **sady nástrojů**a umístěte jej do pravého panelu <xref:System.Windows.Forms.SplitContainer> ovládacího prvku, který jste přidali do formuláře. V okně **vlastnosti** nastavte <xref:System.Windows.Forms.SplitContainer.Dock%2A> <xref:System.Windows.Forms.DockStyle.Fill> vlastnostna<xref:System.Windows.Forms.Orientation.Horizontal>hodnotu a vlastnostnahodnotu.<xref:System.Windows.Forms.SplitContainer.Orientation%2A>

5. Přetáhněte ovládací prvek ze **sady nástrojů** na horní panel druhého <xref:System.Windows.Forms.SplitContainer> ovládacího prvku, který jste přidali do formuláře. <xref:System.Windows.Forms.ListView> <xref:System.Windows.Forms.SplitContainer.Dock%2A> Nastavte vlastnost <xref:System.Windows.Forms.ListView> ovládacího prvku na <xref:System.Windows.Forms.DockStyle.Fill>.

6. Přetáhněte ovládací prvek ze **sady nástrojů** na spodní panel druhého <xref:System.Windows.Forms.SplitContainer> ovládacího prvku. <xref:System.Windows.Forms.RichTextBox> <xref:System.Windows.Forms.SplitContainer.Dock%2A> Nastavte vlastnost <xref:System.Windows.Forms.RichTextBox> ovládacího prvku na <xref:System.Windows.Forms.DockStyle.Fill>.

     Když stisknete klávesu F5 ke spuštění aplikace, formulář zobrazí uživatelské rozhraní se třemi částmi, podobně jako v aplikaci Microsoft Outlook.

    > [!NOTE]
    > Když umístíte ukazatel myši na některé z rozdělovačů v <xref:System.Windows.Forms.SplitContainer> ovládacích prvcích, můžete změnit velikost vnitřních rozměrů.

V tomto okamžiku vývoje aplikací jste si vystavili sofistikované uživatelské rozhraní. Dalším krokem je pokračování v programování samotné aplikace, třeba propojením <xref:System.Windows.Forms.TreeView> ovládacího prvku a <xref:System.Windows.Forms.ListView> ovládacích prvků s nějakým druhem zdroje dat. Další informace o připojení ovládacích prvků k datům naleznete v tématu [datové vazby a model Windows Forms](../data-binding-and-windows-forms.md).

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.SplitContainer>
- [Ovládací prvek SplitContainer](splitcontainer-control-windows-forms.md)
