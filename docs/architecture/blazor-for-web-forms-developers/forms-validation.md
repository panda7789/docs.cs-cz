---
title: Formuláře a ověřování
description: Naučte se vytvářet formuláře pomocí ověřování na straně klienta v Blazor.
author: danroth27
ms.author: daroth
ms.date: 09/19/2019
ms.openlocfilehash: 40b0c4ecce15032b0ae834fe3100414abd7e4e59
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183929"
---
# <a name="forms-and-validation"></a><span data-ttu-id="63ed4-103">Formuláře a ověřování</span><span class="sxs-lookup"><span data-stu-id="63ed4-103">Forms and validation</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="63ed4-104">Rozhraní Web Forms v ASP.NET zahrnuje sadu ověřovacích ovládacích prvků serveru, které zpracovávají ověřování vstupu uživatele do formuláře (`RequiredFieldValidator` `RangeValidator`, `CompareValidator`, a tak dále).</span><span class="sxs-lookup"><span data-stu-id="63ed4-104">The ASP.NET Web Forms framework includes a set of validation server controls that handle validating user input entered into a form (`RequiredFieldValidator`, `CompareValidator`, `RangeValidator`, and so on).</span></span> <span data-ttu-id="63ed4-105">Rozhraní Web Forms v ASP.NET také podporuje vazby modelu a ověřování modelu na základě datových poznámek (`[Required]` `[Range]`, `[StringLength]`, a tak dále).</span><span class="sxs-lookup"><span data-stu-id="63ed4-105">The ASP.NET Web Forms framework also supports model binding and validating the model based on data annotations (`[Required]`, `[StringLength]`, `[Range]`, and so on).</span></span> <span data-ttu-id="63ed4-106">Logiku ověřování lze vyhovět na serveru i na klientovi pomocí nenáročného ověřování založeného na jazyce JavaScript.</span><span class="sxs-lookup"><span data-stu-id="63ed4-106">The validation logic can be enforced both on the server and on the client using unobtrusive JavaScript-based validation.</span></span> <span data-ttu-id="63ed4-107">`ValidationSummary` Serverový ovládací prvek slouží k zobrazení souhrnu chyb ověřování pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="63ed4-107">The `ValidationSummary` server control is used to display a summary of the validation errors to the user.</span></span>

<span data-ttu-id="63ed4-108">Blazor podporuje sdílení ověřovací logiky mezi klientem i serverem.</span><span class="sxs-lookup"><span data-stu-id="63ed4-108">Blazor supports the sharing of validation logic between both the client and the server.</span></span> <span data-ttu-id="63ed4-109">ASP.NET poskytuje předem připravené JavaScriptové implementace mnoha běžných ověření serveru.</span><span class="sxs-lookup"><span data-stu-id="63ed4-109">ASP.NET provides pre-built JavaScript implementations of many common server validations.</span></span> <span data-ttu-id="63ed4-110">V mnoha případech vývojář stále musí psát JavaScript, aby plně implementoval svou logiku ověřování specifickou pro danou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="63ed4-110">In many cases, the developer still has to write JavaScript to fully implement their app-specific validation logic.</span></span> <span data-ttu-id="63ed4-111">Na serveru i klientovi lze použít stejné typy modelů, datové poznámky a logiku ověřování.</span><span class="sxs-lookup"><span data-stu-id="63ed4-111">The same model types, data annotations, and validation logic can be used on both the server and client.</span></span>

<span data-ttu-id="63ed4-112">Blazor poskytuje sadu vstupních komponent.</span><span class="sxs-lookup"><span data-stu-id="63ed4-112">Blazor provides a set of input components.</span></span> <span data-ttu-id="63ed4-113">Vstupní komponenty zpracovávají vazby dat polí na model a ověřují vstup uživatele při odeslání formuláře.</span><span class="sxs-lookup"><span data-stu-id="63ed4-113">The input components handle binding field data to a model and validating the user input when the form is submitted.</span></span>

