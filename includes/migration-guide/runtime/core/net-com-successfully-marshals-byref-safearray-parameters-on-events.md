---
ms.openlocfilehash: 9c72bc686e014a0bffdf272e3813358d1b29cc66
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2019
ms.locfileid: "65198921"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a><span data-ttu-id="c37fa-101">.NET COM úspěšně zařazuje parametry ByRef SafeArray událostí</span><span class="sxs-lookup"><span data-stu-id="c37fa-101">.NET COM successfully marshals ByRef SafeArray parameters on events</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c37fa-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="c37fa-102">Details</span></span>|<span data-ttu-id="c37fa-103">V rozhraní .NET Framework 4.7.2 a předchozími verzemi, ByRef [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) parametru u události COM selže k zařazování zpět do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="c37fa-103">In the .NET Framework 4.7.2 and earlier versions, a ByRef [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) parameter on a COM event would fail to marshal back to native code.</span></span>  <span data-ttu-id="c37fa-104">Díky této změně [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) je teď úspěšně zařazené.</span><span class="sxs-lookup"><span data-stu-id="c37fa-104">With this change the [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) is now marshaled successfully.</span></span><ul><li><span data-ttu-id="c37fa-105">[x] quirked</span><span class="sxs-lookup"><span data-stu-id="c37fa-105">[ x ] Quirked</span></span></li></ul>|
|<span data-ttu-id="c37fa-106">Doporučení</span><span class="sxs-lookup"><span data-stu-id="c37fa-106">Suggestion</span></span>|<span data-ttu-id="c37fa-107">Pokud správně zařazování SafeArray typu ByRef parametrů v události COM přeruší provádění, můžete zakázat tento kód tak, že přidáte následující konfigurační přepínač do konfigurace vaší aplikace:</span><span class="sxs-lookup"><span data-stu-id="c37fa-107">If properly marshaling ByRef SafeArray parameters on COM Events breaks execution, you can disable this code by adding the following configuration switch to your application config:</span></span><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="c37fa-108">Scope</span><span class="sxs-lookup"><span data-stu-id="c37fa-108">Scope</span></span>|<span data-ttu-id="c37fa-109">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="c37fa-109">Minor</span></span>|
|<span data-ttu-id="c37fa-110">Version</span><span class="sxs-lookup"><span data-stu-id="c37fa-110">Version</span></span>|<span data-ttu-id="c37fa-111">4.8</span><span class="sxs-lookup"><span data-stu-id="c37fa-111">4.8</span></span>|
|<span data-ttu-id="c37fa-112">Type</span><span class="sxs-lookup"><span data-stu-id="c37fa-112">Type</span></span>|<span data-ttu-id="c37fa-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="c37fa-113">Runtime</span></span>|
