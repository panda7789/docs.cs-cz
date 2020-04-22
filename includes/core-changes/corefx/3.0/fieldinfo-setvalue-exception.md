---
ms.openlocfilehash: 9f8a790718fbb9d685bb8959808338dc1766bf2c
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021651"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a><span data-ttu-id="d5b61-101">FieldInfo.SetValue vyvolá výjimku pro statická pole pouze init.</span><span class="sxs-lookup"><span data-stu-id="d5b61-101">FieldInfo.SetValue throws exception for static, init-only fields</span></span>

<span data-ttu-id="d5b61-102">Počínaje .NET Core 3.0, je vyvolána výjimka při pokusu <xref:System.Reflection.FieldAttributes.InitOnly> o nastavení <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>hodnoty na statické, pole voláním .</span><span class="sxs-lookup"><span data-stu-id="d5b61-102">Starting in .NET Core 3.0, an exception is thrown when you attempt to set a value on a static, <xref:System.Reflection.FieldAttributes.InitOnly> field by calling <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d5b61-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="d5b61-103">Change description</span></span>

<span data-ttu-id="d5b61-104">V rozhraní .NET Framework a verzích rozhraní .NET Core před verzí 3.0 můžete nastavit hodnotu statického pole, které <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>je konstantní po inicializování[(pouze pro čtení v C#](~/docs/csharp/language-reference/keywords/readonly.md)) voláním .</span><span class="sxs-lookup"><span data-stu-id="d5b61-104">In .NET Framework and versions of .NET Core prior to 3.0, you could set the value of a static field that's constant after it is initialized ([readonly in C#](~/docs/csharp/language-reference/keywords/readonly.md)) by calling <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span></span> <span data-ttu-id="d5b61-105">Nastavení takového pole tímto způsobem však vedlo k nepředvídatelnému chování založenému na cílovém rozhraní a nastavení optimalizace.</span><span class="sxs-lookup"><span data-stu-id="d5b61-105">However, setting such a field in this way resulted in unpredictable behavior based on the target framework and optimization settings.</span></span>

<span data-ttu-id="d5b61-106">V .NET Core 3.0 a novější <xref:System.Reflection.FieldInfo.SetValue%2A> verze při <xref:System.Reflection.FieldAttributes.InitOnly> volání na <xref:System.FieldAccessException?displayProperty=nameWithType> statické, pole je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="d5b61-106">In .NET Core 3.0 and later versions, when you call <xref:System.Reflection.FieldInfo.SetValue%2A> on a static, <xref:System.Reflection.FieldAttributes.InitOnly> field, a <xref:System.FieldAccessException?displayProperty=nameWithType> exception is thrown.</span></span>

> [!TIP]
> <span data-ttu-id="d5b61-107">Pole <xref:System.Reflection.FieldAttributes.InitOnly> je pole, které lze nastavit pouze v době, kdy je deklarováno, nebo v konstruktoru pro obsahující třídu.</span><span class="sxs-lookup"><span data-stu-id="d5b61-107">An <xref:System.Reflection.FieldAttributes.InitOnly> field is one that can only be set at the time it's declared or in the constructor for the containing class.</span></span> <span data-ttu-id="d5b61-108">Jinými slovy, je konstantní po inicializování.</span><span class="sxs-lookup"><span data-stu-id="d5b61-108">In other words, it's constant after it is initialized.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d5b61-109">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="d5b61-109">Version introduced</span></span>

<span data-ttu-id="d5b61-110">3.0</span><span class="sxs-lookup"><span data-stu-id="d5b61-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d5b61-111">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="d5b61-111">Recommended action</span></span>

<span data-ttu-id="d5b61-112">Inicializovat <xref:System.Reflection.FieldAttributes.InitOnly> statické, pole ve statickém konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="d5b61-112">Initialize static, <xref:System.Reflection.FieldAttributes.InitOnly> fields in a static constructor.</span></span> <span data-ttu-id="d5b61-113">To platí pro dynamické i nedynamické typy.</span><span class="sxs-lookup"><span data-stu-id="d5b61-113">This applies to both dynamic and non-dynamic types.</span></span>

<span data-ttu-id="d5b61-114">Případně můžete <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> odebrat atribut z pole a <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>potom zavolat .</span><span class="sxs-lookup"><span data-stu-id="d5b61-114">Alternatively, you can remove the <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> attribute from the field, and then call <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="d5b61-115">Kategorie</span><span class="sxs-lookup"><span data-stu-id="d5b61-115">Category</span></span>

<span data-ttu-id="d5b61-116">Základní knihovny .NET</span><span class="sxs-lookup"><span data-stu-id="d5b61-116">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d5b61-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="d5b61-117">Affected APIs</span></span>

- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)?displayProperty=nameWithType>
- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)`
- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)`

-->
