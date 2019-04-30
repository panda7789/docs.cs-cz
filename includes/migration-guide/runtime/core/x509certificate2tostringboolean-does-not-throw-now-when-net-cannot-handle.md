---
ms.openlocfilehash: 0dfc87201b9b31cd9d936f2c965c7d0ca0140cab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664428"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a><span data-ttu-id="4dfe0-101">X509Certificate2.ToString(Boolean) nevyvolá nyní při .NET nemůže zpracovat certifikát</span><span class="sxs-lookup"><span data-stu-id="4dfe0-101">X509Certificate2.ToString(Boolean) does not throw now when .NET cannot handle the certificate</span></span>

|   |   |
|---|---|
|<span data-ttu-id="4dfe0-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="4dfe0-102">Details</span></span>|<span data-ttu-id="4dfe0-103">V rozhraní .NET Framework 4.5.2 a dřívějších verzích, tato metoda vyvolá-li <code>true</code> byla předána parametru verbose nebyly nainstalovány certifikáty, které nejsou podporované rozhraním .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4dfe0-103">In .NET Framework 4.5.2 and earlier versions, this method would throw if <code>true</code> was passed for the verbose parameter and there were certificates installed that weren't supported by the .NET Framework.</span></span> <span data-ttu-id="4dfe0-104">Metoda teď bude úspěšné a vrátit platný řetězec, který vynechá části nepřístupný certifikátu.</span><span class="sxs-lookup"><span data-stu-id="4dfe0-104">Now, the method will succeed and return a valid string that omits the inaccessible portions of the certificate.</span></span>|
|<span data-ttu-id="4dfe0-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="4dfe0-105">Suggestion</span></span>|<span data-ttu-id="4dfe0-106">Žádný kód v závislosti na <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> očekávat, že vrácený řetězec může vyloučit některé data certifikátu (jako je například veřejný klíč, privátní klíč a rozšíření) v některých případech, ve kterých rozhraní API by mít dříve vyvolána je třeba aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="4dfe0-106">Any code depending on <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> should be updated to expect that the returned string may exclude some certificate data (such as public key, private key, and extensions) in some cases in which the API would have previously thrown.</span></span>|
|<span data-ttu-id="4dfe0-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="4dfe0-107">Scope</span></span>|<span data-ttu-id="4dfe0-108">Edge</span><span class="sxs-lookup"><span data-stu-id="4dfe0-108">Edge</span></span>|
|<span data-ttu-id="4dfe0-109">Version</span><span class="sxs-lookup"><span data-stu-id="4dfe0-109">Version</span></span>|<span data-ttu-id="4dfe0-110">4.6</span><span class="sxs-lookup"><span data-stu-id="4dfe0-110">4.6</span></span>|
|<span data-ttu-id="4dfe0-111">Type</span><span class="sxs-lookup"><span data-stu-id="4dfe0-111">Type</span></span>|<span data-ttu-id="4dfe0-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="4dfe0-112">Runtime</span></span>|
|<span data-ttu-id="4dfe0-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="4dfe0-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|
