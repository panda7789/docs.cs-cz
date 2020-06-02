---
title: Vlastnosti závislosti
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
ms.openlocfilehash: 476ef1bb1ac5ec1f551979c64a41cbae55c554bc
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280254"
---
# <a name="dependency-properties"></a><span data-ttu-id="15288-102">Vlastnosti závislosti</span><span class="sxs-lookup"><span data-stu-id="15288-102">Dependency Properties</span></span>
<span data-ttu-id="15288-103">Vlastnost závislosti (DP) je obvyklá vlastnost, která ukládá její hodnotu do úložiště vlastností místo jejich uložení do proměnné typu (pole), například.</span><span class="sxs-lookup"><span data-stu-id="15288-103">A dependency property (DP) is a regular property that stores its value in a property store instead of storing it in a type variable (field), for example.</span></span>

 <span data-ttu-id="15288-104">Připojená vlastnost Dependency je druh vlastnosti závislosti, která se modeluje jako statické metody Get a set, které představují vlastnosti popisující vztahy mezi objekty a jejich kontejnery (například umístění `Button` objektu na `Panel` kontejneru).</span><span class="sxs-lookup"><span data-stu-id="15288-104">An attached dependency property is a kind of dependency property modeled as static Get and Set methods representing "properties" describing relationships between objects and their containers (e.g., the position of a `Button` object on a `Panel` container).</span></span>

 <span data-ttu-id="15288-105">✔️ Zadejte vlastnosti závislosti, pokud potřebujete vlastnosti pro podporu funkcí WPF, jako jsou například styly, triggery, datové vazby, animace, dynamické prostředky a dědičnost.</span><span class="sxs-lookup"><span data-stu-id="15288-105">✔️ DO provide the dependency properties, if you need the properties to support WPF features such as styling, triggers, data binding, animations, dynamic resources, and inheritance.</span></span>

## <a name="dependency-property-design"></a><span data-ttu-id="15288-106">Návrh vlastnosti závislosti</span><span class="sxs-lookup"><span data-stu-id="15288-106">Dependency Property Design</span></span>
 <span data-ttu-id="15288-107"><xref:System.Windows.DependencyObject>při implementaci vlastností závislosti ✔️ dědit z nebo jeden z jeho podtypů.</span><span class="sxs-lookup"><span data-stu-id="15288-107">✔️ DO inherit from <xref:System.Windows.DependencyObject>, or one of its subtypes, when implementing dependency properties.</span></span> <span data-ttu-id="15288-108">Typ poskytuje velmi efektivní implementaci úložiště vlastností a automaticky podporuje datovou vazbu WPF.</span><span class="sxs-lookup"><span data-stu-id="15288-108">The type provides a very efficient implementation of a property store and automatically supports WPF data binding.</span></span>

 <span data-ttu-id="15288-109">✔️ poskytují regulární vlastnost CLR a veřejné statické pole jen pro čtení, které ukládá instanci <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> pro každou vlastnost závislosti.</span><span class="sxs-lookup"><span data-stu-id="15288-109">✔️ DO provide a regular CLR property and public static read-only field storing an instance of <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> for each dependency property.</span></span>

 <span data-ttu-id="15288-110">✔️ implementovat vlastnosti závislosti voláním metod instance <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> a <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="15288-110">✔️ DO implement dependency properties by calling instance methods <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> and <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.</span></span>

 <span data-ttu-id="15288-111">✔️ Pojmenujte statické pole vlastnosti závislosti příponou názvu vlastnosti s vlastností.</span><span class="sxs-lookup"><span data-stu-id="15288-111">✔️ DO name the dependency property static field by suffixing the name of the property with "Property."</span></span>

 <span data-ttu-id="15288-112">❌Nenastavte výchozí hodnoty vlastností závislosti explicitně v kódu; místo toho je nastavte v metadatech.</span><span class="sxs-lookup"><span data-stu-id="15288-112">❌ DO NOT set default values of dependency properties explicitly in code; set them in metadata instead.</span></span>

 <span data-ttu-id="15288-113">Pokud nastavíte výchozí nastavení vlastnosti explicitně, můžete zabránit tomu, aby se tato vlastnost nastavila některými implicitními prostředky, jako je styl.</span><span class="sxs-lookup"><span data-stu-id="15288-113">If you set a property default explicitly, you might prevent that property from being set by some implicit means, such as a styling.</span></span>

 <span data-ttu-id="15288-114">❌Neumísťujte kód do jiných přístupových objektů vlastností než standardní kód pro přístup k statickému poli.</span><span class="sxs-lookup"><span data-stu-id="15288-114">❌ DO NOT put code in the property accessors other than the standard code to access the static field.</span></span>

 <span data-ttu-id="15288-115">Tento kód nebude proveden, pokud je vlastnost nastavena pomocí implicitních prostředků, jako je například styl, protože styl používá přímo pole static.</span><span class="sxs-lookup"><span data-stu-id="15288-115">That code won’t execute if the property is set by implicit means, such as a styling, because styling uses the static field directly.</span></span>

 <span data-ttu-id="15288-116">❌Nepoužívejte vlastnosti závislosti k ukládání zabezpečených dat.</span><span class="sxs-lookup"><span data-stu-id="15288-116">❌ DO NOT use dependency properties to store secure data.</span></span> <span data-ttu-id="15288-117">K vlastnostem soukromé závislosti lze přistupovat i na veřejném.</span><span class="sxs-lookup"><span data-stu-id="15288-117">Even private dependency properties can be accessed publicly.</span></span>

