---
title: Vytvoření uživatelského rozhraní s více podokny pomocí návrháře
ms.date: 03/30/2017
helpviewer_keywords:
- user interface [Windows Forms], multipane
- SplitContainer control [Windows Forms], using the designer
- multipane user interface
ms.assetid: c3f9294d-a26c-4198-9242-f237f55f7573
ms.openlocfilehash: 6b41d538f1cd1633cec51c89e27adf3c5b47f9a6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737274"
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms-using-the-designer"></a>Postupy: Vytváření uživatelského rozhraní s více podokny s formuláři Windows pomocí Návrháře
V následujícím postupu vytvoříte uživatelské rozhraní s více podokny, které je podobné jako v aplikaci Microsoft Outlook, seznam **složek** , podokno **zprávy** a podokno **náhledu** . Toto uspořádání se dosahuje hlavně prostřednictvím ovládacích prvků docking s formulářem.

 Při ukotvení ovládacího prvku určíte, na který okraj nadřazeného kontejneru je ovládací prvek připevněný. Proto pokud nastavíte vlastnost <xref:System.Windows.Forms.SplitContainer.Dock%2A> na <xref:System.Windows.Forms.DockStyle.Right>, pravý okraj ovládacího prvku bude ukotven k pravému okraji svého nadřazeného ovládacího prvku. Kromě toho je ukotvená hrana ovládacího prvku změněna tak, aby odpovídala jeho ovládacímu prvku kontejneru. Další informace o tom, jak vlastnost <xref:System.Windows.Forms.SplitContainer.Dock%2A> funguje, naleznete v tématu [How to: Dock Controls on model Windows Forms](how-to-dock-controls-on-windows-forms.md).

 Tento postup se zaměřuje na uspořádání <xref:System.Windows.Forms.SplitContainer> a dalších ovládacích prvků ve formuláři, nikoli při přidávání funkcí, které aplikaci napodobují aplikaci Microsoft Outlook.

 Chcete-li vytvořit toto uživatelské rozhraní, umístěte všechny ovládací prvky v rámci ovládacího prvku <xref:System.Windows.Forms.SplitContainer>, který obsahuje ovládací prvek <xref:System.Windows.Forms.TreeView> na levém panelu. Pravé podokno ovládacího prvku <xref:System.Windows.Forms.SplitContainer> obsahuje druhý ovládací prvek <xref:System.Windows.Forms.SplitContainer> s ovládacím prvkem <xref:System.Windows.Forms.ListView> nad <xref:System.Windows.Forms.RichTextBox> ovládací prvek. Tyto ovládací prvky <xref:System.Windows.Forms.SplitContainer> umožňují nezávislé změny velikosti ostatních ovládacích prvků ve formuláři. Techniky v tomto postupu můžete přizpůsobit a vytvořit vlastní uživatelská rozhraní.

## <a name="to-create-an-outlook-style-user-interface-at-design-time"></a>Vytvoření uživatelského rozhraní ve stylu aplikace Outlook v době návrhu

1. Vytvořte nový projekt aplikace pro Windows (**soubor** > **Nový** > **projektu** > **vizuálu C#**  nebo **Visual Basic** > **klasické desktopové** > **model Windows Forms aplikaci**).

2. Přetáhněte ovládací prvek <xref:System.Windows.Forms.SplitContainer> z **panelu nástrojů** do formuláře. V okně **vlastnosti** nastavte vlastnost <xref:System.Windows.Forms.SplitContainer.Dock%2A> na hodnotu <xref:System.Windows.Forms.DockStyle.Fill>.

3. Přetáhněte ovládací prvek <xref:System.Windows.Forms.TreeView> ze **sady nástrojů** na panel na levé straně ovládacího prvku <xref:System.Windows.Forms.SplitContainer>. V okně **vlastnosti** nastavte vlastnost <xref:System.Windows.Forms.SplitContainer.Dock%2A> na <xref:System.Windows.Forms.DockStyle.Left> kliknutím na levý panel v editoru hodnot, který se zobrazí po kliknutí na šipku dolů.

4. Přetáhněte na **panel nástrojů**jiný ovládací prvek <xref:System.Windows.Forms.SplitContainer>; umístěte ho do pravého panelu <xref:System.Windows.Forms.SplitContainer> ovládacího prvku, který jste přidali do formuláře. V okně **vlastnosti** nastavte vlastnost <xref:System.Windows.Forms.SplitContainer.Dock%2A> na hodnotu <xref:System.Windows.Forms.DockStyle.Fill> a vlastnost <xref:System.Windows.Forms.SplitContainer.Orientation%2A> na <xref:System.Windows.Forms.Orientation.Horizontal>.

5. Přetáhněte ovládací prvek <xref:System.Windows.Forms.ListView> ze **sady nástrojů** na horní panel druhého ovládacího prvku <xref:System.Windows.Forms.SplitContainer>, který jste přidali do formuláře. Nastavte vlastnost <xref:System.Windows.Forms.SplitContainer.Dock%2A> ovládacího prvku <xref:System.Windows.Forms.ListView> na <xref:System.Windows.Forms.DockStyle.Fill>.

6. Přetáhněte ovládací prvek <xref:System.Windows.Forms.RichTextBox> ze **sady nástrojů** na spodní panel druhého ovládacího prvku <xref:System.Windows.Forms.SplitContainer>. Nastavte vlastnost <xref:System.Windows.Forms.SplitContainer.Dock%2A> ovládacího prvku <xref:System.Windows.Forms.RichTextBox> na <xref:System.Windows.Forms.DockStyle.Fill>.

     Když stisknete klávesu F5 ke spuštění aplikace, formulář zobrazí uživatelské rozhraní se třemi částmi, podobně jako v aplikaci Microsoft Outlook.

    > [!NOTE]
    > Když umístíte ukazatel myši na některé z rozdělovacích ovládacích prvků v ovládacím prvku <xref:System.Windows.Forms.SplitContainer>, můžete změnit velikost vnitřních rozměrů.

V tomto okamžiku vývoje aplikací jste si vystavili sofistikované uživatelské rozhraní. Dalším krokem je pokračování v programování samotné aplikace, třeba propojením ovládacího prvku <xref:System.Windows.Forms.TreeView> a <xref:System.Windows.Forms.ListView> ovládací prvky s nějakým druhem zdroje dat. Další informace o připojení ovládacích prvků k datům naleznete v tématu [datové vazby a model Windows Forms](../data-binding-and-windows-forms.md).

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.SplitContainer>
- [Ovládací prvek SplitContainer](splitcontainer-control-windows-forms.md)
