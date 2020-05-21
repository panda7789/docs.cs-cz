---
ms.openlocfilehash: 02c9305a36f47dfaf0b1fa8d19b07cd2d34badae
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721269"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a><span data-ttu-id="ca5f1-101">Parametr FieldInfo. SetValue vyvolá výjimku pro statická pole pouze pro init.</span><span class="sxs-lookup"><span data-stu-id="ca5f1-101">FieldInfo.SetValue throws exception for static, init-only fields</span></span>

<span data-ttu-id="ca5f1-102">Počínaje rozhraním .NET Core 3,0 je vyvolána výjimka při pokusu o nastavení hodnoty ve statickém <xref:System.Reflection.FieldAttributes.InitOnly> poli pomocí volání <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="ca5f1-102">Starting in .NET Core 3.0, an exception is thrown when you attempt to set a value on a static, <xref:System.Reflection.FieldAttributes.InitOnly> field by calling <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ca5f1-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="ca5f1-103">Change description</span></span>

<span data-ttu-id="ca5f1-104">V .NET Framework a verzích .NET Core před 3,0 jste mohli nastavit hodnotu statického pole, které je konstanta po inicializaci ([ReadOnly v jazyce C#](~/docs/csharp/language-reference/keywords/readonly.md)) voláním <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="ca5f1-104">In .NET Framework and versions of .NET Core prior to 3.0, you could set the value of a static field that's constant after it is initialized ([readonly in C#](~/docs/csharp/language-reference/keywords/readonly.md)) by calling <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span></span> <span data-ttu-id="ca5f1-105">Nicméně nastavení takového pole tímto způsobem vedlo k nepředvídatelnému chování na základě cílové architektury a nastavení optimalizace.</span><span class="sxs-lookup"><span data-stu-id="ca5f1-105">However, setting such a field in this way resulted in unpredictable behavior based on the target framework and optimization settings.</span></span>

<span data-ttu-id="ca5f1-106">V .NET Core 3,0 a novějších verzích při volání <xref:System.Reflection.FieldInfo.SetValue%2A> ve statickém <xref:System.Reflection.FieldAttributes.InitOnly> poli <xref:System.FieldAccessException?displayProperty=nameWithType> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="ca5f1-106">In .NET Core 3.0 and later versions, when you call <xref:System.Reflection.FieldInfo.SetValue%2A> on a static, <xref:System.Reflection.FieldAttributes.InitOnly> field, a <xref:System.FieldAccessException?displayProperty=nameWithType> exception is thrown.</span></span>

> [!TIP]
> <span data-ttu-id="ca5f1-107"><xref:System.Reflection.FieldAttributes.InitOnly>Pole je jedno, které lze nastavit pouze v okamžiku deklarace nebo v konstruktoru pro třídu, která ji obsahuje.</span><span class="sxs-lookup"><span data-stu-id="ca5f1-107">An <xref:System.Reflection.FieldAttributes.InitOnly> field is one that can only be set at the time it's declared or in the constructor for the containing class.</span></span> <span data-ttu-id="ca5f1-108">Jinými slovy je konstanta po inicializaci.</span><span class="sxs-lookup"><span data-stu-id="ca5f1-108">In other words, it's constant after it is initialized.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ca5f1-109">Představená verze</span><span class="sxs-lookup"><span data-stu-id="ca5f1-109">Version introduced</span></span>

<span data-ttu-id="ca5f1-110">3.0</span><span class="sxs-lookup"><span data-stu-id="ca5f1-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ca5f1-111">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="ca5f1-111">Recommended action</span></span>

<span data-ttu-id="ca5f1-112">Proveďte inicializaci statických <xref:System.Reflection.FieldAttributes.InitOnly> polí ve statickém konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="ca5f1-112">Initialize static, <xref:System.Reflection.FieldAttributes.InitOnly> fields in a static constructor.</span></span> <span data-ttu-id="ca5f1-113">To platí pro dynamické i jiné než dynamické typy.</span><span class="sxs-lookup"><span data-stu-id="ca5f1-113">This applies to both dynamic and non-dynamic types.</span></span>

<span data-ttu-id="ca5f1-114">Alternativně můžete odebrat <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> atribut z pole a pak zavolat <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ca5f1-114">Alternatively, you can remove the <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> attribute from the field, and then call <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="ca5f1-115">Kategorie</span><span class="sxs-lookup"><span data-stu-id="ca5f1-115">Category</span></span>

<span data-ttu-id="ca5f1-116">Knihovny Core .NET</span><span class="sxs-lookup"><span data-stu-id="ca5f1-116">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ca5f1-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="ca5f1-117">Affected APIs</span></span>

- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)?displayProperty=nameWithType>
- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)`
- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)`

-->
