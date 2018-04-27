### <a name="calling-createdefaultauthorizationcontext-with-a-null-argument-has-changed"></a>Volání metody CreateDefaultAuthorizationContext s argumentem null se změnila.

|   |   |
|---|---|
|Podrobnosti|Implementace <xref:System.IdentityModel.Policy.AuthorizationContext?displayProperty=name> vrácený volání <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=name> s hodnotou null authorizationPolicies argument změnil jeho implementace v rozhraní .NET Framework 4.6.|
|Návrh|Ve výjimečných případech může aplikace WCF, které používají vlastní ověřování najdete v části chování rozdíly. V takových případech lze obnovit předchozí chování v některém ze dvou způsobů:<ol><li>Znovu zkompiluje své aplikace a cílení na dřívější verzi rozhraní .NET Framework než 4.6. Pro služby hostované službou IIS, použijte &lt;httpRuntime targetFramework =&quot;verze&quot;  / &gt; element pro cílení na dřívější verzi rozhraní .NET Framework.</li><li>Přidejte následující řádek na <code>&lt;appSettings&gt;</code> části souboru app.config: <code>&lt;add key=&quot;appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext&quot; value=&quot;true&quot; /&gt;</code></li></ol>|
|Rozsah|Vedlejší|
|Version|4.6|
|Typ|Změna orientace|
|Ovlivněné rozhraní API|<ul><li><xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=nameWithType></li></ul>|