## <a name="attached-dependency-property-design"></a><span data-ttu-id="15288-118">Návrh vlastnosti připojené závislosti</span><span class="sxs-lookup"><span data-stu-id="15288-118">Attached Dependency Property Design</span></span>
 <span data-ttu-id="15288-119">Vlastnosti závislosti popsané v předchozí části označují vnitřní vlastnosti deklarovaného typu; `Text`vlastnost je například vlastnost `TextButton` , která ji deklaruje.</span><span class="sxs-lookup"><span data-stu-id="15288-119">Dependency properties described in the preceding section represent intrinsic properties of the declaring type; for example, the `Text` property is a property of `TextButton`, which declares it.</span></span> <span data-ttu-id="15288-120">Speciálním druhem vlastnosti závislosti je vlastnost připojené závislosti.</span><span class="sxs-lookup"><span data-stu-id="15288-120">A special kind of dependency property is the attached dependency property.</span></span>

 <span data-ttu-id="15288-121">Klasickým příkladem připojené vlastnosti je <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="15288-121">A classic example of an attached property is the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="15288-122">Vlastnost představuje pozici sloupce tlačítko (ne mřížka), ale je relevantní pouze v případě, že je tlačítko obsaženo v mřížce, a proto je "připojené" k tlačítkům na základě mřížky.</span><span class="sxs-lookup"><span data-stu-id="15288-122">The property represents Button’s (not Grid’s) column position, but it is only relevant if the Button is contained in a Grid, and so it's "attached" to Buttons by Grids.</span></span>

```xaml
<Grid>
    <Grid.ColumnDefinitions>
        <ColumnDefinition />
        <ColumnDefinition />
    </Grid.ColumnDefinitions>

    <Button Grid.Column="0">Click</Button>
    <Button Grid.Column="1">Clack</Button>
</Grid>
```

 <span data-ttu-id="15288-123">Definice připojené vlastnosti vypadá hlavně podobně jako vlastnost běžné závislosti s tím rozdílem, že přistupující objekty jsou reprezentovány pomocí statických metod get a set:</span><span class="sxs-lookup"><span data-stu-id="15288-123">The definition of an attached property looks mostly like that of a regular dependency property, except that the accessors are represented by static Get and Set methods:</span></span>

```csharp
public class Grid {

    public static int GetColumn(DependencyObject obj) {
        return (int)obj.GetValue(ColumnProperty);
    }

    public static void SetColumn(DependencyObject obj, int value) {
        obj.SetValue(ColumnProperty,value);
    }

    public static readonly DependencyProperty ColumnProperty =
        DependencyProperty.RegisterAttached(
            "Column",
            typeof(int),
            typeof(Grid)
    );
}
```

