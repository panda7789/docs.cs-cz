---
title: Vlastnosti závislosti
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75c83dc75d1c86c89169fcc54220ced2a195bfbe
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44079084"
---
# <a name="dependency-properties"></a><span data-ttu-id="7d9b1-102">Vlastnosti závislosti</span><span class="sxs-lookup"><span data-stu-id="7d9b1-102">Dependency Properties</span></span>
<span data-ttu-id="7d9b1-103">Vlastnost závislosti (DP) je regulární vlastnost, která uloží svou hodnotu v úložišti vlastností místo ukládání proměnná typu (pole), např.</span><span class="sxs-lookup"><span data-stu-id="7d9b1-103">A dependency property (DP) is a regular property that stores its value in a property store instead of storing it in a type variable (field), for example.</span></span>  
  
 <span data-ttu-id="7d9b1-104">Na vlastnost připojené závislostí je druh vlastnost závislosti nemodelují jako statické metody Get a Set představující "properties" popisující vztahy mezi objekty a jejich kontejnery (například pozici `Button` objektu na `Panel` kontejner).</span><span class="sxs-lookup"><span data-stu-id="7d9b1-104">An attached dependency property is a kind of dependency property modeled as static Get and Set methods representing "properties" describing relationships between objects and their containers (e.g., the position of a `Button` object on a `Panel` container).</span></span>  
  
 <span data-ttu-id="7d9b1-105">**✓ DO** zadejte vlastnosti závislosti, pokud budete potřebovat k podpoře funkce WPF například stylů, aktivační události, vazby dat, animací, dynamické prostředky a dědičnosti vlastností.</span><span class="sxs-lookup"><span data-stu-id="7d9b1-105">**✓ DO** provide the dependency properties, if you need the properties to support WPF features such as styling, triggers, data binding, animations, dynamic resources, and inheritance.</span></span>  
  
## <a name="dependency-property-design"></a><span data-ttu-id="7d9b1-106">Návrh vlastnosti závislosti</span><span class="sxs-lookup"><span data-stu-id="7d9b1-106">Dependency Property Design</span></span>  
 <span data-ttu-id="7d9b1-107">**✓ DO** dědí <xref:System.Windows.DependencyObject>, nebo jeden z jeho podtypech při implementaci vlastností závislostí.</span><span class="sxs-lookup"><span data-stu-id="7d9b1-107">**✓ DO** inherit from <xref:System.Windows.DependencyObject>, or one of its subtypes, when implementing dependency properties.</span></span> <span data-ttu-id="7d9b1-108">Typ poskytuje implementaci velmi efektivní úložiště vlastností a automaticky podporuje datové vazby WPF.</span><span class="sxs-lookup"><span data-stu-id="7d9b1-108">The type provides a very efficient implementation of a property store and automatically supports WPF data binding.</span></span>  
  
 <span data-ttu-id="7d9b1-109">**✓ DO** zadejte regulární vlastnost CLR a veřejné statické jen pro čtení pole ukládání instanci <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> pro každou vlastnost závislosti.</span><span class="sxs-lookup"><span data-stu-id="7d9b1-109">**✓ DO** provide a regular CLR property and public static read-only field storing an instance of <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> for each dependency property.</span></span>  
  
 <span data-ttu-id="7d9b1-110">**✓ DO** implementovat vlastností závislostí voláním metod instance <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> a <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7d9b1-110">**✓ DO** implement dependency properties by calling instance methods <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> and <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="7d9b1-111">**✓ DO** názvů statické pole vlastnosti závislosti suffixing název vlastnosti s "Vlastnost."</span><span class="sxs-lookup"><span data-stu-id="7d9b1-111">**✓ DO** name the dependency property static field by suffixing the name of the property with "Property."</span></span>  
  
 <span data-ttu-id="7d9b1-112">**X DO NOT** explicitně nastavit výchozí hodnoty vlastností závislostí v kódu; nastavte je v metadatech.</span><span class="sxs-lookup"><span data-stu-id="7d9b1-112">**X DO NOT** set default values of dependency properties explicitly in code; set them in metadata instead.</span></span>  
  
 <span data-ttu-id="7d9b1-113">Pokud nastavíte výchozí vlastnost explicitně, by mohly bránit tuto vlastnost z nastavování některé implicitní prostředky, například styl.</span><span class="sxs-lookup"><span data-stu-id="7d9b1-113">If you set a property default explicitly, you might prevent that property from being set by some implicit means, such as a styling.</span></span>  
  
 <span data-ttu-id="7d9b1-114">**X DO NOT** vkládat kód do vlastnosti přistupující objekty než standardní kód pro přístup k statické pole.</span><span class="sxs-lookup"><span data-stu-id="7d9b1-114">**X DO NOT** put code in the property accessors other than the standard code to access the static field.</span></span>  
  
 <span data-ttu-id="7d9b1-115">Statické pole, že kód nebude spuštěno Pokud je nastavena implicitní prostředky, například styl, protože práce se styly používá přímo.</span><span class="sxs-lookup"><span data-stu-id="7d9b1-115">That code won’t execute if the property is set by implicit means, such as a styling, because styling uses the static field directly.</span></span>  
  
 <span data-ttu-id="7d9b1-116">**X DO NOT** zabezpečené data pomocí vlastností závislostí.</span><span class="sxs-lookup"><span data-stu-id="7d9b1-116">**X DO NOT** use dependency properties to store secure data.</span></span> <span data-ttu-id="7d9b1-117">Vlastnosti závislostí i privátní přístupná veřejně.</span><span class="sxs-lookup"><span data-stu-id="7d9b1-117">Even private dependency properties can be accessed publicly.</span></span>  
  
