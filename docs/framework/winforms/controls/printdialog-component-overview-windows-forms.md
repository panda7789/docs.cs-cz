---
title: PrintDialog – přehled komponenty (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- PrintDialog
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], about PrintDialog component
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
ms.openlocfilehash: 2478990e3cec00df9a748dbd9875485e5f060ed7
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211759"
---
# <a name="printdialog-component-overview-windows-forms"></a><span data-ttu-id="0dc91-102">PrintDialog – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="0dc91-102">PrintDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="0dc91-103">Windows Forms [PrintDialog](printdialog-component-windows-forms.md) komponenta je předem nakonfigurované dialogové okno umožňuje vybrat tiskárnu, zvolte stránky k tisku a určit další nastavení související s tiskem v aplikacích založených na Windows.</span><span class="sxs-lookup"><span data-stu-id="0dc91-103">The Windows Forms [PrintDialog](printdialog-component-windows-forms.md) component is a pre-configured dialog box used to select a printer, choose the pages to print, and determine other print-related settings in Windows-based applications.</span></span> <span data-ttu-id="0dc91-104">Použijte jako jednoduchým řešením pro tiskárnu a výběr nastavení související s tiskem namísto dialogové okno Vlastní konfigurace.</span><span class="sxs-lookup"><span data-stu-id="0dc91-104">Use it as a simple solution for printer and print-related settings selection in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="0dc91-105">Můžete povolit uživatelům tisknout mnoho částí své dokumenty: vytisknout všechny vybrané stránce rozsah tisku a Tisk výběru.</span><span class="sxs-lookup"><span data-stu-id="0dc91-105">You can enable users to print many parts of their documents: print all, print a selected page range, or print a selection.</span></span> <span data-ttu-id="0dc91-106">Pomocí standardní dialogová okna Windows, můžete vytvořit aplikace, jejichž základní funkce je okamžitě uživatelé znají.</span><span class="sxs-lookup"><span data-stu-id="0dc91-106">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span> <span data-ttu-id="0dc91-107"><xref:System.Windows.Forms.PrintDialog> Komponenta dědí z <xref:System.Windows.Forms.CommonDialog> třídy.</span><span class="sxs-lookup"><span data-stu-id="0dc91-107">The <xref:System.Windows.Forms.PrintDialog> component inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>

## <a name="working-with-the-component"></a><span data-ttu-id="0dc91-108">Práce s komponentou</span><span class="sxs-lookup"><span data-stu-id="0dc91-108">Working with the Component</span></span>

<span data-ttu-id="0dc91-109">Použití <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu pro zobrazení dialogového okna v době běhu.</span><span class="sxs-lookup"><span data-stu-id="0dc91-109">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box at run time.</span></span> <span data-ttu-id="0dc91-110">Tato součást obsahuje vlastnosti, které se týkají buď jedné tiskové úlohy (<xref:System.Drawing.Printing.PrintDocument> třídy) nebo nastavení jednotlivých tiskáren (<xref:System.Drawing.Printing.PrinterSettings> třídy).</span><span class="sxs-lookup"><span data-stu-id="0dc91-110">This component has properties that relate to either a single print job (<xref:System.Drawing.Printing.PrintDocument> class) or the settings of an individual printer (<xref:System.Drawing.Printing.PrinterSettings> class).</span></span> <span data-ttu-id="0dc91-111">Jeden z následujících, pak může sdílet více tiskáren.</span><span class="sxs-lookup"><span data-stu-id="0dc91-111">Either of these, in turn, may be shared by multiple printers.</span></span>

<span data-ttu-id="0dc91-112">Když se přidá do formuláře, <xref:System.Windows.Forms.PrintDialog> součást se zobrazí v hlavním panelu v dolní části Návrháře formulářů Windows v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0dc91-112">When it is added to a form, the <xref:System.Windows.Forms.PrintDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="0dc91-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0dc91-113">See also</span></span>

- <xref:System.Windows.Forms.PrintDialog>
- [<span data-ttu-id="0dc91-114">Komponenta PrintDialog</span><span class="sxs-lookup"><span data-stu-id="0dc91-114">PrintDialog Component</span></span>](printdialog-component-windows-forms.md)
