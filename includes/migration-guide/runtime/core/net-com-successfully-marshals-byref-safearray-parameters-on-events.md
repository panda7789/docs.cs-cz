---
ms.openlocfilehash: 77e9d28d79a92cf1523e4ef5779d78394b00ae80
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621987"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a><span data-ttu-id="3b972-101">.NET COM úspěšně zařazování parametrů ByRef SafeArray u událostí</span><span class="sxs-lookup"><span data-stu-id="3b972-101">.NET COM successfully marshals ByRef SafeArray parameters on events</span></span>

#### <a name="details"></a><span data-ttu-id="3b972-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="3b972-102">Details</span></span>

<span data-ttu-id="3b972-103">V .NET Framework 4.7.2 a dřívějších verzích se parametr ByRef [SAFEARRAY](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) v události com nepodaří zařazovat zpátky do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="3b972-103">In the .NET Framework 4.7.2 and earlier versions, a ByRef [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) parameter on a COM event would fail to marshal back to native code.</span></span>  <span data-ttu-id="3b972-104">V této změně je nyní řazení [SAFEARRAY](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) úspěšně zařazování.</span><span class="sxs-lookup"><span data-stu-id="3b972-104">With this change the [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) is now marshalled successfully.</span></span><ul><li><span data-ttu-id="3b972-105">[x] Quirked</span><span class="sxs-lookup"><span data-stu-id="3b972-105">[ x ] Quirked</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="3b972-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="3b972-106">Suggestion</span></span>

<span data-ttu-id="3b972-107">Pokud správně zařadíte parametry SafeArray typu ByRef u událostí modelu COM, které přeruší provádění, můžete tento kód zakázat přidáním následujícího konfiguračního přepínače do konfigurace aplikace:</span><span class="sxs-lookup"><span data-stu-id="3b972-107">If properly marshalling ByRef SafeArray parameters on COM Events breaks execution, you can disable this code by adding the following configuration switch to your application config:</span></span><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="3b972-108">Name</span><span class="sxs-lookup"><span data-stu-id="3b972-108">Name</span></span>    | <span data-ttu-id="3b972-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3b972-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3b972-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="3b972-110">Scope</span></span>   |<span data-ttu-id="3b972-111">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="3b972-111">Minor</span></span>|
|<span data-ttu-id="3b972-112">Verze</span><span class="sxs-lookup"><span data-stu-id="3b972-112">Version</span></span>|<span data-ttu-id="3b972-113">4,8</span><span class="sxs-lookup"><span data-stu-id="3b972-113">4.8</span></span>|
|<span data-ttu-id="3b972-114">Typ</span><span class="sxs-lookup"><span data-stu-id="3b972-114">Type</span></span>|<span data-ttu-id="3b972-115">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="3b972-115">Runtime</span></span>|
