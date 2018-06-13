---
title: FontDialog – přehled komponenty (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- FontDialog
helpviewer_keywords:
- Font dialog box [Windows Forms], Windows Forms
- Font dialog box
- FontDialog component [Windows Forms], about FontDialog component
ms.assetid: daf46e57-1b4b-4b7a-bad0-b50ca7ba75dc
ms.openlocfilehash: 3a4707ffe471161988d0526ce0908b37299f3e07
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526875"
---
# <a name="fontdialog-component-overview-windows-forms"></a><span data-ttu-id="55f4d-102">FontDialog – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="55f4d-102">FontDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="55f4d-103">Windows Forms <xref:System.Windows.Forms.FontDialog> součást je předem nakonfigurovaný dialogové okno, což je standardní Windows **písma** dialogové okno používá ke zveřejnění písma, které jsou aktuálně nainstalovány v systému.</span><span class="sxs-lookup"><span data-stu-id="55f4d-103">The Windows Forms <xref:System.Windows.Forms.FontDialog> component is a pre-configured dialog box, which is the standard Windows **Font** dialog box used to expose the fonts that are currently installed on the system.</span></span> <span data-ttu-id="55f4d-104">Použití v rámci aplikace systému Windows jako jednoduchým řešením pro výběr písma místo dialogové okno Vlastní konfigurace.</span><span class="sxs-lookup"><span data-stu-id="55f4d-104">Use it within your Windows-based application as a simple solution for font selection in lieu of configuring your own dialog box.</span></span>  
  
 <span data-ttu-id="55f4d-105">Ve výchozím nastavení, dialogové okno zobrazí seznamy pro písmo, styl písma a velikost; Zaškrtávací políčka důsledky jako přeškrtnutí a podtržení; rozevírací seznam pro skript; a ukázka vzhled písma.</span><span class="sxs-lookup"><span data-stu-id="55f4d-105">By default, the dialog box shows list boxes for Font, Font style, and Size; check boxes for effects like Strikeout and Underline; a drop-down list for Script; and a sample of how the font will appear.</span></span> <span data-ttu-id="55f4d-106">(Skript odkazuje jiný znak skripty, které jsou k dispozici pro dané písmo, například hebrejština nebo japonština.) Chcete-li zobrazit dialogové okno písmo, zavolejte <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="55f4d-106">(Script refers to different character scripts that are available for a given font, for example, Hebrew or Japanese.) To display the font dialog box, call the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="55f4d-107">Klíčové vlastnosti</span><span class="sxs-lookup"><span data-stu-id="55f4d-107">Key Properties</span></span>  
 <span data-ttu-id="55f4d-108">Součást má několik vlastností, které konfigurují její vzhled.</span><span class="sxs-lookup"><span data-stu-id="55f4d-108">The component has a number of properties that configure its appearance.</span></span> <span data-ttu-id="55f4d-109">Vlastnosti, které nastavit možnosti – dialogové okno se <xref:System.Windows.Forms.FontDialog.Font%2A> a <xref:System.Windows.Forms.FontDialog.Color%2A>.</span><span class="sxs-lookup"><span data-stu-id="55f4d-109">The properties that set the dialog-box selections are <xref:System.Windows.Forms.FontDialog.Font%2A> and <xref:System.Windows.Forms.FontDialog.Color%2A>.</span></span> <span data-ttu-id="55f4d-110"><xref:System.Windows.Forms.FontDialog.Font%2A> Vlastnost nastaví písmo, styl, velikost, skript a efekty; například `Arial, 10pt, style=Italic, Strikeout`.</span><span class="sxs-lookup"><span data-stu-id="55f4d-110">The <xref:System.Windows.Forms.FontDialog.Font%2A> property sets the font, style, size, script, and effects; for example, `Arial, 10pt, style=Italic, Strikeout`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55f4d-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="55f4d-111">See Also</span></span>  
 <xref:System.Windows.Forms.FontDialog>  
 [<span data-ttu-id="55f4d-112">Komponenta FontDialog</span><span class="sxs-lookup"><span data-stu-id="55f4d-112">FontDialog Component</span></span>](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md)
