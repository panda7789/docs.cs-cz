---
ms.openlocfilehash: d48519443aeee05617538cf2cc12bea49ad3e16d
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761277"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a><span data-ttu-id="d8adc-101">X509Certificate2.ToString(Boolean) nevyvolá nyní při .NET nemůže zpracovat certifikát</span><span class="sxs-lookup"><span data-stu-id="d8adc-101">X509Certificate2.ToString(Boolean) does not throw now when .NET cannot handle the certificate</span></span>

|   |   |
|---|---|
|<span data-ttu-id="d8adc-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="d8adc-102">Details</span></span>|<span data-ttu-id="d8adc-103">V rozhraní .NET Framework 4.5.2 a dřívějších verzích, tato metoda vyvolá-li <code>true</code> byla předána parametru verbose nebyly nainstalovány certifikáty, které nejsou podporované rozhraním .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d8adc-103">In .NET Framework 4.5.2 and earlier versions, this method would throw if <code>true</code> was passed for the verbose parameter and there were certificates installed that weren't supported by the .NET Framework.</span></span> <span data-ttu-id="d8adc-104">Metoda teď bude úspěšné a vrátit platný řetězec, který vynechá části nepřístupný certifikátu.</span><span class="sxs-lookup"><span data-stu-id="d8adc-104">Now, the method will succeed and return a valid string that omits the inaccessible portions of the certificate.</span></span>|
|<span data-ttu-id="d8adc-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="d8adc-105">Suggestion</span></span>|<span data-ttu-id="d8adc-106">Žádný kód v závislosti na <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> očekávat, že vrácený řetězec může vyloučit některé data certifikátu (jako je například veřejný klíč, privátní klíč a rozšíření) v některých případech, ve kterých rozhraní API by mít dříve vyvolána je třeba aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="d8adc-106">Any code depending on <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> should be updated to expect that the returned string may exclude some certificate data (such as public key, private key, and extensions) in some cases in which the API would have previously thrown.</span></span>|
|<span data-ttu-id="d8adc-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="d8adc-107">Scope</span></span>|<span data-ttu-id="d8adc-108">Edge</span><span class="sxs-lookup"><span data-stu-id="d8adc-108">Edge</span></span>|
|<span data-ttu-id="d8adc-109">Version</span><span class="sxs-lookup"><span data-stu-id="d8adc-109">Version</span></span>|<span data-ttu-id="d8adc-110">4.6</span><span class="sxs-lookup"><span data-stu-id="d8adc-110">4.6</span></span>|
|<span data-ttu-id="d8adc-111">Type</span><span class="sxs-lookup"><span data-stu-id="d8adc-111">Type</span></span>|<span data-ttu-id="d8adc-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="d8adc-112">Runtime</span></span>|
|<span data-ttu-id="d8adc-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="d8adc-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|

