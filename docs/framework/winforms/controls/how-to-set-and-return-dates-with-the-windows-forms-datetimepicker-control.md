---
title: "Postupy: Nastavení a vracení kalendářních dat pomocí ovládacího prvku Windows Forms DateTimePicker"
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
- cpp
helpviewer_keywords:
- dates [Windows Forms], setting in DateTimePicker
- DateTimePicker control [Windows Forms], setting and returning dates
- examples [Windows Forms], DateTimePicker control
ms.assetid: a8a48d68-e4b5-426e-9764-51230fc9acd2
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 83a95d2c1aa9f1704f143ae9095cb38596d2c1a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control"></a><span data-ttu-id="0c195-102">Postupy: Nastavení a vracení kalendářních dat pomocí ovládacího prvku Windows Forms DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="0c195-102">How to: Set and Return Dates with the Windows Forms DateTimePicker Control</span></span>
<span data-ttu-id="0c195-103">Aktuálně vybrané data a času v systému Windows Forms <xref:System.Windows.Forms.DateTimePicker> je dáno ovládacího prvku <xref:System.Windows.Forms.DateTimePicker.Value%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0c195-103">The currently selected date or time in the Windows Forms <xref:System.Windows.Forms.DateTimePicker> control is determined by the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property.</span></span> <span data-ttu-id="0c195-104">Můžete nastavit <xref:System.Windows.Forms.DateTimePicker.Value%2A> předtím, než se zobrazí ovládací prvek (například v době návrhu nebo formuláře <xref:System.Windows.Forms.Form.Load> událostí) k určení, datum, pro které bude zpočátku vybrali v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="0c195-104">You can set the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property before the control is displayed (for example, at design time or in the form's <xref:System.Windows.Forms.Form.Load> event) to determine which date will be initially selected in the control.</span></span> <span data-ttu-id="0c195-105">Ve výchozím nastavení, ovládacího prvku na <xref:System.Windows.Forms.DateTimePicker.Value%2A> nastavena na aktuální datum.</span><span class="sxs-lookup"><span data-stu-id="0c195-105">By default, the control's <xref:System.Windows.Forms.DateTimePicker.Value%2A> is set to the current date.</span></span> <span data-ttu-id="0c195-106">Pokud změníte ovládacího prvku <xref:System.Windows.Forms.DateTimePicker.Value%2A> v kódu, se automaticky aktualizuje ovládací prvek na formuláři, aby odrážela nové nastavení.</span><span class="sxs-lookup"><span data-stu-id="0c195-106">If you change the control's <xref:System.Windows.Forms.DateTimePicker.Value%2A> in code, the control is automatically updated on the form to reflect the new setting.</span></span>  
  
 <span data-ttu-id="0c195-107"><xref:System.Windows.Forms.DateTimePicker.Value%2A> Vlastnost vrátí <xref:System.DateTime> struktura jako jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0c195-107">The <xref:System.Windows.Forms.DateTimePicker.Value%2A> property returns a <xref:System.DateTime> structure as its value.</span></span> <span data-ttu-id="0c195-108">Existuje několik vlastností, které <xref:System.DateTime> struktura, která vrátí konkrétní informace o zobrazené datum.</span><span class="sxs-lookup"><span data-stu-id="0c195-108">There are several properties of the <xref:System.DateTime> structure that return specific information about the displayed date.</span></span> <span data-ttu-id="0c195-109">Tyto vlastnosti slouží pouze k vrácení hodnoty; Nepoužívejte je nastavte hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0c195-109">These properties can only be used to return a value; do not use them to set a value.</span></span>  
  
