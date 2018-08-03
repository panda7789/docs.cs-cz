---
title: '&lt;AppContextSwitchOverrides&gt; – Element'
ms.custom: updateeachrelease
ms.date: 04/19/2018
helpviewer_keywords:
- AppContextSwitchOverrides
- compatibility switches
- configuration switches
- configuration
ms.assetid: 4ce07f47-7ddb-4d91-b067-501bd8b88752
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d16ce7f2744869c812b9988e91edd153d9cb4fd2
ms.sourcegitcommit: e8dc507cfdaad504fc9d4c83d28d24569dcef91c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "32747522"
---
# <a name="ltappcontextswitchoverridesgt-element"></a>&lt;AppContextSwitchOverrides&gt; – Element
Definuje jeden nebo více přepínačů používané <xref:System.AppContext> třídě poskytnout mechanismus výslovného nesouhlasu pro nové funkce.  
  
 \<Konfigurace >  
 \<modul runtime >  
\<AppContextSwitchOverrides >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<AppContextSwitchOverrides value="name1=value1[[;name2=value2];...]" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`value`|Požadovaný atribut.<br /><br /> Definuje jeden nebo více názvů switchů a jejich přidružené logické hodnoty.|  
  
### <a name="value-attribute"></a>Hodnota atributu  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|"název = hodnota"|Název předdefinované přepínače spolu s hodnotou (`true` nebo `false`). Více dvojice název/hodnota přepínače jsou odděleny středníky (";"). Seznam názvů předdefinované přepínač podporuje rozhraní .NET Framework naleznete v části poznámky.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 Od verze rozhraní .NET Framework 4.6 `<AppContextSwitchOverrides>` element v konfiguračním souboru umožňuje volajícím určit, jestli můžete své aplikace mohli využívat nové funkce nebo zachování kompatibility s předchozími verzemi knihovny rozhraní API. Například, pokud došlo ke změně chování rozhraní API mezi dvěma verzemi knihovny `<AppContextSwitchOverrides>` element umožňuje volající toto rozhraní API můžete kdykoliv zrušit nové chování ve verzích knihovny, které podporují nové funkce. Pro aplikace, které volají rozhraní API v rozhraní .NET Framework `<AppContextSwitchOverrides>` element můžete také povolit volající, jejichž aplikace cílí na starší verzi rozhraní .NET Framework pro přidání do nové funkce, pokud jejich aplikace běží na verzi rozhraní .NET Framework, která zahrnuje funkce.  
  
 `value` Atribut `<AppContextSwitchOverrides>` element se skládá z jednoho řetězce, který se skládá z jednoho nebo více dvojice název hodnota oddělené středníky.  Každý název identifikuje přepínač kompatibility a jeho odpovídající hodnota je logická hodnota (`true` nebo `false`), která označuje, zda je nastaven přepínač. Ve výchozím nastavení, je v přepínači `false`, a knihoven poskytuje nové funkce. Předchozí funkce poskytují pouze pokud přepínač nastavený (to znamená, je jeho hodnota `true`). To umožňuje knihovny k poskytnutí nové chování pro existující rozhraní API zároveň umožní volajícím, které závisí na předchozím chování chcete vyjádřit výslovný nesouhlas nové funkce.  
  
 Rozhraní .NET Framework podporuje následující přepínače:  
  
