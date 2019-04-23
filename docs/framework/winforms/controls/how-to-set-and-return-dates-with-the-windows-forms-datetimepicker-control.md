---
title: 'Postupy: Nastavení a vracení kalendářních dat pomocí ovládacího prvku Windows Forms DateTimePicker'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- dates [Windows Forms], setting in DateTimePicker
- DateTimePicker control [Windows Forms], setting and returning dates
- examples [Windows Forms], DateTimePicker control
ms.assetid: a8a48d68-e4b5-426e-9764-51230fc9acd2
ms.openlocfilehash: cc4f0bdf7355cda61e6cb95f5e0b18c4f83aa62b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59081538"
---
# <a name="how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control"></a><span data-ttu-id="e08ed-102">Postupy: Nastavení a vracení kalendářních dat pomocí ovládacího prvku Windows Forms DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="e08ed-102">How to: Set and Return Dates with the Windows Forms DateTimePicker Control</span></span>
<span data-ttu-id="e08ed-103">Aktuálně vybrané datum a čas ve Windows Forms <xref:System.Windows.Forms.DateTimePicker> ovládací prvek závisí <xref:System.Windows.Forms.DateTimePicker.Value%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e08ed-103">The currently selected date or time in the Windows Forms <xref:System.Windows.Forms.DateTimePicker> control is determined by the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property.</span></span> <span data-ttu-id="e08ed-104">Můžete nastavit <xref:System.Windows.Forms.DateTimePicker.Value%2A> vlastnost předtím, než se zobrazí ovládací prvek (například v době návrhu nebo v formuláře <xref:System.Windows.Forms.Form.Load> událostí) k určení, která data se původně výběr v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="e08ed-104">You can set the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property before the control is displayed (for example, at design time or in the form's <xref:System.Windows.Forms.Form.Load> event) to determine which date will be initially selected in the control.</span></span> <span data-ttu-id="e08ed-105">Ve výchozím nastavení, ovládací prvek na <xref:System.Windows.Forms.DateTimePicker.Value%2A> je nastavena na aktuální datum.</span><span class="sxs-lookup"><span data-stu-id="e08ed-105">By default, the control's <xref:System.Windows.Forms.DateTimePicker.Value%2A> is set to the current date.</span></span> <span data-ttu-id="e08ed-106">Pokud změníte ovládacího prvku <xref:System.Windows.Forms.DateTimePicker.Value%2A> v kódu, se automaticky aktualizuje ovládací prvek na formuláři tak, aby odrážela nové nastavení.</span><span class="sxs-lookup"><span data-stu-id="e08ed-106">If you change the control's <xref:System.Windows.Forms.DateTimePicker.Value%2A> in code, the control is automatically updated on the form to reflect the new setting.</span></span>  
  
 <span data-ttu-id="e08ed-107"><xref:System.Windows.Forms.DateTimePicker.Value%2A> Vrátí vlastnost <xref:System.DateTime> strukturu jako jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e08ed-107">The <xref:System.Windows.Forms.DateTimePicker.Value%2A> property returns a <xref:System.DateTime> structure as its value.</span></span> <span data-ttu-id="e08ed-108">Existuje několik vlastností <xref:System.DateTime> struktura, která vrátí konkrétní informace o zobrazené datum.</span><span class="sxs-lookup"><span data-stu-id="e08ed-108">There are several properties of the <xref:System.DateTime> structure that return specific information about the displayed date.</span></span> <span data-ttu-id="e08ed-109">Tyto vlastnosti lze použít pouze k vrácení hodnoty; Nepoužívejte je pro nastavení hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e08ed-109">These properties can only be used to return a value; do not use them to set a value.</span></span>  
  
-   <span data-ttu-id="e08ed-110">Pro hodnoty data <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A>, a <xref:System.DateTime.Year%2A> vlastnosti vrací celočíselných hodnot pro tyto časové jednotky vybraným datem.</span><span class="sxs-lookup"><span data-stu-id="e08ed-110">For date values, the <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A>, and <xref:System.DateTime.Year%2A> properties return integer values for those time units of the selected date.</span></span> <span data-ttu-id="e08ed-111"><xref:System.DateTime.DayOfWeek%2A> Vlastnost vrací hodnotu, která vybraný den v týdnu (možné hodnoty jsou uvedeny v <xref:System.DayOfWeek> výčet).</span><span class="sxs-lookup"><span data-stu-id="e08ed-111">The <xref:System.DateTime.DayOfWeek%2A> property returns a value indicating the selected day of the week (possible values are listed in the <xref:System.DayOfWeek> enumeration).</span></span>  
  
