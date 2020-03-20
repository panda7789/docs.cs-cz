---
title: Novinky v rozhraní .NET Framework
ms.custom: updateeachrelease
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
ms.assetid: 1d971dd7-10fc-4692-8dac-30ca308fc0fa
ms.openlocfilehash: fa7138127379b069b646c4b2488d1973a3ddd628
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79143314"
---
# <a name="whats-new-in-net-framework"></a>Co je nového v rozhraní .NET Framework

Tento článek shrnuje klíčové nové funkce a vylepšení v následujících verzích rozhraní .NET Framework:

- [Rozhraní .NET Framework 4.8](#v48)
- [Rozhraní .NET 4.7.2](#v472)
- [Rozhraní .NET 4.7.1](#v471)
- [Rozhraní .NET Framework 4.7](#v47)
- [.NET Framework 4.6.2](#v462)
- [.NET Framework 4.6.1](#v461)
- [.NET 2015 a .NET Framework 4.6](#v46)
- [.NET Framework 4.5.2](#v452)
- [.NET Framework 4.5.1](#v451)
- [.NET Framework 4.5](#v45)

Tento článek neposkytuje komplexní informace o každé nové funkci a může se změnit. Obecné informace o rozhraní .NET Framework naleznete v tématu [Začínáme](../get-started/index.md). Podporované platformy naleznete v [tématu Systémové požadavky](../get-started/system-requirements.md). Odkazy ke stažení a pokyny k instalaci naleznete v [příručce k instalaci](../install/guide-for-developers.md).

> [!NOTE]
> Tým rozhraní .NET Framework také vydává funkce mimo pásmo s NuGet rozšířit podporu platformy a zavést nové funkce, jako jsou neměnné kolekce a simd povoleno vektorové typy. Další informace naleznete [v tématu Další knihovny tříd a rozhraní API](../additional-apis/index.md) a rozhraní [.NET Framework a Out-of-Band releases](../get-started/the-net-framework-and-out-of-band-releases.md).
> Podívejte se na [úplný seznam balíčků NuGet](https://www.nuget.org/profiles/dotnetframework) pro rozhraní .NET Framework.

<a name="v48" />

## <a name="introducing-net-framework-48"></a>Představujeme rozhraní .NET Framework 4.8

Rozhraní .NET Framework 4.8 vychází z předchozích verzí rozhraní .NET Framework 4.x přidáním mnoha nových oprav a několika nových funkcí a zároveň zůstává velmi stabilním produktem.

### <a name="downloading-and-installing-net-framework-48"></a>Stahování a instalace rozhraní .NET Framework 4.8

Rozhraní .NET Framework 4.8 si můžete stáhnout z následujících umístění:

- [Instalační služba rozhraní .NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48)

- [Net Framework 4.8 Offline instalační program](https://dotnet.microsoft.com/download/dotnet-framework/net48)

Rozhraní .NET Framework 4.8 lze nainstalovat do systému Windows 10, Windows 8.1, Windows 7 SP1 a odpovídajících serverových platforem počínaje aktualizací Windows Server 2008 R2 SP1. Rozhraní .NET Framework 4.8 můžete nainstalovat pomocí webového instalačního programu nebo offline instalačního programu. Doporučeným způsobem pro většinu uživatelů je použití webového instalačního programu.

Rozhraní .NET Framework 4.8 v sadě Visual Studio 2012 nebo novější můžete cílit instalací [sady .NET Framework 4.8 Developer Pack](https://go.microsoft.com/fwlink/?LinkId=2085167).

### <a name="whats-new-in-net-framework-48"></a>Co je nového v rozhraní .NET Framework 4.8

Rozhraní .NET Framework 4.8 zavádí nové funkce v následujících oblastech:

- [Základní třídy](#core48)
- [Windows Communication Foundation (WCF)](#wcf48)
- [Windows Presentation Foundation (WPF)](#wpf48)
- [Běžný jazyk runtime](#clr48)

Vylepšená přístupnost, která umožňuje aplikaci poskytovat odpovídající prostředí pro uživatele asistenční technologie, je i nadále hlavním zaměřením rozhraní .NET Framework 4.8. Informace o vylepšení usnadnění v rozhraní .NET Framework 4.8 naleznete [v tématu Co je nového v usnadnění přístupnosti v rozhraní .NET Framework](whats-new-in-accessibility.md).

<a name="core48" />

#### <a name="base-classes"></a>Základní třídy

**Snížený dopad FIPS na kryptografii**. V předchozích verzích rozhraní .NET Framework byly <xref:System.Security.Cryptography.SHA256Managed> spravovány <xref:System.Security.Cryptography.CryptographicException> třídy zprostředkovatele kryptografických služeb, například throw a když jsou systémové kryptografické knihovny konfigurovány v režimu FIPS. Tyto výjimky jsou vyvolány, protože spravované verze tříd kryptografického zprostředkovatele, na rozdíl od systémových kryptografických knihoven, neprošly certifikací FIPS (Federal Information Processing Standards) 140-2. Vzhledem k tomu, že několik vývojářů má své vývojové počítače v režimu FIPS, výjimky jsou běžně vyvolány v produkčních systémech.

Ve výchozím nastavení v aplikacích, které cílí na rozhraní .NET <xref:System.Security.Cryptography.CryptographicException> Framework 4.8, následující spravované třídy kryptografie již v tomto případě nepřihazují:

- <xref:System.Security.Cryptography.MD5Cng>
- <xref:System.Security.Cryptography.MD5CryptoServiceProvider>
- <xref:System.Security.Cryptography.RC2CryptoServiceProvider>
- <xref:System.Security.Cryptography.RijndaelManaged>
- <xref:System.Security.Cryptography.RIPEMD160Managed>
- <xref:System.Security.Cryptography.SHA256Managed>

Místo toho tyto třídy přesměrovat kryptografické operace do knihovny kryptografické systému. Tato změna účinně odstraňuje potenciálně matoucí rozdíl mezi vývojářskými prostředími a produkčními prostředími a umožňuje nativní mařivé součásti a spravované součásti pracovat v rámci stejné kryptografické zásady. Aplikace, které závisí na těchto výjimkách můžete obnovit `Switch.System.Security.Cryptography.UseLegacyFipsThrow` předchozí `true`chování nastavením AppContext přepínač na . Další informace naleznete v tématu [Spravované kryptografické třídy nevyvolání cryptographyException v režimu FIPS](../migration-guide/retargeting/4.7.2-4.8.md#managed-cryptography-classes-do-not-throw-a-cryptographyexception-in-fips-mode).

**Použití aktualizované verze ZLib**

Počínaje rozhraním .NET Framework 4.5 používá sestavení clrcompression.dll [ZLib](https://www.zlib.net), nativní externí knihovnu pro kompresi dat, aby bylo možné poskytnout implementaci pro algoritmus deflate. Rozhraní .NET Framework 4.8, clrcompression.dll je aktualizován o použití ZLib verze 1.2.11, který obsahuje několik klíčových vylepšení a oprav.

<a name="wcf48" />

#### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)

**Zavedení servicehealthbehavior**

Koncové body stavu jsou široce používány orchestračními nástroji ke správě služeb na základě jejich stavu. Kontroly stavu lze také použít pomocí nástrojů pro sledování ke sledování a poskytování oznámení o dostupnosti a výkonu služby.

**ServiceHealthBehavior** je chování služby WCF, které rozšiřuje <xref:System.ServiceModel.Description.IServiceBehavior>.  Při přidání <xref:System.ServiceModel.Description.ServiceDescription.Behaviors?displayProperty=nameWithType> do kolekce chování služby provádí následující akce:

- Vrátí stav služby s kódy odpovědí HTTP. V řetězci dotazu můžete zadat stavový kód HTTP pro požadavek sondy stavu HTTP/GET.

- Publikuje informace o stavu služby. Podrobnosti specifické pro službu, včetně stavu služby, počty omezení a kapacity `?health` lze zobrazit pomocí požadavku HTTP/GET s řetězcem dotazu. Snadný přístup k těmto informacím je důležité při řešení potíží s nechová WCF služby.

Existují dva způsoby, jak vystavit koncový bod stavu a publikovat informace o stavu služby WCF:

- Prostřednictvím kódu. Například:

  ```csharp
  ServiceHost host = new ServiceHost(typeof(Service1),
                     new Uri("http://contoso:81/Service1"));
  ServiceHealthBehavior healthBehavior =
      host.Description.Behaviors.Find<ServiceHealthBehavior>();
  healthBehavior ??= new ServiceHealthBehavior();
  host.Description.Behaviors.Add(healthBehavior);
  ```

  ```vb
  Dim host As New ServiceHost(GetType(Service1),
              New Uri("http://contoso:81/Service1"))
  Dim healthBehavior As ServiceHealthBehavior =
     host.Description.Behaviors.Find(Of ServiceHealthBehavior)()
  If healthBehavior Is Nothing Then
     healthBehavior = New ServiceHealthBehavior()
  End If
  host.Description.Behaviors.Add(healthBehavior)
  ```

- Pomocí konfiguračního souboru. Například:

  ```xml
  <behaviors>
    <serviceBehaviors>
      <behavior name="DefaultBehavior">
        <serviceHealth httpsGetEnabled="true"/>
      </behavior>
    </serviceBehaviors>
  </behaviors>
  ```

Stav služby lze dotazovat pomocí parametrů dotazu, `OnServiceFailure` `OnDispatcherFailure`jako `OnListenerFailure` `OnThrottlePercentExceeded`je například , , , a kód odpovědi HTTP lze zadat pro každý parametr dotazu. Pokud je pro parametr dotazu vynechán kód odpovědi HTTP, použije se ve výchozím nastavení kód odpovědi 503 HTTP. Například:

- Selhání služby:`https://contoso:81/Service1?health&OnServiceFailure=450`

  Stavový kód odpovědi 450 HTTP je vrácen, <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>když [ServiceHost.State](xref:System.ServiceModel.Channels.CommunicationObject.State) je větší než .
Parametry dotazu a příklady:

- OnDispatcherSelhání:`https://contoso:81/Service1?health&OnDispatcherFailure=455`

  Stavový kód 455 HTTP je vrácen, pokud je stav některého z dispečerů kanálu větší než <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>.

- Selhání naslouchací hospodařící síly:`https://contoso:81/Service1?health&OnListenerFailure=465`

  Stavový kód odpovědi 465 HTTP je vrácen, pokud je stav <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>některého z posluchačů kanálu větší než .

- OnThrottlePercentExceeded:`https://contoso:81/Service1?health&OnThrottlePercentExceeded= 70:350,95:500`

  Určuje procento {1 – 100}, které aktivuje odpověď a její kód odpovědi HTTP {200 – 599}. V tomto příkladu:

  - Pokud je procento větší než 95, je vrácen kód odpovědi 500 HTTP.

  - Pokud procento nebo mezi 70 a 95, 350 je vrácena.

  - V opačném případě je vráceno 200.

Stav služby lze zobrazit buď v HTML zadáním `https://contoso:81/Service1?health` řetězce dotazu jako nebo ve `https://contoso:81/Service1?health&Xml`formátu XML zadáním řetězce dotazu, jako je . Řetězec dotazu, jako `https://contoso:81/Service1?health&NoContent` je tomu však vrátí prázdnou stránku HTML.

<a name="wpf48" />

#### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**Vylepšení vysokého dpi**

V rozhraní .NET Framework 4.8 wpf přidává podporu pro sledování V2 DPI povědomí a škálování DPI ve smíšeném režimu. Další informace o [vývoji vysokého výkonu dpi desktopových aplikací v systému Windows](/windows/win32/hidpi/high-dpi-desktop-application-development-on-windows) naleznete v tématu Vývoj aplikací pro stolní počítače S Vysokým obsahem DPI.

Rozhraní .NET Framework 4.8 zlepšuje podporu hostovaných HWND a Windows Forms interoperace v aplikacích WPF s vysokým dpi na platformách, které podporují škálování DPI ve smíšeném režimu (počínaje aktualizací Windows 10 duben 2018). Při hostované HWNDs nebo Windows Forms ovládací prvky jsou vytvořeny jako okna s použitím míchaného režimu DPI pomocí volání [SetThreadDpiHostingBehavior](/windows/desktop/api/winuser/nf-winuser-setthreaddpihostingbehavior) a [SetThreadDpiAwarenessContext](/windows/desktop/api/winuser/nf-winuser-setthreaddpiawarenesscontext), mohou být hostovány v aplikaci V2 WPF per-monitor a jsou velikosti a škálování odpovídajícím způsobem. Takový hostovaný obsah není vykreslen v nativním DPI; místo toho operační systém škáluje hostovaný obsah na příslušnou velikost. Podpora pro režim povědomí DPI v2 monitorování také umožňuje WPF ovládací prvky, které mají být hostovány (tj. nadřazené) v nativním okně v aplikaci s vysokým DPI.

Chcete-li povolit podporu škálování s vysokým dpi ve smíšeném režimu, můžete nastavit následující přepínače [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) v konfiguračním souboru aplikace:

```xml
<runtime>
   <AppContextSwitchOverrides value = "Switch.System.Windows.DoNotScaleForDpiChanges=false; Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false"/>
</runtime>
```

<a name="clr48" />

#### <a name="common-language-runtime"></a>Běžný jazyk runtime

Runtime v rozhraní .NET Framework 4.8 obsahuje následující změny a vylepšení:

**Vylepšení kompilátoru JIT**. Kompilátor Just-in-time (JIT) v rozhraní .NET Framework 4.8 je založen na kompilátoru JIT v rozhraní .NET Core 2.1. Mnoho optimalizací a všechny opravy chyb provedené v kompilátoru .NET Core 2.1 JIT jsou zahrnuty v kompilátoru .NET Framework 4.8 JIT.

**zlepšení NGEN**. Doba runtime zlepšila správu paměti pro [nativní image generátoru](../tools/ngen-exe-native-image-generator.md) (NGEN) obrázky tak, aby data mapovaná z ngen bitové kopie nejsou rezidentní paměti. To snižuje plochu k dispozici pro útoky, které se pokoušejí spustit libovolný kód úpravou paměti, která bude spuštěna.

**Antimalwarové skenování pro všechna sestavení**. V předchozích verzích rozhraní .NET Framework modul runtime prohledá všechna sestavení načtená z disku pomocí programu Windows Defender nebo antimalwarového softwaru jiného výrobce. Sestavení načtená z jiných zdrojů, například <xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType> metodou, však nejsou kontrolována a mohou potenciálně obsahovat nezjištěný malware. Počínaje rozhraním .NET Framework 4.8 spuštěným v systému Windows 10 modul runtime spustí kontrolu antimalwarovými řešeními, která implementují [rozhraní AMSI (Antimalware Scan Interface).](/windows/desktop/AMSI/antimalware-scan-interface-portal)

<a name="v472" />

## <a name="whats-new-in-net-framework-472"></a>Co je nového v rozhraní .NET Framework 4.7.2

Rozhraní .NET Framework 4.7.2 obsahuje nové funkce v následujících oblastech:

- [Základní třídy](#core-472)
- [ASP.NET](#asp-net472)
- [Sítě](#net472)
- [SQL](#sql472)
- [WPF](#wpf472)
- [ClickOnce](#clickonce)

Trvalé zaměření v rozhraní .NET Framework 4.7.2 je lepší usnadnění přístupu, což umožňuje aplikaci poskytovat odpovídající prostředí pro uživatele asistenční technologie. Informace o vylepšení usnadnění v rozhraní .NET Framework 4.7.2 naleznete [v tématu Co je nového v usnadnění přístupnosti v rozhraní .NET Framework](whats-new-in-accessibility.md).

<a name="core-472" />

#### <a name="base-classes"></a>Základní třídy

Rozhraní .NET Framework 4.7.2 obsahuje velké množství kryptografických vylepšení, lepší podporu dekomprese archivů ZIP a další rozhraní API kolekce.

**Nové přetížení RSA. Vytvořit a DSA. Vytvořit**

Metody <xref:System.Security.Cryptography.DSA.Create(System.Security.Cryptography.DSAParameters)?displayProperty=nameWithType> <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> a umožňují zadat klíčové parametry při vytváření <xref:System.Security.Cryptography.DSA> <xref:System.Security.Cryptography.RSA> instancí nového nebo klíče. Umožňují nahradit kód takto:

```csharp
// Before .NET Framework 4.7.2
using (RSA rsa = RSA.Create())
{
   rsa.ImportParameters(rsaParameters);
   // Other code to execute using the RSA instance.
}
```

```vb
' Before .NET Framework 4.7.2
Using rsa = RSA.Create()
   rsa.ImportParameters(rsaParameters)
   ' Other code to execute using the rsa instance.
End Using
```

s kódem, jako je tento:

```csharp
// Starting with .NET Framework 4.7.2
using (RSA rsa = RSA.Create(rsaParameters))
{
   // Other code to execute using the rsa instance.
}
```

```vb
' Starting with .NET Framework 4.7.2
Using rsa = RSA.Create(rsaParameters)
   ' Other code to execute using the rsa instance.
End Using
```

Metody <xref:System.Security.Cryptography.DSA.Create(System.Int32)?displayProperty=nameWithType> <xref:System.Security.Cryptography.RSA.Create(System.Int32)?displayProperty=nameWithType> a umožňují generovat <xref:System.Security.Cryptography.DSA> <xref:System.Security.Cryptography.RSA> nové nebo klíče s určitou velikostí klíče. Například:

```csharp
using (DSA dsa = DSA.Create(2048))
{
   // Other code to execute using the dsa instance.
}
```

```vb
Using dsa = DSA.Create(2048)
   ' Other code to execute using the dsa instance.
End Using
```

**Konstruktory Rfc2898DeriveBytes přijímají název algoritmu hash**

Třída <xref:System.Security.Cryptography.Rfc2898DeriveBytes> má tři nové konstruktory s parametrem, <xref:System.Security.Cryptography.HashAlgorithmName> který identifikuje algoritmus HMAC pro použití při odvození klíčů. Namísto použití SHA-1 by vývojáři měli používat hmac založený na SHA-2, jako je SHA-256, jak je znázorněno v následujícím příkladu:

```csharp
private static byte[] DeriveKey(string password, out int iterations, out byte[] salt,
                                out HashAlgorithmName algorithm)
{
   iterations = 100000;
   algorithm = HashAlgorithmName.SHA256;

   const int SaltSize = 32;
   const int DerivedValueSize = 32;

   using (Rfc2898DeriveBytes pbkdf2 = new Rfc2898DeriveBytes(password, SaltSize,
                                                             iterations, algorithm))
   {
      salt = pbkdf2.Salt;
      return pbkdf2.GetBytes(DerivedValueSize);
   }
}
```

```vb
Private Shared Function DeriveKey(password As String, ByRef iterations As Integer,
                                  ByRef salt AS Byte(), ByRef algorithm As HashAlgorithmName) As Byte()
   iterations = 100000
   algorithm = HashAlgorithmName.SHA256

   Const SaltSize As Integer = 32
   Const  DerivedValueSize As Integer = 32

   Using pbkdf2 = New Rfc2898DeriveBytes(password, SaltSize, iterations, algorithm)
      salt = pbkdf2.Salt
      Return pbkdf2.GetBytes(DerivedValueSize)
   End Using
End Function
```

**Podpora dočasných kláves**

Import PFX může volitelně načíst soukromé klíče přímo z paměti, obcházet pevný disk.Při nový <xref:System.Security.Cryptography.X509Certificates.X509KeyStorageFlags.EphemeralKeySet?displayProperty=nameWithType> příznak je <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> zadán v konstruktoru nebo <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.Import%2A?displayProperty=nameWithType> jeden z přetížení metody, soukromé klíče budou načteny jako dočasné klíče. Tím zabráníte, aby byly klíče viditelné na disku. Nicméně:

- Vzhledem k tomu, že klíče nejsou trvalé na disk, certifikáty načtené tímto příznakem nejsou vhodné kandidáty přidat do X509Store.

- Klíče načtené tímto způsobem jsou téměř vždy načteny přes Windows CNG. Proto volající musí přistupovat k soukromému klíči voláním rozšiřujících metod, jako je [například cert. GetRSAPrivateKey()](xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey%2A). Vlastnost <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> nefunguje.

- Vzhledem <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> k tomu, že starší vlastnost nefunguje s certifikáty, vývojáři by měli před přepnutím na dočasné klíče provádět přísné testování.

**Programové vytváření žádostí o podpis podpisu certifikace PKCS# 10 a certifikátů veřejného klíče X.509**

Počínaje rozhraním .NET Framework 4.7.2 mohou úlohy generovat žádosti o podepisování certifikátů (CSRs), což umožňuje, aby generování žádostí o certifikát bylo připraveno do existujících nástrojů. To je často užitečné v testovacích scénářích.

Další informace a příklady kódu naleznete v tématu Programatické vytváření žádostí o podpis certifikátu PKCS#10 a certifikátů veřejného klíče X.509 v [blogu .NET](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).

**Noví členové SignerInfo**

Počínaje rozhraním .NET Framework <xref:System.Security.Cryptography.Pkcs.SignerInfo> 4.7.2, třída zveřejňuje další informace o podpisu. Můžete načíst hodnotu <xref:System.Security.Cryptography.Pkcs.SignerInfo.SignatureAlgorithm?displayProperty=fullName> vlastnosti k určení podpisu algoritmus používaný podepisující osoby. <xref:System.Security.Cryptography.Pkcs.SignerInfo.GetSignature%2A?displayProperty=nameWithType>můžete být voláni, abyste získali kopii kryptografického podpisu pro tohoto podepisujícího.

**Ponechání zabaleného datového proudu otevřeného po vyřazení CryptoStream**

Počínaje rozhraním .NET Framework 4.7.2 má <xref:System.Security.Cryptography.CryptoStream> třída <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> další konstruktor, který umožňuje nezavírat zalomený datový proud.Chcete-li po nechat zabalený datový proud otevřený po uvolnění <xref:System.Security.Cryptography.CryptoStream> instance, zavolejte nový <xref:System.Security.Cryptography.CryptoStream> konstruktor takto:

```csharp
var cStream = new CryptoStream(stream, transform, mode, leaveOpen: true);
```

```vb
Dim cStream = New CryptoStream(stream, transform, mode, leaveOpen:=true)
```

**Dekompresní změny v DeflateStream**

Počínaje rozhraním .NET Framework 4.7.2 se implementace <xref:System.IO.Compression.DeflateStream> dekompresních operací ve třídě ve výchozím nastavení změnila na nativní rozhraní API systému Windows. Obvykle to má za následek podstatné zlepšení výkonu.

Podpora dekomprese pomocí rozhraní API systému Windows je ve výchozím nastavení povolena pro aplikace, které cílí na rozhraní .NET Framework 4.7.2. Aplikace, které cílí na starší verze rozhraní .NET Framework, ale jsou spuštěny v rozhraní .NET Framework 4.7.2, se mohou do tohoto chování přihlásit přidáním následujícího [přepínače AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do konfiguračního souboru aplikace:

```xml
<AppContextSwitchOverrides value="Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=false" />
```

**Další kolekce API**

Rozhraní .NET Framework 4.7.2 přidává do <xref:System.Collections.Generic.SortedSet%601> typů <xref:System.Collections.Generic.HashSet%601> a řadu nových rozhraní API. Mezi ně patří:

- `TryGetValue`metody, které rozšiřují vzor try používaný v jiných typech kolekcí na tyto dva typy. Existují tyto metody:

  - [veřejné bool HashSet\<T>. TryGetValue(T equalValue, out T actualValue)](xref:System.Collections.Generic.SortedSet%601.TryGetValue%2A)
  - [veřejné bool SortedSet\<T>. TryGetValue(T equalValue, out T actualValue)](xref:System.Collections.Generic.SortedSet%601.TryGetValue%2A)

- `Enumerable.To*`metody rozšíření, které převedou <xref:System.Collections.Generic.HashSet%601>kolekci na :

  - [veřejné statické HashSet\<TSource>\<ToHashSet TSource\<> (tento IEnumerable TSource> zdroj)](xref:System.Linq.Enumerable.ToHashSet%2A)
  - [veřejné\<statické HashSet TSource>\<ToHashSet TSource\<> (tento IEnumerable\<TSource> zdroj, IEqualityComparer TSource> porovnávání)](xref:System.Linq.Enumerable.ToHashSet%2A)

- Nové <xref:System.Collections.Generic.HashSet%601> konstruktory, které umožňují nastavit kapacitu kolekce, což přináší výhodu výkonu, <xref:System.Collections.Generic.HashSet%601> když znáte velikost předem:

  - [veřejná HashSet(int kapacita)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32))
  - [veřejné HashSet (int kapacita, IEqualityComparer\<T> porovnávání)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32,System.Collections.Generic.IEqualityComparer%7B%600%7D))

Třída <xref:System.Collections.Concurrent.ConcurrentDictionary%602> obsahuje nové přetížení <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> a <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> metody načíst hodnotu ze slovníku nebo přidat, pokud není nalezen a přidat hodnotu do slovníku nebo aktualizovat, pokud již existuje.

```csharp
public TValue AddOrUpdate<TArg>(TKey key, Func<TKey, TArg, TValue> addValueFactory, Func<TKey, TValue, TArg, TValue> updateValueFactory, TArg factoryArgument)

public TValue GetOrAdd<TArg>(TKey key, Func<TKey, TArg, TValue> valueFactory, TArg factoryArgument)
```

```vb
Public AddOrUpdate(Of TArg)(key As TKey, addValueFactory As Func(Of TKey, TArg, TValue), updateValueFactory As Func(Of TKey, TValue, TArg, TValue), factoryArgument As TArg) As TValue

Public GetOrAdd(Of TArg)(key As TKey, valueFactory As Func(Of TKey, TArg, TValue), factoryArgument As TArg) As TValue
```

<a name="asp-net472" />

#### <a name="aspnet"></a>ASP.NET

**Podpora vkládání závislostí ve webových formulářích**

[Vkládání závislostí (DI)](/aspnet/core/fundamentals/dependency-injection#overview-of-dependency-injection) odděluje objekty a jejich závislosti tak, aby kód objektu již není třeba změnit jen proto, že se změnila závislost. Při vývoji ASP.NET aplikací, které cílí na rozhraní .NET Framework 4.7.2, můžete:

- Použijte setter založené, založené na rozhraní a vkládání na základě konstruktoru v [obslužné rutiny a moduly](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)), [Page instance](xref:System.Web.UI.Page)a [uživatelské ovládací prvky](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) ASP.NET projekty webových aplikací.

- Použití vkládání založené na setteru a rozhraní v [obslužných rutinách a modulech](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)), [instancích Page](xref:System.Web.UI.Page)a [uživatelských ovládacích prvcích](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) ASP.NET projekty webu.

- Připojte různé rámce vkládání závislostí.

**Podpora souborů cookie stejného webu**

[SameSite](https://tools.ietf.org/html/draft-west-first-party-cookies-07) brání prohlížeči v odesílání souboru cookie spolu s požadavkem na více stránek. Rozhraní .NET Framework 4.7.2 přidá <xref:System.Web.HttpCookie.SameSite?displayProperty=nameWithType> <xref:System.Web.SameSiteMode?displayProperty=nameWithType> vlastnost, jejíž hodnota je člen výčtu. Pokud je <xref:System.Web.SameSiteMode.Strict?displayProperty=nameWithType> jeho <xref:System.Web.SameSiteMode.Lax?displayProperty=nameWithType>hodnota nebo `SameSite` , ASP.NET přidá atribut do hlavičky set-cookie. Podpora Stejnéstránky se <xref:System.Web.HttpCookie> vztahuje na objekty, stejně jako na <xref:System.Web.Security.FormsAuthentication> a <xref:System.Web.SessionState> cookies.

Můžete nastavit SameSite <xref:System.Web.HttpCookie> pro objekt takto:

```csharp
var c = new HttpCookie("secureCookie", "same origin");
c.SameSite = SameSiteMode.Lax;
```

```vb
Dim c As New HttpCookie("secureCookie", "same origin")
c.SameSite = SameSiteMode.Lax
```

Soubory cookie SameSite můžete také nakonfigurovat na úrovni aplikace úpravou souboru web.config:

```xml
<system.web>
   <httpCookies sameSite="Strict" />
</system.web>
```

Můžete přidat SameSite <xref:System.Web.Security.FormsAuthentication> <xref:System.Web.SessionState> pro a cookies úpravou webového konfiguračního souboru:

```xml
<system.web>
   <authentication mode="Forms">
      <forms cookieSameSite="Lax">
         <!-- ...   -->
      </forms>
   <authentication />
   <sessionState cookieSameSite="Lax"></sessionState>
</system.web>
```

<a name="net472" />

#### <a name="networking"></a>Sítě

**Implementace vlastností HttpClientHandler**

Rozhraní .NET Framework 4.7.1 <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> přidalo do třídy osm vlastností. Nicméně, dva <xref:System.PlatformNotSupportedException>hodil . Rozhraní .NET Framework 4.7.2 nyní poskytuje implementaci těchto vlastností. Mezi vlastnosti patří:

- <xref:System.Net.Http.HttpClientHandler.CheckCertificateRevocationList>
- <xref:System.Net.Http.HttpClientHandler.SslProtocols>

<a name="sql472" />

#### <a name="sqlclient"></a>SQLClient

**Podpora univerzálního ověřování azure služby Azure AD a vícefaktorového ověřování**

Rostoucí požadavky na dodržování předpisů a zabezpečení vyžadují, aby mnoho zákazníků používalo vícefaktorové ověřování (MFA). Kromě toho aktuální osvědčené postupy odradit včetně uživatelských hesel přímo v připojovacích řetězcích. Pro podporu těchto změn rozšiřuje rozhraní .NET Framework 4.7.2 [připojovací řetězce SQLClient](xref:System.Data.SqlClient.SqlConnection.ConnectionString) přidáním nové hodnoty Active Directory Interactive pro existující klíčové slovo Ověřování pro podporu ověřování vícefaktorové ověřování a [ověřování Azure AD](/azure/sql-database/sql-database-aad-authentication-configure). Nová interaktivní metoda podporuje nativní a federované uživatele Azure AD, stejně jako uživatele hosta Azure AD. Při použití této metody ověřování MFA uložené službou Azure AD je podporována pro databáze SQL. Kromě toho proces ověřování požaduje heslo uživatele dodržovat doporučené postupy zabezpečení.

V předchozích verzích rozhraní .NET Framework <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryPassword?displayProperty=nameWithType> připojení <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryIntegrated?displayProperty=nameWithType> SQL podporovalo pouze možnosti a. Oba tyto jsou součástí neinteraktivní protokol [ADAL](/azure/active-directory/develop/active-directory-authentication-libraries), který nepodporuje vícefaktorové. S novou <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryInteractive?displayProperty=nameWithType> možností, sql připojení podporuje Vícefaktorové ověřování, stejně jako existující metody ověřování (heslo a integrované ověřování), který umožňuje uživatelům zadávat uživatelská hesla interaktivně bez uchování hesla v připojovacím řetězci.

Další informace a příklad naleznete v tématu SQL -- Azure AD Univerzální a vícefaktorové ověřování Support" v [.NET Blog](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).

**Podpora pro vždy šifrované verze 2**

NET Framework 4.7.2 přidává podpěry pro enklávu vždy šifrované. Původní verze always encrypted je technologie šifrování na straně klienta, ve které šifrovací klíče nikdy neopustí klienta. V enklávě založené vždy šifrované, klient může volitelně odeslat šifrovací klíče do zabezpečené enklávy, což je zabezpečené výpočetní entity, které lze považovat za součást SQL Server, ale že kód SQL Server nelze manipulovat s. Pro podporu enklávy založené vždy šifrované, .NET Framework 4.7.2 přidá následující typy a členy <xref:System.Data.SqlClient> do oboru názvů:

- <xref:System.Data.SqlClient.SqlConnectionStringBuilder.EnclaveAttestationUrl?displayProperty=nameWithType>, který určuje Uri pro enklávu vždy šifrované.

- <xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider>, což je abstraktní třída, ze které jsou odvozeny všechny zprostředkovatele enklávy.

- <xref:System.Data.SqlClient.SqlEnclaveSession>, který zapouzdřuje stav pro danou enklávu.

- <xref:System.Data.SqlClient.SqlEnclaveAttestationParameters>, který poskytuje parametry atestace používané sql serverem k získání informací potřebných ke spuštění určitého protokolu osazení.

Konfigurační soubor aplikace pak určuje <xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider?displayProperty=nameWithType> konkrétní implementaci abstraktní třídy, která poskytuje funkce pro zprostředkovatele enklávy. Například:

```xml
<configuration>
  <configSections>
    <section name="SqlColumnEncryptionEnclaveProviders" type="System.Data.SqlClient.SqlColumnEncryptionEnclaveProviderConfigurationSection,System.Data,Version=4.0.0.0,Culture=neutral,PublicKeyToken=b77a5c561934e089"/>
  </configSections>
  <SqlColumnEncryptionEnclaveProviders>
    <providers>
      <add name="Azure" type="Microsoft.SqlServer.Management.AlwaysEncrypted.AzureEnclaveProvider,MyApp"/>
      <add name="HGS" type="Microsoft.SqlServer.Management.AlwaysEncrypted.HGSEnclaveProvider,MyApp" />
    </providers>
  </SqlColumnEncryptionEnclaveProviders >
</configuration>
```

Základní tok enklávy vždy šifrované je:

1. Uživatel vytvoří alwaysencrypted připojení k SQL Server, který podporoval enklávy založené vždy šifrované. Řidič kontaktuje atestační službu, aby se ujistil, že se připojuje k pravé enklávě.

1. Po otestování enklávy ovladač vytvoří zabezpečený kanál se zabezpečenou enklávou hostovoci hostovoci na serveru SQL Server.

1. Ovladač sdílí šifrovací klíče autorizované klientem se zabezpečenou enklávou po dobu trvání připojení SQL.

<a name="wpf472" />

#### <a name="windows-presentation-foundation"></a>Windows Presentation Foundation

**Hledání ResourceDictionaries podle zdroje**

Počínaje rozhraním .NET Framework 4.7.2 může <xref:System.Windows.Xps.Packaging.IXpsFixedPageReader.ResourceDictionaries> diagnostický pomocník vyhledat ty, které byly vytvořeny z daného zdroje Uri.(Tato funkce je určena diagnostickými asistenty, nikoli produkčními aplikacemi.) Diagnostický asistent, jako je například visual studio "Upravit a pokračovat" zařízení umožňuje jeho uživateli upravit ResourceDictionary s úmyslem, že změny se použijí na spuštěné aplikace. Jedním z kroků v dosažení tohoto je nalezení všech ResourceDictionaries, které spuštěná aplikace vytvořila ze slovníku, který je upravován. Aplikace může například deklarovat ResourceDictionary, jehož obsah je zkopírován z daného zdroje URI:

```xml
<ResourceDictionary Source="MyRD.xaml">
```

Diagnostický pomocník, který uetuje původní značky v *MyRD.xaml* můžete použít novou funkci k vyhledání slovníku.Tato funkce je implementována <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetResourceDictionariesForSource%2A?displayProperty=nameWithType>novou statickou metodou . Diagnostický asistent volá novou metodu pomocí absolutní Uri, který identifikuje původní značky, jak je znázorněno na následujícím kódu:

```csharp
IEnumerable<ResourceDictionary> dictionaries = ResourceDictionaryDiagnostics.GetResourceDictionariesForSource(new Uri("pack://application:,,,/MyApp;component/MyRD.xaml"));
```

```vb
Dim dictionaries As IEnumerable(Of ResourceDictionary) = ResourceDictionaryDiagnostics.GetResourceDictionariesForSource(New Uri("pack://application:,,,/MyApp;component/MyRD.xaml"))
```

Metoda vrátí prázdný výčt, <xref:System.Windows.Diagnostics.VisualDiagnostics> pokud není [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)  povolena a je nastavena proměnná prostředí.

**Hledání resourcedictionary vlastníků**

Počínaje rozhraním .NET Framework 4.7.2 může diagnostický asistent <xref:Windows.UI.Xaml.ResourceDictionary>vyhledat vlastníky daného .(Tato funkce je určena pro diagnostické asistenty a nikoli pro produkční aplikace.) Vždy, když je <xref:Windows.UI.Xaml.ResourceDictionary>provedena změna , WPF automaticky vyhledá všechny [odkazy DynamicResource,](../wpf/advanced/dynamicresource-markup-extension.md) které mohou být ovlivněny změnou.

Diagnostický asistent, jako je například visual studio "Upravit a pokračovat" zařízení může chtít rozšířit to pro zpracování [staticresource](../wpf/advanced/staticresource-markup-extension.md) odkazy. Prvním krokem v tomto procesu je najít vlastníky slovníku; to znamená najít všechny objekty, jejichž `Resources` vlastnost odkazuje na slovník (buď <xref:System.Windows.ResourceDictionary.MergedDictionaries?displayProperty=nameWithType> přímo, nebo nepřímo prostřednictvím vlastnosti). Tři nové statické metody <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics?displayProperty=nameWithType> implementované na třídu, jeden `Resources` pro každý základní typy, které má vlastnost, podporují tento krok:

- [`public static IEnumerable<FrameworkElement> GetFrameworkElementOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetFrameworkElementOwners%2A)

- [`public static IEnumerable<FrameworkContentElement> GetFrameworkContentElementOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetFrameworkContentElementOwners%2A)

- [`public static IEnumerable<Application> GetApplicationOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetApplicationOwners%2A)

Tyto metody vrátí prázdný výčt, <xref:System.Windows.Diagnostics.VisualDiagnostics> pokud [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)  není povolena a je nastavena proměnná prostředí.

**Hledání odkazů na statickou prostředek**

Diagnostický pomocník nyní může přijímat oznámení při každém vyřešení odkazu [staticresource.](../wpf/advanced/staticresource-markup-extension.md)(Funkce je určena pro diagnostické asistenty, nikoli produkční aplikace.) Diagnostický asistent, jako je například visual studio "Upravit a pokračovat" zařízení může chtít aktualizovat <xref:Windows.UI.Xaml.ResourceDictionary> všechna použití prostředku při jeho hodnota v změně. WPF to provádí automaticky pro [odkazy DynamicResource,](../wpf/advanced/dynamicresource-markup-extension.md) ale záměrně tak nečiní pro [odkazy StaticResource.](../wpf/advanced/staticresource-markup-extension.md) Počínaje rozhraním .NET Framework 4.7.2 může diagnostický pomocník použít tato oznámení k vyhledání těchto použití statického prostředku.

Oznámení je implementováno <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.StaticResourceResolved?displayProperty=nameWithType> novou událostí:

```csharp
public static event EventHandler<StaticResourceResolvedEventArgs> StaticResourceResolved;
```

```vb
Public Shared Event StaticResourceResolved As EventHandler(Of StaticResourceResolvedEventArgs)
```

Tato událost je vyvolána vždy, když runtime řeší odkaz [StaticResource.](../wpf/advanced/staticresource-markup-extension.md)Argumenty <xref:System.Windows.Diagnostics.StaticResourceResolvedEventArgs> popisují řešení a označují objekt a vlastnost, které jsou <xref:Windows.UI.Xaml.ResourceDictionary> hostitelem [staticresource](../wpf/advanced/staticresource-markup-extension.md) odkaz a a klíč použitý pro řešení:

```csharp
public class StaticResourceResolvedEventArgs : EventArgs
{
   public Object TargetObject { get; }

   public Object TargetProperty { get; }

   public ResourceDictionary ResourceDictionary { get; }

   public object ResourceKey { get; }
}
```

```vb
Public Class StaticResourceResolvedEventArgs : Inherits EventArgs
   Public ReadOnly Property TargetObject As Object
   Public ReadOnly Property TargetProperty As Object
   Public ReadOnly Property ResourceDictionary As ResourceDictionary
   Public ReadOnly Property ResourceKey As Object
End Class
```

Událost není vyvolána (a `add` jeho přistupující ho je ignorován), pokud <xref:System.Windows.Diagnostics.VisualDiagnostics> není povolena a [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)  je nastavena proměnná prostředí.

#### <a name="clickonce"></a>ClickOnce

Aplikace podporující HDPI pro Windows Forms, Windows Presentation Foundation (WPF) a Visual Studio Tools for Office (VSTO) lze nasadit pomocí ClickOnce. Pokud je v manifestu aplikace nalezena následující položka, nasazení bude úspěšné v rámci rozhraní .NET Framework 4.7.2:

```xml
<windowsSettings>
   <dpiAware xmlns="http://schemas.microsoft.com/SMI/2005/WindowsSettings">true</dpiAware>
</windowsSettings>
```

Pro aplikaci Windows Forms předchozí řešení nastavení povědomí O DPI v konfiguračním souboru aplikace, nikoli manifest u aplikace již není nutné pro nasazení ClickOnce úspěšné.

<a name="v471" />

## <a name="whats-new-in-net-framework-471"></a>Co je nového v rozhraní .NET Framework 4.7.1

Rozhraní .NET Framework 4.7.1 obsahuje nové funkce v následujících oblastech:

- [Základní třídy](#core471)
- [Common language runtime (CLR)](#clr)
- [Sítě](#net471)
- [ASP.NET](#asp-net471)

Kromě toho hlavní zaměření v rozhraní .NET Framework 4.7.1 je lepší přístupnost, která umožňuje aplikaci poskytovat odpovídající prostředí pro uživatele asistenční technologie. Informace o vylepšení usnadnění v rozhraní .NET Framework 4.7.1 naleznete [v tématu Co je nového v usnadnění přístupnosti v rozhraní .NET Framework](whats-new-in-accessibility.md).

<a name="core471" />

#### <a name="base-classes"></a>Základní třídy

**Podpora pro standard .NET 2.0**

[Standard .NET](../../standard/net-standard.md) definuje sadu rozhraní API, která musí být k dispozici pro každou implementaci rozhraní .NET, která podporuje tuto verzi standardu. Rozhraní .NET Framework 4.7.1 plně podporuje rozhraní .NET Standard 2.0 a přidává [přibližně 200 rozhraní API,](https://github.com/dotnet/standard/blob/master/src/netstandard/src/ApiCompatBaseline.net461.txt) která jsou definována v rozhraní .NET Standard 2.0 a chybí v rozhraní .NET Framework 4.6.1, 4.6.2 a 4.7. (Všimněte si, že tyto verze rozhraní .NET Framework podporují rozhraní .NET Standard 2.0 pouze v případě, že jsou v cílovém systému nasazeny také další soubory podpory standardu .NET.) Další informace naleznete v tématu "BCL - .NET Standard 2.0 Support" v blogu [.NET Framework 4.7.1 Runtime a Compiler Features.](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/)

**Podpora pro tvůrce konfigurací**

Tvůrce konfigurace umožňují vývojářům injektáponovat a vytvářet nastavení konfigurace pro aplikace dynamicky za běhu. Vlastní konfigurátory konfigurace lze použít k úpravě existujících dat v konfigurační části nebo k vytvoření oddílu konfigurace zcela od začátku. Bez konfigurátorů jsou soubory .config statické a jejich nastavení jsou definována někdy před spuštěním aplikace.

Chcete-li vytvořit vlastní tvůrce konfigurace, odvodit tvůrce z abstraktní <xref:System.Configuration.ConfigurationBuilder> třídy a přepsat jeho <xref:System.Configuration.ConfigurationBuilder.ProcessConfigurationSection%2A?displayProperty=nameWithType> a <xref:System.Configuration.ConfigurationBuilder.ProcessRawXml%2A?displayProperty=nameWithType>. V souboru .config také definujete své tvůrce. Další informace naleznete v části "Konfigurační stavitelé" v příspěvku blogu [.NET Framework 4.7.1 ASP.NET a funkce konfigurace.](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/)

**Detekce funkcí za běhu**

Třída <xref:System.Runtime.CompilerServices.RuntimeFeature?displayProperty=nameWithType> poskytuje mechanismus pro určení, zda je předdefinovaná funkce podporována v dané implementaci rozhraní .NET v době kompilace nebo běhu. V době kompilace může kompilátor zkontrolovat, zda existuje zadané pole, aby zjistil, zda je funkce podporována; Pokud ano, může vyzařovat kód, který využívá této funkce. Za běhu aplikace může volat <xref:System.Runtime.CompilerServices.RuntimeFeature.IsSupported%2A?displayProperty=nameWithType> metodu před vyzařováním kódu za běhu. Další informace naleznete [v tématu Přidání pomocné metody k popisu funkcí podporovaných modulem runtime](https://github.com/dotnet/corefx/issues/17116).

**Typy řazené kolekce členů hodnoty lze serializovat**

Počínaje rozhraním .NET Framework 4.7.1 <xref:System.ValueTuple?displayProperty=nameWithType> a přidruženými obecnými typy jsou označeny jako [serializovatelné](xref:System.SerializableAttribute), což umožňuje binární serializaci. To by mělo usnadnit migraci <xref:System.Tuple%603> typů <xref:System.Tuple%604>tuple, například a , hodnotu řazené kolekce členů. Další informace naleznete v tématu "Kompilátor – ValueTuple je serializovatelný" v [.NET Framework 4.7.1 Runtime a compiler funkce](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blogu.

**Podpora odkazů jen pro čtení**

Rozhraní .NET Framework 4.7.1 přidává rozhraní <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute?displayProperty=nameWithType>. Tento atribut se používá kompilátory jazyka označit členy, kteří mají jen pro čtení ref návratové typy nebo parametry. Další informace naleznete v tématu "Kompilátor -- podpora pro ReadOnlyReferences" v [.NET Framework 4.7.1 Runtime a compiler funkce](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blogu. Informace o vrácené hodnoty ref naleznete v [tématu ref vrácené hodnoty a ref locals (C# Guide)](../../csharp/programming-guide/classes-and-structs/ref-returns.md) a [ref vrácené hodnoty (Visual Basic)](../../visual-basic/programming-guide/language-features/procedures/ref-return-values.md).

<a name="clr" />

#### <a name="common-language-runtime-clr"></a>Common language runtime (CLR)

**Vylepšení výkonu uvolňování paměti**

Změny uvolňování paměti (GC) v rozhraní .NET Framework 4.7.1 zlepšit celkový výkon, zejména pro přidělení haldy velkých objektů (LOH). V rozhraní .NET Framework 4.7.1 samostatné zámky se používají pro malé objekty haldy (SOH) a LOH přidělení, který umožňuje přidělení LOH dojít při pozadí GC je zametání SOH. V důsledku toho aplikace, které dělají velký počet přidělení LOH by měl vidět snížení konfliktu zámek přidělení a lepší výkon. Další informace naleznete v části "Runtime -- GC vylepšení výkonu" v [.NET Framework 4.7.1 Runtime a compiler funkce](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blogu.

<a name="net471"/>

#### <a name="networking"></a>Sítě

**Sha-2 podpora message.hashAlgorithm**

V rozhraní .NET Framework 4.7 <xref:System.Messaging.Message.HashAlgorithm%2A?displayProperty=nameWithType> a starších <xref:System.Messaging.HashAlgorithm.Md5?displayProperty=nameWithType> <xref:System.Messaging.HashAlgorithm.Sha?displayProperty=nameWithType> verzích vlastnost podporuje hodnoty a pouze. Počínaje rozhraním .NET Framework 4.7.1, <xref:System.Messaging.HashAlgorithm.Sha256?displayProperty=nameWithType>, <xref:System.Messaging.HashAlgorithm.Sha384?displayProperty=nameWithType>, a <xref:System.Messaging.HashAlgorithm.Sha512?displayProperty=nameWithType> jsou také podporovány. Zda je tato hodnota skutečně použita, závisí <xref:System.Messaging.Message> na službě MSMQ, protože samotná instance neprovádí žádné hodnoty, ale jednoduše předává hodnoty službě MSMQ. Další informace naleznete v části "Podpora SHA-2 pro Message.HashAlgorithm" v [rozhraní .NET Framework 4.7.1 ASP.NET a funkce konfigurace](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blogu.

<a name="asp-net471" />

#### <a name="aspnet"></a>ASP.NET

**Kroky spuštění v ASP.NET aplikacích**

ASP.NET zpracovává požadavky v předdefinovaném kanálu, který zahrnuje 23 událostí. ASP.NET provede každou obslužnou rutinu události jako krok spuštění. Ve verzích ASP.NET až .NET Framework 4.7, ASP.NET nemůže tok kontextu spuštění z důvodu přepínání mezi nativní a spravované podprocesy. Místo toho ASP.NET selektivně proudí pouze <xref:System.Web.HttpContext>. Počínaje rozhraním .NET Framework 4.7.1 <xref:System.Web.HttpApplication.OnExecuteRequestStep(System.Action{System.Web.HttpContextBase,System.Action})?displayProperty=nameWithType> metoda také umožňuje modulům obnovit okolní data. Tato funkce je zaměřena na knihovny týkající se trasování, profilování, diagnostiky nebo transakcí, které se starají o tok provádění aplikace. Další informace naleznete v příspěvku blogu "ASP.NET spuštění kroku" v [ASP.NET rozhraní .NET Framework 4.7.1 a funkce konfigurace.](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/)

**ASP.NET analýza httpcookie**

Rozhraní .NET Framework 4.7.1 <xref:System.Web.HttpCookie.TryParse%2A?displayProperty=nameWithType>obsahuje novou metodu , která <xref:System.Web.HttpCookie> poskytuje standardizovaný způsob vytvoření objektu z řetězce a přesné přiřazení hodnot souborů cookie, jako je datum vypršení platnosti a cesta. Další informace naleznete v tématu "ASP.NET httpcookie analýzy" v [rozhraní .NET Framework 4.7.1 ASP.NET a funkce konfigurace](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blogu.

**Možnosti hash SHA-2 pro přihlašovací údaje pro ověřování ASP.NET formulářů**

V rozhraní .NET Framework 4.7 a starších verzích ASP.NET vývojářům povolily ukládat pověření uživatelů s zahálčenými hesly v konfiguračních souborech pomocí MD5 nebo SHA1. Počínaje rozhraním .NET Framework 4.7.1 podporuje ASP.NET také nové zabezpečené možnosti hash SHA-2, jako jsou SHA256, SHA384 a SHA512. SHA1 zůstává výchozí a výchozí algoritmus hash, který není výchozí, lze definovat v konfiguračním souboru webu. Například:

```xml
<system.web>
    <authentication mode="Forms">
        <forms loginUrl="~/login.aspx">
          <credentials passwordFormat="SHA512">
            <user name="jdoe" password="6D003E98EA1C7F04ABF8FCB375388907B7F3EE06F278DB966BE960E7CBBD103DF30CA6D61F7E7FD981B2E4E3A64D43C836A4BEDCA165C33B163E6BCDC538A664" />
          </credentials>
        </forms>
    </authentication>
</system.web>
```

<a name="v47" />

## <a name="whats-new-in-net-framework-47"></a>Co je nového v rozhraní .NET Framework 4.7

Rozhraní .NET Framework 4.7 obsahuje nové funkce v následujících oblastech:

- [Základní třídy](#Core47)
- [Sítě](#net47)
- [ASP.NET](#ASP-NET47)
- [Windows Communication Foundation (WCF)](#wcf47)
- [Windows Forms](#wf47)
- [Windows Presentation Foundation (WPF)](#WPF47)

Seznam nových rozhraní API přidaných do rozhraní .NET Framework 4.7 najdete v [tématu .NET Framework 4.7 API Changes](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-api-changes.md) on GitHub. Seznam vylepšení funkcí a oprav chyb v rozhraní .NET Framework 4.7 najdete v [tématu .NET Framework 4.7 Seznam změn](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-changes.md) na GitHubu. Další informace naleznete [v tématu Oznámení rozhraní .NET Framework 4.7](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-7/) v blogu .NET.

<a name="Core47" />

#### <a name="base-classes"></a>Základní třídy

Rozhraní .NET Framework 4.7 vylepšuje <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>serializaci pomocí rozhraní :

**Vylepšená funkce s kryptografií eliptické křivky (ECC)***

V rozhraní .NET Framework `ImportParameters(ECParameters)` 4.7 <xref:System.Security.Cryptography.ECDsa> byly <xref:System.Security.Cryptography.ECDiffieHellman> do tříd a třídy přidány metody, které umožňují, aby objekt představoval již zavedený klíč. Byla `ExportParameters(Boolean)` také přidána metoda pro export klíče pomocí explicitních parametrů křivky.

Rozhraní .NET Framework 4.7 také přidává podporu pro další křivky (včetně sady brainpoolových křivek) <xref:System.Security.Cryptography.ECDsa.Create%2A> a <xref:System.Security.Cryptography.ECDiffieHellman.Create%2A> přidal předdefinované definice pro snadné vytváření prostřednictvím nových a výrobních metod.

Můžete vidět [příklad vylepšení kryptografie rozhraní .NET Framework 4.7](https://gist.github.com/richlander/5a182899895a87a296c21ada97f7a54e) na GitHubu.

**Lepší podpora řídicích znaků pomocí datacontractjsonserializer**

V rozhraní .NET Framework <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 4.7 serializuje řídicí znaky v souladu se standardem ECMAScript 6. Toto chování je ve výchozím nastavení povoleno pro aplikace, které cílí na rozhraní .NET Framework 4.7, a je funkcí pro přihlášení pro aplikace, které jsou spuštěny v rámci rozhraní .NET Framework 4.7, ale zaměřují se na předchozí verzi rozhraní .NET Framework. Další informace naleznete [v tématu Retargeting Changes in the .NET Framework 4.7](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md).

<a name="net47" />

#### <a name="networking"></a>Sítě

Rozhraní .NET Framework 4.7 přidává následující funkci související se sítí:

**Výchozí podpora operačního systému pro protokoly TLS***

Zásobník TLS, který je <xref:System.Net.Security.SslStream?displayProperty=nameWithType> používán a up-stack komponenty, jako je NAPŘÍKLAD HTTP, FTP a SMTP, umožňuje vývojářům používat výchozí protokoly TLS podporované operačním systémem. Vývojáři již nemusí pevně kódovat verzi TLS.

<a name="ASP-NET47" />

#### <a name="aspnet"></a>ASP.NET

V rozhraní .NET Framework 4.7 obsahuje ASP.NET následující nové funkce:

**Rozšiřitelnost mezipaměti objektů**

Počínaje rozhraním .NET Framework 4.7 přidá ASP.NET novou sadu rozhraní API, která vývojářům umožňují nahradit výchozí ASP.NET implementace pro ukládání objektů v paměti do mezipaměti a monitorování paměti. Vývojáři nyní mohou nahradit některou z následujících tří součástí, pokud ASP.NET implementace není dostatečná:

- **Úložiště mezipaměti objektů**. Pomocí nové části konfigurace zprostředkovatelů mezipaměti mohou vývojáři připojit nové implementace mezipaměti objektů pro ASP.NET aplikaci pomocí nového rozhraní **ICacheStoreProvider.**

- **Monitorování paměti**. Výchozí monitorování paměti v ASP.NET upozorní aplikace, když jsou spuštěny v blízkosti nakonfigurované hospodařilo limit u soukromých bajtů pro proces, nebo když je počítač nedostatek celkové dostupné fyzické paměti RAM. Pokud jsou tato omezení blízko, oznámení jsou aktivována. U některých aplikací jsou oznámení aktivována příliš blízko nakonfigurovaných limitů, aby bylo možné užitečné reakce. Vývojáři nyní mohou psát vlastní monitory paměti <xref:System.Web.Hosting.ApplicationMonitors.MemoryMonitor%2A?displayProperty=nameWithType> nahradit výchozí pomocí vlastnosti.

- **Reakce limitu paměti**. Ve výchozím nastavení ASP.NET pokusí oříznout mezipaměť <xref:System.GC.Collect%2A?displayProperty=nameWithType> objektů a pravidelně volat, když je blízko limitu soukromého bajtového procesu. U některých aplikací jsou <xref:System.GC.Collect%2A?displayProperty=nameWithType> neefektivní četnost volání nebo množství mezipaměti, která je oříznuta. Vývojáři nyní můžete nahradit nebo doplnit výchozí chování přihlášením **iObserver** implementace na monitoru paměti aplikace.

<a name="wcf47" />

#### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)

Windows Communication Foundation (WCF) přidává následující funkce a změny:

**Možnost konfigurace výchozího nastavení zabezpečení zprávy na TLS 1.1 nebo TLS 1.2**

Počínaje rozhraním .NET Framework 4.7 umožňuje wcf konfigurovat tsl 1.1 nebo TLS 1.2 kromě SSL 3.0 a TSL 1.0 jako výchozí protokol zabezpečení zpráv. Toto je nastavení opt-in; Chcete-li jej povolit, musíte do konfiguračního souboru aplikace přidat následující položku:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false" />
</runtime>
```

**Vylepšená spolehlivost aplikací WCF a serializace WCF**

WCF obsahuje řadu změn kódu, které eliminují podmínky časování, čímž se zlepší výkon a spolehlivost možností serializace. Mezi ně patří:

- Lepší podpora pro míchání asynchronního a synchronního kódu při volání **SocketConnection.BeginRead** a **SocketConnection.Read**.
- Vylepšená spolehlivost při přerušení připojení s **SharedConnectionListener** a **DuplexChannelBinder**.
- Vylepšená spolehlivost operací serializace <xref:System.Runtime.Serialization.FormatterServices.GetSerializableMembers%28System.Type%29?displayProperty=nameWithType> při volání metody.
- Lepší spolehlivost při odebírání číšníka voláním **ChannelSynchronizer.RemoveWaiter** metoda.

<a name="wf47" />

#### <a name="windows-forms"></a>Windows Forms

V rozhraní .NET Framework 4.7 windows forms zlepšuje podporu pro monitorování s vysokým obsahem DPI.

**Vysoká podpora DPI**

Počínaje aplikacemi, které cílí na rozhraní .NET Framework 4.7, nabízí rozhraní .NET Framework vysokou podporu DPI a dynamickou podporu DPI pro aplikace Windows Forms. Vysoká podpora DPI zlepšuje rozložení a vzhled formulářů a ovládacích prvků na monitorech s vysokým obsahem DPI. Dynamické DPI změní rozložení a vzhled formulářů a ovládacích prvků, když uživatel změní faktor dpi nebo měřítko zobrazení spuštěné aplikace.

Vysoká podpora DPI je funkce přihlášení, kterou nakonfigurujete definováním oddílu [ \<System.Windows.Forms.ConfigurationSection>](../configure-apps/file-schema/winforms/index.md) v konfiguračním souboru aplikace. Další informace o přidání vysoké podpory DPI a dynamické podpory DPI do aplikace Windows Forms naleznete [v tématu Vysoká podpora DPI ve Windows Forms](../winforms/high-dpi-support-in-windows-forms.md).

<a name="WPF47" />

#### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

V rozhraní .NET Framework 4.7 obsahuje wpf následující vylepšení:

**Podpora balíčku dotykového stylu založeného na zprávách WM_POINTER Windows**

Nyní máte možnost použít balíček dotykového pera založený na [WM_POINTER zpráv](https://docs.microsoft.com/previous-versions/windows/desktop/InputMsg/messages) namísto platformy WISP (Windows Ink Services Platform). Toto je funkce opt-in v rozhraní .NET Framework. Další informace naleznete [v tématu Retargeting Changes in the .NET Framework 4.7](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md).

**Nová implementace pro wpf tisková API**

Rozhraní API pro tisk wpf ve <xref:System.Printing.PrintQueue?displayProperty=nameWithType> třídě volání rozhraní API balíčku [tiskových dokumentů](/windows/desktop/printdocs/tailored-app-printing-api) systému Windows namísto zastaralé rozhraní [XPS Print API](/windows/desktop/printdocs/xps-printing). Dopad této změny na kompatibilitu aplikací naleznete [v tématu Retargeting Changes in the .NET Framework 4.7](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md).

<a name="v462" />

## <a name="whats-new-in-net-framework-462"></a>Co je nového v rozhraní .NET Framework 4.6.2

Rozhraní .NET Framework 4.6.2 obsahuje nové funkce v následujících oblastech:

- [ASP.NET](#ASPNET462)

- [Kategorie znaků](#Strings)

- [Kryptografie](#Crypto462)

- [Sqlclient](#SQLClient)

- [Windows Communication Foundation](#WCF)

- [Windows Presentation Foundation (WPF)](#WPF462)

- [Windows Workflow Foundation (WF)](#WF462)

- [ClickOnce](#clickonce-1)

- [Převod formulářů pro Windows a aplikací WPF na aplikace UPW](#UWPConvert)

- [Vylepšení ladění](#Debug462)

Seznam nových rozhraní API přidaných do rozhraní .NET Framework 4.6.2 najdete v [tématu .NET Framework 4.6.2 API Changes](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-api-changes.md) na GitHubu. Seznam vylepšení funkcí a oprav chyb v rozhraní .NET Framework 4.6.2 najdete v [tématu .NET Framework 4.6.2 Seznam změn](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-changes.md) na GitHubu. Další informace naleznete [v tématu Oznámení rozhraní .NET Framework 4.6.2](https://devblogs.microsoft.com/dotnet/announcing-net-framework-4-6-2/) v blogu .NET.

<a name="ASPNET462" />

### <a name="aspnet"></a>ASP.NET

V rozhraní .NET Framework 4.6.2 obsahuje ASP.NET následující vylepšení:

**Vylepšená podpora lokalizovaných chybových zpráv v validátorech anotací dat**

Validátory anotace umožňují provést ověření přidáním jednoho nebo více atributů do vlastnosti třídy. Prvek atributu <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> definuje text chybové zprávy, pokud se ověření nezdaří. Počínaje rozhraním .NET Framework 4.6.2 ASP.NET usnadňuje lokalizaci chybových zpráv. Chybové zprávy budou lokalizovány, pokud:

1. Je <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> k dispozici v atributu ověření.

2. Soubor prostředků je uložen ve složce App_LocalResources.

3. Název souboru lokalizovaných prostředků má `DataAnnotation.Localization.{` *název*`}.resx`formuláře , kde *název* je název jazykové verze ve formátu *languageCode*`-`*country/regionCode* nebo *languageCode*.

4. Název klíče prostředku je řetězec přiřazený <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> atributu a jeho hodnota je lokalizovaná chybová zpráva.

Například následující atribut anotace dat definuje chybovou zprávu výchozí jazykové verze pro neplatné hodnocení.

```csharp
public class RatingInfo
{
   [Required(ErrorMessage = "The rating must be between 1 and 10.")]
   [Display(Name = "Your Rating")]
   public int Rating { get; set; }
}
```

```vb
Public Class RatingInfo
   <Required(ErrorMessage = "The rating must be between 1 and 10.")>
   <Display(Name = "Your Rating")>
   Public Property Rating As Integer = 1
End Class
```

Potom můžete vytvořit soubor prostředků, DataAnnotation.Localization.fr.resx, jehož klíč je řetězec chybové zprávy a jehož hodnota je lokalizovaná chybová zpráva. Soubor musí být nalezen `App.LocalResources` ve složce. Například následující je klíč a jeho hodnota v lokalizované francouzštině (fr) chybová zpráva:

| Name (Název)                                 | Hodnota                                     |
| ------------------------------------ | ----------------------------------------- |
| Hodnocení musí být mezi 1 a 10. | La note doit être tvoří entre 1 et 10. |

 Kromě toho je lokalizace anotace dat rozšiřitelná. Vývojáři mohou připojit své vlastní zprostředkovatele <xref:System.Web.Globalization.IStringLocalizerProvider> lokalizátoru řetězce implementací rozhraní pro uložení lokalizačního řetězce někde jinde než v souboru prostředků.

 **Asynchronní podpora s poskytovateli úložiště stavu relace**

 ASP.NET nyní umožňuje metody vrácení úloh, které mají být použity s poskytovateli úložiště stavu relace, což umožňuje ASP.NET aplikacím získat výhody škálovatelnosti asynchronní. Chcete-li podporuje asynchronní operace s poskytovateli úložiště <xref:System.Web.SessionState.ISessionStateModule?displayProperty=nameWithType>stavu relace, <xref:System.Web.IHttpModule> ASP.NET obsahuje nové rozhraní , které dědí z a umožňuje vývojářům implementovat vlastní modul stavu relace a zprostředkovatele úložiště asynchronních relací. Rozhraní je definováno takto:

```csharp
public interface ISessionStateModule : IHttpModule {
    void ReleaseSessionState(HttpContext context);
    Task ReleaseSessionStateAsync(HttpContext context);
}
```

```vb
Public Interface ISessionStateModule : Inherits IHttpModule
   Sub ReleaseSessionState(context As HttpContext)
   Function ReleaseSessionStateAsync(context As HttpContext) As Task
End Interface
```

 Kromě toho <xref:System.Web.SessionState.SessionStateUtility> třída obsahuje dvě <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateReadOnly%2A> nové <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateRequired%2A>metody a , které lze použít pro podporu asynchronních operací.

 **Asynchronní podpora pro poskytovatele výstupní mezipaměti**

 Počínaje rozhraním .NET Framework 4.6.2 lze metody vracení úloh použít s poskytovateli výstupní mezipaměti k poskytování výhod škálovatelnosti asynchronní.  Zprostředkovatelé, kteří implementují tyto metody snížit blokování vláken na webovém serveru a zlepšit škálovatelnost ASP.NET služby.

 Pro podporu asynchronních poskytovatelů výstupní mezipaměti byla přidána následující řešení API:

- Třída, <xref:System.Web.Caching.OutputCacheProviderAsync?displayProperty=nameWithType> která dědí <xref:System.Web.Caching.OutputCacheProvider?displayProperty=nameWithType> od a umožňuje vývojářům implementovat zprostředkovatele asynchronní výstupní mezipaměti.

- Třída, <xref:System.Web.Caching.OutputCacheUtility> která poskytuje pomocné metody pro konfiguraci výstupní mezipaměti.

- 18 nových metod <xref:System.Web.HttpCachePolicy?displayProperty=nameWithType> ve třídě. Patří <xref:System.Web.HttpCachePolicy.GetCacheability%2A>mezi <xref:System.Web.HttpCachePolicy.GetCacheExtensions%2A> <xref:System.Web.HttpCachePolicy.GetETag%2A>ně <xref:System.Web.HttpCachePolicy.GetETagFromFileDependencies%2A> <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A> <xref:System.Web.HttpCachePolicy.GetNoStore%2A>, <xref:System.Web.HttpCachePolicy.GetNoTransforms%2A> <xref:System.Web.HttpCachePolicy.GetOmitVaryStar%2A>, <xref:System.Web.HttpCachePolicy.GetProxyMaxAge%2A> <xref:System.Web.HttpCachePolicy.GetRevalidation%2A>, <xref:System.Web.HttpCachePolicy.GetUtcLastModified%2A> <xref:System.Web.HttpCachePolicy.GetVaryByCustom%2A>, <xref:System.Web.HttpCachePolicy.HasSlidingExpiration%2A>, <xref:System.Web.HttpCachePolicy.IsValidUntilExpires%2A>, , , , , , , a .

- 2 nové metody <xref:System.Web.HttpCacheVaryByContentEncodings?displayProperty=nameWithType> ve <xref:System.Web.HttpCacheVaryByContentEncodings.GetContentEncodings%2A> <xref:System.Web.HttpCacheVaryByContentEncodings.SetContentEncodings%2A>třídě: a .

- 2 nové metody <xref:System.Web.HttpCacheVaryByHeaders?displayProperty=nameWithType> ve <xref:System.Web.HttpCacheVaryByHeaders.GetHeaders%2A> <xref:System.Web.HttpCacheVaryByHeaders.SetHeaders%2A>třídě: a .

- 2 nové metody <xref:System.Web.HttpCacheVaryByParams?displayProperty=nameWithType> ve <xref:System.Web.HttpCacheVaryByParams.GetParams%2A> <xref:System.Web.HttpCacheVaryByParams.SetParams%2A>třídě: a .

- Ve <xref:System.Web.Caching.AggregateCacheDependency?displayProperty=nameWithType> třídě <xref:System.Web.Caching.AggregateCacheDependency.GetFileDependencies%2A> metoda.

- V <xref:System.Web.Caching.CacheDependency>, <xref:System.Web.Caching.CacheDependency.GetFileDependencies%2A> metoda.

<a name="Strings" />

### <a name="character-categories"></a>Kategorie znaků

Znaky v rozhraní .NET Framework 4.6.2 jsou klasifikovány na základě [standardu Unicode verze 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/). V rozhraních .NET Framework 4.6 a .NET Framework 4.6.1 byly znaky klasifikovány na základě kategorií znaků Unicode 6.3.

Podpora unicode 8.0 je omezena na klasifikaci znaků podle <xref:System.Globalization.CharUnicodeInfo> třídy a na typy a metody, které jsou na něm závislé. Patří mezi <xref:System.Globalization.StringInfo> ně třída, <xref:System.Char.GetUnicodeCategory%2A?displayProperty=nameWithType> přetížená metoda a [třídy znaků](../../standard/base-types/character-classes-in-regular-expressions.md) rozpoznané modulem regulárních výrazů rozhraní .NET Framework.  Porovnání a řazení znaků a řetězců není touto změnou ovlivněno a nadále se spoléhá na základní operační systém nebo v systémech Windows 7 na znaková data poskytovaná rozhraním .NET Framework.

Změny v kategoriích znaků z Unicode 6.0 na Unicode 7.0 naleznete v [tématu Unicode Standard, verze 7.0.0](https://www.unicode.org/versions/Unicode7.0.0/) na webu Unicode Consortium. Změny z Unicode 7.0 na Unicode 8.0 naleznete v [tématu Unicode Standard, verze 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/) na webu Unicode Consortium.

<a name="Crypto462" />

### <a name="cryptography"></a>Kryptografie

**Podpora certifikátů X509 obsahujících FIPS 186-3 DSA**

Rozhraní .NET Framework 4.6.2 přidává podporu pro certifikáty DSA (Digital Signature Algorithm) X509, jejichž klíče překračují limit 186-2 1024 bit.

Kromě podpory větší velikosti klíčů FIPS 186-3 umožňuje rozhraní .NET Framework 4.6.2 výpočetní podpisy s rodinou algoritmů hash SHA-2 (SHA256, SHA384 a SHA512). Fips 186-3 podpora je poskytována novou <xref:System.Security.Cryptography.DSACng?displayProperty=nameWithType> třídou.

V souladu s nedávnými změnami <xref:System.Security.Cryptography.RSA> třídy v <xref:System.Security.Cryptography.ECDsa> rozhraní .NET Framework 4.6 a <xref:System.Security.Cryptography.DSA> třídy v rozhraní .NET Framework 4.6.1 má abstraktní základní třída v rozhraní .NET Framework 4.6.2 další metody, které volajícím umožňují používat tuto funkci bez přetypování. Můžete volat <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey%2A?displayProperty=nameWithType> metodu rozšíření k podepsání dat, jak ukazuje následující příklad.

```csharp
public static byte[] SignDataDsaSha384(byte[] data, X509Certificate2 cert)
{
    using (DSA dsa = cert.GetDSAPrivateKey())
    {
        return dsa.SignData(data, HashAlgorithmName.SHA384);
    }
}
```

```vb
Public Shared Function SignDataDsaSha384(data As Byte(), cert As X509Certificate2) As Byte()
    Using DSA As DSA = cert.GetDSAPrivateKey()
        Return DSA.SignData(data, HashAlgorithmName.SHA384)
    End Using
End Function
```

A můžete volat <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey%2A?displayProperty=nameWithType> metodu rozšíření k ověření podepsaných dat, jak ukazuje následující příklad.

```csharp
public static bool VerifyDataDsaSha384(byte[] data, byte[] signature, X509Certificate2 cert)
{
    using (DSA dsa = cert.GetDSAPublicKey())
    {
        return dsa.VerifyData(data, signature, HashAlgorithmName.SHA384);
    }
}
```

```vb
 Public Shared Function VerifyDataDsaSha384(data As Byte(), signature As Byte(), cert As X509Certificate2) As Boolean
    Using dsa As DSA = cert.GetDSAPublicKey()
        Return dsa.VerifyData(data, signature, HashAlgorithmName.SHA384)
    End Using
End Function
```

**Zvýšená srozumitelnost pro vstupy do rutin odvození klíčů ECDiffieHellman**

.NET Framework 3.5 přidal podporu pro dohodu elliptic Curve Diffie-Hellman Key Agreement se třemi různými rutinami funkce Odvození klíče (KDF). Vstupy do rutiny a rutiny samotné, byly konfigurovány <xref:System.Security.Cryptography.ECDiffieHellmanCng> prostřednictvím vlastností na objektu. Ale protože ne každý rutinní číst každý vstup vlastnosti, tam byl dostatečný prostor pro zmatek v minulosti developera.

Chcete-li tento problém vyřešit v rozhraní .NET Framework 4.6.2, byly přidány následující tři metody do <xref:System.Security.Cryptography.ECDiffieHellman> základní třídy jasněji reprezentovat tyto Rutiny KDF a jejich vstupy:

|Metoda ECDiffieHellman|Popis|
|----------------------------|-----------------|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHash%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Odvozuje klíčový materiál pomocí vzorce<br /><br /> HASH (secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)<br /><br /> HASH(secretPrepend OrElse *x* OrElse secretAppend)<br /><br /> kde *x* je vypočítaný výsledek algoritmu EC Diffie-Hellman.|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHmac%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Odvozuje klíčový materiál pomocí vzorce<br /><br /> HMAC(hmacKey, secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)<br /><br /> HMAC(hmacKey, secretPrepend OrElse *x* OrElse secretAppend)<br /><br /> kde *x* je vypočítaný výsledek algoritmu EC Diffie-Hellman.|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyTls%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Odvozuje klíčový materiál pomocí algoritmu odvození pseudonáhodné funkce TLS (PRF).|

**Podpora symetrického šifrování trvalého klíče**

Knihovna kryptografie systému Windows (CNG) přidala podporu pro ukládání trvalých symetrických klíčů a použití hardwarově uložených symetrických klíčů a rozhraní .NET Framework 4.6.2 umožnilo vývojářům tuto funkci využívat.  Vzhledem k tomu, že pojem názvy klíčů a zprostředkovatelé klíčů je specifické pro implementaci, použití této `Aes.Create`funkce vyžaduje využití konstruktoru konkrétní typy implementace namísto upřednostňované tovární přístup (například volání ).

Pro algoritmy AES (<xref:System.Security.Cryptography.AesCng>) a 3DES (<xref:System.Security.Cryptography.TripleDESCng>) existuje podpora symetrického šifrování s trvalým klíčem. Například:

```csharp
public static byte[] EncryptDataWithPersistedKey(byte[] data, byte[] iv)
{
    using (Aes aes = new AesCng("AesDemoKey", CngProvider.MicrosoftSoftwareKeyStorageProvider))
    {
        aes.IV = iv;

        // Using the zero-argument overload is required to make use of the persisted key
        using (ICryptoTransform encryptor = aes.CreateEncryptor())
        {
            if (!encryptor.CanTransformMultipleBlocks)
            {
                throw new InvalidOperationException("This is a sample, this case wasn’t handled...");
            }

            return encryptor.TransformFinalBlock(data, 0, data.Length);
        }
    }
}
```

```vb
Public Shared Function EncryptDataWithPersistedKey(data As Byte(), iv As Byte()) As Byte()
    Using Aes As Aes = New AesCng("AesDemoKey", CngProvider.MicrosoftSoftwareKeyStorageProvider)
        Aes.IV = iv

        ' Using the zero-argument overload Is required to make use of the persisted key
        Using encryptor As ICryptoTransform = Aes.CreateEncryptor()
            If Not encryptor.CanTransformMultipleBlocks Then
                Throw New InvalidOperationException("This is a sample, this case wasn’t handled...")
            End If
            Return encryptor.TransformFinalBlock(data, 0, data.Length)
        End Using
    End Using
End Function
```

**Podpora SignedXml pro sha-2 hashing**

Rozhraní .NET Framework 4.6.2 <xref:System.Security.Cryptography.Xml.SignedXml> přidává podporu do třídy pro rsa-SHA256, RSA-SHA384 a RSA-SHA512 PKCS#1 podpisové metody a SHA256, SHA384 a SHA512 referenční algoritmy digest.

Všechny konstanty URI jsou <xref:System.Security.Cryptography.Xml.SignedXml>vystaveny na :

|Pole SignedXml|Trvalé|
|---------------------|--------------|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA256Url>|"http://www.w3.org/2001/04/xmlenc#sha256"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA256Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha256"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA384Url>|"http://www.w3.org/2001/04/xmldsig-more#sha384"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA384Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha384"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA512Url>|"http://www.w3.org/2001/04/xmlenc#sha512"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA512Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha512"|

 Všechny programy, které <xref:System.Security.Cryptography.SignatureDescription> zaregistrovaly <xref:System.Security.Cryptography.CryptoConfig> vlastní obslužnou rutinu <xref:System.Security.Cryptography.CryptoConfig> do přidat podporu pro tyto algoritmy bude i nadále fungovat jako tomu bylo v minulosti, ale protože existují nyní výchozí platformy, registrace již není nutné.

<a name="SQLClient" />

### <a name="sqlclient"></a>Sqlclient

Zprostředkovatel dat rozhraní .NET<xref:System.Data.SqlClient?displayProperty=nameWithType>Framework pro SQL Server ( ) obsahuje následující nové funkce v rozhraní .NET Framework 4.6.2:

**Sdružování připojení a časové limity s databázemi Azure SQL**

Je-li povoleno sdružování připojení a dojde k vypršení časového limitu nebo jiné chybě přihlášení, je výjimka uložena do mezipaměti a výjimka uložená v mezipaměti je vyvolána při každém následném pokusu o připojení pro dalších 5 sekund až 1 minutu. Další informace naleznete v tématu [SQL Server Connection Pooling (ADO.NET)](../data/adonet/sql-server-connection-pooling.md).

Toto chování není žádoucí při připojování k Azure SQL Databases, protože pokusy o připojení může selhat s přechodnými chybami, které se obvykle rychle obnovují. Chcete-li lépe optimalizovat prostředí opakování připojení, chování období blokování fondu připojení se odebere, když se nezdaří připojení k databázím Azure SQL Databases.

Přidání nového `PoolBlockingPeriod` klíčového slova umožňuje vybrat období blokování, které je pro vaši aplikaci nejvhodnější. Mezi tyto hodnoty patří:

<xref:System.Data.SqlClient.PoolBlockingPeriod.Auto>

Doba blokování fondu připojení pro aplikaci, která se připojuje k databázi Azure SQL, je zakázána a je povolena doba blokování fondu připojení pro aplikaci, která se připojuje k jakékoli jiné instanci serveru SQL Server. Toto je výchozí hodnota. Pokud název koncového bodu serveru končí některou z následujících, jsou považovány za Azure SQL Databases:

- .database.windows.net

- .database.chinacloudapi.cn

- .database.usgovcloudapi.net

- .database.cloudapi.de

<xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock>

Doba blokování fondu připojení je vždy povolena.

<xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock>

Doba blokování fondu připojení je vždy zakázána.

**Vylepšení pro vždy šifrované**

SQLClient zavádí dvě vylepšení pro vždy šifrované:

- Chcete-li zlepšit výkon parametrizovaných dotazů proti šifrovaným databázovým sloupcům, jsou nyní uložena do mezipaměti metadata šifrování pro parametry dotazu. S <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled%2A?displayProperty=nameWithType> vlastností `true` nastavenou na (což je výchozí hodnota), pokud je stejný dotaz volán vícekrát, klient načte metadata parametru ze serveru pouze jednou.

- Položky šifrovacího klíče sloupce v mezipaměti klíčů jsou nyní <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionKeyCacheTtl%2A?displayProperty=nameWithType> vyřazeny po konfigurovatelném časovém intervalu nastaveném pomocí vlastnosti.

<a name="WCF" />

### <a name="windows-communication-foundation"></a>Windows Communication Foundation

V rozhraní .NET Framework 4.6.2 byla nadace Windows Communication Foundation vylepšena v následujících oblastech:

**WCF podpora zabezpečení přenosu pro certifikáty uložené pomocí CNG**

WCF zabezpečení přenosu podporuje certifikáty uložené pomocí knihovny kryptografie systému Windows (CNG). V rozhraní .NET Framework 4.6.2 je tato podpora omezena na použití certifikátů s veřejným klíčem, který má exponent ne více než 32 bitů na délku. Pokud aplikace cílí na rozhraní .NET Framework 4.6.2, je tato funkce ve výchozím nastavení zapnutá.

U aplikací, které cílí na rozhraní .NET Framework 4.6.1 a starší, ale jsou spuštěny v rozhraní .NET Framework 4.6.2, lze tuto funkci povolit přidáním následujícího řádku do sekce [ \<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) souboru app.config nebo web.config.

```xml
<AppContextSwitchOverrides
    value="Switch.System.ServiceModel.DisableCngCertificates=false"
/>
```

To lze také provést programově s kódem, jako je následující:

```csharp
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificates";
AppContext.SetSwitch(disableCngCertificates, false);
```

```vb
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"
AppContext.SetSwitch(disableCngCertificates, False)
```

**Lepší podpora pro více pravidel úprav letního času podle třídy DataContractJsonSerializer**

Zákazníci mohou pomocí nastavení konfigurace <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> aplikace určit, zda třída podporuje více pravidel úprav pro jedno časové pásmo. Jedná se o funkci opt-in. Chcete-li jej povolit, přidejte do souboru app.config následující nastavení:

```xml
<runtime>
     <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseTimeZoneInfo=false" />
</runtime>
```

Pokud je tato funkce <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> povolena, objekt používá <xref:System.TimeZoneInfo> typ namísto <xref:System.TimeZone> typu k rekonstrukci dat data a času. <xref:System.TimeZoneInfo>podporuje více pravidel úprav, která umožňují pracovat s historickými daty časových pásem;   <xref:System.TimeZone> není.

Další informace o <xref:System.TimeZoneInfo> struktuře a úpravách časového pásma naleznete v [tématu Přehled časového pásma](../../standard/datetime/time-zone-overview.md).

**NetNamedPipeBinding nejlepší shoda**

WCF má nové nastavení aplikace, které lze nastavit na klientských aplikacích, aby bylo zajištěno, že se vždy připojí ke službě naslouchání na identifikátoru URI, který nejlépe odpovídá tomu, který požadují. S tímto nastavením aplikace nastaveným na `false` (výchozí), je možné, že se klienti, kteří se pokoušejí <xref:System.ServiceModel.NetNamedPipeBinding> připojit ke službě naslouchající na identifikátoru URI, který je podřetězcem požadovaného identifikátoru URI.

Klient se například pokusí připojit ke `net.pipe://localhost/Service1`službě naslouchající v , ale jiná `net.pipe://localhost`služba v tomto počítači spuštěná s oprávněním správce naslouchá na . S tímto nastavením aplikace nastaveným na `false`, by se klient pokusil připojit k nesprávné službě. Po nastavení aplikace `true`na , bude klient vždy připojit k nejlepší odpovídající služby.

> [!NOTE]
> Klienti <xref:System.ServiceModel.NetNamedPipeBinding> pomocí najít služby založené na základní adresu služby (pokud existuje) spíše než úplnou adresu koncového bodu. Chcete-li zajistit, že toto nastavení vždy funguje, služba by měla používat jedinečnou základní adresu.

Chcete-li tuto změnu povolit, přidejte do souboru App.config nebo Web.config klientské aplikace následující nastavení aplikace:

```xml
<configuration>
    <appSettings>
        <add key="wcf:useBestMatchNamedPipeUri" value="true" />
    </appSettings>
</configuration>
```

**SSL 3.0 není výchozí protokol**

Při použití protokolu NetTcp se zabezpečením přenosu a typem pověření certifikátu již není protokol SSL 3.0 výchozím protokolem používaným pro vyjednávání zabezpečeného připojení. Ve většině případů by nemělo být žádné dopad na existující aplikace, protože TLS 1.0 je zahrnuta v seznamu protokolů pro NetTcp. Všichni stávající klienti by měli být schopni vyjednat připojení pomocí alespoň TLS 1.0. Pokud je vyžadováno Ssl3, použijte jeden z následujících konfiguračních mechanismů k jeho přidání do seznamu vyjednaných protokolů.

- Vlastnost <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=nameWithType>

- Vlastnost <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType>

- Oddíl [ \<Transport>](../configure-apps/file-schema/wcf/transport-of-nettcpbinding.md) oddílu [ \<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md)

- Oddíl [ \<sslStreamSecurity>](../configure-apps/file-schema/wcf/sslstreamsecurity.md) oddílu [ \<customBinding>](../configure-apps/file-schema/wcf/custombinding.md)

<a name="WPF462" />

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

V rozhraní .NET Framework 4.6.2 byla nadace Windows Presentation Foundation vylepšena v následujících oblastech:

**Řazení skupin**

Aplikace, která <xref:System.Windows.Data.CollectionView> používá objekt k seskupení dat nyní můžete explicitně deklarovat, jak třídit skupiny. Explicitní řazení řeší problém neintuitivnířazení, ke kterému dochází, když aplikace dynamicky přidává nebo odebere skupiny nebo když změní hodnotu vlastností položky, které se účastní seskupování. Může také zlepšit výkon procesu vytváření skupiny přesunutím porovnání vlastností seskupení z druhu úplné kolekce na druh skupin.

Pro podporu řazení skupin, <xref:System.ComponentModel.GroupDescription.SortDescriptions%2A?displayProperty=nameWithType> <xref:System.ComponentModel.GroupDescription.CustomSort%2A?displayProperty=nameWithType> nové a vlastnosti popisují, jak <xref:System.ComponentModel.GroupDescription> seřadit kolekci skupin vytvořených objektem. To je obdobou způsobu, jakým <xref:System.Windows.Data.ListCollectionView> identicky pojmenované vlastnosti popisují, jak třídit datové položky.

Dvě nové statické <xref:System.Windows.Data.PropertyGroupDescription> vlastnosti <xref:System.Windows.Data.PropertyGroupDescription.CompareNameAscending%2A> <xref:System.Windows.Data.PropertyGroupDescription.CompareNameDescending%2A>třídy a , lze použít pro nejběžnější případy.

Například následující XAML seskupí data podle věku, seřadí věkové skupiny ve vzestupném pořadí a seskupí položky v rámci každé věkové skupiny podle příjmení.

```xaml
<GroupDescriptions>
     <PropertyGroupDescription
         PropertyName="Age"
         CustomSort=
              "{x:Static PropertyGroupDescription.CompareNamesAscending}"/>
     </PropertyGroupDescription>
</GroupDescriptions>

<SortDescriptions>
     <SortDescription PropertyName="LastName"/>
</SortDescriptions>
```

**Podpora dotykové klávesnice**

Podpora dotykové klávesnice umožňuje sledování fokusu v aplikacích WPF automatickým vyvoláním a zavřením dotykové klávesnice v systému Windows 10, když je dotykový vstup přijat ovládacím prvkem, který může přijímat textový vstup.

V předchozích verzích rozhraní .NET Framework se aplikace WPF nemohou přihlásit do sledování fokusu bez zakázání podpory gest a gest y pro pera wpf. V důsledku toho wpf aplikace musí vybrat mezi plnou podporou Dotykové ovládání WPF nebo spoléhat na propagaci myši systému Windows.

**DPI pro jeden monitor**

Pro podporu nedávného rozšíření prostředí s vysokým dpi a hybridního DPI pro aplikace WPF wpf, WPF v rozhraní .NET Framework 4.6.2 umožňuje povědomí na monitoru. Další informace o tom, jak povolit aplikaci WPF na monitoru DPI, najdete v [ukázkách a vývojářském průvodci](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI) na GitHubu.

V předchozích verzích rozhraní .NET Framework jsou aplikace WPF informovány o systému DPI. Jinými slovy, ujtoulovaná uontaje operačního programu podle potřeby pomocí operačního programu v závislosti na DPI monitoru, na kterém je aplikace vykreslena.

U aplikací spuštěných v rámci rozhraní .NET Framework 4.6.2 můžete zakázat změny DPI na monitorování v aplikacích WPF přidáním příkazu konfigurace do sekce [ \<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) konfiguračního souboru aplikace, a to následovně:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Windows.DoNotScaleForDpiChanges=false"/>
</runtime>
```

<a name="WF462" />

### <a name="windows-workflow-foundation-wf"></a>Windows Workflow Foundation (WF)

V rozhraní .NET Framework 4.6.2 byla nadace Windows Workflow Foundation vylepšena v následující oblasti:

**Podpora výrazů jazyka C# a technologie IntelliSense v návrháři služby WF s rehosted**

Počínaje rozhraním .NET Framework 4.5 podporuje wf# výrazy v návrháři Visual Studio i v pracovních postupech kódu. Rehosted Workflow Designer je klíčovou funkcí wf, který umožňuje Návrháře pracovních postupů být v aplikaci mimo Visual Studio (například v WPF).  Windows Workflow Foundation poskytuje možnost podporovat výrazy Jazyka C# a technologie IntelliSense v návrháři pracovních postupů rehosted. Další informace naleznete v [blogu Windows Workflow Foundation](https://docs.microsoft.com/archive/blogs/workflowteam/building-c-expressions-support-and-intellisense-in-the-rehosted-workflow-designer).

`Availability of IntelliSense when a customer rebuilds a workflow project from Visual Studio`Ve verzích rozhraní .NET Framework před verzí 4.6.2 je návrhář WF IntelliSense přerušen, když zákazník znovu vytvoří projekt pracovního postupu z aplikace Visual Studio. Při sestavení projektu je úspěšné, typy pracovních postupů nejsou nalezeny v návrháři a upozornění z IntelliSense pro chybějící typy pracovních postupů se zobrazí v okně **Seznam chyb.** Rozhraní .NET Framework 4.6.2 řeší tento problém a zpřístupňuje technologie IntelliSense.

**Aplikace Workflow V1 s funkcemi Sledování pracovního postupu jsou nyní spuštěny v režimu FIPS**

Počítače s povoleným režimem dodržování předpisů FIPS nyní mohou úspěšně spustit pracovní postup verze 1 stylu aplikace se zapnutým sledováním pracovního postupu. Chcete-li tento scénář povolit, je nutné provést následující změny souboru app.config:

```xml
<add key="microsoft:WorkflowRuntime:FIPSRequired" value="true" />
```

Pokud tento scénář není povolena, spuštění aplikace nadále generovat výjimku se zprávou "Tato implementace není součástí platformy Windows FIPS ověřené kryptografické algoritmy."

**Vylepšení pracovního postupu při použití dynamické aktualizace s návrhářem pracovních postupů sady Visual Studio**

Návrhář pracovních postupů, Návrhář aktivit vývojového diagramu a další návrháři aktivit pracovního <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> postupu nyní úspěšně načítají a zobrazují pracovní postupy, které byly uloženy po volání metody. Ve verzích rozhraní .NET Framework před rozhraním .NET Framework 4.6.2 může načtení souboru <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> XAML v sadě Visual Studio pro pracovní postup, který byl uložen po volání, mít za následek následující problémy:

- Návrhář pracovního postupu nemůže správně načíst soubor <xref:System.Activities.Presentation.ViewState.ViewStateData.Id%2A?displayProperty=nameWithType> XAML (pokud je na konci řádku).

- Návrhář aktivit vývojového diagramu nebo jiné návrháři aktivit pracovního postupu mohou zobrazit všechny objekty ve výchozích umístěních na rozdíl od připojených hodnot vlastností.

<a name="clickonce-1" />

### <a name="clickonce"></a>ClickOnce

ClickOnce byl aktualizován na podporu TLS 1.1 a TLS 1.2 kromě protokolu 1.0, který již podporuje. ClickOnce automaticky detekuje, který protokol je vyžadován; žádné další kroky v rámci clickonce aplikace jsou nutné pro povolení tls 1.1 a 1.2 podporu.

<a name="UWPConvert" />

### <a name="converting-windows-forms-and-wpf-apps-to--uwp-apps"></a>Převod formulářů pro Windows a aplikací WPF na aplikace UPW

Systém Windows nyní nabízí funkce, které přinášejí stávající desktopové aplikace pro Windows, včetně aplikací WPF a Windows Forms, na univerzální platformu Windows (UPW). Tato technologie funguje jako most tím, že umožňuje postupně migrovat stávající základ kódu do UPW, a tím přenést vaši aplikaci do všech zařízení s Windows 10.

Převedené aplikace klasické pracovní plochy získají identitu aplikace podobnou identitě aplikace UPW, což zpřístupňuje api UPW, která umožňuje funkce, jako jsou živé dlaždice a oznámení. Aplikace se nadále chová jako dříve a běží jako aplikace s úplným vztahem důvěryhodnosti. Po převodu aplikace lze do existujícího procesu úplné důvěryhodnosti přidat adaptivní uživatelské rozhraní. Když se všechny funkce přesunou do procesu kontejneru aplikace, můžete odebrat proces úplné důvěryhodnosti a novou aplikaci UPW lze zpřístupnit všem zařízením s Windows 10.

<a name="Debug462" />

### <a name="debugging-improvements"></a>Vylepšení ladění

*Nespravované rozhraní API ladění* bylo vylepšeno v rozhraní .NET Framework 4.6.2 <xref:System.NullReferenceException> k provedení další analýzy při vyvolání, aby bylo `null`možné určit, která proměnná v jednom řádku zdrojového kódu je .   Pro podporu tohoto scénáře byla do nespravovaného rozhraní API ladění přidána následující rozhraní API rozhraní API.

- [Rozhraní ICorDebugCode4](../unmanaged-api/debugging/icordebugcode4-interface.md), [ICorDebugVariableHome](../unmanaged-api/debugging/icordebugvariablehome-interface.md)a [ICorDebugVariableHomeEnum,](../unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) které zveřejňují nativní domovy spravovaných proměnných. To umožňuje ladicím programům provést analýzu toku kódu, <xref:System.NullReferenceException> když dojde k a pracovat zpětně, `null`k určení spravované proměnné, která odpovídá nativnímu umístění, které bylo .

- [Metoda ICorDebugType2::GetTypeID](../unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) poskytuje mapování pro ICorDebugType na [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md), který umožňuje ladicímu programu získat [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) bez instance ICorDebugType. Existující rozhraní API na [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) pak lze určit rozložení třídy typu.

<a name="v461" />

## <a name="whats-new-in-net-framework-461"></a>Co je nového v rozhraní .NET Framework 4.6.1

Rozhraní .NET Framework 4.6.1 obsahuje nové funkce v následujících oblastech:

- [Kryptografie](#Crypto)

- [ADO.NET](#ADO.NET461)

- [Windows Presentation Foundation (WPF)](#WPF461)

- [Windows Workflow Foundation](#WWF461)

- [Profilování](#Profile461)

- [Ngen](#NGEN461)

Další informace o rozhraní .NET Framework 4.6.1 naleznete v následujících tématech:

- [.NET Framework 4.6.1 seznam změn](https://github.com/Microsoft/dotnet/blob/master/releases/net461/dotnet461-changes.md)

- [Kompatibilita aplikací v 4.6.1](../migration-guide/application-compatibility.md)

- [.NET Framework API diff](https://github.com/Microsoft/dotnet/blob/master/releases/net461/dotnet461-api-changes.md) (na GitHubu)

<a name="Crypto" />

### <a name="cryptography-support-for-x509-certificates-containing-ecdsa"></a>Kryptografie: Podpora certifikátů X509 obsahujících ECDSA

Rozhraní .NET Framework 4.6 přidalo podporu RSACng pro certifikáty X509. Rozhraní .NET Framework 4.6.1 přidává podporu pro certifikáty ECDSA (Eliptický oblouk digitálního podpisu) X509.

ECDSA nabízí lepší výkon a je bezpečnější kryptografický algoritmus než RSA, poskytuje vynikající volbu, kde je problém emitovat výkon a škálovatelnost transportní vrstvy (TLS). Implementace rozhraní .NET Framework zalomí volání do existujícífunkce systému Windows.

Následující ukázkový kód ukazuje, jak snadné je generovat podpis pro bajtový datový proud pomocí nové podpory certifikátů ECDSA X509 zahrnutých v rozhraní .NET Framework 4.6.1.

[!code-csharp[whatsnew.461.crypto#1](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#1)]
[!code-vb[whatsnew.461.crypto#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code461.vb#1)]

To nabízí výrazný kontrast ke kódu potřebnému ke generování podpisu v rozhraní .NET Framework 4.6.

[!code-csharp[whatsnew.461.crypto#2](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#2)]
[!code-vb[whatsnew.461.crypto#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code46.vb#2)]

<a name="ADO.NET461" />

### <a name="adonet"></a>ADO.NET

Do ADO.NET byly přidány nové:

**Vždy šifrovaná podpora hardwarově chráněných klíčů**

ADO.NET nyní podporuje ukládání vždy šifrované klíče hlavního sloupce nativně v modulech hardwarového zabezpečení (HSM). Díky této podpoře mohou zákazníci využívat asymetrické klíče uložené v objektech zabezpečení, aniž by museli psát vlastní zprostředkovatele úložiště hlavních klíčů sloupců a registrovat je v aplikacích.

Zákazníci musí nainstalovat zprostředkovatele zprostředkovatele zprostředkovatele zprostředkovatele zprostředkovatele zprostředkovatele zprostředkovatele zprostředkovatele csp poskytovaného dodavatelem nebo zprostředkovatele klíčů CNG na aplikační servery nebo klientské počítače, aby měli přístup k vždy šifrovaným datům chráněným hlavními klíči sloupců uloženými v serveru zabezpečení zabezpečení.

**Vylepšené <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> chování připojení pro AlwaysOn**

SqlClient nyní automaticky poskytuje rychlejší připojení k AlwaysOn dostupnost skupiny (AG). Transparentně zjistí, zda se vaše aplikace připojuje ke skupině dostupnosti AlwaysOn (AG) v jiné podsíti a rychle zjišťuje aktuální aktivní server a poskytuje připojení k serveru. Před vydáním této verze aplikace musela nastavit `"MultisubnetFailover=true"` připojovací řetězec tak, aby označoval, že se připojuje ke skupině dostupnosti AlwaysOn. Bez nastavení klíčového `true`slova připojení na aplikace může dojít k časový limit při připojování k AlwaysOn dostupnost skupiny. V této verzi aplikace *not* již není <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> `true` nutné nastavit. Další informace o podpoře sqlclientu pro skupiny dostupnosti always on naleznete v tématu [Podpora sqlclientu pro vysokou dostupnost, zotavení po havárii](../data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md).

<a name="WPF461" />

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

Windows Presentation Foundation obsahuje řadu vylepšení a změn.

**Vyšší výkon**

Zpoždění při spouštění dotykových událostí bylo opraveno v rozhraní .NET Framework 4.6.1. Kromě toho zadáníovládacího <xref:System.Windows.Controls.RichTextBox> prvku již nenaváže vlákno vykreslení během rychlého zadávání.

**Vylepšení kontroly pravopisu**

Kontrola pravopisu ve WPF byla aktualizována v systému Windows 8.1 a novějších verzích, aby využila podporu operačního systému pro kontrolu pravopisu dalších jazyků.  Před Windows 8.1 nedojde k žádné změně funkčnosti ve verzích systému Windows.

Stejně jako v předchozích verzích rozhraní <xref:System.Windows.Controls.TextBox> .NET <xref:System.Windows.Controls.RichTextBox> Framework je jazyk pro řídicí blok ora zjištěn hledáním informací v následujícím pořadí:

- `xml:lang`, pokud je přítomen.

- Aktuální jazyk zadávání.

- Aktuální jazyková verze vlákna.

Další informace o jazykové podpoře ve WPF naleznete v [příspěvku blogu WPF na rozhraní .NET Framework 4.6.1 .](https://devblogs.microsoft.com/wpf/wpf-in-net-4-6-1/)

**Další podpora pro vlastní slovníky pro jednotlivé uživatele**

V rozhraní .NET Framework 4.6.1 WPF rozpozná vlastní slovníky, které jsou registrovány globálně. Tato funkce je k dispozici kromě možnosti zaregistrovat je na ovládací prvek.

V předchozích verzích WPF vlastní slovníky nerozpoznaly seznamy vyloučených slov a automatických oprav. Jsou podporovány v systémech Windows 8.1 a Windows 10 pomocí `%AppData%\Microsoft\Spelling\<language tag>` souborů, které mohou být umístěny pod adresářem.  Pro tyto soubory platí následující pravidla:

- Soubory by měly mít přípony .dic (pro přidaná slova), .exc (pro vyloučená slova) nebo .acl (pro automatické opravy).

- Soubory by měly být UTF-16 LE ve formátu prostého textu, který začíná označením objednávky bajtů (BOM).

- Každý řádek by se měl skládat ze slova (v seznamech slov s přidanými a vyloučenými slovy) nebo z dvojice automatických oprav se slovy oddělenými svislým pruhem ("&#124;") (v seznamu slov Automatické opravy).

- Tyto soubory jsou považovány za jen pro čtení a nejsou systémem změněny.

> [!NOTE]
> Tyto nové formáty souborů nejsou přímo podporovány WPF kontrolu pravopisu API a vlastní slovníky dodané WPF v aplikacích by měl y nadále používat soubory .lex.

**ukázky**

Existuje několik wpf ukázky v úložišti [GitHub Microsoft/WPF-Samples.](https://github.com/Microsoft/WPF-Samples) Pomozte nám vylepšit naše ukázky tím, že nám pošlete žádost o přijetí nebo otevřete [problém githubu](https://github.com/Microsoft/WPF-Samples/issues).

**Rozšíření DirectX**

WPF obsahuje [balíček NuGet,](https://www.nuget.org/packages/Microsoft.Wpf.Interop.DirectX-x86/) který <xref:System.Windows.Interop.D3DImage> poskytuje nové implementace, které usnadňují práci s obsahem DX10 a Dx11. Kód pro tento balíček byl open sourced a je k dispozici [na GitHubu](https://github.com/Microsoft/WPFDXInterop).

<a name="WWF461" />

### <a name="windows-workflow-foundation-transactions"></a>Windows Workflow Foundation: Transakce

Metoda <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> nyní můžete použít správce distribuovaných transakcí než MSDTC k propagaci transakce. To provést zadáním identifikátoru propagátoru <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> transakcí GUID pro nové přetížení . Pokud je tato operace úspěšná, existují omezení na možnosti transakce. Jakmile je zapsán propagátor transakcí jiné než MSDTC, následující metody <xref:System.Transactions.TransactionPromotionException> vyvolat, protože tyto metody vyžadují povýšení na MSDTC:

- <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetDtcTransaction%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetExportCookie%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetTransmitterPropagationToken%2A?displayProperty=nameWithType>

Jakmile je zapsán propagátor transakcí jiné než MSDTC, musí být použit pro budoucí trvalé zařazení pomocí protokolů, které definuje. Pořadatele <xref:System.Guid> transakcí lze získat pomocí <xref:System.Transactions.Transaction.PromoterType%2A> nemovitosti. Když transakce propaguje, promotér transakcí poskytuje <xref:System.Byte> pole, které představuje propagovaný token. Aplikace může získat povýšený token pro transakci, která není <xref:System.Transactions.Transaction.GetPromotedToken%2A> podporována msdtc s metodou.

Uživatelé nové <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> přetížení musí následovat konkrétní pořadí volání, aby operace povýšení úspěšně dokončit. Tato pravidla jsou popsána v dokumentaci metody.

<a name="Profile461" />

### <a name="profiling"></a>Profilace

Nespravované profilování rozhraní API byla rozšířena takto:

- Lepší podpora pro přístup k PDBs v rozhraní [ICorProfilerInfo7.](../unmanaged-api/profiling/icorprofilerinfo7-interface.md)

  V ASP.NET Core, je stále běžnější pro sestavení, které mají být kompilovány v paměti Roslyn. Pro vývojáře, kteří provádějí nástroje pro profilování, to znamená, že objekty PDB, které byly historicky serializovány na disku, již nemusí být k dispozici. Nástroje profileru často používají objekty PDB k mapování kódu zpět na zdrojové řádky pro úkoly, jako je pokrytí kódu nebo analýza výkonu řádek po řádku. [Rozhraní ICorProfilerInfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) nyní obsahuje dvě nové metody, [ICorProfilerInfo7::GetInMemorySymbolsLength](../unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md) a [ICorProfilerInfo7::ReadInMemorySymbols](../unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md), aby tyto nástroje profileru poskytovaly přístup k datům PDB v paměti, pomocí nových rozhraní API může profiler získat obsah pdb v paměti jako bajtové pole a potom jej zpracovat nebo serializovat na disk.

- Lepší instrumentace s rozhraním ICorProfiler.

  Profilovací programy, `ICorProfiler` které používají funkce ReJit api pro dynamické instrumentace nyní můžete upravit některá metadata. Dříve tyto nástroje mohly kdykoli instrumentovat IL, ale metadata mohla být změněna pouze v době načítání modulu. Vzhledem k tomu, že IL odkazuje na metadata, to omezené druhy instrumentace, které by bylo možné provést. Některé z těchto limitů jsme zrušili přidáním metody [ICorProfilerInfo7::ApplyMetaData](../unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md) pro podporu podmnožiny úprav metadat `AssemblyRef` `TypeRef`po `TypeSpec` `MemberRef`načtení modulu, zejména přidáním nových záznamů , , `MemberSpec`, , a `UserString` záznamů. Tato změna umožňuje mnohem širší škálu přístrojových nástrojů za chodu.

<a name="NGEN461" />

### <a name="native-image-generator-ngen-pdbs"></a>Nativní obrazgenerátor (NGEN) PDBs

Trasování událostí mezi počítači umožňuje zákazníkům profilovat program v počítači A a podívat se na data profilování pomocí mapování zdrojové čáry v počítači B. Pomocí předchozích verzí rozhraní .NET Framework by uživatel zkopíroval všechny moduly a nativní obrázky z profilovaného zařízení k analytickému počítači, který obsahuje ddb IL, a vytvořil mapování zdroj-na nativní. Zatímco tento proces může fungovat dobře, když jsou soubory relativně malé, například pro telefonní aplikace, soubory mohou být velmi velké na stolních systémech a vyžadují značný čas ke kopírování.

S Ngen PDBs NGen můžete vytvořit PDB, který obsahuje il-to-nativní mapování bez závislosti na IL PDB. V našem scénáři trasování událostí mezi počítači je potřeba pouze zkopírovat nativní pdb bitové kopie, která je generována počítačem A do počítače B, a použít [rozhraní API pro přístup k ladění k](/visualstudio/debugger/debug-interface-access/debug-interface-access-sdk-reference) čtení mapování zdroje-IL pdb a mapování IL-TO-NAtivního obrázku PDB. Kombinace obou mapování poskytuje mapování zdroj na nativní. Vzhledem k tomu, že nativní obraz PDB je mnohem menší než všechny moduly a nativní obrázky, proces kopírování z počítače A do počítače B je mnohem rychlejší.

<a name="v46" />

## <a name="whats-new-in-net-2015"></a>Co je nového v rozhraní .NET 2015

.NET 2015 zavádí rozhraní .NET Framework 4.6 a .NET Core. Některé nové funkce platí pro oba a další funkce jsou specifické pro rozhraní .NET Framework 4.6 nebo .NET Core.

- **ASP.NET Core**

  .NET 2015 obsahuje ASP.NET Core, což je štíhlá implementace .NET pro vytváření moderních cloudových aplikací. ASP.NET Core je modulární, takže můžete zahrnout pouze ty funkce, které jsou potřebné ve vaší aplikaci. Může být hostován ve službě IIS nebo hostován samostatně ve vlastním procesu a můžete spouštět aplikace s různými verzemi rozhraní .NET Framework na stejném serveru. Obsahuje nový konfigurační systém prostředí, který je určen pro nasazení v cloudu.

  MVC, Web API a webové stránky jsou sjednoceny do jedné architektury s názvem MVC 6. Aplikace ASP.NET Core se vytvářejí pomocí nástrojů ve Visual Studiu 2015 nebo novějším. Vaše stávající aplikace budou fungovat na novém rozhraní .NET Framework. ale chcete-li vytvořit aplikaci, která používá MVC 6 nebo SignalR 3, musíte použít systém projektu v sadě Visual Studio 2015 nebo novější.

  Další informace naleznete [v tématu ASP.NET Core](/aspnet/core/).

- **aktualizace ASP.NET**

  - **Rozhraní API založené na úlohách pro vyprázdnění asynchronní odezvy**

    ASP.NET nyní poskytuje jednoduché rozhraní API založené na úlohách <xref:System.Web.HttpResponse.FlushAsync%2A?displayProperty=nameWithType>pro vyprázdnění asynchronní odpovědi , , který `async/await` umožňuje odpovědi vyprázdnění asynchronně pomocí podpory jazyka.

  - **Vazba modelu podporuje metody vrácení úloh.**

    V rozhraní .NET Framework 4.5 ASP.NET přidal funkci Vazby modelu, která umožňovala rozšiřitelný přístup zaměřený na kód k datovým operacím založeným na CRUD na stránkách webových formulářů a uživatelských ovládacích prvcích. Model vazby systému nyní podporuje <xref:System.Threading.Tasks.Task>metody vazby modelu -returning. Tato funkce umožňuje vývojářům webových formulářů získat výhody asynchronnosti s snadnou součástí systému datových vazeb při použití novějších verzí ormů, včetně entity Framework.

    Asynchronní vazba modelu `aspnet:EnableAsyncModelBinding` je řízena nastavením konfigurace.

    ```xml
    <appSettings>
        <add key=" aspnet:EnableAsyncModelBinding" value="true|false" />
    </appSettings>
    ```

    V aplikacích, které cílí na rozhraní .NET Framework 4.6, je výchozí . `true` V aplikacích spuštěných v rozhraní .NET Framework 4.6, které `false` cílí na starší verzi rozhraní .NET Framework, je ve výchozím nastavení. To může být povoleno nastavením `true`nastavení konfigurace na .

  - **Podpora HTTP/2 (Windows 10)**

    [HTTP/2](https://www.wikipedia.org/wiki/HTTP/2) je nová verze protokolu HTTP, která poskytuje mnohem lepší využití připojení (méně zpátečních cest mezi klientem a serverem), což má za následek nižší latenci načítání webových stránek pro uživatele.  Webové stránky (na rozdíl od služeb) mají největší prospěch z protokolu HTTP/2, protože protokol optimalizuje pro více artefaktů požadovaných jako součást jednoho prostředí. Podpora HTTP/2 byla přidána do ASP.NET v rozhraní .NET Framework 4.6. Vzhledem k tomu, že síťové funkce existují ve více vrstvách, byly vyžadovány nové funkce v systému Windows, ve službě IIS a v ASP.NET povolit protokol HTTP/2. Chcete-li používat protokol HTTP/2 s ASP.NET, musíte být spuštěni ve Windows 10.

    HTTP/2 je také podporována a zapnuta ve výchozím nastavení pro Windows <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> 10 Univerzální platforma Windows (UPW) aplikace, které používají rozhraní API.

    Aby bylo možné poskytnout způsob, jak používat [PUSH_PROMISE](https://http2.github.io/http2-spec/#PUSH_PROMISE) funkce v ASP.NET <xref:System.Web.HttpResponse.PushPromise%28System.String%29> aplikace, byla do <xref:System.Web.HttpResponse.PushPromise%28System.String%2CSystem.String%2CSystem.Collections.Specialized.NameValueCollection%29> <xref:System.Web.HttpResponse> třídy přidána nová metoda se dvěma přetíženími a , .

    > [!NOTE]
    > Zatímco ASP.NET Core podporuje HTTP/2, podpora funkce PUSH PROMISE ještě nebyla přidána.

    Prohlížeč a webový server (IIS v systému Windows) provést veškerou práci. Nemusíte dělat žádné těžké zvedání pro vaše uživatele.

    Většina [hlavních prohlížečů podporuje protokol HTTP/2](https://www.wikipedia.org/wiki/HTTP/2), takže je pravděpodobné, že uživatelé budou mít prospěch z podpory HTTP/2, pokud ji váš server podporuje.

  - **Podpora protokolu tokenové vazby**

    Společnosti Microsoft a Google spolupracují na novém přístupu k ověřování, který se nazývá [Token Binding Protocol](https://github.com/TokenBinding/Internet-Drafts). Předpokladem je, že ověřovací tokeny (v mezipaměti prohlížeče) mohou být ukradeny a používány zločinci pro přístup k jinak zabezpečeným prostředkům (například k vašemu bankovnímu účtu) bez nutnosti hesla nebo jiných privilegovaných znalostí. Nový protokol má za cíl zmírnit tento problém.

    Token Binding Protocol bude implementován ve Windows 10 jako funkce prohlížeče. ASP.NET aplikace se budou účastnit protokolu, takže ověřovací tokeny jsou ověřeny jako legitimní. Implementace klienta a serveru vytvářejí ochranu mezi koncovými částmi určenou protokolem.

  - **Randomizované algoritmy hash řetězce**

    Rozhraní .NET Framework 4.5 zavedlo [algoritmus hash randomizovaného řetězce](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md). Však to nebylo podporováno ASP.NET z důvodu některých ASP.NET funkce závisí na stabilní hash kód. V rozhraní .NET Framework 4.6 jsou nyní podporovány algoritmy hash randomizovaných řetězců. Chcete-li tuto funkci `aspnet:UseRandomizedStringHashAlgorithm` povolit, použijte nastavení konfigurace.

    ```xml
    <appSettings>
        <add key="aspnet:UseRandomizedStringHashAlgorithm" value="true|false" />
    </appSettings>
    ```

- **ADO.NET**

  Rozhraní ADO .NET nyní podporuje funkci Vždy šifrované dostupné v SQL Serveru 2016 Community Technology Preview 2 (CTP2). S vždy šifrované, SQL Server může provádět operace na šifrovaná data a nejlepší ze všech šifrovací klíč se nachází s aplikací uvnitř důvěryhodného prostředí zákazníka a nikoli na serveru. Vždy šifrované zabezpečuje zákaznická data, takže dba nemají přístup k datům ve formátu prostého textu. Šifrování a dešifrování dat probíhá transparentně na úrovni ovladače, což minimalizuje změny, které je třeba provést u stávajících aplikací. Podrobnosti naleznete [v tématech Vždy šifrované (Database Engine)](/sql/relational-databases/security/encryption/always-encrypted-database-engine) a [vždy šifrované (vývoj klienta)](/sql/relational-databases/security/encryption/always-encrypted-client-development).

- **64bitový kompilátor JIT pro spravovaný kód**

  Rozhraní .NET Framework 4.6 obsahuje novou verzi 64bitového kompilátoru JIT (původně s kódovým názvem RyuJIT). Nový 64bitový kompilátor poskytuje významné zlepšení výkonu oproti staršímu 64bitovému kompilátoru JIT. Nový 64bitový kompilátor je povolen pro 64bitové procesy spuštěné nad rozhraním .NET Framework 4.6. Vaše aplikace poběží v 64bitovém procesu, pokud je zkompilován jako 64bitový nebo AnyCPU a běží na 64bitovém operačním systému. Zatímco byla věnována pozornost tomu, aby přechod na nový kompilátor byl co nejtransparentnější, změny v chování jsou možné.

  Nový 64bitový kompilátor JIT také obsahuje funkce akcelerace hardwarových SIMD ve spojení s typy s podporou SIMD v <xref:System.Numerics> oboru názvů, což může přinést dobré zlepšení výkonu.

- **Vylepšení montážního nakladače**

  Nakladač sestavy nyní používá paměť efektivněji uvolněním sestavení IL po načtení odpovídajícího obrazu NGEN. Tato změna snižuje virtuální paměť, což je výhodné zejména pro velké 32bitové aplikace (například Visual Studio) a také šetří fyzickou paměť.

- **Změny knihovny základních tříd**

  Mnoho nových rozhraní API byly přidány kolem rozhraní .NET Framework 4.6 povolit klíčové scénáře. Patří mezi ně následující změny a dodatky:

  - **Implementace>\<IReadOnlyCollection**

    Další kolekce <xref:System.Collections.Generic.IReadOnlyCollection%601> implementovat, jako <xref:System.Collections.Generic.Queue%601> je například a <xref:System.Collections.Generic.Stack%601>.

  - **CultureInfo.CurrentCulture a CultureInfo.CurrentUICulture**

    <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> Vlastnosti <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> a jsou nyní spíše pro čtení a zápis než jen pro čtení. Pokud těmto vlastnostem přiřadíte nový <xref:System.Globalization.CultureInfo> objekt, změní `Thread.CurrentThread.CurrentCulture` se také aktuální jazyková verze `Thread.CurrentThread.CurrentUICulture` vlákna definovaná vlastností a aktuální jazykovou verzí vlákna uživatelského rozhraní definovanou vlastnostmi.

  - **Vylepšení uvolňování paměti (GC)**

    Třída <xref:System.GC> nyní <xref:System.GC.TryStartNoGCRegion%2A> obsahuje <xref:System.GC.EndNoGCRegion%2A> a metody, které umožňují zakázat uvolňování paměti během provádění kritické cesty.

    Nové přetížení <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%2CSystem.Boolean%29?displayProperty=nameWithType> metody umožňuje určit, zda haldy malý objekt a haldy velkých objektů jsou zametány a komprimovány nebo pouze zatažené.

  - **Typy s podporou SIMD**

    Obor <xref:System.Numerics> názvů nyní obsahuje několik typů s podporou <xref:System.Numerics.Matrix3x2>SIMD, například <xref:System.Numerics.Matrix4x4>, <xref:System.Numerics.Plane>, <xref:System.Numerics.Quaternion>, <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, a <xref:System.Numerics.Vector4>.

    Vzhledem k tomu, že nový 64bitový kompilátor JIT obsahuje také funkce akcelerace hardwarových SIMD, existují obzvláště významná vylepšení výkonu při použití typů s podporou SIMD s novým 64bitovým kompilátorem JIT.

  - **Aktualizace kryptografie**

    Rozhraní <xref:System.Security.Cryptography?displayProperty=nameWithType> API je aktualizováno tak, aby podporovalo [rozhraní API kryptografie Windows CNG](/windows/desktop/SecCNG/cng-reference). Předchozí verze rozhraní .NET Framework se spoléhaly výhradně na [starší verzi rozhraní API kryptografie systému Windows](/windows/desktop/SecCrypto/cryptography-portal) jako základ pro <xref:System.Security.Cryptography?displayProperty=nameWithType> implementaci. Měli jsme požadavky na podporu Rozhraní API Na CNG, protože podporuje [moderní kryptografické algoritmy](/windows/desktop/SecCNG/cng-features#suite-b-support), které jsou důležité pro určité kategorie aplikací.

    Rozhraní .NET Framework 4.6 obsahuje následující nová vylepšení pro podporu rozhraní API kryptografie systému Windows CNG:

    - Sada rozšiřujících metod pro certifikáty X509 a `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)`, které vracejí implementaci založenou na CNG, nikoli implementaci založenou na CAPI, pokud je to možné. (Některé čipové karty atd., stále vyžadují CAPI a api zpracovat záložní).

    - Třída, <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> která poskytuje cng implementaci algoritmu RSA.

    - Vylepšení rsa rozhraní API tak, aby běžné akce již nevyžadují přetypování. Například šifrování dat pomocí <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> objektu vyžaduje kód, jako je následující v předchozích verzích rozhraní .NET Framework.

      [!code-csharp[WhatsNew.Casting#1](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#1)]
      [!code-vb[WhatsNew.Casting#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#1)]

      Kód, který používá nová rozhraní API kryptografie v rozhraní .NET Framework 4.6 lze přepsat následujícím způsobem, aby se zabránilo přetypování.

      [!code-csharp[WhatsNew.Casting#2](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#2)]
      [!code-vb[WhatsNew.Casting#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#2)]

  - **Podpora pro převod dat a časů do nebo z Unixu**

    Do <xref:System.DateTimeOffset> struktury byly přidány následující nové metody, které podporují převod hodnot data a času na čas unixu nebo z něj:

    - <xref:System.DateTimeOffset.FromUnixTimeSeconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.FromUnixTimeMilliseconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.ToUnixTimeSeconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.ToUnixTimeMilliseconds%2A?displayProperty=nameWithType>

  - **Přepínače kompatibility**

    Třída <xref:System.AppContext> přidává novou funkci kompatibility, která umožňuje autorům knihovny poskytnout jednotný mechanismus odhlášení pro nové funkce pro své uživatele. Stanoví volně vázanou smlouvu mezi součástmi za účelem sdělení žádosti o výjimku. Tato funkce je obvykle důležité při změně existující funkce. Naopak již existuje implicitní přihlášení pro nové funkce.

    S <xref:System.AppContext>, knihovny definovat a vystavit přepínače kompatibility, zatímco kód, který závisí na nich můžete nastavit tyto přepínače ovlivnit chování knihovny. Ve výchozím nastavení knihovny poskytují nové funkce a mění je pouze (to znamená, že poskytují předchozí funkce) pokud je přepínač nastaven.

    Aplikace (nebo knihovna) může deklarovat hodnotu <xref:System.Boolean> přepínače (což je vždy hodnota), kterou definuje závislá knihovna. Přepínač je vždy `false`implicitně . Nastavení přepínače `true` na umožňuje. Explicitně nastavení `false` přepínače poskytuje nové chování.

    ```csharp
    AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", true);
    ```

    ```vb
    AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", True)
    ```

    Knihovna musí zkontrolovat, zda spotřebitel deklaroval hodnotu přepínače, a poté na něj vhodně jednat.

    ```csharp
    if (!AppContext.TryGetSwitch("Switch.AmazingLib.ThrowOnException", out shouldThrow))
    {
        // This is the case where the switch value was not set by the application.
        // The library can choose to get the value of shouldThrow by other means.
        // If no overrides nor default values are specified, the value should be 'false'.
        // A false value implies the latest behavior.
    }

    // The library can use the value of shouldThrow to throw exceptions or not.
    if (shouldThrow)
    {
        // old code
    }
    else
    {
        // new code
    }
    ```

    ```vb
    If Not AppContext.TryGetSwitch("Switch.AmazingLib.ThrowOnException", shouldThrow) Then
        ' This is the case where the switch value was not set by the application.
        ' The library can choose to get the value of shouldThrow by other means.
        ' If no overrides nor default values are specified, the value should be 'false'.
        ' A false value implies the latest behavior.
    End If

    ' The library can use the value of shouldThrow to throw exceptions or not.
    If shouldThrow Then
        ' old code
    Else
        ' new code
    End If
    ```

    Je výhodné používat konzistentní formát pro přepínače, protože se jedná o formální smlouvu vystavenou knihovnou. Následují dva zřejmé formáty.

    - *Přepněte*. *oboru názvů*. *název přepínače*

    - *Přepněte*. *knihovny*. *název přepínače*

  - **Změny asynchronního vzoru založeného na úlohách (TAP)**

    Pro aplikace, které cílí na <xref:System.Threading.Tasks.Task> rozhraní <xref:System.Threading.Tasks.Task%601> .NET Framework 4.6 a objekty dědí jazykovou verzi a jazykovou verzi uživatelského rozhraní volajícího vlákna. Chování aplikací, které cílí na předchozí verze rozhraní .NET Framework nebo které necílí na konkrétní verzi rozhraní .NET Framework, není ovlivněno. Další informace naleznete v části "Jazykové verze a úlohy asynchronní operace" v tématu <xref:System.Globalization.CultureInfo> třídy.

    Třída <xref:System.Threading.AsyncLocal%601?displayProperty=nameWithType> umožňuje reprezentovat okolní data, která je místní pro daný tok `async` asynchronního řízení, jako je například metoda. Lze použít k uchování dat ve vláknech. Můžete také definovat metodu zpětného volání, která je upozorňována vždy, když se změní okolní data, protože <xref:System.Threading.AsyncLocal%601.Value%2A?displayProperty=nameWithType> vlastnost byla explicitně změněna, nebo proto, že vlákno narazilo na přechod kontextu.

    Do asynchronního vzoru založeného na úlohách (TAP) byly přidány tři metody pohodlí <xref:System.Threading.Tasks.Task.CompletedTask%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.FromCanceled%2A?displayProperty=nameWithType>, a <xref:System.Threading.Tasks.Task.FromException%2A?displayProperty=nameWithType>, které mají vrátit dokončené úkoly v určitém stavu.

    Třída <xref:System.IO.Pipes.NamedPipeClientStream> nyní podporuje asynchronní komunikaci <xref:System.IO.Pipes.NamedPipeClientStream.ConnectAsync%2A>s novým . Metoda.

  - **EventSource nyní podporuje zápis do protokolu událostí**

    Nyní můžete použít <xref:System.Diagnostics.Tracing.EventSource> třídu k protokolování administrativních nebo provozních zpráv do protokolu událostí, kromě všech existujících relací ETW vytvořených v počítači. V minulosti jste museli použít Microsoft.Diagnostics.Tracing.EventSource NuGet balíček pro tuto funkci. Tato funkce je nyní integrována do rozhraní .NET Framework 4.6.

    Balíček NuGet i rozhraní .NET Framework 4.6 byly aktualizovány následujícími funkcemi:

    - **Dynamické události**

      Umožňuje události definované "průběžně" bez vytváření metod událostí.

    - **Bohatá návratnost**

      Umožňuje předat speciálně přiřazené třídy a pole a primitivní typy jako datovou část.

    - **Sledování aktivity**

      Způsobí, že události Start a Stop označí události mezi nimi id, které představuje všechny aktuálně aktivní aktivity.

    Pro podporu těchto funkcí <xref:System.Diagnostics.Tracing.EventSource.Write%2A> byla přetížená metoda <xref:System.Diagnostics.Tracing.EventSource> přidána do třídy.

- **Windows Presentation Foundation (WPF)**

  - **Vylepšení HDPI**

    Podpora HDPI v WPF je nyní lepší v rozhraní .NET Framework 4.6. Byly provedeny změny zaokrouhlení rozložení, aby se snížilpočet výskytů oříznutí v ovládacích prvcích s ohraničením. Ve výchozím nastavení je tato <xref:System.Runtime.Versioning.TargetFrameworkAttribute> funkce povolena pouze v případě, že je nastavena na hodnotu .NET 4.6.  Aplikace, které cílí na starší verze rozhraní, ale jsou spuštěny v rozhraní .NET Framework 4.6, se mohou přihlásit k novému chování přidáním následujícího řádku do sekce [ \<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) souboru app.config:

    ```xml
    <AppContextSwitchOverrides
    value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false"
    />
    ```

    WPF okna tažné více monitorů s různými nastaveními DPI (Nastavení Více DPI) jsou nyní zcela vykresleny bez zatemnění oblastí. Toto chování můžete odhlásit tak, že `<appSettings>` do části souboru app.config zakážete následující řádek:

    ```xml
    <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    ```

    Do aplikace byla přidána podpora automatického načítání <xref:System.Windows.Input.Cursor?displayProperty=nameWithType>pravého kurzoru na základě nastavení DPI.

  - **Dotek je lepší**

    V rozhraní .NET Framework 4.6 byly vyřešeny zákaznické zprávy o [připojení,](https://connect.microsoft.com/VisualStudio/feedback/details/903760/) které dotykem vytváří nepředvídatelné chování. Prahová hodnota dvojitého klepnutí pro aplikace pro Windows Store a WPF je teď stejná ve Windows 8.1 a vyšší.

  - **Průhledná podřízená podpora okna**

    WPF v rozhraní .NET Framework 4.6 podporuje transparentní podřízená okna ve Windows 8.1 a vyšší. To umožňuje vytvářet neobdélníková a průhledná podřízená okna v oknech nejvyšší úrovně. Tuto funkci můžete povolit <xref:System.Windows.Interop.HwndSourceParameters.UsesPerPixelTransparency%2A?displayProperty=nameWithType> nastavením vlastnosti na . `true`

- **Windows Communication Foundation (WCF)**

  - **Podpora pro SSL**

    WCF nyní podporuje SSL verze TLS 1.1 a TLS 1.2, kromě SSL 3.0 a TLS 1.0, při použití NetTcp s zabezpečením přenosu a ověřování klienta. Nyní je možné vybrat, který protokol použít, nebo zakázat staré méně zabezpečené protokoly. To lze provést nastavením <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A> vlastnosti nebo přidáním následujícího do konfiguračního souboru.

    ```xml
    <netTcpBinding>
        <binding>
          <security mode= "None|Transport|Message|TransportWithMessageCredential" >
              <transport clientCredentialType="None|Windows|Certificate"
                        protectionLevel="None|Sign|EncryptAndSign"
                        sslProtocols="Ssl3|Tls1|Tls11|Tls12">
                </transport>
          </security>
        </binding>
    </netTcpBinding>
    ```

  - **Odesílání zpráv pomocí různých připojení HTTP**

    WCF nyní umožňuje uživatelům zajistit, že některé zprávy jsou odesílány pomocí různých základních připojení HTTP. Toto lze provést dvěma způsoby:

    - **Použití předpony názvu skupiny připojení**

      Uživatelé mohou zadat řetězec, který wcf použije jako předponu pro název skupiny připojení. Dvě zprávy s různými předponami jsou odesílány pomocí různých základních připojení HTTP. Předponu nastavíte přidáním páru klíč/hodnota <xref:System.ServiceModel.Channels.Message.Properties%2A?displayProperty=nameWithType> do vlastnosti zprávy. Klíč je "HttpTransportConnectionGroupNamePrefix"; hodnota je požadovaná předpona.

    - **Použití různých továren kanálů**

      Uživatelé mohou také povolit funkci, která zajišťuje, že zprávy odeslané pomocí kanálů vytvořených různými továrnami kanálů budou používat různá základní připojení HTTP. Chcete-li tuto funkci povolit, `true`musí uživatelé nastavit následující: `appSetting`

      ```xml
      <appSettings>
          <add key="wcf:httpTransportBinding:useUniqueConnectionPoolPerFactory" value="true" />
      </appSettings>
      ```

- **Nadace pracovního postupu systému Windows (WWF)**

  Nyní můžete určit počet sekund, po které bude služba pracovního postupu držet požadavek na operaci mimo pořadí, pokud je před vypršením požadavku nevyřešená záložka "bez protokolu". Záložka "non-protokol" je záložka, která nesouvisí s nevyřízenými aktivitami příjmu. Některé aktivity vytvářejí záložky bez protokolu v rámci jejich implementace, takže nemusí být zřejmé, že existuje záložka bez protokolu. Patří mezi ně stát a pick. Pokud tedy máte službu pracovního postupu implementovanou se stavovým počítačem nebo obsahující aktivitu vyskladnění, budete mít s největší pravděpodobností záložky bez protokolu. Interval určíte přidáním řádku, jako `appSettings` je následující, do oddílu souboru app.config:

  ```xml
  <add key="microsoft:WorkflowServices:FilterResumeTimeoutInSeconds" value="60"/>
  ```

  Výchozí hodnota je 60 sekund. Pokud `value` je nastavena na 0, požadavky mimo pořadí jsou okamžitě odmítnuty s chybou s textem, který vypadá takto:

  ```console
  Operation 'Request3|{http://tempuri.org/}IService' on service instance with identifier '2b0667b6-09c8-4093-9d02-f6c67d534292' cannot be performed at this time. Please ensure that the operations are performed in the correct order and that the binding in use provides ordered delivery guarantees.
  ```

  Jedná se o stejnou zprávu, kterou obdržíte, pokud je přijata zpráva operace mimo pořadí a neexistují žádné záložky bez protokolu.

  Pokud je hodnota `FilterResumeTimeoutInSeconds` prvku nenulová, existují záložky bez protokolu a vyprší časový limit, operace se nezdaří se zprávou časového limitu.

- **Transakce**

  Nyní můžete zahrnout identifikátor distribuované transakce pro transakci, <xref:System.Transactions.TransactionException> která způsobila výjimku odvozenou z vyvolat. To provést přidáním následujícího `appSettings` klíče do části souboru app.config:

  ```xml
  <add key="Transactions:IncludeDistributedTransactionIdInExceptionMessage" value="true"/>
  ```

  Výchozí hodnota je `false`.

- **Sítě**

  - **Opětovné použití soketu**

    Systém Windows 10 obsahuje nový síťový algoritmus s vysokou škálovatelností, který lépe využívá prostředky počítače opětovným použitím místních portů pro odchozí připojení TCP. Rozhraní .NET Framework 4.6 podporuje nový algoritmus, který umožňuje aplikacím .NET využít výhod nového chování. V předchozích verzích systému Windows byl umělý limit souběžného připojení (obvykle 16 384, výchozí velikost dynamického rozsahu portů), což může omezit škálovatelnost služby tím, že způsobí vyčerpání portu při zatížení.

    V rozhraní .NET Framework 4.6 byla přidána dvě rozhraní API, která umožňují opakované použití portu, což účinně odebere limit 64 kB pro souběžná připojení:

    - Hodnota <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> výčtu.

    - Pozemek. <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType>

    Ve výchozím <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> nastavení `false` je `HWRPortReuseOnSocketBind` vlastnost, `HKLM\SOFTWARE\Microsoft\.NETFramework\v4.0.30319` pokud je hodnota klíče registru nastavena na 0x1. Chcete-li povolit opakované použití místního <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> `true`portu v připojeních HTTP, nastavte vlastnost na . To způsobí, že všechna odchozí <xref:System.Net.Http.HttpClient> <xref:System.Net.HttpWebRequest> připojení soketu TCP z a použít novou možnost soketu systému Windows 10, [SO_REUSE_UNICASTPORT](/windows/desktop/WinSock/sol-socket-socket-options), který umožňuje opětovné použití místního portu.

    Vývojáři, kteří píší pouze sokety aplikace můžete určit <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> možnost při volání metody, například <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> tak, aby odchozí sokety znovu použít místní porty během vazby.

  - **Podpora mezinárodních doménových jmen a PunyCode**

    Do <xref:System.Uri> třídy <xref:System.Uri.IdnHost%2A>byla přidána nová vlastnost , která má lépe podporovat mezinárodní názvy domén a PunyCode.

- **Změna velikosti ovládacích prvků v systému Windows Forms.**

  Tato funkce byla rozšířena v rozhraní .NET <xref:System.Windows.Forms.DomainUpDown> <xref:System.Windows.Forms.NumericUpDown>Framework <xref:System.Windows.Forms.DataGridViewComboBoxColumn> <xref:System.Windows.Forms.DataGridViewColumn> 4.6 tak, aby zahrnovala typy , , a a <xref:System.Windows.Forms.ToolStripSplitButton> obdélník určený <xref:System.Drawing.Design.PaintValueEventArgs.Bounds%2A> vlastností použitou při kreslení . <xref:System.Drawing.Design.UITypeEditor>

  Jedná se o funkci opt-in. Chcete-li jej `EnableWindowsFormsHighDpiAutoResizing` povolit, nastavte prvek v `true` souboru konfigurace aplikace (app.config):

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

- **Podpora kódování znakových stránek**

  .NET Core primárně podporuje kódování Unicode a ve výchozím nastavení poskytuje omezenou podporu kódování znakových stránek. Můžete přidat podporu pro kódování znakových stránek, které jsou k dispozici v rozhraní .NET Framework, ale nejsou podporovány v rozhraní .NET Core registrací kódování znakové stránky pomocí <xref:System.Text.Encoding.RegisterProvider%2A?displayProperty=nameWithType> metody. Další informace naleznete v tématu <xref:System.Text.CodePagesEncodingProvider?displayProperty=nameWithType>.

- **.NET Native**

  Aplikace pro Windows pro Windows 10, které cílí na .NET Core a jsou zapsány v Jazyce C# nebo Visual Basicu, můžou využít novou technologii, která kompiluje aplikace do nativního kódu, nikoli do IL. Vyrábějí aplikace charakterizované rychlejším spouštěním a spouštěním. Další informace naleznete [v tématu Kompilace aplikací s nativním rozhraním .NET](../net-native/index.md). Přehled nativní .NET, který zkoumá, jak se liší od kompilace JIT a NGEN a co to znamená pro váš kód, naleznete [v tématu .NET Native a Kompilace](../net-native/net-native-and-compilation.md).

  Vaše aplikace se ve výchozím nastavení kompitují do nativního kódu, když je zkompilujete pomocí Visual Studia 2015 nebo novějšího. Další informace naleznete [v tématu Začínáme s nativním programem .NET](../net-native/getting-started-with-net-native.md).

  Pro podporu ladění nativních aplikací .NET byla do nespravovaného rozhraní API ladění přidána řada nových rozhraní a výčtů. Další informace naleznete v tématu [Ladění (Unmanaged API Reference).](../unmanaged-api/debugging/index.md)

- **Balíčky rozhraní Open source .NET Framework**

  Balíčky .NET Core, jako jsou neměnné kolekce, [rozhraní API SIMD](https://www.nuget.org/packages/Microsoft.Bcl.Simd)a <xref:System.Net.Http> síťová rozhraní API, jako jsou například ty, které se nacházejí v oboru názvů, jsou nyní k dispozici jako balíčky s otevřeným zdrojovým kódem na [GitHubu](https://github.com/). Chcete-li získat přístup ke kódu, přečtěte si [stránku .NET na GitHubu](https://github.com/dotnet/runtime). Další informace a způsob, jak přispět k těmto balíčkům, najdete v tématu [.NET Core a Open-Source](../get-started/net-core-and-open-source.md), [.NET Home Page na GitHubu](https://github.com/dotnet/home).

<a name="v452" />

## <a name="whats-new-in-net-framework-452"></a>Co je nového v rozhraní .NET Framework 4.5.2

- **Nová api pro ASP.NET aplikace.** Nové <xref:System.Web.HttpResponse.AddOnSendingHeaders%2A?displayProperty=nameWithType> a <xref:System.Web.HttpResponseBase.AddOnSendingHeaders%2A?displayProperty=nameWithType> metody umožňují kontrolovat a upravovat hlavičky odpovědí a stavový kód, protože odpověď je vyprázdněna do klientské aplikace. Zvažte použití těchto <xref:System.Web.HttpApplication.PreSendRequestHeaders> metod <xref:System.Web.HttpApplication.PreSendRequestContent> namísto a události; jsou účinnější a spolehlivější.

  Metoda <xref:System.Web.Hosting.HostingEnvironment.QueueBackgroundWorkItem%2A?displayProperty=nameWithType> umožňuje naplánovat malé pracovní položky na pozadí. ASP.NET sleduje tyto položky a zabrání iis z náhlé ukončení pracovního procesu, dokud všechny pracovní položky na pozadí byly dokončeny. Tuto metodu nelze volat mimo doménu ASP.NET spravované aplikace.

  Nové <xref:System.Web.HttpResponse.HeadersWritten?displayProperty=nameWithType> a <xref:System.Web.HttpResponseBase.HeadersWritten?displayProperty=nameWithType> vlastnosti vrátí logické hodnoty, které označují, zda byly zapsány hlavičky odpovědí. Tyto vlastnosti můžete použít k ujistěte se, že volání rozhraní API, jako <xref:System.Web.HttpResponse.StatusCode%2A?displayProperty=nameWithType> je například (které vyvolat výjimky, pokud záhlaví byly zapsány) bude úspěšné.

- **Změna velikosti ovládacích prvků v systému Windows Forms.** Tato funkce byla rozbalena. Nyní můžete použít nastavení systémového DPI ke změně velikosti součástí následujících dalších ovládacích prvků (například rozevírací šipka v polích se seznamem):

  - <xref:System.Windows.Forms.ComboBox>
  - <xref:System.Windows.Forms.ToolStripComboBox>
  - <xref:System.Windows.Forms.ToolStripMenuItem>
  - <xref:System.Windows.Forms.Cursor>
  - <xref:System.Windows.Forms.DataGridView>
  - <xref:System.Windows.Forms.DataGridViewComboBoxColumn>

  Jedná se o funkci opt-in. Chcete-li jej `EnableWindowsFormsHighDpiAutoResizing` povolit, nastavte prvek v `true` souboru konfigurace aplikace (app.config):

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

- **Nová funkce pracovního postupu.** Správce prostředků, který používá <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> metodu (a <xref:System.Transactions.IPromotableSinglePhaseNotification> proto implementuje <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> rozhraní) můžete použít novou metodu požádat o následující:

  - Převést transakci na transakci koordinátora distribuovaných transakcí (MSDTC) společnosti Microsoft.

  - Nahradit <xref:System.Transactions.IPromotableSinglePhaseNotification> <xref:System.Transactions.ISinglePhaseNotification>, což je trvalé zařazení, které podporuje jednofázové potvrzení.

  To lze provést v rámci stejné domény aplikace a nevyžaduje žádné další nespravovaný kód pro interakci s MSDTC k provedení propagace. Nová metoda může být volána pouze v <xref:System.Transactions?displayProperty=nameWithType> případě, <xref:System.Transactions.IPromotableSinglePhaseNotification> `Promote` že je vynikající volání z na metodu, která je implementována promotable zařazení.

- **Vylepšení profilování.** Následující nová nespravovaná profilovací prostředí API poskytují robustnější profilování:

  - [COR_PRF_ASSEMBLY_REFERENCE_INFO – struktura](../unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)
  - [Výčet COR_PRF_HIGH_MONITOR](../unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)
  - [Metoda GetAssemblyReferences](../unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
  - [Metoda GetEventMask2](../unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
  - [Metoda SetEventMask2](../unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
  - [Metoda AddAssemblyReference](../unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)

  Předchozí `ICorProfiler` implementace podporovaly opožděné načítání závislých sestavení. Nová profilovací prostředí API vyžadují závislá sestavení, která jsou vložena profilerem, aby byla okamžitě načítatelná, namísto toho, aby byla načtena po úplné inicializování aplikace. Tato změna nemá vliv na `ICorProfiler` uživatele existujících api.

- **Vylepšení ladění.** Následující nová nespravovaná ladění API poskytují lepší integraci s profilerem. Nyní můžete přistupovat k metadatům vloženým profilerem, stejně jako k místním proměnným a kódu vytvořenému požadavky rejitkompozátoru při ladění výpisu.

  - [Metoda SetWriteableMetadataUpdateMode](../unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)
  - [Metoda EnumerateLocalVariablesEx](../unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)
  - [Metoda GetLocalVariableEx](../unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)
  - [Metoda GetCodeEx](../unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)
  - [Metoda GetActiveReJitRequestILCode](../unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)
  - [Metoda GetInstrumentedILMap](../unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)

- **Změny trasování událostí.** Rozhraní .NET Framework 4.5.2 umožňuje trasování aktivit mimo proces, trasování událostí pro Windows (ETW) pro větší plochu. To umožňuje dodavatelům advanced power managementu (APM) poskytovat zjednodušené nástroje, které přesně sledují náklady na jednotlivé požadavky a aktivity, které protínají vlákna.  Tyto události jsou vyvolány pouze v případě, že řadiče ETW povolit; proto změny nemají vliv na dříve zapsaný kód ETW nebo kód, který běží s ETW zakázáno.

- **Propagace transakce a její převedení na trvalé zařazení**

  <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType>je nové rozhraní API přidané do rozhraní .NET Framework 4.5.2 a 4.6:

  ```csharp
  [System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]
  public Enlistment PromoteAndEnlistDurable(Guid resourceManagerIdentifier,
                                            IPromotableSinglePhaseNotification promotableNotification,
                                            ISinglePhaseNotification enlistmentNotification,
                                            EnlistmentOptions enlistmentOptions)
  ```

  ```vb
  <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")>
  public Function PromoteAndEnlistDurable(resourceManagerIdentifier As Guid,
                                          promotableNotification As IPromotableSinglePhaseNotification,
                                          enlistmentNotification As ISinglePhaseNotification,
                                          enlistmentOptions As EnlistmentOptions) As Enlistment
  ```

  Metoda může být použita zařazení, který byl <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> dříve vytvořen <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> v reakci na metodu. Požádá `System.Transactions` o podporu transakce na transakci MSDTC a "převést" promotable zařazení na trvalé zařazení. Po úspěšném dokončení této <xref:System.Transactions.IPromotableSinglePhaseNotification> metody již nebude rozhraní `System.Transactions`odkazováno aplikacemi a všechna budoucí <xref:System.Transactions.ISinglePhaseNotification> oznámení budou doručena do poskytnutého rozhraní. Dotyčné zařazení musí působit jako trvalé zařazení, které podporuje protokolování transakcí a obnovení. Podrobnosti <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType> naleznete v části Podrobnosti. Kromě toho musí zařazení podporovat <xref:System.Transactions.ISinglePhaseNotification>.  Tato metoda může být volána *pouze* při zpracování <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> volání. Pokud tomu tak není, <xref:System.Transactions.TransactionException> je vyvolána výjimka.

<a name="v451" />

## <a name="whats-new-in-net-framework-451"></a>Co je nového v rozhraní .NET Framework 4.5.1

**Aktualizace z dubna 2014**:

- [Visual Studio 2013 Update 2](https://go.microsoft.com/fwlink/p/?LinkId=393658) obsahuje aktualizace šablon knihovny přenosných tříd pro podporu těchto scénářů:

  - V přenosných knihovnách, které cílí na Windows 8.1, Windows Phone 8.1 a Windows Phone Silverlight 8.1, můžete použít soubory WINDOWS Runtime.

  - XAML (typy Windows.UI.XAML) můžete zahrnout do přenosných knihoven, když cílíte na Windows 8.1 nebo Windows Phone 8.1. Podporovány jsou následující šablony XAML: Prázdná stránka, Slovník prostředků, Ovládací prvek šablony a Uživatelské řízení.

  - Můžete vytvořit přenosnou komponentu Prostředí Windows Runtime (.soubor winmd) pro použití v aplikacích pro Store, které cílí na Windows 8.1 a Windows Phone 8.1.

  - Můžete znovu zacílit na knihovnu tříd pro Windows Store nebo Windows Phone Store, jako je knihovna přenosných tříd.

  Další informace o těchto změnách naleznete v [tématu Portable Class Library](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).

- Sada obsahu rozhraní .NET Framework nyní obsahuje dokumentaci pro nativní rozhraní .NET, což je technologie předkompilace pro vytváření a nasazování aplikací pro Windows. .NET Native zkompiluje vaše aplikace přímo do nativního kódu, nikoli do zprostředkujícího jazyka (IL), pro lepší výkon. Podrobnosti naleznete v [tématu Kompilace aplikací s nativním rozhraním .NET](../net-native/index.md).

- [Referenční zdroj rozhraní .NET Framework](https://referencesource.microsoft.com/) poskytuje nové možnosti procházení a rozšířené funkce. Nyní můžete procházet zdrojový kód rozhraní .NET Framework online, [stáhnout odkaz](https://referencesource.microsoft.com/download.html) pro prohlížení offline a krokovat zdroje (včetně oprav a aktualizací) během ladění. Další informace naleznete v položce blogu [Nový vzhled pro referenční zdroj .NET](https://devblogs.microsoft.com/dotnet/a-new-look-for-net-reference-source/).

Mezi nové funkce a vylepšení základních tříd v rozhraní .NET Framework 4.5.1 patří:

- Automatické přesměrování vazeb pro sestavy. Počínaje Visual Studio 2013, když zkompilujete aplikaci, která se zaměřuje na rozhraní .NET Framework 4.5.1, přesměrování vazby může být přidána do konfiguračního souboru aplikace, pokud vaše aplikace nebo její součásti odkazují na více verzí stejného sestavení. Tuto funkci můžete povolit také pro projekty, které cílí na starší verze rozhraní .NET Framework. Další informace naleznete v [tématu How to: Enable and Disable Automatic Binding Redirection](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md).

- Schopnost shromažďovat diagnostické informace, které vývojářům pomáhají zlepšit výkon serverových a cloudových aplikací. Další informace naleznete <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityId%2A> v <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityIdCore%2A> tématu <xref:System.Diagnostics.Tracing.EventSource> a metody ve třídě.

- Možnost explicitně komprimovat haldy velkých objektů (LOH) během uvolňování paměti. Další informace naleznete <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> v ubytovacím zařízení.

- Další vylepšení výkonu, jako je ASP.NET pozastavení aplikace, vylepšení JIT s více jádry a rychlejší spuštění aplikace po aktualizaci rozhraní .NET Framework. Podrobnosti najdete v [oznámení .NET Framework 4.5.1](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/) a [ASP.NET aplikace pozastavit](https://devblogs.microsoft.com/dotnet/asp-net-app-suspend-responsive-shared-net-web-hosting/) příspěvek blogu.

Mezi vylepšení formulářů Windows patří:

- Změna velikosti ovládacích prvků v systému Windows Forms. Nastavení systémového DPI můžete použít ke změně velikosti součástí ovládacích prvků (například ikon, které se zobrazují v mřížce vlastností) tak, že se přihlásíte pomocí položky v konfiguračním souboru aplikace (app.config) pro vaši aplikaci. Tato funkce je aktuálně podporována v následujících ovládacích prvcích systému Windows:

  - <xref:System.Windows.Forms.PropertyGrid>
  - <xref:System.Windows.Forms.TreeView>
  - Některé aspekty <xref:System.Windows.Forms.DataGridView> (viz [nové funkce v 4.5.2](#v452) pro další podporované ovládací prvky)

  Chcete-li tuto funkci \<povolit, přidejte do konfiguračního souboru `EnableWindowsFormsHighDpiAutoResizing` (app.config) nový prvek nastavení aplikaceNastavení> a nastavte prvek na `true`:

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

Mezi vylepšení při ladění aplikací rozhraní .NET Framework ve Visual Studiu 2013 patří:

- Vrátí hodnoty v ladicím programu sady Visual Studio. Při ladění spravované aplikace ve Visual Studiu 2013 se v okně Autos zobrazí návratové typy a hodnoty pro metody. Tyto informace jsou dostupné pro desktopové aplikace, aplikace pro Windows Store a Windows Phone. Další informace naleznete v [tématu Prozkoumání vrácených hodnot volání metody](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/dn323257(v=vs.120)).

- Upravujte a pokračujte u 64bitových aplikací. Visual Studio 2013 podporuje funkci Úpravy a pokračovat pro 64bitové spravované aplikace pro stolní počítače, Windows Store a Windows Phone. Existující omezení zůstávají v platnosti pro 32bitové i 64bitové aplikace (viz poslední část článku [Podporované změny kódu (C#).](/visualstudio/debugger/supported-code-changes-csharp)

- Ladění podporující asynchronní. Chcete-li usnadnit ladění asynchronních aplikací v sadě Visual Studio 2013, zásobník volání skryje kód infrastruktury poskytovaný kompilátory pro podporu asynchronního programování a také řetězy v logických nadřazených rámcích, takže můžete sledovat provádění logického programu více Jasně. Okno Úkoly nahrazuje okno Paralelní úkoly a zobrazuje úkoly, které se vztahují k určité zarážky, a také zobrazuje všechny další úkoly, které jsou aktuálně aktivní nebo naplánované v aplikaci. O této funkci si můžete přečíst v části Ladění podporující asynchronní informace [v oznámení rozhraní .NET Framework 4.5.1](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/).

- Lepší podpora výjimek pro součásti prostředí Windows Runtime. Výjimky, které vyvstávají z aplikací pro Windows Store, ve Windows 8.1 zachovávají informace o chybě, která výjimku způsobila, a to i přes hranice jazyka. O této funkci si můžete přečíst v části Vývoj aplikací pro Windows Store v [oznámení .NET Framework 4.5.1](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/).

Počínaje Visual Studio 2013, můžete použít [nástroj pro optimalizaci spravovaného profilu s asistencí (Mpgo.exe)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md) k optimalizaci aplikací pro Windows 8.x Store i aplikací klasické pracovní plochy.

Nové funkce v ASP.NET 4.5.1 najdete v [tématu ASP.NET a webových nástrojů pro poznámky k verzi sady Visual Studio 2013](/aspnet/visual-studio/overview/2013/release-notes).

<a name="v45" />

## <a name="whats-new-in-net-framework-45"></a>Co je nového v rozhraní .NET Framework 4.5

### <a name="base-classes"></a>Základní třídy

- Možnost snížit restartování systému zjišťováním a zavíráním aplikací rozhraní .NET Framework 4 během nasazení. Viz [Snížení restartování systému během instalace rozhraní .NET Framework 4.5](../deployment/reducing-system-restarts.md).

- Podpora pro pole, která jsou větší než 2 gigabajty (GB) na 64bitových platformách. Tuto funkci lze povolit v konfiguračním souboru aplikace. Viz [ \<gcAllowVeryLargeObjects> element](../configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md), který také uvádí další omezení velikosti objektu a velikosti pole.

- Lepší výkon prostřednictvím uvolňování paměti na pozadí pro servery. Při použití uvolňování paměti serveru v rozhraní .NET Framework 4.5 je automaticky povoleno uvolňování paměti na pozadí. Viz část Uvolňování paměti serveru na pozadí [v tématu Základy uvolňování paměti.](../../standard/garbage-collection/fundamentals.md)

- Kompilace just-in-time (JIT) na pozadí, která je volitelně k dispozici na vícejádrových procesorech pro zlepšení výkonu aplikací. Viz třída <xref:System.Runtime.ProfileOptimization>.

- Možnost omezit, jak dlouho se modul regulárních výrazů pokusí vyřešit regulární výraz před jeho časovým limitem. Podívejte <xref:System.Text.RegularExpressions.Regex.MatchTimeout%2A?displayProperty=nameWithType> se na nemovitost.

- Možnost definovat výchozí jazykovou verzi pro doménu aplikace. Podívejte <xref:System.Globalization.CultureInfo> se na třídu.

- Podpora konzoly pro kódování Unicode (UTF-16). Podívejte <xref:System.Console> se na třídu.

- Podpora pro správu verzí pořadí kulturních řetězců a data porovnání. Podívejte <xref:System.Globalization.SortVersion> se na třídu.

- Lepší výkon při načítání prostředků. Viz [Balení a nasazení prostředků](../resources/packaging-and-deploying-resources-in-desktop-apps.md).

- Vylepšení komprese zip zmenšit velikost komprimovaného souboru. Podívejte <xref:System.IO.Compression?displayProperty=nameWithType> se na obor názvů.

- Možnost přizpůsobit kontext reflexe přepsat výchozí chování <xref:System.Reflection.Context.CustomReflectionContext> odrazu prostřednictvím třídy.

- Podpora pro 2008 verze standardu Internationalized Domain Names in Applications <xref:System.Globalization.IdnMapping?displayProperty=nameWithType> (IDNA) při použití třídy v systému Windows 8.

- Delegování porovnání řetězců s operačním systémem, který implementuje Unicode 6.0, při použití rozhraní .NET Framework v systému Windows 8. Při spuštění na jiných platformách obsahuje rozhraní .NET Framework vlastní data pro porovnání řetězců, která implementuje unicode 5.x. Viz <xref:System.String> oddíl y třídy <xref:System.Globalization.SortVersion> a poznámky.

- Možnost vypočítat kódy hash pro řetězce na základě domény aplikace. Viz [ \<UseRandomizedStringHashAlgorithm> Element](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).

- Podpora odrazu <xref:System.Type> typu <xref:System.Reflection.TypeInfo> rozdělit mezi a třídy. Viz [Reflexe v rozhraní .NET Framework pro aplikace pro Windows Store](../reflection-and-codedom/reflection-for-windows-store-apps.md).

### <a name="managed-extensibility-framework-mef"></a>Managed Extensibility Framework (MEF)

V rozhraní .NET Framework 4.5 poskytuje rozhraní MEF spravované rozšiřitelnosti následující nové funkce:

- Podpora pro obecné typy.

- Programovací model založený na konvencích, který umožňuje vytvářet součásti založené na konvencích pojmenování, nikoli na atributech.

- Více oborů.

- Podmnožina MEF, kterou můžete použít při vytváření aplikací pro Windows 8.x Store. Tato podmnožina je k dispozici jako [balíček ke stažení](https://www.nuget.org/packages/Microsoft.Composition) z Galerie NuGet. Chcete-li nainstalovat balíček, otevřete projekt v sadě Visual Studio, zvolte `Microsoft.Composition` Spravovat **balíčky NuGet** z nabídky **Project** a vyhledejte balíček online.

Další informace naleznete [v tématu Managed Extensibility Framework (MEF)](../mef/index.md).

### <a name="asynchronous-file-operations"></a>Asynchronní operace se soubory

V rozhraní .NET Framework 4.5 byly do jazyků Jazyka C# a Visual Basic přidány nové asynchronní funkce. Tyto funkce přidat model založený na úlohách pro provádění asynchronních operací. Chcete-li použít tento nový model, použijte asynchronní metody ve třídách V/V. Viz [Vodaná vstupně-videa a synchronního souboru](../../standard/io/asynchronous-file-i-o.md).

<a name="tools" />

### <a name="tools"></a>nástroje

V rozhraní .NET Framework 4.5 umožňuje generátor souborů prostředků (Resgen.exe) vytvořit soubor Resw pro použití v aplikacích pro Windows 8.x Store ze souboru .resources vloženého do sestavení rozhraní .NET Framework. Další informace naleznete v [tématu Resgen.exe (Resource File Generator).](../tools/resgen-exe-resource-file-generator.md)

Optimalizace s asistencí spravovaného profilu (Mpgo.exe) umožňuje zlepšit dobu spuštění aplikace, využití paměti (velikost pracovní sady) a propustnost optimalizací nativních sestav bitových obrázků. Nástroj příkazového řádku generuje data profilu pro nativní sestavení aplikací obrazu. Viz [Mpgo.exe (Nástroj pro řízenou optimalizaci profilu)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md). Počínaje Visual Studio 2013, můžete použít Mpgo.exe k optimalizaci aplikací pro Windows 8.x Store, stejně jako desktopové aplikace.

<a name="parallel" />

### <a name="parallel-computing"></a>Paralelní výpočetní technika

Rozhraní .NET Framework 4.5 poskytuje několik nových funkcí a vylepšení pro paralelní výpočty. Patří mezi ně lepší výkon, lepší řízení, vylepšená podpora asynchronního programování, nová knihovna toku dat a vylepšená podpora paralelního ladění a analýzy výkonu. Podívejte se na položku [Co je nového pro paralelismus v rozhraní .NET 4.5](https://devblogs.microsoft.com/pfxteam/whats-new-for-parallelism-in-net-4-5/) v paralelním programování s .NET blog.

<a name="web" />

### <a name="web"></a>Web

ASP.NET 4.5 a 4.5.1 přidat vazbu modelu pro webové formuláře, podporu WebSocket, asynchronní obslužné rutiny, vylepšení výkonu a mnoho dalších funkcí. Další informace najdete v následujících materiálech:

- [ASP.NET 4.5 a Visual Studio 2012](https://docs.microsoft.com/previous-versions/aspnet/hh420390(v=vs.110))

- [ASP.NET a webové nástroje pro Visual Studio 2013 – poznámky k verzi](/aspnet/visual-studio/overview/2013/release-notes)

### <a name="networking"></a>Sítí<a name="networking" />

Rozhraní .NET Framework 4.5 poskytuje nové programovací rozhraní pro aplikace HTTP. Další informace naleznete v <xref:System.Net.Http?displayProperty=nameWithType> <xref:System.Net.Http.Headers?displayProperty=nameWithType> nových oborech názvů a oborech názvů.

Podpora je také součástí pro nové programovací rozhraní pro přijetí a <xref:System.Net.HttpListener> interakci s připojením WebSocket pomocí existující a související třídy. Další informace naleznete v <xref:System.Net.WebSockets> novém oboru <xref:System.Net.HttpListener> názvů a třídě.

Rozhraní .NET Framework 4.5 navíc obsahuje následující vylepšení sítě:

- Podpora identifikátoru URI kompatibilního s rfc. Další informace naleznete <xref:System.Uri> v tématu a související třídy.

- Podpora pro internacionalizovanou analýzu názvu domény (IDN). Další informace naleznete <xref:System.Uri> v tématu a související třídy.

- Podpora internacionalizace e-mailových adres (EAI). Další informace naleznete <xref:System.Net.Mail> v oboru názvů.

- Vylepšená podpora IPv6. Další informace naleznete <xref:System.Net.NetworkInformation> v oboru názvů.

- Podpora dvourežimových soketů. Další informace naleznete <xref:System.Net.Sockets.Socket> v <xref:System.Net.Sockets.TcpListener> tématu a třídy.

<a name="client" />

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

V rozhraní .NET Framework 4.5 obsahuje Nadace WPF (Windows Presentation Foundation) změny a vylepšení v následujících oblastech:

- Nový <xref:System.Windows.Controls.Ribbon.Ribbon> ovládací prvek, který umožňuje implementovat uživatelské rozhraní pásu karet, které je hostitelem panelu nástrojů rychlý přístup, nabídky aplikací a karet.

- Nové <xref:System.ComponentModel.INotifyDataErrorInfo> rozhraní, které podporuje synchronní a asynchronní ověřování dat.

- Nové funkce <xref:System.Windows.Controls.VirtualizingPanel> pro <xref:System.Windows.Threading.Dispatcher> třídy a.

- Vyšší výkon při zobrazení velkých sad seskupených dat a přístup u kolekcí v podprocesech mimo uživatelské rozhraní.

- Datová vazba na statické vlastnosti, <xref:System.Reflection.ICustomTypeProvider> datová vazba na vlastní typy, které implementují rozhraní, a načítání informací o datové vazbě z výrazu vazby.

- Změna umístění dat při změně hodnot (živé tvarování).

- Možnost zkontrolovat, zda je odpojen kontext dat pro kontejner položek.

- Možnost nastavit dobu, která by měla uplynout mezi změnami vlastností a aktualizacemi zdroje dat.

- Vylepšená podpora pro implementaci vzorů slabých událostí. Události mohou nyní přijímat rozšíření značek.

<a name="windows_communication_foundation" />

### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)

V rozhraní .NET Framework 4.5 byly přidány následující funkce, které usnadňují psaní a údržbu aplikací WCF (Windows Communication Foundation):

- Zjednodušení generovaných konfiguračních souborů.

- Podpora pro vývoj na prvním místě smlouvy.

- Možnost snadněji konfigurovat režim kompatibility ASP.NET.

- Změny výchozíhodnoty vlastnosti přenosu snížit pravděpodobnost, že budete muset nastavit.

- Aktualizace <xref:System.Xml.XmlDictionaryReaderQuotas> třídy snížit pravděpodobnost, že budete muset ručně nakonfigurovat kvóty pro čtečky slovníku XML.

- Ověření konfiguračních souborů WCF pomocí sady Visual Studio jako součást procesu sestavení, takže můžete zjistit chyby konfigurace před spuštěním aplikace.

- Nová podpora asynchronního streamování.

- Nové mapování protokolu HTTPS, které usnadňuje vystavení koncového bodu prostřednictvím protokolu HTTPS pomocí Internetové informační služby (IIS).

- Možnost generovat metadata v jednom dokumentu WSDL připojením `?singleWSDL` k adrese URL služby.

- Websockets podpora povolit skutečnou obousměrnou komunikaci přes porty 80 a 443 s charakteristikami výkonu podobné přenosu TCP.

- Podpora konfigurace služeb v kódu.

- Popisky editoru XML.

- <xref:System.ServiceModel.ChannelFactory>podpora ukládání do mezipaměti.

- Podpora komprese binárního kodéru.

- Podpora přenosu UDP, který umožňuje vývojářům psát služby, které používají zprávy "fire and forget". Klient odešle zprávu službě a očekává žádnou odpověď ze služby.

- Možnost podporovat více režimů ověřování na jednom koncovém bodu WCF při použití zabezpečení přenosu http a přenosu.

- Podpora služeb WCF, které používají mezinárodní názvy domén (IDNs).

Další informace naleznete [v tématu What's New in Windows Communication Foundation](../wcf/whats-new.md).

<a name="windows_workflow_foundation" />

### <a name="windows-workflow-foundation-wf"></a>Windows Workflow Foundation (WF)

V rozhraní .NET Framework 4.5 bylo do nadace Windows Workflow Foundation (WF) přidáno několik nových funkcí, včetně:

- Pracovní postupy stavového počítače, které byly poprvé zavedeny jako součást rozhraní .NET Framework 4.0.1 ([.NET Framework 4 Platform Update 1](https://docs.microsoft.com/archive/blogs/endpoint/microsoft-net-framework-4-platform-update-1)). Tato aktualizace zahrnovala několik nových tříd a aktivit, které vývojářům umožnily vytvářet pracovní postupy stavového počítače. Tyto třídy a aktivity byly aktualizovány pro rozhraní .NET Framework 4.5 tak, aby zahrnovaly:

  - Schopnost nastavit zarážky na stavy.

  - Možnost kopírovat a vkládat přechody v návrháři pracovního postupu.

  - Podpora návrháře pro vytvoření přechodu sdílené aktivační události.

  - Aktivity pro vytváření pracovních <xref:System.Activities.Statements.StateMachine>postupů <xref:System.Activities.Statements.State>stavového počítače, včetně: , a <xref:System.Activities.Statements.Transition>.

- Vylepšené funkce návrháře pracovních postupů, jako jsou následující:

  - Vylepšené možnosti hledání pracovních postupů v sadě Visual Studio, včetně **rychlého hledání** a **hledání v souborech**.

  - Možnost automaticky vytvořit sequence aktivitu při přidání druhé podřízené aktivity do aktivity kontejneru a zahrnout obě aktivity do aktivity Sekvence.

  - Podpora posouvání, která umožňuje změnu viditelné části pracovního postupu bez použití posuvníků.

  - Nové zobrazení **osnovy dokumentu,** které zobrazuje součásti pracovního postupu v zobrazení osnovy ve stromovém stylu a umožňuje vybrat komponentu v zobrazení **Osnova dokumentu.**

  - Možnost přidávat poznámky k aktivitám.

  - Možnost definovat a využívat delegáty aktivit pomocí návrháře pracovního postupu.

  - Automatické připojení a automatické vkládání pro aktivity a přechody v pracovních postupech stavového počítače a vývojového diagramu.

- Uložení informací o stavu zobrazení pracovního postupu v jediném prvku v souboru XAML, takže můžete snadno vyhledat a upravit informace o stavu zobrazení.

- A NoPersistScope kontejneru aktivity zabránit podřízené aktivity z trvalé.

- Podpora výrazů jazyka C#:

  - Projekty pracovního postupu, které používají visual basic, budou používat výrazy jazyka Visual Basic a projekty pracovního postupu jazyka C# budou používat výrazy jazyka C#.

  - C# projekty pracovního postupu, které byly vytvořeny v sadě Visual Studio 2010 a které mají výrazy jazyka Visual Basic jsou kompatibilní s c# workflow projekty, které používají výrazy Jazyka C#.

- Vylepšení správy verzí:

  - Nová <xref:System.Activities.WorkflowIdentity> třída, která poskytuje mapování mezi trvalou instanci pracovního postupu a její definicí pracovního postupu.

  - Souběžné provádění více verzí pracovního postupu ve stejném <xref:System.ServiceModel.Activities.WorkflowServiceHost>hostiteli, včetně .

  - V dynamické aktualizaci možnost upravit definici instance trvalého pracovního postupu.

- Vývoj služby pracovního postupu na prvním místě smlouvy, který poskytuje podporu pro automatické generování aktivit tak, aby odpovídaly existující servisní smlouvě.

Další informace naleznete [v tématu What's New in Windows Workflow Foundation](../windows-workflow-foundation/whats-new-in-wf-in-dotnet.md).

<a name="tailored" />

### <a name="net-for-windows-8x-store-apps"></a>Aplikace .NET pro Windows 8.x Store

Aplikace pro Windows 8.x Store jsou navržené pro konkrétní tvarové faktory a využívají výkon operačního systému Windows. Podmnožina rozhraní .NET Framework 4.5 nebo 4.5.1 je k dispozici pro vytváření aplikací pro Windows 8.x Store pro Windows pomocí C# nebo Visual Basic. Tato podmnožina se nazývá .NET pro aplikace pro Windows 8.x Store a je popsána v [přehledu](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)).

### <a name="portable-class-libraries"></a>Knihovny přenosných tříd<a name="portable" />

Projekt knihovny přenosných tříd v sadě Visual Studio 2012 (a novějších verzích) umožňuje psát a vytvářet spravovaná sestavení, která fungují na více platformách rozhraní .NET Framework. Pomocí projektu knihovny přenosných tříd zvolíte platformy (například Windows Phone a .NET pro aplikace pro Windows 8.x Store), na které chcete cílit. Dostupné typy a členy v projektu jsou automaticky omezeny na běžné typy a členy napříč těmito platformami. Další informace naleznete [v tématu Portable Class Library](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).

## <a name="see-also"></a>Viz také

- [Rozhraní .NET Framework a nesvázaná vydání](../get-started/the-net-framework-and-out-of-band-releases.md)
- [Co je nového v usnadnění v rozhraní .NET Framework](whats-new-in-accessibility.md)
- [Novinky v sadě Visual Studio 2017](/visualstudio/ide/whats-new-visual-studio-2017)
- [Co je nového ve Visual Studiu 2019](/visualstudio/ide/whats-new-visual-studio-2019)
- [ASP.NET](/aspnet)
- [Co je nového pro C++ v Sadě Visual Studio](/cpp/what-s-new-for-visual-cpp-in-visual-studio)
