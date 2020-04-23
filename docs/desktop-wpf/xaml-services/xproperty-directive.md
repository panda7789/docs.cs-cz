---
title: x:Property – direktiva
ms.date: 03/30/2017
ms.assetid: 618555a8-c893-455c-810f-ac54cd24ef10
ms.openlocfilehash: 2804ec935d0626cba9ef050f70a3266cf23bcce0
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071407"
---
# <a name="xproperty-directive"></a><span data-ttu-id="cdc5c-102">x:Property – direktiva</span><span class="sxs-lookup"><span data-stu-id="cdc5c-102">x:Property Directive</span></span>

<span data-ttu-id="cdc5c-103">Deklaruje vlastnost XAML ve značkách.</span><span class="sxs-lookup"><span data-stu-id="cdc5c-103">Declares a XAML property in markup.</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="cdc5c-104">Použití elementu objektu XAML</span><span class="sxs-lookup"><span data-stu-id="cdc5c-104">XAML Object Element Usage</span></span>

```xaml
<object x:Class="className">
  <x:Members>
    <x:Property Name="propertyName" Type="propertyType"/>
    additionalProperties
  </x:Members>
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="cdc5c-105">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="cdc5c-105">XAML Values</span></span>

|||
|-|-|
|`className`|<span data-ttu-id="cdc5c-106">Název záložní třídy nebo částečné třídy pro výrobu XAML.</span><span class="sxs-lookup"><span data-stu-id="cdc5c-106">Name of the backing class or partial class for the XAML production.</span></span>|
|`propertyName`|<span data-ttu-id="cdc5c-107">Název člena definované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cdc5c-107">Member name of the property being defined.</span></span>|
|`propertyType`|<span data-ttu-id="cdc5c-108">Název typu (nebo jiný řetězec formuláře, specifické pro architekturu), který určuje typ této vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cdc5c-108">Type name (or other string form, framework-specific) that specifies the type of this property.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cdc5c-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cdc5c-109">Remarks</span></span>

<span data-ttu-id="cdc5c-110">V implementaci služby .NET XAML Services .</span><span class="sxs-lookup"><span data-stu-id="cdc5c-110">In .NET XAML Services implementation, .</span></span> <span data-ttu-id="cdc5c-111">`x:Property`nemá přímý typ zálohování, ale je <xref:System.Windows.Markup.PropertyDefinition> podporován třídou.</span><span class="sxs-lookup"><span data-stu-id="cdc5c-111">`x:Property` does not have a direct type backing, but is supported by the <xref:System.Windows.Markup.PropertyDefinition> class.</span></span> <span data-ttu-id="cdc5c-112">V datovém proudu uzlu XAML je `x:Property` prvek `Property`reprezentován jako člen s názvem z oboru názvů XAML jazyka XAML jazyka XAML.</span><span class="sxs-lookup"><span data-stu-id="cdc5c-112">In a XAML node stream, an `x:Property` element is represented as a member named `Property`, from the XAML language XAML namespace.</span></span> <span data-ttu-id="cdc5c-113">Člen `Property` hold atributy deklarované značky.</span><span class="sxs-lookup"><span data-stu-id="cdc5c-113">The member `Property` hold attributes as declared by markup.</span></span>

<span data-ttu-id="cdc5c-114">Význam `Name` a `Type` nejsou přiřazeny na úrovni služby .NET XAML Services.</span><span class="sxs-lookup"><span data-stu-id="cdc5c-114">The meaning of `Name` and `Type` are not assigned at .NET XAML Services level.</span></span> <span data-ttu-id="cdc5c-115">Jsou uloženy v počátečním datovém proudu uzlu XAML jako řetězcové hodnoty, které mají být interpretovány později podle pravidel, která mohou být uložena konkrétními rámci.</span><span class="sxs-lookup"><span data-stu-id="cdc5c-115">They are stored in the initial XAML node stream as string values, to be interpreted later under the rules that might be imposed by specific frameworks.</span></span> <span data-ttu-id="cdc5c-116">Význam může zarovnat k názvu XAML a typu XAML, což znamená nebo může být platný pouze v systému typu zálohování, v závislosti na implementaci.</span><span class="sxs-lookup"><span data-stu-id="cdc5c-116">The meaning might align to a XAML name and XAML type meaning, or might only be valid in a backing type system, depending on the implementation.</span></span>

<span data-ttu-id="cdc5c-117">Chcete-li podporovat `x:Members` praktické použití jako prostředek k určení definice členů ve značkách, musí být členy přidruženy ke třídě, která může být změněna.</span><span class="sxs-lookup"><span data-stu-id="cdc5c-117">To support a practical usage of `x:Members` as a means to specify member definitions in markup, the members must be associated with a class that can be modified.</span></span> <span data-ttu-id="cdc5c-118">Zamýšlený model je, který `x:Members` existuje jako člen typu, `x:Class`který určuje .</span><span class="sxs-lookup"><span data-stu-id="cdc5c-118">The intended model is that `x:Members` exists as a member of a type that specifies an `x:Class`.</span></span> <span data-ttu-id="cdc5c-119">Mechanismus pro přisuzování typů a členů nebo pro vytváření definic dynamických členů však není podporován na úrovni služby .NET XAML Services.</span><span class="sxs-lookup"><span data-stu-id="cdc5c-119">However, the mechanism for associating types and members or for producing dynamic member definitions is not supported at .NET XAML Services level.</span></span> <span data-ttu-id="cdc5c-120">To je ponecháno na jednotlivé architektury, které mají modely aplikací, které podporují definice členů z XAML.</span><span class="sxs-lookup"><span data-stu-id="cdc5c-120">This is left to individual frameworks that have application models that support member definitions from XAML.</span></span> <span data-ttu-id="cdc5c-121">MSBUILD obvykle sestavení akce, které značky kompilovat XAML a buď integrovat s kódem na pozadí nebo vyrábět čisté z XAML sestavení jsou potřebné pro podporu této funkce.</span><span class="sxs-lookup"><span data-stu-id="cdc5c-121">Typically, MSBUILD build actions that markup-compile the XAML and either integrate it with code-behind or produce pure from-XAML assemblies are needed to support that feature.</span></span>

## <a name="xproperty-for-windows-workflow-foundation"></a><span data-ttu-id="cdc5c-122">x:Vlastnost pro Nadaci pracovního postupu Windows</span><span class="sxs-lookup"><span data-stu-id="cdc5c-122">x:Property for Windows Workflow Foundation</span></span>

<span data-ttu-id="cdc5c-123">Pro Windows Workflow `x:Property` Foundation definuje členy vlastní aktivity složené výhradně v XAML nebo XAML definované dynamické členy pro návrháře aktivit s kódem na pozadí.</span><span class="sxs-lookup"><span data-stu-id="cdc5c-123">For Windows Workflow Foundation, `x:Property` defines the members of a custom activity composed entirely in XAML, or XAML –defined dynamic members for an activity designer with code-behind.</span></span> <span data-ttu-id="cdc5c-124">`x:Class`musí být také uveden na kořenovém prvku výroby XAML.</span><span class="sxs-lookup"><span data-stu-id="cdc5c-124">`x:Class` must also be specified on the root element of the XAML production.</span></span> <span data-ttu-id="cdc5c-125">Toto není požadavek na úrovni služby .NET XAML, ale stane se požadavkem při načtení výroby XAML akcemi sestavení MSBUILD, které podporují vlastní aktivity a Windows Workflow Foundation XAML obecně.</span><span class="sxs-lookup"><span data-stu-id="cdc5c-125">This is not a requirement at .NET XAML Services level, but becomes a requirement when the XAML production is loaded by the MSBUILD build actions that support custom activities and Windows Workflow Foundation XAML in general.</span></span> <span data-ttu-id="cdc5c-126">Windows Workflow Foundation nepoužívá čistý název typu XAML jako `x:Property` `Type` jeho zamýšlenou hodnotu pro atribut a místo toho používá konvenci, která zde není popsána.</span><span class="sxs-lookup"><span data-stu-id="cdc5c-126">Windows Workflow Foundation does not use the pure XAML type name as its intended value for the `x:Property` `Type` attribute, and instead uses a convention that is not documented here.</span></span> <span data-ttu-id="cdc5c-127">Další informace naleznete v tématu [DynamicActivity Creation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="cdc5c-127">For more information, see [DynamicActivity Creation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).</span></span>
