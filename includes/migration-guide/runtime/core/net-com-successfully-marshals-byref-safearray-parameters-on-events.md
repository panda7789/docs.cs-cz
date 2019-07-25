---
ms.openlocfilehash: 6ff23bbe8c48235770d39cb7d35a1df7de6c5201
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68440259"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a><span data-ttu-id="71cda-101">.NET COM úspěšně zařazování parametrů ByRef SafeArray u událostí</span><span class="sxs-lookup"><span data-stu-id="71cda-101">.NET COM successfully marshals ByRef SafeArray parameters on events</span></span>

|   |   |
|---|---|
|<span data-ttu-id="71cda-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="71cda-102">Details</span></span>|<span data-ttu-id="71cda-103">V .NET Framework 4.7.2 a dřívějších verzích se parametr ByRef [SAFEARRAY](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) v události com nepodaří zařazovat zpátky do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="71cda-103">In the .NET Framework 4.7.2 and earlier versions, a ByRef [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) parameter on a COM event would fail to marshal back to native code.</span></span>  <span data-ttu-id="71cda-104">V této změně je nyní řazení [SAFEARRAY](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) úspěšně zařazování.</span><span class="sxs-lookup"><span data-stu-id="71cda-104">With this change the [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) is now marshalled successfully.</span></span><ul><li><span data-ttu-id="71cda-105">[x] Quirked</span><span class="sxs-lookup"><span data-stu-id="71cda-105">[ x ] Quirked</span></span></li></ul>|
|<span data-ttu-id="71cda-106">Doporučení</span><span class="sxs-lookup"><span data-stu-id="71cda-106">Suggestion</span></span>|<span data-ttu-id="71cda-107">Pokud správně zařadíte parametry SafeArray typu ByRef u událostí modelu COM, které přeruší provádění, můžete tento kód zakázat přidáním následujícího konfiguračního přepínače do konfigurace aplikace:</span><span class="sxs-lookup"><span data-stu-id="71cda-107">If properly marshalling ByRef SafeArray parameters on COM Events breaks execution, you can disable this code by adding the following configuration switch to your application config:</span></span><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="71cda-108">Scope</span><span class="sxs-lookup"><span data-stu-id="71cda-108">Scope</span></span>|<span data-ttu-id="71cda-109">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="71cda-109">Minor</span></span>|
|<span data-ttu-id="71cda-110">Version</span><span class="sxs-lookup"><span data-stu-id="71cda-110">Version</span></span>|<span data-ttu-id="71cda-111">4.8</span><span class="sxs-lookup"><span data-stu-id="71cda-111">4.8</span></span>|
|<span data-ttu-id="71cda-112">type</span><span class="sxs-lookup"><span data-stu-id="71cda-112">Type</span></span>|<span data-ttu-id="71cda-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="71cda-113">Runtime</span></span>|
