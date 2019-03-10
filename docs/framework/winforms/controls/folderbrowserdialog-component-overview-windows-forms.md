---
title: FolderBrowserDialog – přehled komponenty (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- FolderBrowserDialog
helpviewer_keywords:
- FolderBrowserDialog component [Windows Forms], about FolderBrowserDialog
- directories [Windows Forms], enabling browsing in applications
- folders [Windows Forms], enabling browsing in applications
ms.assetid: 796b622c-3ba9-4356-93bb-e217fc52f2c7
ms.openlocfilehash: d08eb456ea2d2d3b805d3df7e0e79b26ea7d415e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708246"
---
# <a name="folderbrowserdialog-component-overview-windows-forms"></a><span data-ttu-id="80ed5-102">FolderBrowserDialog – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="80ed5-102">FolderBrowserDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="80ed5-103">Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> komponenta je modální dialogové okno, které slouží k procházení a výběr složky.</span><span class="sxs-lookup"><span data-stu-id="80ed5-103">The Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> component is a modal dialog box that is used for browsing and selecting folders.</span></span> <span data-ttu-id="80ed5-104">V rámci lze také vytvořit nové složky <xref:System.Windows.Forms.FolderBrowserDialog> komponenty.</span><span class="sxs-lookup"><span data-stu-id="80ed5-104">New folders can also be created from within the <xref:System.Windows.Forms.FolderBrowserDialog> component.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="80ed5-105">Vyberte soubory, místo složky, použijte [OpenFileDialog](openfiledialog-component-windows-forms.md) komponenty.</span><span class="sxs-lookup"><span data-stu-id="80ed5-105">To select files, instead of folders, use the [OpenFileDialog](openfiledialog-component-windows-forms.md) component.</span></span>  
  
 <span data-ttu-id="80ed5-106"><xref:System.Windows.Forms.FolderBrowserDialog> Součást se zobrazí v době běhu pomocí <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="80ed5-106">The <xref:System.Windows.Forms.FolderBrowserDialog> component is displayed at run time using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span> <span data-ttu-id="80ed5-107">Nastavte <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> vlastnosti k určení složky úplně nahoře a jakýmkoliv podsložkám, které se zobrazí ve stromovém zobrazení dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="80ed5-107">Set the <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> property to determine the top-most folder and any subfolders that will appear within the tree view of the dialog box.</span></span> <span data-ttu-id="80ed5-108">Jakmile se zobrazí dialogové okno, můžete použít <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> vlastnost k získání cesty ke složce, která byla vybrána.</span><span class="sxs-lookup"><span data-stu-id="80ed5-108">Once the dialog box has been shown, you can use the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property to get the path of the folder that was selected.</span></span>  
  
 <span data-ttu-id="80ed5-109">Když se přidá do formuláře, <xref:System.Windows.Forms.FolderBrowserDialog> součást se zobrazí v hlavním panelu v dolní části Návrháře formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="80ed5-109">When it is added to a form, the <xref:System.Windows.Forms.FolderBrowserDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80ed5-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="80ed5-110">See also</span></span>
- <xref:System.Windows.Forms.FolderBrowserDialog>
- [<span data-ttu-id="80ed5-111">Postupy: Zvolte složky s komponentou Windows Forms FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="80ed5-111">How to: Choose Folders with the Windows Forms FolderBrowserDialog Component</span></span>](how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component.md)
- [<span data-ttu-id="80ed5-112">Komponenta FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="80ed5-112">FolderBrowserDialog Component</span></span>](folderbrowserdialog-component-windows-forms.md)
