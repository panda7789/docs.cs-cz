---
ms.openlocfilehash: d29be721b50d1c93723b325774a06e86f77dbebf
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621091"
---
### <a name="wcf-addressheadercollection-now-throws-an-argumentexception-if-an-addressheader-element-is-null"></a><span data-ttu-id="aeb7b-101">WCF AddressHeaderCollection nyní vyvolá výjimku ArgumentException, pokud má element addressHeader hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="aeb7b-101">WCF AddressHeaderCollection now throws an ArgumentException if an addressHeader element is null</span></span>

#### <a name="details"></a><span data-ttu-id="aeb7b-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="aeb7b-102">Details</span></span>

<span data-ttu-id="aeb7b-103">Počínaje .NET Framework 4.7.1 konstruktor vyvolá výjimku, <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> <xref:System.ArgumentException> Pokud je jeden z prvků <code>null</code> .</span><span class="sxs-lookup"><span data-stu-id="aeb7b-103">Starting with the .NET Framework 4.7.1, the <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> constructor throws an <xref:System.ArgumentException> if one of the elements is <code>null</code>.</span></span> <span data-ttu-id="aeb7b-104">V .NET Framework 4,7 a dřívějších verzích není vyvolána žádná výjimka.</span><span class="sxs-lookup"><span data-stu-id="aeb7b-104">In the .NET Framework 4.7 and earlier versions, no exception is thrown.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="aeb7b-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="aeb7b-105">Suggestion</span></span>

<span data-ttu-id="aeb7b-106">Pokud narazíte na problémy s kompatibilitou s touto změnou .NET Framework 4.7.1 nebo novější verze, můžete si ji odhlásit přidáním následujícího řádku do <code>&lt;runtime&gt;</code> části app.config souboru::</span><span class="sxs-lookup"><span data-stu-id="aeb7b-106">If you encounter compatibility issues with this change on the .NET Framework 4.7.1 or a later version, you can opt-out of it by adding the following line to the <code>&lt;runtime&gt;</code> section of the app.config file::</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableAddressHeaderCollectionValidation=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="aeb7b-107">Name</span><span class="sxs-lookup"><span data-stu-id="aeb7b-107">Name</span></span>    | <span data-ttu-id="aeb7b-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="aeb7b-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="aeb7b-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="aeb7b-109">Scope</span></span>   |<span data-ttu-id="aeb7b-110">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="aeb7b-110">Minor</span></span>|
|<span data-ttu-id="aeb7b-111">Verze</span><span class="sxs-lookup"><span data-stu-id="aeb7b-111">Version</span></span>|<span data-ttu-id="aeb7b-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="aeb7b-112">4.7.1</span></span>|
|<span data-ttu-id="aeb7b-113">Typ</span><span class="sxs-lookup"><span data-stu-id="aeb7b-113">Type</span></span>|<span data-ttu-id="aeb7b-114">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="aeb7b-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="aeb7b-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="aeb7b-115">Affected APIs</span></span>

-<xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})></li></ul>|
