---
ms.openlocfilehash: cf51d5f6b3eee7189fd9613b3d780a829d197a04
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557998"
---
### <a name="systemsecuritycryptographyoid-is-functionally-init-only"></a><span data-ttu-id="a58f6-101">System. Security. Cryptography. OID je funkčně funkční jenom pro inicializaci.</span><span class="sxs-lookup"><span data-stu-id="a58f6-101">System.Security.Cryptography.Oid is functionally init-only</span></span>

<span data-ttu-id="a58f6-102"><xref:System.Security.Cryptography.Oid?displayProperty=fullName>Třída, která se používá k reprezentaci hodnot identifikátoru objektu ASN. 1 a jejich "" přívětivých "názvů, byla dříve úplně proměnlivá.</span><span class="sxs-lookup"><span data-stu-id="a58f6-102">The <xref:System.Security.Cryptography.Oid?displayProperty=fullName> class, which is used to represent ASN.1 Object Identifier values and their "friendly" names, was previously fully mutable.</span></span> <span data-ttu-id="a58f6-103">Tento proměnlivost byl často přepsaný nebo byl neočekávaně.</span><span class="sxs-lookup"><span data-stu-id="a58f6-103">This mutability was often overlooked or came as a surprise.</span></span> <span data-ttu-id="a58f6-104">Vlastnost Setters nyní vyvolá <xref:System.PlatformNotSupportedException> při pokusu o změnu hodnoty poté, co je již přiřazena.</span><span class="sxs-lookup"><span data-stu-id="a58f6-104">The property setters now throw a <xref:System.PlatformNotSupportedException> when you attempt to change the value after it's already been assigned.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a58f6-105">Popis změny</span><span class="sxs-lookup"><span data-stu-id="a58f6-105">Change description</span></span>

<span data-ttu-id="a58f6-106">V předchozích verzích lze metody set vlastnosti <xref:System.Security.Cryptography.Oid> použít pro změnu hodnoty <xref:System.Security.Cryptography.Oid.FriendlyName> <xref:System.Security.Cryptography.Oid.Value> vlastností a.</span><span class="sxs-lookup"><span data-stu-id="a58f6-106">In previous versions, the property setters on <xref:System.Security.Cryptography.Oid> can be used to change the value of the <xref:System.Security.Cryptography.Oid.FriendlyName> and <xref:System.Security.Cryptography.Oid.Value> properties.</span></span>

<span data-ttu-id="a58f6-107">V rozhraní .NET 5,0 a novějších verzích lze třídy setter použít pouze k inicializaci hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a58f6-107">In .NET 5.0 and later versions, the property setters can only be used to initialize the value.</span></span> <span data-ttu-id="a58f6-108">Jakmile má vlastnost hodnotu, buď z konstruktoru nebo předchozího volání metody setter vlastnosti, metoda setter vlastnosti vždy vyvolá <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="a58f6-108">Once the property has a value, either from a constructor or a previous call to the property setter, the property setter always throws a <xref:System.PlatformNotSupportedException>.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a58f6-109">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="a58f6-109">Reason for change</span></span>

<span data-ttu-id="a58f6-110">Tato změna umožňuje znovu použít <xref:System.Security.Cryptography.Oid> objekty jako součást vrácených hodnot ve veřejných rozhraních API pro omezení profilů přidělení objektů.</span><span class="sxs-lookup"><span data-stu-id="a58f6-110">This change enables the reuse of <xref:System.Security.Cryptography.Oid> objects as part of return values in public APIs to reduce object allocation profiles.</span></span> <span data-ttu-id="a58f6-111">Nemusíte vytvářet dočasné kopie "obrannou linií", když <xref:System.Security.Cryptography.Oid> se hodnoty používají jako vstupy.</span><span class="sxs-lookup"><span data-stu-id="a58f6-111">It avoids the need to create temporary "defensive" copies when <xref:System.Security.Cryptography.Oid> values are used as inputs.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a58f6-112">Představená verze</span><span class="sxs-lookup"><span data-stu-id="a58f6-112">Version introduced</span></span>

<span data-ttu-id="a58f6-113">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="a58f6-113">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a58f6-114">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="a58f6-114">Recommended action</span></span>

<span data-ttu-id="a58f6-115">Vyhněte se použití <xref:System.Security.Cryptography.Oid> jiných nastavení vlastností než pro inicializaci objektu.</span><span class="sxs-lookup"><span data-stu-id="a58f6-115">Avoid using the <xref:System.Security.Cryptography.Oid> property setters other than for object initialization.</span></span> <span data-ttu-id="a58f6-116">Chcete-li reprezentovat novou hodnotu, místo změny hodnoty u existujícího objektu použijte novou instanci.</span><span class="sxs-lookup"><span data-stu-id="a58f6-116">To represent a new value, use a new instance instead of changing the value on an existing object.</span></span>

#### <a name="category"></a><span data-ttu-id="a58f6-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="a58f6-117">Category</span></span>

<span data-ttu-id="a58f6-118">Kryptografie</span><span class="sxs-lookup"><span data-stu-id="a58f6-118">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a58f6-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="a58f6-119">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Oid.FriendlyName?displayProperty=fullName>
- <xref:System.Security.Cryptography.Oid.Value?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Security.Cryptography.Oid.FriendlyName`
- `P:System.Security.Cryptography.Oid.Value`

-->