|Název přepínače|Popis|Zavedena|  
|-----------------|-----------------|----------------|  
|`Switch.MS.Internal.`<br/>`DoNotApplyLayoutRoundingToMarginsAndBorderThickness`|Určuje, zda Windows Presentation Foundation používá starší verze algoritmu pro rozložení ovládacích prvků. Další informace najdete v tématu [omezení rizik: rozložení WPF](~/docs/framework/migration-guide/mitigation-wpf-layout.md).|.NET Framework 4.6|  
|`Switch.MS.Internal.`<br/>`UseSha1AsDefaultHashAlgorithmForDigitalSignatures`|Určuje, zda je výchozí algoritmus používaný k podepisování součástí balíčku PackageDigitalSignatureManager SHA1 nebo SHA256.|Rozhraní .NET framework 4.7.1|
|`Switch.System.Activities.`<br/>`UseMD5CryptoServiceProviderForWFDebugger`|Pokud je nastavena na `false`, umožňuje ladění projektů pracovních postupů založených na XAML pomocí sady Visual Studio, když je povolený standard FIPS. Bez něj <xref:System.NullReferenceException> je vyvolána výjimka ve voláních metod v sestavení System.Activities.|Rozhraní .NET framework 4.7|
|`Switch.System.Activities.`<br/>`UseMD5ForWFDebugger`|Určuje, zda kontrolního součtu pro instanci pracovního postupu v ladicím programu, používá algoritmus MD5 nebo SHA1. | Rozhraní .NET framework 4.7|
|`Switch.System.Diagnostics.`<br/>`IgnorePortablePDBsInStackTraces`|Určuje, zda získat trasování zásobníku při použití přenosných souborů PDB může zahrnovat informace o zdrojovém souboru a řádku. `false` informace zdrojového souboru a řádku; v opačném případě `true`.|Rozhraní .NET framework 4.7.2|
|`Switch.System.Drawing.`<br/>`DontSupportPngFramesInIcons`|Ovládací prvky, zda <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda vyvolá výjimku při <xref:System.Drawing.Icon> objekt má snímky PNG. Další informace najdete v tématu [omezení rizik: PNG rámce v objektech ikonu](~/docs/framework/migration-guide/mitigation-png-frames-in-icon-objects.md).|.NET Framework 4.6|  
|`Switch.System.Drawing.Text.`<br/>`DoNotRemoveGdiFontsResourcesFromFontCollection`|Určuje, zda <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> objekty jsou správně odstraněn, když se přidá do kolekce podle <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType> metody. `true` Chcete-li zachovat starší chování; `false` k uvolnění všech objektů privátní písma. |Rozhraní .NET framework 4.7.2|
|`Switch.System.Drawing.Printing.`</br>`OptimizePrintPreview`|Ovládací prvky, zda výkon <xref:System.Windows.Forms.PrintPreviewDialog> je optimalizovaná pro síťové tiskárny. Další informace najdete v tématu [printpreviewdialog – Přehled ovládacího prvku](../../../winforms/controls/printpreviewdialog-control-overview-windows-forms.md).|.NET Framework 4.6|
|`Switch.System.Globalization.NoAsyncCurrentCulture`|Určuje, zda asynchronní operace nejsou tok z kontextu volajícího vlákna. Další informace najdete v tématu [CurrentCulture a CurrentUICulture téct přes úlohy](~/docs/framework/migration-guide/retargeting/4.5.2-4.6.md#currentculture-and-currentuiculture-flow-across-tasks).|.NET Framework 4.6|  
|`Switch.System.IdentityModel.`<br/>`DisableMultipleDNSEntriesInSANCertificate`|Ovládací prvky, zda <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> metoda se pokusí shodovat s typem deklarace identity jenom s poslední položky DNS. Další informace najdete v tématu [omezení rizik: metoda X509CertificateClaimSet.FindClaims](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md).|.NET Framework 4.6.1|  
|`Switch.System.IdentityModel.`<br/>`EnableCachedEmptyDefaultAuthorizationContext`|Určuje, jestli se má povolit AuthorizationContext.Empty vrátit měnitelný objekt.|.NET Framework 4.6|  
|`Switch.System.IO.BlockLongPaths`|Ovládací prvky, zda cesty delší než `MAX_PATH` throw (260 znaků) <xref:System.IO.PathTooLongException>. Další informace najdete v tématu [dlouhá cesta podporu](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#long-path-support).|.NET Framework 4.6.2|  
|`Switch.System.IO.Compression.`<br/>`DoNotUseNativeZipLibraryForDecompression`|Určuje, zda nativní rutiny operačního systému se používají pro dekompresi podle <xref:System.IO.Compression.DeflateStream> třídy. `false` použití nativních rozhraní API; `true` používat <xref:System.IO.Compression.DeflateStream> implementace.|Rozhraní .NET framework 4.7.2|
|`Switch.System.IO.Compression.ZipFile.`<br/>`UseBackslash`|Používá zpětné lomítko ("\\") namísto dopředného lomítka ("/") jako oddělovač cesty v <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> vlastnost. Další informace najdete v tématu [omezení rizik: Oddělovač cesty ZipArchiveEntry.FullName](~/docs/framework/migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md).|.NET Framework 4.6.1|  
|`Switch.System.IO.Ports.`<br/>`DoNotCatchSerialStreamThreadExceptions`|Určuje, jestli operační systém výjimky, které jsou vyvolány na pozadí podprocesů, které jsou vytvořené pomocí <xref:System.IO.Ports.SerialPort> datové proudy ukončit proces.|Rozhraní .NET framework 4.7.1| 
|`Switch.System.IO.`<br/>`UseLegacyPathHandling`|Určuje, zda se používá starší verzi cesta normalizace a cesty identifikátorů URI jsou podporovány <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> a <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> metody. Další informace najdete v tématu [omezení rizik: cesta normalizace](~/docs/framework/migration-guide/mitigation-path-normalization.md) a [omezení rizik: cesta dvojtečka kontroluje](~/docs/framework/migration-guide/mitigation-path-colon-checks.md).|.NET Framework 4.6.2|  
|`Switch.System.`<br/>`MemberDescriptorEqualsReturnsFalseIfEquivalent`|Určuje, jestli testu pro porovná rovnost <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=nameWithType> vlastností jednoho objektu s <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=nameWithType> vlastnost druhého objektu. Další informace najdete v tématu [nesprávná implementace MemberDescriptor.Equals](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#incorrect-implementation-of-memberdescriptorequals).|.NET Framework 4.6.2|  
 `Switch.System.Net.`<br/>`DontCheckCertificateEKUs`|Zakáže rozšířené použití klíče (EKU) objektu (OID) identifikátor ověření certifikátu. Kolekce identifikátorů objektu (OID), které označují aplikace, které používají klíč je rozšíření rozšířené použití klíče (EKU).|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchSendAuxRecord`|Zakáže zmírnění protokol TLS 1.0 prohlížeče zneužít proti protokolu SSL/TLS (TOUCHDOWN) tím, že zakážete použití SCH_SEND_AUX_RECORD.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchUseStrongCrypto`|Ovládací prvky, zda <xref:System.Net.ServicePointManager?displayProperty=nameWithType> a <xref:System.Net.Security.SslStream?displayProperty=nameWithType> tříd můžete použít protokol SSL 3.0. Další informace najdete v tématu [omezení rizik: protokoly TLS](~/docs/framework/migration-guide/mitigation-tls-protocols.md).|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSystemDefaultTlsVersions`|Zakáže SystemDefault TLS verze návrat zpět k výchozímu nastavení Tls12, Tls11, Tls.|Rozhraní .NET framework 4.7|
|`Switch.System.Net.`<br/>`DontEnableTlsAlerts`|Zakáže upozornění SslStream TLS na straně serveru.|Rozhraní .NET framework 4.7|
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseECMAScriptV6EscapeControlCharacter` |Ovládací prvky, zda [DataContractJsonSerializer](xref:System.Runtime.Serialization.Json.DataContractJsonSerializer) serializuje některé řídicí znaky na základě standardů ECMAScript V6 a V8. Další informace najdete v tématu [omezení rizik: serializace řídicí znaky s objektu DataContractJsonSerializer](Mitigation:%20Serialization%20of%20Control%20Characters%20with%20the%20DataContractJsonSerializer.md)| Rozhraní .NET framework 4.7 |
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseTimeZoneInfo`|Ovládací prvky, zda <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> podporuje víc úpravy nebo pouze jediné úpravy pro časové pásmo. Pokud `true`, použije <xref:System.TimeZoneInfo> typ k serializaci a deserializaci data a času; v opačném případě se použije <xref:System.TimeZone> typ, který nepodporuje víc úpravy pravidel.|.NET Framework 4.6.2|
|`Switch.System.Security.ClaimsIdentity.`<br/>`SetActorAsReferenceWhenCopyingClaimsIdentity`|Ovládací prvky, zda <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=nameWithType> konstruktor nastaví nový objekt <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=nameWithType> vlastnost s existující odkaz na objekt. Další informace najdete v tématu [omezení rizik: konstruktor ClaimsIdentity](~/docs/framework/migration-guide/mitigation-claimsidentity-constructor.md).|.NET Framework 4.6.2|  
|`Switch.System.Security.Cryptography.`<br/>`AesCryptoServiceProvider.DontCorrectlyResetDecryptor`|Ovládací prvky, zda pokus o opakované použití <xref:System.Security.Cryptography.AesCryptoServiceProvider> vyvolá modul pro dešifrování <xref:System.Security.Cryptography.CryptographicException>. Další informace najdete v tématu [AesCryptoServiceProvider modul pro dešifrování. nabízí opakovaně použitelné transformace](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#aescryptoserviceprovider-decryptor-provides-a-reusable-transform).|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`DoNotAddrOfCspParentWindowHandle`|Ovládací prvky, zda hodnota [CspParameters.ParentWindowHandle](xref:System.Security.Cryptography.CspParameters.ParentWindowHandle) vlastnost je [IntPtr](xref:System.IntPtr) , že zpracování představuje umístění okna v paměti, nebo zda je popisovač okna (popisovačem HWND). Další informace najdete v tématu [omezení rizik: CspParameters.ParentWindowHandle očekává, že popisovačem HWND](Mitigation:%20CspParameters.ParentWindowHandle%20Expects%20an%20HWND.md). |Rozhraní .NET framework 4.7|   
|`Switch.System.Security.Cryptography.Pkcs.`<br/>`UseInsecureHashAlgorithms`|Určuje, zda je výchozí nastavení pro některé operace SignedCMS SHA1 nebo SHA256. |Rozhraní .NET framework 4.7.1|
|`Switch.System.Security.Cryptography.Xml.`<br/>`UseInsecureHashAlgorithms`|Určuje, zda je výchozí nastavení pro některé operace SignedXML SHA1 nebo SHA256. |Rozhraní .NET framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`AllowUnsignedToHeader`|Určuje, zda `TransportWithMessageCredential` umožňuje režim zabezpečení zpráv pomocí bez znaménka "na" záhlaví. To je přepínač opt-in. Další informace najdete v tématu [změny v modulu Runtime v rozhraní .NET Framework 4.6.1](https://msdn.microsoft.com/library/mt592686.aspx#WCF).|.NET Framework 4.6.1| 
|`Switch.System.ServiceModel.`<br/>`DisableAddressHeaderCollectionValidation`>|Ovládací prvky, zda <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> vyvolá konstruktor <xref:System.ArgumentException> Pokud jeden z elementů je `null`.|Rozhraní .NET framework 4.7.1| 
|`Switch.System.ServiceModel.`<br />`DisableCngCertificates`|Určuje, že zda pokus o použití X509 certifikáty pomocí zprostředkovatele úložiště klíčů CSG vyvolá výjimku. Další informace najdete v tématu [zabezpečení přenosu WCF podporuje certifikáty na Uložit pomocí CNG](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#wcf-transport-security-supports-certificates-stored-using-cng).|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableExplicitConnectionCloseHeader`|Při použití přenosového protokolu HTTP s využitím služby v místním prostředí, pokud tuto hodnotu nastavíte `true` způsobí, že WCF ignorovat přidávání aplikací `Connection: close` záhlaví hlavičky odpovědi pro požadavek. Tuto hodnotu nastavíte na `false` umožňuje přidání `Connection: close` záhlaví hlavičky odpovědi, což vede k uzavření žádosti o soketu po odeslání odpovědi.|.NET Framework 4.6|
|`Switch.System.ServiceModel.`<br/>`DisableOperationContextAsyncFlow`|Zablokování obslužné rutiny, které jsou výsledkem omezení instance vícenásobné služby na jedno vlákno provádění v čase.|.NET Framework 4.6.2|
|`Switch.System.ServiceModel.`<br/>`DisableUsingServicePointManagerSecurityProtocols`|Spolu s `Switch.System.Net.DontEnableSchUseStrongCrypto`, určuje, jestli používá zabezpečení zpráv WCF TLS 1.1 a TLS 1.2.|Rozhraní .NET framework 4.7 |    
|`Switch.System.ServiceModel.`<br/>`DontEnableSystemDefaultTlsVersions`|Hodnota `false` nastaví výchozí konfigurace umožňuje zvolit protokol operačního systému. Hodnota `true` nastaví výchozí nejvyšší protokolu, které jsou k dispozici. (K dispozici také v obslužná větev z předchozí verze rozhraní framework)|Rozhraní .NET framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InMsmqEncryptionAlgorithm`|Určuje, zda je výchozí zprávu podpisový algoritmus pro zprávy služby MSMQ ve službě WCF SHA1 nebo SHA256.|Rozhraní .NET framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InPipeConnectionGetHashAlgorithm`|Určuje, zda WCF používá ke generování náhodných názvů u pojmenovaných kanálů SHA1 nebo hodnotu hash SHA256.|Rozhraní .NET framework 4.7.1|
|`Switch.System.ServiceModel.Internals`<br/>`IncludeNullExceptionMessageInETWTrace`|Určuje, zda má být vyvolána [NullReferenceException](xref:System.NullReferenceException) při zpráva výjimky je null.|Rozhraní .NET framework 4.7|  
|`Switch.System.ServiceProcess.`<br/>`DontThrowExceptionsOnStart`|Určuje, zda výjimky vyvolané při spuštění služby se rozšíří do volajícího <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> metody.|Rozhraní .NET framework 4.7.1|
|`Switch.System.Uri.`<br/>`DontEnableStrictRFC3986ReservedCharacterSets`|Určuje, zda některých procentuálně zakódovaný, které byly někdy dekódovat nyní konzistentně vlevo kódování znaků. Pokud `true`, jsou dekódovaný; v opačném případě `false`.|Rozhraní .NET framework 4.7.2|
|`Switch.System.Uri.`<br/>`DontKeepUnicodeBidiFormattingCharacters`|Určuje zpracování obousměrné znaky Unicode v identifikátorech URI. `true` pro odstranění z identifikátorů URI; `false` zachovat a procent kódovat.|Rozhraní .NET framework 4.7.2|
|`Switch.System.Windows.Controls.Grid.`<br/>`StarDefinitionsCanExceedAvailableSpace` |Určuje, zda Windows Presentation Foundation použije původní algoritmus (`true`) nebo nový algoritmus (`false`) v přidělování prostoru pro \*– sloupce. Další informace najdete v tématu [omezení rizik: ovládací prvek mřížky přidělování místa na hvězdičku sloupce](Mitigation:%20Grid%20Control's%20Space%20Allocation%20to%20Star-columns.md). |Rozhraní .NET framework 4.7 |
|`Switch.System.Windows.Controls.TabControl.`<br/>`SelectionPropertiesCanLagBehindSelectionChangedEvent`|Určuje, zda selektor nebo na kartě řízení vždy aktualizuje hodnotu vlastností vybranou hodnotu před vyvoláním výběru ovládacích prvků událost změněné.|Rozhraní .NET framework 4.7.1|
|`Switch.System.Windows.Controls.Text.`<br/>`UseAdornerForTextboxSelectionRendering`|Určuje, zda je k dispozici pro vykreslování – doplněk pro úpravy na základě výběru <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.PasswordBox> ovládací prvky, aby se zabránilo occluded text (`false`), nebo zda text je vykreslen pouze ve vrstvě doplněk pro úpravy (`true`).|Rozhraní .NET framework 4.7.2|
|`Switch.System.Windows.DoNotScaleForDpiChanges`|Určuje, zda DPI změnách na jednotlivé systému (hodnota `false`) nebo na monitorování jednotlivých (hodnotu `true`).|.NET Framework 4.6.2|
|`Switch.System.Windows.Forms.`<br/>`DomainUpDown.UseLegacyScrolling`|Určuje, zda vývojář potřebuje pro zpracování speciálně <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> akci, když je k dispozici text ovládacího prvku. `true` zpracování <xref:System.Windows.Forms.DomainUpDown.UpButton> akce; `false` pro <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> a <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> akce, které byly správně synchronizované.|Rozhraní .NET framework 4.7.2|
|`Switch.System.Windows.Forms.`<br />`DontSupportReentrantFilterMessage`|Požádá o mimo kód, který umožňuje vlastní <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementace bezpečně filtrovat zprávy bez vyvolání výjimky při <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> metoda je volána. Další informace najdete v tématu [omezení rizik: implementace vlastního IMessageFilter.PreFilterMessage](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).|.NET Framework 4.6.1|  
|`Switch.System.Windows.Forms.`<br/>`UseLegacyContextMenuStripSourceControlValue`|Určuje, zda <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> vlastnost vrací správy zdrojového kódu, když uživatel otevře v nabídce vnořeném <xref:System.Windows.Forms.ToolStripMenuItem> ovládacího prvku. `true` Chcete-li vrátit `null`, starší chování; `false` vrátit správy zdrojového kódu.|Rozhraní .NET framework 4.7.2|
|`Switch.System.Windows.Input.Stylus.`<br/>`EnablePointerSupport`|Určuje, zda je volitelný `WM_POINTER`– na základě touch/stylus zásobníku je povolená v aplikaci WPF. Další informace najdete v tématu [omezení rizik: založená na ukazatelích dotykového ovládání a podpora pera](../../../migration-guide/mitigation-pointer-based-touch-and-stylus-support.md)|Rozhraní .NET framework 4.7|
|`Switch.System.Windows.Markup.`<br/>`DoNotUseSha256ForMarkupCompilerChecksumAlgorithm`|Určuje, zda je výchozí algoritmus hash používá pro kontrolní součty SHA256 (`false`) nebo SHA1 (`true`).|Rozhraní .NET framework 4.7.2|
|`Switch.System.Windows.Media.ImageSourceConverter.`<br/>`OverrideExceptionWithNullReferenceException`|Určuje, jestli starší verze [NullReferenceException](xref:System.NullReferenceException) dojde místo výjimku, přesněji řečeno určuje příčina výjimky (například [DirectoryNotFoundException –](xref:System.IO.DirectoryNotFoundException) nebo [ FileNotFoundException](xref:System.IO.FileNotFoundException). Je určena pro použití kódem, který závisí na zpracování [NullReferenceException](xref:System.NullReferenceException). | Rozhraní .NET framework 4.7 |
|`Switch.UseLegacyAccessibilityFeatures`|Ovládací prvky, zda funkce usnadnění je k dispozici od verze rozhraní .NET Framework 4.7.1 jsou zapnutá nebo vypnutá. | Rozhraní .NET framework 4.7.1 |
|`Switch.UseLegacyAccessibilityFeatures.2`|Určuje, zda funkce usnadnění v rozhraní .NET Framework 4.7.2 k dispozici jsou povolené ovládacích prvků (`false`) nebo je zakázaný (`true`). Pokud `true`, `Switch.UseLegacyAccessibilityFeatures` musí také být `true` povolit funkce usnadnění v rozhraní .NET Framework 4.7.1.|Rozhraní .NET framework 4.7.2|
|`System.Xml.`<br /><br /> `IgnoreEmptyKeySequences`|Určuje, zda jsou ignorovány prázdná pořadí klíčů v složených klíčů pomocí ověření schématu XSD. Další informace najdete v tématu [omezení rizik: ověřování schématu XML](~/docs/framework/migration-guide/mitigation-xml-schema-validation.md).|.NET Framework 4.6|  
  
> [!NOTE]
>  Nepřidávat `AppContextSwitchOverrides` prvku do konfiguračního souboru aplikace, můžete také nastavit přepínače programově zavoláním `static` (v jazyce C#) nebo `Shared` (v jazyce Visual Basic) <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> metody.  
  
 Vývojáři knihoven můžete také definovat vlastní přepínače pro povolení volajícím chcete vyjádřit výslovný nesouhlas změněné funkce zavedeny v pozdějších verzích jejich knihoven. Další informace najdete v tématu <xref:System.AppContext> třídy.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `AppContextSwitchOverrides` elementu k definování přepínače kompatibility jednu aplikaci, `Switch.System.Globalization.NoAsyncCurrentCulture`, jazykovou verzi, který brání z toku napříč vlákny v volání asynchronní metody.  
  
```xml  
<configuration>  
   <runtime>  
      <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />  
   </runtime>  
</configuration>  
```  
  
 V následujícím příkladu `AppContextSwitchOverrides` element definovat dvě přepínače kompatibility aplikací, `Switch.System.Globalization.NoAsyncCurrentCulture` a `Switch.System.IO.BlockLongPaths`. Všimněte si, že odděluje středníky dvě dvojice název/hodnota.  
  
```xml  
<configuration>  
    <runtime>  
       <AppContextSwitchOverrides   
          value="Switch.System.Globalization.NoAsyncCurrentCulture=true;Switch.System.IO.BlockLongPaths=true" />  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.AppContext?displayProperty=nameWithType>  
 [\<modul runtime > – Element](runtime-element.md)  
 [\<Konfigurace > – Element](../configuration-element.md)
