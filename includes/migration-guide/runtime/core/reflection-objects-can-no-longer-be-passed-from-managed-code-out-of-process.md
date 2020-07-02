---
ms.openlocfilehash: a54b17b2002bd0f85b8b47c5e37e040470d6c494
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621145"
---
### <a name="reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a><span data-ttu-id="c1831-101">Objekty reflexe již nelze předávat ze spravovaného kódu do mimoprocesových klientů modelu DCOM.</span><span class="sxs-lookup"><span data-stu-id="c1831-101">Reflection objects can no longer be passed from managed code to out-of-process DCOM clients</span></span>

#### <a name="details"></a><span data-ttu-id="c1831-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="c1831-102">Details</span></span>

<span data-ttu-id="c1831-103">Objekty reflexe již nelze předávat ze spravovaného kódu pro klienty DCOM mimo procesy.</span><span class="sxs-lookup"><span data-stu-id="c1831-103">Reflection objects can no longer be passed from managed code to out-of-process DCOM clients.</span></span> <span data-ttu-id="c1831-104">Ovlivněny jsou následující typy:</span><span class="sxs-lookup"><span data-stu-id="c1831-104">The following types are affected:</span></span><ul><li><xref:System.Reflection.Assembly?displayProperty=fullName></li><li><span data-ttu-id="c1831-105"><xref:System.Reflection.MemberInfo?displayProperty=fullName>(a jeho odvozené typy, včetně <xref:System.Reflection.FieldInfo?displayProperty=fullName> , <xref:System.Reflection.MethodInfo?displayProperty=fullName> , <xref:System.Type?displayProperty=fullName> a <xref:System.Reflection.TypeInfo?displayProperty=fullName> )</span><span class="sxs-lookup"><span data-stu-id="c1831-105"><xref:System.Reflection.MemberInfo?displayProperty=fullName> (and its derived types, including <xref:System.Reflection.FieldInfo?displayProperty=fullName>, <xref:System.Reflection.MethodInfo?displayProperty=fullName>, <xref:System.Type?displayProperty=fullName>, and <xref:System.Reflection.TypeInfo?displayProperty=fullName>)</span></span></li><li><xref:System.Reflection.MethodBody?displayProperty=fullName></li><li><xref:System.Reflection.Module?displayProperty=fullName></li><li><span data-ttu-id="c1831-106"><xref:System.Reflection.ParameterInfo?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="c1831-106"><xref:System.Reflection.ParameterInfo?displayProperty=fullName>.</span></span></li></ul><span data-ttu-id="c1831-107">Volání <code>IMarshal</code> pro objekt vrátí <code>E_NOINTERFACE</code> .</span><span class="sxs-lookup"><span data-stu-id="c1831-107">Calls to <code>IMarshal</code> for the object return <code>E_NOINTERFACE</code>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c1831-108">Návrh</span><span class="sxs-lookup"><span data-stu-id="c1831-108">Suggestion</span></span>

<span data-ttu-id="c1831-109">Aktualizace zařazovacího kódu pro práci s objekty bez reflexe</span><span class="sxs-lookup"><span data-stu-id="c1831-109">Update marshaling code to work with non-reflection objects</span></span>

| <span data-ttu-id="c1831-110">Name</span><span class="sxs-lookup"><span data-stu-id="c1831-110">Name</span></span>    | <span data-ttu-id="c1831-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="c1831-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c1831-112">Rozsah</span><span class="sxs-lookup"><span data-stu-id="c1831-112">Scope</span></span>   |<span data-ttu-id="c1831-113">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="c1831-113">Minor</span></span>|
|<span data-ttu-id="c1831-114">Verze</span><span class="sxs-lookup"><span data-stu-id="c1831-114">Version</span></span>|<span data-ttu-id="c1831-115">4.6</span><span class="sxs-lookup"><span data-stu-id="c1831-115">4.6</span></span>|
|<span data-ttu-id="c1831-116">Typ</span><span class="sxs-lookup"><span data-stu-id="c1831-116">Type</span></span>|<span data-ttu-id="c1831-117">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="c1831-117">Runtime</span></span>|
