---
title: Přehled komponenty FontDialog
ms.date: 03/30/2017
f1_keywords:
- FontDialog
helpviewer_keywords:
- Font dialog box [Windows Forms], Windows Forms
- Font dialog box
- FontDialog component [Windows Forms], about FontDialog component
ms.assetid: daf46e57-1b4b-4b7a-bad0-b50ca7ba75dc
ms.openlocfilehash: 664b756dc068ca283e4f43edbdd0f3266f5d1142
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745701"
---
# <a name="fontdialog-component-overview-windows-forms"></a><span data-ttu-id="23995-102">FontDialog – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="23995-102">FontDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="23995-103">Komponenta model Windows Forms <xref:System.Windows.Forms.FontDialog> je předem nakonfigurovaným dialogovým oknem, které je standardním dialogovým oknem **písma** systému Windows, které slouží k vystavení písem, která jsou aktuálně nainstalována v systému.</span><span class="sxs-lookup"><span data-stu-id="23995-103">The Windows Forms <xref:System.Windows.Forms.FontDialog> component is a pre-configured dialog box, which is the standard Windows **Font** dialog box used to expose the fonts that are currently installed on the system.</span></span> <span data-ttu-id="23995-104">Použijte ho v rámci aplikace pro Windows jako jednoduché řešení pro výběr písem namísto konfigurace vlastního dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="23995-104">Use it within your Windows-based application as a simple solution for font selection in lieu of configuring your own dialog box.</span></span>  
  
 <span data-ttu-id="23995-105">Ve výchozím nastavení se v dialogovém okně zobrazují pole pro písmo, styl písma a velikost; zaškrtávací políčka pro efekty jako přeškrtnutí a podtržení; rozevírací seznam pro skript; a ukázku, jak se písmo zobrazí.</span><span class="sxs-lookup"><span data-stu-id="23995-105">By default, the dialog box shows list boxes for Font, Font style, and Size; check boxes for effects like Strikeout and Underline; a drop-down list for Script; and a sample of how the font will appear.</span></span> <span data-ttu-id="23995-106">(Skript odkazuje na jiné znakové skripty, které jsou k dispozici pro dané písmo, například hebrejština nebo japonština.) Chcete-li zobrazit dialogové okno písmo, zavolejte metodu <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="23995-106">(Script refers to different character scripts that are available for a given font, for example, Hebrew or Japanese.) To display the font dialog box, call the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="23995-107">Klíčové vlastnosti</span><span class="sxs-lookup"><span data-stu-id="23995-107">Key Properties</span></span>  
 <span data-ttu-id="23995-108">Komponenta má několik vlastností, které konfigurují její vzhled.</span><span class="sxs-lookup"><span data-stu-id="23995-108">The component has a number of properties that configure its appearance.</span></span> <span data-ttu-id="23995-109">Vlastnosti, které nastavují výběry dialogových oken, jsou <xref:System.Windows.Forms.FontDialog.Font%2A> a <xref:System.Windows.Forms.FontDialog.Color%2A>.</span><span class="sxs-lookup"><span data-stu-id="23995-109">The properties that set the dialog-box selections are <xref:System.Windows.Forms.FontDialog.Font%2A> and <xref:System.Windows.Forms.FontDialog.Color%2A>.</span></span> <span data-ttu-id="23995-110">Vlastnost <xref:System.Windows.Forms.FontDialog.Font%2A> nastaví písmo, styl, velikost, skript a efekty; například `Arial, 10pt, style=Italic, Strikeout`.</span><span class="sxs-lookup"><span data-stu-id="23995-110">The <xref:System.Windows.Forms.FontDialog.Font%2A> property sets the font, style, size, script, and effects; for example, `Arial, 10pt, style=Italic, Strikeout`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23995-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="23995-111">See also</span></span>

- <xref:System.Windows.Forms.FontDialog>
- [<span data-ttu-id="23995-112">Komponenta FontDialog</span><span class="sxs-lookup"><span data-stu-id="23995-112">FontDialog Component</span></span>](fontdialog-component-windows-forms.md)
