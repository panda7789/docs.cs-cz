---
title: "Vlastnosti závislosti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 21e2026e7ce0f2dcf1ffc9a328b1bb9630cd8fbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="dependency-properties"></a><span data-ttu-id="b2e79-102">Vlastnosti závislosti</span><span class="sxs-lookup"><span data-stu-id="b2e79-102">Dependency Properties</span></span>
<span data-ttu-id="b2e79-103">Vlastnost závislosti (DP) je regulární vlastnost, která ukládá v úložišti vlastnost místo ukládání typ proměnné (pole), například jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b2e79-103">A dependency property (DP) is a regular property that stores its value in a property store instead of storing it in a type variable (field), for example.</span></span>  
  
 <span data-ttu-id="b2e79-104">Ve vlastnosti připojené závislostí je druh vlastnost závislosti, které jsou modelovat jako statické metody Get a sady reprezentující "vlastnosti" popisující vztahy mezi objekty a jejich kontejnery (například pozici `Button` objekt v `Panel` kontejner).</span><span class="sxs-lookup"><span data-stu-id="b2e79-104">An attached dependency property is a kind of dependency property modeled as static Get and Set methods representing "properties" describing relationships between objects and their containers (e.g., the position of a `Button` object on a `Panel` container).</span></span>  
  
 <span data-ttu-id="b2e79-105">**PROVEĎTE ✓** zadejte vlastnosti závislosti, pokud budete potřebovat k podpoře funkce WPF například stylů, aktivační události, vazby dat, animací, dynamické prostředky a dědičnosti vlastností.</span><span class="sxs-lookup"><span data-stu-id="b2e79-105">**✓ DO** provide the dependency properties, if you need the properties to support WPF features such as styling, triggers, data binding, animations, dynamic resources, and inheritance.</span></span>  
  
## <a name="dependency-property-design"></a><span data-ttu-id="b2e79-106">Návrh vlastnost závislosti</span><span class="sxs-lookup"><span data-stu-id="b2e79-106">Dependency Property Design</span></span>  
 <span data-ttu-id="b2e79-107">**PROVEĎTE ✓** dědí <xref:System.Windows.DependencyObject>, nebo jeden z jeho podtypech při implementaci vlastností závislostí.</span><span class="sxs-lookup"><span data-stu-id="b2e79-107">**✓ DO** inherit from <xref:System.Windows.DependencyObject>, or one of its subtypes, when implementing dependency properties.</span></span> <span data-ttu-id="b2e79-108">Typ poskytuje velmi efektivní implementaci úložiště vlastností a automaticky podporuje datové vazby WPF.</span><span class="sxs-lookup"><span data-stu-id="b2e79-108">The type provides a very efficient implementation of a property store and automatically supports WPF data binding.</span></span>  
  
 <span data-ttu-id="b2e79-109">**PROVEĎTE ✓** zadejte regulární vlastnost CLR a veřejné statické jen pro čtení pole ukládání instanci <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> pro každou vlastnost závislosti.</span><span class="sxs-lookup"><span data-stu-id="b2e79-109">**✓ DO** provide a regular CLR property and public static read-only field storing an instance of <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> for each dependency property.</span></span>  
  
 <span data-ttu-id="b2e79-110">**PROVEĎTE ✓** implementovat vlastností závislostí voláním metod instance <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> a <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b2e79-110">**✓ DO** implement dependency properties by calling instance methods <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> and <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="b2e79-111">**PROVEĎTE ✓** názvů statické pole vlastnosti závislosti suffixing název vlastnosti s "Vlastnost."</span><span class="sxs-lookup"><span data-stu-id="b2e79-111">**✓ DO** name the dependency property static field by suffixing the name of the property with "Property."</span></span>  
  
 <span data-ttu-id="b2e79-112">**X nesmí** explicitně nastavit výchozí hodnoty vlastností závislostí v kódu; nastavte je v metadatech.</span><span class="sxs-lookup"><span data-stu-id="b2e79-112">**X DO NOT** set default values of dependency properties explicitly in code; set them in metadata instead.</span></span>  
  
 <span data-ttu-id="b2e79-113">Pokud nastavíte výchozí vlastnost explicitně, vám může zabránit tuto vlastnost se nastavuje některé implicitní prostředky, jako je například stylů.</span><span class="sxs-lookup"><span data-stu-id="b2e79-113">If you set a property default explicitly, you might prevent that property from being set by some implicit means, such as a styling.</span></span>  
  
 <span data-ttu-id="b2e79-114">**X nesmí** vkládat kód do vlastnosti přistupující objekty než standardní kód pro přístup k statické pole.</span><span class="sxs-lookup"><span data-stu-id="b2e79-114">**X DO NOT** put code in the property accessors other than the standard code to access the static field.</span></span>  
  
 <span data-ttu-id="b2e79-115">Statické pole, kód nebude spustit, pokud je vlastnost nastavena implicitní prostředky, jako je například stylů, protože styly používá přímo.</span><span class="sxs-lookup"><span data-stu-id="b2e79-115">That code won’t execute if the property is set by implicit means, such as a styling, because styling uses the static field directly.</span></span>  
  
 <span data-ttu-id="b2e79-116">**X nesmí** zabezpečené data pomocí vlastností závislostí.</span><span class="sxs-lookup"><span data-stu-id="b2e79-116">**X DO NOT** use dependency properties to store secure data.</span></span> <span data-ttu-id="b2e79-117">Veřejně přístupná vlastností i privátní závislostí.</span><span class="sxs-lookup"><span data-stu-id="b2e79-117">Even private dependency properties can be accessed publicly.</span></span>  
  
