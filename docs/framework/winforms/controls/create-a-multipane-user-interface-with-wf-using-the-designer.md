---
title: 'Postupy: Vytváření uživatelského rozhraní s více podokny s formuláři Windows pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- user interface [Windows Forms], multipane
- SplitContainer control [Windows Forms], using the designer
- multipane user interface
ms.assetid: c3f9294d-a26c-4198-9242-f237f55f7573
ms.openlocfilehash: d0faf86ce31dad6bc053b5af8902e500d2b1c75b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529858"
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms-using-the-designer"></a>Postupy: Vytváření uživatelského rozhraní s více podokny s formuláři Windows pomocí Návrháře
V následujícím postupu vytvoříte více podokny uživatelské rozhraní, které je podobné použít v aplikaci Microsoft Outlook s **složky** seznamu **zprávy** podokně a **Preview** podokně. Toto uspořádání je dosaženo hlavně prostřednictvím ukotvení ovládacích prvků pomocí formuláře.  
  
 V případě ukotvení ovládacího prvku určit, které okraje nadřazeného kontejneru ovládacího prvku je připojen k. Proto pokud nastavíte <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Right>, pravý okraj ovládacího prvku bude ukotven na pravý okraj jeho nadřazenému ovládacímu prvku. Kromě toho se změnila ukotveného okraje ovládacího prvku velikost odpovídat jeho ovládacího prvku kontejneru. Další informace o tom, jak <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnost funguje, najdete v části [postupy: ukotvení ovládacích prvků ve Windows Forms](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md).  
  
 Tento postup se zaměřuje na uspořádání <xref:System.Windows.Forms.SplitContainer> a jiných ovládacích prvků na formuláři, nikoli na přidání funkce zpřístupnění aplikace napodobovat Microsoft Outlook.  
  
 Pokud chcete vytvořit toto uživatelské rozhraní, umístěte všechny ovládací prvky v rámci <xref:System.Windows.Forms.SplitContainer> ovládací prvek, který obsahuje <xref:System.Windows.Forms.TreeView> ovládacího prvku v levém panelu. Na pravém panelu <xref:System.Windows.Forms.SplitContainer> ovládací prvek obsahuje druhý <xref:System.Windows.Forms.SplitContainer> řízení s <xref:System.Windows.Forms.ListView> ovládací prvek nahoře <xref:System.Windows.Forms.RichTextBox> ovládacího prvku. Tyto <xref:System.Windows.Forms.SplitContainer> ovládací prvky povolit nezávislé změnu velikosti další ovládací prvky na formuláři. Můžete upravit postupy v tomto postupu plavidla vlastní uživatelská rozhraní vlastní.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-an-outlook-style-user-interface-at-design-time"></a>Chcete-li vytvořit uživatelské rozhraní aplikace Outlook-style v době návrhu  
  
1.  Vytvořte nový projekt aplikace Windows. Podrobnosti najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Přetáhněte <xref:System.Windows.Forms.SplitContainer> řídit z **sada nástrojů** do formuláře. V **vlastnosti** nastavte <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.  
  
3.  Přetáhněte <xref:System.Windows.Forms.TreeView> řídit z **sada nástrojů** na levém panelu <xref:System.Windows.Forms.SplitContainer> ovládacího prvku. V **vlastnosti** nastavte <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Left> kliknutím na levém panelu v editoru hodnota zobrazí, když po kliknutí na šipku dolů.  
  
4.  Přetáhněte další <xref:System.Windows.Forms.SplitContainer> řídit z **sada nástrojů**; umístit na pravém panelu <xref:System.Windows.Forms.SplitContainer> jste přidali do svého formuláře ovládací prvek. V **vlastnosti** nastavte <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill> a <xref:System.Windows.Forms.SplitContainer.Orientation%2A> vlastnost <xref:System.Windows.Forms.Orientation.Horizontal>.  
  
5.  Přetáhněte <xref:System.Windows.Forms.ListView> řídit z **sada nástrojů** na horním panelu druhý <xref:System.Windows.Forms.SplitContainer> jste přidali do svého formuláře ovládací prvek. Nastavte <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnost <xref:System.Windows.Forms.ListView> řídit k <xref:System.Windows.Forms.DockStyle.Fill>.  
  
6.  Přetáhněte <xref:System.Windows.Forms.RichTextBox> řídit z **sada nástrojů** na spodním panelu druhý <xref:System.Windows.Forms.SplitContainer> ovládacího prvku. Nastavte <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnost <xref:System.Windows.Forms.RichTextBox> řídit k <xref:System.Windows.Forms.DockStyle.Fill>.  
  
     V tomto okamžiku stisknutí klávesy F5 a spusťte aplikaci formuláři se zobrazí na třemi částmi uživatelské rozhraní, podobně jako u aplikace Microsoft Outlook.  
  
    > [!NOTE]
    >  Když vložíte ukazatel myši nad buď příčky v rámci <xref:System.Windows.Forms.SplitContainer> ovládací prvky, můžete změnit velikost interní dimenze.  
  
     V tomto okamžiku při vývoji aplikací mít vytvořené sofistikované uživatelské rozhraní. Dalším krokem je pokračováním programování aplikací, samostatně, případně připojením <xref:System.Windows.Forms.TreeView> řízení a <xref:System.Windows.Forms.ListView> ovládacích prvků do určitého druhu zdroje dat. Další informace o připojení ovládacích prvků k datům najdete v tématu [datové vazby a rozhraní Windows Forms](../../../../docs/framework/winforms/data-binding-and-windows-forms.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.SplitContainer>  
 [Ovládací prvek SplitContainer](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)
