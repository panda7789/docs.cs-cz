---
title: Zobrazení data ve vlastním formátu pomocí ovládacího prvku DateTimePicker
description: Naučte se používat ovládací prvek model Windows Forms DateTimePicker k formátování zobrazení dat a časů v ovládacím prvku.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DateTimePicker control [Windows Forms], display styles
- examples [Windows Forms], DateTimePicker control
- dates [Windows Forms], displaying in DateTimePicker control
ms.assetid: 39767691-2d2b-46b6-a663-b7901e581a6e
ms.openlocfilehash: 773070136e4fd43ab1bf510ebcaf6b0aa6a7ba8a
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325834"
---
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a><span data-ttu-id="e1b99-103">Postupy: Zobrazení data ve vlastním formátu pomocí ovládacího prvku Windows Forms DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="e1b99-103">How to: Display a Date in a Custom Format with the Windows Forms DateTimePicker Control</span></span>
<span data-ttu-id="e1b99-104"><xref:System.Windows.Forms.DateTimePicker>Ovládací prvek model Windows Forms poskytuje flexibilitu při formátování zobrazení dat a časů v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="e1b99-104">The Windows Forms <xref:System.Windows.Forms.DateTimePicker> control gives you flexibility in formatting the display of dates and times in the control.</span></span> <span data-ttu-id="e1b99-105"><xref:System.Windows.Forms.DateTimePicker.Format%2A>Vlastnost umožňuje vybrat z předdefinovaných formátů, které jsou uvedeny v části <xref:System.Windows.Forms.DateTimePickerFormat> .</span><span class="sxs-lookup"><span data-stu-id="e1b99-105">The <xref:System.Windows.Forms.DateTimePicker.Format%2A> property allows you to select from predefined formats, listed in the <xref:System.Windows.Forms.DateTimePickerFormat>.</span></span> <span data-ttu-id="e1b99-106">Pokud žádný z těchto důvodů není pro vaše účely vhodný, můžete vytvořit vlastní styl formátu pomocí znaků formátu uvedených v části <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> .</span><span class="sxs-lookup"><span data-stu-id="e1b99-106">If none of these is adequate for your purposes, you can create your own format style using format characters listed in <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.</span></span>  
  
### <a name="to-display-a-custom-format"></a><span data-ttu-id="e1b99-107">Zobrazení vlastního formátu</span><span class="sxs-lookup"><span data-stu-id="e1b99-107">To display a custom format</span></span>  
  
1. <span data-ttu-id="e1b99-108">Nastavte <xref:System.Windows.Forms.DateTimePicker.Format%2A> vlastnost na hodnotu `DateTimePickerFormat.Custom` .</span><span class="sxs-lookup"><span data-stu-id="e1b99-108">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to `DateTimePickerFormat.Custom`.</span></span>  
  
2. <span data-ttu-id="e1b99-109">Nastavte <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> vlastnost na řetězec formátu.</span><span class="sxs-lookup"><span data-stu-id="e1b99-109">Set the <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> property to a format string.</span></span>  
  
    ```vb  
    DateTimePicker1.Format = DateTimePickerFormat.Custom  
    ' Display the date as "Mon 27 Feb 2012".  
    DateTimePicker1.CustomFormat = "ddd dd MMM yyyy"  
    ```  
  
    ```csharp  
    dateTimePicker1.Format = DateTimePickerFormat.Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1.CustomFormat = "ddd dd MMM yyyy";  
    ```  
  
    ```cpp  
    dateTimePicker1->Format = DateTimePickerFormat::Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1->CustomFormat = "ddd dd MMM yyyy";  
    ```  
  
### <a name="to-add-text-to-the-formatted-value"></a><span data-ttu-id="e1b99-110">Přidání textu do naformátované hodnoty</span><span class="sxs-lookup"><span data-stu-id="e1b99-110">To add text to the formatted value</span></span>  
  
1. <span data-ttu-id="e1b99-111">Použijte jednoduché uvozovky k uzavření libovolného znaku, který není formátovacím znakem, jako je "M" nebo oddělovače jako ":".</span><span class="sxs-lookup"><span data-stu-id="e1b99-111">Use single quotation marks to enclose any character that is not a format character like "M" or a delimiter like ":".</span></span> <span data-ttu-id="e1b99-112">Například řetězec formátu níže zobrazuje aktuální datum ve formátu "dnes je: 05:30:31 pátek, v. března 2012" v jazykové verzi English (USA).</span><span class="sxs-lookup"><span data-stu-id="e1b99-112">For example, the format string below displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span>  
  
    ```vb  
    DateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy"  
    ```  
  
    ```csharp  
    dateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
    ```  
  
    ```cpp  
    dateTimePicker1->CustomFormat =  
       "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
    ```  
  
     <span data-ttu-id="e1b99-113">V závislosti na nastavení jazykové verze se může změnit libovolný znak, který není uzavřen v jednoduchých uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="e1b99-113">Depending on the culture setting, any characters not enclosed in single quotation marks may be changed.</span></span> <span data-ttu-id="e1b99-114">Například řetězec formátu uvedený výše zobrazuje aktuální datum ve formátu "dnes je: 05:30:31 pátek, březen 02, 2012" v jazykové verzi anglické (USA).</span><span class="sxs-lookup"><span data-stu-id="e1b99-114">For example, the format string above displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span> <span data-ttu-id="e1b99-115">Všimněte si, že první dvojtečka je uzavřena v jednoduchých uvozovkách, protože není určena jako znak odložení, protože je v "hh: mm: SS".</span><span class="sxs-lookup"><span data-stu-id="e1b99-115">Note that the first colon is enclosed in single quotation marks, because it is not intended to be a delimiting character as it is in "hh:mm:ss".</span></span> <span data-ttu-id="e1b99-116">V jiné jazykové verzi se formát může zobrazit jako "dnes je: 05.30.31 pátek, březen 02, 2012".</span><span class="sxs-lookup"><span data-stu-id="e1b99-116">In another culture, the format might appear as "Today is: 05.30.31 Friday March 02, 2012".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1b99-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="e1b99-117">See also</span></span>

- [<span data-ttu-id="e1b99-118">DateTimePicker – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="e1b99-118">DateTimePicker Control</span></span>](datetimepicker-control-windows-forms.md)
- [<span data-ttu-id="e1b99-119">Postupy: Nastavení a vracení kalendářních dat pomocí ovládacího prvku Windows Forms DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="e1b99-119">How to: Set and Return Dates with the Windows Forms DateTimePicker Control</span></span>](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