## <a name="attached-dependency-property-design"></a><span data-ttu-id="b2e79-118">Návrh vlastnost připojené závislostí</span><span class="sxs-lookup"><span data-stu-id="b2e79-118">Attached Dependency Property Design</span></span>  
 <span data-ttu-id="b2e79-119">Závislost vlastností popsaných v předchozí části představují vnitřní vlastnosti deklarující typ; například `Text` vlastnost je vlastností `TextButton`, který deklaruje ho.</span><span class="sxs-lookup"><span data-stu-id="b2e79-119">Dependency properties described in the preceding section represent intrinsic properties of the declaring type; for example, the `Text` property is a property of `TextButton`, which declares it.</span></span> <span data-ttu-id="b2e79-120">Zvláštní druh vlastnost závislosti je vlastnost připojené závislosti.</span><span class="sxs-lookup"><span data-stu-id="b2e79-120">A special kind of dependency property is the attached dependency property.</span></span>  
  
 <span data-ttu-id="b2e79-121">Je classic třeba přidružená vlastnost <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b2e79-121">A classic example of an attached property is the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="b2e79-122">Vlastnost představuje pozici sloupce tlačítka (ne mřížky), ale je pouze relevantní Pokud tlačítko je obsažen v mřížce, a tudíž je "připojen" na tlačítka podle mřížky.</span><span class="sxs-lookup"><span data-stu-id="b2e79-122">The property represents Button’s (not Grid’s) column position, but it is only relevant if the Button is contained in a Grid, and so it's "attached" to Buttons by Grids.</span></span>  
  
```  
<Grid>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition />  
        <ColumnDefinition />  
    </Grid.ColumnDefinitions>  
  
    <Button Grid.Column="0">Click</Button>  
    <Button Grid.Column="1">Clack</Button>  
</Grid>  
```  
  
 <span data-ttu-id="b2e79-123">Definice přidružená vlastnost vypadá nejčastěji, vlastnosti regulární závislosti, s tím rozdílem, že přístupové objekty jsou reprezentované pomocí statické metody Get a sady:</span><span class="sxs-lookup"><span data-stu-id="b2e79-123">The definition of an attached property looks mostly like that of a regular dependency property, except that the accessors are represented by static Get and Set methods:</span></span>  
  
