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
ms.openlocfilehash: 7f140807bf4b42e530302190042e729c59248e7f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789308"
---
# <a name="fontdialog-component-overview-windows-forms"></a><span data-ttu-id="4d79f-102">FontDialog – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="4d79f-102">FontDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="4d79f-103">Windows Forms <xref:System.Windows.Forms.FontDialog> komponenta je předem nakonfigurované dialogovému oknu, což je standardní Windows **písmo** dialogové okno používá k vystavení písma, které jsou nainstalovány v systému.</span><span class="sxs-lookup"><span data-stu-id="4d79f-103">The Windows Forms <xref:System.Windows.Forms.FontDialog> component is a pre-configured dialog box, which is the standard Windows **Font** dialog box used to expose the fonts that are currently installed on the system.</span></span> <span data-ttu-id="4d79f-104">Použití v rámci vaší aplikace založené na Windows jako jednoduchým řešením pro výběr písma namísto dialogové okno Vlastní konfigurace.</span><span class="sxs-lookup"><span data-stu-id="4d79f-104">Use it within your Windows-based application as a simple solution for font selection in lieu of configuring your own dialog box.</span></span>  
  
 <span data-ttu-id="4d79f-105">Ve výchozím nastavení, dialogové okno zobrazuje pole se seznamem pro písmo, styl písma a velikosti. Zaškrtněte políčka pro efekty, jako jsou přeškrtnutí a podtržení; rozevírací seznam pro skript PowerShell workflow a vzorky vzhled písma.</span><span class="sxs-lookup"><span data-stu-id="4d79f-105">By default, the dialog box shows list boxes for Font, Font style, and Size; check boxes for effects like Strikeout and Underline; a drop-down list for Script; and a sample of how the font will appear.</span></span> <span data-ttu-id="4d79f-106">(Skript odkazuje na jiný znak skripty, které jsou k dispozici pro dané písmo, například hebrejštinu a japonština.) Chcete-li zobrazit dialogové okno písmo, zavolejte <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4d79f-106">(Script refers to different character scripts that are available for a given font, for example, Hebrew or Japanese.) To display the font dialog box, call the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="4d79f-107">Vlastnosti klíče</span><span class="sxs-lookup"><span data-stu-id="4d79f-107">Key Properties</span></span>  
 <span data-ttu-id="4d79f-108">Komponenta má několik vlastností, které konfigurace její vzhled.</span><span class="sxs-lookup"><span data-stu-id="4d79f-108">The component has a number of properties that configure its appearance.</span></span> <span data-ttu-id="4d79f-109">Vlastnosti nastavené možnosti dialogového okna jsou <xref:System.Windows.Forms.FontDialog.Font%2A> a <xref:System.Windows.Forms.FontDialog.Color%2A>.</span><span class="sxs-lookup"><span data-stu-id="4d79f-109">The properties that set the dialog-box selections are <xref:System.Windows.Forms.FontDialog.Font%2A> and <xref:System.Windows.Forms.FontDialog.Color%2A>.</span></span> <span data-ttu-id="4d79f-110"><xref:System.Windows.Forms.FontDialog.Font%2A> Vlastnost nastaví písmo, styl, velikost, skriptů a efekty; například `Arial, 10pt, style=Italic, Strikeout`.</span><span class="sxs-lookup"><span data-stu-id="4d79f-110">The <xref:System.Windows.Forms.FontDialog.Font%2A> property sets the font, style, size, script, and effects; for example, `Arial, 10pt, style=Italic, Strikeout`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d79f-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d79f-111">See also</span></span>

- <xref:System.Windows.Forms.FontDialog>
- [<span data-ttu-id="4d79f-112">Komponenta FontDialog</span><span class="sxs-lookup"><span data-stu-id="4d79f-112">FontDialog Component</span></span>](fontdialog-component-windows-forms.md)
