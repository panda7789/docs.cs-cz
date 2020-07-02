---
ms.openlocfilehash: b88f7d4a17f885b687d99ab9410a56039e176080
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614429"
---
### <a name="calls-to-claimsidentity-constructors"></a><span data-ttu-id="63373-101">Volání konstruktorů hodnota ClaimsIdentity</span><span class="sxs-lookup"><span data-stu-id="63373-101">Calls to ClaimsIdentity constructors</span></span>

#### <a name="details"></a><span data-ttu-id="63373-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="63373-102">Details</span></span>

<span data-ttu-id="63373-103">Počínaje .NET Framework 4.6.2 dojde ke změně v tom, jak <xref:System.Security.Claims.ClaimsIdentity> konstruktory s <xref:System.Security.Principal.IIdentity?displayProperty=fullName> parametrem nastaví <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="63373-103">Starting with the .NET Framework 4.6.2, there is a change in how <xref:System.Security.Claims.ClaimsIdentity> constructors with an <xref:System.Security.Principal.IIdentity?displayProperty=fullName> parameter set the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property.</span></span> <span data-ttu-id="63373-104">Pokud <xref:System.Security.Principal.IIdentity?displayProperty=fullName> je argumentem <xref:System.Security.Claims.ClaimsIdentity> objekt a <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> vlastnost tohoto objektu není, je <xref:System.Security.Claims.ClaimsIdentity> `null` <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> vlastnost připojena pomocí <xref:System.Security.Claims.ClaimsIdentity.Clone> metody.</span><span class="sxs-lookup"><span data-stu-id="63373-104">If the <xref:System.Security.Principal.IIdentity?displayProperty=fullName> argument is a <xref:System.Security.Claims.ClaimsIdentity> object, and the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property of that <xref:System.Security.Claims.ClaimsIdentity> object is not `null`, the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property is attached by using the <xref:System.Security.Claims.ClaimsIdentity.Clone> method.</span></span> <span data-ttu-id="63373-105">V rozhraní Framework 4.6.1 a starších verzích <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> je vlastnost připojena jako stávající odkaz. Z důvodu této změny, počínaje .NET Framework 4.6.2, není <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> vlastnost nového <xref:System.Security.Claims.ClaimsIdentity> objektu shodná s <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> vlastností <xref:System.Security.Principal.IIdentity?displayProperty=fullName> argumentu konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="63373-105">In the Framework 4.6.1 and earlier versions, the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property is attached as an existing reference.Because of this change, starting with the .NET Framework 4.6.2, the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property of the new <xref:System.Security.Claims.ClaimsIdentity> object is not equal to the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property of the constructor's <xref:System.Security.Principal.IIdentity?displayProperty=fullName> argument.</span></span> <span data-ttu-id="63373-106">V .NET Framework 4.6.1 a dřívějších verzích se rovná.</span><span class="sxs-lookup"><span data-stu-id="63373-106">In the .NET Framework 4.6.1 and earlier versions, it is equal.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="63373-107">Návrh</span><span class="sxs-lookup"><span data-stu-id="63373-107">Suggestion</span></span>

<span data-ttu-id="63373-108">Pokud je toto chování nežádoucí, můžete předchozí chování obnovit nastavením `Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity` přepínače v konfiguračním souboru aplikace na `true` .</span><span class="sxs-lookup"><span data-stu-id="63373-108">If this behavior is undesirable, you can restore the previous behavior by setting the `Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity` switch in your application configuration file to `true`.</span></span> <span data-ttu-id="63373-109">To vyžaduje, abyste do `<runtime>` oddílu web.config souboru přidali následující:</span><span class="sxs-lookup"><span data-stu-id="63373-109">This requires that you add the following to the `<runtime>` section of your web.config file:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="63373-110">Name</span><span class="sxs-lookup"><span data-stu-id="63373-110">Name</span></span>    | <span data-ttu-id="63373-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="63373-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="63373-112">Rozsah</span><span class="sxs-lookup"><span data-stu-id="63373-112">Scope</span></span>   | <span data-ttu-id="63373-113">Edge</span><span class="sxs-lookup"><span data-stu-id="63373-113">Edge</span></span>        |
| <span data-ttu-id="63373-114">Verze</span><span class="sxs-lookup"><span data-stu-id="63373-114">Version</span></span> | <span data-ttu-id="63373-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="63373-115">4.6.2</span></span>       |
| <span data-ttu-id="63373-116">Typ</span><span class="sxs-lookup"><span data-stu-id="63373-116">Type</span></span>    | <span data-ttu-id="63373-117">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="63373-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="63373-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="63373-118">Affected APIs</span></span>

- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity)>
- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim})>
- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim},System.String,System.String,System.String)>
