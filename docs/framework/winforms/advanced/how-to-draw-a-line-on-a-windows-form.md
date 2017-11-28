---
title: "Postupy: Kreslení čáry v rozhraní Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
f1_keywords: Graphics.DrawLine
helpviewer_keywords:
- examples [Windows Forms], drawing lines on forms
- drawing [Windows Forms], lines
- lines [Windows Forms], drawing
- drawing lines
ms.assetid: 55c1dbeb-75d0-430c-9814-a24b8971ad8c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 984cdaca14c354ca78118412911c69c282ddd1bc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-line-on-a-windows-form"></a><span data-ttu-id="eb90f-102">Postupy: Kreslení čáry v rozhraní Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eb90f-102">How to: Draw a Line on a Windows Form</span></span>
<span data-ttu-id="eb90f-103">Tento příklad nakreslí čáru ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="eb90f-103">This example draws a line on a form.</span></span> <span data-ttu-id="eb90f-104">Obvykle při kreslení ve formuláři zpracováváte formuláře <xref:System.Windows.Forms.Control.Paint> událostí a proveďte kreslení pomocí <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> vlastnost <xref:System.Windows.Forms.PaintEventArgs>, jak je uvedeno v tomto příkladu</span><span class="sxs-lookup"><span data-stu-id="eb90f-104">Typically, when you draw on a form, you handle the form’s  <xref:System.Windows.Forms.Control.Paint> event and perform the drawing using the <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> property of the <xref:System.Windows.Forms.PaintEventArgs>, as shown in this example</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb90f-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="eb90f-105">Example</span></span>  
 [!code-csharp[System.Drawing.UsingAPen#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="eb90f-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="eb90f-106">Compiling the Code</span></span>  
 <span data-ttu-id="eb90f-107">V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="eb90f-107">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="eb90f-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="eb90f-108">Robust Programming</span></span>  
 <span data-ttu-id="eb90f-109">Vždy byste měli zavolat <xref:System.IDisposable.Dispose%2A> na všechny objekty, které využívají systémové prostředky, jako například <xref:System.Drawing.Pen> objekty.</span><span class="sxs-lookup"><span data-stu-id="eb90f-109">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Pen> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb90f-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="eb90f-110">See Also</span></span>  
 <xref:System.Drawing.Graphics.DrawLine%2A>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 [<span data-ttu-id="eb90f-111">Začínáme s programováním grafiky</span><span class="sxs-lookup"><span data-stu-id="eb90f-111">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="eb90f-112">Kreslení čar a obrazců pomocí pera</span><span class="sxs-lookup"><span data-stu-id="eb90f-112">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [<span data-ttu-id="eb90f-113">Grafika a kreslení v systému Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eb90f-113">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
