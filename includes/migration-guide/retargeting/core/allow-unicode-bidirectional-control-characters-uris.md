---
ms.openlocfilehash: 3e9a1009167d8a765bc401d64a574bd123736ccd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61639399"
---
### <a name="allow-unicode-bidirectional-control-characters-in-uris"></a>Povolit řídicí znaky Unicode obousměrné v identifikátorech URI

|   |   |
|---|---|
|Podrobnosti|Určuje kódování Unicode několik speciální řídicí znaky, které určuje orientaci textu. V předchozích verzích rozhraní .NET Framework tyto znaky se nesprávně chyběly všechny identifikátory URI i v případě, že byly k dispozici v jejich procentuálně zakódovaný formuláře. Aby bylo možné lépe postupujte podle [RFC 3987](https://tools.ietf.org/html/rfc3987), umožňujeme teď tyto znaky v identifikátorech URI. Pokud najít nekódovaných v identifikátoru URI, jsou procentuálně zakódovaný. Pokud najít procentuálně zakódovaný jsou ponechané jako-je.|
|Doporučení|U aplikací s cílovou verzí rozhraní .NET Framework počínaje 4.7.2 Podpora kódování Unicode obousměrné znaky ve výchozím nastavení zapnutá. Pokud tuto změnu nežádoucí, můžete jej zakázat přidáním následujícího kódu [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) přepněte <code>&lt;runtime&gt;</code> oddílu konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Pro aplikace, které jsou cíleny na starší verze rozhraní .NET Framework, ale jsou spuštěny v rozhraní .NET Framework 4.7.2 počínaje verzí podpora je ve výchozím nastavení zakázané obousměrné znaky kódování Unicode. Můžete ji povolit tak, že přidáte následující [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) přepněte <code>&lt;runtime&gt;</code> oddílu konfiguračního souboru aplikace::<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7.2|
|Type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|
