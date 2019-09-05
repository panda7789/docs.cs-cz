---
title: Element <AppContextSwitchOverrides>
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- AppContextSwitchOverrides
- compatibility switches
- configuration switches
- configuration
ms.assetid: 4ce07f47-7ddb-4d91-b067-501bd8b88752
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7fe354a929aad93ba4d4a6ea3cb43b2607be1f05
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252874"
---
# <a name="appcontextswitchoverrides-element"></a>\<AppContextSwitchOverrides – element >
Definuje jeden nebo více přepínačů používaných <xref:System.AppContext> třídou k poskytnutí mechanismu odhlášení pro nové funkce.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> modulu runtime**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<AppContextSwitchOverrides>**  
  
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
  
|Value|Popis|  
|-----------|-----------------|  
|"název = hodnota"|Předdefinovaný název přepínače spolu s jeho hodnotou (`true` nebo `false`). Dvojice název/hodnota více přepínačů jsou odděleny středníky (";"). Seznam předdefinovaných názvů přepínačů podporovaných .NET Framework naleznete v části poznámky.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 Počínaje .NET Framework 4,6 `<AppContextSwitchOverrides>` prvek v konfiguračním souboru umožňuje volajícím rozhraní API zjistit, jestli jejich aplikace může využívat nové funkce nebo zachovat kompatibilitu s předchozími verzemi knihovny. Například pokud se chování rozhraní API změnilo mezi dvěma verzemi knihovny, `<AppContextSwitchOverrides>` element umožňuje volajícím tohoto rozhraní API odhlásit se z nového chování ve verzích knihovny, které podporují nové funkce. Pro aplikace, které volají rozhraní API v .NET Framework, `<AppContextSwitchOverrides>` může element taky povolit volajícím, jejichž aplikace cílí na starší verzi .NET Framework, aby se přihlásily k novým funkcím, pokud je jejich aplikace spuštěná na verzi .NET Framework, která obsahuje. možnost.  
  
 `value` Atribut`<AppContextSwitchOverrides>` elementu se skládá z jednoho řetězce, který se skládá z jedné nebo více párů název/hodnota oddělených středníkem.  Každý název identifikuje přepínač kompatibility a jeho odpovídající hodnota je logická hodnota (`true` nebo `false`), která označuje, zda je přepínač nastaven. Ve výchozím nastavení je `false`přepínač a knihovny poskytují nové funkce. Poskytují jenom předchozí funkce, pokud je nastavený přepínač (to znamená, že jeho hodnota je `true`). Díky tomu mohou knihovny poskytovat nové chování pro existující rozhraní API a současně umožnit volajícím, kteří závisejí na předchozím chování a odhlásit se z nových funkcí.  
  
 .NET Framework podporuje následující přepínače:  
  