```  
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
  
## <a name="dependency-property-validation"></a><span data-ttu-id="b2e79-124">Ověření vlastností závislostí</span><span class="sxs-lookup"><span data-stu-id="b2e79-124">Dependency Property Validation</span></span>  
 <span data-ttu-id="b2e79-125">Vlastnosti často implementovat, co se nazývá ověření.</span><span class="sxs-lookup"><span data-stu-id="b2e79-125">Properties often implement what is called validation.</span></span> <span data-ttu-id="b2e79-126">Logiku ověření provede, když je proveden pokus o ke změně hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b2e79-126">Validation logic executes when an attempt is made to change the value of a property.</span></span>  
  
 <span data-ttu-id="b2e79-127">Přístupové objekty vlastnosti závislosti bohužel nemůže obsahovat libovolný ověřovacího kódu.</span><span class="sxs-lookup"><span data-stu-id="b2e79-127">Unfortunately dependency property accessors cannot contain arbitrary validation code.</span></span> <span data-ttu-id="b2e79-128">Místo toho je třeba zadat během registrace vlastnost logiku ověření pro vlastnost závislosti.</span><span class="sxs-lookup"><span data-stu-id="b2e79-128">Instead, dependency property validation logic needs to be specified during property registration.</span></span>  
  
 <span data-ttu-id="b2e79-129">**X nesmí** chápat logiku ověření pro vlastnost závislosti vlastnosti přistupující objekty.</span><span class="sxs-lookup"><span data-stu-id="b2e79-129">**X DO NOT** put dependency property validation logic in the property’s accessors.</span></span> <span data-ttu-id="b2e79-130">Místo toho předat zpětné volání pro ověření do `DependencyProperty.Register` metoda.</span><span class="sxs-lookup"><span data-stu-id="b2e79-130">Instead, pass a validation callback to `DependencyProperty.Register` method.</span></span>  
  
## <a name="dependency-property-change-notifications"></a><span data-ttu-id="b2e79-131">Oznámení o změnách závislostí vlastnost</span><span class="sxs-lookup"><span data-stu-id="b2e79-131">Dependency Property Change Notifications</span></span>  
 <span data-ttu-id="b2e79-132">**X nesmí** implementovat logiku oznámení změn v přístupové objekty vlastnosti závislosti.</span><span class="sxs-lookup"><span data-stu-id="b2e79-132">**X DO NOT** implement change notification logic in dependency property accessors.</span></span> <span data-ttu-id="b2e79-133">Vlastnosti závislosti mají funkce oznámení předdefinované změnu, která použije zadáním zpětné volání oznámení změny na <xref:System.Windows.PropertyMetadata>.</span><span class="sxs-lookup"><span data-stu-id="b2e79-133">Dependency properties have a built-in change notifications feature that must be used by supplying a change notification callback to the <xref:System.Windows.PropertyMetadata>.</span></span>  
  
## <a name="dependency-property-value-coercion"></a><span data-ttu-id="b2e79-134">Převod hodnotu vlastnosti závislosti</span><span class="sxs-lookup"><span data-stu-id="b2e79-134">Dependency Property Value Coercion</span></span>  
 <span data-ttu-id="b2e79-135">Vlastnost převod probíhá při hodnotě zadané pro vlastnost setter je upraveném nastavovací metoda předtím, než je ve skutečnosti Změna úložiště vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b2e79-135">Property coercion takes place when the value given to a property setter is modified by the setter before the property store is actually modified.</span></span>  
  
 <span data-ttu-id="b2e79-136">**X nesmí** implementovat logiku na převod přístupové objekty vlastnosti závislosti.</span><span class="sxs-lookup"><span data-stu-id="b2e79-136">**X DO NOT** implement coercion logic in dependency property accessors.</span></span>  
  
 <span data-ttu-id="b2e79-137">Vlastností závislostí obsahují předdefinované převod funkci a použitím zadáním zpětné volání pro převod `PropertyMetadata`.</span><span class="sxs-lookup"><span data-stu-id="b2e79-137">Dependency properties have a built-in coercion feature, and it can be used by supplying a coercion callback to the `PropertyMetadata`.</span></span>  
  
 <span data-ttu-id="b2e79-138">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="b2e79-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="b2e79-139">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="b2e79-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2e79-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="b2e79-140">See Also</span></span>  
 [<span data-ttu-id="b2e79-141">Pokyny pro návrh Framework</span><span class="sxs-lookup"><span data-stu-id="b2e79-141">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="b2e79-142">Obecné vzory návrhu</span><span class="sxs-lookup"><span data-stu-id="b2e79-142">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)
