---
ms.openlocfilehash: fa2a856911c7dcf81a39b7682a62a86c35328037
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275606"
---
### <a name="wcf-addressheadercollection-now-throws-an-argumentexception-if-an-addressheader-element-is-null"></a>WCF AddressHeaderCollection nyní vyvolá ArgumentException, pokud je element addressHeader null

|   |   |
|---|---|
|Podrobnosti|Počínaje rozhraním .NET Framework <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> 4.7.1, konstruktor vyvolá <xref:System.ArgumentException> if <code>null</code>jeden z prvků . V rozhraní .NET Framework 4.7 a starších verzích není vyvolána žádná výjimka.|
|Návrh|Pokud se setkáte s problémy s kompatibilitou s touto změnou v rozhraní .NET Framework 4.7.1 nebo novější verzi, můžete se od ní odhlásit přidáním následujícího řádku do <code>&lt;runtime&gt;</code> části souboru app.config::<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableAddressHeaderCollectionValidation=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7.1|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})></li></ul>|
