---
title: "Postupy: Vytváření nadřazených formulářů MDI"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parent forms
- MDI [Windows Forms], creating forms
ms.assetid: 12c71221-2377-4bb6-b10b-7b4b300fd462
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0147bc0777fdf3168ab0bc36ced0943571187d3c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-mdi-parent-forms"></a>Postupy: Vytváření nadřazených formulářů MDI
> [!IMPORTANT]
>  Toto téma používá <xref:System.Windows.Forms.MainMenu> ovládací prvek, který byl nahrazen <xref:System.Windows.Forms.MenuStrip> ovládacího prvku. <xref:System.Windows.Forms.MainMenu> Řízení se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte.  Informace o vytváření MDI nadřazené formuláře pomocí <xref:System.Windows.Forms.MenuStrip>, najdete v části [postupy: vytvoření seznamu okna MDI pomocí MenuStrip](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md).  
  
 Základ pro aplikace rozhraní více dokumentů (MDI) je nadřazeného formuláře MDI. Toto je formulář, který obsahuje podřízených oken MDI, které jsou dílčí windows, ve kterém uživatel komunikuje aplikace MDI. Vytvoření formuláře MDI nadřazené je snadné, v Návrháři formulářů a programově.  
  
### <a name="to-create-an-mdi-parent-form-at-design-time"></a>K vytvoření formuláře MDI nadřazené v době návrhu  
  
1.  Vytvořte projekt aplikace Windows.  
  
2.  V **vlastnosti** nastavte <xref:System.Windows.Forms.Form.IsMdiContainer%2A> vlastnost **true**.  
  
     Tento formulář označí jako kontejner MDI pro podřízené windows.  
  
    > [!NOTE]
    >  Při nastavení vlastností ve **vlastnosti** okno, můžete také nastavit `WindowState` vlastnost **Maximized**, pokud chcete, protože je to nejjednodušší provádět k manipulaci s podřízených oken MDI, pokud je nadřazený formulář Maximalizovaný. Kromě toho Pamatujte, že jsou okraje nadřazeného formuláře MDI vyzvedne, až bude barvu systému (set v Ovládacích panelech systému Windows), místo barvu pozadí nastavíte pomocí <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType> vlastnost.  
  
3.  Z **sada nástrojů**, přetáhněte ji **MenuStrip** ovládacího prvku do formuláře. Vytvořit položku nabídky nejvyšší úrovně s **Text** vlastnost nastavena na hodnotu **& souboru** s názvem položky podnabídky **& Nový** a **& Zavřít**. Také vytvořit nabídku nejvyšší úrovně položky názvem **& okno**.  
  
     První nabídky vytvoří a skrytí položek nabídky v době běhu, a druhá nabídka bude sledovat otevřete podřízených oken MDI. V tomto okamžiku jste vytvořili nadřazeného okna MDI.  
  
4.  Stiskněte klávesu **F5** ke spuštění aplikace. Informace o vytváření podřízeného MDI windows, které fungují v rámci nadřazeného formuláře MDI najdete v tématu [postupy: vytváření podřízených formulářů MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md).  
  
## <a name="see-also"></a>Viz také  
 [Aplikace MDI (Multiple-Document Interface)](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [Postupy: Vytváření podřízených formulářů MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [Postupy: Určení podřízeného prvku aktivního MDI](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 [Postupy: Odesílání dat do aktivního podřízeného MDI](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 [Postupy: Uspořádání podřízených formulářů MDI](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)
