---
title: Přehled komponenty FolderBrowserDialog
ms.date: 03/30/2017
f1_keywords:
- FolderBrowserDialog
helpviewer_keywords:
- FolderBrowserDialog component [Windows Forms], about FolderBrowserDialog
- directories [Windows Forms], enabling browsing in applications
- folders [Windows Forms], enabling browsing in applications
ms.assetid: 796b622c-3ba9-4356-93bb-e217fc52f2c7
ms.openlocfilehash: 8b017ba08ae4205e930ac00177c89a89fde17d3b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745727"
---
# <a name="folderbrowserdialog-component-overview-windows-forms"></a><span data-ttu-id="60733-102">FolderBrowserDialog – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="60733-102">FolderBrowserDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="60733-103">Součást model Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> je modální dialogové okno, které se používá pro procházení a výběr složek.</span><span class="sxs-lookup"><span data-stu-id="60733-103">The Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> component is a modal dialog box that is used for browsing and selecting folders.</span></span> <span data-ttu-id="60733-104">Nové složky je také možné vytvořit v rámci součásti <xref:System.Windows.Forms.FolderBrowserDialog>.</span><span class="sxs-lookup"><span data-stu-id="60733-104">New folders can also be created from within the <xref:System.Windows.Forms.FolderBrowserDialog> component.</span></span>

> [!NOTE]
> <span data-ttu-id="60733-105">Chcete-li vybrat soubory namísto složek, použijte komponentu [OpenFileDialog](openfiledialog-component-windows-forms.md) .</span><span class="sxs-lookup"><span data-stu-id="60733-105">To select files, instead of folders, use the [OpenFileDialog](openfiledialog-component-windows-forms.md) component.</span></span>

<span data-ttu-id="60733-106">Komponenta <xref:System.Windows.Forms.FolderBrowserDialog> se zobrazuje za běhu pomocí metody <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="60733-106">The <xref:System.Windows.Forms.FolderBrowserDialog> component is displayed at run time using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span> <span data-ttu-id="60733-107">Nastavte vlastnost <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A>, aby se určila složka nejvyšší úrovně a všechny podsložky, které se zobrazí ve stromovém zobrazení dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="60733-107">Set the <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> property to determine the top-most folder and any subfolders that will appear within the tree view of the dialog box.</span></span> <span data-ttu-id="60733-108">Po zobrazení dialogového okna můžete použít vlastnost <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> a získat tak cestu vybrané složky.</span><span class="sxs-lookup"><span data-stu-id="60733-108">Once the dialog box has been shown, you can use the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property to get the path of the folder that was selected.</span></span>

<span data-ttu-id="60733-109">Při přidání do formuláře se komponenta <xref:System.Windows.Forms.FolderBrowserDialog> zobrazí v zásobníku v dolní části Návrhář formulářů v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="60733-109">When it is added to a form, the <xref:System.Windows.Forms.FolderBrowserDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="60733-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="60733-110">See also</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [<span data-ttu-id="60733-111">Postupy: Výběr složek pomocí komponenty Windows Forms FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="60733-111">How to: Choose Folders with the Windows Forms FolderBrowserDialog Component</span></span>](how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component.md)
- [<span data-ttu-id="60733-112">Komponenta FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="60733-112">FolderBrowserDialog Component</span></span>](folderbrowserdialog-component-windows-forms.md)
