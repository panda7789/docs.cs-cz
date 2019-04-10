---
title: 'Postupy: Zobrazení data ve vlastním formátu pomocí ovládacího prvku Windows Forms DateTimePicker'
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
ms.openlocfilehash: 08d5a505229cd434dbf82e8ae4624bb418efd379
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59335937"
---
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a><span data-ttu-id="51480-102">Postupy: Zobrazení data ve vlastním formátu pomocí ovládacího prvku Windows Forms DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="51480-102">How to: Display a Date in a Custom Format with the Windows Forms DateTimePicker Control</span></span>
<span data-ttu-id="51480-103">Windows Forms <xref:System.Windows.Forms.DateTimePicker> ovládacího prvku poskytuje flexibilitu při formátování zobrazení dat a časů v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="51480-103">The Windows Forms <xref:System.Windows.Forms.DateTimePicker> control gives you flexibility in formatting the display of dates and times in the control.</span></span> <span data-ttu-id="51480-104"><xref:System.Windows.Forms.DateTimePicker.Format%2A> Vlastnost vám umožní vybrat z předdefinovaných formátů, uvedené v <xref:System.Windows.Forms.DateTimePickerFormat>.</span><span class="sxs-lookup"><span data-stu-id="51480-104">The <xref:System.Windows.Forms.DateTimePicker.Format%2A> property allows you to select from predefined formats, listed in the <xref:System.Windows.Forms.DateTimePickerFormat>.</span></span> <span data-ttu-id="51480-105">Pokud žádná z nich je vhodný pro vaše potřeby, můžete vytvořit vlastní styl formátování pomocí formátu znaky uvedené v <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.</span><span class="sxs-lookup"><span data-stu-id="51480-105">If none of these is adequate for your purposes, you can create your own format style using format characters listed in <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.</span></span>  
  
### <a name="to-display-a-custom-format"></a><span data-ttu-id="51480-106">K zobrazení vlastního formátu</span><span class="sxs-lookup"><span data-stu-id="51480-106">To display a custom format</span></span>  
  
1. <span data-ttu-id="51480-107">Nastavte <xref:System.Windows.Forms.DateTimePicker.Format%2A> vlastnost `DateTimePickerFormat.Custom`.</span><span class="sxs-lookup"><span data-stu-id="51480-107">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to `DateTimePickerFormat.Custom`.</span></span>  
  
2. <span data-ttu-id="51480-108">Nastavte <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> nastavte na řetězec formátu.</span><span class="sxs-lookup"><span data-stu-id="51480-108">Set the <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> property to a format string.</span></span>  
  
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
  
### <a name="to-add-text-to-the-formatted-value"></a><span data-ttu-id="51480-109">Chcete-li přidat text formátovaná hodnota</span><span class="sxs-lookup"><span data-stu-id="51480-109">To add text to the formatted value</span></span>  
  
1. <span data-ttu-id="51480-110">Pomocí jednoduchých uvozovek uzavřete libovolný znak, který není znak formátu jako "M" nebo oddělovač, jako je ":".</span><span class="sxs-lookup"><span data-stu-id="51480-110">Use single quotation marks to enclose any character that is not a format character like "M" or a delimiter like ":".</span></span> <span data-ttu-id="51480-111">Například řetězec formátu níže zobrazí aktuální datum ve formátu "Dnes je: 05:30:31. března pátek 02, 2012" v jazykové verze Angličtina (Spojené státy).</span><span class="sxs-lookup"><span data-stu-id="51480-111">For example, the format string below displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span>  
  
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
  
     <span data-ttu-id="51480-112">V závislosti na nastavení jazykové verze, nejspíš se změní všechny znaky, není uzavřen v jednoduchých uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="51480-112">Depending on the culture setting, any characters not enclosed in single quotation marks may be changed.</span></span> <span data-ttu-id="51480-113">Například řetězec formátu výše zobrazuje aktuální datum ve formátu "Dnes je: 05:30:31. března pátek 02, 2012" v jazykové verze Angličtina (Spojené státy).</span><span class="sxs-lookup"><span data-stu-id="51480-113">For example, the format string above displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span> <span data-ttu-id="51480-114">Protože ale nemají být oddělovací znak je "hh: mm:", mějte na paměti, že první dvojtečku uzavřen v jednoduchých uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="51480-114">Note that the first colon is enclosed in single quotation marks, because it is not intended to be a delimiting character as it is in "hh:mm:ss".</span></span> <span data-ttu-id="51480-115">V jiné jazykové verze, může být ve formátu zobrazí jako "Dnes je: 05.30.31 pátek březen 02, 2012".</span><span class="sxs-lookup"><span data-stu-id="51480-115">In another culture, the format might appear as "Today is: 05.30.31 Friday March 02, 2012".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51480-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="51480-116">See also</span></span>

- [<span data-ttu-id="51480-117">Ovládací prvek DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="51480-117">DateTimePicker Control</span></span>](datetimepicker-control-windows-forms.md)
- [<span data-ttu-id="51480-118">Postupy: Nastavení a vracení kalendářních dat pomocí ovládacího prvku Windows Forms DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="51480-118">How to: Set and Return Dates with the Windows Forms DateTimePicker Control</span></span>](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
