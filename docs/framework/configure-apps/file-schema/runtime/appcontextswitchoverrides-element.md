---
title: Element AppContextSwitchOverrides
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- AppContextSwitchOverrides
- compatibility switches
- configuration switches
- configuration
ms.assetid: 4ce07f47-7ddb-4d91-b067-501bd8b88752
ms.openlocfilehash: 8d5cd73bb9393533cb669581420e24297cb5ff71
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "82102928"
---
# <a name="appcontextswitchoverrides-element"></a>\<AppContextSwitchOverrides> – element

Definuje jeden nebo více přepínačů používaných <xref:System.AppContext> třídou k poskytnutí mechanismu odhlášení pro nové funkce.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<AppContextSwitchOverrides>**

## <a name="syntax"></a>Syntaxe

```xml
<AppContextSwitchOverrides value="name1=value1[[;name2=value2];...]" />
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`value`|Požadovaný atribut.<br /><br /> Definuje jeden nebo více názvů přepínačů a jejich přidružených logických hodnot.|

### <a name="value-attribute"></a>Value – atribut

|Hodnota|Description|
|-----------|-----------------|
|"název = hodnota"|Předdefinovaný název přepínače spolu s jeho hodnotou ( `true` nebo `false` ). Dvojice název/hodnota více přepínačů jsou odděleny středníky (";"). Seznam předdefinovaných názvů přepínačů podporovaných .NET Framework naleznete v části poznámky.|

### <a name="child-elements"></a>Podřízené elementy
 Žádné

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Description|
|-------------|-----------------|
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|

## <a name="remarks"></a>Poznámky
 Počínaje .NET Framework 4,6 `<AppContextSwitchOverrides>` prvek v konfiguračním souboru umožňuje volajícím rozhraní API zjistit, jestli jejich aplikace může využívat nové funkce nebo zachovat kompatibilitu s předchozími verzemi knihovny. Například pokud se chování rozhraní API změnilo mezi dvěma verzemi knihovny, `<AppContextSwitchOverrides>` element umožňuje volajícím tohoto rozhraní API odhlásit se z nového chování ve verzích knihovny, které podporují nové funkce. Pro aplikace, které volají rozhraní API v .NET Framework, `<AppContextSwitchOverrides>` může element také povolit volajícím, jejichž aplikace cílí na starší verzi .NET Framework, aby se přihlásily k novým funkcím, pokud je jejich aplikace spuštěná ve verzi .NET Framework, která obsahuje tyto funkce.

 `value`Atribut `<AppContextSwitchOverrides>` elementu se skládá z jednoho řetězce, který se skládá z jedné nebo více párů název/hodnota oddělených středníkem.  Každý název identifikuje přepínač kompatibility a jeho odpovídající hodnota je logická hodnota ( `true` nebo `false` ), která označuje, zda je přepínač nastaven. Ve výchozím nastavení je přepínač `false` a knihovny poskytují nové funkce. Poskytují jenom předchozí funkce, pokud je nastavený přepínač (to znamená, že jeho hodnota je `true` ). Díky tomu mohou knihovny poskytovat nové chování pro existující rozhraní API a současně umožnit volajícím, kteří závisejí na předchozím chování a odhlásit se z nových funkcí.

.NET Framework podporuje následující přepínače:

|Název přepínače|Description|Vedou|
|-----------------|-----------------|----------------|
|`Switch.MS.Internal.`<br/>`DoNotApplyLayoutRoundingToMarginsAndBorderThickness`|Určuje, zda Windows Presentation Foundation používá starší algoritmus pro rozložení ovládacích prvků. Další informace najdete v tématu [zmírnění rizika: rozložení WPF](../../../migration-guide/mitigation-wpf-layout.md).|.NET Framework 4.6|
|`Switch.MS.Internal.`<br/>`UseSha1AsDefaultHashAlgorithmForDigitalSignatures`|Určuje, zda výchozí algoritmus použitý k podepisování částí balíčku pomocí PackageDigitalSignatureManager je SHA1 nebo SHA256.<br>Microsoft doporučuje SHA256 z důvodu kolizí problémů se SHA1.|.NET Framework 4.7.1|
|`Switch.System.Activities.`<br/>`UseMD5CryptoServiceProviderForWFDebugger`|Když je nastaveno na `false` , umožňuje ladění projektů pracovních postupů založených na jazyce XAML se sadou Visual Studio, pokud je povolený Standard FIPS. Bez této akce <xref:System.NullReferenceException> je vyvolána v volání metod v sestavení System. Activities.|.NET Framework 4,7|
|`Switch.System.Activities.`<br/>`UseMD5ForWFDebugger`|Určuje, zda kontrolní součet pro instanci pracovního postupu v ladicím programu používá algoritmus MD5 nebo SHA1. | .NET Framework 4,7|
|`Switch.System.Activities.`<br/>`UseSHA1HashForDebuggerSymbols`|Určuje, jestli se hash Checksum kontrolního součtu používá algoritmus SHA1, který je zavedený jako výchozí v .NET Framework 4,7 ( `true` ), nebo jestli používá výchozí SHA256 algoritmus, který jste zavedli jako výchozí v .NET Framework 4,8 ( `false` ).<br>Microsoft doporučuje SHA256 z důvodu kolizí problémů se SHA1.| .NET Framework 4.8|
|`Switch.System.Diagnostics.`<br/>`IgnorePortablePDBsInStackTraces`|Určuje, zda trasování zásobníku při použití přenosného soubory PDB může obsahovat zdrojový soubor a informace o řádku. `false`Chcete-li zahrnout zdrojový soubor a informace o řádku; v opačném případě `true` .| .NET Framework 4.7.2|
|`Switch.System.Drawing.`<br/>`DontSupportPngFramesInIcons`|Určuje, zda <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda vyvolá výjimku <xref:System.Drawing.Icon> , pokud má objekt snímky PNG. Další informace naleznete v tématu [zmírňující rizika: snímky PNG v objektech ikon](../../../migration-guide/mitigation-png-frames-in-icon-objects.md).|.NET Framework 4.6|
|`Switch.System.Drawing.Text.`<br/>`DoNotRemoveGdiFontsResourcesFromFontCollection`|Určuje, zda <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> jsou objekty po přidání do kolekce správně uvolněny <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType> metodou. `true`Chcete-li zachovat starší verze chování; `false`k Dispose všech soukromých objektů písma. | .NET Framework 4.7.2|
|`Switch.System.Drawing.Printing.`<br>`OptimizePrintPreview`|Určuje, zda je výkon aplikace <xref:System.Windows.Forms.PrintPreviewDialog> optimalizován pro síťové tiskárny. Další informace najdete v tématu [Přehled ovládacího prvku PrintPreviewDialog –](../../../winforms/controls/printpreviewdialog-control-overview-windows-forms.md).|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceJapaneseEraYearRanges`|Určuje, jestli jsou vynutily kontroly rozsahu roků pro mazání v japonském kalendáři. `true`k vykonání kontrol rozsahu roku a `false` jejich zakázání (výchozí chování). Další informace najdete v tématu [práce s kalendáři](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceLegacyJapaneseDateParsing`|Určuje, zda je jako první rok japonského období v rámci operace analýzy rozpoznán pouze "1". `true`rozpoznání pouze "1"; `false`pro rozpoznání "1" nebo Gannen (výchozí chování). Další informace najdete v tématu [práce s kalendáři](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6|
|`Switch.System.Globalization.FormatJapaneseFirstYearAsANumber`|Určuje, zda je první rok japonského období v japonštině reprezentován jako "1" nebo Gannen při formátování operací. `true`Pokud chcete naformátovat první rok období posouzení jako "1"; `false`naformátujte ho jako Gannen (výchozí chování). Další informace najdete v tématu [práce s kalendáři](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6|
|`Switch.System.Globalization.NoAsyncCurrentCulture`|Určuje, zda asynchronní operace netokůují z kontextu volajícího vlákna. Další informace najdete v tématu [tok CurrentCulture a CurrentUICulture napříč úkoly](../../../migration-guide/retargeting/4.5.2-4.6.md#currentculture-and-currentuiculture-flow-across-tasks).|.NET Framework 4.6|
|`Switch.System.IdentityModel.`<br/>`DisableMultipleDNSEntriesInSANCertificate`|Určuje, zda se <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> Metoda pokusí porovnat typ deklarace identity pouze s poslední položkou DNS. Další informace naleznete v tématu [zmírňing: X509CertificateClaimSet. FindClaims metoda](../../../migration-guide/mitigation-x509certificateclaimset-findclaims-method.md).|.NET Framework 4.6.1|
|`Switch.System.IdentityModel.`<br/>`EnableCachedEmptyDefaultAuthorizationContext`|Určuje, zda má být povolen AuthorizationContext. Empty, aby vracel proměnlivý objekt.|.NET Framework 4.6|
|`Switch.System.IO.BlockLongPaths`|Určuje, zda cesty delší než `MAX_PATH` (260 znaků) vyvolávají výjimku <xref:System.IO.PathTooLongException> . Další informace najdete v tématu [podpora dlouhých cest](../../../migration-guide/retargeting/4.6.1-4.6.2.md#long-path-support).|.NET Framework 4.6.2|
|`Switch.System.IO.Compression.`<br/>`DoNotUseNativeZipLibraryForDecompression`|Určuje, zda jsou pro dekompresi třídou použity nativní rutiny operačního systému <xref:System.IO.Compression.DeflateStream> . `false`použití nativních rozhraní API; `true`pro použití <xref:System.IO.Compression.DeflateStream> implementace.| .NET Framework 4.7.2|
|`Switch.System.IO.Compression.ZipFile.`<br/>`UseBackslash`|Používá zpětné lomítko (" \\ ") místo lomítka ("/") jako oddělovač cest ve <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> Vlastnosti. Další informace naleznete v tématu [zmírnění rizika: ZipArchiveEntry. FullName Path oddělovače](../../../migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md).|.NET Framework 4.6.1|
|`Switch.System.IO.Ports.`<br/>`DoNotCatchSerialStreamThreadExceptions`|Určuje, zda výjimky operačního systému, které jsou vyvolány v vláknech na pozadí vytvořených pomocí <xref:System.IO.Ports.SerialPort> datových proudů, ukončí proces.|.NET Framework 4.7.1|
|`Switch.System.IO.`<br/>`UseLegacyPathHandling`|Určuje, zda se používá normalizace cesty starší verze a že metody a podporují cesty URI <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> . Další informace najdete v tématu [zmírnění rizika: normalizace cest](../../../migration-guide/mitigation-path-normalization.md) a [zmírnění rizik: kontroly cest – dvojtečky](../../../migration-guide/mitigation-path-colon-checks.md).|.NET Framework 4.6.2|
|`Switch.System.`<br/>`MemberDescriptorEqualsReturnsFalseIfEquivalent`|Určuje, zda test rovnosti porovnává <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=nameWithType> vlastnost jednoho objektu s <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=nameWithType> vlastností druhého objektu. Další informace najdete v tématu [nesprávná implementace MemberDescriptor. Equals](../../../migration-guide/retargeting/4.6.1-4.6.2.md#incorrect-implementation-of-memberdescriptorequals).|.NET Framework 4.6.2|
 `Switch.System.Net.`<br/>`DontCheckCertificateEKUs`|Zakáže ověřování identifikátoru objektu (OID) pro rozšířené použití klíče certifikátu (EKU). Rozšíření rozšířené použití klíče (EKU) je kolekce identifikátorů objektů (OID), které označují aplikace, které klíč používají.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchSendAuxRecord`|Zakáže využívání SCH_SEND_AUX_RECORD v prohlížeči TLS 1.0 proti zmírnění zabezpečení SSL/TLS (TOUCHDOWN).|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchUseStrongCrypto`|Určuje, jestli <xref:System.Net.ServicePointManager?displayProperty=nameWithType> <xref:System.Net.Security.SslStream?displayProperty=nameWithType> třídy a můžou používat protokol SSL 3,0. Další informace najdete v tématu [zmírnění rizik: protokoly TLS](../../../migration-guide/mitigation-tls-protocols.md).|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSystemDefaultTlsVersions`|Zakáže SystemDefault verze TLS a vrátí se zpět na výchozí hodnotu Tls12, Tls11, TLS.|.NET Framework 4,7|
|`Switch.System.Net.`<br/>`DontEnableTlsAlerts`|Zakáže výstrahy SslStream TLS na straně serveru.|.NET Framework 4,7|
|`Switch.System.Runtime.InteropServices.`<br/>`DoNotMarshalOutByrefSafeArrayOnInvoke`|Určuje, zda parametry typu ByRef SafeArray na událostech zprostředkovatele komunikace s objekty COM zařazovat zpět do nativního kódu ( `false` ) nebo zda je zařazování zpět do nativního kódu zakázáno ( `true` ).| .NET Framework 4.8|
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseECMAScriptV6EscapeControlCharacter` |Určuje, zda [DataContractJsonSerializer](xref:System.Runtime.Serialization.Json.DataContractJsonSerializer) serializovat některé řídicí znaky v závislosti na standardech rozhraní ECMAScript V6 a V8. Další informace naleznete v tématu [zmírnění rizika: serializace řídicích znaků pomocí DataContractJsonSerializer](../../../migration-guide/mitigation-serialization-control-characters.md)| .NET Framework 4,7 |
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseTimeZoneInfo`|Určuje, zda <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> podporuje více úprav nebo pouze jednu úpravu pro časové pásmo. Pokud `true` , používá <xref:System.TimeZoneInfo> typ k serializaci a deserializaci dat data a času; v opačném případě používá <xref:System.TimeZone> typ, který nepodporuje více pravidel úprav.|.NET Framework 4.6.2|
|`Switch.System.Runtime.Serialization.UseNewMaxArraySize`|Určuje, zda <xref:System.Runtime.Serialization.ObjectManager?displayProperty=nameWithType> Při serializaci objektu a deserializaci používá větší velikost pole. Nastavte tento přepínač na `true` , chcete-li zlepšit výkon serializace a deserializace rozsáhlých grafů objektů podle typů, jako je například <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> . | .NET Framework 4.7.2|
|`Switch.System.Security.ClaimsIdentity.`<br/>`SetActorAsReferenceWhenCopyingClaimsIdentity`|Určuje, zda <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29> konstruktor nastaví vlastnost nového objektu na <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=nameWithType> stávající odkaz na objekt. Další informace naleznete v tématu [zmírňující rizika: konstruktor hodnota ClaimsIdentity](../../../migration-guide/retargeting/4.6.1-4.6.2.md).|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`AesCryptoServiceProvider.DontCorrectlyResetDecryptor`|Určuje, zda pokus o opakované použití <xref:System.Security.Cryptography.AesCryptoServiceProvider> dešifry vyvolá <xref:System.Security.Cryptography.CryptographicException> . Další informace najdete v tématu [dešifrovací modul AesCryptoServiceProvider, který poskytuje opakovaně použitelnou transformaci](../../../migration-guide/retargeting/4.6.1-4.6.2.md#aescryptoserviceprovider-decryptor-provides-a-reusable-transform).|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`DoNotAddrOfCspParentWindowHandle`|Určuje, zda je hodnota vlastnosti [CspParameters. ParentWindowHandle](xref:System.Security.Cryptography.CspParameters.ParentWindowHandle) typu [IntPtr](xref:System.IntPtr) , která představuje umístění paměti popisovače okna nebo zda se jedná o popisovač okna (HWND). Další informace najdete v tématu [zmírnění rizika: CspParameters. ParentWindowHandle očekává HWND](../../../migration-guide/retargeting/4.6.2-4.7.md#cspparametersparentwindowhandle-now-expects-hwnd-value). |.NET Framework 4,7|
|`Switch.System.Security.Cryptography.`<br/>`UseLegacyFipsThrow`|Určuje, zda použití spravovaných kryptografických tříd v režimu FIPS vyvolá <xref:System.Security.Cryptography.CryptographicException> ( `true` ) nebo spoléhá na implementaci systémových knihoven ( `false` ).| .NET Framework 4.8|
|`Switch.System.Security.Cryptography.Pkcs.`<br/>`UseInsecureHashAlgorithms`|Určuje, zda je výchozí hodnota pro některé operace SignedCMS nastaveno na hodnotu SHA1 nebo SHA256.<br>Microsoft doporučuje SHA256 z důvodu kolizí problémů se SHA1.|.NET Framework 4.7.1|
|`Switch.System.Security.Cryptography.X509Certificates.`<br/>`ECDsaCertificateExtensions.UseLegacyPublicKeyReader`|Určuje, zda <xref:System.Security.Cryptography.X509Certificates.ECDsaCertificateExtensions.GetECDsaPublicKey%2A?displayProperty=nameWithType> metoda správně zpracovává všechny pojmenované křivky podporované operačním systémem ( `false` ) nebo se vrátí k původnímu chování.| .NET Framework 4.8|
|`Switch.System.Security.Cryptography.Xml.`<br/>`UseInsecureHashAlgorithms`|Určuje, zda je výchozí hodnota pro některé operace SignedXML nastaveno na hodnotu SHA1 nebo SHA256.<br>Microsoft doporučuje SHA256 z důvodu kolizí problémů se SHA1.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`AllowUnsignedToHeader`|Určuje, zda `TransportWithMessageCredential` režim zabezpečení umožňuje zprávy s nepodepsaným záhlavím "do". Toto je přepínač pro výslovný souhlas. Další informace najdete v tématu [změny za běhu v .NET Framework 4.6.1](../../../migration-guide/runtime/4.5.2-4.6.1.md#windows-communication-foundation-wcf).|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableAddressHeaderCollectionValidation`>|Určuje, zda <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> konstruktor vyvolá výjimku <xref:System.ArgumentException> , je-li jeden z prvků `null` .|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br />`DisableCngCertificates`|Určuje, zda pokus o použití certifikátů x509 s poskytovatelem úložiště klíčů CSG vyvolá výjimku. Další informace najdete v tématu [zabezpečení přenosu WCF podporuje certifikáty uložené pomocí CNG](../../../migration-guide/retargeting/4.6.1-4.6.2.md#wcf-transport-security-supports-certificates-stored-using-cng).|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableExplicitConnectionCloseHeader`|Při použití přenosu protokolu HTTP u samoobslužné služby se při nastavení této hodnoty způsobí, `true` že služba WCF ignoruje aplikaci přidáním `Connection: close` hlavičky do hlaviček odpovědi pro požadavek. Pokud tuto hodnotu nastavíte `false` , umožníte přidat `Connection: close` hlavičku do hlaviček odpovědí, což vede k zavření soketu požadavku po odeslání odpovědi.|.NET Framework 4.6|
|`Switch.System.ServiceModel.`<br/>`DisableOperationContextAsyncFlow`|Zpracovává zablokování, které je výsledkem omezení instancí služby znovu zavedené na jedno vlákno spuštění v jednom okamžiku.|.NET Framework 4.6.2|
|`Switch.System.ServiceModel.`<br/>`DisableUsingServicePointManagerSecurityProtocols`|Společně s nástrojem `Switch.System.Net.DontEnableSchUseStrongCrypto` Určuje, zda zabezpečení zpráv WCF používá tls 1,1 a tls 1,2.|.NET Framework 4,7 |
|`Switch.System.ServiceModel.`<br/>`DontEnableSystemDefaultTlsVersions`|Hodnota `false` Nastaví výchozí konfiguraci tak, aby operační systém mohl zvolit protokol. Hodnota `true` Nastaví výchozí hodnotu na nejvyšší dostupný protokol. (K dispozici také na branách pro obsluhu předchozích verzí rozhraní)|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InMsmqEncryptionAlgorithm`|Určuje, zda je výchozí algoritmus podepisování zprávy pro zprávy služby MSMQ ve službě WCF SHA1 nebo SHA256.<br>Microsoft doporučuje SHA256 z důvodu kolizí problémů se SHA1.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InPipeConnectionGetHashAlgorithm`|Určuje, zda WCF používá algoritmus SHA1 nebo SHA256 hash pro generování náhodných názvů pro pojmenované kanály.<br>Microsoft doporučuje SHA256 z důvodu kolizí problémů se SHA1.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.Internals`<br/>`IncludeNullExceptionMessageInETWTrace`|Určuje, zda má být vyvolána výjimka [NullReferenceException](xref:System.NullReferenceException) , pokud je zpráva výjimky null.|.NET Framework 4,7|
|`Switch.System.ServiceProcess.`<br/>`DontThrowExceptionsOnStart`|Určuje, zda jsou výjimky vyvolané při spuštění služby šířeny volajícímu <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> metody.|.NET Framework 4.7.1|
|`Switch.System.Threading.UseNetCoreTimer`|Určuje, jestli <xref:System.Threading.Timer> instance využívají vylepšení výkonu pro vysoce škálovatelná prostředí. `true`V případě, že jsou povolena vylepšení výkonu, pokud `false` (výchozí hodnota), jsou zakázána.| .NET Framework 4.8|
|`Switch.System.Uri.`<br/>`DontEnableStrictRFC3986ReservedCharacterSets`|Určuje, zda jsou aktuálně dekódované znaky s kódováním%, které byly někdy dekódované, nyní konzistentně zakódovány. Pokud `true` jsou Dekódovatelné, v opačném případě `false` .| .NET Framework 4.7.2|
|`Switch.System.Uri.`<br/>`DontKeepUnicodeBidiFormattingCharacters`|Určuje zpracování obousměrných znaků Unicode v identifikátorech URI. `true`Pokud je chcete odstranit z identifikátorů URI; `false`pro zachování a procenta jejich kódování.| .NET Framework 4.7.2|
|`Switch.System.Windows.Controls.Grid.`<br/>`StarDefinitionsCanExceedAvailableSpace` |Určuje, zda Windows Presentation Foundation použije starý algoritmus ( `true` ) nebo nový algoritmus ( `false` ) při přidělování prostoru do \* sloupců. Další informace najdete v tématu [zmírňující rizika: přidělování prostoru ovládacího prvku mřížky do hvězdiček-Columns](../../../migration-guide/retargeting/4.6.2-4.7.md#wpf-grid-allocation-of-space-to-star-columns). |.NET Framework 4,7 |
|`Switch.System.Windows.Controls.TabControl.`<br/>`SelectionPropertiesCanLagBehindSelectionChangedEvent`|Určuje, zda ovládací prvek selektor nebo karta vždy aktualizuje hodnotu vlastnosti vybrané hodnoty před vyvoláním události změny výběru.|.NET Framework 4.7.1|
|`Switch.System.Windows.Controls.Text.`<br/>`UseAdornerForTextboxSelectionRendering`|Určuje, zda není pro ovládací prvky a k dispozici vykreslování výběru založené na doplňku <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.PasswordBox> , aby se zabránilo zastíněna textu ( `false` ), nebo zda je text vykreslen pouze ve vrstvě doplňku ( `true` ).| .NET Framework 4.7.2|
|`Switch.System.Windows.Data.Binding.`<br/>`IListIndexerHidesCustomIndexer`|Určuje, zda jsou vlastní indexery IList používány nesprávně ( `true` ) nebo správně ( `false` ) <xref:System.Windows.Data.Binding?displayProperty=nameWithType> třídou.| .NET Framework 4.8|
|`Switch.System.Windows.DoNotScaleForDpiChanges`|Určuje, zda ke změnám DPI dojde v závislosti na systému (hodnota `false` ) nebo na monitorování (hodnota `true` ).|.NET Framework 4.6.2|
|`Switch.System.Windows.`<br/>`DoNotUsePresentationDpiCapabilityTier2OrGreater`|Určuje, zda jsou vylepšení velikosti ovládacích prvků v <xref:System.Windows.Interop.HwndHost?displayProperty=nameWithType> nástroji při spuštění WPF v režimu podporujícím monitorování zakázána ( `true` ) nebo povolena ( `false` ).| .NET Framework 4.8|
|`Switch.System.Windows.Forms.`<br/>`DomainUpDown.UseLegacyScrolling`|Určuje, zda vývojář potřebuje při <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> zobrazení textu ovládacího prvku speciálně zpracovat akci. `true`pro zpracování <xref:System.Windows.Forms.DomainUpDown.UpButton> akce, aby byly `false` <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> akce a <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> správně synchronizovány.| .NET Framework 4.7.2|
|`Switch.System.Windows.Forms.`<br />`DontSupportReentrantFilterMessage`|Výslovný z kódu, který umožňuje vlastní <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementaci bezpečně filtrovat zprávy bez vyvolání výjimky při <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> volání metody. Další informace naleznete v tématu [zmírňující rizika: Custom IMessageFilter. PreFilterMessage Implements](../../../migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).|.NET Framework 4.6.1|
|`Switch.System.Windows.Forms.`<br/>`UseLegacyContextMenuStripSourceControlValue`|Určuje, zda <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> vlastnost vrací ovládací prvek zdroje, když uživatel otevře nabídku z vnořeného <xref:System.Windows.Forms.ToolStripMenuItem> ovládacího prvku. `true`Chcete-li vrátit `null` , starší chování; `false` pro vrácení správy zdrojového kódu.| .NET Framework 4.7.2|
|`Switch.System.Windows.Forms.UseLegacyToolTipDisplay`|Určuje, jestli je podpora volání tlačítek zakázaná ( `true` ) nebo povolená ( `false` ). Povolení podpory volání popisů tlačítek vyžaduje taky starší funkce usnadnění, které definuje `Switch.UseLegacyAccessibilityFeatures` , `Switch.UseLegacyAccessibilityFeatures.2` a `Switch.UseLegacyAccessibilityFeatures.3` všechny jsou zakázané (nastavené na `false` ).| .NET Framework 4.8|
|`Switch.System.Windows.Input.Stylus.`<br/>`EnablePointerSupport`|Určuje, zda `WM_POINTER` je v aplikacích WPF povolena volitelná dotyková nebo stylusová sada. Další informace najdete v tématu [zmírnění rizika: dotykové ovládání s ukazateli a Podpora stylusu.](../../../migration-guide/mitigation-pointer-based-touch-and-stylus-support.md)|.NET Framework 4,7|
|`Switch.System.Windows.Markup.`<br/>`DoNotUseSha256ForMarkupCompilerChecksumAlgorithm`|Určuje, zda je výchozí algoritmus hash používaný pro kontrolní součty SHA256 ( `false` ) nebo SHA1 ( `true` ).<br>Microsoft doporučuje SHA256 z důvodu kolizí problémů se SHA1.| .NET Framework 4.7.2|
|`Switch.System.Windows.Media.ImageSourceConverter.`<br/>`OverrideExceptionWithNullReferenceException`|Určuje, zda je vyvolána starší verze [NullReferenceException](xref:System.NullReferenceException) namísto výjimky, která přesněji označuje příčinu výjimky (například [DirectoryNotFoundException](xref:System.IO.DirectoryNotFoundException) nebo [FileNotFoundException](xref:System.IO.FileNotFoundException). Je určena pro použití kódem, který závisí na zpracování [NullReferenceException](xref:System.NullReferenceException). | .NET Framework 4,7 |
|`Switch.System.Workflow.ComponentModel.`<br/>`UseLegacyHashForXomlFileChecksum`|Určuje, zda je hodnota hash kontrolního součtu souborů XOML v sestaveních projektů pracovních postupů používána pomocí algoritmu MD5 ( `true` ) nebo zda používá SHA256 algoritmus představený jako výchozí v .NET Framework 4,8.<br>Microsoft doporučuje SHA256 z důvodu kolizí problémů s MD5.| .NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForSqlTrackingCacheKey`|Určuje, jestli má hashování kontrolního součtu SqlTrackingService používat algoritmus MD5 ( `true` ) pro řetězce uložené v mezipaměti, nebo jestli používá SHA256 algoritmus, který jste zavedli jako výchozí v .NET Framework 4,8.<br>Microsoft doporučuje SHA256 z důvodu kolizí problémů s MD5.| .NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForWorkflowDefinitionDispenserCacheKey`|Určuje, jestli má hashový součet pomocí modulu runtime workflowu používat algoritmus MD5 ( `true` ) pro definice pracovních postupů uložených v mezipaměti, nebo jestli používá SHA256 algoritmus, který jste zavedli jako výchozí v .NET Framework 4,8.<br>Microsoft doporučuje SHA256 z důvodu kolizí problémů s MD5.| .NET Framework 4.8|
|`Switch.UseLegacyAccessibilityFeatures`|Určuje, jestli jsou funkce usnadnění dostupné od .NET Framework 4.7.1 povolené nebo zakázané. | .NET Framework 4.7.1 |
|`Switch.UseLegacyAccessibilityFeatures.2`|Určuje, jestli jsou funkce usnadnění dostupné v .NET Framework 4.7.2 povolené ( `false` ) nebo Disabled ( `true` ). Pokud `true` je `Switch.UseLegacyAccessibilityFeatures` potřeba, musí být také `true` umožněna možnost .NET Framework 4.7.1 funkce usnadnění.| .NET Framework 4.7.2|
|`Switch.UseLegacyAccessibilityFeatures.3`|Určuje, jestli jsou funkce usnadnění zavedené v .NET Framework 4,8 povolené ( `false` ) nebo zakázané ( `true` ). Pokud `true` `Switch.UseLegacyAccessibilityFeatures` a `Switch.UseLegacyAccessibilityFeatures.2` musí být také `true` .| .NET Framework 4.8|
|`Switch.UseLegacyToolTipDisplay`|Určuje, zda se mají zobrazit popisy tlačítek, když uživatel najede myší na ovládací prvek WPF ( `true` ), nebo zda je zobrazen na ovládacím panelu klávesnice a prostřednictvím klávesy klávesových zkratek ( `false` , výchozí chování). U aplikací, které běží na .NET Framework 4,8, ale cílících na předchozí verze .NET Framework musíte povolit podporu fokusu klávesnice a klávesových zkratek, `Switch.UseLegacyAccessibilityFeatures` `Switch.UseLegacyAccessibilityFeatures.2` a `Switch.UseLegacyAccessibilityFeatures.3` to všechny nastavit na `false` .| .NET Framework 4.8|
|`Switch.System.Xml.`<br />`IgnoreEmptyKeySequences`|Určuje, zda jsou prázdné posloupnosti klíčů ve složených klíčích ignorovány ověřováním schématu XSD. Další informace najdete v tématu [zmírnění rizika: ověřování schématu XML](../../../migration-guide/mitigation-xml-schema-validation.md).|.NET Framework 4.6|

> [!NOTE]
> Místo přidávání `AppContextSwitchOverrides` elementu do konfiguračního souboru aplikace lze také nastavit přepínače programově voláním `static` metody (v jazyce C#) nebo `Shared` (v Visual Basic) <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> .

 Vývojáři knihovny mohou také definovat vlastní přepínače, aby mohli volající odhlásit ze změněných funkcí zavedených v novějších verzích jejich knihoven. Další informace naleznete v tématu <xref:System.AppContext> Třída.

## <a name="switches-in-aspnet-apps"></a>Přepínače v aplikacích ASP.NET

ASP.NET aplikaci můžete nakonfigurovat tak, aby používala nastavení kompatibility přidáním [\<Add>](../appsettings/add-element-for-appsettings.md) elementu do [\<appSettings>](../appsettings/index.md) oddílu souboru Web. config.

Následující příklad používá `<add>` element pro přidání dvou nastavení do `<appSettings>` oddílu souboru Web. config:

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="example"></a>Příklad

 Následující příklad používá `AppContextSwitchOverrides` element k definování jednoho přepínače kompatibility aplikace, `Switch.System.Globalization.NoAsyncCurrentCulture` který brání jazykové verzi v toku mezi vlákny v volání asynchronní metody.

```xml
<configuration>
   <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />
   </runtime>
</configuration>
```

 Následující příklad používá `AppContextSwitchOverrides` element k definování dvou přepínačů kompatibility aplikace `Switch.System.Globalization.NoAsyncCurrentCulture` a `Switch.System.IO.BlockLongPaths` . Dva páry název/hodnota jsou odděleny středníkem.

```xml
<configuration>
    <runtime>
       <AppContextSwitchOverrides
          value="Switch.System.Globalization.NoAsyncCurrentCulture=true;Switch.System.IO.BlockLongPaths=true" />
    </runtime>
</configuration>
```

## <a name="see-also"></a>Viz také

- [Zmírnění nového chování v .NET Framework 4,6 a novějším](../../../migration-guide/mitigations.md)
- <xref:System.AppContext?displayProperty=nameWithType>
- [\<runtime>Objekt](runtime-element.md)
- [\<configuration>Objekt](../configuration-element.md)
