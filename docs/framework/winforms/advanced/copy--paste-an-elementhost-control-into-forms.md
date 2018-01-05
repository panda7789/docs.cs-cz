---
title: "Návod: Zkopírování a vložení ovládacího prvku ElementHost do samostatného formuláře Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 6e81bb13-577c-46c3-a1cf-8d15969fb83e
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 579bce312296d9799f9f7c739f740e2c9111ccff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-copying-and-pasting-an-elementhost-control-into-separate-windows-forms"></a>Návod: Zkopírování a vložení ovládacího prvku ElementHost do samostatného formuláře Windows
Tento návod ukazuje, jak kopírovat ovládacího prvku Windows Presentation Foundation (WPF) z jednoho formuláře Windows do jiného.  
  
 V tomto návodu můžete provádět následující úlohy:  
  
-   Vytvoření projektu.  
  
-   Zkopírujte ovládací prvek WPF.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu modelu Windows Forms.  
  
> [!NOTE]
>  Pokud hostování obsahu subsystému WPF, jsou podporovány pouze projekty C# a Visual Basic.  
  
#### <a name="to-create-the-project"></a>Vytvoření projektu  
  
-   Vytvořte nový projekt aplikace Windows Forms v jazyce Visual Basic a Visual C# s názvem `CopyElementHost`.  
  
## <a name="copying-a-wpf-control"></a>Kopírování ovládací prvek WPF  
 Po přidání ovládací prvek WPF do projektu, zkopírujte jej do jiných formulářů v projektu.  
  
#### <a name="to-copy-a-wpf-control"></a>Kopírování ovládací prvek WPF  
  
1.  Přidat nové WPF <xref:System.Windows.Controls.UserControl> projektu k řešení. Použití výchozího názvu pro typ ovládacího prvku `UserControl1.xaml`. Další informace najdete v tématu [návod: vytvoření nové WPF obsahu v aplikaci Windows Forms v době návrhu](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  Sestavte projekt.  
  
3.  Otevřete `Form1` v Návrháři formulářů.  
  
4.  Z **sada nástrojů**, přetáhněte instanci `UserControl1` do formuláře.  
  
     Instance `UserControl1` je hostován v nové <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek s názvem `elementHost1`.  
  
5.  S `elementHost1` vybrána, stiskněte CTRL + C zkopírujte jej do schránky.  
  
6.  Přidání nového formuláře Windows Form do projektu. Použití výchozího názvu pro typ formuláře `Form2`.  
  
7.  S `Form2` otevřít v Návrháři formulářů, stiskněte klávesy CTRL + V vložte kopii `elementHost1` do formuláře.  
  
     Zkopírovaný ovládacího prvku se nazývá také `elementHost1`, protože je privátní pole `Form2` třídy. Neexistuje žádný název kolizí s `elementHost1` v `Form1` třídy.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Migrace a interoperabilita](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [Používání ovládacích prvků WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [Návrhář WPF](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)
