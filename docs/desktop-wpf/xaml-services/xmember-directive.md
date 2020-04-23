---
title: x:Member – direktiva
ms.date: 03/30/2017
ms.assetid: 4d8394ef-644c-4331-b6c5-be855d392980
ms.openlocfilehash: e82bb6397404ee466a12ab438585ae1898c34d1a
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071470"
---
# <a name="xmember-directive"></a><span data-ttu-id="01612-102">x:Member – direktiva</span><span class="sxs-lookup"><span data-stu-id="01612-102">x:Member Directive</span></span>
<span data-ttu-id="01612-103">Deklaruje člen XAML v přirážce.</span><span class="sxs-lookup"><span data-stu-id="01612-103">Declares a XAML member in markup.</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="01612-104">Použití elementu objektu XAML</span><span class="sxs-lookup"><span data-stu-id="01612-104">XAML Object Element Usage</span></span>

```xaml
<object x:Class="className">
  <x:Members>
    <x:Member Name="propertyName"/>
    additionalMembers
  </x:Members>
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="01612-105">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="01612-105">XAML Values</span></span>

|||
|-|-|
|`className`|<span data-ttu-id="01612-106">Název záložní třídy nebo částečné třídy pro výrobu XAML.</span><span class="sxs-lookup"><span data-stu-id="01612-106">Name of the backing class or partial class for the XAML production.</span></span>|
|`memberName`|<span data-ttu-id="01612-107">Název člena definované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="01612-107">Member name of the property being defined.</span></span>|

## <a name="remarks"></a><span data-ttu-id="01612-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="01612-108">Remarks</span></span>

<span data-ttu-id="01612-109">V implementaci služby .NET XAML Services .</span><span class="sxs-lookup"><span data-stu-id="01612-109">In .NET XAML Services implementation, .</span></span> <span data-ttu-id="01612-110">`x:Member`nemá přímý typ zálohování, ale je <xref:System.Windows.Markup.MemberDefinition> podporován třídou.</span><span class="sxs-lookup"><span data-stu-id="01612-110">`x:Member` does not have a direct type backing, but is supported by the <xref:System.Windows.Markup.MemberDefinition> class.</span></span> <span data-ttu-id="01612-111">V datovém proudu uzlu XAML je `x:Member` prvek `Member`reprezentován jako člen s názvem z oboru názvů XAML jazyka XAML jazyka XAML.</span><span class="sxs-lookup"><span data-stu-id="01612-111">In a XAML node stream, an `x:Member` element is represented as a member named `Member`, from the XAML language XAML namespace.</span></span> <span data-ttu-id="01612-112">Člen `Member` obsahuje atributy deklarované značkou.</span><span class="sxs-lookup"><span data-stu-id="01612-112">The member `Member` holds attributes as declared by markup.</span></span>

<span data-ttu-id="01612-113">Význam `Name` a `Type` nejsou přiřazeny na úrovni služby .NET XAML Services.</span><span class="sxs-lookup"><span data-stu-id="01612-113">The meaning of `Name` and `Type` are not assigned at .NET XAML Services level.</span></span> <span data-ttu-id="01612-114">Jsou uloženy v počátečním datovém proudu uzlu XAML jako řetězcové hodnoty, které mají být interpretovány později podle pravidel, která mohou být uložena konkrétními rámci.</span><span class="sxs-lookup"><span data-stu-id="01612-114">They are stored in the initial XAML node stream as string values, to be interpreted later under the rules that might be imposed by specific frameworks.</span></span> <span data-ttu-id="01612-115">Význam může zarovnat k názvu XAML a typu XAML, což znamená nebo může být platný pouze v systému typu zálohování, v závislosti na implementaci.</span><span class="sxs-lookup"><span data-stu-id="01612-115">The meaning might align to a XAML name and XAML type meaning, or might only be valid in a backing type system, depending on the implementation.</span></span>

<span data-ttu-id="01612-116">Chcete-li podporovat `x:Members` praktické použití jako prostředek k určení definice členů ve značkách, musí být členy přidruženy ke třídě, která může být změněna.</span><span class="sxs-lookup"><span data-stu-id="01612-116">To support a practical usage of `x:Members` as a means to specify member definitions in markup, the members must be associated with a class that can be modified.</span></span> <span data-ttu-id="01612-117">Zamýšlený model je, který `x:Members` existuje jako člen typu, `x:Class`který určuje .</span><span class="sxs-lookup"><span data-stu-id="01612-117">The intended model is that `x:Members` exists as a member of a type that specifies an `x:Class`.</span></span> <span data-ttu-id="01612-118">Mechanismus pro přisuzování typů a členů nebo pro vytváření definic dynamických členů však není podporován na úrovni služby .NET XAML Services.</span><span class="sxs-lookup"><span data-stu-id="01612-118">However, the mechanism for associating types and members or for producing dynamic member definitions is not supported at .NET XAML Services level.</span></span> <span data-ttu-id="01612-119">To je ponecháno na jednotlivé architektury, které mají modely aplikací, které podporují definice členů z XAML.</span><span class="sxs-lookup"><span data-stu-id="01612-119">This is left to individual frameworks that have application models that support member definitions from XAML.</span></span> <span data-ttu-id="01612-120">MSBUILD obvykle sestavení akce, které značky kompilovat XAML a buď integrovat s kódem na pozadí nebo vyrábět čisté z XAML sestavení jsou potřebné pro podporu této funkce.</span><span class="sxs-lookup"><span data-stu-id="01612-120">Typically, MSBUILD build actions that markup-compile the XAML and either integrate it with code-behind or produce pure from-XAML assemblies are needed to support that feature.</span></span>

## <a name="xproperty-for-windows-workflow-foundation"></a><span data-ttu-id="01612-121">x:Vlastnost pro Nadaci pracovního postupu Windows</span><span class="sxs-lookup"><span data-stu-id="01612-121">x:Property for Windows Workflow Foundation</span></span>

<span data-ttu-id="01612-122">Pro Windows Workflow `x:Property` Foundation definuje členy vlastní aktivity složené výhradně v XAML nebo XAML definované dynamické členy pro návrháře aktivit s kódem na pozadí.</span><span class="sxs-lookup"><span data-stu-id="01612-122">For Windows Workflow Foundation, `x:Property` defines the members of a custom activity composed entirely in XAML, or XAML –defined dynamic members for an activity designer with code-behind.</span></span> <span data-ttu-id="01612-123">`x:Class`musí být také uveden na kořenovém prvku výroby XAML.</span><span class="sxs-lookup"><span data-stu-id="01612-123">`x:Class` must also be specified on the root element of the XAML production.</span></span> <span data-ttu-id="01612-124">Toto není požadavek na úrovni služby .NET XAML, ale stane se požadavkem při načtení výroby XAML akcemi sestavení MSBUILD, které podporují vlastní aktivity a Windows Workflow Foundation XAML obecně.</span><span class="sxs-lookup"><span data-stu-id="01612-124">This is not a requirement at .NET XAML Services level, but becomes a requirement when the XAML production is loaded by the MSBUILD build actions that support custom activities and Windows Workflow Foundation XAML in general.</span></span> <span data-ttu-id="01612-125">Windows Workflow Foundation nepoužívá čistý název typu XAML jako `x:Property` `Type` jeho zamýšlenou hodnotu pro atribut a místo toho používá konvenci, která zde není popsána.</span><span class="sxs-lookup"><span data-stu-id="01612-125">Windows Workflow Foundation does not use the pure XAML type name as its intended value for the `x:Property` `Type` attribute, and instead uses a convention that is not documented here.</span></span> <span data-ttu-id="01612-126">Další informace naleznete v tématu [DynamicActivity Creation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="01612-126">For more information, see [DynamicActivity Creation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).</span></span>