|<span data-ttu-id="63ed4-114">Vstupní komponenta</span><span class="sxs-lookup"><span data-stu-id="63ed4-114">Input component</span></span>|<span data-ttu-id="63ed4-115">Vykreslený HTML element</span><span class="sxs-lookup"><span data-stu-id="63ed4-115">Rendered HTML element</span></span>    |
|---------------|-------------------------|
|`InputCheckbox`|`<input type="checkbox">`|
|`InputDate`    |`<input type="date">`    |
|`InputNumber`  |`<input type="number">`  |
|`InputSelect`  |`<select>`               |
|`InputText`    |`<input>`                |
|`InputTextArea`|`<textarea>`             |

<span data-ttu-id="63ed4-116">Komponenta zabalí tyto vstupní komponenty a orchestruje proces ověření `EditContext`prostřednictvím. `EditForm`</span><span class="sxs-lookup"><span data-stu-id="63ed4-116">The `EditForm` component wraps these input components and orchestrates the validation process through an `EditContext`.</span></span> <span data-ttu-id="63ed4-117">Při vytváření objektu `EditForm`určíte, ke které instanci modelu se má vytvořit vazba `Model` , pomocí parametru.</span><span class="sxs-lookup"><span data-stu-id="63ed4-117">When creating an `EditForm`, you specify what model instance to bind to using the `Model` parameter.</span></span> <span data-ttu-id="63ed4-118">Ověřování se obvykle provádí pomocí datových poznámek a je rozšiřitelné.</span><span class="sxs-lookup"><span data-stu-id="63ed4-118">Validation is typically done using data annotations, and it's extensible.</span></span> <span data-ttu-id="63ed4-119">Chcete-li povolit ověřování na základě datových poznámek, `DataAnnotationsValidator` přidejte komponentu jako podřízenou položku `EditForm`.</span><span class="sxs-lookup"><span data-stu-id="63ed4-119">To enable data annotation-based validation, add the `DataAnnotationsValidator` component as a child of the `EditForm`.</span></span> <span data-ttu-id="63ed4-120">Komponenta poskytuje pohodlnou událost ke zpracování platných (`OnValidSubmit`) a neplatných`OnInvalidSubmit`() odesílání. `EditForm`</span><span class="sxs-lookup"><span data-stu-id="63ed4-120">The `EditForm` component provides a convenient event for handling valid (`OnValidSubmit`) and invalid (`OnInvalidSubmit`) submissions.</span></span> <span data-ttu-id="63ed4-121">K dispozici je také obecnější `OnSubmit` událost, která umožňuje Trigger a zpracování ověření sami.</span><span class="sxs-lookup"><span data-stu-id="63ed4-121">There's also a more generic `OnSubmit` event that lets you trigger and handle the validation yourself.</span></span>

<span data-ttu-id="63ed4-122">Chcete-li zobrazit souhrn chyb ověřování, použijte `ValidationSummary` komponentu.</span><span class="sxs-lookup"><span data-stu-id="63ed4-122">To display a validation error summary, use the `ValidationSummary` component.</span></span> <span data-ttu-id="63ed4-123">Chcete-li zobrazit ověřovací zprávy pro konkrétní vstupní pole, použijte `ValidationMessage` komponentu a určete výraz lambda `For` pro parametr, který odkazuje na příslušný člen modelu.</span><span class="sxs-lookup"><span data-stu-id="63ed4-123">To display validation messages for a specific input field, use the `ValidationMessage` component, specifying a lambda expression for the `For` parameter that points to the appropriate model member.</span></span>

<span data-ttu-id="63ed4-124">Následující typ modelu definuje několik ověřovacích pravidel pomocí datových poznámek:</span><span class="sxs-lookup"><span data-stu-id="63ed4-124">The following model type defines several validation rules using data annotations:</span></span>

```csharp
using System;
using System.ComponentModel.DataAnnotations;

public class Starship
{
    [Required]
    [StringLength(16, 
        ErrorMessage = "Identifier too long (16 character limit).")]
    public string Identifier { get; set; }

    public string Description { get; set; }

    [Required]
    public string Classification { get; set; }

    [Range(1, 100000, 
        ErrorMessage = "Accommodation invalid (1-100000).")]
    public int MaximumAccommodation { get; set; }

    [Required]
    [Range(typeof(bool), "true", "true", 
        ErrorMessage = "This form disallows unapproved ships.")]
    public bool IsValidatedDesign { get; set; }

    [Required]
    public DateTime ProductionDate { get; set; }
}
```

