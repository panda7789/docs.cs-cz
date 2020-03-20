---
ms.openlocfilehash: 9ec5fa379556dedeaa7a35e34f004340ab47a39c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804425"
---
### <a name="calling-createdefaultauthorizationcontext-with-a-null-argument-has-changed"></a>Volání CreateDefaultAuthorizationContext s nulovým argumentem bylo změněno.

|   |   |
|---|---|
|Podrobnosti|Implementace <xref:System.IdentityModel.Policy.AuthorizationContext?displayProperty=name> vrácené volání <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=name> s null authorizationPolicies argument změnil jeho implementaci v rozhraní .NET Framework 4.6.|
|Návrh|Ve výjimečných případech wcf aplikace, které používají vlastní ověřování může zobrazit rozdíly v chování. V takových případech lze předchozí chování obnovit dvěma způsoby:<ol><li>Překompilujte aplikaci tak, aby cílila na starší verzi rozhraní .NET Framework než 4.6. Pro služby hostované službou &lt;IIS použijte&quot;element httpRuntime targetFramework= x.x&quot;  / &gt; k cílení na starší verzi rozhraní .NET Framework.</li><li>Do části souboru <code>&lt;appSettings&gt;</code> app.config přidejte následující řádek:<code>&lt;add key=&quot;appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext&quot; value=&quot;true&quot; /&gt;</code></li></ol>|
|Rozsah|Vedlejší|
|Version|4.6|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=nameWithType></li></ul>|
