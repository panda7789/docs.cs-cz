---
title: Přehled komponenty OpenFileDialog
ms.date: 03/30/2017
f1_keywords:
- OpenFileDialog
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], about OpenFileDialog
- Open File dialog box [Windows Forms], displaying in Windows Forms
ms.assetid: cd717300-46b6-4f82-8207-b218fa7fa407
ms.openlocfilehash: c519b373150a49ee41dbb0c503f7d5a4862477d5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728433"
---
# <a name="openfiledialog-component-overview-windows-forms"></a><span data-ttu-id="fafed-102">OpenFileDialog – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="fafed-102">OpenFileDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="fafed-103">Součást model Windows Forms <xref:System.Windows.Forms.OpenFileDialog> je předem nakonfigurovaným dialogovým oknem.</span><span class="sxs-lookup"><span data-stu-id="fafed-103">The Windows Forms <xref:System.Windows.Forms.OpenFileDialog> component is a pre-configured dialog box.</span></span> <span data-ttu-id="fafed-104">Jedná se o stejný dialog **otevřeného souboru** , který je vystavený operačním systémem Windows.</span><span class="sxs-lookup"><span data-stu-id="fafed-104">It is the same **Open File** dialog box exposed by the Windows operating system.</span></span> <span data-ttu-id="fafed-105">Dědí z třídy <xref:System.Windows.Forms.CommonDialog>.</span><span class="sxs-lookup"><span data-stu-id="fafed-105">It inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>

## <a name="use-this-component"></a><span data-ttu-id="fafed-106">Použít tuto součást</span><span class="sxs-lookup"><span data-stu-id="fafed-106">Use this component</span></span>

<span data-ttu-id="fafed-107">Tuto součást použijte v aplikaci pro Windows jako jednoduché řešení pro výběr souborů namísto konfigurace vlastního dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="fafed-107">Use this component within your Windows-based application as a simple solution for file selection in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="fafed-108">Když se spoléháte na standardní dialogová okna systému Windows, vytvoříte aplikace, jejichž základní funkce je pro uživatele okamžitě známa.</span><span class="sxs-lookup"><span data-stu-id="fafed-108">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span> <span data-ttu-id="fafed-109">Mějte ale na paměti, že při použití <xref:System.Windows.Forms.OpenFileDialog> komponenty musíte napsat vlastní logiku otevírání souborů.</span><span class="sxs-lookup"><span data-stu-id="fafed-109">Be aware, however, that when using the <xref:System.Windows.Forms.OpenFileDialog> component, you must write your own file-opening logic.</span></span>

<span data-ttu-id="fafed-110">Použijte metodu <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> k zobrazení dialogového okna v době běhu.</span><span class="sxs-lookup"><span data-stu-id="fafed-110">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog at run time.</span></span> <span data-ttu-id="fafed-111">Uživatelům můžete umožnit otevírání souborů s více výběry s vlastností <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A>.</span><span class="sxs-lookup"><span data-stu-id="fafed-111">You can enable users to multi-select files to be opened with the <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A> property.</span></span> <span data-ttu-id="fafed-112">Kromě toho můžete použít vlastnost <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> k určení, zda se v dialogovém okně zobrazí zaškrtávací políčko jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="fafed-112">Additionally, you can use the <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> property to determine if a read-only check box appears in the dialog box.</span></span> <span data-ttu-id="fafed-113">Vlastnost <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> určuje, zda je zaškrtnuto políčko jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="fafed-113">The <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> property indicates whether the read-only check box is selected.</span></span> <span data-ttu-id="fafed-114">Nakonec vlastnost <xref:System.Windows.Forms.FileDialog.Filter%2A> nastaví aktuální řetězec filtru názvu souboru, který určuje možnosti, které se zobrazí v poli "soubory typu" v dialogovém okně.</span><span class="sxs-lookup"><span data-stu-id="fafed-114">Finally, the <xref:System.Windows.Forms.FileDialog.Filter%2A> property sets the current file name filter string, which determines the choices that appear in the "Files of type" box in the dialog box.</span></span>

<span data-ttu-id="fafed-115">Při přidání do formuláře se komponenta <xref:System.Windows.Forms.OpenFileDialog> zobrazí v zásobníku v dolní části Návrhář formulářů v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fafed-115">When it is added to a form, the <xref:System.Windows.Forms.OpenFileDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="fafed-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="fafed-116">See also</span></span>

- <xref:System.Windows.Forms.OpenFileDialog>
- [<span data-ttu-id="fafed-117">Komponenta OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="fafed-117">OpenFileDialog Component</span></span>](openfiledialog-component-windows-forms.md)
