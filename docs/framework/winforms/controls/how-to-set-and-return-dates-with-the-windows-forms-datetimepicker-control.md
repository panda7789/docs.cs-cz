---
title: Nastavení a vrácení dat pomocí ovládacího prvku DateTimePicker
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
ms.openlocfilehash: 1e0aa58e98748ccde9411f0f4871adbae3a5f14d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747111"
---
# <a name="how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control"></a><span data-ttu-id="0e542-102">Postupy: Nastavení a vracení kalendářních dat pomocí ovládacího prvku Windows Forms DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="0e542-102">How to: Set and Return Dates with the Windows Forms DateTimePicker Control</span></span>
<span data-ttu-id="0e542-103">Aktuálně vybrané datum nebo čas v ovládacím prvku model Windows Forms <xref:System.Windows.Forms.DateTimePicker> určuje vlastnost <xref:System.Windows.Forms.DateTimePicker.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="0e542-103">The currently selected date or time in the Windows Forms <xref:System.Windows.Forms.DateTimePicker> control is determined by the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property.</span></span> <span data-ttu-id="0e542-104">Vlastnost <xref:System.Windows.Forms.DateTimePicker.Value%2A> lze nastavit před zobrazením ovládacího prvku (například v době návrhu nebo v události <xref:System.Windows.Forms.Form.Load> formuláře) k určení, které datum bude na ovládacím prvku původně vybráno.</span><span class="sxs-lookup"><span data-stu-id="0e542-104">You can set the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property before the control is displayed (for example, at design time or in the form's <xref:System.Windows.Forms.Form.Load> event) to determine which date will be initially selected in the control.</span></span> <span data-ttu-id="0e542-105">Ve výchozím nastavení je <xref:System.Windows.Forms.DateTimePicker.Value%2A> ovládacího prvku nastaven na aktuální datum.</span><span class="sxs-lookup"><span data-stu-id="0e542-105">By default, the control's <xref:System.Windows.Forms.DateTimePicker.Value%2A> is set to the current date.</span></span> <span data-ttu-id="0e542-106">Změníte-li <xref:System.Windows.Forms.DateTimePicker.Value%2A> ovládacího prvku v kódu, bude ovládací prvek automaticky aktualizován ve formuláři tak, aby odrážel nové nastavení.</span><span class="sxs-lookup"><span data-stu-id="0e542-106">If you change the control's <xref:System.Windows.Forms.DateTimePicker.Value%2A> in code, the control is automatically updated on the form to reflect the new setting.</span></span>  
  
 <span data-ttu-id="0e542-107">Vlastnost <xref:System.Windows.Forms.DateTimePicker.Value%2A> vrací strukturu <xref:System.DateTime> jako hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0e542-107">The <xref:System.Windows.Forms.DateTimePicker.Value%2A> property returns a <xref:System.DateTime> structure as its value.</span></span> <span data-ttu-id="0e542-108">Existuje několik vlastností <xref:System.DateTime> struktury, které vracejí konkrétní informace o zobrazeném datu.</span><span class="sxs-lookup"><span data-stu-id="0e542-108">There are several properties of the <xref:System.DateTime> structure that return specific information about the displayed date.</span></span> <span data-ttu-id="0e542-109">Tyto vlastnosti lze použít pouze k vrácení hodnoty; Nepoužívejte je k nastavení hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0e542-109">These properties can only be used to return a value; do not use them to set a value.</span></span>  
  
- <span data-ttu-id="0e542-110">Pro hodnoty kalendářních dat vrátí <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A>a <xref:System.DateTime.Year%2A> vlastnosti celočíselné hodnoty pro tyto časové jednotky vybraného data.</span><span class="sxs-lookup"><span data-stu-id="0e542-110">For date values, the <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A>, and <xref:System.DateTime.Year%2A> properties return integer values for those time units of the selected date.</span></span> <span data-ttu-id="0e542-111">Vlastnost <xref:System.DateTime.DayOfWeek%2A> vrací hodnotu udávající vybraný den v týdnu (možné hodnoty jsou uvedeny v <xref:System.DayOfWeek> výčtu).</span><span class="sxs-lookup"><span data-stu-id="0e542-111">The <xref:System.DateTime.DayOfWeek%2A> property returns a value indicating the selected day of the week (possible values are listed in the <xref:System.DayOfWeek> enumeration).</span></span>  
  
- <span data-ttu-id="0e542-112">Pro časové hodnoty vrací <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A>a <xref:System.DateTime.Millisecond%2A> vlastnosti pro tyto časové jednotky celočíselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0e542-112">For time values, the <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A>, and <xref:System.DateTime.Millisecond%2A> properties return integer values for those time units.</span></span> <span data-ttu-id="0e542-113">Chcete-li nakonfigurovat ovládací prvek tak, aby zobrazoval časy, přečtěte si téma [Postup: zobrazení času pomocí ovládacího prvku DateTimePicker](how-to-display-time-with-the-datetimepicker-control.md).</span><span class="sxs-lookup"><span data-stu-id="0e542-113">To configure the control to display times, see [How to: Display Time with the DateTimePicker Control](how-to-display-time-with-the-datetimepicker-control.md).</span></span>  
  
### <a name="to-set-the-date-and-time-value-of-the-control"></a><span data-ttu-id="0e542-114">Nastavení hodnoty data a času ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="0e542-114">To set the date and time value of the control</span></span>  
  
- <span data-ttu-id="0e542-115">Vlastnost <xref:System.Windows.Forms.DateTimePicker.Value%2A> nastavte na hodnotu datum nebo čas.</span><span class="sxs-lookup"><span data-stu-id="0e542-115">Set the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property to a date or time value.</span></span>  
  
    ```vb  
    DateTimePicker1.Value = New DateTime(2001, 10, 20)  
    ```  
  
    ```csharp  
    dateTimePicker1.Value = new DateTime(2001, 10, 20);  
    ```  
  
    ```cpp  
    dateTimePicker1->Value = DateTime(2001, 10, 20);  
    ```  
  
### <a name="to-return-the-date-and-time-value"></a><span data-ttu-id="0e542-116">Vrácení hodnoty data a času</span><span class="sxs-lookup"><span data-stu-id="0e542-116">To return the date and time value</span></span>  
  
- <span data-ttu-id="0e542-117">Voláním vlastnosti <xref:System.Windows.Forms.DateTimePicker.Text%2A> vrátíte celou hodnotu formátovanou v ovládacím prvku nebo zavolejte příslušnou metodu vlastnosti <xref:System.Windows.Forms.DateTimePicker.Value%2A>, která vrátí část hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0e542-117">Call the <xref:System.Windows.Forms.DateTimePicker.Text%2A> property to return the entire value as formatted in the control, or call the appropriate method of the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property to return a part of the value.</span></span> <span data-ttu-id="0e542-118">Pomocí <xref:System.Windows.Forms.DateTimePicker.ToString%2A> převeďte informace na řetězec, který se může zobrazit uživateli.</span><span class="sxs-lookup"><span data-stu-id="0e542-118">Use <xref:System.Windows.Forms.DateTimePicker.ToString%2A> to convert the information into a string that can be displayed to the user.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0e542-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="0e542-119">See also</span></span>

- [<span data-ttu-id="0e542-120">Ovládací prvek DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="0e542-120">DateTimePicker Control</span></span>](datetimepicker-control-windows-forms.md)
- [<span data-ttu-id="0e542-121">Postupy: Zobrazení data ve vlastním formátu pomocí ovládacího prvku Windows Forms DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="0e542-121">How to: Display a Date in a Custom Format with the Windows Forms DateTimePicker Control</span></span>](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)
