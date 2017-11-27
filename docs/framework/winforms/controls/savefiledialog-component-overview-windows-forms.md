---
title: "SaveFileDialog – přehled komponenty (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4cbdc1cb96234e302458cbeac6d6ae26b63c956e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="savefiledialog-component-overview-windows-forms"></a><span data-ttu-id="e3536-102">SaveFileDialog – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="e3536-102">SaveFileDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="e3536-103">Windows Forms <xref:System.Windows.Forms.SaveFileDialog> součást je předem nakonfigurovaný dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="e3536-103">The Windows Forms <xref:System.Windows.Forms.SaveFileDialog> component is a pre-configured dialog box.</span></span> <span data-ttu-id="e3536-104">Je stejný jako standardní **uložit soubor** dialogové okno používaná systémem Windows.</span><span class="sxs-lookup"><span data-stu-id="e3536-104">It is the same as the standard **Save File** dialog box used by Windows.</span></span> <span data-ttu-id="e3536-105">Dědí z <xref:System.Windows.Forms.CommonDialog> třídy.</span><span class="sxs-lookup"><span data-stu-id="e3536-105">It inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>  
  
## <a name="working-with-the-savefiledialog-component"></a><span data-ttu-id="e3536-106">Práce s SaveFileDialog – komponenta</span><span class="sxs-lookup"><span data-stu-id="e3536-106">Working with the SaveFileDialog Component</span></span>  
 <span data-ttu-id="e3536-107">Použijte jako jednoduchým řešením pro povolení uživatelům ukládat soubory namísto dialogové okno Vlastní konfigurace.</span><span class="sxs-lookup"><span data-stu-id="e3536-107">Use it as a simple solution for enabling users to save files instead of configuring your own dialog box.</span></span> <span data-ttu-id="e3536-108">Podle standardní dialogová okna Windows, je dobře obeznámeni uživatelé základní funkce aplikací, které vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="e3536-108">By relying on standard Windows dialog boxes, the basic functionality of applications you create is immediately familiar to users.</span></span> <span data-ttu-id="e3536-109">Nezapomeňte však, že v případě pomocí <xref:System.Windows.Forms.SaveFileDialog> součást, musíte napsat vlastní logiky ukládání souborů.</span><span class="sxs-lookup"><span data-stu-id="e3536-109">Be aware, however, that when using the <xref:System.Windows.Forms.SaveFileDialog> component, you must write your own file-saving logic.</span></span>  
  
 <span data-ttu-id="e3536-110">Můžete použít <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu pro zobrazení dialogu za běhu.</span><span class="sxs-lookup"><span data-stu-id="e3536-110">You can use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box at run time.</span></span> <span data-ttu-id="e3536-111">Můžete otevřít soubor v režimu pro čtení a zápis pomocí <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="e3536-111">You can open a file in read/write mode using the <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method.</span></span>  
  
 <span data-ttu-id="e3536-112">Při jejím přidání do formuláře <xref:System.Windows.Forms.SaveFileDialog> součást se zobrazí na hlavním panelu v dolní části Návrhář formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="e3536-112">When it is added to a form, the <xref:System.Windows.Forms.SaveFileDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3536-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="e3536-113">See Also</span></span>  
 <xref:System.Windows.Forms.SaveFileDialog>  
 [<span data-ttu-id="e3536-114">SaveFileDialog – komponenta</span><span class="sxs-lookup"><span data-stu-id="e3536-114">SaveFileDialog Component</span></span>](../../../../docs/framework/winforms/controls/savefiledialog-component-windows-forms.md)
