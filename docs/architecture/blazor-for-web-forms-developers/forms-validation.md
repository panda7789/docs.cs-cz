---
title: Formuláře a ověřování
description: Naučte se vytvářet formuláře pomocí ověřování na straně klienta v Blazor .
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- Blazor WebAssembly
ms.date: 09/19/2019
ms.openlocfilehash: 1a99719f59415872510aef051d1f3c73daf53e15
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173273"
---
# <a name="forms-and-validation"></a>Formuláře a ověřování

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Rozhraní Web Forms v ASP.NET zahrnuje sadu ověřovacích ovládacích prvků serveru, které zpracovávají ověřování vstupu uživatele do formuláře ( `RequiredFieldValidator` ,, `CompareValidator` `RangeValidator` a tak dále). Rozhraní Web Forms v ASP.NET také podporuje vazby modelu a ověřování modelu na základě datových poznámek ( `[Required]` ,, `[StringLength]` `[Range]` a tak dále). Logiku ověřování lze vyhovět na serveru i na klientovi pomocí nenáročného ověřování založeného na jazyce JavaScript. `ValidationSummary`Serverový ovládací prvek slouží k zobrazení souhrnu chyb ověřování pro uživatele.

Blazorpodporuje sdílení logiky ověřování mezi klientem i serverem. ASP.NET poskytuje předem připravené JavaScriptové implementace mnoha běžných ověření serveru. V mnoha případech vývojář stále musí psát JavaScript, aby plně implementoval svou logiku ověřování specifickou pro danou aplikaci. Na serveru i klientovi lze použít stejné typy modelů, datové poznámky a logiku ověřování.

Blazorposkytuje sadu vstupních komponent. Vstupní komponenty zpracovávají vazby dat polí na model a ověřují vstup uživatele při odeslání formuláře.

|Vstupní komponenta|Vykreslený HTML element    |
|---------------|-------------------------|
|`InputCheckbox`|`<input type="checkbox">`|
|`InputDate`    |`<input type="date">`    |
|`InputNumber`  |`<input type="number">`  |
|`InputSelect`  |`<select>`               |
|`InputText`    |`<input>`                |
|`InputTextArea`|`<textarea>`             |

`EditForm`Komponenta zabalí tyto vstupní komponenty a orchestruje proces ověření prostřednictvím `EditContext` . Při vytváření objektu `EditForm` určíte, ke které instanci modelu se má vytvořit vazba, pomocí `Model` parametru. Ověřování se obvykle provádí pomocí datových poznámek a je rozšiřitelné. Chcete-li povolit ověřování na základě datových poznámek, přidejte `DataAnnotationsValidator` komponentu jako podřízenou položku `EditForm` . `EditForm`Komponenta poskytuje pohodlnou událost ke zpracování platných ( `OnValidSubmit` ) a neplatných ( `OnInvalidSubmit` ) odesílání. K dispozici je také obecnější `OnSubmit` událost, která umožňuje Trigger a zpracování ověření sami.

Chcete-li zobrazit souhrn chyb ověřování, použijte `ValidationSummary` komponentu. Chcete-li zobrazit ověřovací zprávy pro konkrétní vstupní pole, použijte `ValidationMessage` komponentu a určete výraz lambda pro `For` parametr, který odkazuje na příslušný člen modelu.

Následující typ modelu definuje několik ověřovacích pravidel pomocí datových poznámek:

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

Následující komponenta ukazuje vytvoření formuláře v Blazor závislosti na `Starship` typu modelu:

```razor
<h1>New Ship Entry Form</h1>

<EditForm Model="@starship" OnValidSubmit="@HandleValidSubmit">
    <DataAnnotationsValidator />
    <ValidationSummary />

    <p>
        <label for="identifier">Identifier: </label>
        <InputText id="identifier" @bind-Value="starship.Identifier" />
        <ValidationMessage For="() => starship.Identifier" />
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
        <ValidationMessage For="() => starship.Classification" />
    </p>
    <p>
        <label for="accommodation">Maximum Accommodation: </label>
        <InputNumber id="accommodation" @bind-Value="starship.MaximumAccommodation" />
        <ValidationMessage For="() => starship.MaximumAccommodation" />
    </p>
    <p>
        <label for="valid">Engineering Approval: </label>
        <InputCheckbox id="valid" @bind-Value="starship.IsValidatedDesign" />
        <ValidationMessage For="() => starship.IsValidatedDesign" />
    </p>
    <p>
        <label for="productionDate">Production Date: </label>
        <InputDate id="productionDate" @bind-Value="starship.ProductionDate" />
        <ValidationMessage For="() => starship.ProductionDate" />
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

Po odeslání formuláře se data vázaná na model neuložila do žádného úložiště dat, jako je databáze. V Blazor WebAssembly aplikaci je třeba data odeslat na server. Například pomocí požadavku HTTP POST. V Blazor serverové aplikaci jsou již data na serveru, ale musí být trvalá. Manipulace s přístupem k datům v Blazor aplikacích je předmětem části [řešení problémů s daty](data.md) .

## <a name="additional-resources"></a>Další zdroje informací

Další informace o [formulářích a ověřování](/aspnet/core/blazor/forms-validation) v Blazor aplikacích najdete v Blazor dokumentaci.

>[!div class="step-by-step"]
>[Předchozí](state-management.md) 
> [Další](data.md)
