---
title: OpenFileDialog – přehled komponenty (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- OpenFileDialog
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], about OpenFileDialog
- Open File dialog box [Windows Forms], displaying in Windows Forms
ms.assetid: cd717300-46b6-4f82-8207-b218fa7fa407
ms.openlocfilehash: ec275a5923d332d23205c79442fa23bc6e402e3f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59147332"
---
# <a name="openfiledialog-component-overview-windows-forms"></a><span data-ttu-id="2f261-102">OpenFileDialog – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="2f261-102">OpenFileDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="2f261-103">Windows Forms <xref:System.Windows.Forms.OpenFileDialog> komponenta je předem nakonfigurované dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="2f261-103">The Windows Forms <xref:System.Windows.Forms.OpenFileDialog> component is a pre-configured dialog box.</span></span> <span data-ttu-id="2f261-104">Jde o stejný **otevřít soubor** dialogové okno vystavené operačního systému Windows.</span><span class="sxs-lookup"><span data-stu-id="2f261-104">It is the same **Open File** dialog box exposed by the Windows operating system.</span></span> <span data-ttu-id="2f261-105">Dědí z <xref:System.Windows.Forms.CommonDialog> třídy.</span><span class="sxs-lookup"><span data-stu-id="2f261-105">It inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>  
  
## <a name="using-this-component"></a><span data-ttu-id="2f261-106">Pomocí této součásti</span><span class="sxs-lookup"><span data-stu-id="2f261-106">Using this Component</span></span>  
 <span data-ttu-id="2f261-107">Použití této komponenty v rámci vaší aplikace pro systém Windows jako jednoduchým řešením pro výběr souboru namísto dialogové okno Vlastní konfigurace.</span><span class="sxs-lookup"><span data-stu-id="2f261-107">Use this component within your Windows-based application as a simple solution for file selection in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="2f261-108">Pomocí standardní dialogová okna Windows, můžete vytvořit aplikace, jejichž základní funkce je okamžitě uživatelé znají.</span><span class="sxs-lookup"><span data-stu-id="2f261-108">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span> <span data-ttu-id="2f261-109">Mějte na paměti, ale, že pomocí <xref:System.Windows.Forms.OpenFileDialog> komponenty, je nutné napsat vlastní logikou otevření souboru.</span><span class="sxs-lookup"><span data-stu-id="2f261-109">Be aware, however, that when using the <xref:System.Windows.Forms.OpenFileDialog> component, you must write your own file-opening logic.</span></span>  
  
 <span data-ttu-id="2f261-110">Použití <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu pro zobrazení dialogového okna v době běhu.</span><span class="sxs-lookup"><span data-stu-id="2f261-110">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog at run time.</span></span> <span data-ttu-id="2f261-111">Můžete umožnit uživatelům si vybrat víc souborů otevíraly pomocí <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2f261-111">You can enable users to multi-select files to be opened with the <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A> property.</span></span> <span data-ttu-id="2f261-112">Kromě toho můžete použít <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> a určí, pokud se v dialogovém okně zobrazí zaškrtávací políčko jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="2f261-112">Additionally, you can use the <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> property to determine if a read-only check box appears in the dialog box.</span></span> <span data-ttu-id="2f261-113"><xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> Vlastnost určuje, zda je zaškrtnuto zaškrtávací políčko jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="2f261-113">The <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> property indicates whether the read-only check box is selected.</span></span> <span data-ttu-id="2f261-114">Nakonec <xref:System.Windows.Forms.FileDialog.Filter%2A> nastaví aktuální soubor název řetězec filtru, který určuje možnosti, které se zobrazí v poli "Soubory typu" v dialogovém okně Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2f261-114">Finally, the <xref:System.Windows.Forms.FileDialog.Filter%2A> property sets the current file name filter string, which determines the choices that appear in the "Files of type" box in the dialog box.</span></span>  
  
 <span data-ttu-id="2f261-115">Když se přidá do formuláře, <xref:System.Windows.Forms.OpenFileDialog> součást se zobrazí v hlavním panelu v dolní části Návrháře formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="2f261-115">When it is added to a form, the <xref:System.Windows.Forms.OpenFileDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f261-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2f261-116">See also</span></span>

- <xref:System.Windows.Forms.OpenFileDialog>
- [<span data-ttu-id="2f261-117">Komponenta OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="2f261-117">OpenFileDialog Component</span></span>](openfiledialog-component-windows-forms.md)