<span data-ttu-id="63ed4-125">Následující komponenta ukazuje vytvoření formuláře v Blazor podle `Starship` typu modelu:</span><span class="sxs-lookup"><span data-stu-id="63ed4-125">The following component demonstrates building a form in Blazor based on the `Starship` model type:</span></span>

```razor
<h1>New Ship Entry Form</h1>

<EditForm Model="@starship" OnValidSubmit="@HandleValidSubmit">
    <DataAnnotationsValidator />
    <ValidationSummary />

    <p>
        <label for="identifier">Identifier: </label>
        <InputText id="identifier" @bind-Value="starship.Identifier" />
        <ValidationMessage For="() => "starship.Identifier" />
    </p>
    <p>
        <label for="description">Description (optional): </label>
        <InputTextArea id="description" @bind-Value="starship.Description" />
    </p>
    <p>
        <label for="classification">Primary Classification: </label>
        <InputSelect id="classification" @bind-Value="starship.Classification">
            <option value="">Select classification ...</option>
            <option value="Exploration">Exploration</option>
            <option value="Diplomacy">Diplomacy</option>
            <option value="Defense">Defense</option>
        </InputSelect>
        <ValidationMessage For="() => "starship.Classification" />
    </p>
    <p>
        <label for="accommodation">Maximum Accommodation: </label>
        <InputNumber id="accommodation" @bind-Value="starship.MaximumAccommodation" />
        <ValidationMessage For="() => "starship.MaximumAccommodation" />
    </p>
    <p>
        <label for="valid">Engineering Approval: </label>
        <InputCheckbox id="valid" @bind-Value="starship.IsValidatedDesign" />
        <ValidationMessage For="() => "starship.IsValidatedDesign" />
    </p>
    <p>
        <label for="productionDate">Production Date: </label>
        <InputDate id="productionDate" @bind-Value="starship.ProductionDate" />
        <ValidationMessage For="() => "starship.ProductionDate" />
    </p>

    <button type="submit">Submit</button>
</EditForm>

@code {
    private Starship starship = new Starship();

    private void HandleValidSubmit()
    {
        // Save the data
    }
}
```

<span data-ttu-id="63ed4-126">Po odeslání formuláře se data vázaná na model neuložila do žádného úložiště dat, jako je databáze.</span><span class="sxs-lookup"><span data-stu-id="63ed4-126">After the form submission, the model-bound data hasn't been saved to any data store, like a database.</span></span> <span data-ttu-id="63ed4-127">V aplikaci WebAssembly v Blazor musí být data odeslána na server.</span><span class="sxs-lookup"><span data-stu-id="63ed4-127">In a Blazor WebAssembly app, the data must be sent to the server.</span></span> <span data-ttu-id="63ed4-128">Například pomocí požadavku HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="63ed4-128">For example, using an HTTP POST request.</span></span> <span data-ttu-id="63ed4-129">V aplikaci Blazor serveru se data na serveru již nacházejí, ale musí být trvalá.</span><span class="sxs-lookup"><span data-stu-id="63ed4-129">In a Blazor Server app, the data is already on the server, but it must be persisted.</span></span> <span data-ttu-id="63ed4-130">Manipulace s přístupem k datům v aplikacích Blazor je předmětem části [řešení problémů s daty](data.md) .</span><span class="sxs-lookup"><span data-stu-id="63ed4-130">Handling data access in Blazor apps is the subject of the [Dealing with data](data.md) section.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="63ed4-131">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="63ed4-131">Additional resources</span></span>

<span data-ttu-id="63ed4-132">Další informace o [formulářích a ověřování](/aspnet/core/blazor/forms-validation) v aplikacích Blazor najdete v dokumentaci k Blazor.</span><span class="sxs-lookup"><span data-stu-id="63ed4-132">For more information on [forms and validation](/aspnet/core/blazor/forms-validation) in Blazor apps, see the Blazor documentation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="63ed4-133">[Předchozí](state-management.md)
>[Další](data.md)</span><span class="sxs-lookup"><span data-stu-id="63ed4-133">[Previous](state-management.md)
[Next](data.md)</span></span>
