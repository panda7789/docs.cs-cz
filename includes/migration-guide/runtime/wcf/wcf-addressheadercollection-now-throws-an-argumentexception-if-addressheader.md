---
ms.openlocfilehash: a26b8c8a6315e57e70f4810ac4f5fb7ab4ba9b58
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760432"
---
### <a name="wcf-addressheadercollection-now-throws-an-argumentexception-if-an-addressheader-element-is-null"></a><span data-ttu-id="9ab4f-101">WCF AddressHeaderCollection nyní vyvolá ArgumentException, pokud prvek do objektu addressHeader má hodnotu null</span><span class="sxs-lookup"><span data-stu-id="9ab4f-101">WCF AddressHeaderCollection now throws an ArgumentException if an addressHeader element is null</span></span>

|   |   |
|---|---|
|<span data-ttu-id="9ab4f-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="9ab4f-102">Details</span></span>|<span data-ttu-id="9ab4f-103">Od verze rozhraní .NET Framework 4.7.1, <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> vyvolá konstruktor <xref:System.ArgumentException> Pokud jeden z elementů <code>null</code>.</span><span class="sxs-lookup"><span data-stu-id="9ab4f-103">Starting with the .NET Framework 4.7.1, the <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> constructor throws an <xref:System.ArgumentException> if one of the elements is <code>null</code>.</span></span> <span data-ttu-id="9ab4f-104">V rozhraní .NET Framework 4.7 a dřívějších verzích není vyvolána žádná výjimka.</span><span class="sxs-lookup"><span data-stu-id="9ab4f-104">In the .NET Framework 4.7 and earlier versions, no exception is thrown.</span></span>|
|<span data-ttu-id="9ab4f-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="9ab4f-105">Suggestion</span></span>|<span data-ttu-id="9ab4f-106">Pokud narazíte na problémy s kompatibilitou s touto změnou v rozhraní .NET Framework 4.7.1 nebo novější, je můžete odhlásit ho tak, že přidáte následující řádek, který <code>&lt;runtime&gt;</code> část souboru app.config::</span><span class="sxs-lookup"><span data-stu-id="9ab4f-106">If you encounter compatibility issues with this change on the .NET Framework 4.7.1 or a later version, you can opt-out of it by adding the following line to the <code>&lt;runtime&gt;</code> section of the app.config file::</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableAddressHeaderCollectionValidation=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="9ab4f-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="9ab4f-107">Scope</span></span>|<span data-ttu-id="9ab4f-108">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="9ab4f-108">Minor</span></span>|
|<span data-ttu-id="9ab4f-109">Version</span><span class="sxs-lookup"><span data-stu-id="9ab4f-109">Version</span></span>|<span data-ttu-id="9ab4f-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="9ab4f-110">4.7.1</span></span>|
|<span data-ttu-id="9ab4f-111">Type</span><span class="sxs-lookup"><span data-stu-id="9ab4f-111">Type</span></span>|<span data-ttu-id="9ab4f-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="9ab4f-112">Runtime</span></span>|
|<span data-ttu-id="9ab4f-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="9ab4f-113">Affected APIs</span></span>|<ul><li><xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})?displayProperty=nameWithType></li></ul>|

