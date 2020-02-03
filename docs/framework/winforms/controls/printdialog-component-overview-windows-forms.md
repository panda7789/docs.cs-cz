---
title: Přehled komponenty PrintDialog
ms.date: 03/30/2017
f1_keywords:
- PrintDialog
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], about PrintDialog component
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
ms.openlocfilehash: 0ed7f7a1f9770f71b75ae744a056b6943335c852
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728677"
---
# <a name="printdialog-component-overview-windows-forms"></a><span data-ttu-id="b8f33-102">PrintDialog – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="b8f33-102">PrintDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="b8f33-103">Komponenta model Windows Forms [PrintDialog](printdialog-component-windows-forms.md) je předem nakonfigurovaným dialogovým oknem použitým k výběru tiskárny, výběru stránek k tisku a určení dalších nastavení souvisejících s tiskem v aplikacích založených na systému Windows.</span><span class="sxs-lookup"><span data-stu-id="b8f33-103">The Windows Forms [PrintDialog](printdialog-component-windows-forms.md) component is a pre-configured dialog box used to select a printer, choose the pages to print, and determine other print-related settings in Windows-based applications.</span></span> <span data-ttu-id="b8f33-104">Použijte ji jako jednoduché řešení pro výběr nastavení tiskárny a tisku místo konfigurace vlastního dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="b8f33-104">Use it as a simple solution for printer and print-related settings selection in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="b8f33-105">Uživatelům můžete umožnit tisk mnoha částí jejich dokumentů: tisknout vše, vytisknout vybraný rozsah stránky nebo vytisknout výběr.</span><span class="sxs-lookup"><span data-stu-id="b8f33-105">You can enable users to print many parts of their documents: print all, print a selected page range, or print a selection.</span></span> <span data-ttu-id="b8f33-106">Když se spoléháte na standardní dialogová okna systému Windows, vytvoříte aplikace, jejichž základní funkce je pro uživatele okamžitě známa.</span><span class="sxs-lookup"><span data-stu-id="b8f33-106">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span> <span data-ttu-id="b8f33-107">Komponenta <xref:System.Windows.Forms.PrintDialog> dědí z <xref:System.Windows.Forms.CommonDialog> třídy.</span><span class="sxs-lookup"><span data-stu-id="b8f33-107">The <xref:System.Windows.Forms.PrintDialog> component inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>

## <a name="working-with-the-component"></a><span data-ttu-id="b8f33-108">Práce s komponentou</span><span class="sxs-lookup"><span data-stu-id="b8f33-108">Working with the Component</span></span>

<span data-ttu-id="b8f33-109">Použijte metodu <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> k zobrazení dialogového okna v době běhu.</span><span class="sxs-lookup"><span data-stu-id="b8f33-109">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box at run time.</span></span> <span data-ttu-id="b8f33-110">Tato součást obsahuje vlastnosti, které se vztahují buď na jednu tiskovou úlohu (<xref:System.Drawing.Printing.PrintDocument> třídy), nebo na nastavení jednotlivých tiskáren (<xref:System.Drawing.Printing.PrinterSettings> třídy).</span><span class="sxs-lookup"><span data-stu-id="b8f33-110">This component has properties that relate to either a single print job (<xref:System.Drawing.Printing.PrintDocument> class) or the settings of an individual printer (<xref:System.Drawing.Printing.PrinterSettings> class).</span></span> <span data-ttu-id="b8f33-111">Jedna z těchto z nich může být sdílena několika tiskárnami.</span><span class="sxs-lookup"><span data-stu-id="b8f33-111">Either of these, in turn, may be shared by multiple printers.</span></span>

<span data-ttu-id="b8f33-112">Při přidání do formuláře se komponenta <xref:System.Windows.Forms.PrintDialog> zobrazí v zásobníku v dolní části Návrhář formulářů v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b8f33-112">When it is added to a form, the <xref:System.Windows.Forms.PrintDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="b8f33-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="b8f33-113">See also</span></span>

- <xref:System.Windows.Forms.PrintDialog>
- [<span data-ttu-id="b8f33-114">Komponenta PrintDialog</span><span class="sxs-lookup"><span data-stu-id="b8f33-114">PrintDialog Component</span></span>](printdialog-component-windows-forms.md)