## <a name="attached-dependency-property-design"></a><span data-ttu-id="7d9b1-118">Návrh vlastnosti připojené závislostí</span><span class="sxs-lookup"><span data-stu-id="7d9b1-118">Attached Dependency Property Design</span></span>  
 <span data-ttu-id="7d9b1-119">Vlastnosti závislostí popsaných v předchozí části představují vnitřní vlastnosti deklarujícího typu; například `Text` vlastností je vlastnost `TextButton`, který deklaruje.</span><span class="sxs-lookup"><span data-stu-id="7d9b1-119">Dependency properties described in the preceding section represent intrinsic properties of the declaring type; for example, the `Text` property is a property of `TextButton`, which declares it.</span></span> <span data-ttu-id="7d9b1-120">Zvláštní druh vlastnost závislosti je vlastnost připojené závislosti.</span><span class="sxs-lookup"><span data-stu-id="7d9b1-120">A special kind of dependency property is the attached dependency property.</span></span>  
  
 <span data-ttu-id="7d9b1-121">Klasické příkladem připojené vlastnosti je <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7d9b1-121">A classic example of an attached property is the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="7d9b1-122">Vlastnost představuje pozici sloupce tlačítka (ne mřížky), ale je pouze relevantní tlačítko je součástí do mřížky, takže je "připojeno" k tlačítka pomocí mřížky.</span><span class="sxs-lookup"><span data-stu-id="7d9b1-122">The property represents Button’s (not Grid’s) column position, but it is only relevant if the Button is contained in a Grid, and so it's "attached" to Buttons by Grids.</span></span>  
  
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
  
 <span data-ttu-id="7d9b1-123">Definice připojené vlastnosti vypadá převážně u vlastnosti regulárního závislosti, s tím rozdílem, přístupové objekty jsou reprezentovány statické metody Get a Set:</span><span class="sxs-lookup"><span data-stu-id="7d9b1-123">The definition of an attached property looks mostly like that of a regular dependency property, except that the accessors are represented by static Get and Set methods:</span></span>  
  
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
  
