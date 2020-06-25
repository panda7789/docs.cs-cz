---
title: 'Postupy: Zobrazení času pomocí ovládacího prvku DateTimePicker'
description: Naučte se používat ovládací prvek model Windows Forms DateTimePicker k tomu, aby uživatelé mohli vybrat datum a čas a zobrazit toto datum a čas v zadaném formátu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time [Windows Forms], displaying in DateTimePicker control
- examples [Windows Forms], DateTimePicker control
- DateTimePicker control [Windows Forms], displaying time
ms.assetid: 0c1c8b40-1b50-4301-a90c-39516775ccb1
ms.openlocfilehash: ab584367a189d05e567bb57d386c6bf629201102
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325578"
---
# <a name="how-to-display-time-with-the-datetimepicker-control"></a><span data-ttu-id="cc006-103">Postupy: Zobrazení času pomocí ovládacího prvku DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="cc006-103">How to: Display Time with the DateTimePicker Control</span></span>
<span data-ttu-id="cc006-104">Pokud chcete, aby vaše aplikace uživatelům umožnila vybrat datum a čas a zobrazit toto datum a čas v zadaném formátu, použijte <xref:System.Windows.Forms.DateTimePicker> ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="cc006-104">If you want your application to enable users to select a date and time, and to display that date and time in the specified format, use the <xref:System.Windows.Forms.DateTimePicker> control.</span></span> <span data-ttu-id="cc006-105">Následující postup ukazuje, jak použít <xref:System.Windows.Forms.DateTimePicker> ovládací prvek k zobrazení času.</span><span class="sxs-lookup"><span data-stu-id="cc006-105">The following procedure shows how to use the <xref:System.Windows.Forms.DateTimePicker> control to display the time.</span></span>  
  
### <a name="to-display-the-time-with-the-datetimepicker-control"></a><span data-ttu-id="cc006-106">Zobrazení času s ovládacím prvkem DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="cc006-106">To display the time with the DateTimePicker control</span></span>  
  
1. <span data-ttu-id="cc006-107">Nastavte <xref:System.Windows.Forms.DateTimePicker.Format%2A> vlastnost na<xref:System.Windows.Forms.DateTimePickerFormat.Time></span><span class="sxs-lookup"><span data-stu-id="cc006-107">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to <xref:System.Windows.Forms.DateTimePickerFormat.Time></span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#2)]  
  
2. <span data-ttu-id="cc006-108">Nastavte <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> vlastnost pro na <xref:System.Windows.Forms.DateTimePicker> `true` .</span><span class="sxs-lookup"><span data-stu-id="cc006-108">Set the <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> property for the <xref:System.Windows.Forms.DateTimePicker> to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="cc006-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="cc006-109">Example</span></span>  
 <span data-ttu-id="cc006-110">Následující ukázka kódu ukazuje, jak vytvořit <xref:System.Windows.Forms.DateTimePicker> , který umožňuje uživatelům zvolit jenom čas.</span><span class="sxs-lookup"><span data-stu-id="cc006-110">The following code sample shows how to create a <xref:System.Windows.Forms.DateTimePicker> that enables users to choose a time only.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cc006-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="cc006-111">Compiling the Code</span></span>  
 <span data-ttu-id="cc006-112">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="cc006-112">This example requires:</span></span>  
  
- <span data-ttu-id="cc006-113">Odkazy na sestavení System, System. data, System. Drawing a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="cc006-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc006-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="cc006-114">See also</span></span>

- [<span data-ttu-id="cc006-115">DateTimePicker – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="cc006-115">DateTimePicker Control</span></span>](datetimepicker-control-windows-forms.md)
