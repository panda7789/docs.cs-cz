---
ms.openlocfilehash: 9ec5fa379556dedeaa7a35e34f004340ab47a39c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234368"
---
### <a name="calling-createdefaultauthorizationcontext-with-a-null-argument-has-changed"></a>Volání CreateDefaultAuthorizationContext s argumentem null se změnil

|   |   |
|---|---|
|Podrobnosti|Provádění <xref:System.IdentityModel.Policy.AuthorizationContext?displayProperty=name> vrácený voláním <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=name> s hodnotou null authorizationPolicies argument změnila jeho implementace v rozhraní .NET Framework 4.6.|
|Doporučení|Ve výjimečných případech může aplikace WCF, které používají vlastní ověřování najdete v článku behaviorální rozdíly. V takových případech lze obnovit předchozí chování v některém ze dvou způsobů:<ol><li>Znovu kompilovat aplikace pro cílení na dřívější verzi rozhraní .NET Framework než 4.6. Služby hostované v IIS, použijte &lt;httpRuntime targetFramework =&quot;x.x&quot;  / &gt; – element pro cílení na dřívější verzi rozhraní .NET Framework.</li><li>Přidejte následující řádek, který <code>&lt;appSettings&gt;</code> části souboru app.config: <code>&lt;add key=&quot;appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext&quot; value=&quot;true&quot; /&gt;</code></li></ol>|
|Rozsah|Vedlejší|
|Version|4.6|
|Type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=nameWithType></li></ul>|
