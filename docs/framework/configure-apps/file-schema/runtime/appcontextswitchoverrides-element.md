---
title: Prvek AppContextSwitchOverrides
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- AppContextSwitchOverrides
- compatibility switches
- configuration switches
- configuration
ms.assetid: 4ce07f47-7ddb-4d91-b067-501bd8b88752
ms.openlocfilehash: 8d5cd73bb9393533cb669581420e24297cb5ff71
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102928"
---
# <a name="appcontextswitchoverrides-element"></a>\<AppContextSwitchOverrides> prvek

Definuje jeden nebo více přepínačů používaných třídou <xref:System.AppContext> k poskytnutí mechanismu odhlášení pro nové funkce.

[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>za běhu**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<>AppContextSwitchOverrides**

## <a name="syntax"></a>Syntaxe

```xml
<AppContextSwitchOverrides value="name1=value1[[;name2=value2];...]" />
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`value`|Požadovaný atribut.<br /><br /> Definuje jeden nebo více názvů přepínačů a jejich přidružené logické hodnoty.|

### <a name="value-attribute"></a>atribut hodnoty

|Hodnota|Popis|
|-----------|-----------------|
|"name=value"|Předdefinovaný název přepínače spolu`true` s `false`jeho hodnotou ( nebo ). Více párů názvů/hodnot přepínačů je odděleno středníky (";"). Seznam předdefinovaných názvů přepínačů podporovaných rozhraním .NET Framework naleznete v části Poznámky.|

### <a name="child-elements"></a>Podřízené elementy
 Žádné.

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Popis|
|-------------|-----------------|
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|

## <a name="remarks"></a>Poznámky
 Počínaje rozhraním .NET Framework `<AppContextSwitchOverrides>` 4.6 umožňuje prvek v konfiguračním souboru volajícím rozhraní API určit, zda jejich aplikace může využívat nové funkce nebo zachovat kompatibilitu s předchozími verzemi knihovny. Například pokud chování rozhraní API se změnilo mezi dvěma `<AppContextSwitchOverrides>` verzemi knihovny, prvek umožňuje volajícím tohoto rozhraní API odhlásit nové chování na verze knihovny, které podporují nové funkce. Pro aplikace, které volají rozhraní API `<AppContextSwitchOverrides>` v rozhraní .NET Framework, prvek může také povolit volajícím, jejichž aplikace cílstarší verze rozhraní .NET Framework se přihlásit do nové funkce, pokud jejich aplikace běží na verzi rozhraní .NET Framework, který obsahuje tuto funkci.

 Atribut `value` `<AppContextSwitchOverrides>` prvku se skládá z jednoho řetězce, který se skládá z jednoho nebo více párů název/hodnota oddělený středníkem.  Každý název identifikuje přepínač kompatibility a jeho odpovídající`true` hodnota `false`je logická hodnota ( nebo ), která označuje, zda je přepínač nastaven. Ve výchozím nastavení `false`je přepínač a knihovny poskytují nové funkce. Poskytují pouze předchozí funkce, pokud je přepínač nastaven (to `true`znamená, že jeho hodnota je ). To umožňuje knihovnám poskytovat nové chování pro existující rozhraní API a současně umožňuje volajícím, kteří jsou závislí na předchozím chování, odhlásit se z nové funkce.

Rozhraní .NET Framework podporuje následující přepínače:

|Název přepínače|Popis|Zavedena|
|-----------------|-----------------|----------------|
|`Switch.MS.Internal.`<br/>`DoNotApplyLayoutRoundingToMarginsAndBorderThickness`|Určuje, zda program Windows Presentation Foundation používá starší verzi algoritmu pro rozložení ovládacího prvku. Další informace naleznete v [tématu Mitigation: WPF Layout](../../../migration-guide/mitigation-wpf-layout.md).|.NET Framework 4.6|
|`Switch.MS.Internal.`<br/>`UseSha1AsDefaultHashAlgorithmForDigitalSignatures`|Určuje, zda je výchozí algoritmus použitý pro podepisování částí balíčku správcem PackageDigitalSignatureManager SHA1 nebo SHA256.<br>Kvůli problémům s kolizí s SHA1, Microsoft doporučuje SHA256.|Rozhraní .NET 4.7.1|
|`Switch.System.Activities.`<br/>`UseMD5CryptoServiceProviderForWFDebugger`|Pokud je `false`nastavena na , umožňuje ladění projektů pracovních postupů založených na XAML pomocí sady Visual Studio, pokud je povolena FIPS. Bez něj <xref:System.NullReferenceException> je vyvolána volání metody v System.Activities sestavení.|Rozhraní .NET Framework 4.7|
|`Switch.System.Activities.`<br/>`UseMD5ForWFDebugger`|Určuje, zda kontrolní součet pro instanci pracovního postupu v ladicím programu používá MD5 nebo SHA1. | Rozhraní .NET Framework 4.7|
|`Switch.System.Activities.`<br/>`UseSHA1HashForDebuggerSymbols`|Určuje, zda hodnota hash kontrolního součtu pracovního postupu používá algoritmus`true`SHA1 zavedený jako výchozí v rozhraní .NET Framework 4.7 ( ),`false`nebo zda používá výchozí algoritmus SHA256 zavedený jako výchozí v rozhraní .NET Framework 4.8 ( ).<br>Kvůli problémům s kolizí s SHA1, Microsoft doporučuje SHA256.| .NET Framework 4.8|
|`Switch.System.Diagnostics.`<br/>`IgnorePortablePDBsInStackTraces`|Určuje, zda trasování zásobníku získat při použití přenosných PDB může obsahovat zdrojové informace o souboru a řádku. `false`zahrnout zdrojové informace o souboru a řádku; v `true`opačném případě .| .NET Framework 4.7.2|
|`Switch.System.Drawing.`<br/>`DontSupportPngFramesInIcons`|Určuje, <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> zda metoda vyvolá výjimku, když <xref:System.Drawing.Icon> má objekt rámce PNG. Další informace naleznete v [tématu Mitigation: PNG Frames in Icon Objects](../../../migration-guide/mitigation-png-frames-in-icon-objects.md).|.NET Framework 4.6|
|`Switch.System.Drawing.Text.`<br/>`DoNotRemoveGdiFontsResourcesFromFontCollection`|Určuje, <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> zda jsou objekty správně uvolněny <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType> při přidání do kolekce metodou. `true`zachovat starší chování; `false` chcete-li vyřadit všechny soukromé objekty písma. | .NET Framework 4.7.2|
|`Switch.System.Drawing.Printing.`<br>`OptimizePrintPreview`|Určuje, zda <xref:System.Windows.Forms.PrintPreviewDialog> je výkon optimalizován pro síťové tiskárny. Další informace naleznete v [tématu Přehled ovládacího prvku PrintPreviewDialog](../../../winforms/controls/printpreviewdialog-control-overview-windows-forms.md).|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceJapaneseEraYearRanges`|Určuje, zda jsou vynuceny kontroly rozsahu roku pro období japonského kalendáře. `true`vynucovat kontroly rozsahu roku a `false` zakázat je (výchozí chování). Další informace naleznete v [tématu Práce s kalendáři](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceLegacyJapaneseDateParsing`|Určuje, zda je v parsování rozpoznáno pouze "1" jako první rok japonského kalendářního období. `true`rozpoznat pouze "1"; `false` rozpoznat buď "1" nebo Gannen (výchozí chování). Další informace naleznete v [tématu Práce s kalendáři](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6|
|`Switch.System.Globalization.FormatJapaneseFirstYearAsANumber`|Určuje, zda je první rok japonského kalendářního období v operacích formátování reprezentován jako "1" nebo Gannen. `true`naformátovat první rok éry jako "1"; `false` naformátujte jej jako Gannen (výchozí chování). Další informace naleznete v [tématu Práce s kalendáři](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6|
|`Switch.System.Globalization.NoAsyncCurrentCulture`|Určuje, zda asynchronní operace netokují z kontextu volajícího vlákna. Další informace naleznete [v tématu CurrentCulture a CurrentUICulture toku mezi úkoly](../../../migration-guide/retargeting/4.5.2-4.6.md#currentculture-and-currentuiculture-flow-across-tasks).|.NET Framework 4.6|
|`Switch.System.IdentityModel.`<br/>`DisableMultipleDNSEntriesInSANCertificate`|Určuje, <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> zda se metoda pokusí porovnat typ deklarace pouze s poslední položkou DNS. Další informace naleznete [v tématu Mitigation: X509CertificateClaimSet.FindClaims Method](../../../migration-guide/mitigation-x509certificateclaimset-findclaims-method.md).|.NET Framework 4.6.1|
|`Switch.System.IdentityModel.`<br/>`EnableCachedEmptyDefaultAuthorizationContext`|Určuje, zda má být authorization AuthorizationContext.Empty to return a mutable object.|.NET Framework 4.6|
|`Switch.System.IO.BlockLongPaths`|Určuje, zda cesty `MAX_PATH` delší než (260 znaků) vyvolat <xref:System.IO.PathTooLongException>. Další informace naleznete v tématu [Podpora dlouhé cesty](../../../migration-guide/retargeting/4.6.1-4.6.2.md#long-path-support).|.NET Framework 4.6.2|
|`Switch.System.IO.Compression.`<br/>`DoNotUseNativeZipLibraryForDecompression`|Určuje, zda nativní rutiny operačního <xref:System.IO.Compression.DeflateStream> režimu se používají pro dekompresi třídou. `false`použití nativních api; `true` použití <xref:System.IO.Compression.DeflateStream> implementace.| .NET Framework 4.7.2|
|`Switch.System.IO.Compression.ZipFile.`<br/>`UseBackslash`|Používá zpětné lomítko ("\\") spíše než lomítko ("/") jako oddělovač cesty ve vlastnosti. <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> Další informace naleznete [v tématu Mitigation: ZipArchiveEntry.FullName Path Separator](../../../migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md).|.NET Framework 4.6.1|
|`Switch.System.IO.Ports.`<br/>`DoNotCatchSerialStreamThreadExceptions`|Určuje, zda výjimky operačního systému, které <xref:System.IO.Ports.SerialPort> jsou vyvolány na vláknech na pozadí vytvořených pomocí datových proudů, proces ukončí.|Rozhraní .NET 4.7.1|
|`Switch.System.IO.`<br/>`UseLegacyPathHandling`|Určuje, zda se používá normalizace starší cesty <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> a <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> cesty URI jsou podporovány metodami a. Další informace naleznete v [tématu Mitigation: Path Normalization](../../../migration-guide/mitigation-path-normalization.md) and [Mitigation: Path Colon Checks](../../../migration-guide/mitigation-path-colon-checks.md).|.NET Framework 4.6.2|
|`Switch.System.`<br/>`MemberDescriptorEqualsReturnsFalseIfEquivalent`|Určuje, zda test rovnosti <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=nameWithType> porovná vlastnost jednoho <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=nameWithType> objektu s vlastností druhého objektu. Další informace naleznete [v tématu Nesprávné implementace MemberDescriptor.Equals](../../../migration-guide/retargeting/4.6.1-4.6.2.md#incorrect-implementation-of-memberdescriptorequals).|.NET Framework 4.6.2|
 `Switch.System.Net.`<br/>`DontCheckCertificateEKUs`|Zakáže ověření identifikátoru objektu (EKU) rozšířeného použití klíče (EKU) certifikátu. Rozšířené využití klíče (EKU) rozšíření je kolekce identifikátorů objektů (ID), které označují aplikace, které používají klíč.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchSendAuxRecord`|Zakáže tls1.0 zneužití prohlížeče proti SSL/TLS (BEAST) zmírnění zakázáním použití SCH_SEND_AUX_RECORD.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchUseStrongCrypto`|Určuje, <xref:System.Net.ServicePointManager?displayProperty=nameWithType> zda <xref:System.Net.Security.SslStream?displayProperty=nameWithType> mohou třídy a používat protokol SSL 3.0. Další informace naleznete v [tématu Mitigation: TLS Protocols](../../../migration-guide/mitigation-tls-protocols.md).|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSystemDefaultTlsVersions`|Zakáže systemdefault TLS verze vrátit zpět na výchozí Tls12, Tls11, Tls.|Rozhraní .NET Framework 4.7|
|`Switch.System.Net.`<br/>`DontEnableTlsAlerts`|Zakáže výstrahy na straně serveru SslStream TLS.|Rozhraní .NET Framework 4.7|
|`Switch.System.Runtime.InteropServices.`<br/>`DoNotMarshalOutByrefSafeArrayOnInvoke`|Určuje, zda parametry ByRef SafeArray na interop`false`události COM zařazují zpět`true`do nativního kódu ( ) nebo zda je zakázáno zařazování zpět na nativní kód ( ).| .NET Framework 4.8|
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseECMAScriptV6EscapeControlCharacter` |Určuje, zda [DataContractJsonSerializer](xref:System.Runtime.Serialization.Json.DataContractJsonSerializer) serializuje některé řídicí znaky na základě standardů ECMAScript V6 a V8. Další informace naleznete v [tématu Mitigation: Serializace řídicích znaků pomocí dataContractJsonSerializer](../../../migration-guide/mitigation-serialization-control-characters.md)| Rozhraní .NET Framework 4.7 |
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseTimeZoneInfo`|Určuje, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> zda podporuje více úprav nebo pouze jednu úpravu pro časové pásmo. Pokud `true`používá <xref:System.TimeZoneInfo> typ serializovat a rekonstruovat data data data a času; v opačném případě <xref:System.TimeZone> používá typ, který nepodporuje více pravidel úprav.|.NET Framework 4.6.2|
|`Switch.System.Runtime.Serialization.UseNewMaxArraySize`|Určuje, <xref:System.Runtime.Serialization.ObjectManager?displayProperty=nameWithType> zda během serializace a deserializace objektu používá větší velikost pole. Nastavte tento `true` přepínač na zlepšení výkonu serializace a deserializace velkých objektů <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>grafů podle typů, jako je například . | .NET Framework 4.7.2|
|`Switch.System.Security.ClaimsIdentity.`<br/>`SetActorAsReferenceWhenCopyingClaimsIdentity`|Určuje, <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29> zda konstruktor nastaví <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=nameWithType> vlastnost nového objektu s existujícím odkazem na objekt. Další informace naleznete v [tématu Mitigation: ClaimsIdentity Constructor](../../../migration-guide/retargeting/4.6.1-4.6.2.md).|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`AesCryptoServiceProvider.DontCorrectlyResetDecryptor`|Určuje, zda pokus o <xref:System.Security.Cryptography.AesCryptoServiceProvider> opětovné použití dešifrovacího oru <xref:System.Security.Cryptography.CryptographicException>vyvolá soubor . Další informace naleznete v [tématu AesCryptoServiceProvider decryptor poskytuje opakovaně použitelnou transformaci](../../../migration-guide/retargeting/4.6.1-4.6.2.md#aescryptoserviceprovider-decryptor-provides-a-reusable-transform).|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`DoNotAddrOfCspParentWindowHandle`|Určuje, zda je hodnota vlastnosti [CspParameters.ParentWindowHandle](xref:System.Security.Cryptography.CspParameters.ParentWindowHandle) [IntPtr,](xref:System.IntPtr) která představuje umístění paměti popisovače okna, nebo zda se jedná o popisovač okna (HWND). Další informace naleznete [v tématu Mitigation: CspParameters.ParentWindowHandle Expects a HWND](../../../migration-guide/retargeting/4.6.2-4.7.md#cspparametersparentwindowhandle-now-expects-hwnd-value). |Rozhraní .NET Framework 4.7|
|`Switch.System.Security.Cryptography.`<br/>`UseLegacyFipsThrow`|Určuje, zda použití spravovaných kryptografických`true`tříd v režimu FIPS vyvolá`false` <xref:System.Security.Cryptography.CryptographicException> ( ) nebo spoléhá na implementaci systémových knihoven ( ).| .NET Framework 4.8|
|`Switch.System.Security.Cryptography.Pkcs.`<br/>`UseInsecureHashAlgorithms`|Určuje, zda je výchozí hodnota pro některé operace SignedCMS SHA1 nebo SHA256.<br>Kvůli problémům s kolizí s SHA1, Microsoft doporučuje SHA256.|Rozhraní .NET 4.7.1|
|`Switch.System.Security.Cryptography.X509Certificates.`<br/>`ECDsaCertificateExtensions.UseLegacyPublicKeyReader`|Určuje, <xref:System.Security.Cryptography.X509Certificates.ECDsaCertificateExtensions.GetECDsaPublicKey%2A?displayProperty=nameWithType> zda metoda správně zpracovává všechny pojmenované křivky`false`podporované operačním systémem ( ) nebo se vrátí ke staršímu chování.| .NET Framework 4.8|
|`Switch.System.Security.Cryptography.Xml.`<br/>`UseInsecureHashAlgorithms`|Určuje, zda je výchozí hodnota pro některé operace SignedXML SHA1 nebo SHA256.<br>Kvůli problémům s kolizí s SHA1, Microsoft doporučuje SHA256.|Rozhraní .NET 4.7.1|
|`Switch.System.ServiceModel.`<br/>`AllowUnsignedToHeader`|Určuje, `TransportWithMessageCredential` zda režim zabezpečení umožňuje zprávy s neznamítnou hlavičkou "to". Jedná se o opt-in přepínač. Další informace naleznete [v tématu Runtime Changes in the .NET Framework 4.6.1](../../../migration-guide/runtime/4.5.2-4.6.1.md#windows-communication-foundation-wcf).|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableAddressHeaderCollectionValidation`>|Určuje, <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> zda konstruktor <xref:System.ArgumentException> vyvolá if jeden `null`z prvků .|Rozhraní .NET 4.7.1|
|`Switch.System.ServiceModel.`<br />`DisableCngCertificates`|Určuje, zda pokus o použití certifikátů X509 s poskytovatelem úložiště klíčů CSG vyvolá výjimku. Další informace naleznete v tématu [WCF zabezpečení přenosu podporuje certifikáty uložené pomocí CNG](../../../migration-guide/retargeting/4.6.1-4.6.2.md#wcf-transport-security-supports-certificates-stored-using-cng).|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableExplicitConnectionCloseHeader`|Při použití přenosu HTTP s samoobslužnou `true` službou způsobí nastavení této `Connection: close` hodnoty na WCF ignorovat aplikaci, která přidává hlavičku do hlaviček odpovědí pro požadavek. Nastavení této `false` hodnoty umožňuje `Connection: close` přidání hlavičky do hlavičky odpovědi, což má za následek zavření soketu požadavku po odeslání odpovědi.|.NET Framework 4.6|
|`Switch.System.ServiceModel.`<br/>`DisableOperationContextAsyncFlow`|Zpracovává zablokování, které vyplývají z omezení instance služby opětovného účastníka na jedno vlákno provádění najednou.|.NET Framework 4.6.2|
|`Switch.System.ServiceModel.`<br/>`DisableUsingServicePointManagerSecurityProtocols`|Spolu `Switch.System.Net.DontEnableSchUseStrongCrypto`s , určuje, zda WCF zabezpečení zpráv používá TLS 1.1 a TLS 1.2.|Rozhraní .NET Framework 4.7 |
|`Switch.System.ServiceModel.`<br/>`DontEnableSystemDefaultTlsVersions`|Hodnota nastaví `false` výchozí konfiguraci, aby operační systém mohl zvolit protokol. Hodnota nastaví `true` výchozí hodnotu na nejvyšší dostupný protokol. (K dispozici také na servisní větvi předchozích verzí frameworku)|Rozhraní .NET 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InMsmqEncryptionAlgorithm`|Určuje, zda je výchozí algoritmus podepisování zpráv pro zprávy služby MSMQ ve wcf sha1 nebo SHA256.<br>Kvůli problémům s kolizí s SHA1, Microsoft doporučuje SHA256.|Rozhraní .NET 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InPipeConnectionGetHashAlgorithm`|Určuje, zda wcf používá SHA1 nebo SHA256 hash generovat náhodné názvy pro pojmenované kanály.<br>Kvůli problémům s kolizí s SHA1, Microsoft doporučuje SHA256.|Rozhraní .NET 4.7.1|
|`Switch.System.ServiceModel.Internals`<br/>`IncludeNullExceptionMessageInETWTrace`|Určuje, zda má být vyvolána [výjimka NullReferenceException,](xref:System.NullReferenceException) pokud je zpráva výjimky null.|Rozhraní .NET Framework 4.7|
|`Switch.System.ServiceProcess.`<br/>`DontThrowExceptionsOnStart`|Určuje, zda jsou výjimky vyzývané při <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> spuštění služby rozšířeny volajícímu metody.|Rozhraní .NET 4.7.1|
|`Switch.System.Threading.UseNetCoreTimer`|Určuje, <xref:System.Threading.Timer> zda instance využívají vylepšení výkonu pro prostředí s vysokým měřítkem. Pokud `true`jsou povolena vylepšení výkonu; pokud `false` (výchozí hodnota), jsou zakázány.| .NET Framework 4.8|
|`Switch.System.Uri.`<br/>`DontEnableStrictRFC3986ReservedCharacterSets`|Určuje, zda jsou některé znaky kódované procentem, které byly někdy dekódovány, nyní konzistentně zakódovány. Pokud `true`jsou dekódovány; v `false`opačném případě .| .NET Framework 4.7.2|
|`Switch.System.Uri.`<br/>`DontKeepUnicodeBidiFormattingCharacters`|Určuje zpracování obousměrných znaků Unicode v identifikátorech URI. `true`je zbavit identifikátorů URI; `false` zachovat a procentuální kódování.| .NET Framework 4.7.2|
|`Switch.System.Windows.Controls.Grid.`<br/>`StarDefinitionsCanExceedAvailableSpace` |Určuje, zda Windows Presentation Foundation použije`true`starý algoritmus`false`( ) nebo nový \*algoritmus ( ) při přidělování prostoru -columns. Další informace naleznete [v tématu Mitigation: Grid Control's Space Allocation to Star-columns](../../../migration-guide/retargeting/4.6.2-4.7.md#wpf-grid-allocation-of-space-to-star-columns). |Rozhraní .NET Framework 4.7 |
|`Switch.System.Windows.Controls.TabControl.`<br/>`SelectionPropertiesCanLagBehindSelectionChangedEvent`|Určuje, zda volič nebo ovládací prvek tabulátoru vždy aktualizuje hodnotu své vlastnosti vybrané hodnoty před vyvoláním události změněné výběru.|Rozhraní .NET 4.7.1|
|`Switch.System.Windows.Controls.Text.`<br/>`UseAdornerForTextboxSelectionRendering`|Určuje, zda je pro ovládací prvky <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.PasswordBox> ovládací prvky, které mají`false`zabránit zakončování textu ( ),`true`nebo zda je text vykreslen pouze ve vrstvě Adorner ( (| .NET Framework 4.7.2|
|`Switch.System.Windows.Data.Binding.`<br/>`IListIndexerHidesCustomIndexer`|Určuje, zda jsou vlastní indexery`true`IList`false`používány <xref:System.Windows.Data.Binding?displayProperty=nameWithType> třídou nesprávně ( ) nebo správně ( ).| .NET Framework 4.8|
|`Switch.System.Windows.DoNotScaleForDpiChanges`|Určuje, zda ke změnám DPI dochází na `false`základě systému (hodnota ) `true`nebo na monitor (hodnota ).|.NET Framework 4.6.2|
|`Switch.System.Windows.`<br/>`DoNotUsePresentationDpiCapabilityTier2OrGreater`|Určuje, zda jsou vylepšení velikosti ovládacích prvků v režimu <xref:System.Windows.Interop.HwndHost?displayProperty=nameWithType> WPF`true`spuštěna`false`v režimu podporující chod na monitoru zakázána ( ) nebo povolena ( ).| .NET Framework 4.8|
|`Switch.System.Windows.Forms.`<br/>`DomainUpDown.UseLegacyScrolling`|Určuje, zda vývojář potřebuje speciálně zpracovat akci, <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> když je přítomen text ovládacího prvku. `true`zvládnout <xref:System.Windows.Forms.DomainUpDown.UpButton> akci; `false` pro <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> akce <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> a správně synchronizované.| .NET Framework 4.7.2|
|`Switch.System.Windows.Forms.`<br />`DontSupportReentrantFilterMessage`|Odhlásí z kódu, který <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> umožňuje vlastní implementaci bezpečně filtrovat zprávy <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> bez vyvolání výjimky při volání metody. Další informace naleznete [v tématu Mitigation: Custom IMessageFilter.PreFilterMessageMessage Implementations](../../../migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).|.NET Framework 4.6.1|
|`Switch.System.Windows.Forms.`<br/>`UseLegacyContextMenuStripSourceControlValue`|Určuje, <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> zda vlastnost vrátí zdrojový prvek, když uživatel otevře <xref:System.Windows.Forms.ToolStripMenuItem> nabídku z vnořeného ovládacího prvku. `true`chcete-li vrátit `null`, dědictví chování; `false` pro návrat ovládacího prvku zdrojového kódu.| .NET Framework 4.7.2|
|`Switch.System.Windows.Forms.UseLegacyToolTipDisplay`|Určuje, zda je podpora vyvolání popisku zakázána (`true`) nebo povolena (`false`). Povolení podpory vyvolání popisku také vyžaduje `Switch.UseLegacyAccessibilityFeatures` `Switch.UseLegacyAccessibilityFeatures.2`starší `Switch.UseLegacyAccessibilityFeatures.3` funkce usnadnění definované `false`službou , a všechny funkce jsou zakázány (nastaveno na).| .NET Framework 4.8|
|`Switch.System.Windows.Input.Stylus.`<br/>`EnablePointerSupport`|Určuje, zda `WM_POINTER`je v aplikacích WPF povolen volitelný balíček dotykového ovládání a pera. Další informace naleznete [v tématu Mitigation: Pointer-based Touch and Stylus Support Další informace naleznete v tématu Mitigation: Pointer-based Touch and Stylus Support](../../../migration-guide/mitigation-pointer-based-touch-and-stylus-support.md)|Rozhraní .NET Framework 4.7|
|`Switch.System.Windows.Markup.`<br/>`DoNotUseSha256ForMarkupCompilerChecksumAlgorithm`|Určuje, zda je výchozí algoritmus hash použitý pro`false`kontrolní součty`true`SHA256 ( ) nebo SHA1 ( ).<br>Kvůli problémům s kolizí s SHA1, Microsoft doporučuje SHA256.| .NET Framework 4.7.2|
|`Switch.System.Windows.Media.ImageSourceConverter.`<br/>`OverrideExceptionWithNullReferenceException`|Určuje, zda je vyvolána starší [verze NullReferenceException](xref:System.NullReferenceException) namísto výjimky, která konkrétně označuje příčinu výjimky (například [DirectoryNotFoundException](xref:System.IO.DirectoryNotFoundException) nebo [FileNotFoundException](xref:System.IO.FileNotFoundException). Je určen pro použití kód, který závisí na zpracování [NullReferenceException](xref:System.NullReferenceException). | Rozhraní .NET Framework 4.7 |
|`Switch.System.Workflow.ComponentModel.`<br/>`UseLegacyHashForXomlFileChecksum`|Určuje, zda zařazování souborů XOML v sestaveních projektu`true`pracovního postupu používá algoritmus MD5 ( ) nebo zda používají algoritmus SHA256 zavedený jako výchozí v rozhraní .NET Framework 4.8.<br>Kvůli problémům s kolizí s MD5, Microsoft doporučuje SHA256.| .NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForSqlTrackingCacheKey`|Určuje, zda algoritmus hash kontrolního součtu službou`true`SqlTrackingService používá algoritmus MD5 ( ) pro řetězce uložené v mezipaměti nebo zda používá algoritmus SHA256 zavedený jako výchozí v rozhraní .NET Framework 4.8.<br>Kvůli problémům s kolizí s MD5, Microsoft doporučuje SHA256.| .NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForWorkflowDefinitionDispenserCacheKey`|Určuje, zda algoritmus hash kontrolního součtu pomocí`true`runtime pracovního postupu používá algoritmus MD5 ( ) pro definice pracovního postupu uložené v mezipaměti nebo zda používá algoritmus SHA256 zavedený jako výchozí v rozhraní .NET Framework 4.8.<br>Kvůli problémům s kolizí s MD5, Microsoft doporučuje SHA256.| .NET Framework 4.8|
|`Switch.UseLegacyAccessibilityFeatures`|Určuje, zda jsou dostupné funkce usnadnění počínaje rozhraním .NET Framework 4.7.1 povoleny nebo zakázány. | Rozhraní .NET 4.7.1 |
|`Switch.UseLegacyAccessibilityFeatures.2`|Určuje, zda jsou funkce usnadnění dostupné v rozhraní`false`.NET Framework`true`4.7.2 povoleny ( ) nebo zakázány ( ). If `true` `Switch.UseLegacyAccessibilityFeatures` , musí `true` být také povolit .NET Framework 4.7.1 funkce usnadnění.| .NET Framework 4.7.2|
|`Switch.UseLegacyAccessibilityFeatures.3`|Určuje, zda jsou funkce usnadnění zavedené v rozhraní`false`.NET`true`Framework 4.8 povoleny ( ) nebo zakázány ( ). Pokud `true` `Switch.UseLegacyAccessibilityFeatures` a `Switch.UseLegacyAccessibilityFeatures.2` musí `true`být také .| .NET Framework 4.8|
|`Switch.UseLegacyToolTipDisplay`|Určuje, zda se popisky zobrazí, když uživatel najede kurzorem myši na ovládací prvek WPF (`true`),`false`nebo zda jsou zobrazeny jak při fokusu klávesnice, tak pomocí klávesové zkratky ( , výchozí chování). U aplikací spuštěných v rozhraní .NET Framework 4.8, ale zaměřených na předchozí verze `Switch.UseLegacyAccessibilityFeatures` `Switch.UseLegacyAccessibilityFeatures.2`rozhraní `Switch.UseLegacyAccessibilityFeatures.3` .NET Framework, vyžaduje povolení fokusu klávesnice i podpory klávesových zkratek tuto možnost a všechny možnosti nastavení na `false`.| .NET Framework 4.8|
|`Switch.System.Xml.`<br />`IgnoreEmptyKeySequences`|Určuje, zda jsou prázdné sekvence kláves ve složených klíčích ověřováním schématu XSD ignorovány. Další informace naleznete v [tématu Mitigation: XML Schema Validation](../../../migration-guide/mitigation-xml-schema-validation.md).|.NET Framework 4.6|

> [!NOTE]
> Namísto přidání `AppContextSwitchOverrides` prvku do konfiguračního souboru aplikace můžete také `static` nastavit přepínače `Shared` programově voláním <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> metody (v jazyce C#) nebo (v jazyce Visual Basic).

 Vývojáři knihovny mohou také definovat vlastní přepínače, které volajícím umožňují odhlásit se ze změněných funkcí zavedených v novějších verzích jejich knihoven. Další informace naleznete <xref:System.AppContext> ve třídě.

## <a name="switches-in-aspnet-apps"></a>Přepínače v ASP.NET aplikacích

Aplikaci ASP.NET můžete nakonfigurovat tak, [ \<](../appsettings/add-element-for-appsettings.md) aby používala nastavení kompatibility přidáním prvku Add>do části [ \<applicationSettings>](../appsettings/index.md) souboru web.config.

Následující příklad používá `<add>` prvek k přidání `<appSettings>` dvou nastavení do oddílu souboru web.config:

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="example"></a>Příklad

 Následující příklad používá `AppContextSwitchOverrides` prvek k definování jednoho `Switch.System.Globalization.NoAsyncCurrentCulture`přepínače kompatibility aplikace , který zabraňuje jazykové verzi toku přes vlákna v volání asynchronní metody.

```xml
<configuration>
   <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />
   </runtime>
</configuration>
```

 Následující příklad používá `AppContextSwitchOverrides` prvek k definování dvou `Switch.System.Globalization.NoAsyncCurrentCulture` `Switch.System.IO.BlockLongPaths`přepínačů kompatibility aplikací a . Středník odděluje dva dvojice název/hodnota.

```xml
<configuration>
    <runtime>
       <AppContextSwitchOverrides
          value="Switch.System.Globalization.NoAsyncCurrentCulture=true;Switch.System.IO.BlockLongPaths=true" />
    </runtime>
</configuration>
```

## <a name="see-also"></a>Viz také

- [Zmírnění nových chování v rozhraní .NET Framework 4.6 a novějších](../../../migration-guide/mitigations.md)
- <xref:System.AppContext?displayProperty=nameWithType>
- [\<> element za běhu](runtime-element.md)
- [\<konfigurace> Element](../configuration-element.md)
