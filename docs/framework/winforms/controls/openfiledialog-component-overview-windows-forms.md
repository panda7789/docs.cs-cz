---
title: "OpenFileDialog – přehled komponenty (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OpenFileDialog
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], about OpenFileDialog
- Open File dialog box [Windows Forms], displaying in Windows Forms
ms.assetid: cd717300-46b6-4f82-8207-b218fa7fa407
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d3e5dc6630d9bc7a2090a28daabbf08eeed59005
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="openfiledialog-component-overview-windows-forms"></a><span data-ttu-id="e438e-102">OpenFileDialog – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="e438e-102">OpenFileDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="e438e-103">Windows Forms <xref:System.Windows.Forms.OpenFileDialog> součást je předem nakonfigurovaný dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="e438e-103">The Windows Forms <xref:System.Windows.Forms.OpenFileDialog> component is a pre-configured dialog box.</span></span> <span data-ttu-id="e438e-104">Stejná **otevření souboru** dialogové okno vystavené operačního systému Windows.</span><span class="sxs-lookup"><span data-stu-id="e438e-104">It is the same **Open File** dialog box exposed by the Windows operating system.</span></span> <span data-ttu-id="e438e-105">Dědí z <xref:System.Windows.Forms.CommonDialog> třídy.</span><span class="sxs-lookup"><span data-stu-id="e438e-105">It inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>  
  
## <a name="using-this-component"></a><span data-ttu-id="e438e-106">Pomocí této součásti</span><span class="sxs-lookup"><span data-stu-id="e438e-106">Using this Component</span></span>  
 <span data-ttu-id="e438e-107">Použijte tuto součást v rámci vaší aplikace systému Windows jako jednoduchým řešením pro výběr souboru místo dialogové okno Vlastní konfigurace.</span><span class="sxs-lookup"><span data-stu-id="e438e-107">Use this component within your Windows-based application as a simple solution for file selection in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="e438e-108">Podle standardní dialogová okna Windows, můžete vytvořit aplikace, jehož základní funkce je dobře obeznámeni uživatele.</span><span class="sxs-lookup"><span data-stu-id="e438e-108">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span> <span data-ttu-id="e438e-109">Nezapomeňte však, že v případě pomocí <xref:System.Windows.Forms.OpenFileDialog> součást, musíte napsat vlastní logiky otevírání souboru.</span><span class="sxs-lookup"><span data-stu-id="e438e-109">Be aware, however, that when using the <xref:System.Windows.Forms.OpenFileDialog> component, you must write your own file-opening logic.</span></span>  
  
 <span data-ttu-id="e438e-110">Použití <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu pro zobrazení dialogu za běhu.</span><span class="sxs-lookup"><span data-stu-id="e438e-110">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog at run time.</span></span> <span data-ttu-id="e438e-111">Můžete povolit uživatelům vybrat víc souborů otevřít pomocí <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e438e-111">You can enable users to multi-select files to be opened with the <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A> property.</span></span> <span data-ttu-id="e438e-112">Kromě toho můžete použít <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> vlastnosti k určení, pokud se v dialogovém okně zobrazí zaškrtávací políčko jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="e438e-112">Additionally, you can use the <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> property to determine if a read-only check box appears in the dialog box.</span></span> <span data-ttu-id="e438e-113"><xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> Vlastnost určuje, zda je zaškrtnuto políčko jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="e438e-113">The <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> property indicates whether the read-only check box is selected.</span></span> <span data-ttu-id="e438e-114">Nakonec <xref:System.Windows.Forms.FileDialog.Filter%2A> vlastnost nastaví aktuální soubor název řetězec filtru, která určuje možnosti, které se zobrazují v poli "Soubory typu" v dialogovém okně.</span><span class="sxs-lookup"><span data-stu-id="e438e-114">Finally, the <xref:System.Windows.Forms.FileDialog.Filter%2A> property sets the current file name filter string, which determines the choices that appear in the "Files of type" box in the dialog box.</span></span>  
  
 <span data-ttu-id="e438e-115">Při jejím přidání do formuláře <xref:System.Windows.Forms.OpenFileDialog> součást se zobrazí na hlavním panelu v dolní části Návrhář formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="e438e-115">When it is added to a form, the <xref:System.Windows.Forms.OpenFileDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e438e-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="e438e-116">See Also</span></span>  
 <xref:System.Windows.Forms.OpenFileDialog>  
 [<span data-ttu-id="e438e-117">Komponenta OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="e438e-117">OpenFileDialog Component</span></span>](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)