-   <span data-ttu-id="0c195-110">Pro hodnoty data <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A>, a <xref:System.DateTime.Year%2A> vlastnosti, vrátí celé číslo hodnoty pro tyto časové jednotky vybraným datem.</span><span class="sxs-lookup"><span data-stu-id="0c195-110">For date values, the <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A>, and <xref:System.DateTime.Year%2A> properties return integer values for those time units of the selected date.</span></span> <span data-ttu-id="0c195-111"><xref:System.DateTime.DayOfWeek%2A> Vlastnost vrací hodnotu, která určuje vybraný den v týdnu (možné hodnoty jsou uvedeny v <xref:System.DayOfWeek> výčet).</span><span class="sxs-lookup"><span data-stu-id="0c195-111">The <xref:System.DateTime.DayOfWeek%2A> property returns a value indicating the selected day of the week (possible values are listed in the <xref:System.DayOfWeek> enumeration).</span></span>  
  
-   <span data-ttu-id="0c195-112">Pro hodnoty času <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A>, a <xref:System.DateTime.Millisecond%2A> vlastnosti vrátí celé číslo hodnoty těchto časových jednotek.</span><span class="sxs-lookup"><span data-stu-id="0c195-112">For time values, the <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A>, and <xref:System.DateTime.Millisecond%2A> properties return integer values for those time units.</span></span> <span data-ttu-id="0c195-113">Konfigurovat ovládací prvek zobrazí dobu, najdete v tématu [postupy: zobrazení času pomocí ovládacího prvku DateTimePicker](../../../../docs/framework/winforms/controls/how-to-display-time-with-the-datetimepicker-control.md).</span><span class="sxs-lookup"><span data-stu-id="0c195-113">To configure the control to display times, see [How to: Display Time with the DateTimePicker Control](../../../../docs/framework/winforms/controls/how-to-display-time-with-the-datetimepicker-control.md).</span></span>  
  
### <a name="to-set-the-date-and-time-value-of-the-control"></a><span data-ttu-id="0c195-114">Chcete-li nastavit hodnoty data a času ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="0c195-114">To set the date and time value of the control</span></span>  
  
-   <span data-ttu-id="0c195-115">Nastavte <xref:System.Windows.Forms.DateTimePicker.Value%2A> vlastnost na hodnotu data a času.</span><span class="sxs-lookup"><span data-stu-id="0c195-115">Set the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property to a date or time value.</span></span>  
  
    ```vb  
    DateTimePicker1.Value = New DateTime(2001, 10, 20)  
    ```  
  
    ```csharp  
    dateTimePicker1.Value = new DateTime(2001, 10, 20);  
    ```  
  
    ```cpp  
    dateTimePicker1->Value = DateTime(2001, 10, 20);  
    ```  
  
### <a name="to-return-the-date-and-time-value"></a><span data-ttu-id="0c195-116">Chcete-li vrátit hodnotu data a času</span><span class="sxs-lookup"><span data-stu-id="0c195-116">To return the date and time value</span></span>  
  
-   <span data-ttu-id="0c195-117">Volání <xref:System.Windows.Forms.DateTimePicker.Text%2A> vlastnost, která má vrátit celou hodnotu jako formátované v ovládacím prvku nebo volejte příslušnou metodu <xref:System.Windows.Forms.DateTimePicker.Value%2A> vlastnost vrátit část hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0c195-117">Call the <xref:System.Windows.Forms.DateTimePicker.Text%2A> property to return the entire value as formatted in the control, or call the appropriate method of the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property to return a part of the value.</span></span> <span data-ttu-id="0c195-118">Použití <xref:System.Windows.Forms.DateTimePicker.ToString%2A> informace převést na řetězec, který lze zobrazit uživateli.</span><span class="sxs-lookup"><span data-stu-id="0c195-118">Use <xref:System.Windows.Forms.DateTimePicker.ToString%2A> to convert the information into a string that can be displayed to the user.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0c195-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="0c195-119">See Also</span></span>  
 [<span data-ttu-id="0c195-120">Ovládací prvek DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="0c195-120">DateTimePicker Control</span></span>](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)  
 [<span data-ttu-id="0c195-121">Postupy: Zobrazení data ve vlastním formátu pomocí ovládacího prvku Windows Forms DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="0c195-121">How to: Display a Date in a Custom Format with the Windows Forms DateTimePicker Control</span></span>](../../../../docs/framework/winforms/controls/display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)
