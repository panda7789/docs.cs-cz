---
title: Chování AutoSize v ovládacím prvku TableLayoutPanel
ms.date: 03/30/2017
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
ms.openlocfilehash: 466edeee5f45ec72ef265ef4855049c7852641b0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164967"
---
# <a name="autosize-behavior-in-the-tablelayoutpanel-control"></a><span data-ttu-id="c9bb8-102">Chování AutoSize v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="c9bb8-102">AutoSize Behavior in the TableLayoutPanel Control</span></span>
## <a name="distinct-autosize-behaviors"></a><span data-ttu-id="c9bb8-103">Chování DISTINCT AutoSize</span><span class="sxs-lookup"><span data-stu-id="c9bb8-103">Distinct AutoSize Behaviors</span></span>  
 <span data-ttu-id="c9bb8-104"><xref:System.Windows.Forms.TableLayoutPanel> Ovládací prvek podporuje automatické velikosti chování následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="c9bb8-104">The <xref:System.Windows.Forms.TableLayoutPanel> control supports automatic sizing behavior in the following ways:</span></span>  
  
-   <span data-ttu-id="c9bb8-105">Až <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnosti;</span><span class="sxs-lookup"><span data-stu-id="c9bb8-105">Through the <xref:System.Windows.Forms.Control.AutoSize%2A> property;</span></span>  
  
-   <span data-ttu-id="c9bb8-106">Prostřednictvím <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> vlastnost <xref:System.Windows.Forms.TableLayoutPanel> styly sloupců a řádků ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c9bb8-106">Through the <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> property on the <xref:System.Windows.Forms.TableLayoutPanel> control’s column and row styles.</span></span>  
  
### <a name="the-autosize-property-with-row-and-column-styles"></a><span data-ttu-id="c9bb8-107">S vlastností AutoSize řádků a styly sloupců</span><span class="sxs-lookup"><span data-stu-id="c9bb8-107">The AutoSize Property with Row and Column Styles</span></span>  
 <span data-ttu-id="c9bb8-108">Následující tabulka popisuje interakce mezi <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost a <xref:System.Windows.Forms.TableLayoutPanel> styly sloupců a řádků ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c9bb8-108">The following table describes the interaction between the <xref:System.Windows.Forms.Control.AutoSize%2A> property and the <xref:System.Windows.Forms.TableLayoutPanel> control’s column and row styles.</span></span>  
  
|<span data-ttu-id="c9bb8-109">Nastavení AutoSize</span><span class="sxs-lookup"><span data-stu-id="c9bb8-109">AutoSize setting</span></span>|<span data-ttu-id="c9bb8-110">Styl interakce</span><span class="sxs-lookup"><span data-stu-id="c9bb8-110">Style interaction</span></span>|  
|----------------------|-----------------------|  
|`false`|<span data-ttu-id="c9bb8-111"><xref:System.Windows.Forms.TableLayoutPanel> Ovládací prvek pokračuje zleva doprava a přiděluje místo pro sloupce nebo řádku nebo v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="c9bb8-111">The <xref:System.Windows.Forms.TableLayoutPanel> control proceeds from left to right, and allocates space for the column or row or in the following order.</span></span><br /><br /> <span data-ttu-id="c9bb8-112">1.  Pokud <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> je nastavena na <xref:System.Windows.Forms.SizeType.Absolute>, určený v pixelech <xref:System.Windows.Forms.ColumnStyle.Width%2A> nebo <xref:System.Windows.Forms.RowStyle.Height%2A> je přidělen.</span><span class="sxs-lookup"><span data-stu-id="c9bb8-112">1.  If the <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> property is set to <xref:System.Windows.Forms.SizeType.Absolute>, the number of pixels specified by <xref:System.Windows.Forms.ColumnStyle.Width%2A> or <xref:System.Windows.Forms.RowStyle.Height%2A> is allocated.</span></span><br /><span data-ttu-id="c9bb8-113">2.  Pokud <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> je nastavena na <xref:System.Windows.Forms.SizeType.AutoSize>, vrácený podřízeného ovládacího prvku v pixelech <xref:System.Windows.Forms.Control.GetPreferredSize%2A> je přidělena metoda.</span><span class="sxs-lookup"><span data-stu-id="c9bb8-113">2.  If the <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> property is set to <xref:System.Windows.Forms.SizeType.AutoSize>, the number of pixels returned by the child control’s <xref:System.Windows.Forms.Control.GetPreferredSize%2A> method is allocated.</span></span><br /><span data-ttu-id="c9bb8-114">3.  Po místo pro všechny <xref:System.Windows.Forms.SizeType.Absolute> a <xref:System.Windows.Forms.SizeType.AutoSize> sloupců nebo řádků je přidělen, všechny sloupce nebo řádky s <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> nastavena na <xref:System.Windows.Forms.SizeType.Percent> jsou používány k přidělení proporcionálně zbývající volné místo</span><span class="sxs-lookup"><span data-stu-id="c9bb8-114">3.  After space for all <xref:System.Windows.Forms.SizeType.Absolute> and <xref:System.Windows.Forms.SizeType.AutoSize> columns or rows is allocated, any columns or rows with <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> set to <xref:System.Windows.Forms.SizeType.Percent> are used to proportionally allocate the remaining free space</span></span>|  
|`true`|<span data-ttu-id="c9bb8-115">Podobně jako na předchozí interakci s výjimkou, která <xref:System.Windows.Forms.SizeType.Percent> sloupců nebo řádků získat aspekty automatické velikosti.</span><span class="sxs-lookup"><span data-stu-id="c9bb8-115">Similar to the previous interaction, with the exception that <xref:System.Windows.Forms.SizeType.Percent> columns or rows acquire an automatic sizing aspect.</span></span><br /><br /> <span data-ttu-id="c9bb8-116"><xref:System.Windows.Forms.TableLayoutPanel> Rozšíří ovládací prvek sloupec nebo řádek, který má dostatek volného místa, vytvořit tak, aby žádný sloupec nebo řádek s <xref:System.Windows.Forms.SizeType.Percent> stylů klipy jeho obsah.</span><span class="sxs-lookup"><span data-stu-id="c9bb8-116">The <xref:System.Windows.Forms.TableLayoutPanel> control expands the column or row to create adequate free space, so that no column or row with <xref:System.Windows.Forms.SizeType.Percent> styling clips its contents.</span></span> <span data-ttu-id="c9bb8-117"><xref:System.Windows.Forms.TableLayoutPanel> Ovládací prvek přiděluje nové místo proporcionálně souladu s <xref:System.Windows.Forms.ColumnStyle.Width%2A> nebo <xref:System.Windows.Forms.RowStyle.Height%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c9bb8-117">The <xref:System.Windows.Forms.TableLayoutPanel> control allocates the new space proportionally according to the <xref:System.Windows.Forms.ColumnStyle.Width%2A> or <xref:System.Windows.Forms.RowStyle.Height%2A> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c9bb8-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c9bb8-118">See also</span></span>

- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="c9bb8-119">TableLayoutPanel – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="c9bb8-119">TableLayoutPanel Control Overview</span></span>](tablelayoutpanel-control-overview.md)