-   <span data-ttu-id="e08ed-112">Pro časové hodnoty <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A>, a <xref:System.DateTime.Millisecond%2A> vlastnosti vrací celočíselných hodnot pro tyto časové jednotky.</span><span class="sxs-lookup"><span data-stu-id="e08ed-112">For time values, the <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A>, and <xref:System.DateTime.Millisecond%2A> properties return integer values for those time units.</span></span> <span data-ttu-id="e08ed-113">Pokud chcete nakonfigurovat ovládací prvek pro zobrazení doby, najdete v článku [jak: Zobrazení času pomocí ovládacího prvku DateTimePicker](how-to-display-time-with-the-datetimepicker-control.md).</span><span class="sxs-lookup"><span data-stu-id="e08ed-113">To configure the control to display times, see [How to: Display Time with the DateTimePicker Control](how-to-display-time-with-the-datetimepicker-control.md).</span></span>  
  
### <a name="to-set-the-date-and-time-value-of-the-control"></a><span data-ttu-id="e08ed-114">Chcete-li nastavit hodnoty data a času ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="e08ed-114">To set the date and time value of the control</span></span>  
  
-   <span data-ttu-id="e08ed-115">Nastavte <xref:System.Windows.Forms.DateTimePicker.Value%2A> vlastnost na hodnotu data a času.</span><span class="sxs-lookup"><span data-stu-id="e08ed-115">Set the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property to a date or time value.</span></span>  
  
    ```vb  
    DateTimePicker1.Value = New DateTime(2001, 10, 20)  
    ```  
  
    ```csharp  
    dateTimePicker1.Value = new DateTime(2001, 10, 20);  
    ```  
  
    ```cpp  
    dateTimePicker1->Value = DateTime(2001, 10, 20);  
    ```  
  
### <a name="to-return-the-date-and-time-value"></a><span data-ttu-id="e08ed-116">K vrácení hodnoty data a času</span><span class="sxs-lookup"><span data-stu-id="e08ed-116">To return the date and time value</span></span>  
  
-   <span data-ttu-id="e08ed-117">Volání <xref:System.Windows.Forms.DateTimePicker.Text%2A> vlastnost vrátí celou hodnotu jako ve formátu v ovládacím prvku nebo volání metody odpovídající <xref:System.Windows.Forms.DateTimePicker.Value%2A> vlastnost vrátí část hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e08ed-117">Call the <xref:System.Windows.Forms.DateTimePicker.Text%2A> property to return the entire value as formatted in the control, or call the appropriate method of the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property to return a part of the value.</span></span> <span data-ttu-id="e08ed-118">Použití <xref:System.Windows.Forms.DateTimePicker.ToString%2A> informace převést na řetězec, který je možné zobrazit uživateli.</span><span class="sxs-lookup"><span data-stu-id="e08ed-118">Use <xref:System.Windows.Forms.DateTimePicker.ToString%2A> to convert the information into a string that can be displayed to the user.</span></span>  
  
    ```vb  
    MessageBox.Show("The selected value is ", DateTimePicker1.Text)  
    MessageBox.Show("The day of the week is ",   
       DateTimePicker1.Value.DayOfWeek.ToString)  
    MessageBox.Show("Millisecond is: ",   
       DateTimePicker1.Value.Millisecond.ToString)  
    ```  
  
    ```csharp  
    MessageBox.Show ("The selected value is " +   
       dateTimePicker1.Text);  
    MessageBox.Show ("The day of the week is " +   
       dateTimePicker1.Value.DayOfWeek.ToString());  
    MessageBox.Show("Millisecond is: " +   
       dateTimePicker1.Value.Millisecond.ToString());  
    ```  
  
    ```cpp  
    MessageBox::Show (String::Concat("The selected value is ",  
       dateTimePicker1->Text));  
    MessageBox::Show (String::Concat("The day of the week is ",  
       dateTimePicker1->Value.DayOfWeek.ToString()));  
    MessageBox::Show(String::Concat("Millisecond is: ",  
       dateTimePicker1->Value.Millisecond.ToString()));  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e08ed-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e08ed-119">See also</span></span>

- [<span data-ttu-id="e08ed-120">Ovládací prvek DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="e08ed-120">DateTimePicker Control</span></span>](datetimepicker-control-windows-forms.md)
- [<span data-ttu-id="e08ed-121">Postupy: Zobrazení data ve vlastním formátu pomocí ovládacího prvku Windows Forms DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="e08ed-121">How to: Display a Date in a Custom Format with the Windows Forms DateTimePicker Control</span></span>](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)
