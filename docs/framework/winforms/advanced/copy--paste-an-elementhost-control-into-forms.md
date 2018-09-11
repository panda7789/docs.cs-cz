---
title: 'Návod: Zkopírování a vložení ovládacího prvku ElementHost do samostatného formuláře Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 6e81bb13-577c-46c3-a1cf-8d15969fb83e
ms.openlocfilehash: 55b426fbe95bac269183a649ecd839175a8cbdda
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44337678"
---
# <a name="walkthrough-copying-and-pasting-an-elementhost-control-into-separate-windows-forms"></a>Návod: Zkopírování a vložení ovládacího prvku ElementHost do samostatného formuláře Windows
Tento návod ukazuje, jak kopírovat ovládací prvek Windows Presentation Foundation (WPF) z jeden formulář Windows do jiného.  
  
 V tomto podrobném návodu můžete provádět následující úlohy:  
  
-   Vytvoření projektu.  
  
-   Zkopírujte ovládací prvek WPF.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu Windows Forms.  
  
> [!NOTE]
>  Při hostování obsahu WPF, jsou podporovány pouze projekty C# a Visual Basic.  
  
#### <a name="to-create-the-project"></a>Vytvoření projektu  
  
-   Vytvořte nový projekt Formulářové aplikace Windows v jazyce Visual Basic nebo Visual C# s názvem `CopyElementHost`.  
  
## <a name="copying-a-wpf-control"></a>Kopírování ovládacího prvku WPF  
 Po přidání ovládacího prvku WPF do projektu, můžete ji zkopírovat do jiných formulářů v projektu.  
  
#### <a name="to-copy-a-wpf-control"></a>Kopírování ovládacího prvku WPF  
  
1.  Přidat nový WPF <xref:System.Windows.Controls.UserControl> projektu do řešení. Použití výchozího názvu pro typ ovládacího prvku `UserControl1.xaml`. Další informace najdete v tématu [návod: vytváření nových WPF obsahu ve Windows Forms v době návrhu](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  Sestavte projekt.  
  
3.  Otevřít `Form1` v Návrháři formulářů Windows.  
  
4.  Z **nástrojů**, přetáhněte instance `UserControl1` do formuláře.  
  
     Instance `UserControl1` hostována v novém <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek s názvem `elementHost1`.  
  
5.  S `elementHost1` vybrána, stiskněte CTRL + C zkopírujte do schránky.  
  
6.  Přidáte nový formulář Windows do projektu. Použití výchozího názvu pro typ formuláře `Form2`.  
  
7.  S `Form2` otevřete v Návrháři formulářů Windows, stiskněte klávesy CTRL + V vložte kopii `elementHost1` do formuláře.  
  
     Zkopírovaný ovládací prvek je také název `elementHost1`, protože je privátní pole `Form2` třídy. Neexistuje žádné kolize názvů s `elementHost1` v `Form1` třídy.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Migrace a interoperabilita](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [Používání ovládacích prvků WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [Návrh kódu XAML v sadě Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
