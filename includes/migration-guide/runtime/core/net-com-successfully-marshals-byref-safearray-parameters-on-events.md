---
ms.openlocfilehash: d5768a0c25bcd0880cbffde9e57ca9fe7a81cf06
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665603"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a><span data-ttu-id="8b3c2-101">.NET COM úspěšně zařazuje parametry ByRef SafeArray událostí</span><span class="sxs-lookup"><span data-stu-id="8b3c2-101">.NET COM successfully marshals ByRef SafeArray parameters on events</span></span>

|   |   |
|---|---|
|<span data-ttu-id="8b3c2-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="8b3c2-102">Details</span></span>|<span data-ttu-id="8b3c2-103">V rozhraní .NET Framework 4.7.2 a předchozími verzemi, ByRef [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) parametru u události COM selže k zařazování zpět do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="8b3c2-103">In the .NET Framework 4.7.2 and earlier versions, a ByRef [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) parameter on a COM event would fail to marshal back to native code.</span></span>  <span data-ttu-id="8b3c2-104">Díky této změně [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) je nyní zařazeno úspěšně.</span><span class="sxs-lookup"><span data-stu-id="8b3c2-104">With this change the [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) is now marshalled successfully.</span></span><ul><li><span data-ttu-id="8b3c2-105">[x] quirked</span><span class="sxs-lookup"><span data-stu-id="8b3c2-105">[ x ] Quirked</span></span></li></ul>|
|<span data-ttu-id="8b3c2-106">Doporučení</span><span class="sxs-lookup"><span data-stu-id="8b3c2-106">Suggestion</span></span>|<span data-ttu-id="8b3c2-107">Pokud správně zařazování SafeArray typu ByRef parametrů v události COM přeruší provádění, můžete zakázat tento kód tak, že přidáte následující konfigurační přepínač do konfigurace vaší aplikace:</span><span class="sxs-lookup"><span data-stu-id="8b3c2-107">If properly marshalling ByRef SafeArray parameters on COM Events breaks execution, you can disable this code by adding the following configuration switch to your application config:</span></span><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="8b3c2-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="8b3c2-108">Scope</span></span>|<span data-ttu-id="8b3c2-109">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="8b3c2-109">Minor</span></span>|
|<span data-ttu-id="8b3c2-110">Version</span><span class="sxs-lookup"><span data-stu-id="8b3c2-110">Version</span></span>|<span data-ttu-id="8b3c2-111">4.8</span><span class="sxs-lookup"><span data-stu-id="8b3c2-111">4.8</span></span>|
|<span data-ttu-id="8b3c2-112">Type</span><span class="sxs-lookup"><span data-stu-id="8b3c2-112">Type</span></span>|<span data-ttu-id="8b3c2-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="8b3c2-113">Runtime</span></span>|
