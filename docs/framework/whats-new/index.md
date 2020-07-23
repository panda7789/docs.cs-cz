---
title: Co je nového v .NET Framework
description: Podívejte se, co je nového v různých verzích .NET Framework. Přečtěte si přehled klíčových nových funkcí a vylepšení v každé verzi.
ms.custom: updateeachrelease
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
ms.assetid: 1d971dd7-10fc-4692-8dac-30ca308fc0fa
ms.openlocfilehash: 42f872bba87a88fc92a37879e815ee7068407cf7
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925589"
---
# <a name="whats-new-in-net-framework"></a>Co je nového v .NET Framework

Tento článek shrnuje klíčové nové funkce a vylepšení v následujících verzích .NET Framework:

- [.NET Framework 4,8](#v48)
- [.NET Framework 4.7.2](#v472)
- [.NET Framework 4.7.1](#v471)
- [.NET Framework 4,7](#v47)
- [.NET Framework 4.6.2](#v462)
- [.NET Framework 4.6.1](#v461)
- [.NET 2015 a .NET Framework 4,6](#v46)
- [.NET Framework 4.5.2](#v452)
- [.NET Framework 4.5.1](#v451)
- [.NET Framework 4.5](#v45)

Tento článek neposkytuje úplné informace o každé nové funkci a může se změnit. Obecné informace o .NET Framework najdete v tématu [Začínáme](../get-started/index.md). Podporované platformy najdete v tématu [požadavky na systém](../get-started/system-requirements.md). Odkazy na stažení a pokyny k instalaci najdete v [Průvodci instalací](../install/guide-for-developers.md)nástroje.

> [!NOTE]
> .NET Framework tým také uvolní funkce mimo pásmo s nástrojem NuGet, aby rozšířila podporu platforem a zavedla nové funkce, jako jsou neměnné kolekce a typy vektorů s podporou SIMD. Další informace najdete v tématech [Další knihovny tříd a rozhraní API](../additional-apis/index.md) a [.NET Framework a vzdálené verze](../get-started/the-net-framework-and-out-of-band-releases.md).
> Podívejte se na [úplný seznam balíčků NuGet](https://www.nuget.org/profiles/dotnetframework) pro .NET Framework.

<a name="v48"></a>

## <a name="introducing-net-framework-48"></a>Představujeme .NET Framework 4,8

.NET Framework 4,8 sestaví na předchozích verzích .NET Framework 4. x přidáním mnoha nových oprav a několika nových funkcí a zbývajícím produktem.

### <a name="download-and-install-net-framework-48"></a>Stažení a instalace .NET Framework 4,8

.NET Framework 4,8 si můžete stáhnout z těchto umístění:

- [Webová instalační služba .NET Framework 4,8](https://dotnet.microsoft.com/download/dotnet-framework/net48)

- [.NET Framework 4,8 – offline instalační program](https://dotnet.microsoft.com/download/dotnet-framework/net48)

.NET Framework 4,8 lze nainstalovat do systému Windows 10, Windows 8.1, Windows 7 SP1 a odpovídajících serverových platforem od verze Windows Server 2008 R2 SP1. .NET Framework 4,8 můžete nainstalovat buď pomocí webové instalační služby, nebo v offline instalačním programu. Doporučeným způsobem pro většinu uživatelů je použití webové instalační služby.

Můžete cílit .NET Framework 4,8 v sadě Visual Studio 2012 nebo novější instalací sady [.NET Framework 4,8 Developer Pack](https://go.microsoft.com/fwlink/?LinkId=2085167).

### <a name="whats-new-in-net-framework-48"></a>Co je nového v .NET Framework 4,8

.NET Framework 4,8 zavádí nové funkce v následujících oblastech:

- [Základní třídy](#core48)
- [Windows Communication Foundation (WCF)](#wcf48)
- [Windows Presentation Foundation (WPF)](#wpf48)
- [Modul CLR (Common Language Runtime)](#clr48)

Vylepšené přístupnost, která aplikaci umožňuje zajistit vhodné prostředí pro uživatele technologie pro usnadnění práce, je nadále hlavním cílem .NET Framework 4,8. Informace o vylepšeních usnadnění v .NET Framework 4,8 najdete v tématu [co je nového v přístupnosti v .NET Framework](whats-new-in-accessibility.md).

<a name="core48"></a>

#### <a name="base-classes"></a>Základní třídy

Byl **snížen dopad FIPS na kryptografii**. V předchozích verzích .NET Framework spravované třídy zprostředkovatele kryptografických služeb, jako je například <xref:System.Security.Cryptography.SHA256Managed> throw a v <xref:System.Security.Cryptography.CryptographicException> případě, že systémové šifrovací knihovny jsou konfigurovány v režimu FIPS. Tyto výjimky jsou vyvolány, protože spravované verze tříd zprostředkovatele kryptografických služeb, na rozdíl od systémových kryptografických knihoven, neprošly certifikací FIPS (Federal Information Processing Standards) 140-2. Vzhledem k tomu, že někteří vývojáři mají své vývojové počítače v režimu FIPS, jsou výjimky obvykle vyvolány v produkčních systémech.

Ve výchozím nastavení nejsou v aplikacích, které cílí na .NET Framework 4,8, následující spravované třídy kryptografie již <xref:System.Security.Cryptography.CryptographicException> v tomto případě vyvolávat:

- <xref:System.Security.Cryptography.MD5Cng>
- <xref:System.Security.Cryptography.MD5CryptoServiceProvider>
- <xref:System.Security.Cryptography.RC2CryptoServiceProvider>
- <xref:System.Security.Cryptography.RijndaelManaged>
- <xref:System.Security.Cryptography.RIPEMD160Managed>
- <xref:System.Security.Cryptography.SHA256Managed>

Místo toho tyto třídy přesměrují kryptografické operace do systémové knihovny kryptografie. Tato změna efektivně odstraňuje potenciálně matoucí rozdíl mezi vývojářskými prostředími a provozními prostředími a zpřístupňuje nativní komponenty a spravované komponenty v rámci stejných kryptografických zásad. Aplikace, které závisí na těchto výjimkách, mohou obnovit předchozí chování nastavením přepínače AppContext `Switch.System.Security.Cryptography.UseLegacyFipsThrow` na `true` . Další informace najdete v tématu [spravované kryptografické třídy nevyvolávají výjimku CryptographyException v režimu FIPS](../migration-guide/retargeting/4.7.2-4.8.md#managed-cryptography-classes-do-not-throw-a-cryptographyexception-in-fips-mode).

**Použití aktualizované verze ZLib**

Počínaje .NET Framework 4,5 clrcompression.dll sestavení používá [ZLib](https://www.zlib.net), nativní externí knihovnu pro kompresi dat, aby bylo možné poskytnout implementaci pro algoritmus deflate. clrcompression.dll .NET Framework 4,8 se aktualizuje tak, aby používal ZLib verzi 1.2.11, která zahrnuje několik klíčových vylepšení a oprav.

<a name="wcf48"></a>

#### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)

**Úvod do ServiceHealthBehavior**

Nástroje pro orchestraci využívají koncové body stavu ke správě služeb na základě jejich stavu. Kontroly stavu lze také použít pomocí nástrojů pro monitorování ke sledování a poskytování oznámení o dostupnosti a výkonu služby.

**ServiceHealthBehavior** je chování služby WCF, které rozšiřuje <xref:System.ServiceModel.Description.IServiceBehavior> .  Při přidání do <xref:System.ServiceModel.Description.ServiceDescription.Behaviors?displayProperty=nameWithType> kolekce provede chování služby následující akce:

- Vrátí stav služby s kódy odpovědí HTTP. V řetězci dotazu můžete zadat stavový kód HTTP pro požadavek na test stavu HTTP/GET.

- Publikuje informace o stavu služby. Podrobnosti konkrétní služby, včetně stavu služby, počtu omezení a kapacity, se dají zobrazit pomocí požadavku HTTP/GET s `?health` řetězcem dotazu. Usnadnění přístupu k těmto informacím je důležité při řešení potíží se službou WCF, která se nechová.

Existují dva způsoby, jak vystavit koncový bod stavu a publikovat informace o stavu služby WCF:

- Prostřednictvím kódu. Příklad:

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

- Pomocí konfiguračního souboru. Příklad:

  ```xml
  <behaviors>
    <serviceBehaviors>
      <behavior name="DefaultBehavior">
        <serviceHealth httpsGetEnabled="true"/>
      </behavior>
    </serviceBehaviors>
  </behaviors>
  ```

Na stav služby se dá zadat dotaz pomocí parametrů dotazu `OnServiceFailure` , jako jsou,, a `OnDispatcherFailure` `OnListenerFailure` `OnThrottlePercentExceeded` ), a pro každý parametr dotazu je možné zadat kód odpovědi HTTP. Pokud je pro parametr dotazu vynechání kódu odpovědi HTTP, ve výchozím nastavení se používá kód odpovědi HTTP 503. Příklad:

- OnServiceFailure:`https://contoso:81/Service1?health&OnServiceFailure=450`

  Kód stavu odpovědi HTTP 450 je vrácen, když je [Třída ServiceHost. State](xref:System.ServiceModel.Channels.CommunicationObject.State) je větší než <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType> .
Parametry a příklady dotazů:

- OnDispatcherFailure:`https://contoso:81/Service1?health&OnDispatcherFailure=455`

  Stavový kód odpovědi HTTP 455 se vrátí, pokud je stav některého z přeslaných kanálů větší než <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType> .

- OnListenerFailure:`https://contoso:81/Service1?health&OnListenerFailure=465`

  Stavový kód odpovědi HTTP 465 se vrátí, pokud je stav jakéhokoli naslouchacího procesu kanálu větší než <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType> .

- OnThrottlePercentExceeded:`https://contoso:81/Service1?health&OnThrottlePercentExceeded= 70:350,95:500`

  Určuje procento {1 – 100}, které aktivuje odpověď a kód odpovědi HTTP {200 – 599}. V tomto příkladu:

  - Pokud je procento větší než 95, vrátí se kód odpovědi HTTP 500.

  - Pokud je vráceno procento nebo mezi 70 a 95, 350.

  - V opačném případě se vrátí 200.

Stav služby se dá zobrazit v HTML zadáním řetězce dotazu, jako je `https://contoso:81/Service1?health` nebo v XML, zadáním řetězce dotazu, jako je `https://contoso:81/Service1?health&Xml` . Řetězec dotazu jako `https://contoso:81/Service1?health&NoContent` vrátí prázdnou stránku HTML.

<a name="wpf48"></a>

#### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**Vylepšení vysokého rozlišení DPI**

V .NET Framework 4,8 WPF přidává podporu pro sledování rozlišení DPI podle monitoru v2 a škálování ve smíšeném režimu. Další informace o vývoji vysokého rozlišení DPI najdete v tématu [vývoj desktopových aplikací s vysokým rozlišením v systému Windows](/windows/win32/hidpi/high-dpi-desktop-application-development-on-windows) .

.NET Framework 4,8 vylepšuje podporu hostovaných HWND a model Windows Forms spolupráce v aplikacích WPF s vysokým rozlišením DPI na platformách, které podporují škálování DPI ve smíšeném režimu (od aktualizace Windows 10. dubna 2018). Když jsou hostované ovládací prvky HWND nebo model Windows Forms vytvořeny jako okna s rozlišením DPI ve smíšeném režimu pomocí volání [SetThreadDpiHostingBehavior](/windows/desktop/api/winuser/nf-winuser-setthreaddpihostingbehavior) a [SetThreadDpiAwarenessContext](/windows/desktop/api/winuser/nf-winuser-setthreaddpiawarenesscontext), mohou být hostovány v aplikaci WPF pro monitor v2 a mají odpovídající velikost a správné škálování. Takový hostovaný obsah se nevykresluje s nativním rozlišením DPI; operační systém místo toho škáluje hostovaný obsah na příslušnou velikost. Podpora režimu sledování DPI v rámci monitoru v2 také umožňuje hostování ovládacích prvků WPF (tj. nadřazených) v nativním okně aplikace s vysokým rozlišením DPI.

Pokud chcete povolit podporu pro škálování ve smíšeném režimu s vysokým rozlišením DPI, můžete nastavit následující [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) přepínače konfiguračního souboru aplikace:

```xml
<runtime>
   <AppContextSwitchOverrides value = "Switch.System.Windows.DoNotScaleForDpiChanges=false; Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false"/>
</runtime>
```

<a name="clr48"></a>

#### <a name="common-language-runtime"></a>Modul CLR (Common Language Runtime)

Modul runtime v .NET Framework 4,8 obsahuje následující změny a vylepšení:

**Vylepšení kompilátoru JIT**. Kompilátor JIT (just-in-time) v .NET Framework 4,8 je založen na kompilátoru JIT v rozhraní .NET Core 2,1. Mnohé z optimalizací a všechny opravy chyb provedené kompilátorem JIT .NET Core 2,1 jsou součástí kompilátoru .NET Framework 4,8 JIT.

**Vylepšení Ngen**. Modul runtime zlepšil správu paměti pro Image [generátoru nativních imagí](../tools/ngen-exe-native-image-generator.md) (NGen), takže data mapovaná z imagí Ngen nejsou rezidentní v paměti. Tím se snižuje plocha dostupná pro útoky, které se pokoušejí spustit libovolný kód úpravou paměti, která se spustí.

**Kontrola antimalwaru pro všechna sestavení**. V předchozích verzích .NET Framework modul runtime prohledává všechna sestavení načtená z disku pomocí programu Windows Defender nebo antimalwarového softwaru jiného výrobce. Nicméně sestavení načtená z jiných zdrojů, například <xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType> metodou, nejsou prohledávána a mohou potenciálně obsahovat nezjištěné malware. Počínaje .NET Framework 4,8 spuštěným v systému Windows 10 spustí modul runtime kontrolu pomocí antimalwarových řešení, která implementují [rozhraní AMSI (antimalwarová kontrola)](/windows/desktop/AMSI/antimalware-scan-interface-portal).

<a name="v472"></a>

## <a name="whats-new-in-net-framework-472"></a>Co je nového v .NET Framework 4.7.2

.NET Framework 4.7.2 zahrnuje nové funkce v následujících oblastech:

- [Základní třídy](#core-472)
- [ASP.NET](#asp-net472)
- [Sítě](#net472)
- [SQL](#sql472)
- [WPF](#wpf472)
- [ClickOnce](#clickonce)

Dalším cílem .NET Framework 4.7.2 je lepší přístupnost, která umožňuje aplikaci poskytovat vhodné prostředí pro uživatele technologie usnadnění. Informace o vylepšeních usnadnění v .NET Framework 4.7.2 najdete v tématu [co je nového v přístupnosti v .NET Framework](whats-new-in-accessibility.md).

<a name="core-472"></a>

#### <a name="base-classes"></a>Základní třídy

.NET Framework 4.7.2 obsahuje velký počet kryptografických vylepšení, lepší podporu dekomprese pro archivy ZIP a další rozhraní API pro shromažďování dat.

**Nová přetížení RSA. Vytvořte a DSA. Vytvořeny**

<xref:System.Security.Cryptography.DSA.Create(System.Security.Cryptography.DSAParameters)?displayProperty=nameWithType>Metody a <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> umožňují zadávat klíčové parametry při vytváření instance nového <xref:System.Security.Cryptography.DSA> nebo <xref:System.Security.Cryptography.RSA> klíče. Umožňují nahradit kód podobný následujícímu:

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

podobný kód:

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

<xref:System.Security.Cryptography.DSA.Create(System.Int32)?displayProperty=nameWithType>Metody a <xref:System.Security.Cryptography.RSA.Create(System.Int32)?displayProperty=nameWithType> umožňují generovat nové klíče <xref:System.Security.Cryptography.DSA> nebo <xref:System.Security.Cryptography.RSA> klíče s určitou velikostí klíče. Příklad:

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

**Konstruktory Rfc2898DeriveBytes přijímají název algoritmu hash.**

<xref:System.Security.Cryptography.Rfc2898DeriveBytes>Třída má tři nové konstruktory s <xref:System.Security.Cryptography.HashAlgorithmName> parametrem, který IDENTIFIKUJE algoritmus HMAC, který má být použit při odvozování klíčů. Místo použití algoritmu SHA-1 by vývojáři měli používat HMAC založené na SHA-2, jako je SHA-256, jak je znázorněno v následujícím příkladu:

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

**Podpora dočasných klíčů**

Import PFX může volitelně načíst soukromé klíče přímo z paměti a obejít pevný disk.Když je nový <xref:System.Security.Cryptography.X509Certificates.X509KeyStorageFlags.EphemeralKeySet?displayProperty=nameWithType> příznak zadán v <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> konstruktoru nebo v jednom z přetížení <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.Import%2A?displayProperty=nameWithType> metody, privátní klíče budou načteny jako dočasné klíče. To brání tomu, aby se klíče na disku zobrazily. Naopak

- Vzhledem k tomu, že klíče nejsou trvale uložené na disku, certifikáty načtené pomocí tohoto příznaku nejsou vhodnými kandidáty k přidání do X509Store.

- Klíče načtené tímto způsobem jsou téměř vždy načítány prostřednictvím služby Windows CNG. Proto volající musí získat přístup k privátnímu klíči voláním metod rozšíření, jako je například [CERT. GetRSAPrivateKey ()](xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey%2A). Vlastnost nefunguje <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> .

- Vzhledem k tomu <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> , že vlastnost starší verze nefunguje s certifikáty, vývojáři by měli před přechodem na dočasné klíče provádět přísné testy.

**Programové vytváření žádostí o podepsání certifikátu PKCS # 10 a certifikátů veřejných klíčů X. 509**

Počínaje .NET Framework 4.7.2 můžou úlohy generovat žádosti o podepsání certifikátu (oddělení IT), které umožňují, aby se generování žádosti o certifikát připravilo na stávající nástroje. To je často užitečné v testovacích scénářích.

Další informace a příklady kódu naleznete v tématu "programové vytváření žádostí o podepsání certifikátu PKCS # 10 a" certifikátů veřejných klíčů X. 509 "na [blogu .NET](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).

**Noví členové SignerInfo**

Počínaje .NET Framework 4.7.2 <xref:System.Security.Cryptography.Pkcs.SignerInfo> Třída zveřejňuje Další informace o podpisu. Můžete načíst hodnotu <xref:System.Security.Cryptography.Pkcs.SignerInfo.SignatureAlgorithm?displayProperty=fullName> vlastnosti a určit tak algoritmus podpisu, který používá podepisující osoba. <xref:System.Security.Cryptography.Pkcs.SignerInfo.GetSignature%2A?displayProperty=nameWithType>dá se zavolat, aby se získala kopie kryptografického podpisu pro tohoto podepsaného.

**Otevření zabaleného datového proudu po odstranění CryptoStream**

Počínaje .NET Framework 4.7.2 <xref:System.Security.Cryptography.CryptoStream> má třída další konstruktor, který umožňuje <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> Zavřít zabalený datový proud.Chcete-li nechat zabalený datový proud otevřený po <xref:System.Security.Cryptography.CryptoStream> uvolnění instance, zavolejte nový <xref:System.Security.Cryptography.CryptoStream> konstruktor následujícím způsobem:

```csharp
var cStream = new CryptoStream(stream, transform, mode, leaveOpen: true);
```

```vb
Dim cStream = New CryptoStream(stream, transform, mode, leaveOpen:=true)
```

**Dekomprese změn v DeflateStream**

Počínaje .NET Framework 4.7.2 se implementace operací dekomprese ve <xref:System.IO.Compression.DeflateStream> třídě změnila tak, aby ve výchozím nastavení používala nativní rozhraní API systému Windows. Obvykle to vede k výraznému zlepšení výkonu.

Podpora dekomprese pomocí rozhraní Windows API je ve výchozím nastavení povolená pro aplikace, které cílí na .NET Framework 4.7.2. Aplikace, které jsou cíleny na starší verze .NET Framework, ale jsou spuštěny v rámci .NET Framework 4.7.2, se můžou na toto chování vyjádřit přidáním následujícího [přepínače AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do konfiguračního souboru aplikace:

```xml
<AppContextSwitchOverrides value="Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=false" />
```

**Další rozhraní API pro shromažďování**

.NET Framework 4.7.2 přidá mnoho nových rozhraní API k <xref:System.Collections.Generic.SortedSet%601> <xref:System.Collections.Generic.HashSet%601> typům a. Mezi ně patří:

- `TryGetValue`metody, které přesahují vzor try použitý v jiných typech kolekcí těchto dvou typů. Existují tyto metody:

  - [Public \<T> bool HashSet – TryGetValue (T equalValue; out T actualValue)](xref:System.Collections.Generic.SortedSet%601.TryGetValue%2A)
  - [Public \<T> bool SortedSet TryGetValue (T equalValue; out T actualValue)](xref:System.Collections.Generic.SortedSet%601.TryGetValue%2A)

- `Enumerable.To*`metody rozšíření, které převádějí kolekci na <xref:System.Collections.Generic.HashSet%601> :

  - [veřejný statický HashSet – \<TSource> ToHashSet \<TSource> (Tento \<TSource> zdroj IEnumerable)](xref:System.Linq.Enumerable.ToHashSet%2A)
  - [public static HashSet – \<TSource> ToHashSet \<TSource> (this IEnumerable \<TSource> source, IEqualityComparer \<TSource> Comparer)](xref:System.Linq.Enumerable.ToHashSet%2A)

- Nové <xref:System.Collections.Generic.HashSet%601> konstruktory, které umožňují nastavit kapacitu kolekce, což vede k výhodám výkonu, když znáte velikost <xref:System.Collections.Generic.HashSet%601> předem:

  - [veřejné HashSet – (kapacita celé číslo)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32))
  - [Public HashSet – (kapacita int, IEqualityComparer \<T> Comparer)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32,System.Collections.Generic.IEqualityComparer%7B%600%7D))

<xref:System.Collections.Concurrent.ConcurrentDictionary%602>Třída obsahuje nová přetížení <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> metod a k načtení hodnoty ze slovníku nebo k jejímu přidání, pokud nebyla nalezena, a pro přidání hodnoty do slovníku nebo její aktualizaci, pokud již existuje.

```csharp
public TValue AddOrUpdate<TArg>(TKey key, Func<TKey, TArg, TValue> addValueFactory, Func<TKey, TValue, TArg, TValue> updateValueFactory, TArg factoryArgument)

public TValue GetOrAdd<TArg>(TKey key, Func<TKey, TArg, TValue> valueFactory, TArg factoryArgument)
```

```vb
Public AddOrUpdate(Of TArg)(key As TKey, addValueFactory As Func(Of TKey, TArg, TValue), updateValueFactory As Func(Of TKey, TValue, TArg, TValue), factoryArgument As TArg) As TValue

Public GetOrAdd(Of TArg)(key As TKey, valueFactory As Func(Of TKey, TArg, TValue), factoryArgument As TArg) As TValue
```

<a name="asp-net472"></a>

#### <a name="aspnet"></a>ASP.NET

**Podpora pro vkládání závislostí ve webových formulářích**

[Vkládání závislostí (di)](/aspnet/core/fundamentals/dependency-injection#overview-of-dependency-injection) odděluje objekty a jejich závislosti tak, že kód objektu již není nutné změnit pouze proto, že došlo ke změně závislosti. Při vývoji aplikací ASP.NET, které cílí na .NET Framework 4.7.2, můžete:

- Použijte metodu setter založenou na rozhraních a na bázi konstruktoru v [obslužných rutinách a modulech](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)), [instancích stránky](xref:System.Web.UI.Page)a [uživatelských ovládacích prvcích](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) projektů webové aplikace ASP.NET.

- Používejte vkládání na základě rozhraní a založených na rozhraních v [obslužných rutinách a modulech](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)), [instancích stránky](xref:System.Web.UI.Page)a [uživatelských ovládacích prvcích](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) projektů webu ASP.NET.

- Připojte se k různým rozhraním injektáže pro vkládání závislostí.

**Podpora souborů cookie stejného webu**

[SameSite](https://tools.ietf.org/html/draft-west-first-party-cookies-07) zabraňuje prohlížeči v posílání souborů cookie spolu s žádostí mezi weby. .NET Framework 4.7.2 přidá <xref:System.Web.HttpCookie.SameSite?displayProperty=nameWithType> vlastnost, jejíž hodnota je <xref:System.Web.SameSiteMode?displayProperty=nameWithType> člen výčtu. Pokud je jeho hodnota <xref:System.Web.SameSiteMode.Strict?displayProperty=nameWithType> nebo <xref:System.Web.SameSiteMode.Lax?displayProperty=nameWithType> , ASP.NET přidá `SameSite` atribut do hlavičky Set-cookie. Podpora SameSite se vztahuje na <xref:System.Web.HttpCookie> objekty i na <xref:System.Web.Security.FormsAuthentication> <xref:System.Web.SessionState> soubory cookie a.

SameSite pro objekt můžete nastavit takto <xref:System.Web.HttpCookie> :

```csharp
var c = new HttpCookie("secureCookie", "same origin");
c.SameSite = SameSiteMode.Lax;
```

```vb
Dim c As New HttpCookie("secureCookie", "same origin")
c.SameSite = SameSiteMode.Lax
```

Soubory cookie SameSite můžete na úrovni aplikace nakonfigurovat také úpravou souboru web.config:

```xml
<system.web>
   <httpCookies sameSite="Strict" />
</system.web>
```

SameSite pro <xref:System.Web.Security.FormsAuthentication> a <xref:System.Web.SessionState> soubory cookie můžete přidat úpravou konfiguračního souboru Web:

```xml
<system.web>
   <authentication mode="Forms">
      <forms cookieSameSite="Lax">
         <!-- ...   -->
      </forms>
   </authentication>
   <sessionState cookieSameSite="Lax"></sessionState>
</system.web>
```

<a name="net472"></a>

#### <a name="networking"></a>Sítě

**Implementace vlastností HttpClientHandler**

.NET Framework 4.7.1 přidal do třídy osm vlastností <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> . Nicméně dvě vyvolaly výjimku <xref:System.PlatformNotSupportedException> . .NET Framework 4.7.2 nyní poskytuje implementaci těchto vlastností. Mezi vlastnosti patří:

- <xref:System.Net.Http.HttpClientHandler.CheckCertificateRevocationList>
- <xref:System.Net.Http.HttpClientHandler.SslProtocols>

<a name="sql472"></a>

#### <a name="sqlclient"></a>SQLClient

**Podpora Azure Active Directory univerzálního ověřování a Multi-Factor Authentication**

Rostoucí požadavky na dodržování předpisů a požadavky na zabezpečení vyžadují, aby spousta zákazníků používala vícefaktorové ověřování (MFA). Kromě toho aktuální osvědčené postupy zabrání zahrnutí uživatelských hesel přímo v připojovacích řetězcích. Pro podporu těchto změn .NET Framework 4.7.2 rozšiřuje [připojovací řetězce SqlClient](xref:System.Data.SqlClient.SqlConnection.ConnectionString) přidáním nové hodnoty "Active Directory Interactive" pro stávající klíčové slovo "ověřování" pro podporu MFA a [ověřování Azure AD](/azure/sql-database/sql-database-aad-authentication-configure). Nová interaktivní metoda podporuje uživatele v rámci nativních a federovaných uživatelů Azure AD i uživatele typu Host služby Azure AD. Při použití této metody se pro databáze SQL podporuje ověřování MFA, které ukládá služba Azure AD. Kromě toho proces ověřování požaduje heslo uživatele, aby dodržoval osvědčené postupy zabezpečení.

V předchozích verzích .NET Framework připojení SQL podporovalo pouze <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryPassword?displayProperty=nameWithType> <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryIntegrated?displayProperty=nameWithType> Možnosti a. Obě tyto součásti jsou součástí neinteraktivního [protokolu ADAL](/azure/active-directory/develop/active-directory-authentication-libraries), který nepodporuje vícefaktorové ověřování. Díky nové <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryInteractive?displayProperty=nameWithType> Možnosti připojení SQL podporuje vícefaktorové ověřování a taky existující metody ověřování (heslo a integrované ověřování), které uživatelům umožňují zadat uživatelská hesla interaktivně, aniž by museli uchovávat hesla v připojovacím řetězci.

Další informace a příklad najdete v tématu Podpora SQL--Azure AD Universal a Multi-Factor Authentication na [blogu .NET](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).

**Podpora pro Always Encrypted verze 2**

NET Framework 4.7.2 přidává podporu pro Always Encrypted založenou na enklávy. Původní verze Always Encrypted je technologie šifrování na straně klienta, ve které šifrovací klíče nikdy nenechávají klienta. V Always Encrypted založeném na enklávy může klient volitelně odesílat šifrovací klíče na zabezpečený enklávy, což je zabezpečená výpočetní entita, kterou je možné považovat za součást SQL Server, ale SQL Server kód nemůže manipulovat. Pro podporu Always Encrypted založeného na enklávy, .NET Framework 4.7.2 přidá následující typy a členy do <xref:System.Data.SqlClient> oboru názvů:

- <xref:System.Data.SqlClient.SqlConnectionStringBuilder.EnclaveAttestationUrl?displayProperty=nameWithType>, který určuje identifikátor URI pro Always Encrypted založené na enklávy.

- <xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider>, což je abstraktní třída, ze které jsou odvozeni všichni poskytovatelé enklávy.

- <xref:System.Data.SqlClient.SqlEnclaveSession>, který zapouzdřuje stav pro danou relaci enklávy.

- <xref:System.Data.SqlClient.SqlEnclaveAttestationParameters>, který poskytuje parametry ověření identity používané SQL Server k získání informací potřebných ke spuštění konkrétního protokolu ověření identity.

Konfigurační soubor aplikace pak určí konkrétní implementaci abstraktní <xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider?displayProperty=nameWithType> třídy, která poskytuje funkce pro poskytovatele enklávy. Příklad:

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

Základní tok Always Encrypted založeného na enklávy:

1. Uživatel vytvoří připojení AlwaysEncrypted k SQL Server, která podporuje Always Encrypted založenou na enklávy. Ovladač kontaktuje službu ověření identity, aby zajistil, že se připojí k pravé enklávy.

1. Po ověření enklávy ovladač vytvoří zabezpečený kanál se zabezpečeným enklávy hostovaným na SQL Server.

1. Ovladač sdílí šifrovací klíče autorizované klientem s zabezpečeným enklávy po dobu trvání připojení SQL.

<a name="wpf472"></a>

#### <a name="windows-presentation-foundation"></a>Windows Presentation Foundation

**Hledání třídách ResourceDictionaries podle zdroje**

Počínaje .NET Framework 4.7.2 může diagnostický pomocník najít  <xref:System.Windows.Xps.Packaging.IXpsFixedPageReader.ResourceDictionaries> vytvářený z daného zdrojového identifikátoru URI.(Tato funkce se používá pro diagnostické asistenty, nikoli pro produkční aplikace.) Pomocník pro diagnostiku, jako je "Edit-and-Continue" sady Visual Studio, umožňuje svému uživateli upravit ResourceDictionary s záměrem, aby se změny projevily u běžící aplikace. V tomto kroku najdete všechny třídách ResourceDictionaries, které spuštěná aplikace vytvořila ze upravovaného slovníku. Například aplikace může deklarovat ResourceDictionary, jehož obsah je zkopírován z daného zdrojového identifikátoru URI:

```xml
<ResourceDictionary Source="MyRD.xaml" />
```

Diagnostický pomocník, který upravuje původní kód v souboru *MyRD. XAML*,   může k vyhledání slovníku použít novou funkci.Tato funkce je implementována novou statickou metodou <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetResourceDictionariesForSource%2A?displayProperty=nameWithType> . Pomocník diagnostiky volá novou metodu pomocí absolutního identifikátoru URI, který identifikuje původní kód, jak je znázorněno v následujícím kódu:

```csharp
IEnumerable<ResourceDictionary> dictionaries = ResourceDictionaryDiagnostics.GetResourceDictionariesForSource(new Uri("pack://application:,,,/MyApp;component/MyRD.xaml"));
```

```vb
Dim dictionaries As IEnumerable(Of ResourceDictionary) = ResourceDictionaryDiagnostics.GetResourceDictionariesForSource(New Uri("pack://application:,,,/MyApp;component/MyRD.xaml"))
```

Metoda vrátí prázdnou hodnotu výčtu, pokud  <xref:System.Windows.Diagnostics.VisualDiagnostics> není povolena a [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)   Proměnná prostředí je nastavena.

**Hledání vlastníků ResourceDictionary**

Počínaje .NET Framework 4.7.2 může pomocník pro diagnostiku najít vlastníky daného <xref:Windows.UI.Xaml.ResourceDictionary> .(Tato funkce je určena pro diagnostické asistenty, nikoli pro produkční aplikace.) Pokaždé, když je provedena změna na <xref:Windows.UI.Xaml.ResourceDictionary> , WPF automaticky najde všechny odkazy na [DynamicResource](../wpf/advanced/dynamicresource-markup-extension.md) , které mohou být ovlivněny změnou.

Nástroj pro diagnostiku, jako je například zařízení "Edit-and-Continue" sady Visual Studio, může chtít tuto funkci zvětšit, aby zpracovávala odkazy na [StaticResource](../wpf/advanced/staticresource-markup-extension.md) . Prvním krokem v tomto procesu je vyhledání vlastníků slovníku; To znamená, aby bylo možné najít všechny objekty, jejichž `Resources` vlastnost odkazuje na slovník (buď přímo, nebo nepřímo přes <xref:System.Windows.ResourceDictionary.MergedDictionaries?displayProperty=nameWithType> vlastnost). Tři nové statické metody implementované u <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics?displayProperty=nameWithType> třídy, jeden pro každý ze základních typů, které mají `Resources` vlastnost, podporují tento krok:

- [`public static IEnumerable<FrameworkElement> GetFrameworkElementOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetFrameworkElementOwners%2A)

- [`public static IEnumerable<FrameworkContentElement> GetFrameworkContentElementOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetFrameworkContentElementOwners%2A)

- [`public static IEnumerable<Application> GetApplicationOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetApplicationOwners%2A)

Tyto metody vrátí prázdný vyčíslitelné, pokud  <xref:System.Windows.Diagnostics.VisualDiagnostics> není povoleno a [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)   Proměnná prostředí je nastavena.

**Hledání odkazů na StaticResource**

Diagnostika pomocníka teď může obdržet oznámení vždy, když se vyřeší odkaz na [StaticResource](../wpf/advanced/staticresource-markup-extension.md) .(Tato funkce se používá pro diagnostické asistenty, nikoli pro produkční aplikace.) Nástroj pro diagnostiku, jako je například zařízení "Edit-and-Continue" sady Visual Studio, může chtít aktualizovat všechna použití prostředku, když se změní jeho hodnota <xref:Windows.UI.Xaml.ResourceDictionary> . WPF to provede automaticky pro [DynamicResource](../wpf/advanced/dynamicresource-markup-extension.md) odkazy, ale záměrně to neudělá pro odkazy [StaticResource](../wpf/advanced/staticresource-markup-extension.md) . Od .NET Framework 4.7.2 může pomocník diagnostiky použít tato oznámení k vyhledání těchto použití statického prostředku.

Oznámení je implementováno novou <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.StaticResourceResolved?displayProperty=nameWithType> událostí:

```csharp
public static event EventHandler<StaticResourceResolvedEventArgs> StaticResourceResolved;
```

```vb
Public Shared Event StaticResourceResolved As EventHandler(Of StaticResourceResolvedEventArgs)
```

Tato událost je vyvolána pokaždé, když modul runtime vyřeší odkaz [StaticResource](../wpf/advanced/staticresource-markup-extension.md) .<xref:System.Windows.Diagnostics.StaticResourceResolvedEventArgs>Argumenty popisují rozlišení a označují objekt a vlastnost, které hostují odkaz [StaticResource](../wpf/advanced/staticresource-markup-extension.md) a klíč a, který  <xref:Windows.UI.Xaml.ResourceDictionary> se používá pro řešení:

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

Událost není vyvolána (a její `add` přistupující objekt je ignorován), pokud  <xref:System.Windows.Diagnostics.VisualDiagnostics> není povolena a [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)   Proměnná prostředí je nastavena.

#### <a name="clickonce"></a>ClickOnce

HDPI aplikace pro model Windows Forms, Windows Presentation Foundation (WPF) a Visual Studio Tools for Office (VSTO) se dají nasadit pomocí technologie ClickOnce. Pokud je v manifestu aplikace nalezen následující záznam, nasazení bude úspěšné v části .NET Framework 4.7.2:

```xml
<windowsSettings>
   <dpiAware xmlns="http://schemas.microsoft.com/SMI/2005/WindowsSettings">true</dpiAware>
</windowsSettings>
```

V případě model Windows Forms aplikace není pro úspěšné nasazení ClickOnce předchozí alternativní řešení nastavení zvyšování rozlišení DPI v konfiguračním souboru aplikace, a ne jako manifest aplikace, již nutné.

<a name="v471"></a>

## <a name="whats-new-in-net-framework-471"></a>Co je nového v .NET Framework 4.7.1

.NET Framework 4.7.1 zahrnuje nové funkce v následujících oblastech:

- [Základní třídy](#core471)
- [Modul CLR (Common Language Runtime)](#clr)
- [Sítě](#net471)
- [ASP.NET](#asp-net471)

Navíc je hlavní fokus v .NET Framework 4.7.1 vylepšený přístupnost, což aplikaci umožňuje zajistit vhodné prostředí pro uživatele technologie usnadnění. Informace o vylepšeních usnadnění v .NET Framework 4.7.1 najdete v tématu [co je nového v přístupnosti v .NET Framework](whats-new-in-accessibility.md).

<a name="core471"></a>

#### <a name="base-classes"></a>Základní třídy

**Podpora pro .NET Standard 2,0**

[.NET Standard](../../standard/net-standard.md) definuje sadu rozhraní API, která musí být k dispozici v každé implementaci rozhraní .NET, která podporuje tuto verzi standardu. .NET Framework 4.7.1 plně podporuje .NET Standard 2,0 a přidává [asi 200 rozhraní API](https://github.com/dotnet/standard/blob/master/src/netstandard/src/ApiCompatBaseline.net461.txt) , která jsou definována v .NET Standard 2,0 a chybí v .NET Framework 4.6.1, 4.6.2 a 4,7. (Upozorňujeme, že tyto verze .NET Framework podporují .NET Standard 2,0 pouze v případě, že jsou do cílového systému nasazeny také další .NET Standard podpůrné soubory.) Další informace najdete v příspěvku na blogu o podpoře BCL-.NET Standard 2,0 v tématu [.NET Framework 4.7.1 runtime a funkce kompilátoru](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) .

**Podpora pro sestavovatele konfigurace**

Tvůrci konfigurace umožňují vývojářům dynamicky vkládat a sestavovat nastavení konfigurace pro aplikace v době běhu. Vlastní tvůrci konfigurace lze použít k úpravě existujících dat v konfiguračním oddílu nebo k sestavení konfiguračního oddílu úplně od začátku. Bez konfiguračních tvůrců, soubory. config jsou statické a jejich nastavení je definováno určitou dobu před spuštěním aplikace.

Chcete-li vytvořit vlastního tvůrce konfigurace, odvodit svého tvůrce z abstraktní <xref:System.Configuration.ConfigurationBuilder> třídy a přepsat jeho <xref:System.Configuration.ConfigurationBuilder.ProcessConfigurationSection%2A?displayProperty=nameWithType> a <xref:System.Configuration.ConfigurationBuilder.ProcessRawXml%2A?displayProperty=nameWithType> . Můžete také definovat své sestavovatele v souboru. config. Další informace najdete v části "tvůrci konfigurace" v příspěvku na blogu [.NET Framework 4.7.1 ASP.NET a konfigurační funkce](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) .

**Detekce funkcí za běhu**

<xref:System.Runtime.CompilerServices.RuntimeFeature?displayProperty=nameWithType>Třída poskytuje mechanismus pro určení, zda je předdefinovaná funkce v dané implementaci rozhraní .NET podporována v době kompilace nebo v době běhu. V době kompilace může kompilátor ověřit, zda zadané pole existuje k určení, zda je funkce podporována. Pokud ano, může vygenerovat kód, který tuto funkci využívá. V době běhu může aplikace zavolat <xref:System.Runtime.CompilerServices.RuntimeFeature.IsSupported%2A?displayProperty=nameWithType> metodu před vygenerováním kódu za běhu. Další informace najdete v tématu [Přidání pomocné metody pro popis funkcí podporovaných modulem runtime](https://github.com/dotnet/corefx/issues/17116).

**Typy řazené kolekce členů mají hodnotu serializovat.**

Počínaje .NET Framework 4.7.1 <xref:System.ValueTuple?displayProperty=nameWithType> a přidružené obecné typy jsou označeny jako [serializovatelný](xref:System.SerializableAttribute), což umožňuje binární serializaci. To by mělo být pro snazší migraci typů řazené kolekce členů, například <xref:System.Tuple%603> a <xref:System.Tuple%604> , k hodnotám řazené kolekce členů. Další informace naleznete v příspěvku "Compiler--ValueTuple je serializovatelný" v příspěvku blogu [.NET Framework 4.7.1 runtime a funkce kompilátoru](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) .

**Podpora odkazů jen pro čtení**

.NET Framework 4.7.1 přidá <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute?displayProperty=nameWithType> . Tento atribut používají kompilátory jazyka k označení členů, kteří mají návratový typ nebo parametry ref jen pro čtení. Další informace najdete v příspěvku na blogu o kompilátoru – podpora pro ReadOnlyReferences v tématu [.NET Framework 4.7.1 runtime a funkce kompilátoru](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) . Informace o vrácených hodnotách ref naleznete v tématech [ref Return Values a Locals (příručka C#)](../../csharp/programming-guide/classes-and-structs/ref-returns.md) a [ref Return values (Visual Basic)](../../visual-basic/programming-guide/language-features/procedures/ref-return-values.md).

<a name="clr"></a>

#### <a name="common-language-runtime-clr"></a>Common language runtime (CLR)

**Vylepšení výkonu shromažďování paměti**

Změny uvolňování paměti (GC) v .NET Framework 4.7.1 vylepšit celkový výkon, zejména pro přidělení LOH (large object Heap). V .NET Framework 4.7.1 jsou používány samostatné zámky pro LOH (Small Object Heap) a LOH alokace, což umožňuje přidělení, když je uvolňování paměti SOH na pozadí. V důsledku toho by aplikace, které vytvářejí velký počet přidělení LOH, měly vidět snížení kolizí uzamčení přidělení a lepší výkon. Další informace najdete v části "prostředí runtime – vylepšení výkonu GC" v příspěvku blogu [.NET Framework 4.7.1 runtime a funkce kompilátoru](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) .

<a name="net471"/>

#### <a name="networking"></a>Sítě

**Podpora SHA-2 pro Message. HashAlgorithm**

V .NET Framework 4,7 a starších verzích <xref:System.Messaging.Message.HashAlgorithm%2A?displayProperty=nameWithType> podporuje vlastnost <xref:System.Messaging.HashAlgorithm.Md5?displayProperty=nameWithType> pouze hodnoty a <xref:System.Messaging.HashAlgorithm.Sha?displayProperty=nameWithType> . Počínaje .NET Framework 4.7.1, <xref:System.Messaging.HashAlgorithm.Sha256?displayProperty=nameWithType> , a <xref:System.Messaging.HashAlgorithm.Sha384?displayProperty=nameWithType> <xref:System.Messaging.HashAlgorithm.Sha512?displayProperty=nameWithType> jsou také podporovány. Určuje, zda je tato hodnota skutečně používána, záleží na službě MSMQ, protože <xref:System.Messaging.Message> samotná instance neprovádí žádné hodnoty hash, ale jednoduše předává hodnoty do služby MSMQ. Další informace najdete v tomto příspěvku na blogu podpora SHA-2 pro Message. HashAlgorithm v části [.NET Framework 4.7.1 ASP.NET a konfigurační funkce](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) .

<a name="asp-net471"></a>

#### <a name="aspnet"></a>ASP.NET

**Kroky provádění v aplikacích ASP.NET**

ASP.NET zpracovává požadavky v předdefinovaném kanálu, který zahrnuje 23 událostí. ASP.NET spustí jednotlivé obslužné rutiny události jako krok provedení. Ve verzích ASP.NET až .NET Framework 4,7 nemůže ASP.NET z důvodu přepínání mezi nativními a spravovanými vlákny flowovat kontext spuštění. Místo toho ASP.NET selektivní toky pouze <xref:System.Web.HttpContext> . Počínaje .NET Framework 4.7.1 <xref:System.Web.HttpApplication.OnExecuteRequestStep(System.Action{System.Web.HttpContextBase,System.Action})?displayProperty=nameWithType> Metoda také umožňuje modulům obnovovat okolní data. Tato funkce je zaměřená na knihovny, které mají na starosti trasování, profilování, diagnostiku nebo transakce, například informace o toku spuštění aplikace. Další informace najdete v příspěvku na blogu věnovaném funkci "ASP.NET provádění kroku" v tématu [.NET Framework 4.7.1 ASP.NET a konfigurační funkce](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) .

**ASP.NET HttpCookie – analýza**

.NET Framework 4.7.1 zahrnuje novou metodu, <xref:System.Web.HttpCookie.TryParse%2A?displayProperty=nameWithType> která poskytuje standardizovaný způsob, jak vytvořit <xref:System.Web.HttpCookie> objekt z řetězce a přesně přiřadit hodnoty souborů cookie, jako je datum vypršení platnosti a cesta. Další informace najdete v blogovém příspěvku "ASP.NET HttpCookie analyze" v blogu [.NET Framework 4.7.1 ASP.NET and Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) .

**Možnosti hash SHA-2 pro přihlašovací údaje ověřování ASP.NET Forms**

V .NET Framework 4,7 a starších verzích umožnili vývojářům ASP.NET ukládat přihlašovací údaje uživatele s hashými hesly v konfiguračních souborech pomocí MD5 nebo SHA1. Počínaje .NET Framework 4.7.1, ASP.NET podporuje také nové zabezpečené možnosti hash SHA-2, jako jsou SHA256, SHA384 a SHA512. SHA1 zůstává výchozí a v konfiguračním souboru webu lze definovat jiný algoritmus hash, který není výchozí. Příklad:

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

<a name="v47"></a>

## <a name="whats-new-in-net-framework-47"></a>Co je nového v .NET Framework 4,7

.NET Framework 4,7 obsahuje nové funkce v následujících oblastech:

- [Základní třídy](#Core47)
- [Sítě](#net47)
- [ASP.NET](#ASP-NET47)
- [Windows Communication Foundation (WCF)](#wcf47)
- [Windows Forms](#wf47)
- [Windows Presentation Foundation (WPF)](#WPF47)

Seznam nových rozhraní API přidaných do .NET Framework 4,7 najdete v článku [změny rozhraní api .NET Framework 4,7](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-api-changes.md) na GitHubu. Seznam vylepšení funkcí a oprav chyb v .NET Framework 4,7 naleznete v části [.NET Framework 4,7 seznam změn](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-changes.md) na GitHubu. Další informace najdete v tématu [oznámení .NET Framework 4,7](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-7/) na blogu .NET.

<a name="Core47"></a>

#### <a name="base-classes"></a>Základní třídy

.NET Framework 4,7 vylepšuje serializaci <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> :

**Vylepšená funkce s použitím kryptografie s eliptickou křivkou (ECC)***

V .NET Framework 4,7 `ImportParameters(ECParameters)` byly metody přidány do <xref:System.Security.Cryptography.ECDsa> tříd a, <xref:System.Security.Cryptography.ECDiffieHellman> aby objekt mohl představovat již zavedený klíč. `ExportParameters(Boolean)`Metoda byla přidána také pro export klíče pomocí explicitních parametrů křivky.

.NET Framework 4,7 také přidává podporu pro další křivky (včetně sady křivky Brainpool) a přidala předdefinované definice pro usnadnění vytváření prostřednictvím nových <xref:System.Security.Cryptography.ECDsa.Create%2A> a <xref:System.Security.Cryptography.ECDiffieHellman.Create%2A> výrobních metod.

Na GitHubu můžete vidět [příklad kryptografických vylepšení .NET Framework 4,7](https://gist.github.com/richlander/5a182899895a87a296c21ada97f7a54e) .

**Lepší podpora kontrolních znaků DataContractJsonSerializer**

V .NET Framework 4,7 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> třída serializace řídicích znaků v souladu se standardem ECMAScript 6. Toto chování je ve výchozím nastavení povolené pro aplikace, které cílí na .NET Framework 4,7, a je funkce pro přihlášení k aplikacím, které běží v .NET Framework 4,7, ale cílí na předchozí verzi .NET Framework. Další informace najdete v části [Kompatibilita aplikací](../migration-guide/application-compatibility.md) .

<a name="net47"></a>

#### <a name="networking"></a>Sítě

.NET Framework 4,7 přidává následující funkci související se sítí:

**Výchozí podpora operačního systému pro protokoly TLS***

Zásobník protokolu TLS, který používají <xref:System.Net.Security.SslStream?displayProperty=nameWithType> komponenty a součásti v zásobníku, jako jsou http, FTP a SMTP, umožňuje vývojářům používat výchozí protokoly TLS podporované operačním systémem. Vývojáři už nemusejí mít pevně zakódování verze TLS.

<a name="ASP-NET47"></a>

#### <a name="aspnet"></a>ASP.NET

V .NET Framework 4,7 obsahuje ASP.NET následující nové funkce:

**Rozšiřitelnost mezipaměti objektů**

Počínaje .NET Framework 4,7 přidá ASP.NET novou sadu rozhraní API, která vývojářům umožní nahradit výchozí implementaci ASP.NET pro ukládání objektů do paměti a monitorování paměti. Vývojáři teď můžou nahradit některou z následujících tří součástí, pokud ASP.NET implementace není adekvátní:

- **Úložiště mezipaměti objektů**. Při použití konfiguračního oddílu Noví poskytovatelé mezipaměti můžou vývojáři připojit nové implementace mezipaměti objektů pro aplikaci ASP.NET pomocí nového rozhraní **ICacheStoreProvider** .

- **Monitorování paměti**. Výchozí monitorování paměti v ASP.NET upozorní aplikace, když běží blízko nakonfigurovaného limitu privátních bajtů pro daný proces, nebo když má počítač nedostatek celkového dostupné fyzické paměti RAM. Když jsou tato omezení blízko, jsou aktivována oznámení. U některých aplikací se oznámení aktivují příliš blízko nakonfigurovaných limitů, aby bylo možné reakce na užitečné. Vývojáři teď můžou zapisovat vlastní monitory paměti, které nahradí výchozí hodnotu pomocí <xref:System.Web.Hosting.ApplicationMonitors.MemoryMonitor%2A?displayProperty=nameWithType> Vlastnosti.

- **Reakce na limit paměti**. Ve výchozím nastavení se ASP.NET pokusí oříznout mezipaměť objektů a pravidelně volat, <xref:System.GC.Collect%2A?displayProperty=nameWithType> Pokud je limit procesu privátního bajtu blízko. U některých aplikací je frekvence volání <xref:System.GC.Collect%2A?displayProperty=nameWithType> nebo množství mezipaměti, která je oříznuta, neefektivní. Vývojáři teď můžou nahradit nebo doplnit výchozí chování tím, že se přihlásí k odběru **IObserver** implementace do monitorování paměti aplikace.

<a name="wcf47"></a>

#### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)

Windows Communication Foundation (WCF) přidá následující funkce a změny:

**Možnost konfigurovat výchozí nastavení zabezpečení zpráv na TLS 1,1 nebo TLS 1,2**

Počínaje .NET Framework 4,7 umožňuje WCF nakonfigurovat kromě protokolu SSL 3,0 a TSL 1,0 i možnost TSL 1,1 nebo TLS 1,2 jako výchozí protokol zabezpečení zpráv. Toto je nastavení výslovného souhlasu; Pokud ho chcete povolit, musíte do konfiguračního souboru aplikace přidat následující položku:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false" />
</runtime>
```

**Vylepšená spolehlivost aplikací WCF a serializace WCF**

WCF zahrnuje řadu změn kódu, které eliminují konflikty časování, což zvyšuje výkon a spolehlivost možností serializace. Mezi ně patří:

- Lepší podpora pro kombinování asynchronního a synchronního kódu v voláních **Připojení SocketConnection bylo. BeginRead** a **Připojení SocketConnection bylo. Read**.
- Lepší spolehlivost při přerušení připojení pomocí **SharedConnectionListener** a **DuplexChannelBinder**.
- Zlepšená spolehlivost operací serializace při volání <xref:System.Runtime.Serialization.FormatterServices.GetSerializableMembers%28System.Type%29?displayProperty=nameWithType> metody.
- Lepší spolehlivost při odebírání nástroje Wait voláním metody **ChannelSynchronizer. RemoveWaiter** .

<a name="wf47"></a>

#### <a name="windows-forms"></a>Windows Forms

V .NET Framework 4,7 model Windows Forms vylepšuje podporu pro monitory s vysokým rozlišením DPI.

**Podpora vysokého rozlišení DPI**

Počínaje aplikacemi, které cílí na .NET Framework 4,7, .NET Framework funkce vysokého rozlišení DPI a podpora dynamického DPI pro model Windows Forms aplikace. Podpora vysokého rozlišení DPI vylepšuje rozložení a vzhled formulářů a ovládacích prvků na obrazovkách s vysokým rozlišením DPI. Dynamické DPI mění rozložení a vzhled formulářů a ovládacích prvků, když uživatel změní v běžící aplikaci Měřítko DPI nebo zobrazení.

Podpora vysokého rozlišení DPI je funkce výslovného souhlasu, kterou nakonfigurujete tak, že definujete [\<System.Windows.Forms.ConfigurationSection>](../configure-apps/file-schema/winforms/index.md) oddíl v konfiguračním souboru aplikace. Další informace o přidání podpory vysokého rozlišení DPI a dynamické podpory DPI do vaší aplikace model Windows Forms najdete [v tématu Podpora vysokého rozlišení DPI v model Windows Forms](../winforms/high-dpi-support-in-windows-forms.md).

<a name="WPF47"></a>

#### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

V .NET Framework 4,7 zahrnuje WPF následující vylepšení:

**Podpora pro sadu dotykové a stylusové sady založená na zprávách Windows WM_POINTER**

Teď máte možnost používat pro [WM_POINTER zprávy](https://docs.microsoft.com/previous-versions/windows/desktop/InputMsg/messages) místo platformy Windows Ink Services (Wispr) k dispozici tónovou nebo stylusovou sadu. Toto je funkce výslovného souhlasu v .NET Framework. Další informace najdete v části [Kompatibilita aplikací](../migration-guide/application-compatibility.md) .

**Nová implementace pro rozhraní API pro tisk WPF**

Rozhraní API pro tisk v platformě WPF ve <xref:System.Printing.PrintQueue?displayProperty=nameWithType> třídě volají [rozhraní API pro tiskové dokumenty](/windows/desktop/printdocs/tailored-app-printing-api) systému Windows namísto zastaralých [tiskových rozhraní XPS](/windows/desktop/printdocs/xps-printing). Dopad této změny na kompatibilitu aplikace naleznete v části [Kompatibilita aplikací](../migration-guide/application-compatibility.md) .

<a name="v462"></a>

## <a name="whats-new-in-net-framework-462"></a>Co je nového v .NET Framework 4.6.2

.NET Framework 4.6.2 zahrnuje nové funkce v následujících oblastech:

- [ASP.NET](#ASPNET462)

- [Kategorie znaků](#Strings)

- [Kryptografie](#Crypto462)

- [SqlClient](#SQLClient)

- [Windows Communication Foundation](#WCF)

- [Windows Presentation Foundation (WPF)](#WPF462)

- [Windows Workflow Foundation (WF)](#WF462)

- [ClickOnce](#clickonce-1)

- [Převod aplikací model Windows Forms a WPF na aplikace pro UWP](#UWPConvert)

- [Vylepšení ladění](#Debug462)

Seznam nových rozhraní API přidaných do .NET Framework 4.6.2 najdete v tématu [.NET Framework změn rozhraní API 4.6.2](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-api-changes.md) na GitHubu. Seznam vylepšení funkcí a oprav chyb v .NET Framework 4.6.2 najdete v článku [.NET Framework 4.6.2 seznam změn](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-changes.md) na GitHubu. Další informace najdete v tématu [oznámení .NET Framework 4.6.2](https://devblogs.microsoft.com/dotnet/announcing-net-framework-4-6-2/) na blogu .NET.

<a name="ASPNET462"></a>

### <a name="aspnet"></a>ASP.NET

ASP.NET v .NET Framework 4.6.2 zahrnuje následující vylepšení:

**Vylepšená podpora pro lokalizované chybové zprávy v validátorech datových poznámek**

Validátory datových poznámek umožňují provádět ověřování přidáním jednoho nebo více atributů do vlastnosti třídy. <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType>Element atributu definuje text chybové zprávy, pokud se ověření nepovede. Počínaje .NET Framework 4.6.2, ASP.NET usnadňuje lokalizaci chybových zpráv. Chybové zprávy budou lokalizovány v těchto případech:

1. <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType>Je k dispozici v atributu ověřování.

2. Soubor prostředků je uložený ve složce App_LocalResources.

3. Název souboru lokalizovaných zdrojů má `DataAnnotation.Localization.{` *název*formuláře `}.resx` , kde *název* je název jazykové verze ve formátu *languageCode* `-` *Country/regionCode* nebo *languageCode*.

4. Klíčovým názvem prostředku je řetězec přiřazený k <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> atributu a jeho hodnota je lokalizovaná chybová zpráva.

Například následující atribut poznámky k datům definuje chybovou zprávu výchozí jazykové verze pro neplatné hodnocení.

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

Pak můžete vytvořit soubor prostředků, dataanotace. Localization. fr. resx, jehož klíč je řetězec chybové zprávy a jehož hodnota je lokalizovaná chybová zpráva. Soubor se musí nacházet ve `App.LocalResources` složce. Například následující je klíč a jeho hodnota v lokalizované chybové zprávě jazyka francouzštiny (FR):

| Název                                 | Hodnota                                     |
| ------------------------------------ | ----------------------------------------- |
| Hodnocení musí být v rozmezí od 1 do 10. | La doit être tvoří meziplatformní 1 et 10. |

 Lokalizace datových poznámek je navíc rozšiřitelná. Vývojáři mohou připojit vlastní poskytovatele řetězce lokalizátora implementací <xref:System.Web.Globalization.IStringLocalizerProvider> rozhraní k uložení lokalizačního řetězce jinde než v souboru prostředků.

 **Asynchronní podpora s poskytovateli úložiště stavu relace**

 ASP.NET teď umožňuje používat metody vracející úlohy s poskytovateli úložiště stavu relace, což aplikacím ASP.NET umožní získat výhody škálovatelnosti Async. Pro podporu asynchronních operací s poskytovateli úložiště stavu relace zahrnuje ASP.NET nové rozhraní, <xref:System.Web.SessionState.ISessionStateModule?displayProperty=nameWithType> které dědí z <xref:System.Web.IHttpModule> a umožňuje vývojářům implementovat vlastní modul stavu relace a zprostředkovatele úložiště asynchronních relací. Rozhraní je definováno následujícím způsobem:

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

 Kromě toho <xref:System.Web.SessionState.SessionStateUtility> Třída obsahuje dvě nové metody <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateReadOnly%2A> a <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateRequired%2A> , které lze použít k podpoře asynchronních operací.

 **Asynchronní podpora pro poskytovatele výstupní mezipaměti**

 Počínaje .NET Framework 4.6.2 lze metody vracející úlohy použít s poskytovateli výstupní mezipaměti k zajištění výhod škálovatelnosti Async.  Poskytovatelé, kteří implementují tyto metody, omezují blokování vláken na webovém serveru a zlepšují škálovatelnost služby ASP.NET.

 Byla přidána následující rozhraní API pro podporu zprostředkovatelů asynchronní výstupní mezipaměti:

- <xref:System.Web.Caching.OutputCacheProviderAsync?displayProperty=nameWithType>Třída, která dědí z <xref:System.Web.Caching.OutputCacheProvider?displayProperty=nameWithType> a umožňuje vývojářům implementovat asynchronního poskytovatele výstupní mezipaměti.

- <xref:System.Web.Caching.OutputCacheUtility>Třída, která poskytuje podpůrné metody pro konfiguraci výstupní mezipaměti.

- 18 nových metod <xref:System.Web.HttpCachePolicy?displayProperty=nameWithType> třídy. Mezi ně patří <xref:System.Web.HttpCachePolicy.GetCacheability%2A> ,,,, <xref:System.Web.HttpCachePolicy.GetCacheExtensions%2A> <xref:System.Web.HttpCachePolicy.GetETag%2A> <xref:System.Web.HttpCachePolicy.GetETagFromFileDependencies%2A> <xref:System.Web.HttpCachePolicy.GetMaxAge%2A> , <xref:System.Web.HttpCachePolicy.GetMaxAge%2A> , <xref:System.Web.HttpCachePolicy.GetNoStore%2A> , <xref:System.Web.HttpCachePolicy.GetNoTransforms%2A> , <xref:System.Web.HttpCachePolicy.GetOmitVaryStar%2A> , <xref:System.Web.HttpCachePolicy.GetProxyMaxAge%2A> , <xref:System.Web.HttpCachePolicy.GetRevalidation%2A> , <xref:System.Web.HttpCachePolicy.GetUtcLastModified%2A> ,, a <xref:System.Web.HttpCachePolicy.GetVaryByCustom%2A> <xref:System.Web.HttpCachePolicy.HasSlidingExpiration%2A> <xref:System.Web.HttpCachePolicy.IsValidUntilExpires%2A> .

- 2 nové metody ve <xref:System.Web.HttpCacheVaryByContentEncodings?displayProperty=nameWithType> třídě: <xref:System.Web.HttpCacheVaryByContentEncodings.GetContentEncodings%2A> a <xref:System.Web.HttpCacheVaryByContentEncodings.SetContentEncodings%2A> .

- 2 nové metody ve <xref:System.Web.HttpCacheVaryByHeaders?displayProperty=nameWithType> třídě: <xref:System.Web.HttpCacheVaryByHeaders.GetHeaders%2A> a <xref:System.Web.HttpCacheVaryByHeaders.SetHeaders%2A> .

- 2 nové metody ve <xref:System.Web.HttpCacheVaryByParams?displayProperty=nameWithType> třídě: <xref:System.Web.HttpCacheVaryByParams.GetParams%2A> a <xref:System.Web.HttpCacheVaryByParams.SetParams%2A> .

- Ve <xref:System.Web.Caching.AggregateCacheDependency?displayProperty=nameWithType> třídě <xref:System.Web.Caching.AggregateCacheDependency.GetFileDependencies%2A> metoda.

- V <xref:System.Web.Caching.CacheDependency> <xref:System.Web.Caching.CacheDependency.GetFileDependencies%2A> metodě metoda.

<a name="Strings"></a>

### <a name="character-categories"></a>Kategorie znaků

Znaky v .NET Framework 4.6.2 jsou klasifikovány na základě [standardu Unicode verze 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/). V .NET Framework 4,6 a .NET Framework 4.6.1 byly znaky klasifikovány na základě kategorií znaků Unicode 6,3.

Podpora Unicode 8,0 je omezená na klasifikaci znaků <xref:System.Globalization.CharUnicodeInfo> třídou a na typy a metody, které na ní spoléhají. Mezi ně patří <xref:System.Globalization.StringInfo> třída, přetížená <xref:System.Char.GetUnicodeCategory%2A?displayProperty=nameWithType> Metoda a [třídy znaků](../../standard/base-types/character-classes-in-regular-expressions.md) rozpoznané modulem .NET Framework regulárních výrazů.  Porovnání znaků a řetězců a jejich řazení není ovlivněno touto změnou a nadále se spoléhá na základní operační systém nebo v systémech Windows 7 na znaková data, která poskytuje .NET Framework.

Změny v kategoriích znaků z Unicode 6,0 až Unicode 7,0 najdete na webu Unicode Consortium na [standardu Unicode verze 7.0.0](https://www.unicode.org/versions/Unicode7.0.0/) . Změny z Unicode 7,0 na Unicode 8,0 najdete na webu Unicode Consortium na [standardu Unicode verze 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/) .

<a name="Crypto462"></a>

### <a name="cryptography"></a>Kryptografie

**Podpora pro certifikáty x509 obsahující FIPS 186-3 DSA**

.NET Framework 4.6.2 přidává podporu certifikátů x509 (Digital Signature Algorithm), jejichž klíče překračují limit bitů FIPS 186-2 1024.

Kromě podpory většího počtu klíčových velikostí FIPS 186-3 umožňuje .NET Framework 4.6.2 výpočetních signatur pomocí řady SHA-2 algoritmů hash (SHA256, SHA384 a SHA512). Podpora FIPS 186-3 je poskytována novou <xref:System.Security.Cryptography.DSACng?displayProperty=nameWithType> třídou.

V případě, že se v <xref:System.Security.Cryptography.RSA> .NET Framework 4,6 a třídě v .NET Framework 4.6.1 zachovává poslední změny třídy <xref:System.Security.Cryptography.ECDsa> , <xref:System.Security.Cryptography.DSA> má abstraktní základní třída v .NET Framework 4.6.2 další metody, které umožňují volajícím používat tuto funkci bez přetypování. Můžete zavolat <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey%2A?displayProperty=nameWithType> metodu rozšíření pro podepsání dat, jak ukazuje následující příklad.

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

A můžete zavolat <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey%2A?displayProperty=nameWithType> metodu rozšíření pro ověření podepsaných dat, jak ukazuje následující příklad.

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

**Větší přehlednost pro vstupy pro rutiny odvození ECDiffieHellman klíčů**

.NET Framework 3,5 přidali podporu pro klíčovou smlouvu Diffie-Hellman s eliptickou křivkou se třemi různými rutinami funkce odvození klíče (KDF). Vstupy pro rutiny a samotné rutiny byly nakonfigurovány prostřednictvím vlastností <xref:System.Security.Cryptography.ECDiffieHellmanCng> objektu. Ale vzhledem k tomu, že ne všechny rutiny čtou všechna vstupní vlastnost, existovala v minulosti pro vás rozsáhlá místnost pro nejasnost.

Pro vyřešení tohoto .NET Framework 4.6.2 byly do základní třídy přidány následující tři metody, <xref:System.Security.Cryptography.ECDiffieHellman> které jasně reprezentují tyto KDF rutiny a jejich vstupy:

|Metoda ECDiffieHellman|Popis|
|----------------------------|-----------------|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHash%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Odvozuje materiál klíče pomocí vzorce.<br /><br /> HASH (secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)<br /><br /> HASH (secretPrepend OrElse *×* OrElse secretAppend)<br /><br /> kde *x* je vypočtený výsledek algoritmu ES Diffie-Hellman.|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHmac%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Odvozuje materiál klíče pomocí vzorce.<br /><br /> HMAC (hmacKey, secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)<br /><br /> HMAC (hmacKey; secretPrepend OrElse *x* OrElse secretAppend)<br /><br /> kde *x* je vypočtený výsledek algoritmu ES Diffie-Hellman.|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyTls%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Odvodí klíč klíče pomocí algoritmu odvození náhodného použití funkce TLS.|

**Podpora trvalého symetrického šifrování s trvalým klíčem**

Knihovna kryptografických služeb systému Windows (CNG) přidala podporu pro ukládání trvalých symetrických klíčů a používání hardwarových symetrických klíčů a .NET Framework 4.6.2 umožňuje vývojářům využít tuto funkci.  Vzhledem k tomu, že pojem názvů klíčů a poskytovatelů klíčů jsou specifické pro konkrétní implementaci, vyžaduje použití této funkce konstruktor konkrétních typů implementace namísto preferovaného přístupu k továrně (například volání `Aes.Create` ).

Pro algoritmy AES ( <xref:System.Security.Cryptography.AesCng> ) a 3DES () existují trvalé podpory symetrického šifrování-Key <xref:System.Security.Cryptography.TripleDESCng> . Příklad:

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
                throw new InvalidOperationException("This is a sample, this case wasn't handled...");
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
                Throw New InvalidOperationException("This is a sample, this case wasn't handled...")
            End If
            Return encryptor.TransformFinalBlock(data, 0, data.Length)
        End Using
    End Using
End Function
```

**Podpora SignedXml pro algoritmus hash SHA-2**

.NET Framework 4.6.2 přidává podporu <xref:System.Security.Cryptography.Xml.SignedXml> tříd pro signatury RSA-SHA256, RSA-SHA384 a RSA-SHA512 pro podpisové metody a SHA256, SHA384 a SHA512 referenční algoritmy Digest.

Konstanty identifikátoru URI jsou všechny vystavené na <xref:System.Security.Cryptography.Xml.SignedXml> :

|Pole SignedXml|Trvalé|
|---------------------|--------------|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA256Url>|"http://www.w3.org/2001/04/xmlenc#sha256"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA256Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha256"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA384Url>|"http://www.w3.org/2001/04/xmldsig-more#sha384"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA384Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha384"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA512Url>|"http://www.w3.org/2001/04/xmlenc#sha512"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA512Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha512"|

 Všechny programy, které zaregistrovaly vlastní <xref:System.Security.Cryptography.SignatureDescription> obslužnou rutinu do nástroje <xref:System.Security.Cryptography.CryptoConfig> pro přidání podpory pro tyto algoritmy, budou i nadále fungovat stejně jako v minulosti, ale vzhledem k tomu, že jsou teď výchozí nastavení platformy, <xref:System.Security.Cryptography.CryptoConfig> registrace už není potřeba.

<a name="SQLClient"></a>

### <a name="sqlclient"></a>SqlClient

.NET Framework Zprostředkovatel dat pro SQL Server ( <xref:System.Data.SqlClient?displayProperty=nameWithType> ) obsahuje následující nové funkce .NET Framework 4.6.2:

**Sdružování připojení a vypršení časových limitů pomocí databází SQL Azure**

Je-li povoleno sdružování připojení a dojde k vypršení časového limitu nebo jiné chyby přihlášení, je výjimka uložena do mezipaměti a při každém následném pokusu o připojení na dalších 5 sekund až 1 minutu je vyvolána výjimka v mezipaměti. Další informace najdete v tématu věnovaném [sdružování připojení SQL Server (ADO.NET)](../data/adonet/sql-server-connection-pooling.md).

Toto chování není vhodné při připojování k databázím Azure SQL, protože pokusy o připojení mohou selhat s přechodem k přechodným chybám, které se obvykle obnovují rychle. Pro lepší optimalizaci možností opakovaného pokusu o připojení se při selhání připojení k databázím Azure SQL odstraní chování při blokování fondu připojení.

Přidání `PoolBlockingPeriod` klíčového slova New vám umožní vybrat dobu blokování, která se pro vaši aplikaci nejlépe hodí. Mezi tyto hodnoty patří:

<xref:System.Data.SqlClient.PoolBlockingPeriod.Auto>

Doba blokování fondu připojení pro aplikaci, která se připojuje k Azure SQL Database je zakázána a je povolená doba blokování fondu připojení pro aplikaci, která se připojuje k jakékoli jiné instanci SQL Server. Toto je výchozí hodnota. Pokud název koncového bodu serveru končí některým z následujících, považují se za databáze SQL Azure:

- . database.windows.net

- . database.chinacloudapi.cn

- . database.usgovcloudapi.net

- . database.cloudapi.de

<xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock>

Doba blokování fondu připojení je vždycky povolená.

<xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock>

Doba blokování fondu připojení je vždycky zakázaná.

**Vylepšení pro Always Encrypted**

SQLClient přináší dvě vylepšení pro Always Encrypted:

- Pro zlepšení výkonu parametrizovaných dotazů proti šifrovaným databázovým sloupcům jsou metadata šifrování pro parametry dotazu nyní ukládána do mezipaměti. <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled%2A?displayProperty=nameWithType>Pokud je vlastnost nastavena na `true` (což je výchozí hodnota), je-li stejný dotaz volán několikrát, klient načte metadata parametrů ze serveru pouze jednou.

- Položky šifrovacího klíče sloupce v mezipaměti klíčů jsou teď po konfigurovatelném časovém intervalu vyřazení, které nastavíte pomocí <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionKeyCacheTtl%2A?displayProperty=nameWithType> Vlastnosti.

<a name="WCF"></a>

### <a name="windows-communication-foundation"></a>Windows Communication Foundation

V .NET Framework 4.6.2 byly Windows Communication Foundation rozšířeny v následujících oblastech:

**Podpora zabezpečení přenosu WCF pro certifikáty uložené pomocí CNG**

Zabezpečení přenosu WCF podporuje certifikáty uložené pomocí knihovny kryptografických služeb systému Windows (CNG). V .NET Framework 4.6.2 je tato podpora omezená na použití certifikátů s veřejným klíčem, který má exponent větší než 32 bitů. Když je aplikace cílena na .NET Framework 4.6.2, je tato funkce ve výchozím nastavení zapnutá.

Pro aplikace, které cílí na .NET Framework 4.6.1 a starší, ale běží na .NET Framework 4.6.2, je možné tuto funkci povolit přidáním následujícího řádku do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) části souboru app.config nebo web.config.

```xml
<AppContextSwitchOverrides
    value="Switch.System.ServiceModel.DisableCngCertificates=false"
/>
```

To lze provést také programově s kódem podobným následujícímu:

```csharp
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificates";
AppContext.SetSwitch(disableCngCertificates, false);
```

```vb
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"
AppContext.SetSwitch(disableCngCertificates, False)
```

**Lepší podpora více pravidel úprav více letního času pomocí třídy DataContractJsonSerializer**

Zákazníci mohou použít nastavení konfigurace aplikace k určení, zda <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Třída podporuje více pravidel úprav pro jedno časové pásmo. Toto je funkce výslovného souhlasu. Pokud ho chcete povolit, přidejte do souboru app.config následující nastavení:

```xml
<runtime>
     <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseTimeZoneInfo=false" />
</runtime>
```

Když je tato funkce povolená, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> objekt <xref:System.TimeZoneInfo> místo <xref:System.TimeZone> typu použije k deserializaci dat data a času typ. <xref:System.TimeZoneInfo>podporuje více pravidel úprav, což umožňuje pracovat s historickými daty časových pásem;   <xref:System.TimeZone>není.

Další informace o <xref:System.TimeZoneInfo> úpravách struktury a časových pásem najdete v tématu [Přehled časových pásem](../../standard/datetime/time-zone-overview.md).

**NetNamedPipeBinding nejlepší shody**

Služba WCF má nové nastavení aplikace, které lze nastavit na klientských aplikacích, aby bylo zajištěno, že se budou vždy připojovat ke službě naslouchat na identifikátoru URI, který nejlépe odpovídá tomu, kterou vyžádají. Když je nastavení této aplikace nastaveno na `false` (výchozí), klienti nástroje používají <xref:System.ServiceModel.NetNamedPipeBinding> k pokusu o připojení ke službě naslouchající na identifikátoru URI, který je podřetězec požadovaného identifikátoru URI.

Například klient se pokusí připojit ke službě naslouchat na adrese `net.pipe://localhost/Service1` , ale na tomto počítači, na kterém je spuštěná s oprávněním správce, naslouchá jiná služba `net.pipe://localhost` . Když je nastavení této aplikace nastaveno na `false` , klient se pokusí připojit k nesprávné službě. Po nastavení nastavení aplikace se `true` Klient vždy připojí k nejlépe vyhovující službě.

> [!NOTE]
> Klienti používají <xref:System.ServiceModel.NetNamedPipeBinding> Najít služby na základě základní adresy služby (pokud existuje), nikoli úplné adresy koncového bodu. Chcete-li zajistit, aby toto nastavení vždy fungovalo, měla by služba používat jedinečnou základní adresu.

Pokud chcete tuto změnu povolit, přidejte do souboru App.config nebo Web.config klientské aplikace následující nastavení aplikace:

```xml
<configuration>
    <appSettings>
        <add key="wcf:useBestMatchNamedPipeUri" value="true" />
    </appSettings>
</configuration>
```

**SSL 3,0 není výchozím protokolem.**

Pokud používáte NetTcp se zabezpečením přenosu a typem přihlašovacích údajů certifikátu, SSL 3,0 už není výchozím protokolem používaným pro vyjednávání zabezpečeného připojení. Ve většině případů by nemělo dojít k žádným dopadům na existující aplikace, protože TLS 1,0 je zahrnutý v seznamu protokolů pro NetTcp. Všichni existující klienti by měli být schopni vyjednat připojení pomocí aspoň TLS 1,0. Pokud se vyžaduje SSL3, použijte jeden z následujících konfiguračních mechanismů a přidejte ho do seznamu sjednaných protokolů.

- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=nameWithType>Vlastnost

- <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType>Vlastnost

- [\<transport>](../configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)Část [\<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md) oddílu

- [\<sslStreamSecurity>](../configure-apps/file-schema/wcf/sslstreamsecurity.md)Část [\<customBinding>](../configure-apps/file-schema/wcf/custombinding.md) oddílu

<a name="WPF462"></a>

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

V .NET Framework 4.6.2 byly Windows Presentation Foundation rozšířeny v následujících oblastech:

**Seskupení řazení**

Aplikace, která používá <xref:System.Windows.Data.CollectionView> objekt k seskupení dat, teď může explicitně deklarovat způsob řazení skupin. Explicitní řazení řeší problém neintuitivního řazení, ke kterému dochází, když aplikace dynamicky přidává nebo odebírá skupiny nebo když změní hodnotu vlastností položek, které jsou součástí seskupení. Může také zvýšit výkon procesu vytváření skupiny přesunutím porovnání vlastností seskupení z řazení celé kolekce do řazení skupin.

Aby bylo možné podporovat řazení skupin, nové <xref:System.ComponentModel.GroupDescription.SortDescriptions%2A?displayProperty=nameWithType> a <xref:System.ComponentModel.GroupDescription.CustomSort%2A?displayProperty=nameWithType> vlastnosti popisují způsob řazení kolekce skupin vytvořených <xref:System.ComponentModel.GroupDescription> objektem. To je analogické jako způsob, jakým identicky pojmenované <xref:System.Windows.Data.ListCollectionView> vlastnosti popisují způsob řazení datových položek.

Dvě nové statické vlastnosti <xref:System.Windows.Data.PropertyGroupDescription> třídy <xref:System.Windows.Data.PropertyGroupDescription.CompareNameAscending%2A> a <xref:System.Windows.Data.PropertyGroupDescription.CompareNameDescending%2A> lze použít v nejběžnějších případech.

Například následující XAML seskupuje data podle stáří, řadí věkové skupiny ve vzestupném pořadí a seskupuje položky v rámci každé věkové skupiny podle příjmení.

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

Podpora dotykové klávesnice umožňuje sledovat fokus v aplikacích WPF automatickým vyvoláním a chybějícím dotykovou klávesnicí ve Windows 10, když je vstup dotykového ovládání přijatý ovládacím prvkem, který může přebírat textový vstup.

V předchozích verzích .NET Framework se aplikace WPF nemůžou vyjádřit k sledování fokusu bez zakázání podpory gesta perem a dotykového ovládání WPF. V důsledku toho musí aplikace WPF zvolit mezi plnou podporou WPF touch nebo se spoléhat na povýšení myší systému Windows.

**Rozlišení DPI pro monitor**

Pro podporu nedávných rozmnožení prostředí s vysokým rozlišením DPI a hybridních DPI pro aplikace WPF se v .NET Framework 4.6.2 umožňuje sledovat jednotlivé monitory. Další informace o tom, jak povolit aplikaci WPF pro monitorování rozlišení DPI na monitoru, najdete v [ukázkách a v příručce pro vývojáře](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI) na GitHubu.

V předchozích verzích .NET Framework aplikace WPF používají systémovou rozlišení DPI. Jinými slovy, uživatelské rozhraní aplikace se podle potřeby škáluje operačním systémem, v závislosti na DPI monitoru, na kterém je aplikace vykreslená.

Pro aplikace běžící pod .NET Framework 4.6.2 můžete v aplikacích WPF zakázat změny rozlišení DPI podle monitoru přidáním příkazu konfigurace do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace následujícím způsobem:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Windows.DoNotScaleForDpiChanges=false"/>
</runtime>
```

<a name="WF462"></a>

### <a name="windows-workflow-foundation-wf"></a>Windows Workflow Foundation (WF)

V .NET Framework 4.6.2 bylo programovací model Windows Workflow Foundation vylepšeno v následující oblasti:

**Podpora pro výrazy jazyka C# a IntelliSense v přehostovaném návrháři WF**

Počínaje .NET Framework 4,5 podporuje WF výrazy jazyka C# v návrháři sady Visual Studio i v pracovních postupech kódu. Rehostovaná Návrhář postupu provádění je klíčovou funkcí WF, která umožňuje, aby se Návrhář postupu provádění v aplikaci mimo Visual Studio (například v WPF).  Programovací model Windows Workflow Foundation poskytuje možnost podporovat výrazy jazyka C# a IntelliSense v Návrhář postupu provádění hostitele. Další informace najdete na [blogu programovací model Windows Workflow Foundation](https://docs.microsoft.com/archive/blogs/workflowteam/building-c-expressions-support-and-intellisense-in-the-rehosted-workflow-designer).

`Availability of IntelliSense when a customer rebuilds a workflow project from Visual Studio`Ve verzích .NET Framework před 4.6.2 se IntelliSense Návrháře WF při opětovném sestavení projektu pracovního postupu ze sady Visual Studio přeruší. I když je sestavení projektu úspěšné, typy pracovních postupů nejsou v Návrháři nalezeny a upozornění z IntelliSense pro chybějící typy pracovních postupů se zobrazí v okně **Seznam chyb** . .NET Framework 4.6.2 řeší tento problém a zpřístupňuje IntelliSense.

**Aplikace pracovního postupu V1 se sledováním pracovních postupů zapnuto v režimu FIPS**

Počítače s povoleným režimem dodržování standardů FIPS teď můžou úspěšně spustit aplikaci ve stylu pracovního postupu verze 1 se sledováním pracovních postupů zapnutým. Chcete-li povolit tento scénář, musíte provést následující změnu app.config souboru:

```xml
<add key="microsoft:WorkflowRuntime:FIPSRequired" value="true" />
```

Pokud tento scénář není povolený, bude při spuštění aplikace i nadále vygenerována výjimka se zprávou "Tato implementace není součástí ověřených kryptografických algoritmů standardu FIPS platformy Windows."

**Vylepšení pracovního postupu při použití dynamické aktualizace se sadou Visual Studio Návrhář postupu provádění**

Návrháři aktivity Návrhář postupu provádění, vývojový diagram a jiní návrháři aktivit pracovního postupu nyní úspěšně načetli a zobrazili pracovní postupy, které byly uloženy po volání <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> metody. Ve verzích .NET Framework před .NET Framework 4.6.2 načítání souboru XAML v sadě Visual Studio pro pracovní postup, který byl uložen po volání, <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> může způsobit následující problémy:

- Návrhář postupu provádění nemůže správně načíst soubor XAML (když <xref:System.Activities.Presentation.ViewState.ViewStateData.Id%2A?displayProperty=nameWithType> je na konci řádku).

- Návrhář aktivity vývojového diagramu nebo jiný Návrhář aktivity pracovního postupu může zobrazit všechny objekty ve výchozích umístěních na rozdíl od hodnot připojených vlastností.

<a name="clickonce-1"></a>

### <a name="clickonce"></a>ClickOnce

ClickOnce je aktualizovaná tak, aby podporovala TLS 1,1 a TLS 1,2 kromě protokolu 1,0, který už podporuje. ClickOnce automaticky zjišťuje, který protokol je vyžadován; aby bylo možné povolit podporu TLS 1,1 a 1,2, nejsou v rámci aplikace ClickOnce nutné žádné další kroky.

<a name="UWPConvert"></a>

### <a name="converting-windows-forms-and-wpf-apps-to--uwp-apps"></a>Převod aplikací model Windows Forms a WPF na aplikace pro UWP

Windows teď nabízí možnosti, jak přenést existující desktopové aplikace pro Windows, včetně WPF a model Windows Forms aplikací, do Univerzální platforma Windows (UWP). Tato technologie funguje jako most, protože vám umožní postupně migrovat stávající základ kódu na UWP. tím se vaše aplikace přinášejí všem zařízením s Windows 10.

Převedená aplikace klasické pracovní plochy získala identitu aplikace podobnou identitě aplikací v aplikacích UWP, což zpřístupňuje rozhraní API UWP pro povolení funkcí, jako jsou živé dlaždice a oznámení. Aplikace se i nadále chová stejně jako dřív a běží jako aplikace s plnou důvěryhodností. Po převedení aplikace lze do stávajícího procesu úplného vztahu důvěryhodnosti přidat proces kontejneru aplikace a přidat adaptivní uživatelské rozhraní. Když se všechny funkce přesunou do procesu kontejneru aplikace, může se odebrat úplný proces důvěryhodnosti a nová aplikace pro UWP se dá zpřístupnit pro všechna zařízení s Windows 10.

<a name="Debug462"></a>

### <a name="debugging-improvements"></a>Vylepšení ladění

*Rozhraní API pro nespravované ladění* bylo vylepšeno v .NET Framework 4.6.2, aby bylo možné provést další analýzu při <xref:System.NullReferenceException> vyvolání, aby bylo možné určit, která proměnná v jednom řádku zdrojového kódu je `null` .   Pro podporu tohoto scénáře byla do nespravovaného ladicího rozhraní API přidána následující rozhraní API.

- Rozhraní [ICorDebugCode4](../unmanaged-api/debugging/icordebugcode4-interface.md), [ICorDebugVariableHome](../unmanaged-api/debugging/icordebugvariablehome-interface.md)a [ICorDebugVariableHomeEnum](../unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) , která zveřejňují nativní domy spravovaných proměnných. To umožňuje ladicím programům provádět některé analýzy toku kódu <xref:System.NullReferenceException> , když dojde k chybě a chcete-li pracovat zpět k určení spravované proměnné, která odpovídá nativnímu umístění, které bylo `null` .

- Metoda [ICorDebugType2:: GetTypeId.](../unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) poskytuje mapování pro ICorDebugType pro [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md), což ladicímu programu umožňuje získat [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) bez instance ICorDebugType. Existující rozhraní API na [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) lze použít k určení rozložení třídy typu.

<a name="v461"></a>

## <a name="whats-new-in-net-framework-461"></a>Co je nového v .NET Framework 4.6.1

.NET Framework 4.6.1 zahrnuje nové funkce v následujících oblastech:

- [Kryptografie](#Crypto)

- [ADO.NET](#ADO.NET461)

- [Windows Presentation Foundation (WPF)](#WPF461)

- [Windows Workflow Foundation](#WWF461)

- [Profilace](#Profile461)

- [NGen](#NGEN461)

Další informace o .NET Framework 4.6.1 najdete v následujících tématech:

- [Seznam změn .NET Framework 4.6.1](https://github.com/Microsoft/dotnet/blob/master/releases/net461/dotnet461-changes.md)

- [Kompatibilita aplikací v 4.6.1](../migration-guide/application-compatibility.md)

- [Rozdíl .NET Framework rozhraní API](https://github.com/Microsoft/dotnet/blob/master/releases/net461/dotnet461-api-changes.md) (na GitHubu)

<a name="Crypto"></a>

### <a name="cryptography-support-for-x509-certificates-containing-ecdsa"></a>Kryptografie: podpora pro certifikáty x509 obsahující ECDSA

.NET Framework 4,6 přidal podporu algoritmem RSACng pro certifikáty x509. .NET Framework 4.6.1 přidává podporu pro certifikáty x509 ECDSA (s eliptickou křivkou pro digitální podpis algoritmu).

ECDSA nabízí lepší výkon a jedná se o bezpečnější algoritmus šifrování než RSA. poskytuje skvělou volbu toho, kde je výkon a škálovatelnost protokolu TLS (Transport Layer Security) obavy. Implementace .NET Framework zabalí volání do stávajících funkcí systému Windows.

Následující příklad kódu ukazuje, jak snadné je generovat signaturu pro datový proud bajtů pomocí nové podpory pro certifikáty ECDSA x509 zahrnuté do .NET Framework 4.6.1.

[!code-csharp[whatsnew.461.crypto#1](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#1)]
[!code-vb[whatsnew.461.crypto#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code461.vb#1)]

To nabízí označený rozdíl na kód potřebný k vygenerování podpisu v .NET Framework 4,6.

[!code-csharp[whatsnew.461.crypto#2](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#2)]
[!code-vb[whatsnew.461.crypto#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code46.vb#2)]

<a name="ADO.NET461"></a>

### <a name="adonet"></a>ADO.NET

Do ADO.NET byly přidány následující:

**Always Encrypted podpora pro klíče chráněné hardwarem**

ADO.NET teď podporuje nativně ukládání Always Encrypted hlavních klíčů sloupce v modulech zabezpečení hardwaru (HSM). Díky této podpoře můžou zákazníci využívat asymetrické klíče uložené v HSM, aniž by museli psát vlastní Zprostředkovatelé úložiště klíčů pro vlastní sloupce a zaregistrovali je v aplikacích.

Aby mohli uživatelé získat přístup k Always Encrypted chráněným pomocí hlavních klíčů, které jsou uložené v modulu hardwarového zabezpečení (HSM), musí si do aplikačních serverů nebo klientských počítačů nainstalovat poskytovatele kryptografických služeb na základě dodavatele modulu hardwarového zabezpečení (HSM).

**Vylepšené <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> chování připojení pro AlwaysOn**

SqlClient nyní automaticky poskytuje rychlejší připojení ke skupině dostupnosti AlwaysOn (AG). Transparentně detekuje, jestli se vaše aplikace připojuje ke skupině dostupnosti AlwaysOn (AG) v jiné podsíti, a rychle zjistí aktuální aktivní server a poskytuje připojení k serveru. Před touto verzí musela aplikace nastavit připojovací řetězec tak, aby obsahovala `"MultisubnetFailover=true"` , aby označovala, že se připojil ke skupině dostupnosti AlwaysOn. Bez nastavení klíčového slova Connection na `true` se může u aplikace při připojování ke skupině dostupnosti AlwaysOn vyskytnout časový limit. V této *verzi nemusí aplikace* nastavovat <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> `true` již. Další informace o podpoře SqlClient pro skupiny dostupnosti Always On najdete v článku [Podpora SqlClient pro vysokou dostupnost a zotavení po havárii](../data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md).

<a name="WPF461"></a>

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

Windows Presentation Foundation zahrnuje řadu vylepšení a změn.

**Vylepšený výkon**

Zpoždění při vyvolávání událostí dotyku bylo opraveno .NET Framework 4.6.1. Kromě toho psaní v <xref:System.Windows.Controls.RichTextBox> ovládacím prvku již během rychlého vstupu nespojuje vlákno vykreslování.

**Vylepšení kontroly pravopisu**

Kontrola pravopisu v subsystému WPF byla aktualizována na Windows 8.1 a novějších verzích, aby bylo možné využívat operační systém pro kontrolu pravopisu dalších jazyků.  Před Windows 8.1 se ve verzích Windows nezměnily žádné funkce.

Stejně jako v předchozích verzích .NET Framework se detekuje jazyk pro <xref:System.Windows.Controls.TextBox> Ora blok ovládacího prvku <xref:System.Windows.Controls.RichTextBox> hledáním informací v následujícím pořadí:

- `xml:lang`, pokud je k dispozici.

- Aktuální jazyk vstupu.

- Aktuální jazyková verze vlákna.

Další informace o podpoře jazyků v subsystému WPF najdete v [blogovém příspěvku WPF o funkcích .NET Framework 4.6.1](https://devblogs.microsoft.com/wpf/wpf-in-net-4-6-1/).

**Další podpora pro vlastní slovníky pro jednotlivé uživatele**

V .NET Framework 4.6.1 rozpozná WPF vlastní slovníky, které jsou zaregistrované globálně. Tato funkce je kromě možnosti registrace pro jednotlivé ovládací prvky k dispozici.

V předchozích verzích WPF vlastní slovníky nerozpoznaly vyloučená slova a seznamy automatických oprav. Jsou podporovány v Windows 8.1 a Windows 10 prostřednictvím souborů, které lze umístit do `%AppData%\Microsoft\Spelling\<language tag>` adresáře.  Následující pravidla se vztahují na tyto soubory:

- Soubory by měly mít přípony. dic (pro přidaná slova),. EXC (vyloučená slova) nebo. ACL (pro automatické opravy).

- Soubory by měly být UTF-16 LE prostého textu, který začíná znakem pořadí bajtů (BOM).

- Každý řádek by měl obsahovat slovo (v seznamech přidaných a vyloučených slov) nebo dvojici automatických slov oddělených svislým pruhem ("&#124;") (v seznamu slov pro automatické opravy).

- Tyto soubory jsou považovány za jen pro čtení a systém je nemění.

> [!NOTE]
> Tyto nové formáty souborů nejsou přímo podporovány rozhraními API pro kontrolu pravopisu WPF a vlastní slovníky dodávané WPF v aplikacích by měly dál používat soubory. lex.

**ukázky**

V úložišti GitHub [Microsoft/WPF-Samples](https://github.com/Microsoft/WPF-Samples) je několik ukázek WPF. Nám pomůžou vylepšit naše ukázky odesláním žádosti o přijetí změn nebo otevřením [problému GitHubu](https://github.com/Microsoft/WPF-Samples/issues).

**Rozšíření DirectX**

WPF obsahuje [balíček NuGet](https://www.nuget.org/packages/Microsoft.Wpf.Interop.DirectX-x86/) , který poskytuje nové implementace, které usnadňují <xref:System.Windows.Interop.D3DImage> spolupráci s DX10 a DX11 obsahem. Kód pro tento balíček je otevřený source a je dostupný [na GitHubu](https://github.com/Microsoft/WPFDXInterop).

<a name="WWF461"></a>

### <a name="windows-workflow-foundation-transactions"></a>Programovací model Windows Workflow Foundation: transakcí

<xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType>Metoda teď může použít jiný správce distribuovaných transakcí než MSDTC k povýšení transakce. To provedete tak, že zadáte identifikátor ID zvýšení transakce GUID k novému <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> přetížení. Pokud je tato operace úspěšná, existují omezení na možnosti transakce. Jakmile je povýšen na transakci bez služby MSDTC, následující metody vyvolávají výjimku, <xref:System.Transactions.TransactionPromotionException> protože tyto metody vyžadují povýšení na MSDTC:

- <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetDtcTransaction%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetExportCookie%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetTransmitterPropagationToken%2A?displayProperty=nameWithType>

Jakmile je vyřazení transakce bez služby MSDTC, je nutné ji použít pro budoucí trvalé zařazení pomocí protokolů, které definuje. Na <xref:System.Guid> zvýšení transakce lze získat pomocí <xref:System.Transactions.Transaction.PromoterType%2A> Vlastnosti. V případě, že transakce propaguje, poskytne vykonavatel transakce <xref:System.Byte> pole, které představuje povýšený token. Aplikace může získat povýšený token pro transakci, která není povýšena MSDTC, s <xref:System.Transactions.Transaction.GetPromotedToken%2A> metodou.

Aby <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> bylo možné operaci povýšení úspěšně dokončit, musí se uživatelé nového přetížení řídit konkrétní sekvencí volání. Tato pravidla jsou popsána v dokumentaci metody.

<a name="Profile461"></a>

### <a name="profiling"></a>Profilace

Nespravované rozhraní API profilování bylo vylepšeno následujícím způsobem:

- Lepší podpora pro přístup k soubory PDB v rozhraní [ICorProfilerInfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) .

  V ASP.NET Core se sestavení stane mnohem častější, aby sestavení bylo zkompilováno v paměti pomocí Roslyn. Pro vývojáře, kteří vytvářejí nástroje pro profilaci, to znamená, že soubory PDB, který historicky byly serializovány na disk, již nemusí být k dispozici. Nástroje profileru často používají soubory PDB k mapování kódu zpět na zdrojové řádky pro úlohy, jako je pokrytí kódu nebo analýza výkonu po jednotlivých řádcích. Rozhraní [ICorProfilerInfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) nyní obsahuje dvě nové metody, [ICorProfilerInfo7:: GetInMemorySymbolsLength](../unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md) a [ICorProfilerInfo7:: ReadInMemorySymbols](../unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)k poskytnutí těchto nástrojů profileru s přístupem k datům PDB v paměti pomocí nových rozhraní API může Profiler získat obsah souboru PDB v paměti jako bajtové pole a pak ho zpracovat nebo serializovat na disk.

- Lepší instrumentaci pomocí rozhraní ICorProfiler.

  Profilery, které používají `ICorProfiler` funkci ReJIT rozhraní API pro dynamickou instrumentaci, teď můžou upravovat některá metadata. Dříve takové nástroje mohly instrumentaci IL kdykoli instrumentovat, ale metadata se dají upravovat jenom v době načtení modulu. Vzhledem k tomu, že IL odkazuje na metadata, omezíme tak druhy instrumentace, které by bylo možné provést. Některé z těchto omezení jsme převedli přidáním metody [ICorProfilerInfo7:: ApplyMetaData](../unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md) pro podporu podmnožiny úprav metadat po načtení modulu, zejména přidáním nových `AssemblyRef` záznamů,,,, a `TypeRef` `TypeSpec` `MemberRef` `MemberSpec` `UserString` . Tato změna přináší mnohem širší množství možností instrumentace.

<a name="NGEN461"></a>

### <a name="native-image-generator-ngen-pdbs"></a>Generátor nativních bitových kopií (NGEN) soubory PDB

Trasování událostí mezi počítači umožňuje zákazníkům profilovat program na počítači a a prohlédnout si data profilace pomocí mapování zdrojového řádku na počítači B. pomocí předchozích verzí .NET Framework, uživatel zkopíruje všechny moduly a nativní bitové kopie z profilované počítače do počítače analýzy, který obsahuje soubor. PDB, aby vytvořil mapování zdrojové na nativní. I když tento proces může fungovat i v případě, že jsou soubory relativně malé, například pro telefonní aplikace, můžou být soubory velmi velké na stolních počítačích a vyžadovat delší dobu kopírování.

V případě Ngen soubory PDB může NGen vytvořit PDB, který obsahuje mapování IL-to-Native bez závislosti na souboru PDB IL. V našem scénáři trasování událostí mezi počítači je potřeba ke zkopírování nativní bitové kopie image generované počítačem A na počítač B a k použití rozhraní [API pro přístup k rozhraní ladění](/visualstudio/debugger/debug-interface-access/debug-interface-access-sdk-reference) , aby se načetlo mapování typu source-to-Il z nativního souboru PDB na nativní. Kombinování obou mapování poskytuje mapování zdrojové na nativní. Vzhledem k tomu, že je soubor PDB nativní image mnohem menší než všechny moduly a nativní bitové kopie, proces kopírování z počítače A na počítač B je mnohem rychlejší.

<a name="v46"></a>

## <a name="whats-new-in-net-2015"></a>Co je nového v .NET 2015

.NET 2015 zavádí .NET Framework 4,6 a .NET Core. Některé nové funkce platí i pro i další funkce jsou specifické pro .NET Framework 4,6 nebo .NET Core.

- **ASP.NET Core**

  .NET 2015 zahrnuje ASP.NET Core, což je implementace štíhlé aplikace .NET pro vytváření moderních cloudových aplikací. ASP.NET Core je modulární, takže můžete zahrnout jenom ty funkce, které jsou potřeba ve vaší aplikaci. Dá se hostovat ve službě IIS nebo v místním prostředí ve vlastním procesu a můžete spouštět aplikace s různými verzemi .NET Framework na stejném serveru. Obsahuje nový systém konfigurace prostředí, který je určený pro nasazení v cloudu.

  MVC, webové rozhraní API a webové stránky jsou sjednocené do jediného rozhraní s názvem MVC 6. ASP.NET Core aplikace můžete vytvářet prostřednictvím nástrojů v aplikaci Visual Studio 2015 nebo novější. Stávající aplikace budou fungovat na novém .NET Framework. Chcete-li však vytvořit aplikaci, která používá MVC 6 nebo Signal 3, je nutné použít systém projektu v aplikaci Visual Studio 2015 nebo novější.

  Informace najdete v tématu [ASP.NET Core](/aspnet/core/).

- **ASP.NET aktualizace**

  - **Rozhraní API založené na úlohách pro vyprazdňování asynchronních odpovědí**

    ASP.NET nyní poskytuje jednoduché rozhraní API založené na úlohách pro vyprazdňování asynchronních odpovědí, <xref:System.Web.HttpResponse.FlushAsync%2A?displayProperty=nameWithType> což umožňuje, aby odpovědi byly vyčištěny asynchronně pomocí podpory vašeho jazyka `async/await` .

  - **Vazba modelu podporuje metody vracející úlohy**

    V .NET Framework 4,5 přidal ASP.NET funkci vazby modelu, která povolila rozšiřitelný přístup k datům na základě kódu, na stránky webových formulářů a uživatelské ovládací prvky. Systém vazby modelu teď podporuje <xref:System.Threading.Tasks.Task> – vrací metody vazby modelu. Tato funkce umožňuje vývojářům webových formulářů získat výhody škálovatelnosti v rámci asynchronního přenosu dat při použití novějších verzí systému ORMs, včetně Entity Framework.

    Vazba asynchronního modelu je řízena `aspnet:EnableAsyncModelBinding` nastavením konfigurace.

    ```xml
    <appSettings>
        <add key=" aspnet:EnableAsyncModelBinding" value="true|false" />
    </appSettings>
    ```

    U aplikací, které cílí na .NET Framework 4,6, se nastaví jako výchozí `true` . V aplikacích běžících na .NET Framework 4,6, které cílí na starší verzi .NET Framework, je `false` ve výchozím nastavení. Dá se povolit nastavením nastavení konfigurace na `true` .

  - **Podpora HTTP/2 (Windows 10)**

    [Http/2](https://www.wikipedia.org/wiki/HTTP/2) je nová verze protokolu HTTP, která poskytuje mnohem lepší využití připojení (méně zpátečních cest mezi klientem a serverem). Výsledkem je načítání webových stránek s nižší latencí pro uživatele.  Webové stránky (na rozdíl od služeb) využívají maximum HTTP/2, protože protokol je optimalizován pro více artefaktů, které jsou požadovány v rámci jednoho prostředí. Do ASP.NET v .NET Framework 4,6 byla přidána podpora protokolu HTTP/2. Vzhledem k tomu, že síťové funkce existují na více vrstvách, byly v systému Windows, ve službě IIS a v ASP.NET k dispozici nové funkce pro povolení protokolu HTTP/2. Abyste mohli používat HTTP/2 s ASP.NET, musíte běžet na Windows 10.

    Pro aplikace Windows 10 Univerzální platforma Windows (UWP), které používají rozhraní API, se standardně podporuje i HTTP/2 <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> .

    Aby bylo možné používat funkci [PUSH_PROMISE](https://http2.github.io/http2-spec/#PUSH_PROMISE) v aplikacích ASP.NET, je nová metoda se dvěma přetíženími <xref:System.Web.HttpResponse.PushPromise%28System.String%29> a <xref:System.Web.HttpResponse.PushPromise%28System.String%2CSystem.String%2CSystem.Collections.Specialized.NameValueCollection%29> přidána do <xref:System.Web.HttpResponse> třídy.

    > [!NOTE]
    > I když ASP.NET Core podporuje HTTP/2, podpora funkce PUSH Promise ještě není přidaná.

    Prohlížeč a webový server (IIS v systému Windows) mají veškerou práci. Nemusíte pro uživatele dělat těžkou zdvihání.

    Většina [hlavních prohlížečů podporuje HTTP/2](https://www.wikipedia.org/wiki/HTTP/2), takže pokud je server podporuje, bude vám vaše uživatelé moci podporu HTTP/2 využít.

  - **Podpora pro protokol vazby tokenů**

    Microsoft a Google spolupracuje na novém přístupu k ověřování, který se nazývá [protokol vazby tokenů](https://github.com/TokenBinding/Internet-Drafts). Místní je, že ověřovací tokeny (v mezipaměti prohlížeče) můžou být odcizené a používané podvodníky pro přístup k jiným zabezpečeným prostředkům (třeba k bankovnímu účtu) bez vyžadování hesla nebo jakýchkoli dalších privilegovaných znalostí. Nový protokol se zaměřuje na zmírnění tohoto problému.

    Protokol vazby tokenu bude v systému Windows 10 implementován jako funkce prohlížeče. Aplikace ASP.NET se budou podílet na protokolu, aby ověřovací tokeny byly ověřené jako legitimní. Implementace klienta a serveru vytvoří kompletní ochranu určenou protokolem.

  - **Algoritmy hash s náhodným řetězcem**

    .NET Framework 4,5 představil [algoritmus hash s náhodným řetězcem](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md). ASP.NET ho ale nepodporuje, protože některé funkce ASP.NET jsou závislé na stabilním kódu hash. V .NET Framework 4,6 jsou nyní podporovány algoritmy hash s náhodným řetězcem. Pokud chcete tuto funkci povolit, použijte `aspnet:UseRandomizedStringHashAlgorithm` nastavení konfigurace.

    ```xml
    <appSettings>
        <add key="aspnet:UseRandomizedStringHashAlgorithm" value="true|false" />
    </appSettings>
    ```

- **ADO.NET**

  Rozhraní ADO .NET teď podporuje funkci Always Encrypted dostupnou v SQL Server 2016 Community Technology Preview 2 (CTP2). Pomocí Always Encrypted může SQL Server provádět operace s šifrovanými daty a nejlepší ze všech šifrovacích klíčů se nachází v rámci důvěryhodného prostředí zákazníka, nikoli na serveru. Always Encrypted zabezpečuje zákaznická data, takže specializující nemají přístup k datům ve formátu prostého textu. Šifrování a dešifrování dat probíhá transparentně na úrovni ovladače a minimalizuje změny, které je třeba provést u existujících aplikací. Podrobnosti najdete v tématu [Always Encrypted (databázový stroj)](/sql/relational-databases/security/encryption/always-encrypted-database-engine) a [Always Encrypted (vývoj klientů)](/sql/relational-databases/security/encryption/always-encrypted-client-development).

- **64 kompilátor JIT pro spravovaný kód**

  .NET Framework 4,6 obsahuje novou verzi 64 kompilátoru JIT (původně kódu s názvem RyuJIT). Nový 64 kompilátor poskytuje významné zlepšení výkonu oproti staršímu 64 kompilátoru JIT. Nový 64 kompilátor je povolen pro 64 procesy spuštěné nad .NET Framework 4,6. Vaše aplikace bude spuštěna v 64m procesu, pokud je kompilována jako 64-bit nebo AnyCPU a je spuštěna v operačním systému 64. I když jste se ujistili, že přechod na nový kompilátor je co možná transparentní, jsou možné změny v chování.

  Nový 64 kompilátor JIT zahrnuje také funkce akcelerace hardwarového SIMDu v případě, že se v oboru názvů společně s typy SIMD podporují <xref:System.Numerics> , což může přinést dobré zlepšení výkonu.

- **Vylepšení zavaděče sestavení**

  Zavaděč sestavení nyní používá paměť efektivněji uvolněním sestavení IL po načtení odpovídající image NGEN. Tato změna snižuje virtuální paměť, což je zvláště užitečné pro velké 32ové aplikace (jako je například Visual Studio), a také šetří fyzickou paměť.

- **Změny knihovny základních tříd**

  K .NET Framework 4,6 bylo přidáno mnoho nových rozhraní API, které umožňuje použití klíčových scénářů. Mezi ně patří tyto změny a dodatky:

  - **\<T>Implementace IReadOnlyCollection**

    Další kolekce implementují <xref:System.Collections.Generic.IReadOnlyCollection%601> například <xref:System.Collections.Generic.Queue%601> a <xref:System.Collections.Generic.Stack%601> .

  - **CultureInfo. CurrentCulture a CultureInfo. CurrentUICulture**

    <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>Vlastnosti a <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> jsou nyní určeny pro čtení i zápis, nikoli jen pro čtení. Pokud <xref:System.Globalization.CultureInfo> k těmto vlastnostem přiřadíte nový objekt, změní se také aktuální jazyková verze vlákna definovaná `Thread.CurrentThread.CurrentCulture` vlastností a aktuální jazyková verze vlákna uživatelského rozhraní definovaná `Thread.CurrentThread.CurrentUICulture` vlastnostmi.

  - **Vylepšení uvolňování paměti (GC)**

    <xref:System.GC>Třída teď obsahuje <xref:System.GC.TryStartNoGCRegion%2A> metody a <xref:System.GC.EndNoGCRegion%2A> , které umožňují zakázat uvolňování paměti během provádění kritické cesty.

    Nové přetížení <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%2CSystem.Boolean%29?displayProperty=nameWithType> metody umožňuje řídit, zda je halda malých objektů i halda pro velké objekty Swept a komprimována nebo Swept pouze.

  - **Typy s povoleným SIMD**

    <xref:System.Numerics>Obor názvů teď obsahuje několik typů s povoleným SIMD, jako <xref:System.Numerics.Matrix3x2> jsou, <xref:System.Numerics.Matrix4x4> ,, <xref:System.Numerics.Plane> <xref:System.Numerics.Quaternion> , <xref:System.Numerics.Vector2> , <xref:System.Numerics.Vector3> a <xref:System.Numerics.Vector4> .

    Vzhledem k tomu, že nový 64 kompilátor JIT zahrnuje také funkce akcelerace hardwarového SIMD, existují obzvláště významná zlepšení výkonu při použití typů SIMD s novým 64 kompilátorem JIT.

  - **Aktualizace kryptografie**

    <xref:System.Security.Cryptography?displayProperty=nameWithType>Rozhraní API se aktualizuje tak, aby podporovalo [rozhraní API kryptografie Windows CNG](/windows/desktop/SecCNG/cng-reference). Předchozí verze .NET Framework se jako základ pro implementaci spoléhaly jenom na [starší verzi rozhraní API kryptografie Windows](/windows/desktop/SecCrypto/cryptography-portal) <xref:System.Security.Cryptography?displayProperty=nameWithType> . Měli jsme požadavky na podporu rozhraní API CNG, protože podporuje [moderní kryptografické algoritmy](/windows/desktop/SecCNG/cng-features#suite-b-support), které jsou důležité pro určité kategorie aplikací.

    .NET Framework 4,6 obsahuje následující nová vylepšení pro podporu kryptografických rozhraní API Windows CNG:

    - Sada rozšiřujících metod pro certifikáty x509 `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` a `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` , která vrací implementaci založenou na CNG spíše než implementaci založenou na rozhraní CAPI, pokud je to možné. (Některé čipové karty atd., stále vyžadují rozhraní CAPI a rozhraní API zařídí záložní verze.)

    - <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType>Třída, která poskytuje implementaci CNG algoritmu RSA.

    - Vylepšení rozhraní RSA API tak, aby běžné akce již nevyžadovaly přetypování. Například šifrování dat pomocí <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> objektu vyžaduje v předchozích verzích .NET Framework kód jako v následujícím příkladu.

      [!code-csharp[WhatsNew.Casting#1](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#1)]
      [!code-vb[WhatsNew.Casting#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#1)]

      Kód, který používá nová rozhraní API kryptografie v .NET Framework 4,6, lze přepsat následujícím způsobem, aby se zabránilo přetypování.

      [!code-csharp[WhatsNew.Casting#2](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#2)]
      [!code-vb[WhatsNew.Casting#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#2)]

  - **Podpora převodu dat a časů do nebo z času v systému UNIX**

    Do struktury byly přidány následující nové metody <xref:System.DateTimeOffset> , které podporují převod hodnot data a času na čas systému UNIX nebo z něj:

    - <xref:System.DateTimeOffset.FromUnixTimeSeconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.FromUnixTimeMilliseconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.ToUnixTimeSeconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.ToUnixTimeMilliseconds%2A?displayProperty=nameWithType>

  - **Přepínače kompatibility**

    <xref:System.AppContext>Třída přidává novou funkci kompatibility, která umožňuje zapisovačům knihoven poskytnout jednotný mechanismus pro odhlášení pro nové funkce pro své uživatele. Zřizuje volně spojený kontrakt mezi komponentami, aby bylo možné sdělit požadavek na výslovný souhlas. Tato možnost je obvykle důležitá, když dojde ke změně existující funkce. Naopak pro nové funkce už existuje implicitní výslovný souhlas.

    S <xref:System.AppContext> , knihovny definují a zveřejňují přepínače kompatibility, zatímco kód, který na nich závisí, může nastavit tyto přepínače tak, aby ovlivnily chování knihovny. Ve výchozím nastavení knihovny poskytují nové funkce a mění je pouze (to znamená, že poskytují předchozí funkce), pokud je přepínač nastaven.

    Aplikace (nebo knihovna) může deklarovat hodnotu přepínače (což je vždy <xref:System.Boolean> hodnota), kterou definuje závislá knihovna. Přepínač je vždy implicitně `false` . Nastavením přepínače `true` ho povolíte. Explicitním nastavením přepínače, aby bylo `false` zajištěno nové chování.

    ```csharp
    AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", true);
    ```

    ```vb
    AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", True)
    ```

    Knihovna musí ověřit, zda příjemce deklaroval hodnotu přepínače a následně na něj musí reagovat.

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

    Je výhodné použít pro přepínače konzistentní formát, protože se jedná o formální kontrakt, který je zpřístupněný knihovnou. Níže jsou uvedené dva zjevné formáty.

    - *Přepínač*. *obor názvů*. *přepínač*

    - *Přepínač*. *Knihovna*. *přepínač*

  - **Změny asynchronního vzoru založeného na úlohách (klepnutím)**

    Pro aplikace, které cílí na .NET Framework 4,6, <xref:System.Threading.Tasks.Task> a objekty dědí jazykovou verzi <xref:System.Threading.Tasks.Task%601> a jazykovou verzi uživatelského rozhraní volajícího vlákna. Chování aplikací, které cílí na předchozí verze .NET Framework nebo které necílí na konkrétní verzi .NET Framework, není ovlivněno. Další informace naleznete v části "jazyková verze a asynchronní operace založené na úlohách" v <xref:System.Globalization.CultureInfo> tématu třídy.

    <xref:System.Threading.AsyncLocal%601?displayProperty=nameWithType>Třída umožňuje znázornit ambientní data, která jsou lokální pro daný tok asynchronního řízení, jako je například `async` metoda. Dá se použít k uchovávání dat napříč vlákny. Můžete také definovat metodu zpětného volání, která je upozorněna vždy, když se změní okolní data buď z důvodu <xref:System.Threading.AsyncLocal%601.Value%2A?displayProperty=nameWithType> explicitního Změna vlastnosti, nebo protože vlákno zaznamenalo kontextový přechod.

    <xref:System.Threading.Tasks.Task.CompletedTask%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task.FromCanceled%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task.FromException%2A?displayProperty=nameWithType> Do asynchronního vzoru založeného na úlohách (klepnutím) byly přidány tři praktické metody,, a, které budou vracet dokončené úkoly v určitém stavu.

    <xref:System.IO.Pipes.NamedPipeClientStream>Třída teď podporuje asynchronní komunikaci s jejím novým <xref:System.IO.Pipes.NamedPipeClientStream.ConnectAsync%2A> . Metoda.

  - **EventSource teď podporuje zápis do protokolu událostí.**

    Nyní můžete použít <xref:System.Diagnostics.Tracing.EventSource> třídu k protokolování administrativních a provozních zpráv do protokolu událostí, a to i na všechny existující relace ETW, které byly vytvořeny v počítači. V minulosti jste pro tuto funkci museli použít balíček NuGet Microsoft. Diagnostics. Tracing. EventSource. Tato funkce je teď integrovaná .NET Framework 4,6.

    Balíček NuGet i .NET Framework 4,6 byly aktualizovány pomocí následujících funkcí:

    - **Dynamické události**

      Povoluje události definované "průběžně" bez vytváření metod událostí.

    - **Bohatá datová část**

      Povoluje jako datovou část speciálně definované třídy a pole a také primitivní typy, které mají být předány.

    - **Sledování aktivit**

      Způsobí, že události spuštění a zastavení mezi nimi budou označovat události s ID, které představuje všechny aktuálně aktivní aktivity.

    Pro podporu těchto funkcí byla přetížená <xref:System.Diagnostics.Tracing.EventSource.Write%2A> Metoda přidána do <xref:System.Diagnostics.Tracing.EventSource> třídy.

- **Windows Presentation Foundation (WPF)**

  - **Vylepšení HDPI**

    Podpora HDPI v subsystému WPF je teď v .NET Framework 4,6 lepší. Byly provedeny změny rozložení při zaokrouhlování, aby se snížily instance oříznutí v ovládacích prvcích s ohraničením. Ve výchozím nastavení je tato funkce povolená, jenom když <xref:System.Runtime.Versioning.TargetFrameworkAttribute> je nastavená na .net 4,6.  Aplikace, které jsou cíleny na starší verze rozhraní, ale jsou spuštěny v .NET Framework 4,6 se mohou přihlásit k novému chování přidáním následujícího řádku do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) části app.config souboru:

    ```xml
    <AppContextSwitchOverrides
    value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false"
    />
    ```

    WPF Windows přecházející z více monitorů s různými nastaveními DPI (nastavení s více DPI) se teď kompletně vykreslují bez černých oblastí. Toto chování můžete odhlásit přidáním následujícího řádku do `<appSettings>` části souboru app.config, abyste zakázali toto nové chování:

    ```xml
    <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    ```

    Do se přidala podpora pro automatické načtení správného kurzoru na základě nastavení DPI <xref:System.Windows.Input.Cursor?displayProperty=nameWithType> .

  - **Dotykové ovládání je lepší**

    Zákaznické zprávy o [připojení](https://connect.microsoft.com/VisualStudio/feedback/details/903760/) tohoto dotykového ovládání vytvářejí nepředvídatelné chování, které se řeší v .NET Framework 4,6. Prahová hodnota dvojitého kliknutí pro aplikace pro Windows Store a aplikace WPF je teď stejná jako u Windows 8.1 a vyšších.

  - **Podpora transparentního podřízeného okna**

    WPF v .NET Framework 4,6 podporuje transparentní podřízená okna v Windows 8.1 a vyšším. To umožňuje vytvořit v oknech nejvyšší úrovně neobdélníkové a průhledné podřízené okna. Tuto funkci můžete povolit nastavením <xref:System.Windows.Interop.HwndSourceParameters.UsesPerPixelTransparency%2A?displayProperty=nameWithType> vlastnosti na `true` .

- **Windows Communication Foundation (WCF)**

  - **Podpora SSL**

    Služba WCF teď podporuje protokol SSL verze TLS 1,1 a TLS 1,2 kromě protokolu SSL 3,0 a TLS 1,0 při použití NetTcp s zabezpečením přenosu a ověřováním klientů. Nyní je možné vybrat, který protokol se má použít, nebo zakázat staré méně zabezpečené protokoly. To lze provést buď nastavením <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A> vlastnosti, nebo přidáním následujícího do konfiguračního souboru.

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

  - **Posílání zpráv pomocí různých připojení HTTP**

    WCF teď umožňuje uživatelům zajistit, aby se určité zprávy odesílaly pomocí různých základních připojení HTTP. Toto lze provést dvěma způsoby:

    - **Použití předpony názvu skupiny připojení**

      Uživatelé můžou zadat řetězec, který bude WCF používat jako předponu pro název skupiny připojení. Dvě zprávy s různými předponami jsou odesílány pomocí různých základních připojení HTTP. Předponu můžete nastavit přidáním páru klíč-hodnota k <xref:System.ServiceModel.Channels.Message.Properties%2A?displayProperty=nameWithType> vlastnosti zprávy. Klíč je "HttpTransportConnectionGroupNamePrefix"; hodnota je požadovaná předpona.

    - **Používání různých továrn kanálů**

      Uživatelé taky můžou povolit funkci, která zajistí, že se zprávy odeslané pomocí kanálů vytvořených různými továrnami kanálů budou používat v různých podkladových připojeních HTTP. Chcete-li povolit tuto funkci, musí uživatelé nastavit `appSetting` následující `true` :

      ```xml
      <appSettings>
          <add key="wcf:httpTransportBinding:useUniqueConnectionPoolPerFactory" value="true" />
      </appSettings>
      ```

- **Programovací model Windows Workflow Foundation (WWF)**

  Nyní můžete zadat počet sekund, po které bude služba pracovního postupu pojmout požadavek na operaci mimo pořadí, pokud před vypršením časového limitu žádosti existuje nevyřízená záložka bez protokolu. Záložka "non-Protocol" je záložka, která nesouvisí s nezpracovanými aktivitami příjmu. Některé aktivity vytvářejí záložky bez protokolu v rámci jejich implementace, takže nemusí být zřejmé, že existuje záložka bez protokolu. Mezi ně patří stav a výběr. Takže pokud máte službu pracovního postupu implementovanou se stavovým počítačem nebo obsahuje aktivitu vyskladnění, pravděpodobně budete mít záložky bez protokolu. Interval zadejte tak, že do části souboru app.config přidáte řádek podobný následujícímu `appSettings` :

  ```xml
  <add key="microsoft:WorkflowServices:FilterResumeTimeoutInSeconds" value="60"/>
  ```

  Výchozí hodnota je 60 sekund. Pokud `value` je hodnota nastavena na 0, žádosti mimo pořadí jsou okamžitě odmítnuty s chybou text, který vypadá takto:

  ```console
  Operation 'Request3|{http://tempuri.org/}IService' on service instance with identifier '2b0667b6-09c8-4093-9d02-f6c67d534292' cannot be performed at this time. Please ensure that the operations are performed in the correct order and that the binding in use provides ordered delivery guarantees.
  ```

  Jedná se o stejnou zprávu, kterou dostanete, pokud je přijata zpráva o operacích mimo pořadí a nejsou k dispozici žádné záložky bez protokolu.

  Pokud hodnota `FilterResumeTimeoutInSeconds` elementu je nenulová, neexistují žádné záložky bez protokolu a časový limit vyprší, operace se nezdařila se zprávou o vypršení časového limitu.

- **Transakce**

  Nyní můžete zahrnout identifikátor distribuované transakce pro transakci, která způsobila výjimku odvozenou od <xref:System.Transactions.TransactionException> vyvolání. Uděláte to tak, že do `appSettings` části souboru app.config přidáte následující klíč:

  ```xml
  <add key="Transactions:IncludeDistributedTransactionIdInExceptionMessage" value="true"/>
  ```

  Výchozí hodnota je `false`.

- **Sítě**

  - **Opakované použití soketu**

    Windows 10 obsahuje nový síťový algoritmus s vysokou škálovatelností, který zajišťuje lepší využívání prostředků počítače tím, že znovu používá místní porty pro odchozí připojení TCP. .NET Framework 4,6 podporuje nový algoritmus a umožňuje aplikacím .NET využít nové chování. V předchozích verzích Windows se jednalo o umělý limit souběžného připojení (obvykle 16 384, výchozí velikost dynamického rozsahu portů), což může omezit škálovatelnost služby tím, že při zatížení způsobuje vyčerpání portů.

    V .NET Framework 4,6 byly přidány dvě rozhraní API, aby bylo možné znovu použít port, což efektivně odstraní limit 64 KB pro souběžná připojení:

    - <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType>Hodnota výčtu.

    - <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType>Vlastnost.

    Ve výchozím nastavení <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> vlastnost je, `false` Pokud `HWRPortReuseOnSocketBind` hodnota `HKLM\SOFTWARE\Microsoft\.NETFramework\v4.0.30319` klíče registru není nastavená na 0x1. Chcete-li povolit používání místních portů u připojení HTTP, nastavte <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> vlastnost na hodnotu `true` . To způsobí, že všechna odchozí připojení soketu TCP z <xref:System.Net.Http.HttpClient> a <xref:System.Net.HttpWebRequest> na používá novou možnost soketu Windows 10, [SO_REUSE_UNICASTPORT](/windows/desktop/WinSock/sol-socket-socket-options), která umožňuje opakované použití místního portu.

    Vývojáři, kteří vytvářejí pouze sokety, mohou určit <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> možnost při volání metody, například <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> tak, aby odchozí sokety opakovaně znovu vyvolaly místní porty během vytváření vazby.

  - **Podpora mezinárodních názvů domén a PunyCode**

    Do třídy se přidala nová vlastnost, <xref:System.Uri.IdnHost%2A> která bude <xref:System.Uri> lépe podporovat názvy mezinárodních domén a Punycode.

- **Změna velikosti v ovládacích prvcích model Windows Forms.**

  Tato funkce byla rozšířena v .NET Framework 4,6, aby zahrnovala <xref:System.Windows.Forms.DomainUpDown> <xref:System.Windows.Forms.NumericUpDown> typy,, a <xref:System.Windows.Forms.DataGridViewComboBoxColumn> <xref:System.Windows.Forms.DataGridViewColumn> <xref:System.Windows.Forms.ToolStripSplitButton> a obdélník určený <xref:System.Drawing.Design.PaintValueEventArgs.Bounds%2A> vlastností použitou při vykreslování <xref:System.Drawing.Design.UITypeEditor> .

  Toto je funkce výslovného souhlasu. Pokud ho chcete povolit, nastavte `EnableWindowsFormsHighDpiAutoResizing` element na `true` v souboru konfigurace aplikace (app.config):

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

- **Podpora kódování znakových stránek**

  .NET Core primárně podporuje kódování Unicode a ve výchozím nastavení poskytuje omezené podpory pro kódování znakových stránek. Můžete přidat podporu pro kódování znakových stránek, která jsou k dispozici v .NET Framework, ale nepodporovaná v .NET Core, registrací kódování znakové stránky pomocí <xref:System.Text.Encoding.RegisterProvider%2A?displayProperty=nameWithType> metody. Další informace naleznete v tématu <xref:System.Text.CodePagesEncodingProvider?displayProperty=nameWithType>.

- **.NET Native**

  Aplikace pro Windows pro Windows 10, které cílí na .NET Core a jsou napsané v jazyce C# nebo Visual Basic můžou využít novou technologii, která kompiluje aplikace do nativního kódu místo IL. Vytváří aplikace s větším počtem časů spuštění a spuštění. Další informace najdete v tématu [kompilace aplikací pomocí .NET Native](../net-native/index.md). Přehled .NET Native, který prověřuje, jak se liší od kompilace JIT i NGEN a co znamená pro váš kód, naleznete v tématu [.NET Native a kompilace](../net-native/net-native-and-compilation.md).

  Vaše aplikace jsou kompilovány do nativního kódu ve výchozím nastavení, když je kompilujete pomocí sady Visual Studio 2015 nebo novější. Další informace najdete v tématu [Začínáme s .NET Native](../net-native/getting-started-with-net-native.md).

  Pro podporu ladění aplikací .NET Native bylo přidáno několik nových rozhraní a výčtů do nespravovaného ladicího rozhraní API. Další informace naleznete v tématu [ladění (nespravované rozhraní API)](../unmanaged-api/debugging/index.md) .

- **Open Source .NET Framework balíčky**

  Balíčky .NET Core, jako jsou neměnné kolekce, [rozhraní API SIMD](https://www.nuget.org/packages/Microsoft.Bcl.Simd)a síťové rozhraní API, jako jsou ty, které se nacházejí v <xref:System.Net.Http> oboru názvů, jsou teď dostupné jako open source balíčky na [GitHubu](https://github.com/). Přístup k kódu naleznete v tématu [.NET na GitHubu](https://github.com/dotnet/runtime). Další informace a o tom, jak přispívat do těchto balíčků, najdete v tématu [.NET Core a open source](../get-started/net-core-and-open-source.md), [Domovská stránka .NET na GitHubu](https://github.com/dotnet/home).

<a name="v452"></a>

## <a name="whats-new-in-net-framework-452"></a>Co je nového v .NET Framework 4.5.2

- **Nová rozhraní API pro aplikace ASP.NET** Nové <xref:System.Web.HttpResponse.AddOnSendingHeaders%2A?displayProperty=nameWithType> metody a <xref:System.Web.HttpResponseBase.AddOnSendingHeaders%2A?displayProperty=nameWithType> umožňují kontrolovat a upravovat hlavičky odpovědí a stavový kód, protože odpověď se vyprazdňuje do klientské aplikace. Zvažte použití těchto metod namísto <xref:System.Web.HttpApplication.PreSendRequestHeaders> <xref:System.Web.HttpApplication.PreSendRequestContent> událostí a. jsou efektivnější a spolehlivé.

  <xref:System.Web.Hosting.HostingEnvironment.QueueBackgroundWorkItem%2A?displayProperty=nameWithType>Metoda umožňuje naplánovat malé pracovní položky na pozadí. ASP.NET sleduje tyto položky a brání službě IIS v náhlém ukončení pracovního procesu, dokud nebudou dokončeny všechny pracovní položky na pozadí. Tuto metodu nejde volat mimo doménu spravované aplikace ASP.NET.

  Nové <xref:System.Web.HttpResponse.HeadersWritten?displayProperty=nameWithType> vlastnosti a <xref:System.Web.HttpResponseBase.HeadersWritten?displayProperty=nameWithType> vrátí logické hodnoty, které určují, zda byly napsány hlavičky odpovědi. Tyto vlastnosti můžete použít k tomu, abyste se ujistili, že volání rozhraní API <xref:System.Web.HttpResponse.StatusCode%2A?displayProperty=nameWithType> (která vyvolávají výjimky při zápisu hlaviček) budou úspěšná.

- **Změna velikosti v ovládacích prvcích model Windows Forms.** Tato funkce se rozšířila. Nyní můžete použít nastavení systému DPI pro změnu velikosti součástí následujících dalších ovládacích prvků (například šipky rozevíracího seznamu v polích se seznamem):

  - <xref:System.Windows.Forms.ComboBox>
  - <xref:System.Windows.Forms.ToolStripComboBox>
  - <xref:System.Windows.Forms.ToolStripMenuItem>
  - <xref:System.Windows.Forms.Cursor>
  - <xref:System.Windows.Forms.DataGridView>
  - <xref:System.Windows.Forms.DataGridViewComboBoxColumn>

  Toto je funkce výslovného souhlasu. Pokud ho chcete povolit, nastavte `EnableWindowsFormsHighDpiAutoResizing` element na `true` v souboru konfigurace aplikace (app.config):

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

- **Nová funkce pracovního postupu.** Správce prostředků, který používá <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> metodu (a proto implementuje <xref:System.Transactions.IPromotableSinglePhaseNotification> rozhraní), může použít novou <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> metodu k vyžádání následujícího:

  - Povýšit transakci na transakci Microsoft DTC (Distributed Transaction Coordinator) (MSDTC).

  - Nahraďte <xref:System.Transactions.IPromotableSinglePhaseNotification> <xref:System.Transactions.ISinglePhaseNotification> , což je trvalé zařazení, které podporuje jednotlivé fáze potvrzení.

  To se dá udělat v rámci stejné domény aplikace a nevyžaduje žádný dodatečný nespravovaný kód pro interakci se službou MSDTC, aby bylo možné provést povýšení. Nová metoda může být volána pouze v případě, že existuje nedokončené volání <xref:System.Transactions?displayProperty=nameWithType> do <xref:System.Transactions.IPromotableSinglePhaseNotification> `Promote` metody, která je implementována prostřednictvím zařazení do propagačního objektu.

- **Vylepšení profilace.** Následující nová nespravovaná rozhraní API pro profilaci poskytují robustnější profilaci:

  - [Struktura COR_PRF_ASSEMBLY_REFERENCE_INFO](../unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)
  - [Výčet COR_PRF_HIGH_MONITOR](../unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)
  - [GetAssemblyReferences – metoda](../unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
  - [GetEventMask2 – metoda](../unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
  - [SetEventMask2 – metoda](../unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
  - [AddAssemblyReference – metoda](../unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)

  Předchozí `ICorProfiler` implementace podporovaly opožděné načítání závislých sestavení. Nové rozhraní API pro profilování vyžadují závislá sestavení, která jsou vložená profilerem tak, aby se spustitelný hned, místo aby se načetla po úplné inicializaci aplikace. Tato změna neovlivní uživatele existujících `ICorProfiler` rozhraní API.

- **Vylepšení ladění.** Následující nová nespravovaná ladicí rozhraní API poskytují lepší integraci s profilerem. Teď můžete přistupovat k metadatům vloženým profilerem a také k místním proměnným a kódu vytvořeným požadavky kompilátoru ReJIT při ladění výpisu.

  - [SetWriteableMetadataUpdateMode – metoda](../unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)
  - [EnumerateLocalVariablesEx – metoda](../unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)
  - [GetLocalVariableEx – metoda](../unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)
  - [GetCodeEx – metoda](../unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)
  - [GetActiveReJitRequestILCode – metoda](../unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)
  - [GetInstrumentedILMap – metoda](../unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)

- **Změny trasování událostí.** .NET Framework 4.5.2 umožňuje trasování aktivit založené na trasování událostí pro Windows (ETW) pro větší plochu. To umožňuje prodejcům pokročilého řízení spotřeby (APM) poskytovat odlehčené nástroje, které přesně sledují náklady na jednotlivé požadavky a aktivity, které procházejí vlákny.  Tyto události jsou vyvolány pouze v případě, že je povolí řadič ETW. Proto změny neovlivní dříve psaný kód ETW nebo kód, který běží se zakázanou ETW.

- **Zvýšení úrovně transakce a její převedení na trvalý zařazení**

  <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType>je nové rozhraní API přidané do .NET Framework 4.5.2 a 4,6:

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

  Metodu lze použít pro zařazení, které bylo dříve vytvořeno <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> v reakci na <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> metodu. Žádá `System.Transactions` o povýšení transakce na transakci MSDTC a na "převést" zařazení do trvalého zařazení. Po úspěšném dokončení této metody <xref:System.Transactions.IPromotableSinglePhaseNotification> již nebude odkazováno na rozhraní `System.Transactions` a veškerá budoucí oznámení budou doručena do poskytnutého <xref:System.Transactions.ISinglePhaseNotification> rozhraní. Příslušné zařazení musí působit jako trvalé zařazení, které podporuje protokolování a obnovení transakcí. Podrobnosti najdete <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType> v tématu. Zařazení navíc musí podporovat <xref:System.Transactions.ISinglePhaseNotification> .  Tuto metodu lze volat *pouze* během zpracovávání <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> volání. V takovém případě <xref:System.Transactions.TransactionException> je vyvolána výjimka.

<a name="v451"></a>

## <a name="whats-new-in-net-framework-451"></a>Co je nového ve .NET Framework 4.5.1

**Aktualizace z dubna 2014**:

- [Visual Studio 2013 aktualizace 2](https://go.microsoft.com/fwlink/p/?LinkId=393658) obsahuje aktualizace šablon přenosných knihoven tříd pro podporu těchto scénářů:

  - Rozhraní prostředí Windows Runtime API můžete použít v přenosných knihovnách, které cílí na Windows 8.1, Windows Phone 8,1 a Windows Phone Silverlight 8,1.

  - Když cílíte Windows 8.1 nebo Windows Phone 8,1, můžete do přenosných knihoven zahrnout XAML (typy Windows. UI. XAML). Podporovány jsou následující šablony XAML: prázdná stránka, slovník prostředků, ovládací prvek s šablonou a uživatelský ovládací prvek.

  - Můžete vytvořit přenosnou součást prostředí Windows Runtime (soubor. winmd) pro použití v aplikacích pro Store, které cílí na Windows 8.1 a Windows Phone 8,1.

  - Můžete změnit cíl knihovny tříd Windows Store nebo Windows Phone Store, jako je Přenosná knihovna tříd.

  Další informace o těchto změnách naleznete v tématu [Přenosná knihovna tříd](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).

- Sada .NET Framework obsahu teď obsahuje dokumentaci pro .NET Native, což je předkompilace technologie pro sestavování a nasazování aplikací pro Windows. .NET Native zkompiluje vaše aplikace přímo do nativního kódu, spíše než do mezilehlého jazyka (IL), pro lepší výkon. Podrobnosti najdete v tématu [kompilace aplikací pomocí .NET Native](../net-native/index.md).

- [Zdroj odkazů .NET Framework](https://referencesource.microsoft.com/) poskytuje nové prostředí pro procházení a vylepšené funkce. Nyní můžete procházet zdrojový kód .NET Framework online, [stahovat reference](https://referencesource.microsoft.com/download.html) pro zobrazení v režimu offline a procházet zdroje (včetně oprav a aktualizací) během ladění. Další informace najdete v blogu o [novém hledání zdroje odkazů .NET](https://devblogs.microsoft.com/dotnet/a-new-look-for-net-reference-source/).

Mezi nové funkce a vylepšení základních tříd v .NET Framework 4.5.1 patří:

- Automatické přesměrování vazby pro sestavení. Počínaje Visual Studio 2013 se při kompilování aplikace, která cílí na .NET Framework 4.5.1, dají přesměrování vazby přidat do konfiguračního souboru aplikace, pokud vaše aplikace nebo její součásti odkazují na více verzí stejného sestavení. Tuto funkci můžete také povolit pro projekty, které cílí na starší verze .NET Framework. Další informace najdete v tématu [Postup: povolení a zákaz automatického přesměrování vazby](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md).

- Možnost shromažďovat diagnostické informace, které vývojářům pomůžou zlepšit výkon serverových a cloudových aplikací. Další informace naleznete v tématu <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityId%2A> metody a <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityIdCore%2A> <xref:System.Diagnostics.Tracing.EventSource> třídy.

- Schopnost explicitně komprimovat haldu velkých objektů (LOH) během uvolňování paměti. Další informace najdete v tématu <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> vlastnost.

- Další vylepšení výkonu, jako je například pozastavení aplikace ASP.NET, vícejazykové vylepšení JIT a rychlejší spuštění aplikace po aktualizaci .NET Framework. Podrobnosti najdete v příspěvku na blogu [.NET Framework 4.5.1](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/) a v blogovém příspěvku o [pozastavení aplikace ASP.NET](https://devblogs.microsoft.com/dotnet/asp-net-app-suspend-responsive-shared-net-web-hosting/) .

Mezi vylepšení model Windows Forms patří:

- Změna velikosti v ovládacích prvcích model Windows Forms. Pomocí nastavení rozlišení DPI systému můžete změnit velikost součástí ovládacích prvků (například ikony, které se zobrazí v mřížce vlastností), tím, že se přiřadíte k položce v konfiguračním souboru aplikace (app.config) pro vaši aplikaci. Tato funkce je aktuálně podporována v následujících ovládacích prvcích model Windows Forms:

  - <xref:System.Windows.Forms.PropertyGrid>
  - <xref:System.Windows.Forms.TreeView>
  - Některé aspekty <xref:System.Windows.Forms.DataGridView> (viz [nové funkce v 4.5.2](#v452) pro další podporované ovládací prvky)

  Chcete-li povolit tuto funkci, přidejte nový \<appSettings> prvek do konfiguračního souboru (app.config) a nastavte `EnableWindowsFormsHighDpiAutoResizing` element na `true` :

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

Vylepšení při ladění .NET Frameworkch aplikací v Visual Studio 2013 zahrnují:

- Návratové hodnoty v ladicím programu sady Visual Studio. Při ladění spravované aplikace v Visual Studio 2013 zobrazí okno Automatické hodnoty návratové typy a hodnoty pro metody. Tyto informace jsou k dispozici pro stolní počítače, Windows Store a aplikace Windows Phone. Další informace naleznete v tématu [Kontrola vrácených hodnot volání metody](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/dn323257(v=vs.120)).

- Upravit a pokračovat pro 64 aplikace Visual Studio 2013 podporuje funkci upravit a pokračovat pro 64 spravované aplikace pro stolní počítače, Windows Store a Windows Phone. Stávající omezení zůstávají v platnosti pro 32 i pro 64-bitové aplikace (viz poslední část článku [podporované změny kódu (C#)](/visualstudio/debugger/supported-code-changes-csharp) ).

- Asynchronní ladění. Aby bylo snazší ladit asynchronní aplikace v Visual Studio 2013, zásobník volání skrývá kód infrastruktury poskytnutý kompilátory pro podporu asynchronního programování a také řetězení v logických nadřazených snímcích, takže můžete pořídit provádění logického programu podrobněji. Okno úkoly nahrazuje okno paralelní úkoly a zobrazuje úkoly, které se vztahují k určité zarážce, a také zobrazí všechny další úkoly, které jsou v aplikaci aktuálně aktivní nebo naplánované. O této funkci si můžete přečíst v části "asynchronní ladění" v [oznámení .NET Framework 4.5.1](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/).

- Lepší podpora výjimek pro součásti prostředí Windows Runtime. V Windows 8.1 výjimky, které vznikají v aplikacích pro Windows Store, uchovávají informace o chybě, která způsobila výjimku, i přes hranice jazyka. O této funkci si můžete přečíst v části vývoj aplikací pro Windows Store v [oznámení .NET Framework 4.5.1](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/).

Počínaje Visual Studio 2013 můžete použít [Nástroj pro optimalizaci spravovaného profilu (Mpgo.exe)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md) k optimalizaci aplikací pro Windows 8. x Store a aplikací klasické pracovní plochy.

Nové funkce v ASP.NET 4.5.1 najdete v tématu [ASP.NET and Web Tools for Visual Studio 2013 poznámky k verzi](/aspnet/visual-studio/overview/2013/release-notes).

<a name="v45"></a>

## <a name="whats-new-in-net-framework-45"></a>Co je nového v .NET Framework 4,5

### <a name="base-classes"></a>Základní třídy

- Schopnost snížit restart systému tím, že během nasazení detekuje a zavírá aplikace .NET Framework 4. Viz [snížení počtu restartování systému během instalace .NET Framework 4,5](../deployment/reducing-system-restarts.md).

- Podpora pro pole, která jsou větší než 2 gigabajty (GB) na 64-bitových platformách. Tato funkce se dá povolit v konfiguračním souboru aplikace. Podívejte se na [ \<gcAllowVeryLargeObjects> element](../configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md), který také obsahuje další omezení velikosti objektu a velikosti pole.

- Lepší výkon při uvolňování paměti na pozadí pro servery. Pokud používáte systém uvolňování paměti serveru v .NET Framework 4,5, automatické uvolňování paměti na pozadí je povoleno. V tématu [základní informace o uvolňování paměti](../../standard/garbage-collection/fundamentals.md) najdete v části uvolňování paměti serveru na pozadí.

- Kompilace JIT (just-in-time), která je volitelně dostupná pro procesory s více jádry ke zlepšení výkonu aplikace. Viz třída <xref:System.Runtime.ProfileOptimization>.

- Možnost omezit dobu, po kterou se modul regulárních výrazů pokusí přeložit regulární výraz předtím, než vyprší jeho časový limit. Podívejte se na <xref:System.Text.RegularExpressions.Regex.MatchTimeout%2A?displayProperty=nameWithType> vlastnost.

- Možnost definovat výchozí jazykovou verzi pro doménu aplikace. Podívejte se na <xref:System.Globalization.CultureInfo> třídu.

- Podpora konzoly pro kódování Unicode (UTF-16). Podívejte se na <xref:System.Console> třídu.

- Podpora správy verzí pro kulturní řazení řetězců a porovnávání dat. Podívejte se na <xref:System.Globalization.SortVersion> třídu.

- Lepší výkon při načítání prostředků. Viz [balení a nasazení prostředků](../resources/packaging-and-deploying-resources-in-desktop-apps.md).

- Vylepšení komprese zip ke zmenšení velikosti komprimovaného souboru. Viz <xref:System.IO.Compression?displayProperty=nameWithType> obor názvů.

- Možnost přizpůsobit kontext reflexe pro přepsání výchozího chování reflexe prostřednictvím <xref:System.Reflection.Context.CustomReflectionContext> třídy.

- Podpora verze 2008 mezinárodních názvů domén v aplikacích (IDNA) standard, pokud <xref:System.Globalization.IdnMapping?displayProperty=nameWithType> je třída použita ve Windows 8.

- Delegování porovnání řetězců k operačnímu systému, které implementuje kódování Unicode 6,0, pokud je .NET Framework použito v systému Windows 8. Při spuštění na jiných platformách .NET Framework zahrnuje vlastní data porovnání řetězců, která implementují Unicode 5. x. Podívejte se na <xref:System.String> třídu a oddíl poznámky <xref:System.Globalization.SortVersion> třídy.

- Možnost vypočítat kódy hash pro řetězce na základě domény aplikace. Viz [ \<UseRandomizedStringHashAlgorithm> element](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).

- Podpora reflexe typu je rozdělena mezi <xref:System.Type> <xref:System.Reflection.TypeInfo> třídy a. Podívejte [se na reflexi v .NET Framework pro aplikace pro Windows Store](../reflection-and-codedom/reflection-for-windows-store-apps.md).

### <a name="managed-extensibility-framework-mef"></a>Managed Extensibility Framework (MEF)

V .NET Framework 4,5 obsahuje Managed Extensibility Framework (MEF) tyto nové funkce:

- Podpora pro obecné typy.

- Programovací model založený na konvencích, který umožňuje vytvářet části na základě konvencí pojmenování, nikoli atributů.

- Více oborů.

- Podmnožina MEF, kterou můžete použít při vytváření aplikací pro Windows 8. x Store. Tato podmnožina je k dispozici jako [balíček ke stažení](https://www.nuget.org/packages/Microsoft.Composition) z galerie NuGet. Pokud chcete balíček nainstalovat, otevřete projekt v aplikaci Visual Studio, v nabídce **projekt** vyberte **Spravovat balíčky NuGet** a vyhledejte `Microsoft.Composition` balíček online.

Další informace naleznete v tématu [Managed Extensibility Framework (MEF)](../mef/index.md).

### <a name="asynchronous-file-operations"></a>Asynchronní operace se soubory

V .NET Framework 4,5 byly do jazyků C# a Visual Basic přidány nové asynchronní funkce. Tyto funkce přidávají model založený na úlohách pro provádění asynchronních operací. Chcete-li použít tento nový model, použijte asynchronní metody v I/O třídách. Viz [asynchronní vstupně-výstupní operace se soubory](../../standard/io/asynchronous-file-i-o.md).

<a name="tools"></a>

### <a name="tools"></a>Nástroje

V .NET Framework 4,5 vám generátor souborů prostředků (Resgen.exe) umožňuje vytvořit soubor. resw pro použití v aplikacích Windows 8. x Store ze souboru. Resources vloženého do sestavení .NET Framework. Další informace najdete v tématu [Resgen.exe (generátor zdrojového souboru)](../tools/resgen-exe-resource-file-generator.md).

Spravovaná optimalizace na základě profilu (Mpgo.exe) umožňuje zlepšit dobu spuštění aplikace, využití paměti (velikost pracovní sady) a propustnost optimalizací sestavení nativních imagí. Nástroj příkazového řádku generuje data profilu pro sestavení aplikace nativní bitové kopie. Viz [Mpgo.exe (Nástroj pro optimalizaci spravovaného profilu)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md). Počínaje Visual Studio 2013 můžete použít Mpgo.exe k optimalizaci aplikací pro Store Windows 8. x a desktopových aplikací.

<a name="parallel"></a>

### <a name="parallel-computing"></a>Paralelní výpočetní prostředí

.NET Framework 4,5 obsahuje několik nových funkcí a vylepšení paralelního zpracování. Mezi ně patří Vylepšený výkon, zvýšené řízení, vylepšená podpora pro asynchronní programování, nová knihovna toku dat a vylepšená podpora pro paralelní ladění a analýzu výkonu. Informace o [tom, co je nového pro paralelismus v .net 4,5](https://devblogs.microsoft.com/pfxteam/whats-new-for-parallelism-in-net-4-5/) , najdete v blogu věnovaném paralelnímu programování pomocí .NET.

<a name="web"></a>

### <a name="web"></a>Web

ASP.NET 4,5 a 4.5.1 přidávají vazbu modelu pro webové formuláře, podporu WebSocket, asynchronní obslužné rutiny, vylepšení výkonu a mnoho dalších funkcí. Další informace naleznete v následujících zdrojích:

- [ASP.NET 4,5 a Visual Studio 2012](https://docs.microsoft.com/previous-versions/aspnet/hh420390(v=vs.110))

- [ASP.NET a webové nástroje pro Visual Studio 2013 – poznámky k verzi](/aspnet/visual-studio/overview/2013/release-notes)

### <a name="networking"></a>Sítě<a name="networking"></a>

.NET Framework 4,5 poskytuje nové programovací rozhraní pro aplikace HTTP. Další informace najdete v tématu nové <xref:System.Net.Http?displayProperty=nameWithType> <xref:System.Net.Http.Headers?displayProperty=nameWithType> obory názvů a.

Podpora je také k dispozici pro nové programovací rozhraní pro příjem a interakci s připojením protokolu WebSocket pomocí existující <xref:System.Net.HttpListener> a související třídy. Další informace naleznete v tématu nový <xref:System.Net.WebSockets> obor názvů a <xref:System.Net.HttpListener> Třída.

Kromě toho .NET Framework 4,5 zahrnuje následující vylepšení sítě:

- Podpora identifikátoru URI kompatibilního se specifikací RFC. Další informace naleznete v tématu <xref:System.Uri> a související třídy.

- Podpora pro analýzu mezinárodních názvů domén (IDN). Další informace naleznete v tématu <xref:System.Uri> a související třídy.

- Podpora mezinárodní adresy e-mailové adresy (EAI). Další informace najdete v tématu <xref:System.Net.Mail> obor názvů.

- Vylepšená podpora protokolu IPv6. Další informace najdete v tématu <xref:System.Net.NetworkInformation> obor názvů.

- Podpora soketu s duálním režimem. Další informace naleznete v tématu <xref:System.Net.Sockets.Socket> třídy a <xref:System.Net.Sockets.TcpListener> .

<a name="client"></a>

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

V .NET Framework 4,5 Windows Presentation Foundation (WPF) obsahuje změny a vylepšení v následujících oblastech:

- Nový <xref:System.Windows.Controls.Ribbon.Ribbon> ovládací prvek, který umožňuje implementovat uživatelské rozhraní pásu karet, které je hostitelem panelu nástrojů pro rychlý přístup, nabídky aplikace a karet.

- Nové <xref:System.ComponentModel.INotifyDataErrorInfo> rozhraní, které podporuje synchronní a asynchronní ověřování dat.

- Nové funkce pro <xref:System.Windows.Controls.VirtualizingPanel> třídy a <xref:System.Windows.Threading.Dispatcher> .

- Vylepšený výkon při zobrazování rozsáhlých sad seskupených dat a přístup k kolekcím na vláknech, která nejsou v uživatelském rozhraní.

- Vázání dat na statické vlastnosti, datové vazby na vlastní typy, které implementují <xref:System.Reflection.ICustomTypeProvider> rozhraní a načítání informací o vazbách dat z výrazu vazby.

- Změna umístění dat při změně hodnot (živé tvarování).

- Možnost kontrolovat, zda je kontext dat pro kontejner položek odpojen.

- Možnost nastavit dobu, která má uplynout mezi změnami vlastností a aktualizacemi zdrojů dat.

- Vylepšená podpora pro implementaci slabých vzorů událostí. Události nyní také mohou přijímat rozšíření značek.

<a name="windows_communication_foundation"></a>

### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)

V .NET Framework 4,5 byly přidány následující funkce, které zjednodušují psaní a údržbu aplikací Windows Communication Foundation (WCF):

- Zjednodušení generovaných konfiguračních souborů.

- Podpora vývoje pro první kontrakt.

- Možnost snazší konfigurace režimu kompatibility ASP.NET.

- Změny ve výchozích hodnotách vlastností přenosu snižují pravděpodobnost, že je budete muset nastavit.

- Aktualizuje <xref:System.Xml.XmlDictionaryReaderQuotas> třídu, aby se snížila pravděpodobnost, že bude nutné ručně nakonfigurovat kvóty pro čtečky slovníku XML.

- Ověření konfiguračních souborů WCF nástrojem Visual Studio v rámci procesu sestavení, aby bylo možné zjistit chyby konfigurace před spuštěním aplikace.

- Nová podpora asynchronního streamování.

- Nové mapování protokolu HTTPS, které usnadňuje vystavení koncového bodu přes HTTPS pomocí Internetová informační služba (IIS).

- Možnost generovat metadata v jednom dokumentu WSDL připojením `?singleWSDL` k adrese URL služby.

- Podpora WebSockets podporuje true obousměrnou komunikaci přes porty 80 a 443 s charakteristikami výkonu podobným přenosu protokolu TCP.

- Podpora konfigurace služeb v kódu.

- Popisy editoru XML.

- <xref:System.ServiceModel.ChannelFactory>Podpora ukládání do mezipaměti.

- Podpora komprese binárního kodéru

- Podpora pro přenos UDP, který vývojářům umožňuje psát služby, které používají zprávy "oheň a zapomenout". Klient pošle zprávu službě a neočekává odpověď ze služby.

- Možnost podporovat více režimů ověřování na jednom koncovém bodu WCF při použití přenosu protokolu HTTP a zabezpečení přenosu.

- Podpora služeb WCF, které používají mezinárodní názvy domén (IDN).

Další informace najdete v tématu [co je nového v Windows Communication Foundation](../wcf/whats-new.md).

<a name="windows_workflow_foundation"></a>

### <a name="windows-workflow-foundation-wf"></a>Windows Workflow Foundation (WF)

V .NET Framework 4,5 byly do programovací model Windows Workflow Foundation (WF) přidány některé nové funkce, včetně těchto:

- Pracovní postupy stavového stroje, které byly poprvé představeny jako součást .NET Framework 4.0.1 ([.NET Framework 4 Platform Update 1](https://docs.microsoft.com/archive/blogs/endpoint/microsoft-net-framework-4-platform-update-1)). Tato aktualizace obsahuje několik nových tříd a aktivit, které vývojářům umožnili vytvářet pracovní postupy stavového počítače. Tyto třídy a aktivity byly aktualizovány, aby .NET Framework 4,5 zahrnovaly:

  - Možnost nastavovat zarážky na stavech.

  - Možnost Kopírovat a vkládat přechody v Návrháři postupu.

  - Podpora návrháře pro vytvoření přechodu na sdílené triggery

  - Aktivity pro vytváření pracovních postupů stavového počítače, včetně: <xref:System.Activities.Statements.StateMachine> , <xref:System.Activities.Statements.State> a <xref:System.Activities.Statements.Transition> .

- Rozšířené funkce Návrhář postupu provádění, například následující:

  - Rozšířené možnosti hledání pracovních postupů v aplikaci Visual Studio, včetně **rychlého hledání** a **hledání v souborech**.

  - Schopnost automaticky vytvořit aktivitu sekvence, když se do aktivity kontejneru přidá druhá podřízená aktivita, a zahrnout obě aktivity do aktivity sekvence.

  - Podpora posouvání, která umožňuje změnit viditelnou část pracovního postupu bez použití posuvníků.

  - Nové zobrazení **Osnova dokumentu** , které zobrazuje součásti pracovního postupu v zobrazení osnovy ve stylu stromu a umožňuje v zobrazení **Osnova dokumentu** vybrat komponentu.

  - Možnost přidávat poznámky k aktivitám.

  - Možnost definovat a spotřebovat delegáty aktivit pomocí návrháře pracovních postupů.

  - Automatické připojení a automatické vložení pro aktivity a přechody v pracovních postupech stavového stroje a vývojového diagramu.

- Úložiště informací o stavu zobrazení pracovního postupu v jednom prvku v souboru XAML, takže můžete snadno vyhledat a upravit informace o stavu zobrazení.

- Aktivita kontejneru oboru NoPersistScope, která zabraňuje zachování podřízených aktivit.

- Podpora pro výrazy jazyka C#:

  - Projekty pracovního postupu, které používají Visual Basic, budou používat výrazy Visual Basic a projekty pracovního postupu C# budou používat výrazy jazyka C#.

  - Projekty pracovního postupu c#, které byly vytvořeny v aplikaci Visual Studio 2010 a které mají Visual Basic výrazy jsou kompatibilní s projekty pracovního postupu C#, které používají výrazy jazyka C#.

- Vylepšení správy verzí:

  - Nová <xref:System.Activities.WorkflowIdentity> třída, která poskytuje mapování mezi trvalou instancí pracovního postupu a její definicí pracovního postupu.

  - Souběžné spouštění více verzí pracovních postupů ve stejném hostiteli, včetně <xref:System.ServiceModel.Activities.WorkflowServiceHost> .

  - V případě dynamické aktualizace je možné změnit definici trvalé instance pracovního postupu.

- Vývoj služby pracovního postupu prvního kontraktu, který poskytuje podporu pro automatické generování aktivit, které se shodují s existující smlouvou služby.

Další informace najdete v tématu [co je nového v programovací model Windows Workflow Foundation](../windows-workflow-foundation/whats-new-in-wf-in-dotnet.md).

<a name="tailored"></a>

### <a name="net-for-windows-8x-store-apps"></a>Aplikace .NET pro Windows 8.x Store

Aplikace pro Store ve Windows 8. x jsou navržené pro konkrétní faktory a využívají sílu operačního systému Windows. K dispozici je podmnožina .NET Framework 4,5 nebo 4.5.1 pro sestavování aplikací Windows 8. x Store pro Windows pomocí jazyka C# nebo Visual Basic. Tato podmnožina se nazývá .NET pro aplikace Windows 8. x Store a je popsána v [přehledu](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)).

### <a name="portable-class-libraries"></a>Přenositelné knihovny tříd<a name="portable"></a>

Přenosná knihovna tříd projektu v aplikaci Visual Studio 2012 (a novějších verzích) umožňuje psát a sestavovat spravovaná sestavení, která fungují na více .NET Framework platformách. Pomocí přenositelného projektu knihovny tříd zvolíte platformy (například Windows Phone a .NET pro aplikace pro Windows 8. x Store) k cíli. Dostupné typy a členy v projektu jsou automaticky omezeny na společné typy a členy napříč těmito platformami. Další informace naleznete v tématu [Přenosná knihovna tříd](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).

## <a name="see-also"></a>Viz také

- [Rozhraní .NET Framework a nesvázaná vydání](../get-started/the-net-framework-and-out-of-band-releases.md)
- [Co je nového v přístupnosti v .NET Framework](whats-new-in-accessibility.md)
- [Co je nového v aplikaci Visual Studio 2017](/visualstudio/ide/whats-new-visual-studio-2017)
- [Novinky v sadě Visual Studio 2019](/visualstudio/ide/whats-new-visual-studio-2019)
- [ASP.NET](/aspnet)
- [Co je nového v jazyce C++ v aplikaci Visual Studio](/cpp/what-s-new-for-visual-cpp-in-visual-studio)
