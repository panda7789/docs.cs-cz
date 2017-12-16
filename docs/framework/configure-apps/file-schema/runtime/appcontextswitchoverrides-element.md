---
title: "&lt;AppContextSwitchOverrides&gt; – Element"
ms.custom: 
ms.date: 10/17/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AppContextSwitchOverrides
- compatibility switches
- configuration switches
- configuration
ms.assetid: 4ce07f47-7ddb-4d91-b067-501bd8b88752
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 83244e1df239110d86367423b91458aefb5d07a5
ms.sourcegitcommit: 5bfcb8d341239df251351f318038d31cdc9159d7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2017
---
# <a name="ltappcontextswitchoverridesgt-element"></a>&lt;AppContextSwitchOverrides&gt; – Element
Definuje jeden nebo více přepínač používaný <xref:System.AppContext> třídy poskytují mechanismus vyjádření výslovného nesouhlasu pro nové funkce.  
  
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
|`value`|Požadovaný atribut.<br /><br /> Definuje jeden nebo více názvů přepínače a jejich přidružené hodnoty, logická hodnota.|  
  
### <a name="value-attribute"></a>Hodnota atributu  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|"název = hodnota"|Název předdefinované přepínače společně s jeho hodnota (`true` nebo `false`). Více dvojic název hodnota přepínače jsou odděleny středníky (";"). Seznam názvů předdefinované přepínač nepodporuje rozhraní .NET Framework najdete v části poznámky.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 Od verze rozhraní .NET Framework 4.6 `<AppContextSwitchOverrides>` element v konfiguračním souboru umožňuje volající rozhraní API pro určení, zda své aplikace můžete využít nové funkce nebo zachování kompatibility s předchozími verzemi knihovny. Pokud došlo ke změně chování rozhraní API mezi dvěma verzemi knihovny, například `<AppContextSwitchOverrides>` element umožňuje volající toto rozhraní API pro vyjádření výslovného nesouhlasu nové chování na verze knihovny, které podporují nové funkce. Pro aplikace, které volání rozhraní API v rozhraní .NET Framework `<AppContextSwitchOverrides>` element můžete povolit také volající cíle dřívější verzi rozhraní .NET Framework, který se přidá do nové funkce, pokud své aplikace běží na verzi rozhraní .NET Framework, která zahrnuje, jejichž aplikace funkce.  
  
 `value` Atribut `<AppContextSwitchOverrides>` element se skládá z jednoho řetězce, který obsahuje jeden nebo více páry název hodnota oddělené středníkem.  Každý název identifikuje kompatibility přepínače a jeho odpovídající hodnota je logická hodnota (`true` nebo `false`) určující, zda je nastaven přepínač. Ve výchozím nastavení, je přepínač `false`, a knihovny přinášejí nové funkce. Předchozí funkce poskytují pouze pokud je přepínač nastavený (který je jeho hodnota může být `true`). To umožňuje knihovny zajistit nové chování pro existující rozhraní API současně volající, kteří jsou závislé na předchozí chování pro vyjádření výslovného nesouhlasu nové funkce.  
  
 Rozhraní .NET Framework podporuje následující přepínače:  
  
