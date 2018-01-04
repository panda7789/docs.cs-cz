---
title: "Postupy: Zobrazení data ve vlastním formátu pomocí ovládacího prvku Windows Forms DateTimePicker"
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
- DateTimePicker control [Windows Forms], display styles
- examples [Windows Forms], DateTimePicker control
- dates [Windows Forms], displaying in DateTimePicker control
ms.assetid: 39767691-2d2b-46b6-a663-b7901e581a6e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a5f5c7d856991ae8e0bf7caff656bf7010255628
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a><span data-ttu-id="4ad87-102">Postupy: Zobrazení data ve vlastním formátu pomocí ovládacího prvku Windows Forms DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="4ad87-102">How to: Display a Date in a Custom Format with the Windows Forms DateTimePicker Control</span></span>
<span data-ttu-id="4ad87-103">Windows Forms <xref:System.Windows.Forms.DateTimePicker> řízení poskytuje flexibilitu při formátování zobrazení data a časy v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="4ad87-103">The Windows Forms <xref:System.Windows.Forms.DateTimePicker> control gives you flexibility in formatting the display of dates and times in the control.</span></span> <span data-ttu-id="4ad87-104"><xref:System.Windows.Forms.DateTimePicker.Format%2A> Vlastnost umožňuje vybrat z předdefinovaných formátů, uvedené v <xref:System.Windows.Forms.DateTimePickerFormat>.</span><span class="sxs-lookup"><span data-stu-id="4ad87-104">The <xref:System.Windows.Forms.DateTimePicker.Format%2A> property allows you to select from predefined formats, listed in the <xref:System.Windows.Forms.DateTimePickerFormat>.</span></span> <span data-ttu-id="4ad87-105">Pokud žádná z nich je dostačující pro vaše záměry, můžete vytvořit vlastní formát styl pomocí formátu znaky uvedené v <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.</span><span class="sxs-lookup"><span data-stu-id="4ad87-105">If none of these is adequate for your purposes, you can create your own format style using format characters listed in <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.</span></span>  
  
### <a name="to-display-a-custom-format"></a><span data-ttu-id="4ad87-106">Vlastní formát zobrazení</span><span class="sxs-lookup"><span data-stu-id="4ad87-106">To display a custom format</span></span>  
  
1.  <span data-ttu-id="4ad87-107">Nastavte <xref:System.Windows.Forms.DateTimePicker.Format%2A> vlastnost `DateTimePickerFormat.Custom`.</span><span class="sxs-lookup"><span data-stu-id="4ad87-107">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to `DateTimePickerFormat.Custom`.</span></span>  
  
2.  <span data-ttu-id="4ad87-108">Nastavte <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> vlastnost na řetězci formátu.</span><span class="sxs-lookup"><span data-stu-id="4ad87-108">Set the <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> property to a format string.</span></span>  
  
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
  
### <a name="to-add-text-to-the-formatted-value"></a><span data-ttu-id="4ad87-109">Chcete-li přidat text k formátovanou hodnotu</span><span class="sxs-lookup"><span data-stu-id="4ad87-109">To add text to the formatted value</span></span>  
  
1.  <span data-ttu-id="4ad87-110">Pomocí jednoduchých uvozovek uzavřete libovolný znak, který není znak formátu jako "M" nebo oddělovač jako ":".</span><span class="sxs-lookup"><span data-stu-id="4ad87-110">Use single quotation marks to enclose any character that is not a format character like "M" or a delimiter like ":".</span></span> <span data-ttu-id="4ad87-111">Například řetězec formátu níže zobrazí aktuální datum ve formátu "Dnes je: 05:30:31 pátek 02 března 2012" v Czech (Czech Republic) jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="4ad87-111">For example, the format string below displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span>  
  
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
  
     <span data-ttu-id="4ad87-112">V závislosti na nastavení jazykové verze, mohou být změněny žádné znaky, není uzavřený v jednoduchých uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="4ad87-112">Depending on the culture setting, any characters not enclosed in single quotation marks may be changed.</span></span> <span data-ttu-id="4ad87-113">Například řetězec formátu výše zobrazí aktuální datum ve formátu "Dnes je: 05:30:31 pátek 02 března 2012" v Czech (Czech Republic) jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="4ad87-113">For example, the format string above displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span> <span data-ttu-id="4ad87-114">Všimněte si, že první dvojtečkou uzavřen v jednoduchých uvozovkách, protože není určen jako rozdělujících znaků, protože je v hh: mm".</span><span class="sxs-lookup"><span data-stu-id="4ad87-114">Note that the first colon is enclosed in single quotation marks, because it is not intended to be a delimiting character as it is in "hh:mm:ss".</span></span> <span data-ttu-id="4ad87-115">V jinou jazykovou verzi, může být ve formátu zobrazí jako "Dnes je: 05.30.31 pátek 02 března 2012".</span><span class="sxs-lookup"><span data-stu-id="4ad87-115">In another culture, the format might appear as "Today is: 05.30.31 Friday March 02, 2012".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ad87-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="4ad87-116">See Also</span></span>  
 [<span data-ttu-id="4ad87-117">Ovládací prvek DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="4ad87-117">DateTimePicker Control</span></span>](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)  
 [<span data-ttu-id="4ad87-118">Postupy: Nastavení a vracení kalendářních dat pomocí ovládacího prvku Windows Forms DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="4ad87-118">How to: Set and Return Dates with the Windows Forms DateTimePicker Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
