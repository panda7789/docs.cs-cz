---
title: SaveFileDialog – přehled komponenty (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
ms.openlocfilehash: b06c4d510cefdc7558944995594fd209b6121cb1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103036"
---
# <a name="savefiledialog-component-overview-windows-forms"></a><span data-ttu-id="2218a-102">SaveFileDialog – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="2218a-102">SaveFileDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="2218a-103">Windows Forms <xref:System.Windows.Forms.SaveFileDialog> komponenta je předem nakonfigurované dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="2218a-103">The Windows Forms <xref:System.Windows.Forms.SaveFileDialog> component is a pre-configured dialog box.</span></span> <span data-ttu-id="2218a-104">Je stejný jako standardní **uložit soubor** dialogové okno používá Windows.</span><span class="sxs-lookup"><span data-stu-id="2218a-104">It is the same as the standard **Save File** dialog box used by Windows.</span></span> <span data-ttu-id="2218a-105">Dědí z <xref:System.Windows.Forms.CommonDialog> třídy.</span><span class="sxs-lookup"><span data-stu-id="2218a-105">It inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>  
  
## <a name="working-with-the-savefiledialog-component"></a><span data-ttu-id="2218a-106">Práce s SaveFileDialog – komponenta</span><span class="sxs-lookup"><span data-stu-id="2218a-106">Working with the SaveFileDialog Component</span></span>  
 <span data-ttu-id="2218a-107">Použijte jako jednoduché řešení umožňující uživatelům ukládat soubory místo dialogové okno Vlastní konfigurace.</span><span class="sxs-lookup"><span data-stu-id="2218a-107">Use it as a simple solution for enabling users to save files instead of configuring your own dialog box.</span></span> <span data-ttu-id="2218a-108">Základní funkce aplikací, které vytvoříte je pomocí standardní dialogová okna Windows, okamžitě uživatelé znají.</span><span class="sxs-lookup"><span data-stu-id="2218a-108">By relying on standard Windows dialog boxes, the basic functionality of applications you create is immediately familiar to users.</span></span> <span data-ttu-id="2218a-109">Mějte na paměti, ale, že pomocí <xref:System.Windows.Forms.SaveFileDialog> komponenty, je nutné napsat vlastní logikou ukládání souborů.</span><span class="sxs-lookup"><span data-stu-id="2218a-109">Be aware, however, that when using the <xref:System.Windows.Forms.SaveFileDialog> component, you must write your own file-saving logic.</span></span>  
  
 <span data-ttu-id="2218a-110">Můžete použít <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu pro zobrazení dialogového okna v době běhu.</span><span class="sxs-lookup"><span data-stu-id="2218a-110">You can use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box at run time.</span></span> <span data-ttu-id="2218a-111">Můžete otevřít soubor pomocí režimu pro čtení a zápis <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="2218a-111">You can open a file in read/write mode using the <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method.</span></span>  
  
 <span data-ttu-id="2218a-112">Když se přidá do formuláře, <xref:System.Windows.Forms.SaveFileDialog> součást se zobrazí v hlavním panelu v dolní části Návrháře formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="2218a-112">When it is added to a form, the <xref:System.Windows.Forms.SaveFileDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2218a-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2218a-113">See also</span></span>

- <xref:System.Windows.Forms.SaveFileDialog>
- [<span data-ttu-id="2218a-114">Komponenta SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="2218a-114">SaveFileDialog Component</span></span>](savefiledialog-component-windows-forms.md)