|Název přepínače|Popis|Vedou|  
|-----------------|-----------------|----------------|  
|`Switch.MS.Internal.`<br/>`DoNotApplyLayoutRoundingToMarginsAndBorderThickness`|Určuje, zda Windows Presentation Foundation používá starší algoritmus pro rozložení ovládacích prvků. Další informace najdete v tématu [zmírnění rizika: Rozložení](../../../migration-guide/mitigation-wpf-layout.md)WPF|.NET Framework 4.6|  
|`Switch.MS.Internal.`<br/>`UseSha1AsDefaultHashAlgorithmForDigitalSignatures`|Určuje, zda výchozí algoritmus použitý k podepisování částí balíčku pomocí PackageDigitalSignatureManager je SHA1 nebo SHA256.<br>Microsoft doporučuje SHA256 z důvodu kolizí problémů se SHA1.|.NET Framework 4.7.1|
|`Switch.System.Activities.`<br/>`UseMD5CryptoServiceProviderForWFDebugger`|Když je nastaveno `false`na, umožňuje ladění projektů pracovních postupů založených na jazyce XAML se sadou Visual Studio, pokud je povolený Standard FIPS. Bez této <xref:System.NullReferenceException> akce je vyvolána v volání metod v sestavení System. Activities.|Rozhraní .NET framework 4.7|
|`Switch.System.Activities.`<br/>`UseMD5ForWFDebugger`|Určuje, zda kontrolní součet pro instanci pracovního postupu v ladicím programu používá algoritmus MD5 nebo SHA1. | Rozhraní .NET framework 4.7|
|`Switch.System.Activities.`<br/>`UseSHA1HashForDebuggerSymbols`|Určuje, jestli se hash Checksum kontrolního součtu používá algoritmus SHA1, který je zavedený jako výchozí v .NET Framework 4,7 (`true`), nebo jestli používá výchozí SHA256 algoritmus, který jste zavedli jako výchozí v .NET Framework 4,8 (`false`).<br>Microsoft doporučuje SHA256 z důvodu kolizí problémů se SHA1.|.NET Framework 4,8|
|`Switch.System.Diagnostics.`<br/>`IgnorePortablePDBsInStackTraces`|Určuje, zda trasování zásobníku při použití přenosného soubory PDB může obsahovat zdrojový soubor a informace o řádku. `false`Chcete-li zahrnout zdrojový soubor a informace o řádku; v opačném případě. `true`|.NET Framework 4.7.2|
|`Switch.System.Drawing.`<br/>`DontSupportPngFramesInIcons`|Určuje, zda <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda vyvolá výjimku, <xref:System.Drawing.Icon> Pokud má objekt snímky PNG. Další informace najdete v tématu [zmírnění rizika: Snímky PNG v objektech](../../../migration-guide/mitigation-png-frames-in-icon-objects.md)ikon|.NET Framework 4.6|
|`Switch.System.Drawing.Text.`<br/>`DoNotRemoveGdiFontsResourcesFromFontCollection`|Určuje, <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> zda jsou objekty po přidání do kolekce <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType> správně uvolněny metodou. `true`Chcete-li zachovat starší verze chování; `false` k Dispose všech soukromých objektů písma. |.NET Framework 4.7.2|
|`Switch.System.Drawing.Printing.`<br>`OptimizePrintPreview`|Určuje, zda <xref:System.Windows.Forms.PrintPreviewDialog> je výkon aplikace optimalizován pro síťové tiskárny. Další informace najdete v tématu [Přehled ovládacího prvku PrintPreviewDialog –](../../../winforms/controls/printpreviewdialog-control-overview-windows-forms.md).|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceJapaneseEraYearRanges`|Určuje, jestli jsou vynutily kontroly rozsahu roků pro mazání v japonském kalendáři. `true`k vykonání kontrol rozsahu roku `false` a jejich zakázání (výchozí chování). Další informace najdete v tématu [práce s kalendáři](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceLegacyJapaneseDateParsing`|Určuje, zda je jako první rok japonského období v rámci operace analýzy rozpoznán pouze "1". `true`rozpoznání pouze "1"; `false` pro rozpoznání "1" nebo Gannen (výchozí chování). Další informace najdete v tématu [práce s kalendáři](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6| 
|`Switch.System.Globalization.FormatJapaneseFirstYearAsANumber`|Určuje, zda je první rok japonského období v japonštině reprezentován jako "1" nebo Gannen při formátování operací. `true`Pokud chcete naformátovat první rok období posouzení jako "1"; `false` naformátujte ho jako Gannen (výchozí chování). Další informace najdete v tématu [práce s kalendáři](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6|
|`Switch.System.Globalization.NoAsyncCurrentCulture`|Určuje, zda asynchronní operace netokůují z kontextu volajícího vlákna. Další informace najdete v tématu [tok CurrentCulture a CurrentUICulture napříč úkoly](../../../migration-guide/retargeting/4.5.2-4.6.md#currentculture-and-currentuiculture-flow-across-tasks).|.NET Framework 4.6|  
|`Switch.System.IdentityModel.`<br/>`DisableMultipleDNSEntriesInSANCertificate`|Určuje, zda <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> se metoda pokusí porovnat typ deklarace identity pouze s poslední položkou DNS. Další informace najdete v tématu [zmírnění rizika: X509CertificateClaimSet. FindClaims –](../../../migration-guide/mitigation-x509certificateclaimset-findclaims-method.md)metoda|.NET Framework 4.6.1|  
|`Switch.System.IdentityModel.`<br/>`EnableCachedEmptyDefaultAuthorizationContext`|Určuje, zda má být povolen AuthorizationContext. Empty, aby vracel proměnlivý objekt.|.NET Framework 4.6|  
|`Switch.System.IO.BlockLongPaths`|Určuje, zda cesty delší `MAX_PATH` než (260 znaků) <xref:System.IO.PathTooLongException>vyvolávají výjimku. Další informace najdete v tématu [podpora dlouhých cest](../../../migration-guide/retargeting/4.6.1-4.6.2.md#long-path-support).|.NET Framework 4.6.2|  
|`Switch.System.IO.Compression.`<br/>`DoNotUseNativeZipLibraryForDecompression`|Určuje, zda jsou pro dekompresi <xref:System.IO.Compression.DeflateStream> třídou použity nativní rutiny operačního systému. `false`použití nativních rozhraní API; `true` pro<xref:System.IO.Compression.DeflateStream> použití implementace.|.NET Framework 4.7.2|
|`Switch.System.IO.Compression.ZipFile.`<br/>`UseBackslash`|Používá zpětné lomítko (\\"") místo lomítka ("/") jako oddělovač cest <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> ve vlastnosti. Další informace najdete v tématu [zmírnění rizika: Oddělovač](../../../migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md)cesty ZipArchiveEntry. FullName.|.NET Framework 4.6.1|  
|`Switch.System.IO.Ports.`<br/>`DoNotCatchSerialStreamThreadExceptions`|Určuje, zda výjimky operačního systému, které jsou vyvolány v <xref:System.IO.Ports.SerialPort> vláknech na pozadí vytvořených pomocí datových proudů, ukončí proces.|.NET Framework 4.7.1| 
|`Switch.System.IO.`<br/>`UseLegacyPathHandling`|Určuje, zda se používá normalizace cesty starší verze a že <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> metody a <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> podporují cesty URI. Další informace najdete v tématu [zmírnění rizika: Normalizace](../../../migration-guide/mitigation-path-normalization.md) a [zmírnění cesty: Kontroluje](../../../migration-guide/mitigation-path-colon-checks.md)dvojtečku cesty.|.NET Framework 4.6.2|
|`Switch.System.`<br/>`MemberDescriptorEqualsReturnsFalseIfEquivalent`|Určuje, zda test rovnosti porovnává <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=nameWithType> vlastnost jednoho objektu <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=nameWithType> s vlastností druhého objektu. Další informace najdete v tématu [nesprávná implementace MemberDescriptor. Equals](../../../migration-guide/retargeting/4.6.1-4.6.2.md#incorrect-implementation-of-memberdescriptorequals).|.NET Framework 4.6.2|  
 `Switch.System.Net.`<br/>`DontCheckCertificateEKUs`|Zakáže ověřování identifikátoru objektu (OID) pro rozšířené použití klíče certifikátu (EKU). Rozšíření rozšířené použití klíče (EKU) je kolekce identifikátorů objektů (OID), které označují aplikace, které klíč používají.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchSendAuxRecord`|Zakáže využívání SCH_SEND_AUX_RECORD v prohlížeči TLS 1.0 proti riziku SSL/TLS (TOUCHDOWN).|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchUseStrongCrypto`|Určuje, jestli <xref:System.Net.ServicePointManager?displayProperty=nameWithType> třídy <xref:System.Net.Security.SslStream?displayProperty=nameWithType> a můžou používat protokol SSL 3,0. Další informace najdete v tématu [zmírnění rizika: Protokoly](../../../migration-guide/mitigation-tls-protocols.md)TLS.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSystemDefaultTlsVersions`|Zakáže SystemDefault verze TLS a vrátí se zpět na výchozí hodnotu Tls12, Tls11, TLS.|Rozhraní .NET framework 4.7|
|`Switch.System.Net.`<br/>`DontEnableTlsAlerts`|Zakáže výstrahy SslStream TLS na straně serveru.|Rozhraní .NET framework 4.7|
|`Switch.System.Runtime.InteropServices.`<br/>`DoNotMarshalOutByrefSafeArrayOnInvoke`|Určuje, zda parametry typu ByRef SAFEARRAY na událostech zprostředkovatele komunikace s objekty COM`false`zařazovat zpět do nativního kódu () nebo zda je`true`zařazování zpět do nativního kódu zakázáno ().|.NET Framework 4,8|
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseECMAScriptV6EscapeControlCharacter` |Určuje, zda [DataContractJsonSerializer](xref:System.Runtime.Serialization.Json.DataContractJsonSerializer) serializovat některé řídicí znaky v závislosti na standardech rozhraní ECMAScript V6 a V8. Další informace najdete v tématu [zmírnění rizika: Serializace řídicích znaků pomocí DataContractJsonSerializer](../../../migration-guide/mitigation-serialization-control-characters.md)| Rozhraní .NET framework 4.7 |
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseTimeZoneInfo`|Určuje, zda <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> podporuje více úprav nebo pouze jednu úpravu pro časové pásmo. Pokud `true`, <xref:System.TimeZone> používá typ k serializaci a deserializaci dat data a času; v opačném případě používá typ, který nepodporuje více pravidel úprav. <xref:System.TimeZoneInfo>|.NET Framework 4.6.2|
|`Switch.System.Runtime.Serialization.UseNewMaxArraySize`|Určuje, <xref:System.Runtime.Serialization.ObjectManager?displayProperty=nameWithType> zda při serializaci objektu a deserializaci používá větší velikost pole. Nastavte tento přepínač na `true` , chcete-li zlepšit výkon serializace a deserializace rozsáhlých grafů objektů podle typů <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, jako je například. |.NET Framework 4.7.2|
|`Switch.System.Security.ClaimsIdentity.`<br/>`SetActorAsReferenceWhenCopyingClaimsIdentity`|Určuje, zda <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=nameWithType> konstruktor nastaví <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=nameWithType> vlastnost nového objektu na stávající odkaz na objekt. Další informace najdete v tématu [zmírnění rizika: Konstruktor](../../../migration-guide/mitigation-claimsidentity-constructor.md)hodnota ClaimsIdentity|.NET Framework 4.6.2|  
|`Switch.System.Security.Cryptography.`<br/>`AesCryptoServiceProvider.DontCorrectlyResetDecryptor`|Určuje, zda pokus o opakované použití <xref:System.Security.Cryptography.AesCryptoServiceProvider> dešifry <xref:System.Security.Cryptography.CryptographicException>vyvolá. Další informace najdete v tématu [dešifrovací modul AesCryptoServiceProvider, který poskytuje opakovaně použitelnou transformaci](../../../migration-guide/retargeting/4.6.1-4.6.2.md#aescryptoserviceprovider-decryptor-provides-a-reusable-transform).|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`DoNotAddrOfCspParentWindowHandle`|Určuje, zda je hodnota vlastnosti [CspParameters. ParentWindowHandle](xref:System.Security.Cryptography.CspParameters.ParentWindowHandle) typu [IntPtr](xref:System.IntPtr) , která představuje umístění paměti popisovače okna nebo zda se jedná o popisovač okna (HWND). Další informace najdete v tématu [zmírnění rizika: CspParameters. ParentWindowHandle očekává HWND](../../../migration-guide/retargeting/4.6.2-4.7.md#cspparametersparentwindowhandle-now-expects-hwnd-value). |Rozhraní .NET framework 4.7|   
|`Switch.System.Security.Cryptography.`<br/>`UseLegacyFipsThrow`|Určuje, zda použití spravovaných kryptografických tříd v režimu FIPS vyvolá <xref:System.Security.Cryptography.CryptographicException> (`true`) nebo spoléhá na implementaci systémových knihoven (`false`).|.NET Framework 4,8|
|`Switch.System.Security.Cryptography.Pkcs.`<br/>`UseInsecureHashAlgorithms`|Určuje, zda je výchozí hodnota pro některé operace SignedCMS nastaveno na hodnotu SHA1 nebo SHA256.<br>Microsoft doporučuje SHA256 z důvodu kolizí problémů se SHA1.|.NET Framework 4.7.1|
|`Switch.System.Security.Cryptography.X509Certificates.`<br/>`ECDsaCertificateExtensions.UseLegacyPublicKeyReader`|Určuje, zda <xref:System.Security.Cryptography.X509Certificates.ECDsaCertificateExtensions.GetECDsaPublicKey%2A?displayProperty=nameWithType> metoda správně zpracovává všechny pojmenované křivky podporované operačním systémem (`false`) nebo se vrátí k původnímu chování.|.NET Framework 4,8|
|`Switch.System.Security.Cryptography.Xml.`<br/>`UseInsecureHashAlgorithms`|Určuje, zda je výchozí hodnota pro některé operace SignedXML nastaveno na hodnotu SHA1 nebo SHA256.<br>Microsoft doporučuje SHA256 z důvodu kolizí problémů se SHA1.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`AllowUnsignedToHeader`|Určuje, zda `TransportWithMessageCredential` režim zabezpečení umožňuje zprávy s nepodepsaným záhlavím "do". Toto je přepínač pro výslovný souhlas. Další informace najdete v tématu [změny za běhu v .NET Framework 4.6.1](../../../migration-guide/runtime/4.5.2-4.6.1.md#windows-communication-foundation-wcf).|.NET Framework 4.6.1| 
|`Switch.System.ServiceModel.`<br/>`DisableAddressHeaderCollectionValidation`>|Určuje, zda <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> konstruktor vyvolá výjimku <xref:System.ArgumentException> , je `null`-li jeden z prvků.|.NET Framework 4.7.1| 
|`Switch.System.ServiceModel.`<br />`DisableCngCertificates`|Určuje, zda pokus o použití certifikátů x509 s poskytovatelem úložiště klíčů CSG vyvolá výjimku. Další informace najdete v tématu [zabezpečení přenosu WCF podporuje certifikáty uložené pomocí CNG](../../../migration-guide/retargeting/4.6.1-4.6.2.md#wcf-transport-security-supports-certificates-stored-using-cng).|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableExplicitConnectionCloseHeader`|Při použití přenosu protokolu HTTP u samoobslužné služby se při nastavení této hodnoty způsobí, `true` že služba WCF ignoruje aplikaci `Connection: close` přidáním hlavičky do hlaviček odpovědi pro požadavek. Pokud tuto hodnotu `false` nastavíte, umožníte `Connection: close` přidat hlavičku do hlaviček odpovědí, což vede k zavření soketu požadavku po odeslání odpovědi.|.NET Framework 4.6|
|`Switch.System.ServiceModel.`<br/>`DisableOperationContextAsyncFlow`|Zpracovává zablokování, které je výsledkem omezení instancí předané služby na jediné vlákno spuštění v jednom okamžiku.|.NET Framework 4.6.2|
|`Switch.System.ServiceModel.`<br/>`DisableUsingServicePointManagerSecurityProtocols`|Společně s `Switch.System.Net.DontEnableSchUseStrongCrypto`nástrojem určuje, zda zabezpečení zpráv WCF používá TLS 1,1 a TLS 1,2.|Rozhraní .NET framework 4.7 |    
|`Switch.System.ServiceModel.`<br/>`DontEnableSystemDefaultTlsVersions`|Hodnota `false` nastaví výchozí konfiguraci tak, aby operační systém mohl zvolit protokol. Hodnota `true` nastaví výchozí hodnotu na nejvyšší dostupný protokol. (K dispozici také na branách pro obsluhu předchozích verzí rozhraní)|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InMsmqEncryptionAlgorithm`|Určuje, zda je výchozí algoritmus podepisování zprávy pro zprávy služby MSMQ ve službě WCF SHA1 nebo SHA256.<br>Microsoft doporučuje SHA256 z důvodu kolizí problémů se SHA1.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InPipeConnectionGetHashAlgorithm`|Určuje, zda WCF používá algoritmus SHA1 nebo SHA256 hash pro generování náhodných názvů pro pojmenované kanály.<br>Microsoft doporučuje SHA256 z důvodu kolizí problémů se SHA1.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.Internals`<br/>`IncludeNullExceptionMessageInETWTrace`|Určuje, zda má být vyvolána výjimka [NullReferenceException](xref:System.NullReferenceException) , pokud je zpráva výjimky null.|Rozhraní .NET framework 4.7|  
|`Switch.System.ServiceProcess.`<br/>`DontThrowExceptionsOnStart`|Určuje, zda jsou výjimky vyvolané při spuštění služby šířeny volajícímu <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> metody.|.NET Framework 4.7.1|
|`Switch.System.Threading.UseNetCoreTimer`|Určuje, <xref:System.Threading.Timer> jestli instance využívají vylepšení výkonu pro vysoce škálovatelná prostředí. V `true`případě, že jsou povolena vylepšení výkonu, `false` Pokud (výchozí hodnota), jsou zakázána.|.NET Framework 4,8|
|`Switch.System.Uri.`<br/>`DontEnableStrictRFC3986ReservedCharacterSets`|Určuje, zda jsou aktuálně dekódované znaky s kódováním%, které byly někdy dekódované, nyní konzistentně zakódovány. Pokud `true`jsou Dekódovatelné, `false`v opačném případě.|.NET Framework 4.7.2|
|`Switch.System.Uri.`<br/>`DontKeepUnicodeBidiFormattingCharacters`|Určuje zpracování obousměrných znaků Unicode v identifikátorech URI. `true`Pokud je chcete odstranit z identifikátorů URI; `false` pro zachování a procenta jejich kódování.|.NET Framework 4.7.2|
|`Switch.System.Windows.Controls.Grid.`<br/>`StarDefinitionsCanExceedAvailableSpace` |Určuje, zda Windows Presentation Foundation použije starý algoritmus (`true`) nebo nový algoritmus (`false`) při přidělování prostoru do \*sloupců. Další informace najdete v tématu [zmírnění rizika: Přidělování prostoru ovládacího prvku mřížky pro sloupce](../../../migration-guide/retargeting/4.6.2-4.7.md#wpf-grid-allocation-of-space-to-star-columns)hvězdiček |Rozhraní .NET framework 4.7 |
|`Switch.System.Windows.Controls.TabControl.`<br/>`SelectionPropertiesCanLagBehindSelectionChangedEvent`|Určuje, zda ovládací prvek selektor nebo karta vždy aktualizuje hodnotu vlastnosti vybrané hodnoty před vyvoláním události změny výběru.|.NET Framework 4.7.1|
|`Switch.System.Windows.Controls.Text.`<br/>`UseAdornerForTextboxSelectionRendering`|Určuje, zda je k dispozici vykreslení nevizuálního výběru založeného na doplňku pro <xref:System.Windows.Controls.TextBox> ovládací prvky`false`a <xref:System.Windows.Controls.PasswordBox> , aby se zabránilo zastíněna textu (), nebo zda je`true`text vykreslen pouze ve vrstvě doplňku ().|.NET Framework 4.7.2|
|`Switch.System.Windows.Data.Binding.`<br/>`IListIndexerHidesCustomIndexer`|Určuje, zda jsou vlastní indexery IList používány nesprávně`false`() nebo správně`true`() <xref:System.Windows.Data.Binding?displayProperty=nameWithType> třídou.|.NET Framework 4,8|
|`Switch.System.Windows.DoNotScaleForDpiChanges`|Určuje, zda ke změnám dpi dojde v závislosti na systému (hodnota `false`) nebo na monitorování ( `true`hodnota).|.NET Framework 4.6.2|
|`Switch.System.Windows.`<br/>`DoNotUsePresentationDpiCapabilityTier2OrGreater`|Určuje, zda jsou vylepšení velikosti ovládacích prvků v <xref:System.Windows.Interop.HwndHost?displayProperty=nameWithType> nástroji při spuštění WPF v režimu podporujícím monitorování zakázána (`true`) nebo povolena (`false`).|.NET Framework 4,8|
|`Switch.System.Windows.Forms.`<br/>`DomainUpDown.UseLegacyScrolling`|Určuje, zda vývojář potřebuje při zobrazení textu ovládacího <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> prvku speciálně zpracovat akci. `true`pro zpracování <xref:System.Windows.Forms.DomainUpDown.UpButton> akce; pro akce a<xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>proveďtesynchronizacisprávně. <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> `false`|.NET Framework 4.7.2|
|`Switch.System.Windows.Forms.`<br />`DontSupportReentrantFilterMessage`|Výslovný z kódu, který umožňuje vlastní <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementaci bezpečně filtrovat zprávy bez vyvolání výjimky <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> při volání metody. Další informace najdete v tématu [zmírnění rizika: Vlastní implementace](../../../migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md)IMessageFilter. PreFilterMessage.|.NET Framework 4.6.1|  
|`Switch.System.Windows.Forms.`<br/>`UseLegacyContextMenuStripSourceControlValue`|Určuje, zda <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> vlastnost vrací ovládací prvek zdroje, když uživatel otevře nabídku z vnořeného <xref:System.Windows.Forms.ToolStripMenuItem> ovládacího prvku. `true`pro vrácení `null`starší verze chování; `false` Chcete-li vrátit správu zdrojového kódu.|.NET Framework 4.7.2|
|`Switch.System.Windows.Forms.UseLegacyToolTipDisplay`|Určuje, jestli je podpora volání tlačítek zakázaná`true`() nebo povolená (`false`). Povolení podpory volání popisů tlačítek vyžaduje taky starší funkce usnadnění, `Switch.UseLegacyAccessibilityFeatures`které `Switch.UseLegacyAccessibilityFeatures.2`definuje, `Switch.UseLegacyAccessibilityFeatures.3` a všechny jsou zakázané ( `false`nastavené na).|.NET Framework 4,8|
|`Switch.System.Windows.Input.Stylus.`<br/>`EnablePointerSupport`|Určuje, zda je `WM_POINTER`v aplikacích WPF povolena volitelná dotyková nebo stylusová sada. Další informace najdete v tématu [zmírnění rizika: Dotyková podpora na základě ukazatele a stylusu](../../../migration-guide/mitigation-pointer-based-touch-and-stylus-support.md)|Rozhraní .NET framework 4.7|
|`Switch.System.Windows.Markup.`<br/>`DoNotUseSha256ForMarkupCompilerChecksumAlgorithm`|Určuje, zda je výchozí algoritmus hash používaný pro kontrolní součty SHA256`false`() nebo SHA1`true`().<br>Microsoft doporučuje SHA256 z důvodu kolizí problémů se SHA1.|.NET Framework 4.7.2|
|`Switch.System.Windows.Media.ImageSourceConverter.`<br/>`OverrideExceptionWithNullReferenceException`|Určuje, zda je vyvolána starší verze [NullReferenceException](xref:System.NullReferenceException) namísto výjimky, která přesněji označuje příčinu výjimky (například [DirectoryNotFoundException](xref:System.IO.DirectoryNotFoundException) nebo [FileNotFoundException](xref:System.IO.FileNotFoundException). Je určena pro použití kódem, který závisí na zpracování [NullReferenceException](xref:System.NullReferenceException). | Rozhraní .NET framework 4.7 |
|`Switch.System.Workflow.ComponentModel.`<br/>`UseLegacyHashForXomlFileChecksum`|Určuje, zda je hodnota hash kontrolního součtu souborů XOML v sestaveních projektů pracovních`true`postupů používána pomocí algoritmu MD5 () nebo zda používá SHA256 algoritmus představený jako výchozí v .NET Framework 4,8.<br>Microsoft doporučuje SHA256 z důvodu kolizí problémů s MD5.|.NET Framework 4,8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForSqlTrackingCacheKey`|Určuje, jestli má hashování kontrolního součtu SqlTrackingService používat algoritmus`true`MD5 () pro řetězce uložené v mezipaměti, nebo jestli používá SHA256 algoritmus, který jste zavedli jako výchozí v .NET Framework 4,8.<br>Microsoft doporučuje SHA256 z důvodu kolizí problémů s MD5.|.NET Framework 4,8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForWorkflowDefinitionDispenserCacheKey`|Určuje, jestli má hashový součet pomocí modulu runtime workflowu používat algoritmus`true`MD5 () pro definice pracovních postupů uložených v mezipaměti, nebo jestli používá SHA256 algoritmus, který jste zavedli jako výchozí v .NET Framework 4,8.<br>Microsoft doporučuje SHA256 z důvodu kolizí problémů s MD5.|.NET Framework 4,8|
|`Switch.UseLegacyAccessibilityFeatures`|Určuje, jestli jsou funkce usnadnění dostupné od .NET Framework 4.7.1 povolené nebo zakázané. | .NET Framework 4.7.1 |
|`Switch.UseLegacyAccessibilityFeatures.2`|Určuje, jestli jsou funkce usnadnění dostupné v .NET Framework 4.7.2 povolené`false`() nebo Disabled (`true`). Pokud `true`je `Switch.UseLegacyAccessibilityFeatures` potřeba, musí `true` být také umožněna možnost .NET Framework 4.7.1 funkce usnadnění.|.NET Framework 4.7.2|
|`Switch.UseLegacyAccessibilityFeatures.3`|Určuje, jestli jsou funkce usnadnění zavedené v .NET Framework`false`4,8 povolené ()`true`nebo zakázané (). Pokud `true`a musíbýt`true`také. `Switch.UseLegacyAccessibilityFeatures` `Switch.UseLegacyAccessibilityFeatures.2`|.NET Framework 4,8|
|`Switch.UseLegacyToolTipDisplay`|Určuje, zda se mají zobrazit popisy tlačítek, když uživatel najede myší na ovládací prvek WPF (`true`), nebo zda je zobrazen na ovládacím panelu klávesnice a prostřednictvím klávesy klávesových zkratek`false`(, výchozí chování). `Switch.UseLegacyAccessibilityFeatures`U aplikací, které `Switch.UseLegacyAccessibilityFeatures.2`běží na .NET Framework 4,8, ale cílících na předchozí verze .NET Framework musíte povolit podporu fokusu klávesnice a klávesových zkratek `Switch.UseLegacyAccessibilityFeatures.3` , a to všechny `false`nastavit na.|.NET Framework 4,8|
|`System.Xml.`<br /><br /> `IgnoreEmptyKeySequences`|Určuje, zda jsou prázdné posloupnosti klíčů ve složených klíčích ignorovány ověřováním schématu XSD. Další informace najdete v tématu [zmírnění rizika: Ověřování](../../../migration-guide/mitigation-xml-schema-validation.md)schématu XML.|.NET Framework 4.6|  
  
> [!NOTE]
> `AppContextSwitchOverrides` Místo přidávání elementu do konfiguračního souboru aplikace lze také nastavit přepínače programově `static` voláním metody (in C#) nebo `Shared` (in Visual Basic) <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> .  
  
 Vývojáři knihovny mohou také definovat vlastní přepínače, aby mohli volající odhlásit ze změněných funkcí zavedených v novějších verzích jejich knihoven. Další informace naleznete v tématu <xref:System.AppContext> třída.  
  
## <a name="switches-in-aspnet-applications"></a>Přepínače v aplikacích ASP.NET

ASP.NET aplikaci můžete nakonfigurovat tak, aby používala nastavení kompatibility přidáním [ \<elementu add >](../appsettings/add-element-for-appsettings.md) do [ \<oddílu appSettings >](../appsettings/index.md) souboru Web. config. 

Následující příklad používá `<add>` element pro přidání dvou nastavení `<appSettings>` do oddílu souboru Web. config:

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="example"></a>Příklad

 Následující příklad používá `AppContextSwitchOverrides` element k definování jednoho `Switch.System.Globalization.NoAsyncCurrentCulture`přepínače kompatibility aplikace, který brání jazykové verzi v toku mezi vlákny v volání asynchronní metody.  
  
```xml  
<configuration>  
   <runtime>  
      <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />  
   </runtime>  
</configuration>  
```  
  
 Následující příklad používá `AppContextSwitchOverrides` element k definování dvou `Switch.System.Globalization.NoAsyncCurrentCulture` přepínačů kompatibility aplikace a `Switch.System.IO.BlockLongPaths`. Všimněte si, že obě dvojice název/hodnota jsou odděleny středníkem.  
  
```xml  
<configuration>  
    <runtime>  
       <AppContextSwitchOverrides   
          value="Switch.System.Globalization.NoAsyncCurrentCulture=true;Switch.System.IO.BlockLongPaths=true" />  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.AppContext?displayProperty=nameWithType>
- [\<Běhový > element](runtime-element.md)
- [\<Element > Konfigurace](../configuration-element.md)
