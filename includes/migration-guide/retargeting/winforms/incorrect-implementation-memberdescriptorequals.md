---
ms.openlocfilehash: 2d0798917b639bc90bf3f78f6fb9f19d0eaf2c71
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614543"
---
### <a name="incorrect-implementation-of-memberdescriptorequals"></a><span data-ttu-id="236f4-101">Nesprávná implementace MemberDescriptor. Equals</span><span class="sxs-lookup"><span data-stu-id="236f4-101">Incorrect implementation of MemberDescriptor.Equals</span></span>

#### <a name="details"></a><span data-ttu-id="236f4-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="236f4-102">Details</span></span>

<span data-ttu-id="236f4-103">Původní implementace <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> metody porovnává dvě různé vlastnosti řetězce z porovnávaných objektů: název kategorie a řetězec s popisem.</span><span class="sxs-lookup"><span data-stu-id="236f4-103">The original implementation of the <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> method compares two different string properties from the objects being compared: the category name and the description string.</span></span> <span data-ttu-id="236f4-104">Tato oprava slouží k porovnání <xref:System.ComponentModel.MemberDescriptor.Category> prvního objektu s <xref:System.ComponentModel.MemberDescriptor.Category> druhým a <xref:System.ComponentModel.MemberDescriptor.Description> od prvního k <xref:System.ComponentModel.MemberDescriptor.Description> druhému.</span><span class="sxs-lookup"><span data-stu-id="236f4-104">The fix is to compare the <xref:System.ComponentModel.MemberDescriptor.Category> of the first object to the <xref:System.ComponentModel.MemberDescriptor.Category> of the second one, and the <xref:System.ComponentModel.MemberDescriptor.Description> of the first to the <xref:System.ComponentModel.MemberDescriptor.Description> of the second.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="236f4-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="236f4-105">Suggestion</span></span>

<span data-ttu-id="236f4-106">Pokud vaše aplikace závisí na tom <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> `false` , kde se někdy vrátí, když jsou popisovače ekvivalentní a že cílíte na .NET Framework 4.6.2 nebo novější, máte k dispozici několik možností:</span><span class="sxs-lookup"><span data-stu-id="236f4-106">If your application depends on <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> sometimes returning `false` when descriptors are equivalent, and you are targeting the .NET Framework 4.6.2 or later, you have several options:</span></span>

- <span data-ttu-id="236f4-107">Udělejte změny kódu pro porovnání <xref:System.ComponentModel.MemberDescriptor.Category> polí a <xref:System.ComponentModel.MemberDescriptor.Description> také při volání <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="236f4-107">Make code changes to compare the <xref:System.ComponentModel.MemberDescriptor.Category> and <xref:System.ComponentModel.MemberDescriptor.Description> fields manually in addition to calling the <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> method.</span></span>
- <span data-ttu-id="236f4-108">Odsouhlasit tuto změnu přidáním následující hodnoty do souboru app.config:</span><span class="sxs-lookup"><span data-stu-id="236f4-108">Opt out of this change by adding the following value to the app.config file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true" />
</runtime>
```

<span data-ttu-id="236f4-109">Pokud vaše aplikace cílí na .NET Framework 4.6.1 nebo starší verze a běží na .NET Framework 4.6.2 nebo novějším a chcete povolit tuto změnu, můžete nastavit přepínač kompatibility na `false` hodnotu přidáním následující hodnoty do souboru app.config:</span><span class="sxs-lookup"><span data-stu-id="236f4-109">If your application targets .NET Framework 4.6.1 or earlier and is running on the .NET Framework 4.6.2 or later and you want this change enabled, you can set the compatibility switch to `false` by adding the following value to the app.config file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=false" />
</runtime>
```

| <span data-ttu-id="236f4-110">Name</span><span class="sxs-lookup"><span data-stu-id="236f4-110">Name</span></span>    | <span data-ttu-id="236f4-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="236f4-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="236f4-112">Rozsah</span><span class="sxs-lookup"><span data-stu-id="236f4-112">Scope</span></span>   | <span data-ttu-id="236f4-113">Edge</span><span class="sxs-lookup"><span data-stu-id="236f4-113">Edge</span></span>        |
| <span data-ttu-id="236f4-114">Verze</span><span class="sxs-lookup"><span data-stu-id="236f4-114">Version</span></span> | <span data-ttu-id="236f4-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="236f4-115">4.6.2</span></span>       |
| <span data-ttu-id="236f4-116">Typ</span><span class="sxs-lookup"><span data-stu-id="236f4-116">Type</span></span>    | <span data-ttu-id="236f4-117">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="236f4-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="236f4-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="236f4-118">Affected APIs</span></span>

- <xref:System.ComponentModel.MemberDescriptor.Equals(System.Object)?displayProperty=nameWithType>
