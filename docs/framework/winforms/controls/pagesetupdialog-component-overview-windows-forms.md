---
title: PageSetupDialog – přehled komponenty (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- PageSetupDialog
helpviewer_keywords:
- Page Setup dialog box [Windows Forms], displaying
- PageSetupDialog component
ms.assetid: 791caacb-a5ca-4fca-bad9-1a5721ad697c
ms.openlocfilehash: 989183b6152dfccb6167d89433317cea596d83c5
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211745"
---
# <a name="pagesetupdialog-component-overview-windows-forms"></a><span data-ttu-id="b6410-102">PageSetupDialog – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="b6410-102">PageSetupDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="b6410-103">Windows Forms <xref:System.Windows.Forms.PageSetupDialog> komponenta je předem nakonfigurované dialogové okno používá k nastavení stránky podrobností pro tisk v aplikacích založených na Windows.</span><span class="sxs-lookup"><span data-stu-id="b6410-103">The Windows Forms <xref:System.Windows.Forms.PageSetupDialog> component is a pre-configured dialog box used to set page details for printing in Windows-based applications.</span></span> <span data-ttu-id="b6410-104">Použití v rámci aplikace založené na Windows jako jednoduché řešení pro uživatele nastavit předvolby stránky namísto dialogové okno Vlastní konfigurace.</span><span class="sxs-lookup"><span data-stu-id="b6410-104">Use it within your Windows-based application as a simple solution for users to set page preferences in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="b6410-105">Můžete povolit uživatelům nastavit okraj a okraj úpravy, záhlaví a zápatí a orientaci na výšku nebo na šířku.</span><span class="sxs-lookup"><span data-stu-id="b6410-105">You can enable users to set border and margin adjustments, headers and footers, and portrait or landscape orientation.</span></span> <span data-ttu-id="b6410-106">Pomocí standardní dialogová okna Windows, můžete vytvořit aplikace, jejichž základní funkce je okamžitě uživatelé znají.</span><span class="sxs-lookup"><span data-stu-id="b6410-106">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span>

## <a name="key-properties-and-methods"></a><span data-ttu-id="b6410-107">Klíčové vlastnosti a metody</span><span class="sxs-lookup"><span data-stu-id="b6410-107">Key Properties and Methods</span></span>

<span data-ttu-id="b6410-108">Použití <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu pro zobrazení dialogového okna v době běhu.</span><span class="sxs-lookup"><span data-stu-id="b6410-108">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog at run time.</span></span> <span data-ttu-id="b6410-109">Tato součást oznámila vlastnosti můžete nastavit, které se týkají buď jednu stránku (<xref:System.Drawing.Printing.PrintDocument> třídy) nebo jakýkoliv dokument (<xref:System.Drawing.Printing.PageSettings> třídy).</span><span class="sxs-lookup"><span data-stu-id="b6410-109">This component has properties you can set that relate to either a single page (<xref:System.Drawing.Printing.PrintDocument> class) or any document (<xref:System.Drawing.Printing.PageSettings> class).</span></span> <span data-ttu-id="b6410-110">Kromě toho <xref:System.Windows.Forms.PageSetupDialog> součást je možné určit konkrétní nastavení tiskárny, které jsou uloženy v <xref:System.Drawing.Printing.PrinterSettings> třídy.</span><span class="sxs-lookup"><span data-stu-id="b6410-110">Additionally, the <xref:System.Windows.Forms.PageSetupDialog> component can be used to determine specific printer settings, which are stored in the <xref:System.Drawing.Printing.PrinterSettings> class.</span></span>

<span data-ttu-id="b6410-111">Když se přidá do formuláře, <xref:System.Windows.Forms.PageSetupDialog> součást se zobrazí v hlavním panelu v dolní části Návrháře formulářů Windows v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b6410-111">When it is added to a form, the <xref:System.Windows.Forms.PageSetupDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="b6410-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b6410-112">See also</span></span>

- <xref:System.Windows.Forms.PageSetupDialog>
- [<span data-ttu-id="b6410-113">Komponenta PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="b6410-113">PageSetupDialog Component</span></span>](pagesetupdialog-component-windows-forms.md)