|Název přepínače|Popis|Zavedly|  
|-----------------|-----------------|----------------|  
|`Switch.MS.Internal.`<br/>`DoNotApplyLayoutRoundingToMarginsAndBorderThickness`|Určuje, zda Windows Presentation Foundation používá starší verze algoritmus pro rozložení ovládacích prvků. Další informace najdete v tématu [omezení rizik: rozložení WPF](~/docs/framework/migration-guide/mitigation-wpf-layout.md).|.NET Framework 4.6|  
|`Switch.MS.Internal.`<br/>`UseSha1AsDefaultHashAlgorithmForDigitalSignatures`|Určuje, zda je výchozí algoritmus používaný k podepisování části balíčku PackageDigitalSignatureManager SHA1 nebo SHA256.|Rozhraní .NET framework 4.7.1|
|`Switch.System.Activities.`<br/>`UseMD5CryptoServiceProviderForWFDebugger`|Pokud nastavíte hodnotu `false`, umožňuje ladění projektů založených na XAML pracovního postupu pomocí sady Visual Studio, pokud je povoleno FIPS. Bez něj <xref:System.NullReferenceException> je vyvolána ve voláních metod v sestavení systém.|Rozhraní .NET framework 4.7|
|`Switch.System.Activities.`<br/>`UseMD5ForWFDebugger`|Určuje, zda kontrolního součtu pro instanci pracovního postupu v ladicím programu používá algoritmus MD5 nebo SHA1. | Rozhraní .NET framework 4.7|
|`Switch.System.Drawing.`<br/>`DontSupportPngFramesInIcons`|Ovládací prvky jestli <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda výjimku při <xref:System.Drawing.Icon> objekt má rámce PNG. Další informace najdete v tématu [omezení rizik: PNG rámce v objektech ikonu](~/docs/framework/migration-guide/mitigation-png-frames-in-icon-objects.md).|.NET Framework 4.6|  
|`Switch.System.Globalization.NoAsyncCurrentCulture`|Určuje, zda z kontextu volající vlákno není toku asynchronní operace. Další informace najdete v tématu [CurrentCulture a CurrentUICulture tok napříč úlohy](~/docs/framework/migration-guide/retargeting/4.5.2-4.6.md#currentculture-and-currentuiculture-flow-across-tasks).|.NET Framework 4.6|  
|`Switch.System.IdentityModel.`<br/>`DisableMultipleDNSEntriesInSANCertificate`|Ovládací prvky jestli <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> metoda se pokusí o porovnání typ deklarace identity jenom s poslední položky DNS. Další informace najdete v tématu [omezení rizik: metoda X509CertificateClaimSet.FindClaims](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md).|.NET Framework 4.6.1|  
|`Switch.System.IO.BlockLongPaths`|Ovládací prvky zda cesty delší než `MAX_PATH` throw (260 znaků) <xref:System.IO.PathTooLongException>. Další informace najdete v tématu [dlouhá cesta podporu](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#long-path-support).|.NET Framework 4.6.2|  
|`Switch.System.IO.Compression.ZipFile.`<br/>`UseBackslash`|Používá zpětné lomítko ("\\") namísto dopředné lomítko ("/") jako oddělovač cesty v <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> vlastnost. Další informace najdete v tématu [omezení rizik: Oddělovač cesty ZipArchiveEntry.FullName](~/docs/framework/migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md).|.NET Framework 4.6.1|  
|`Switch.System.IO.Ports.`<br/>`DoNotCatchSerialStreamThreadExceptions`|Určuje, jestli operační systém výjimky, které jsou vyvolány na vytvořené pomocí vlákna na pozadí <xref:System.IO.Ports.SerialPort> datové proudy ukončit proces.|Rozhraní .NET framework 4.7.1| 
|`Switch.System.IO.`<br/>`UseLegacyPathHandling`|Určuje, zda se používá starší verze cesta normalizaci a cesty identifikátoru URI se nepodporuje <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> a <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> metody. Další informace najdete v tématu [zmírnění dopadů: cesta normalizaci](~/docs/framework/migration-guide/mitigation-path-normalization.md) a [zmírnění dopadů: cesta dvojtečkou kontroluje](~/docs/framework/migration-guide/mitigation-path-colon-checks.md).|.NET Framework 4.6.2|  
|`Switch.System.`<br/>`MemberDescriptorEqualsReturnsFalseIfEquivalent`|Určuje, jestli testu pro porovná rovnost <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=nameWithType> vlastnost jednoho objektu s <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=nameWithType> vlastnost druhý objekt. Další informace najdete v tématu [nesprávné implementace MemberDescriptor.Equals](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#incorrect-implementation-of-memberdescriptorequals).|.NET Framework 4.6.2|  
 `Switch.System.Net.`<br/>`DontCheckCertificateEKUs`|Zakáže rozšířené použití klíče (EKU) objektu (OID) identifikátor ověření certifikátu. Kolekce identifikátorů objektů (OID), které označují aplikace, které používají klíče je rozšíření rozšířené použití klíče (EKU).|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchSendAuxRecord`|Zakázáním použití SCH_SEND_AUX_RECORD zakáže zmírnění TLS1.0 prohlížeče zneužít proti SSL/TLS (BEAST).|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchUseStrongCrypto`|Ovládací prvky jestli <xref:System.Net.ServicePointManager?displayProperty=nameWithType> a <xref:System.Net.Security.SslStream?displayProperty=nameWithType> třídy můžete použít protokol SSL 3.0. Další informace najdete v tématu [omezení rizik: protokoly TLS](~/docs/framework/migration-guide/mitigation-tls-protocols.md).|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSystemDefaultTlsVersions`|Zakáže SystemDefault TLS verze vrácení zpět na výchozí Tls12, Tls11, Tls.|Rozhraní .NET framework 4.7|
|`Switch.System.Net.`<br/>`DontEnableTlsAlerts`|Zakáže výstrahy SslStream TLS na straně serveru.|Rozhraní .NET framework 4.7|
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseECMAScriptV6EscapeControlCharacter` |Ovládací prvky jestli [DataContractJsonSerializer](xref:System.Runtime.Serialization.Json.DataContractJsonSerializer) serializuje některé řídicí znaky založených na standardech ECMAScript V6 a v8:. Další informace najdete v tématu [omezení rizik: serializace řídicí znaky s objektu DataContractJsonSerializer](Mitigation:%20Serialization%20of%20Control%20Characters%20with%20the%20DataContractJsonSerializer.md)| Rozhraní .NET framework 4.7 |
|`Switch.System.Security.ClaimsIdentity.`<br/>`SetActorAsReferenceWhenCopyingClaimsIdentity`|Ovládací prvky jestli <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=nameWithType> konstruktor nastaví nový objekt <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=nameWithType> vlastnost s odkaz na existující objekt. Další informace najdete v tématu [omezení rizik: konstruktor ClaimsIdentity](~/docs/framework/migration-guide/mitigation-claimsidentity-constructor.md).|.NET Framework 4.6.2|  
|`Switch.System.Security.Cryptography.`<br/>`AesCryptoServiceProvider.DontCorrectlyResetDecryptor`|Ovládací prvky zda pokus o opakované použití <xref:System.Security.Cryptography.AesCryptoServiceProvider> vyvolá modul pro dešifrování <xref:System.Security.Cryptography.CryptographicException>. Další informace najdete v tématu poskytuje modul pro dešifrování AesCryptoServiceProvider opakovaně použitelné transform](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#aescryptoserviceprovider-decryptor-provides-a-reusable-transform).|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`DoNotAddrOfCspParentWindowHandle`|Ovládací prvky zda hodnotu [CspParameters.ParentWindowHandle](xref:System.Security.Cryptography.CspParameters.ParentWindowHandle) vlastnost je [IntPtr](xref:System.IntPtr) , představuje umístění paměti okno zpracování, nebo zda je popisovač okna (popisovačem HWND). Další informace najdete v tématu [omezení rizik: CspParameters.ParentWindowHandle očekává popisovačem HWND](Mitigation:%20CspParameters.ParentWindowHandle%20Expects%20an%20HWND.md). |Rozhraní .NET framework 4.7|   
|`Switch.System.Security.Cryptography.Pkcs.`<br/>`UseInsecureHashAlgorithms`|Určuje, zda je výchozí nastavení pro některé operace SignedCMS SHA1 nebo SHA256. |Rozhraní .NET framework 4.7.1|
|`Switch.System.Security.Cryptography.Xml.`<br/>`UseInsecureHashAlgorithms`|Určuje, zda je výchozí nastavení pro některé operace SignedXML SHA1 nebo SHA256. |Rozhraní .NET framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`AllowUnsignedToHeader`|Určuje, zda `TransportWithMessageCredential` režim zabezpečení umožňuje zprávy s nepodepsaný "na" záhlaví. Toto je přepínač přihlášení. Další informace najdete v tématu [změny v modulu Runtime v rozhraní .NET Framework 4.6.1](https://msdn.microsoft.com/library/mt592686.aspx#WCF).|.NET Framework 4.6.1| 
|`Switch.System.ServiceModel.`<br/>`DisableAddressHeaderCollectionValidation`>|Ovládací prvky jestli <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> konstruktor vyvolá <xref:System.ArgumentException> Pokud jeden z elementů je `null`.|Rozhraní .NET framework 4.7.1| 
|`Switch.System.ServiceModel.`<br />`DisableCngCertificates`|Určuje, že zda pokus o použití X509 certifikátů pomocí zprostředkovatele úložiště klíčů CSG vyvolá výjimku. Další informace najdete v tématu [zabezpečení přenosu WCF podporuje certifikáty uložené pomocí CNG](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#wcf-transport-security-supports-certificates-stored-using-cng).|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableOperationContextAsyncFlow`|Zablokování obslužných rutin, které jsou výsledkem omezení instancí vícenásobné služby na jedno vlákno provádění najednou.|.NET Framework 4.6.2|
|`Switch.System.ServiceModel.`<br/>`DisableUsingServicePointManagerSecurityProtocols`|Spolu s `Switch.System.Net.DontEnableSchUseStrongCrypto`, určuje, zda zabezpečení zpráv WCF používá protokoly TLS 1.1 a TLS 1.2.|Rozhraní .NET framework 4.7 |    
|`Switch.System.ServiceModel.`<br/>`UseSha1InMsmqEncryptionAlgorithm`|Určuje, zda je výchozí zprávu podpisový algoritmus pro zprávy služby MSMQ ve službě WCF SHA1 nebo SHA256.|Rozhraní .NET framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InPipeConnectionGetHashAlgorithm`|Určuje, zda WCF používá ke generování náhodné názvy pro pojmenované kanály SHA1 nebo hodnotu hash SHA256.|Rozhraní .NET framework 4.7.1|
|`Switch.System.ServiceProcess.`<br/>`DontThrowExceptionsOnStart`|Určuje, zda výjimky vydané na spuštění služby rozšířeny volající <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> metoda.|Rozhraní .NET framework 4.7.1|
|`Switch.System.Windows.Controls.Grid.`<br/>`StarDefinitionsCanExceedAvailableSpace` |Určuje, zda Windows Presentation Foundation platí staré algoritmus (`true`) nebo nového algoritmu (`false`) v přidělování místa pro \*-sloupce. Další informace najdete v tématu [omezení rizik: ovládání mřížky přidělení místa na sloupce hvězdičky](Mitigation:%20Grid%20Control's%20Space%20Allocation%20to%20Star-columns.md). |Rozhraní .NET framework 4.7 |
|`Switch.System.Windows.Controls.TabControl.`<br/>`SelectionPropertiesCanLagBehindSelectionChangedEvent`|Ovládací prvky, jestli selektor nebo na kartě řízení vždy aktualizace hodnota jeho vlastnosti vybrané hodnoty před vyvoláním výběru událost změněné.|Rozhraní .NET framework 4.7.1|
|`Switch.System.Windows.Forms.`<br />`DontSupportReentrantFilterMessage`|Výslovný nesouhlas kód, který umožňuje vlastní <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementace k bezpečně filtrovat zprávy, aniž by došlo k výjimce při <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> metoda je volána. Další informace najdete v tématu [omezení rizik: implementace vlastních IMessageFilter.PreFilterMessage](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).|.NET Framework 4.6.1|  
|`Switch.System.Windows.Input.Stylus.`<br/>`EnablePointerSupport`|Určuje, zda je volitelný `WM_POINTER`– na základě touch/pera zásobníku je povolena v aplikacích WPF. Další informace najdete v tématu [omezení rizik: na základě ukazatel Touch a podporu pera](Mitigation:%20Pointer-based%20Touch%20and%20Stylus%20Support.md) | 
|`Switch.System.Windows.Media.ImageSourceConverter.`<br/>`OverrideExceptionWithNullReferenceException`|Určuje, jestli starší verze [NullReferenceException](xref:System.NullReferenceException) je vyvolána místo výjimky, konkrétně určující příčinou výjimky (například [DirectoryNotFoundException](xref:System.IO.DirectoryNotFoundException) nebo [ FileNotFoundException](xref:System.IO.FileNotFoundException). Je určena pro použití v kódu, který závisí na zpracování [NullReferenceException](xref:System.NullReferenceException). | Rozhraní .NET framework 4.7 |
|`Switch.UseLegacyAccessibilityFeatures`|Ovládací prvky zda funkce usnadnění přístupu k dispozici od verze rozhraní .NET Framework 4.7.1 jsou povoleny nebo zakázány. | Rozhraní .NET framework 4.7.1 |
|`System.Xml.`<br /><br /> `IgnoreEmptyKeySequences`|Určuje, zda jsou ověření schématu XSD ignorovat prázdný posloupnosti kláves v složeného klíče. Další informace najdete v tématu [omezení rizik: ověřování schématu XML](~/docs/framework/migration-guide/mitigation-xml-schema-validation.md).|.NET Framework 4.6|  
  
> [!NOTE]
>  Místo přidávání `AppContextSwitchOverrides` element konfiguračního souboru aplikace, můžete také nastavit přepínače programově zavoláním `static` (v jazyku C#) nebo `Shared` (v jazyce Visual Basic) <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> metoda.  
  
 Vývojáři knihovny můžete také definovat vlastní přepínače se mají povolit volající pro vyjádření výslovného nesouhlasu změněné funkce byla zavedená v novějších verzích své knihovny. Další informace najdete v tématu <xref:System.AppContext> třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `AppContextSwitchOverrides` elementu, který chcete definovat přepínač kompatibility jednu aplikaci, `Switch.System.Globalization.NoAsyncCurrentCulture`, který brání předávaných mezi vláken ve volání asynchronních metod jazykovou verzi.  
  
```xml  
<configuration>  
   <runtime>  
      <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />  
   </runtime>  
</configuration>  
```  
  
 Následující příklad používá `AppContextSwitchOverrides` elementu, který chcete definovat dva přepínače kompatibility aplikací, `Switch.System.Globalization.NoAsyncCurrentCulture` a `Switch.System.IO.BlockLongPaths`. Všimněte si, že středníkem odděluje dvě dvojice název/hodnota.  
  
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
 [\<modul runtime > elementu](runtime-element.md)  
 [\<Konfigurace > elementu](../configuration-element.md)
