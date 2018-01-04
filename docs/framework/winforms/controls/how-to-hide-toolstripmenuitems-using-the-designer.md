---
title: "Postupy: Skrývání ToolStripMenuItems pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding menu items in designer
- MenuStrip control [Windows Forms], hiding menu items in designer
- menu items [Windows Forms], hiding
ms.assetid: 8f1b057e-3d8a-4f11-88df-935f7b29a836
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5ac840953e34ac6726bb1c240c062d0f17b8cb71
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-hide-toolstripmenuitems-using-the-designer"></a>Postupy: Skrývání ToolStripMenuItems pomocí Návrháře
Skrytí položek nabídky je způsob, jak řídit uživatelské rozhraní (UI) vaší aplikace a omezit uživatele příkazy. Často můžete skrýt celou nabídku, když jsou všechny položky nabídky na něm není k dispozici. To představuje rušeni pro uživatele. Kromě toho můžete chtít skrýt i zakázat nabídka nebo položka nabídky, jak skrytí samostatně nezabrání uživatel přístup k příkazu nabídky pomocí klávesové zkratky. Další informace o deaktivace položek nabídky najdete v tématu [postupy: zákaz ToolStripMenuItems pomocí návrháře](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-hide-a-top-level-menu-and-its-submenu-items"></a>Chcete-li skrýt nabídek nejvyšší úrovně a jeho dílčí položky  
  
1.  Vyberte položku nabídky nejvyšší úrovně a nastavit jeho <xref:System.Windows.Forms.ToolStripItem.Visible%2A> nebo <xref:System.Windows.Forms.ToolStripItem.Available%2A> vlastnost `false`.  
  
     Skrytí položek nabídky nejvyšší úrovně, všechny položky nabídky v rámci této nabídky jsou rovněž skryté. Pokud kliknete na jiném zařízení, než na <xref:System.Windows.Forms.MenuStrip> po nastavení <xref:System.Windows.Forms.ToolStripItem.Visible%2A> k `false`, zmizí ze svého formuláře, což ukazuje spuštění účinku akci celý nabídka nejvyšší úrovně a jeho dílčí položky. Chcete-li zobrazit skrytá nabídka nejvyšší úrovně v době návrhu, klikněte na <xref:System.Windows.Forms.MenuStrip> v **komponent**v **Osnova dokumentu**, nebo v horní části mřížku vlastností.  
  
> [!NOTE]
>  Občas bude skrýt celou nabídku s výjimkou několika nabídky podřízené ve scénáři slučovat dokumentu rozhraní (MDI).  
  
### <a name="to-hide-a-submenu-item"></a>Chcete-li skrýt položku podnabídky  
  
1.  Vyberte položku podnabídky a nastavit jeho <xref:System.Windows.Forms.ToolStripItem.Visible%2A> vlastnost `false`.  
  
     Skryjete položku podnabídky, zůstává viditelná ve formuláři v době návrhu tak, aby bylo možné snadno vybrat pro další práci. Ve skutečnosti se bude skrytá za běhu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ToolStripItem.Visible%2A>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>  
 <xref:System.Windows.Forms.ToolStripItem.Available%2A>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>  
 [Přehled ovládacího prvku MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)  
 [Postupy: Zákaz ToolStripMenuItems pomocí Návrháře](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md)
