---
ms.openlocfilehash: 6ff23bbe8c48235770d39cb7d35a1df7de6c5201
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "68440259"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a><span data-ttu-id="34de3-101">.NET COM úspěšně zařazuje parametry ByRef SafeArray na události</span><span class="sxs-lookup"><span data-stu-id="34de3-101">.NET COM successfully marshals ByRef SafeArray parameters on events</span></span>

|   |   |
|---|---|
|<span data-ttu-id="34de3-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="34de3-102">Details</span></span>|<span data-ttu-id="34de3-103">V rozhraní .NET Framework 4.7.2 a starších verzích by parametr ByRef [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) při události com selhal při zařazování zpět do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="34de3-103">In the .NET Framework 4.7.2 and earlier versions, a ByRef [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) parameter on a COM event would fail to marshal back to native code.</span></span>  <span data-ttu-id="34de3-104">S touto změnou [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) je nyní seřazené úspěšně.</span><span class="sxs-lookup"><span data-stu-id="34de3-104">With this change the [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) is now marshalled successfully.</span></span><ul><li><span data-ttu-id="34de3-105">[x] Nevychaný</span><span class="sxs-lookup"><span data-stu-id="34de3-105">[ x ] Quirked</span></span></li></ul>|
|<span data-ttu-id="34de3-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="34de3-106">Suggestion</span></span>|<span data-ttu-id="34de3-107">Pokud správně zařazování Parametrů ByRef SafeArray na události modelu COM přeruší spuštění, můžete zakázat tento kód přidáním následujícího přepínače konfigurace konfigurace aplikace:</span><span class="sxs-lookup"><span data-stu-id="34de3-107">If properly marshalling ByRef SafeArray parameters on COM Events breaks execution, you can disable this code by adding the following configuration switch to your application config:</span></span><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="34de3-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="34de3-108">Scope</span></span>|<span data-ttu-id="34de3-109">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="34de3-109">Minor</span></span>|
|<span data-ttu-id="34de3-110">Version</span><span class="sxs-lookup"><span data-stu-id="34de3-110">Version</span></span>|<span data-ttu-id="34de3-111">4.8</span><span class="sxs-lookup"><span data-stu-id="34de3-111">4.8</span></span>|
|<span data-ttu-id="34de3-112">Typ</span><span class="sxs-lookup"><span data-stu-id="34de3-112">Type</span></span>|<span data-ttu-id="34de3-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="34de3-113">Runtime</span></span>|
