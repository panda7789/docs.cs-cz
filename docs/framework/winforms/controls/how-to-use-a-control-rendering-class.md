---
title: 'Postupy: Použití třídy vykreslující ovládací prvek'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- professional appearance [Windows Forms], rendering Windows Forms controls
- visual themes [Windows Forms], applying to Windows Forms controls
- visual styles [Windows Forms], rendering Windows Forms controls
ms.assetid: c0125e34-cd74-4c35-818c-3e40f462b0a3
ms.openlocfilehash: a0f450ff5f169026007002a0d2907ee35e79b29d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64630557"
---
# <a name="how-to-use-a-control-rendering-class"></a><span data-ttu-id="a68b8-102">Postupy: Použití třídy vykreslující ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="a68b8-102">How to: Use a Control Rendering Class</span></span>
<span data-ttu-id="a68b8-103">Tento příklad ukazuje, jak používat <xref:System.Windows.Forms.ComboBoxRenderer> třídy k vykreslení na šipku rozevíracího seznamu pole se seznamem ovládací prvek pole.</span><span class="sxs-lookup"><span data-stu-id="a68b8-103">This example demonstrates how to use the <xref:System.Windows.Forms.ComboBoxRenderer> class to render the drop-down arrow of a combo box control.</span></span> <span data-ttu-id="a68b8-104">V příkladu se skládá z <xref:System.Windows.Forms.Control.OnPaint%2A> metoda jednoduché vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="a68b8-104">The example consists of the <xref:System.Windows.Forms.Control.OnPaint%2A> method of a simple custom control.</span></span> <span data-ttu-id="a68b8-105"><xref:System.Windows.Forms.ComboBoxRenderer.IsSupported%2A?displayProperty=nameWithType> Vlastnost se používá k určení, zda jsou vizuální styly povoleny v klientské oblasti okna aplikace.</span><span class="sxs-lookup"><span data-stu-id="a68b8-105">The <xref:System.Windows.Forms.ComboBoxRenderer.IsSupported%2A?displayProperty=nameWithType> property is used to determine whether visual styles are enabled in the client area of application windows.</span></span> <span data-ttu-id="a68b8-106">Pokud vizuální styly jsou aktivní, pak bude <xref:System.Windows.Forms.ComboBoxRenderer.DrawDropDownButton%2A?displayProperty=nameWithType> metoda vykreslí na šipku rozevíracího seznamu s vizuálními styly; v opačném případě <xref:System.Windows.Forms.ControlPaint.DrawComboButton%2A?displayProperty=nameWithType> metoda vykreslí na šipku rozevíracího seznamu v klasické Windows.</span><span class="sxs-lookup"><span data-stu-id="a68b8-106">If visual styles are active, then the <xref:System.Windows.Forms.ComboBoxRenderer.DrawDropDownButton%2A?displayProperty=nameWithType> method will render the drop-down arrow with visual styles; otherwise, the <xref:System.Windows.Forms.ControlPaint.DrawComboButton%2A?displayProperty=nameWithType> method will render the drop-down arrow in the classic Windows style.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a68b8-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="a68b8-107">Example</span></span>  
 [!code-cpp[System.Windows.Forms_ControlRenderer#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/cpp/form1.cpp#10)]
 [!code-csharp[System.Windows.Forms_ControlRenderer#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms_ControlRenderer#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a68b8-108">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="a68b8-108">Compiling the Code</span></span>  
 <span data-ttu-id="a68b8-109">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="a68b8-109">This example requires:</span></span>  
  
- <span data-ttu-id="a68b8-110">Vlastní ovládací prvek odvozený z <xref:System.Windows.Forms.Control> třídy.</span><span class="sxs-lookup"><span data-stu-id="a68b8-110">A custom control derived from the <xref:System.Windows.Forms.Control> class.</span></span>  
  
- <span data-ttu-id="a68b8-111">A <xref:System.Windows.Forms.Form> , který je hostitelem vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="a68b8-111">A <xref:System.Windows.Forms.Form> that hosts the custom control.</span></span>  
  
- <span data-ttu-id="a68b8-112">Odkazy <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, a <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> obory názvů.</span><span class="sxs-lookup"><span data-stu-id="a68b8-112">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a68b8-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a68b8-113">See also</span></span>

- [<span data-ttu-id="a68b8-114">Vykreslování ovládacích prvků s vizuálními styly</span><span class="sxs-lookup"><span data-stu-id="a68b8-114">Rendering Controls with Visual Styles</span></span>](rendering-controls-with-visual-styles.md)
