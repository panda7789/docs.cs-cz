---
title: 'Postupy: Kreslení čáry v rozhraní Windows Forms'
description: Naučte se, jak na formuláři nakreslit čáru tím, že zpracujete událost nátěru a pak ji vyplníte pomocí vlastnosti Graphics objektu PaintEventArgs.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- Graphics.DrawLine
helpviewer_keywords:
- examples [Windows Forms], drawing lines on forms
- drawing [Windows Forms], lines
- lines [Windows Forms], drawing
- drawing lines
ms.assetid: 55c1dbeb-75d0-430c-9814-a24b8971ad8c
ms.openlocfilehash: c8e92dc265c63413275561d0e2e3aa820eaec724
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621623"
---
# <a name="how-to-draw-a-line-on-a-windows-form"></a><span data-ttu-id="6d90d-103">Postupy: Kreslení čáry v rozhraní Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6d90d-103">How to: Draw a Line on a Windows Form</span></span>
<span data-ttu-id="6d90d-104">Tento příklad nakreslí čáru na formuláři.</span><span class="sxs-lookup"><span data-stu-id="6d90d-104">This example draws a line on a form.</span></span> <span data-ttu-id="6d90d-105">Při kreslení na formuláři se obvykle zpracovává <xref:System.Windows.Forms.Control.Paint> událost formuláře a provádí vykreslování pomocí <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> vlastnosti <xref:System.Windows.Forms.PaintEventArgs> , jak je znázorněno v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="6d90d-105">Typically, when you draw on a form, you handle the form’s  <xref:System.Windows.Forms.Control.Paint> event and perform the drawing using the <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> property of the <xref:System.Windows.Forms.PaintEventArgs>, as shown in this example</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d90d-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="6d90d-106">Example</span></span>  
 [!code-csharp[System.Drawing.UsingAPen#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6d90d-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="6d90d-107">Compiling the Code</span></span>  
 <span data-ttu-id="6d90d-108">Předchozí příklad je navržen pro použití s model Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e` , což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="6d90d-108">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="6d90d-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="6d90d-109">Robust Programming</span></span>  
 <span data-ttu-id="6d90d-110">Vždy byste měli volat <xref:System.IDisposable.Dispose%2A> všechny objekty, které využívají systémové prostředky, jako například <xref:System.Drawing.Pen> objekty.</span><span class="sxs-lookup"><span data-stu-id="6d90d-110">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Pen> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d90d-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6d90d-111">See also</span></span>

- <xref:System.Drawing.Graphics.DrawLine%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="6d90d-112">Začínáme s programováním grafiky</span><span class="sxs-lookup"><span data-stu-id="6d90d-112">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="6d90d-113">Kreslení čar a obrazců pomocí pera</span><span class="sxs-lookup"><span data-stu-id="6d90d-113">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="6d90d-114">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6d90d-114">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