## <a name="dependency-property-validation"></a><span data-ttu-id="15288-124">Ověřování vlastností závislosti</span><span class="sxs-lookup"><span data-stu-id="15288-124">Dependency Property Validation</span></span>
 <span data-ttu-id="15288-125">Vlastnosti často implementují, co se nazývá ověřování.</span><span class="sxs-lookup"><span data-stu-id="15288-125">Properties often implement what is called validation.</span></span> <span data-ttu-id="15288-126">Logika ověřování se spustí, když se provede pokus o změnu hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="15288-126">Validation logic executes when an attempt is made to change the value of a property.</span></span>

 <span data-ttu-id="15288-127">Přístupové objekty vlastnosti bohužel nemůžou obsahovat libovolný ověřovací kód.</span><span class="sxs-lookup"><span data-stu-id="15288-127">Unfortunately dependency property accessors cannot contain arbitrary validation code.</span></span> <span data-ttu-id="15288-128">Místo toho je nutné při registraci vlastnosti zadat logiku ověřování vlastností závislostí.</span><span class="sxs-lookup"><span data-stu-id="15288-128">Instead, dependency property validation logic needs to be specified during property registration.</span></span>

 <span data-ttu-id="15288-129">❌Do přístupových objektů vlastnosti neumísťujte logiku ověřování vlastností závislostí.</span><span class="sxs-lookup"><span data-stu-id="15288-129">❌ DO NOT put dependency property validation logic in the property’s accessors.</span></span> <span data-ttu-id="15288-130">Místo toho předejte metodu zpětného volání ověření do `DependencyProperty.Register` metody.</span><span class="sxs-lookup"><span data-stu-id="15288-130">Instead, pass a validation callback to `DependencyProperty.Register` method.</span></span>

## <a name="dependency-property-change-notifications"></a><span data-ttu-id="15288-131">Oznámení o změně vlastnosti závislosti</span><span class="sxs-lookup"><span data-stu-id="15288-131">Dependency Property Change Notifications</span></span>
 <span data-ttu-id="15288-132">❌Neimplementujte logiku oznámení změn v přístupových parametrech vlastnosti závislosti.</span><span class="sxs-lookup"><span data-stu-id="15288-132">❌ DO NOT implement change notification logic in dependency property accessors.</span></span> <span data-ttu-id="15288-133">Vlastnosti závislosti mají vestavěnou funkci oznámení změn, kterou je nutné použít při poskytnutí zpětného volání oznámení o změně do <xref:System.Windows.PropertyMetadata> .</span><span class="sxs-lookup"><span data-stu-id="15288-133">Dependency properties have a built-in change notifications feature that must be used by supplying a change notification callback to the <xref:System.Windows.PropertyMetadata>.</span></span>

## <a name="dependency-property-value-coercion"></a><span data-ttu-id="15288-134">Hodnota vlastnosti závislosti – vynucení</span><span class="sxs-lookup"><span data-stu-id="15288-134">Dependency Property Value Coercion</span></span>
 <span data-ttu-id="15288-135">K převodu vlastnosti dojde, pokud je hodnota zadaná metodě setter vlastnosti změněna před samotným úpravou úložiště vlastností.</span><span class="sxs-lookup"><span data-stu-id="15288-135">Property coercion takes place when the value given to a property setter is modified by the setter before the property store is actually modified.</span></span>

 <span data-ttu-id="15288-136">❌Neimplementujte logiku vynucení v přístupových parametrech vlastnosti závislosti.</span><span class="sxs-lookup"><span data-stu-id="15288-136">❌ DO NOT implement coercion logic in dependency property accessors.</span></span>

 <span data-ttu-id="15288-137">Vlastnosti závislosti mají integrovanou funkci pro vynucení a lze ji použít poskytnutím zpětného volání do `PropertyMetadata` .</span><span class="sxs-lookup"><span data-stu-id="15288-137">Dependency properties have a built-in coercion feature, and it can be used by supplying a coercion callback to the `PropertyMetadata`.</span></span>

 <span data-ttu-id="15288-138">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="15288-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="15288-139">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="15288-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="15288-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="15288-140">See also</span></span>

- [<span data-ttu-id="15288-141">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="15288-141">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="15288-142">Běžné vzory návrhu</span><span class="sxs-lookup"><span data-stu-id="15288-142">Common Design Patterns</span></span>](common-design-patterns.md)
