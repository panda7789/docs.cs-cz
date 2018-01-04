---
title: "Chování AutoSize v ovládacím prvku TableLayoutPanel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AutoSize property [Windows Forms], tableLayoutPanel control
- controls [Windows Forms], sizing
- localizing forms
- layout [Windows Forms], AutoSize
- sizing [Windows Forms], automatic
- TableLayoutPanel control [Windows Forms], AutoSize behavior
- automatic sizing
- AutoSizeMode property
ms.assetid: 9233e0c3-2fa6-405e-8701-959479b1250e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 06bd0686b31b52ccb8580a545910339d2e2cd5bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="autosize-behavior-in-the-tablelayoutpanel-control"></a><span data-ttu-id="ac345-102">Chování AutoSize v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="ac345-102">AutoSize Behavior in the TableLayoutPanel Control</span></span>
## <a name="distinct-autosize-behaviors"></a><span data-ttu-id="ac345-103">Chování odlišné AutoSize</span><span class="sxs-lookup"><span data-stu-id="ac345-103">Distinct AutoSize Behaviors</span></span>  
 <span data-ttu-id="ac345-104"><xref:System.Windows.Forms.TableLayoutPanel> Řízení podporuje chování Automatická změna velikosti následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="ac345-104">The <xref:System.Windows.Forms.TableLayoutPanel> control supports automatic sizing behavior in the following ways:</span></span>  
  
-   <span data-ttu-id="ac345-105">Prostřednictvím <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost;</span><span class="sxs-lookup"><span data-stu-id="ac345-105">Through the <xref:System.Windows.Forms.Control.AutoSize%2A> property;</span></span>  
  
-   <span data-ttu-id="ac345-106">Prostřednictvím <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> vlastnost <xref:System.Windows.Forms.TableLayoutPanel> styly ovládacího prvku řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="ac345-106">Through the <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> property on the <xref:System.Windows.Forms.TableLayoutPanel> control’s column and row styles.</span></span>  
  
### <a name="the-autosize-property-with-row-and-column-styles"></a><span data-ttu-id="ac345-107">S vlastností AutoSize s řádků a sloupců styly</span><span class="sxs-lookup"><span data-stu-id="ac345-107">The AutoSize Property with Row and Column Styles</span></span>  
 <span data-ttu-id="ac345-108">Následující tabulka popisuje interakce mezi <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost a <xref:System.Windows.Forms.TableLayoutPanel> styly ovládacího prvku řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="ac345-108">The following table describes the interaction between the <xref:System.Windows.Forms.Control.AutoSize%2A> property and the <xref:System.Windows.Forms.TableLayoutPanel> control’s column and row styles.</span></span>  
  
|<span data-ttu-id="ac345-109">Nastavení AutoSize</span><span class="sxs-lookup"><span data-stu-id="ac345-109">AutoSize setting</span></span>|<span data-ttu-id="ac345-110">Styl interakce</span><span class="sxs-lookup"><span data-stu-id="ac345-110">Style interaction</span></span>|  
|----------------------|-----------------------|  
|`false`|<span data-ttu-id="ac345-111"><xref:System.Windows.Forms.TableLayoutPanel> Řízení pokračuje zleva doprava a přiděluje místo na sloupec nebo řádek nebo v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="ac345-111">The <xref:System.Windows.Forms.TableLayoutPanel> control proceeds from left to right, and allocates space for the column or row or in the following order.</span></span><br /><br /> <span data-ttu-id="ac345-112">1.  Pokud <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> je nastavena na <xref:System.Windows.Forms.SizeType.Absolute>, počet pixelů určeného <xref:System.Windows.Forms.ColumnStyle.Width%2A> nebo <xref:System.Windows.Forms.RowStyle.Height%2A> je přidělen.</span><span class="sxs-lookup"><span data-stu-id="ac345-112">1.  If the <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> property is set to <xref:System.Windows.Forms.SizeType.Absolute>, the number of pixels specified by <xref:System.Windows.Forms.ColumnStyle.Width%2A> or <xref:System.Windows.Forms.RowStyle.Height%2A> is allocated.</span></span><br /><span data-ttu-id="ac345-113">2.  Pokud <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> je nastavena na <xref:System.Windows.Forms.SizeType.AutoSize>, vrácený podřízeného ovládacího prvku v pixelech <xref:System.Windows.Forms.Control.GetPreferredSize%2A> metoda je přidělen.</span><span class="sxs-lookup"><span data-stu-id="ac345-113">2.  If the <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> property is set to <xref:System.Windows.Forms.SizeType.AutoSize>, the number of pixels returned by the child control’s <xref:System.Windows.Forms.Control.GetPreferredSize%2A> method is allocated.</span></span><br /><span data-ttu-id="ac345-114">3.  Po místa pro všechny <xref:System.Windows.Forms.SizeType.Absolute> a <xref:System.Windows.Forms.SizeType.AutoSize> sloupců a řádků je přidělen, všechny sloupce nebo řádky s <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> nastavena na <xref:System.Windows.Forms.SizeType.Percent> jsou používány k přidělení úměrně zbývající volné místo</span><span class="sxs-lookup"><span data-stu-id="ac345-114">3.  After space for all <xref:System.Windows.Forms.SizeType.Absolute> and <xref:System.Windows.Forms.SizeType.AutoSize> columns or rows is allocated, any columns or rows with <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> set to <xref:System.Windows.Forms.SizeType.Percent> are used to proportionally allocate the remaining free space</span></span>|  
|`true`|<span data-ttu-id="ac345-115">Podobně jako předchozí interakci s tou výjimkou, který <xref:System.Windows.Forms.SizeType.Percent> sloupců a řádků získat aspekt Automatická změna velikosti.</span><span class="sxs-lookup"><span data-stu-id="ac345-115">Similar to the previous interaction, with the exception that <xref:System.Windows.Forms.SizeType.Percent> columns or rows acquire an automatic sizing aspect.</span></span><br /><br /> <span data-ttu-id="ac345-116"><xref:System.Windows.Forms.TableLayoutPanel> Řízení rozšíří sloupce nebo řádku k vytvoření dostatkem volného místa, tak, aby žádný sloupec nebo řádek s <xref:System.Windows.Forms.SizeType.Percent> stylů klipy její obsah.</span><span class="sxs-lookup"><span data-stu-id="ac345-116">The <xref:System.Windows.Forms.TableLayoutPanel> control expands the column or row to create adequate free space, so that no column or row with <xref:System.Windows.Forms.SizeType.Percent> styling clips its contents.</span></span> <span data-ttu-id="ac345-117"><xref:System.Windows.Forms.TableLayoutPanel> Řízení přiděluje nový prostor úměrně souladu se <xref:System.Windows.Forms.ColumnStyle.Width%2A> nebo <xref:System.Windows.Forms.RowStyle.Height%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ac345-117">The <xref:System.Windows.Forms.TableLayoutPanel> control allocates the new space proportionally according to the <xref:System.Windows.Forms.ColumnStyle.Width%2A> or <xref:System.Windows.Forms.RowStyle.Height%2A> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ac345-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="ac345-118">See Also</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [<span data-ttu-id="ac345-119">Přehled ovládacího prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="ac345-119">TableLayoutPanel Control Overview</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-overview.md)
