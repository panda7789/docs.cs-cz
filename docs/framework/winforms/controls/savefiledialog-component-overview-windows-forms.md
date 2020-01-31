---
title: Přehled komponenty SaveFileDialog
ms.date: 03/30/2017
f1_keywords:
- SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
ms.openlocfilehash: 7609c29b7e932ecee7dc8a289617094bd8d480e2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743096"
---
# <a name="savefiledialog-component-overview-windows-forms"></a><span data-ttu-id="18c1c-102">SaveFileDialog – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="18c1c-102">SaveFileDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="18c1c-103">Součást model Windows Forms <xref:System.Windows.Forms.SaveFileDialog> je předem nakonfigurovaným dialogovým oknem.</span><span class="sxs-lookup"><span data-stu-id="18c1c-103">The Windows Forms <xref:System.Windows.Forms.SaveFileDialog> component is a pre-configured dialog box.</span></span> <span data-ttu-id="18c1c-104">Je stejný jako dialogové okno standardní **Uložit soubor** používaný v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="18c1c-104">It is the same as the standard **Save File** dialog box used by Windows.</span></span> <span data-ttu-id="18c1c-105">Dědí z třídy <xref:System.Windows.Forms.CommonDialog>.</span><span class="sxs-lookup"><span data-stu-id="18c1c-105">It inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>

## <a name="working-with-the-savefiledialog-component"></a><span data-ttu-id="18c1c-106">Práce s komponentou SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="18c1c-106">Working with the SaveFileDialog Component</span></span>

<span data-ttu-id="18c1c-107">Použijte ji jako jednoduché řešení, které umožňuje uživatelům ukládat soubory místo konfigurace vlastního dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="18c1c-107">Use it as a simple solution for enabling users to save files instead of configuring your own dialog box.</span></span> <span data-ttu-id="18c1c-108">Když se spoléháte na standardní dialogová okna systému Windows, jsou základní funkce aplikací, které vytvoříte, okamžitě známé uživatelům.</span><span class="sxs-lookup"><span data-stu-id="18c1c-108">By relying on standard Windows dialog boxes, the basic functionality of applications you create is immediately familiar to users.</span></span> <span data-ttu-id="18c1c-109">Mějte ale na paměti, že při použití komponenty <xref:System.Windows.Forms.SaveFileDialog> musíte napsat vlastní logiku pro ukládání souborů.</span><span class="sxs-lookup"><span data-stu-id="18c1c-109">Be aware, however, that when using the <xref:System.Windows.Forms.SaveFileDialog> component, you must write your own file-saving logic.</span></span>

<span data-ttu-id="18c1c-110">Můžete použít metodu <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> k zobrazení dialogového okna v době běhu.</span><span class="sxs-lookup"><span data-stu-id="18c1c-110">You can use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box at run time.</span></span> <span data-ttu-id="18c1c-111">Pomocí metody <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> můžete otevřít soubor v režimu pro čtení i zápis.</span><span class="sxs-lookup"><span data-stu-id="18c1c-111">You can open a file in read/write mode using the <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method.</span></span>

<span data-ttu-id="18c1c-112">Při přidání do formuláře se komponenta <xref:System.Windows.Forms.SaveFileDialog> zobrazí v zásobníku v dolní části Návrhář formulářů v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="18c1c-112">When it is added to a form, the <xref:System.Windows.Forms.SaveFileDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="18c1c-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="18c1c-113">See also</span></span>

- <xref:System.Windows.Forms.SaveFileDialog>
- [<span data-ttu-id="18c1c-114">Komponenta SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="18c1c-114">SaveFileDialog Component</span></span>](savefiledialog-component-windows-forms.md)
