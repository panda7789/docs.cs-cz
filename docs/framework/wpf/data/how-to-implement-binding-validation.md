---
title: 'Postupy: Implementace ověření připojení'
description: Naučte se používat ověřování vazby k poskytnutí vizuální zpětné vazby uživateli, když je v Windows Presentation Foundation (WPF) zadána neplatná hodnota.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validation of binding [WPF]
- data binding [WPF], validation of binding
- binding [WPF], validation of
ms.assetid: eb98b33d-9866-49ae-b981-bc5ff20d607a
ms.openlocfilehash: 0813be9f79a83a9dae26db1dadb58b5e973339fd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617879"
---
# <a name="how-to-implement-binding-validation"></a><span data-ttu-id="f5121-103">Postupy: Implementace ověření připojení</span><span class="sxs-lookup"><span data-stu-id="f5121-103">How to: Implement Binding Validation</span></span>

<span data-ttu-id="f5121-104">Tento příklad ukazuje, jak použít <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> aktivační proceduru a se stylem k poskytnutí vizuální zpětné vazby, která uživatele informují o tom, že je zadána neplatná hodnota na základě vlastního ověřovacího pravidla.</span><span class="sxs-lookup"><span data-stu-id="f5121-104">This example shows how to use an <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> and a style trigger to provide visual feedback to inform the user when an invalid value is entered, based on a custom validation rule.</span></span>

## <a name="example"></a><span data-ttu-id="f5121-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="f5121-105">Example</span></span>

<span data-ttu-id="f5121-106">Textový obsah <xref:System.Windows.Controls.TextBox> v následujícím příkladu je vázán na `Age` vlastnost (typu int) objektu zdroje vazby s názvem `ods` .</span><span class="sxs-lookup"><span data-stu-id="f5121-106">The text content of the <xref:System.Windows.Controls.TextBox> in the following example is bound to the `Age` property (of type int) of a binding source object named `ods`.</span></span> <span data-ttu-id="f5121-107">Vazba je nastavená tak, aby používala ověřovací pravidlo s názvem `AgeRangeRule` , aby pokud uživatel zadal jiné než číselné znaky nebo hodnotu menší než 21 nebo větší než 130, zobrazí se vedle textového pole červený vykřičník a v případě, že uživatel přesune ukazatel myši na textové pole, zobrazí se chybová zpráva s chybovou zprávou.</span><span class="sxs-lookup"><span data-stu-id="f5121-107">The binding is set up to use a validation rule named `AgeRangeRule` so that if the user enters non-numeric characters or a value that is smaller than 21 or greater than 130, a red exclamation mark appears next to the text box and a tool tip with the error message appears when the user moves the mouse over the text box.</span></span>

