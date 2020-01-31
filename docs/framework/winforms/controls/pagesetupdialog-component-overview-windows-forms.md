---
title: PageSetupDialog – přehled komponenty
ms.date: 03/30/2017
f1_keywords:
- PageSetupDialog
helpviewer_keywords:
- Page Setup dialog box [Windows Forms], displaying
- PageSetupDialog component
ms.assetid: 791caacb-a5ca-4fca-bad9-1a5721ad697c
ms.openlocfilehash: a891cb8cc77007d7591d41461c94f61c077eb300
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744343"
---
# <a name="pagesetupdialog-component-overview-windows-forms"></a><span data-ttu-id="e3feb-102">PageSetupDialog – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="e3feb-102">PageSetupDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="e3feb-103">Součást model Windows Forms <xref:System.Windows.Forms.PageSetupDialog> je předem nakonfigurovaným dialogovým oknem použitým k nastavení podrobností o tisku v aplikacích založených na systému Windows.</span><span class="sxs-lookup"><span data-stu-id="e3feb-103">The Windows Forms <xref:System.Windows.Forms.PageSetupDialog> component is a pre-configured dialog box used to set page details for printing in Windows-based applications.</span></span> <span data-ttu-id="e3feb-104">Použijte ji v aplikaci pro Windows jako jednoduché řešení pro uživatele, aby se místo konfigurace vlastního dialogového okna nastavily předvolby stránky.</span><span class="sxs-lookup"><span data-stu-id="e3feb-104">Use it within your Windows-based application as a simple solution for users to set page preferences in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="e3feb-105">Uživatelům můžete povolit nastavení úprav ohraničení a okrajů, záhlaví a zápatí a orientace na výšku nebo na šířku.</span><span class="sxs-lookup"><span data-stu-id="e3feb-105">You can enable users to set border and margin adjustments, headers and footers, and portrait or landscape orientation.</span></span> <span data-ttu-id="e3feb-106">Když se spoléháte na standardní dialogová okna systému Windows, vytvoříte aplikace, jejichž základní funkce je pro uživatele okamžitě známa.</span><span class="sxs-lookup"><span data-stu-id="e3feb-106">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span>

## <a name="key-properties-and-methods"></a><span data-ttu-id="e3feb-107">Klíčové vlastnosti a metody</span><span class="sxs-lookup"><span data-stu-id="e3feb-107">Key Properties and Methods</span></span>

<span data-ttu-id="e3feb-108">Použijte metodu <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> k zobrazení dialogového okna v době běhu.</span><span class="sxs-lookup"><span data-stu-id="e3feb-108">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog at run time.</span></span> <span data-ttu-id="e3feb-109">Tato součást obsahuje vlastnosti, které můžete nastavit, které se vztahují k jedné stránce (<xref:System.Drawing.Printing.PrintDocument> třídě) nebo k libovolnému dokumentu (<xref:System.Drawing.Printing.PageSettings> třídě).</span><span class="sxs-lookup"><span data-stu-id="e3feb-109">This component has properties you can set that relate to either a single page (<xref:System.Drawing.Printing.PrintDocument> class) or any document (<xref:System.Drawing.Printing.PageSettings> class).</span></span> <span data-ttu-id="e3feb-110">Kromě toho lze komponentu <xref:System.Windows.Forms.PageSetupDialog> použít k určení konkrétního nastavení tiskárny, která jsou uložena ve třídě <xref:System.Drawing.Printing.PrinterSettings>.</span><span class="sxs-lookup"><span data-stu-id="e3feb-110">Additionally, the <xref:System.Windows.Forms.PageSetupDialog> component can be used to determine specific printer settings, which are stored in the <xref:System.Drawing.Printing.PrinterSettings> class.</span></span>

<span data-ttu-id="e3feb-111">Při přidání do formuláře se komponenta <xref:System.Windows.Forms.PageSetupDialog> zobrazí v zásobníku v dolní části Návrhář formulářů v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e3feb-111">When it is added to a form, the <xref:System.Windows.Forms.PageSetupDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="e3feb-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e3feb-112">See also</span></span>

- <xref:System.Windows.Forms.PageSetupDialog>
- [<span data-ttu-id="e3feb-113">Komponenta PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="e3feb-113">PageSetupDialog Component</span></span>](pagesetupdialog-component-windows-forms.md)
