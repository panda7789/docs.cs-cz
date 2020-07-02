---
ms.openlocfilehash: 51208762cea2a5688c5d43e5d444d4e014e5f0b4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621139"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a><span data-ttu-id="7bdda-101">X509Certificate2. ToString (Boolean) nevrátí hodnotu Now, pokud rozhraní .NET nemůže zpracovat certifikát.</span><span class="sxs-lookup"><span data-stu-id="7bdda-101">X509Certificate2.ToString(Boolean) does not throw now when .NET cannot handle the certificate</span></span>

#### <a name="details"></a><span data-ttu-id="7bdda-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="7bdda-102">Details</span></span>

<span data-ttu-id="7bdda-103">V .NET Framework 4.5.2 a starších verzích vyvolala Tato metoda, pokud <code>true</code> byla předána parametru verbose, a nainstalují se certifikáty, které nepodporovala .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7bdda-103">In .NET Framework 4.5.2 and earlier versions, this method would throw if <code>true</code> was passed for the verbose parameter and there were certificates installed that weren't supported by the .NET Framework.</span></span> <span data-ttu-id="7bdda-104">Nyní bude metoda úspěšná a vrátí platný řetězec, který vynechá nepřístupné části certifikátu.</span><span class="sxs-lookup"><span data-stu-id="7bdda-104">Now, the method will succeed and return a valid string that omits the inaccessible portions of the certificate.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7bdda-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="7bdda-105">Suggestion</span></span>

<span data-ttu-id="7bdda-106">Jakýkoli kód, který závisí na <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> tom, by měl být aktualizován, aby bylo možné očekávat, že vrácený řetězec může vyloučit některá data certifikátu (například veřejný klíč, privátní klíč a rozšíření) v některých případech, kdy by předtím bylo vyvoláno rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="7bdda-106">Any code depending on <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> should be updated to expect that the returned string may exclude some certificate data (such as public key, private key, and extensions) in some cases in which the API would have previously thrown.</span></span>

| <span data-ttu-id="7bdda-107">Name</span><span class="sxs-lookup"><span data-stu-id="7bdda-107">Name</span></span>    | <span data-ttu-id="7bdda-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="7bdda-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7bdda-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="7bdda-109">Scope</span></span>   |<span data-ttu-id="7bdda-110">Edge</span><span class="sxs-lookup"><span data-stu-id="7bdda-110">Edge</span></span>|
|<span data-ttu-id="7bdda-111">Verze</span><span class="sxs-lookup"><span data-stu-id="7bdda-111">Version</span></span>|<span data-ttu-id="7bdda-112">4.6</span><span class="sxs-lookup"><span data-stu-id="7bdda-112">4.6</span></span>|
|<span data-ttu-id="7bdda-113">Typ</span><span class="sxs-lookup"><span data-stu-id="7bdda-113">Type</span></span>|<span data-ttu-id="7bdda-114">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="7bdda-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7bdda-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="7bdda-115">Affected APIs</span></span>

-<xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|