[!code-xaml[BindValidation#2](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#2)]

<span data-ttu-id="f5121-108">Následující příklad ukazuje implementaci `AgeRangeRule` , která dědí z <xref:System.Windows.Controls.ValidationRule> a Přepisuje <xref:System.Windows.Controls.ValidationRule.Validate%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="f5121-108">The following example shows the implementation of `AgeRangeRule`, which inherits from <xref:System.Windows.Controls.ValidationRule> and overrides the <xref:System.Windows.Controls.ValidationRule.Validate%2A> method.</span></span> <span data-ttu-id="f5121-109">`Int32.Parse`Metoda je volána na hodnotu, aby se zajistilo, že neobsahuje neplatné znaky.</span><span class="sxs-lookup"><span data-stu-id="f5121-109">The `Int32.Parse` method is called on the value to make sure that it does not contain any invalid characters.</span></span> <span data-ttu-id="f5121-110"><xref:System.Windows.Controls.ValidationRule.Validate%2A>Metoda vrátí hodnotu <xref:System.Windows.Controls.ValidationResult> , která označuje, zda je hodnota platná na základě toho, zda je při analýze zachycena výjimka a zda je hodnota stáří mimo dolní a horní mez.</span><span class="sxs-lookup"><span data-stu-id="f5121-110">The <xref:System.Windows.Controls.ValidationRule.Validate%2A> method returns a <xref:System.Windows.Controls.ValidationResult> that indicates if the value is valid based on whether an exception is caught during the parsing and whether the age value is outside of the lower and upper bounds.</span></span>

[!code-csharp[BindValidation#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/AgeRangeRule.cs#3)]
[!code-vb[BindValidation#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindValidation/VisualBasic/AgeRangeRule.vb#3)]

<span data-ttu-id="f5121-111">Následující příklad ukazuje vlastní <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` , který vytvoří červený vykřičník pro upozornění uživatele na chybu ověřování.</span><span class="sxs-lookup"><span data-stu-id="f5121-111">The following example shows the custom <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` that creates a red exclamation mark to notify the user of a validation error.</span></span> <span data-ttu-id="f5121-112">Šablony ovládacích prvků slouží k předefinování vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f5121-112">Control templates are used to redefine the appearance of a control.</span></span>

[!code-xaml[BindValidation#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#4)]

<span data-ttu-id="f5121-113">Jak je znázorněno v následujícím příkladu, <xref:System.Windows.Controls.ToolTip> zobrazuje se chybová zpráva, která je vytvořena pomocí stylu s názvem `textBoxInError` .</span><span class="sxs-lookup"><span data-stu-id="f5121-113">As shown in the following example, the <xref:System.Windows.Controls.ToolTip> that shows the error message is created using the style named `textBoxInError`.</span></span> <span data-ttu-id="f5121-114">Pokud <xref:System.Windows.Controls.Validation.HasError%2A> je hodnota `true` , aktivační událost nastaví popisek nástroje aktuální <xref:System.Windows.Controls.TextBox> na jeho první chybu ověření.</span><span class="sxs-lookup"><span data-stu-id="f5121-114">If the value of <xref:System.Windows.Controls.Validation.HasError%2A> is `true`, the trigger sets the tool tip of the current <xref:System.Windows.Controls.TextBox> to its first validation error.</span></span> <span data-ttu-id="f5121-115"><xref:System.Windows.Data.Binding.RelativeSource%2A>Je nastaven na <xref:System.Windows.Data.RelativeSourceMode.Self> a odkazuje na aktuální prvek.</span><span class="sxs-lookup"><span data-stu-id="f5121-115">The <xref:System.Windows.Data.Binding.RelativeSource%2A> is set to <xref:System.Windows.Data.RelativeSourceMode.Self>, referring to the current element.</span></span>

[!code-xaml[BindValidation#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#5)]

<span data-ttu-id="f5121-116">Úplný příklad najdete v tématu [Ukázka ověření vazby](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/BindValidation).</span><span class="sxs-lookup"><span data-stu-id="f5121-116">For the complete example, see [Bind Validation sample](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/BindValidation).</span></span>
  
<span data-ttu-id="f5121-117">Všimněte si, že pokud neposkytnete vlastní <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> výchozí šablonu chyb, zobrazí se uživateli při chybě ověření vizuální zpětná vazba.</span><span class="sxs-lookup"><span data-stu-id="f5121-117">Note that if you do not provide a custom <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> the default error template appears to provide visual feedback to the user when there is a validation error.</span></span> <span data-ttu-id="f5121-118">Další informace najdete v tématu věnovaném ověření dat v [přehledu datových vazeb](../../../desktop-wpf/data/data-binding-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="f5121-118">See "Data Validation" in [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md) for more information.</span></span> <span data-ttu-id="f5121-119">Také [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje integrované ověřovací pravidlo, které zachycuje výjimky, které jsou vyvolány během aktualizace vlastnosti zdroje vazby.</span><span class="sxs-lookup"><span data-stu-id="f5121-119">Also, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] provides a built-in validation rule that catches exceptions that are thrown during the update of the binding source property.</span></span> <span data-ttu-id="f5121-120">Další informace naleznete v tématu <xref:System.Windows.Controls.ExceptionValidationRule>.</span><span class="sxs-lookup"><span data-stu-id="f5121-120">For more information, see <xref:System.Windows.Controls.ExceptionValidationRule>.</span></span>

## <a name="see-also"></a><span data-ttu-id="f5121-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f5121-121">See also</span></span>

- [<span data-ttu-id="f5121-122">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="f5121-122">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="f5121-123">– postupy</span><span class="sxs-lookup"><span data-stu-id="f5121-123">How-to Topics</span></span>](data-binding-how-to-topics.md)
