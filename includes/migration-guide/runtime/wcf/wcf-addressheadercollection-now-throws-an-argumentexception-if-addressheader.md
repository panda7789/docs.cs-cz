---
ms.openlocfilehash: d29be721b50d1c93723b325774a06e86f77dbebf
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621091"
---
### <a name="wcf-addressheadercollection-now-throws-an-argumentexception-if-an-addressheader-element-is-null"></a>WCF AddressHeaderCollection nyní vyvolá výjimku ArgumentException, pokud má element addressHeader hodnotu null.

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4.7.1 konstruktor vyvolá výjimku, <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> <xref:System.ArgumentException> Pokud je jeden z prvků <code>null</code> . V .NET Framework 4,7 a dřívějších verzích není vyvolána žádná výjimka.

#### <a name="suggestion"></a>Návrh

Pokud narazíte na problémy s kompatibilitou s touto změnou .NET Framework 4.7.1 nebo novější verze, můžete si ji odhlásit přidáním následujícího řádku do <code>&lt;runtime&gt;</code> části app.config souboru::<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableAddressHeaderCollectionValidation=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.7.1|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})></li></ul>|
