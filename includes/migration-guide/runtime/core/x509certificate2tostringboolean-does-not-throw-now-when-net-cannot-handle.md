---
ms.openlocfilehash: 0dfc87201b9b31cd9d936f2c965c7d0ca0140cab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858584"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a><span data-ttu-id="e30b7-101">X509Certificate2.ToString(Boolean) nevyvolá nyní, když rozhraní .NET nemůže zpracovat certifikát</span><span class="sxs-lookup"><span data-stu-id="e30b7-101">X509Certificate2.ToString(Boolean) does not throw now when .NET cannot handle the certificate</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e30b7-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e30b7-102">Details</span></span>|<span data-ttu-id="e30b7-103">V rozhraní .NET Framework 4.5.2 a starších <code>true</code> verzích by tato metoda vyvolala, pokud by byla předána pro podrobný parametr a byly nainstalovány certifikáty, které nebyly podporovány rozhraním .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e30b7-103">In .NET Framework 4.5.2 and earlier versions, this method would throw if <code>true</code> was passed for the verbose parameter and there were certificates installed that weren't supported by the .NET Framework.</span></span> <span data-ttu-id="e30b7-104">Nyní metoda bude úspěšné a vrátí platný řetězec, který vynechá nepřístupné části certifikátu.</span><span class="sxs-lookup"><span data-stu-id="e30b7-104">Now, the method will succeed and return a valid string that omits the inaccessible portions of the certificate.</span></span>|
|<span data-ttu-id="e30b7-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="e30b7-105">Suggestion</span></span>|<span data-ttu-id="e30b7-106">Jakýkoli kód <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> v závislosti na by měl být aktualizován očekávat, že vrácený řetězec může vyloučit některá data certifikátu (například veřejný klíč, soukromý klíč a rozšíření) v některých případech, ve kterých by rozhraní API dříve vyvolána.</span><span class="sxs-lookup"><span data-stu-id="e30b7-106">Any code depending on <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> should be updated to expect that the returned string may exclude some certificate data (such as public key, private key, and extensions) in some cases in which the API would have previously thrown.</span></span>|
|<span data-ttu-id="e30b7-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="e30b7-107">Scope</span></span>|<span data-ttu-id="e30b7-108">Edge</span><span class="sxs-lookup"><span data-stu-id="e30b7-108">Edge</span></span>|
|<span data-ttu-id="e30b7-109">Version</span><span class="sxs-lookup"><span data-stu-id="e30b7-109">Version</span></span>|<span data-ttu-id="e30b7-110">4.6</span><span class="sxs-lookup"><span data-stu-id="e30b7-110">4.6</span></span>|
|<span data-ttu-id="e30b7-111">Typ</span><span class="sxs-lookup"><span data-stu-id="e30b7-111">Type</span></span>|<span data-ttu-id="e30b7-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="e30b7-112">Runtime</span></span>|
|<span data-ttu-id="e30b7-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="e30b7-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|
