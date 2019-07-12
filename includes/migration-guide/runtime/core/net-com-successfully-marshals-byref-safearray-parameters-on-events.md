---
ms.openlocfilehash: 2f4f92c8615b328caee2ad0b90028c76048026f4
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802705"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a><span data-ttu-id="4afd6-101">.NET COM úspěšně zařazuje parametry ByRef SafeArray událostí</span><span class="sxs-lookup"><span data-stu-id="4afd6-101">.NET COM successfully marshals ByRef SafeArray parameters on events</span></span>

|   |   |
|---|---|
|<span data-ttu-id="4afd6-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="4afd6-102">Details</span></span>|<span data-ttu-id="4afd6-103">V rozhraní .NET Framework 4.7.2 a předchozími verzemi, ByRef [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) parametru u události COM selže k zařazování zpět do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="4afd6-103">In the .NET Framework 4.7.2 and earlier versions, a ByRef [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) parameter on a COM event would fail to marshal back to native code.</span></span>  <span data-ttu-id="4afd6-104">Díky této změně [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) je nyní zařazeno úspěšně.</span><span class="sxs-lookup"><span data-stu-id="4afd6-104">With this change the [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) is now marshalled successfully.</span></span><ul><li><span data-ttu-id="4afd6-105">[x] quirked</span><span class="sxs-lookup"><span data-stu-id="4afd6-105">[ x ] Quirked</span></span></li></ul>|
|<span data-ttu-id="4afd6-106">Doporučení</span><span class="sxs-lookup"><span data-stu-id="4afd6-106">Suggestion</span></span>|<span data-ttu-id="4afd6-107">Pokud správně zařazování SafeArray typu ByRef parametrů v události COM přeruší provádění, můžete zakázat tento kód tak, že přidáte následující konfigurační přepínač do konfigurace vaší aplikace:</span><span class="sxs-lookup"><span data-stu-id="4afd6-107">If properly marshalling ByRef SafeArray parameters on COM Events breaks execution, you can disable this code by adding the following configuration switch to your application config:</span></span><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="4afd6-108">Scope</span><span class="sxs-lookup"><span data-stu-id="4afd6-108">Scope</span></span>|<span data-ttu-id="4afd6-109">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="4afd6-109">Minor</span></span>|
|<span data-ttu-id="4afd6-110">Version</span><span class="sxs-lookup"><span data-stu-id="4afd6-110">Version</span></span>|<span data-ttu-id="4afd6-111">4.8</span><span class="sxs-lookup"><span data-stu-id="4afd6-111">4.8</span></span>|
|<span data-ttu-id="4afd6-112">type</span><span class="sxs-lookup"><span data-stu-id="4afd6-112">Type</span></span>|<span data-ttu-id="4afd6-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="4afd6-113">Runtime</span></span>|

