---
ms.openlocfilehash: 35fc4782ebbba33f5fc6668712af9d89d00cafe9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614620"
---
### <a name="wpf-changing-a-primary-key-when-displaying-ado-data-in-a-masterdetail-scenario"></a><span data-ttu-id="b9866-101">WPF měnící primární klíč při zobrazení dat ADO ve scénáři hlavní/podrobnosti</span><span class="sxs-lookup"><span data-stu-id="b9866-101">WPF Changing a primary key when displaying ADO data in a Master/Detail scenario</span></span>

#### <a name="details"></a><span data-ttu-id="b9866-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="b9866-102">Details</span></span>

<span data-ttu-id="b9866-103">Předpokládejme, že máte kolekci položek typu ADO `Order` s relací s názvem OrderDetails, která &quot; &quot; ji souvisí s kolekcí položek typu `Detail` prostřednictvím pole ČísloObjednávky primárního klíče &quot; &quot; .</span><span class="sxs-lookup"><span data-stu-id="b9866-103">Suppose you have an ADO collection of items of type `Order`, with a relation named &quot;OrderDetails&quot; relating it to a collection of items of type `Detail` via the primary key &quot;OrderID&quot;.</span></span> <span data-ttu-id="b9866-104">V aplikaci WPF můžete vytvořit propojení ovládacího prvku seznam s podrobnostmi o daném pořadí:</span><span class="sxs-lookup"><span data-stu-id="b9866-104">In your WPF app, you can bind a list control to the details for a given order:</span></span>

```xaml
<ListBox ItemsSource="{Binding Path=OrderDetails}" >
```

<span data-ttu-id="b9866-105">kde DataContext je `Order` .</span><span class="sxs-lookup"><span data-stu-id="b9866-105">where the DataContext is an `Order`.</span></span> <span data-ttu-id="b9866-106">WPF Získá hodnotu `OrderDetails` vlastnosti-a kolekci D všech `Detail` položek, jejichž `OrderID` `OrderID` počet odpovídá hlavní položce.</span><span class="sxs-lookup"><span data-stu-id="b9866-106">WPF gets the value of the `OrderDetails` property - a collection D of all the `Detail` items whose `OrderID` matches the `OrderID` of the master item.</span></span> <span data-ttu-id="b9866-107">Změna chování nastane při změně primárního klíče `OrderID` hlavní položky.</span><span class="sxs-lookup"><span data-stu-id="b9866-107">The behavior change arises when you change the primary key `OrderID` of the master item.</span></span> <span data-ttu-id="b9866-108">ADO automaticky změní `OrderID` všechny ovlivněné záznamy v kolekci podrobností (konkrétně ty zkopírované do kolekce D).</span><span class="sxs-lookup"><span data-stu-id="b9866-108">ADO automatically changes the `OrderID` of each of the affected records in the Details collection (namely the ones copied into collection D).</span></span>  <span data-ttu-id="b9866-109">Ale co se stane se D?</span><span class="sxs-lookup"><span data-stu-id="b9866-109">But what happens to D?</span></span>

- <span data-ttu-id="b9866-110">Staré chování: kolekce D je zrušená.</span><span class="sxs-lookup"><span data-stu-id="b9866-110">Old behavior: Collection D is cleared.</span></span> <span data-ttu-id="b9866-111">Hlavní položka *nevyvolává oznámení* o změně vlastnosti `OrderDetails` .</span><span class="sxs-lookup"><span data-stu-id="b9866-111">The master item does *not* raise a change notification for property `OrderDetails`.</span></span> <span data-ttu-id="b9866-112">Seznam stále používá kolekci D, která je nyní prázdná.</span><span class="sxs-lookup"><span data-stu-id="b9866-112">The ListBox continues to use collection D, which is now empty.</span></span>
- <span data-ttu-id="b9866-113">Nové chování: kolekce D se nezměnila.</span><span class="sxs-lookup"><span data-stu-id="b9866-113">New behavior:  Collection D is unchanged.</span></span> <span data-ttu-id="b9866-114">Každá z jeho položek vyvolá oznámení o změně `OrderID` Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b9866-114">Each of its items raises a change notification for the `OrderID` property.</span></span> <span data-ttu-id="b9866-115">Seznam stále používá kolekci D a zobrazuje podrobnosti s novým `OrderID` .</span><span class="sxs-lookup"><span data-stu-id="b9866-115">The ListBox continues to use collection D, and displays the details with the new `OrderID`.</span></span> <span data-ttu-id="b9866-116">WPF implementuje nové chování vytvořením kolekce D jiným způsobem: voláním metody ADO <xref:System.Data.DataRowView.CreateChildView(System.Data.DataRelation,System.Boolean)?displayProperty=nameWithType> s `followParent` argumentem nastaveným na `true` .</span><span class="sxs-lookup"><span data-stu-id="b9866-116">WPF implements the new behavior by creating collection D in a different way:  by calling the ADO method <xref:System.Data.DataRowView.CreateChildView(System.Data.DataRelation,System.Boolean)?displayProperty=nameWithType> with the `followParent` argument set to `true`.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b9866-117">Návrh</span><span class="sxs-lookup"><span data-stu-id="b9866-117">Suggestion</span></span>

<span data-ttu-id="b9866-118">Aplikace získá nové chování pomocí následujícího přepínače AppContext.</span><span class="sxs-lookup"><span data-stu-id="b9866-118">An app gets the new behavior by using the following AppContext switch.</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Data.DoNotUseFollowParentWhenBindingToADODataRelation=false"/>
  </runtime>
</configuration>
```

<span data-ttu-id="b9866-119">Přepínač nastaví výchozí nastavení `true` (staré chování) pro aplikace, které cílí na rozhraní .NET 4.7.1 nebo níže, a na `false` (nové chování) pro aplikace, které cílí na rozhraní .NET 4.7.2 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="b9866-119">The switch defaults to `true` (old behavior) for apps that target .NET 4.7.1 or below, and to `false` (new behavior) for apps that target .NET 4.7.2 or above.</span></span>

| <span data-ttu-id="b9866-120">Name</span><span class="sxs-lookup"><span data-stu-id="b9866-120">Name</span></span>    | <span data-ttu-id="b9866-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b9866-121">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b9866-122">Rozsah</span><span class="sxs-lookup"><span data-stu-id="b9866-122">Scope</span></span>   | <span data-ttu-id="b9866-123">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="b9866-123">Minor</span></span>       |
| <span data-ttu-id="b9866-124">Verze</span><span class="sxs-lookup"><span data-stu-id="b9866-124">Version</span></span> | <span data-ttu-id="b9866-125">4.7.2</span><span class="sxs-lookup"><span data-stu-id="b9866-125">4.7.2</span></span>       |
| <span data-ttu-id="b9866-126">Typ</span><span class="sxs-lookup"><span data-stu-id="b9866-126">Type</span></span>    | <span data-ttu-id="b9866-127">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="b9866-127">Retargeting</span></span> |