## <a name="dependency-property-validation"></a><span data-ttu-id="7d9b1-124">Ověření vlastností závislostí</span><span class="sxs-lookup"><span data-stu-id="7d9b1-124">Dependency Property Validation</span></span>  
 <span data-ttu-id="7d9b1-125">Vlastnosti často implementovat, co se nazývá ověření.</span><span class="sxs-lookup"><span data-stu-id="7d9b1-125">Properties often implement what is called validation.</span></span> <span data-ttu-id="7d9b1-126">Logiku ověřování provede při pokusu o změnit hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7d9b1-126">Validation logic executes when an attempt is made to change the value of a property.</span></span>  
  
 <span data-ttu-id="7d9b1-127">Bohužel přistupující objekty vlastnosti závislost nemůže obsahovat libovolný ověřovací kód.</span><span class="sxs-lookup"><span data-stu-id="7d9b1-127">Unfortunately dependency property accessors cannot contain arbitrary validation code.</span></span> <span data-ttu-id="7d9b1-128">Místo toho logiku ověření závislostí vlastnost je nutné zadat během registrace vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7d9b1-128">Instead, dependency property validation logic needs to be specified during property registration.</span></span>  
  
 <span data-ttu-id="7d9b1-129">**X DO NOT** chápat logiku ověření pro vlastnost závislosti vlastnosti přistupující objekty.</span><span class="sxs-lookup"><span data-stu-id="7d9b1-129">**X DO NOT** put dependency property validation logic in the property’s accessors.</span></span> <span data-ttu-id="7d9b1-130">Místo toho předat zpětné volání pro ověření do `DependencyProperty.Register` metody.</span><span class="sxs-lookup"><span data-stu-id="7d9b1-130">Instead, pass a validation callback to `DependencyProperty.Register` method.</span></span>  
  
## <a name="dependency-property-change-notifications"></a><span data-ttu-id="7d9b1-131">Oznámení změn vlastností závislosti</span><span class="sxs-lookup"><span data-stu-id="7d9b1-131">Dependency Property Change Notifications</span></span>  
 <span data-ttu-id="7d9b1-132">**X DO NOT** implementovat logiku oznámení změn v přístupové objekty vlastnosti závislosti.</span><span class="sxs-lookup"><span data-stu-id="7d9b1-132">**X DO NOT** implement change notification logic in dependency property accessors.</span></span> <span data-ttu-id="7d9b1-133">Vlastnosti závislosti obsahují integrované změnit funkci oznámení, které musí být použito poskytnutím zpětné volání oznámení změn, aby <xref:System.Windows.PropertyMetadata>.</span><span class="sxs-lookup"><span data-stu-id="7d9b1-133">Dependency properties have a built-in change notifications feature that must be used by supplying a change notification callback to the <xref:System.Windows.PropertyMetadata>.</span></span>  
  
## <a name="dependency-property-value-coercion"></a><span data-ttu-id="7d9b1-134">Vynucení hodnotu vlastnosti závislosti</span><span class="sxs-lookup"><span data-stu-id="7d9b1-134">Dependency Property Value Coercion</span></span>  
 <span data-ttu-id="7d9b1-135">Vlastnost převod se provádí při změně hodnoty zadané pro vlastnost setter podle setter předtím, než se skutečně upraví úložiště vlastností.</span><span class="sxs-lookup"><span data-stu-id="7d9b1-135">Property coercion takes place when the value given to a property setter is modified by the setter before the property store is actually modified.</span></span>  
  
 <span data-ttu-id="7d9b1-136">**X DO NOT** implementovat logiku na převod přístupové objekty vlastnosti závislosti.</span><span class="sxs-lookup"><span data-stu-id="7d9b1-136">**X DO NOT** implement coercion logic in dependency property accessors.</span></span>  
  
 <span data-ttu-id="7d9b1-137">Vlastnosti závislosti mají integrovanou vynucení funkce a je možné poskytnutím zpětné volání vynucení, aby `PropertyMetadata`.</span><span class="sxs-lookup"><span data-stu-id="7d9b1-137">Dependency properties have a built-in coercion feature, and it can be used by supplying a coercion callback to the `PropertyMetadata`.</span></span>  
  
 <span data-ttu-id="7d9b1-138">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="7d9b1-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="7d9b1-139">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="7d9b1-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d9b1-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d9b1-140">See also</span></span>

- [<span data-ttu-id="7d9b1-141">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="7d9b1-141">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="7d9b1-142">Obecné vzory návrhu</span><span class="sxs-lookup"><span data-stu-id="7d9b1-142">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)
