---
ms.openlocfilehash: 0dfc87201b9b31cd9d936f2c965c7d0ca0140cab
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774143"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a><span data-ttu-id="a6513-101">X509Certificate2.ToString(Boolean) nevyvolá nyní při .NET nemůže zpracovat certifikát</span><span class="sxs-lookup"><span data-stu-id="a6513-101">X509Certificate2.ToString(Boolean) does not throw now when .NET cannot handle the certificate</span></span>

|   |   |
|---|---|
|<span data-ttu-id="a6513-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="a6513-102">Details</span></span>|<span data-ttu-id="a6513-103">V rozhraní .NET Framework 4.5.2 a dřívějších verzích, tato metoda vyvolá-li <code>true</code> byla předána parametru verbose nebyly nainstalovány certifikáty, které nejsou podporované rozhraním .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a6513-103">In .NET Framework 4.5.2 and earlier versions, this method would throw if <code>true</code> was passed for the verbose parameter and there were certificates installed that weren't supported by the .NET Framework.</span></span> <span data-ttu-id="a6513-104">Metoda teď bude úspěšné a vrátit platný řetězec, který vynechá části nepřístupný certifikátu.</span><span class="sxs-lookup"><span data-stu-id="a6513-104">Now, the method will succeed and return a valid string that omits the inaccessible portions of the certificate.</span></span>|
|<span data-ttu-id="a6513-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="a6513-105">Suggestion</span></span>|<span data-ttu-id="a6513-106">Žádný kód v závislosti na <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> očekávat, že vrácený řetězec může vyloučit některé data certifikátu (jako je například veřejný klíč, privátní klíč a rozšíření) v některých případech, ve kterých rozhraní API by mít dříve vyvolána je třeba aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="a6513-106">Any code depending on <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> should be updated to expect that the returned string may exclude some certificate data (such as public key, private key, and extensions) in some cases in which the API would have previously thrown.</span></span>|
|<span data-ttu-id="a6513-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="a6513-107">Scope</span></span>|<span data-ttu-id="a6513-108">Edge</span><span class="sxs-lookup"><span data-stu-id="a6513-108">Edge</span></span>|
|<span data-ttu-id="a6513-109">Version</span><span class="sxs-lookup"><span data-stu-id="a6513-109">Version</span></span>|<span data-ttu-id="a6513-110">4.6</span><span class="sxs-lookup"><span data-stu-id="a6513-110">4.6</span></span>|
|<span data-ttu-id="a6513-111">Type</span><span class="sxs-lookup"><span data-stu-id="a6513-111">Type</span></span>|<span data-ttu-id="a6513-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="a6513-112">Runtime</span></span>|
|<span data-ttu-id="a6513-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="a6513-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|
