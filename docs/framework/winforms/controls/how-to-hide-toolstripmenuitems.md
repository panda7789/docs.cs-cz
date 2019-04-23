---
title: 'Postupy: Skrytí ToolStripMenuItems'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding
- MenuStrip control [Windows Forms], hiding menu items
- menus [Windows Forms], hiding menu items
- menu items [Windows Forms], hiding
- hiding menu items
ms.assetid: 418a768f-808a-44cd-8cef-f4e161883621
ms.openlocfilehash: dc9daa945f2a546548f2cc6ea033378bd9ceff93
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59127423"
---
# <a name="how-to-hide-toolstripmenuitems"></a><span data-ttu-id="6e1fb-102">Postupy: Skrytí ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="6e1fb-102">How to: Hide ToolStripMenuItems</span></span>
<span data-ttu-id="6e1fb-103">Skrytí položek nabídky je způsob, jak ovládací prvek uživatelského rozhraní aplikace a omezit uživatelských příkazů.</span><span class="sxs-lookup"><span data-stu-id="6e1fb-103">Hiding menu items is a way to control the user interface of your application and restrict user commands.</span></span> <span data-ttu-id="6e1fb-104">Často můžete skrýt celou nabídku, když jsou všechny položky nabídky na něm není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="6e1fb-104">Often, you will want to hide an entire menu when all of the menu items on it are unavailable.</span></span> <span data-ttu-id="6e1fb-105">To představuje méně rozptýlení pro daného uživatele.</span><span class="sxs-lookup"><span data-stu-id="6e1fb-105">This presents fewer distractions for the user.</span></span> <span data-ttu-id="6e1fb-106">Kromě toho můžete chtít skrýt i zakázat nabídky nebo položku nabídky, protože skrytí samostatně nebrání uživateli přístup k příkazu nabídky pomocí klávesové zkratky.</span><span class="sxs-lookup"><span data-stu-id="6e1fb-106">Furthermore, you might want to both hide and disable the menu or menu item, as hiding alone does not prevent the user from accessing a menu command by using a shortcut key.</span></span>  
  
### <a name="to-hide-any-menu-item-programmatically"></a><span data-ttu-id="6e1fb-107">Chcete-li skrýt všechny položky nabídky prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="6e1fb-107">To hide any menu item programmatically</span></span>  
  
-   <span data-ttu-id="6e1fb-108">V rámci metody, kde nastavíte vlastnosti položky nabídky, přidejte kód pro nastavení <xref:System.Windows.Forms.ToolStripItem.Visible%2A> vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="6e1fb-108">Within the method where you set the properties of the menu item, add code to set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property to `false`.</span></span>  
  
    ```vb  
    MenuItem3.Visible = False  
    ```  
  
    ```csharp  
    menuItem3.Visible = false;  
    ```  
  
    ```cpp  
    menuItem3->Visible = false;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6e1fb-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e1fb-109">See also</span></span>

- <xref:System.Windows.Forms.ToolStripItem.Visible%2A>
- <xref:System.Windows.Forms.MenuStrip>
- [<span data-ttu-id="6e1fb-110">Přehled ovládacího prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="6e1fb-110">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
- [<span data-ttu-id="6e1fb-111">Postupy: Zákaz ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="6e1fb-111">How to: Disable ToolStripMenuItems</span></span>](how-to-disable-toolstripmenuitems.md)
