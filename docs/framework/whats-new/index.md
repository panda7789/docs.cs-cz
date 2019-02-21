---
title: Co je nového v rozhraní .NET Framework
ms.custom: updateeachrelease
ms.date: 04/10/2018
dev_langs:
  - csharp
  - vb
helpviewer_keywords:
  - 'what''s new [.NET Framework]'
ms.assetid: 1d971dd7-10fc-4692-8dac-30ca308fc0fa
author: rpetrusha
ms.author: ronpet
---
# Co je nového v rozhraní .NET Framework <a name="introduction"></a>

Tento článek shrnuje hlavní nové funkce a vylepšení v následujících verzích rozhraní .NET Framework:

- [.NET Framework 4.7.2](#v472)
- [.NET Framework 4.7.1](#v471)
- [.NET Framework 4.7](#v47)
- [.NET Framework 4.6.2](#v462)
- [.NET Framework 4.6.1](#v461)
- [.NET 2015 a .NET Framework 4.6](#v46)
- [.NET Framework 4.5.2](#v452)
- [.NET Framework 4.5.1](#v451)
- [.NET Framework 4.5](#v45)

Tento článek neposkytuje úplné informace o každé nové funkce a může se změnit. Obecné informace o rozhraní .NET Framework najdete v tématu [Začínáme](../../../docs/framework/get-started/index.md). Podporované platformy naleznete v tématu [požadavky na systém](~/docs/framework/get-started/system-requirements.md). Odkazy ke stažení a pokyny k instalaci najdete v tématu [Průvodce instalací](../../../docs/framework/install/guide-for-developers.md).

> [!NOTE]
> Tým rozhraní .NET Framework verze také funkce mimo pásmo s NuGet se rozšiřuje podpora platformy a pro zavedení nových funkcí, jako jsou neměnné kolekce a typy vektorů s podporou SIMD. Další informace najdete v tématu [další knihovny tříd a rozhraní API](../additional-apis/index.md) a [The .NET Framework a vydání Out-of-Band](~/docs/framework/get-started/the-net-framework-and-out-of-band-releases.md). Najdete v článku [úplný seznam balíčků NuGet](https://blogs.msdn.microsoft.com/dotnet/p/nugetpackages/) pro rozhraní .NET Framework, nebo se přihlásit k odběru [našeho kanálu](https://nuget.org/api/v2/curated-feeds/dotnetframework/Packages/).

<a name="v472" />

## <a name="introducing-the-net-framework-472"></a>Úvod do rozhraní .NET Framework 4.7.2

Rozhraní .NET Framework 4.7.2 staví na předchozích verzích rozhraní .NET Framework 4.x přidáním nové opravy mnoha a několik nových funkcí přitom velmi stabilní produkt.

### <a name="downloading-and-installing-the-net-framework-472"></a>Stažení a instalace rozhraní .NET Framework 4.7.2

Rozhraní .NET Framework 4.7.2 si můžete stáhnout z následujícího umístění:

- [Rozhraní .NET framework 4.7.2 Webová instalační služba](https://go.microsoft.com/fwlink/?LinkId=863262)

- [Offline instalační program rozhraní .NET Framework 4.7.2](https://go.microsoft.com/fwlink/?LinkId=863265)

Rozhraní .NET Framework 4.7.2 lze nainstalovat na Windows 10, Windows 8.1, Windows 7 SP1 a odpovídající serverových platforem od Windows serveru 2008 R2 SP1. Rozhraní .NET Framework 4.7.2 můžete nainstalovat pomocí instalačního programu webové nebo offline instalační program. Doporučený postup pro většinu uživatelů je použít webovou Instalační službu.

Můžete cílit rozhraní .NET Framework 4.7.2 v sadě Visual Studio 2012 nebo novější pomocí instalace [rozhraní .NET Framework 4.7.2 Developer Pack](https://go.microsoft.com/fwlink/?LinkId=874338).

### <a name="whats-new-in-the-net-framework-472"></a>Co je nového v rozhraní .NET Framework 4.7.2

Rozhraní .NET Framework 4.7.2 obsahuje nové funkce v následujících oblastech:

- [Jádro](#core-472)
- [ASP.NET](#asp-net472)
- [Sítě](#net472)
- [SQL](#sql472)
- [WPF](#wpf472)
- [ClickOnce](#clickonce)

Pokračování fokus v rozhraní .NET Framework 4.7.2 je vylepšené přístupnosti, které umožňuje aplikaci poskytovat vhodné prostředí pro uživatele technologie pro usnadnění. Informace o vylepšení přístupnosti v rozhraní .NET Framework 4.7.2 najdete v tématu [co je nového v usnadnění přístupu v rozhraní .NET Framework](whats-new-in-accessibility.md).

<a name="core-472" />

#### <a name="core"></a>Jádro

Rozhraní .NET Framework 4.7.2 funkce velké množství vylepšení kryptografických, lepší podporu pro dekompresi archivy ZIP a další kolekci rozhraní API.

**Nová přetížení RSA. Vytvoření a DSA. Vytvoření**

<xref:System.Security.Cryptography.DSA.Create(System.Security.Cryptography.DSAParameters)?displayProperty=nameWithType> a <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> metody umožňují určit parametry klíče při vytváření nové instance <xref:System.Security.Cryptography.DSA> nebo <xref:System.Security.Cryptography.RSA> klíč. Umožňují vám nahraďte kód podobný tomuto:

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
s kódem takto:
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

<xref:System.Security.Cryptography.DSA.Create(System.Int32)?displayProperty=nameWithType> a <xref:System.Security.Cryptography.RSA.Create(System.Int32)?displayProperty=nameWithType> metody vám umožňuje vygenerovat nové <xref:System.Security.Cryptography.DSA> nebo <xref:System.Security.Cryptography.RSA> klíče s konkrétní velikostí klíče. Příklad:

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

**Konstruktory Rfc2898DeriveBytes přijměte název hashovacího algoritmu**

<xref:System.Security.Cryptography.Rfc2898DeriveBytes> Třída má tři nové konstruktory s <xref:System.Security.Cryptography.HashAlgorithmName> parametr, který určuje algoritmus HMAC při odvození klíče. Nemusíte používat SHA-1, vývojáři měli použít algoritmus SHA-2 a technologií HMAC jako SHA-256, jak je znázorněno v následujícím příkladu:

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

**Podpora pro dočasné klíče**

PFX import můžete volitelně načíst privátního klíče přímo z paměti bez použití pevný disk. Při nové <xref:System.Security.Cryptography.X509Certificates.X509KeyStorageFlags.EphemeralKeySet?displayProperty=nameWithType> zadán příznak v <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> konstruktor nebo jednoho z přetížení <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.Import%2A?displayProperty=nameWithType> metoda, se načtou privátní klíče jako dočasné klíče. To brání klíče viditelné na disku. Ale:

- Protože klíče nejsou uložit trvale na disk, certifikáty načítají s nejsou vhodnými kandidáty pro přidání do X509Store tento příznak.

- Klíče načteny tímto způsobem jsou téměř vždy načteno prostřednictvím Windows CNG. Proto volající musí přístup k soukromému klíči voláním metody rozšíření [certifikátu. GetRSAPrivateKey()](xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey%2A). <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> Vlastnost nebude fungovat.

- Od verze starší <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> vlastnost nefunguje s certifikáty, vývojáři by měl provádět důkladné testování před přepnutím do dočasné klíče.

**Programové vytváření PKCS #10 certifikační podpisový požadavků a veřejný klíč certifikátů X.509**

Počínaje rozhraním .NET Framework 4.7.2, úlohy můžete vygenerovat certifikát Podepisování požadavky nástroje (CSR), která umožňuje vytvoření certifikátu žádosti budou umístěné do stávající nástroje. To je často užitečné v testovací scénáře.

Další informace a příklady kódu naleznete v tématu "programové vytváření PKCS #10 podpisový požadavky certifikace a veřejný klíč certifikátů X.509" v [Blog k .NET](https://blogs.msdn.microsoft.com/dotnet/2018/03/08/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).

**Nové členy SignerInfo**

Počínaje rozhraním .NET Framework 4.7.2, <xref:System.Security.Cryptography.Pkcs.SignerInfo> třída zveřejňuje informace o podpisu. Můžete načíst hodnotu <xref:System.Security.Cryptography.Pkcs.SignerInfo.SignatureAlgorithm?displayProperty=fullName> a určí algoritmus podpisu používané podpisu. <xref:System.Security.Cryptography.Pkcs.SignerInfo.GetSignature%2A?displayProperty=nameWithType> lze volat pro kopii kryptografický podpis pro tento podepisující osoba.

**Ponechejte zabalené stream otevřené po vyřazení CryptoStream**

Počínaje rozhraním .NET Framework 4.7.2, <xref:System.Security.Cryptography.CryptoStream> třída má dodatečném konstruktoru, který umožňuje <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> není zavřete zabalené datového proudu. Ponechat otevřené po zabalené datový proud <xref:System.Security.Cryptography.CryptoStream> zrušení instance, zavolat novou <xref:System.Security.Cryptography.CryptoStream> konstruktor následujícím způsobem:

```csharp
var cStream = new CryptoStream(stream, transform, mode, leaveOpen: true);
```
```vb
Dim cStream = New CryptoStream(stream, transform, mode, leaveOpen:=true)
```

**Dekomprese změnami DeflateStream**

Od verze rozhraní .NET Framework 4.7.2, provádění operace pro dekompresi v <xref:System.IO.Compression.DeflateStream> došlo ke změně třídy používat nativní rozhraní API Windows ve výchozím nastavení. Obvykle to vede k zlepšení výkonu.

Ve výchozím nastavení u aplikací určených pro rozhraní .NET Framework 4.7.2 je povolena podpora pro dekompresi pomocí rozhraní Windows API. Aplikace, které jsou cíleny na starší verze rozhraní .NET Framework, ale jsou spuštěny v rozhraní .NET Framework 4.7.2 můžete začít používat toto chování přidáním následujícího kódu [přepínač AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do konfiguračního souboru aplikace:

```xml
<AppContextSwitchOverrides value="Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=false" />
```

**Další kolekce rozhraní API**

Přidá počet nových rozhraní API pro rozhraní .NET Framework 4.7.2 <xref:System.Collections.Generic.SortedSet%601> a <xref:System.Collections.Generic.HashSet%601> typy. Zde jsou některé z nich:

- `TryGetValue` metody, které rozšiřují zkuste používaným v jiných typech kolekce na tyto dva typy. Metody jsou:

   - [veřejné bool HashSet<T>. TryGetValue (out T actualValue T equalValue)](xref:System.Collections.Generic.SortedSet%601.TryGetValue%2A)
   - [veřejné bool SortedSet<T>. TryGetValue (out T actualValue T equalValue)](xref:System.Collections.Generic.SortedSet%601.TryGetValue%2A)

- `Enumerable.To*` rozšiřující metody, které převést kolekci, <xref:System.Collections.Generic.HashSet%601>:

   - [Veřejné statické HashSet<TSource> ToHashSet<TSource>(toto rozhraní IEnumerable<TSource> zdroje)](xref:System.Linq.Enumerable.ToHashSet%2A)
   - [Veřejné statické HashSet<TSource> ToHashSet<TSource>(toto rozhraní IEnumerable<TSource> zdroje IEqualityComparer<TSource> porovnávače)](xref:System.Linq.Enumerable.ToHashSet%2A)

- Nové <xref:System.Collections.Generic.HashSet%601> konstruktory, které vám umožní nastavit kapacitu kolekce, který dává zvýšení výkonu, když víte, velikost <xref:System.Collections.Generic.HashSet%601> předem:

   - [HashSet – Public (int kapacitu)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32))
   - [HashSet – Public (int kapacitu, IEqualityComparer<T> porovnávače)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32,System.Collections.Generic.IEqualityComparer%7B%600%7D))

<xref:System.Collections.Concurrent.ConcurrentDictionary%602> Třída zahrnuje nové přetížení <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> a <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> metody k načtení hodnoty ze slovníku nebo ho přidat, pokud není nalezen a k přidání hodnoty do slovníku nebo ji aktualizovat, pokud již existuje.

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

**Podpora pro injektáž závislostí ve webových formulářů**

[Injektáž závislostí (DI)](/aspnet/core/fundamentals/dependency-injection#overview-of-dependency-injection) odděluje objekty a jejich závislosti tak, aby kód objektu už nebude potřeba změnit to, že došlo ke změně závislosti. Při vývoji aplikací ASP.NET, které se zaměřují na rozhraní .NET Framework 4.7.2, můžete:

- Pomocí vkládání založené na setter, založené na rozhraní a na základě konstruktoru v [moduly a obslužné rutiny](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)), [stránce instance](xref:System.Web.UI.Page), a [uživatelské ovládací prvky](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) technologie ASP.NET webové aplikace projekty.

- Pomocí vkládání setter a interface v [moduly a obslužné rutiny](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)), [stránce instance](xref:System.Web.UI.Page), a [uživatelské ovládací prvky](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) webových projektů ASP.NET.

- Zařaďte různých závislostí architektury vkládání.

**Podpora pro soubory cookie stejný web**

[SameSite](https://tools.ietf.org/html/draft-west-first-party-cookies-07) zabrání odesílání spolu s podvržení žádosti soubor cookie prohlížeče. Rozhraní .NET Framework 4.7.2 přidá <xref:System.Web.HttpCookie.SameSite?displayProperty=nameWithType> vlastnost, jejíž hodnota je <xref:System.Web.SameSiteMode?displayProperty=nameWithType> člena výčtu. Pokud je jeho hodnota <xref:System.Web.SameSiteMode.Strict?displayProperty=nameWithType> nebo <xref:System.Web.SameSiteMode.Lax?displayProperty=nameWithType>, přidá ASP.NET `SameSite` atribut hlavičkou set-cookie. SameSite podpora se vztahuje na <xref:System.Web.HttpCookie> objekty, stejně jako na <xref:System.Web.Security.FormsAuthentication> a <xref:System.Web.SessionState> soubory cookie.

Můžete nastavit SameSite pro <xref:System.Web.HttpCookie> objektu následujícím způsobem:

```csharp
var c = new HttpCookie("secureCookie", "same origin");
c.SameSite = SameSiteMode.Lax;
```
```vb
Dim c As New HttpCookie("secureCookie", "same origin")
c.SameSite = SameSiteMode.Lax
```
SameSite soubory cookie na úrovni aplikace můžete taky nakonfigurovat úpravou souboru web.config:

```xml
<system.web>
   <httpCookies sameSite="Strict" />
</system.web>
```
Můžete přidat SameSite pro <xref:System.Web.Security.FormsAuthentication> a <xref:System.Web.SessionState> soubory cookie úpravou souboru webové konfigurace:

```xml
<system.web>
   <authentication mode="Forms">
      <forms cookieSameSite="Lax">
         <!-- ...   -->
      </forms>
   <authentication />
   <sessionSate cookieSameSite="Lax"></sessionState>
</system.web>
```

<a name="net472" />

#### <a name="networking"></a>Síťové služby

**Implementace vlastnosti HttpClientHandler**

Rozhraní .NET Framework 4.7.1 přidána osm vlastnosti, které chcete <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> třídy. Ale dvě vyvolalo <xref:System.PlatformNotSupportedException>. Rozhraní .NET Framework 4.7.2 nyní poskytuje implementaci pro tyto vlastnosti. Mezi vlastnosti patří:

- <xref:System.Net.Http.HttpClientHandler.CheckCertificateRevocationList>
- <xref:System.Net.Http.HttpClientHandler.SslProtocols>

<a name="sql472" />

#### <a name="sqlclient"></a>SQLClient

**Podpora pro Azure Active Directory, univerzální ověřování a Vícefaktorové ověřování**

Rostoucí požadavky dodržování předpisů a zabezpečení vyžadují, kterou mnozí uživatelé používají ověřování službou Multi-Factor Authentication (MFA). Kromě toho aktuální osvědčené postupy Zabraňte včetně uživatelská hesla přímo v připojovacích řetězcích. Pro podporu těchto změn rozhraní .NET Framework 4.7.2 rozšiřuje [SQLClient připojovací řetězce](xref:System.Data.SqlClient.SqlConnection.ConnectionString) tak, že přidáte novou hodnotu "Active Directory Interactive", existující klíčového slova "Ověřování" pro podporu vícefaktorového ověřování a [Azure AD Ověřování](/azure/sql-database/sql-database-aad-authentication-configure). Nová interaktivní metoda podporuje nativní a federovaných uživatelů Azure AD, stejně jako uživatele typu Host Azure AD. Když tato metoda se používá, se ověření MFA uložené ve službě Azure AD je podporována pro databáze SQL. Kromě toho v procesu ověřování požadavků heslo uživatele dodržovat osvědčené postupy zabezpečení.

V předchozích verzích rozhraní .NET Framework, připojení SQL, které jsou podporovány pouze <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryPassword?displayProperty=nameWithType> a <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryIntegrated?displayProperty=nameWithType> možnosti. Obě tyto jsou součástí neinteraktivní [ADAL protokol](/azure/active-directory/develop/active-directory-authentication-libraries), který nepodporuje vícefaktorové ověřování. S novými <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryInteractive?displayProperty=nameWithType> možnost, připojení k SQL podporuje vícefaktorové ověřování, stejně jako stávající metody ověřování (heslo a integrované ověřování), což umožňuje uživatelům k zadání hesel uživatelského interaktivně bez zachování hesel v připojení řetězec.

Další informace a příklad naleznete v části "SQL – Azure AD univerzální a službou Multi-Factor Authentication podporu ověřování" v [Blog k .NET](https://blogs.msdn.microsoft.com/dotnet/2018/03/08/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).

**Podpora pro funkce Always Encrypted verze 2**

NET Framework 4.7.2 přidá podporuje pro na základě enklávy s funkcí Always Encrypted. Původní verze s funkcí Always Encrypted je technologie šifrování na straně klienta, v jaké šifrovací klíče nikdy neopustí klienta. V enklávě podle funkce Always Encrypted může klient volitelně odeslat šifrovací klíče do zabezpečené enklávy, což je zabezpečené výpočetní entita, která může být považována za součást SQL Server, ale, že kód systému SQL Server nelze manipulovat se. Pokud chcete podporovat, na základě enklávy s funkcí Always Encrypted, rozhraní .NET Framework 4.7.2 přidá následující typy a členy, <xref:System.Data.SqlClient> obor názvů:

- <xref:System.Data.SqlClient.SqlConnectionStringBuilder.EnclaveAttestationUrl?displayProperty=nameWithType>, který určuje identifikátor Uri pro na základě enklávy s funkcí Always Encrypted.

- <xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider>, což je abstraktní třída, ze které všechny enklávy jsou odvozeny poskytovatelů.

- <xref:System.Data.SqlClient.SqlEnclaveSession>, který zapouzdří stav pro danou enklávy relace.

- <xref:System.Data.SqlClient.SqlEnclaveAttestationParameters>, který obsahuje parametry ověření SQL Server používá k získání informací potřebných k provedení konkrétní protokol ověření identity.

Konfigurační soubor aplikace pak určuje konkrétní implementaci abstraktní <xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider?displayProperty=nameWithType> třídu, která poskytuje funkce pro poskytovatele enklávy. Příklad:

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

Základní tok na základě enklávy s funkcí Always Encrypted je:

1. Uživatel vytvoří AlwaysEncrypted připojení k systému SQL Server, který se nepodporuje na základě enklávy s funkcí Always Encrypted. Ovladač kontaktuje službu ověření k zajištění, že se připojuje ke správné enklávy.

1. Jakmile enklávě byla ověřena, ovladač naváže zabezpečený kanál s zabezpečené enklávy hostované v systému SQL Server.

1. Ovladač sdílí šifrovacích klíčů oprávnění od klienta se zabezpečené enklávy po dobu trvání připojení SQL.

<a name="wpf472" />

#### <a name="windows-presentation-foundation"></a>Windows Presentation Foundation

**Hledání třídách ResourceDictionaries podle zdroje**

Počínaje rozhraním .NET Framework 4.7.2, můžete najít diagnostiku Pomocníka s nastavením <xref:System.Windows.Xps.Packaging.IXpsFixedPageReader.ResourceDictionaries> , které byly vytvořeny z daného zdroje identifikátoru Uri. (Tato funkce je pro použití diagnostických asistenti, nikoli produkčních aplikací.) Diagnostické asistenta, jako je Visual Studio "Edit-and-Continue" zařízení umožňuje uživatel upravit ResourceDictionary se záměrem, že změny se použijí ke spuštěné aplikaci. Jeden krok v dosažení tohoto cíle je vyhledání všech třídách ResourceDictionaries vytvořené běžící aplikaci ze slovníku, který se právě upravuje. Například může aplikace deklarovat ResourceDictionary, jehož obsah je zkopírován z daného zdroje identifikátoru URI:

```xml
<ResourceDictionary Source="MyRD.xaml">
```

Diagnostické asistent, který upraví původní kód v *MyRD.xaml* nové funkce lze použít k vyhledání slovníku. Tato funkce je implementováno novou statickou metodu <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetResourceDictionariesForSource%2A?displayProperty=nameWithType>. Diagnostické Pomocníka s nastavením volá novou metodu pomocí absolutní identifikátor Uri, který identifikuje původní značek, jak je znázorněno v následujícím kódu:

```csharp
IEnumerable<ResourceDictionary> dictionaries = ResourceDictionaryDiagnostics.GetResourceDictionariesForSource(new Uri("pack://application:,,,/MyApp;component/MyRD.xaml"));
```
```vb
Dim dictionaries As IEnumerable(Of ResourceDictionary) = ResourceDictionaryDiagnostics.GetResourceDictionariesForSource(New Uri("pack://application:,,,/MyApp;component/MyRD.xaml"))
```

Metoda vrátí prázdnou vyčíslitelné Pokud <xref:System.Windows.Diagnostics.VisualDiagnostics> je povolená a [ `ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO` ](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)  nastavení proměnné prostředí.

**Vyhledání ResourceDictionary vlastníky**

Počínaje rozhraním .NET Framework 4.7.2, mohou diagnostické Pomocníka s nastavením vyhledat vlastníci daný <xref:Windows.UI.Xaml.ResourceDictionary>. (Tato funkce je pro použití diagnostických Asistenti a ne produkční aplikace.) Vždy, když je provedena změna <xref:Windows.UI.Xaml.ResourceDictionary>, WPF automaticky vyhledá všechny [DynamicResource](../wpf/advanced/dynamicresource-markup-extension.md) odkazy, které by mohly mít dopad změnu.

Diagnostické asistenta, jako je Visual Studio "Edit-and-Continue" zařízení může být vhodné pro rozšíření pro zpracování [StaticResource](../wpf/advanced/staticresource-markup-extension.md) odkazy. Prvním krokem v tomto procesu je požadované vlastníky slovníku To znamená Chcete-li vyhledat všechny objekty jehož `Resources` vlastnost odkazuje na adresář (buď přímo nebo nepřímo prostřednictvím <xref:System.Windows.ResourceDictionary.MergedDictionaries?displayProperty=nameWithType> vlastnost). Tři nové statické metody implementovány v <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics?displayProperty=nameWithType> třídy, jeden pro každou ze základních typů, které má `Resources` vlastnost, podporují tento krok:

- [`public static IEnumerable<FrameworkElement> GetFrameworkElementOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetFrameworkElementOwners%2A)

- [`public static IEnumerable<FrameworkContentElement> GetFrameworkContentElementOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetFrameworkContentElementOwners%2A)

- [`public static IEnumerable<Application> GetApplicationOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetApplicationOwners%2A)

Tyto metody vrací prázdný vyčíslitelné Pokud <xref:System.Windows.Diagnostics.VisualDiagnostics> je povolená a [ `ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO` ](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)  nastavení proměnné prostředí.

**Hledají se odkazy StaticResource**

Diagnostické asistent teď můžou přijímat oznámení pokaždé, když se [StaticResource](../wpf/advanced/staticresource-markup-extension.md) odkaz je vyřešený. (Tato funkce je pro použití diagnostických asistenti, nikoli produkčních aplikací.) Diagnostické asistenta, jako je Visual Studio "Edit-and-Continue" zařízení chtít aktualizovat všechny výskyty prostředek při její hodnotu v <xref:Windows.UI.Xaml.ResourceDictionary> změny. WPF se k tomu automaticky [DynamicResource](../wpf/advanced/dynamicresource-markup-extension.md) odkazy, ale záměrně nenabízí tak [StaticResource](../wpf/advanced/staticresource-markup-extension.md) odkazy. Počínaje rozhraním .NET Framework 4.7.2, diagnostických Pomocníka s nastavením lze použít tato oznámení k vyhledání těchto používá statický prostředek.

Oznámení je implementována pomocí nového <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.StaticResourceResolved?displayProperty=nameWithType> události:

```csharp
public static event EventHandler<StaticResourceResolvedEventArgs> StaticResourceResolved;
```

```vb
Public Shared Event StaticResourceResolved As EventHandler(Of StaticResourceResolvedEventArgs)
```

Tato událost je vyvolána pokaždé, když se odstraňuje modul runtime [StaticResource](../wpf/advanced/staticresource-markup-extension.md) odkaz. <xref:System.Windows.Diagnostics.StaticResourceResolvedEventArgs> Argumenty popisují rozlišení a označení objektu a vlastnosti, které hostují [StaticResource](../wpf/advanced/staticresource-markup-extension.md) odkaz a <xref:Windows.UI.Xaml.ResourceDictionary> a klíč se používá pro rozlišení:

```csharp
public class StaticResourceResolvedEventArgs : EventArgs
{
   public Object TargetObject { get; }

   public Object TargetProperty { get; }

   public ResourceDictionary ResourceDictionary { get; }

   public object ResourceKey { get; }
}
```

Není vyvolána událost (a jeho `add` přístupový objekt se ignoruje.) Pokud <xref:System.Windows.Diagnostics.VisualDiagnostics> je povolená a [ `ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO` ](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)  nastavení proměnné prostředí.

#### <a name="clickonce"></a>ClickOnce

Všechny s ohledem na HDPI aplikace pro Windows Forms, Windows Presentation Foundation (WPF) a Visual Studio Tools for Office (VSTO) můžete nasadit s použitím technologie ClickOnce. Pokud tuto položku je nalezena v manifestu aplikace, bude v rámci rozhraní .NET Framework 4.7.2 úspěšné nasazení:

```xml
<windowsSettings>
   <dpiAware xmlns="http://schemas.microsoft.com/SMI/2005/WindowsSettings">true</dpiAware>
</windowsSettings>
```

Pro aplikace Windows Forms předchozí řešení nastavení sledování DPI v konfiguračním souboru aplikace namísto manifestu aplikace již není nezbytné pro nasazení ClickOnce proběhla úspěšně.

<a name="v471" />

## <a name="whats-new-in-the-net-framework-471"></a>Co je nového v rozhraní .NET Framework 4.7.1

Rozhraní .NET Framework 4.7.1 obsahuje nové funkce v následujících oblastech:

- [Jádro](#core471)
- [Common language runtime (CLR)](#clr)
- [Sítě](#net471)
- [ASP.NET](#asp-net471)

Kromě toho je hlavní fokus v rozhraní .NET Framework 4.7.1 vylepšené přístupnosti, které umožňuje aplikaci poskytovat vhodné prostředí pro uživatele technologie pro usnadnění. Informace o vylepšení přístupnosti v rozhraní .NET Framework 4.7.1 najdete v tématu [co je nového v usnadnění přístupu v rozhraní .NET Framework](whats-new-in-accessibility.md).

<a name="core471" />

#### <a name="core"></a>Jádro

**Podpora pro .NET Standard 2.0**

[.NET standard](~/docs/standard/net-standard.md) definuje sadu rozhraní API, která musí být k dispozici na jednotlivých implementace .NET, která podporuje verzi standard. Rozhraní .NET Framework 4.7.1 plně podporuje .NET Standard 2.0 a přidá [přibližně 200 rozhraní API](https://github.com/dotnet/standard/blob/master/netstandard/src/ApiCompatBaseline.net461.txt) , které jsou definovány v .NET Standard 2.0 a nebyly nalezeny v rozhraní .NET Framework 4.7, 4.6.1 a 4.6.2. (Všimněte si, že tyto verze rozhraní .NET Framework podporují .NET Standard 2.0, pouze v případě, že další podpůrné soubory .NET Standard jsou nasazené v cílovém systému.) Další informace najdete v tématu "BCL – .NET Standard 2.0 Support" [Runtime rozhraní .NET Framework 4.7.1 a funkce kompilátoru](https://blogs.msdn.microsoft.com/dotnet/2017/09/28/net-framework-4-7-1-runtime-and-compiler-features) blogový příspěvek.

**Podpora konfigurace počítačů**

Konfigurace počítačů umožňují vývojářům vložení a nastavení konfigurace pro aplikace sestavení dynamicky za běhu. Tvůrci vlastní konfigurace slouží k úpravě existující data v konfiguračním oddílu nebo pro vytváření konfiguračního oddílu úplně od začátku. Bez konfigurace tvůrci souborech .config jsou statické a jejich nastavení jsou definovány nějakou dobu, než se spustí aplikace.

K vytvoření vlastní konfigurace Tvůrce odvozujete od abstraktní vaše Tvůrce <xref:System.Configuration.ConfigurationBuilder> třídy a přepsat její <xref:System.Configuration.ConfigurationBuilder.ProcessConfigurationSection%2A?displayProperty=nameWithType> a <xref:System.Configuration.ConfigurationBuilder.ProcessRawXml%2A?displayProperty=nameWithType>. Také definovat vaše tvůrci v souboru .config. Další informace najdete v tématu v části "Konfigurace tvůrci" [rozhraní .NET Framework 4.7.1 ASP.NET a konfigurace funkce](https://blogs.msdn.microsoft.com/dotnet/2017/09/13/net-framework-4-7-1-asp-net-and-configuration-features) blogový příspěvek.

**Běhové funkce detekce**

<xref:System.Runtime.CompilerServices.RuntimeFeature?displayProperty=nameWithType> Třída poskytuje mechanismus pro určení, zda předdefinované funkce je podporovaná v daném implementace .NET v době kompilace nebo běhu. V době kompilace kompilátor můžete zkontrolovat, zda existuje zadaná pole k určení, zda tato funkce je podporovaná; Pokud ano, ho můžete generovat kód, který využívá výhod této funkce. V době běhu aplikace může volat <xref:System.Runtime.CompilerServices.RuntimeFeature.IsSupported%2A?displayProperty=nameWithType> metody před generování kódu v době běhu. Další informace najdete v tématu [přidejte pomocnou metodu k popisu funkce podporované modulem runtime](https://github.com/dotnet/corefx/issues/17116).

**Jsou Serializovatelné typy řazené kolekce členů hodnot**

Od verze rozhraní .NET Framework 4.7.1, <xref:System.ValueTuple?displayProperty=nameWithType> a její přidružené obecné typy jsou označeny jako [Serializable](xref:System.SerializableAttribute), který umožňuje binární serializace. To by měl vytvořte migrace typy řazené kolekce členů, například <xref:System.Tuple%603> a <xref:System.Tuple%604>, hodnota řazené kolekce členů typů jednodušší. Další informace najdete v tématu "Kompilátoru – typu ValueTuple je serializovatelný" v [Runtime rozhraní .NET Framework 4.7.1 a funkce kompilátoru](https://blogs.msdn.microsoft.com/dotnet/2017/09/28/net-framework-4-7-1-runtime-and-compiler-features) blogový příspěvek.

**Podpora pro odkazy jen pro čtení**

Rozhraní .NET Framework 4.7.1 přidá <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute?displayProperty=nameWithType>. Tento atribut slouží k označení členy, které mají jen pro čtení ref návratové typy nebo parametry pomocí kompilátorů jazyka. Další informace najdete v tématu "Kompilátoru – podpora pro ReadOnlyReferences" [Runtime rozhraní .NET Framework 4.7.1 a funkce kompilátoru](https://blogs.msdn.microsoft.com/dotnet/2017/09/28/net-framework-4-7-1-runtime-and-compiler-features) blogový příspěvek. Informace o návratových hodnot ref, naleznete v tématu [Ref návratové hodnoty a ref lokální proměnné (C# průvodce)](~/docs/csharp/programming-guide/classes-and-structs/ref-returns.md) a [Ref návratové hodnoty (Visual Basic)](../../visual-basic/programming-guide/language-features/procedures/ref-return-values.md).

<a name="clr" />

#### <a name="common-language-runtime-clr"></a>Common language runtime (CLR)

**Vylepšení výkonu kolekce uvolnění paměti**

Změny v uvolňování paměti (GC) v rozhraní .NET Framework 4.7.1 zvýšit celkový výkon, hlavně pro přidělení haldy velkých objektů (LOH). Samostatné uzamčení se v rozhraní .NET Framework 4.7.1 používají pro přidělení haldy malých objektů (SOH) a LOH, který umožňuje LOH přidělení má použít při uvolňování paměti na pozadí (BGC) je cílit na konkrétní prohlášení o stavu. Aplikace, kterým je velký počet přidělení LOH v důsledku toho by se zobrazit snížení přidělení kolize zámků a vylepšení výkonu. Další informace najdete v části "Vylepšení výkonu pro uvolňování paměti – modul Runtime" v [Runtime rozhraní .NET Framework 4.7.1 a funkce kompilátoru](https://blogs.msdn.microsoft.com/dotnet/2017/09/28/net-framework-4-7-1-runtime-and-compiler-features/) blogový příspěvek.

<a name="net471"/>

#### <a name="networking"></a>Síťové služby

**Podpora Message.HashAlgorithm SHA-2**

V rozhraní .NET Framework 4.7 a předchozími verzemi <xref:System.Messaging.Message.HashAlgorithm%2A?displayProperty=nameWithType> hodnoty vlastností, které jsou podporovány <xref:System.Messaging.HashAlgorithm.Md5?displayProperty=nameWithType> a <xref:System.Messaging.HashAlgorithm.Sha?displayProperty=nameWithType> pouze. Od verze rozhraní .NET Framework 4.7.1, <xref:System.Messaging.HashAlgorithm.Sha256?displayProperty=nameWithType>, <xref:System.Messaging.HashAlgorithm.Sha384?displayProperty=nameWithType>, a <xref:System.Messaging.HashAlgorithm.Sha512?displayProperty=nameWithType> jsou také podporovány. Určuje, zda tato hodnota se používá ve skutečnosti závisí na služby MSMQ, od té doby <xref:System.Messaging.Message> k řazení samotné nemá žádné algoritmu hash, ale jednoduše předává hodnot do služby MSMQ. Další informace najdete v tématu v části "podpora Message.HashAlgorithm SHA-2" [funkce rozhraní .NET Framework 4.7.1 ASP.NET a konfigurace](https://blogs.msdn.microsoft.com/dotnet/2017/09/13/net-framework-4-7-1-asp-net-and-configuration-features/) blogový příspěvek.

<a name="asp-net471" />

#### <a name="aspnet"></a>ASP.NET

**Provedení kroků v aplikacích ASP.NET**

ASP.NET zpracovává požadavky v předdefinované kanál, který zahrnuje 23 události. ASP.NET provede každou obslužnou rutinu události jako krok zpracování. Ve verzi technologie ASP.NET do rozhraní .NET Framework 4.7 nelze ASP.NET tok kontextu spuštění z důvodu přepínání mezi nativní a spravovaná vlákna. Místo toho ASP.NET selektivně toky pouze <xref:System.Web.HttpContext>. Od verze rozhraní .NET Framework 4.7.1, <xref:System.Web.HttpApplication.OnExecuteRequestStep(System.Action{System.Web.HttpContextBase,System.Action})?displayProperty=nameWithType> metoda také umožňuje moduly okolí data obnovit. Tato funkce je cílená na knihovny pro obeznámeni s trasování, profilování, diagnostiky nebo transakce, například o provádění toku aplikace. Další informace najdete v tématu "ASP.NET provádění kroku funkce" [rozhraní .NET Framework 4.7.1 ASP.NET a konfigurace funkce](https://blogs.msdn.microsoft.com/dotnet/2017/09/13/net-framework-4-7-1-asp-net-and-configuration-features) blogový příspěvek.

**Analýza kódu HttpCookie technologie ASP.NET**

Rozhraní .NET Framework 4.7.1 zahrnuje nové metody, <xref:System.Web.HttpCookie.TryParse%2A?displayProperty=nameWithType>, který poskytuje standardizované způsob, jak vytvořit <xref:System.Web.HttpCookie> objekt z řetězce a přesně přiřadit hodnoty souboru cookie, například datum vypršení platnosti a cestu. Další informace najdete v tématu "ASP.NET HttpCookie analýza kódu" v [rozhraní .NET Framework 4.7.1 ASP.NET a konfigurace funkce](https://blogs.msdn.microsoft.com/dotnet/2017/09/13/net-framework-4-7-1-asp-net-and-configuration-features) blogový příspěvek.

**Hodnota hash SHA-2 možnosti pro ověřovací pověření formuláře technologie ASP.NET**

V rozhraní .NET Framework 4.7 a dřívějších verzích technologie ASP.NET povolena vývojáři ukládání přihlašovacích údajů s hashovaná hesla v konfiguračních souborech na použití MD5 nebo SHA1. Od verze rozhraní .NET Framework 4.7.1, ASP.NET podporuje nové zabezpečené možnosti hashovací algoritmus SHA-2, jako je SHA256, SHA384 a SHA512. SHA1 zůstane výchozí a jiné než výchozí hashovací algoritmus je definovat v konfiguračním souboru webu. Příklad:

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

## <a name="whats-new-in-the-net-framework-47"></a>Co je nového v rozhraní .NET Framework 4.7

Rozhraní .NET Framework 4.7 obsahuje nové funkce v následujících oblastech:

- [Jádro](#Core47)
- [Sítě](#net47)
- [ASP.NET](#ASP-NET47)
- [Windows Communication Foundation (WCF)](#wcf47)
- [Windows Forms](#wf47)
- [Windows Presentation Foundation (WPF)](#WPF47)

Seznam nových rozhraní API přidá do rozhraní .NET Framework 4.7, najdete v části [změn rozhraní API aplikace rozhraní .NET Framework 4.7](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-api-changes.md) na Githubu. Seznam vylepšení funkcí a oprav chyb v rozhraní .NET Framework 4.7 najdete v tématu [rozhraní .NET Framework 4.7 změny seznamu](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-changes.md) na Githubu.  Další informace najdete v tématu [uvedení rozhraní .NET Framework 4.7](https://blogs.msdn.microsoft.com/dotnet/2017/04/05/announcing-the-net-framework-4-7/) v blogu .NET.

<a name="Core47" />

#### <a name="core"></a>Jádro

Rozhraní .NET Framework 4.7 zlepšuje serializace pomocí <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:

**Rozšířené funkce s šifrování ECC (Elliptic Curve)***

V rozhraní .NET Framework 4.7 `ImportParameters(ECParameters)` metody byly přidány do <xref:System.Security.Cryptography.ECDsa> a <xref:System.Security.Cryptography.ECDiffieHellman> tříd pro povolení pro objekt představující klíč rozhraní už navázalo. `ExportParameters(Boolean)` Metoda se taky přidala pro export klíče pomocí parametrů explicitní křivky.

Rozhraní .NET Framework 4.7 také přidává podporu pro další křivky (včetně sady Brainpool křivky) a přidal předdefinované definice pro snadné vytváření prostřednictvím nového <xref:System.Security.Cryptography.ECDsa.Create%2A> a <xref:System.Security.Cryptography.ECDiffieHellman.Create%2A> metody pro vytváření objektů.

Zobrazí se [příklad rozhraní .NET Framework 4.7 kryptografických vylepšení](https://gist.github.com/richlander/5a182899895a87a296c21ada97f7a54e) na Githubu.

**Lepší podporu pro řídicí znaky pomocí objektu DataContractJsonSerializer**

V rozhraní .NET Framework 4.7 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> serializuje řídicí znaky podle standardu ECMAScript 6. Toto chování je povoleno standardně pro aplikace, které jsou cíleny rozhraní .NET Framework 4.7 a je přihlašovaná funkce pro aplikace, které jsou spuštěny v rozhraní .NET Framework 4.7 ale cílení na předchozí verzi rozhraní .NET Framework. Další informace najdete v tématu [změny mění se cílení v rozhraní .NET Framework 4.7](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md).

<a name="net47" />

#### <a name="networking"></a>Síťové služby

Rozhraní .NET Framework 4.7 přidá následující funkce související se sítí:

**Výchozí operační systém podporující protokoly TLS***

Zásobník protokolu TLS, který používá <xref:System.Net.Security.SslStream?displayProperty=nameWithType> nahoru zásobníku komponent, jako jsou HTTP, FTP a SMTP a umožňuje vývojářům využít protokoly TLS výchozí podporovaný operační systém. Vývojáři potřebují žádné delší pevně zakódovat verze TLS.

<a name="ASP-NET47" />

#### <a name="aspnet"></a>ASP.NET

V rozhraní .NET Framework 4.7 technologie ASP.NET obsahuje následující nové funkce:

**Rozšiřující objekt mezipaměti**

Od verze rozhraní .NET Framework 4.7, ASP.NET přidá novou sadu rozhraní API, která vývojářům umožňuje nahradit výchozí implementace technologie ASP.NET pro ukládání do mezipaměti objektů v paměti do mezipaměti a paměť. Vývojáři, můžete teď může nahradit některé z následujících tří součástí Pokud implementace technologie ASP.NET není dostatečný:

- **Objekt mezipaměti Store**. Pomocí nové konfigurační oddíl zprostředkovatelů mezipaměti můžete vývojáři zařadit nové implementace mezipaměti objekt pro aplikaci ASP.NET pomocí nových **ICacheStoreProvider** rozhraní.

- **Sledování paměti**. Sledování paměti výchozí v technologii ASP.NET upozorní aplikace neopravňují neblíží limitu nakonfigurované Nesdílené bajty pro proces, nebo pokud je počítač nedostatek celkové dostupné fyzické paměti RAM. Když se blíží tato omezení jsou vyvolávány oznámení. U některých aplikací jsou oznámení aktivovány, nakonfigurované limity umožňující užitečné reakcí s palcem příliš zavřít. Vývojáři teď můžou zadat své vlastní sledování paměti a nahradit výchozí pomocí <xref:System.Web.Hosting.ApplicationMonitors.MemoryMonitor%2A?displayProperty=nameWithType> vlastnost.

- **Reakcí s palcem Limit paměti**. Ve výchozím nastavení, technologie ASP.NET pokusí oříznout mezipaměť objektů a pravidelně volala <xref:System.GC.Collect%2A?displayProperty=nameWithType> při blíží limitu soukromých bajtů procesu. U některých aplikací Četnost volání <xref:System.GC.Collect%2A?displayProperty=nameWithType> nebo velikost mezipaměti, která je oříznuta jsou neefektivní. Vývojáři mohou nyní nahrazení nebo doplnění výchozí chování prostřednictvím přihlášení odběru **IObserver** implementace monitorování paměti aplikace.

<a name="wcf47" />

#### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)

Windows Communication Foundation (WCF) přidá následující funkce a změny:

**Umožňuje nakonfigurovat výchozí nastavení zabezpečení zprávy protokolu TLS 1.1 a TLS 1.2**

Od verze rozhraní .NET Framework 4.7, WCF umožňuje nakonfigurovat protokol TLS 1.1 a TLS 1.2 kromě SSL 3.0 a protokol TLS 1.0 jako výchozí protokol zabezpečení zprávy. Toto je nastavení opt-in; ho Pokud chcete povolit, je nutné přidat následující položku do konfiguračního souboru aplikace:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false" />
</runtime>
```

**Vylepšení spolehlivosti aplikací služby WCF a serializace WCF**

WCF obsahuje několik změn kódu, které eliminovat konflikty časování, následné vylepšení výkonu a spolehlivosti možnosti serializace. Zde jsou některé z nich:

- Lepší podpora pro kombinování synchronní a asynchronní kód ve voláních **SocketConnection.BeginRead** a **SocketConnection.Read**.
- Lepší spolehlivosti při přerušení připojení s **SharedConnectionListener** a **DuplexChannelBinder**.
- Vylepšená spolehlivost uživatelské Serializační operace při volání <xref:System.Runtime.Serialization.FormatterServices.GetSerializableMembers%28System.Type%29?displayProperty=nameWithType> metody.
- Lepší spolehlivosti při odebírání číšník voláním **ChannelSynchronizer.RemoveWaiter** metody.

<a name="wf47" />

#### <a name="windows-forms"></a>Windows Forms

Windows Forms v rozhraní .NET Framework 4.7 zlepšuje podporu pro vysokou sledování DPI.

**Podpora vysoké rozlišení DPI**

Počínaje aplikací využívajících rozhraní .NET Framework 4.7, rozhraní .NET Framework obsahuje vysokého nastavení DPI a dynamické DPI podporu pro aplikace Windows Forms. Podpora vysoké rozlišení DPI zlepšuje rozložení a vzhled formuláře a ovládací prvky na vysoké rozlišení DPI monitorech. Dynamické DPI změní rozložení a vzhled formuláře a ovládací prvky, když uživatel změní měřítko DPI nebo zobrazení spuštěné aplikace.

Podpora vysoké DPI je přihlašovaná funkce, které nakonfigurujete tak, že definujete [ \<System.Windows.Forms.ConfigurationSection >](../configure-apps/file-schema/winforms/index.md) oddílu v konfiguračním souboru aplikace. Další informace o přidávání podporu vysoké rozlišení DPI a dynamické DPI aplikace Windows Forms, naleznete v tématu [vysoké rozlišení DPI podporují ve Windows Forms](../winforms/high-dpi-support-in-windows-forms.md).

<a name="WPF47" />

#### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

WPF v rozhraní .NET Framework 4.7, zahrnuje následující vylepšení:

**Podpora dotykového ovládání/stylus zásobníku na základě zpráv Windows WM_POINTER**

Teď máte možnost používat dotykové ovládání/stylus zásobníku na základě [WM_POINTER zprávy](https://docs.microsoft.com/previous-versions/windows/desktop/InputMsg/messages) místo Windows Ink služby platformy (WISP). To je přihlašovaná funkce v rozhraní .NET Framework. Další informace najdete v tématu [změny mění se cílení v rozhraní .NET Framework 4.7](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md).

**Novou implementaci pro tisk přes rozhraní API pro WPF**

WPF v rozhraní API v tisku <xref:System.Printing.PrintQueue?displayProperty=nameWithType> třída volat Windows [tisk dokumentu balíčku rozhraní API](/windows/desktop/printdocs/tailored-app-printing-api) místo zastaralá [XPS tisk API](/windows/desktop/printdocs/xps-printing). Dopad této změny na kompatibilitu aplikací, najdete v části [změny mění se cílení v rozhraní .NET Framework 4.7](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md).

<a name="v462" />

## <a name="whats-new-in-the-net-framework-462"></a>Co je nového v rozhraní .NET Framework 4.6.2

[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] Obsahuje nové funkce v následujících oblastech:

- [ASP.NET](#ASPNET462)

- [Kategoriích znaků](#Strings)

- [Cryptography](#Crypto462)

- [SqlClient](#SQLClient)

- [Windows Communication Foundation](#WCF)

- [Windows Presentation Foundation (WPF)](#WPF462)

- [Windows Workflow Foundation (WF)](#WF462)

- [ClickOnce](#clickonce-1)

- [Převod Windows Forms a WPF aplikace na aplikacích pro UWP](#UWPConvert)

- [Vylepšení ladění](#Debug462)

Seznam nových rozhraní API přidá do rozhraní .NET Framework 4.6.2, najdete v části [změn rozhraní API .NET Framework 4.6.2](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-api-changes.md) na Githubu. Seznam vylepšení funkcí a oprav chyb v rozhraní .NET Framework 4.6.2, najdete v tématu [rozhraní .NET Framework 4.6.2 seznam změn](https://go.microsoft.com/fwlink/?LinkId=708778) na Githubu.  Další informace najdete v tématu [uvedení rozhraní .NET Framework 4.6.2](https://blogs.msdn.microsoft.com/dotnet/2016/08/02/announcing-net-framework-4-6-2/) v blogu .NET.

<a name="ASPNET462" />

### <a name="aspnet"></a>ASP.NET

V [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], technologie ASP.NET obsahuje následující vylepšení:

**Vylepšená podpora pro lokalizované chybové zprávy v validátory anotace dat**

Validátory anotace data umožňují provést ověření přidáním jednoho nebo více atributů k vlastnosti třídy. Atributu <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> element definuje text chybové zprávy, pokud se ověřování nezdaří. Počínaje [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], ASP.NET umožňuje snadno lokalizovat chybové zprávy. Pokud bude lokalizovaný chybové zprávy:

1.  <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> Je k dispozici v ověřovací atribut.

2.  Soubor prostředků je uložen ve složce App_LocalResources.

3.  Název souboru lokalizované prostředky má tvar `DataAnnotation.Localization.{` *název*`}.resx`, kde *název* je název jazykové verze ve formátu *languageCode* `-` *země/regionCode* nebo *languageCode*.

4.  Název klíče prostředku je řetězec přiřazený k <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> atribut a jeho hodnota je lokalizované chybové zprávy.

Například následující atribut anotace data definuje výchozí jazykovou verzi chybová zpráva pro neplatnou hodnocení.

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

Potom můžete vytvořit soubor prostředků DataAnnotation.Localization.fr.resx, jehož klíč je řetězec chybové zprávy a jehož hodnota je lokalizované chybové zprávy. Soubor musí být nalezen v `App.LocalResources` složky. Například následující je klíč a její hodnotu v lokalizovaných francouzština (fr) jazyka chybová zpráva:

| Název                                 | Hodnota                                     |
| ------------------------------------ | ----------------------------------------- |
| Hodnocení musí být mezi 1 a 10. | La note doit être comprise entre 1 et 10. |

 Kromě toho je rozšiřitelný lokalizační Poznámka data. Vývojářům můžete zařadit vlastní řetězec poskytovatele lokalizátora implementací <xref:System.Web.Globalization.IStringLocalizerProvider> rozhraní pro uložení řetězce lokalizace někde jinak než v souboru prostředků.

 **Podpora asynchronního s poskytovateli úložiště stavu relace**

 ASP.NET teď umožňuje použít s poskytovateli úložiště stavu relace, což aplikace v ASP.NET získáte výhody škálovatelnosti asynchronní metody vracející úlohy. Chcete podporuje asynchronní operace se stav relace ukládat poskytovatelů, technologie ASP.NET obsahuje nové rozhraní <xref:System.Web.SessionState.ISessionStateModule?displayProperty=nameWithType>, který dědí z <xref:System.Web.IHttpModule> a vývojářům umožňuje implementovat vlastní zprostředkovatele stavu relace modulu a asynchronní relace úložiště. Rozhraní je definovaná následujícím způsobem:

```csharp
public interface ISessionStateModule : IHttpModule {
    void ReleaseSessionState(HttpContext context);
    Task ReleaseSessionStateAsync(HttpContext context);
}
```

 Kromě toho <xref:System.Web.SessionState.SessionStateUtility> třída obsahuje dvě nové metody, <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateReadOnly%2A> a <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateRequired%2A>, který lze použít pro podporu asynchronních operací.

 **Podpora asynchronního pro zprostředkovatele výstupní mezipaměti**

 Počínaje [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], vracející úlohy můžete použít u metody zprostředkovatele výstupní mezipaměti zajistit škálovatelnost výhody asynchronní.  Poskytovatelé, které implementují tyto metody omezení blokování vlákna na webovém serveru a zlepšit škálovatelnost služby ASP.NET.

 Byly přidány následující rozhraní API pro podporu asynchronních zprostředkovatele výstupní mezipaměti:

- <xref:System.Web.Caching.OutputCacheProviderAsync?displayProperty=nameWithType> Třída, která dědí z <xref:System.Web.Caching.OutputCacheProvider?displayProperty=nameWithType> a vývojářům umožňuje implementovat asynchronní poskytovatel výstupní mezipaměti.

- <xref:System.Web.Caching.OutputCacheUtility> Třídu, která poskytuje pomocné metody pro konfiguraci do výstupní mezipaměti.

- 18 nové metody v <xref:System.Web.HttpCachePolicy?displayProperty=nameWithType> třídy. Patří mezi ně <xref:System.Web.HttpCachePolicy.GetCacheability%2A>, <xref:System.Web.HttpCachePolicy.GetCacheExtensions%2A>, <xref:System.Web.HttpCachePolicy.GetETag%2A>, <xref:System.Web.HttpCachePolicy.GetETagFromFileDependencies%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetNoStore%2A>, <xref:System.Web.HttpCachePolicy.GetNoTransforms%2A>, <xref:System.Web.HttpCachePolicy.GetOmitVaryStar%2A>, <xref:System.Web.HttpCachePolicy.GetProxyMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetRevalidation%2A>, <xref:System.Web.HttpCachePolicy.GetUtcLastModified%2A>, <xref:System.Web.HttpCachePolicy.GetVaryByCustom%2A>, <xref:System.Web.HttpCachePolicy.HasSlidingExpiration%2A>, a <xref:System.Web.HttpCachePolicy.IsValidUntilExpires%2A>.

- 2 nové metody v <xref:System.Web.HttpCacheVaryByContentEncodings?displayProperty=nameWithType> třídy: <xref:System.Web.HttpCacheVaryByContentEncodings.GetContentEncodings%2A> a <xref:System.Web.HttpCacheVaryByContentEncodings.SetContentEncodings%2A>.

- 2 nové metody v <xref:System.Web.HttpCacheVaryByHeaders?displayProperty=nameWithType> třídy: <xref:System.Web.HttpCacheVaryByHeaders.GetHeaders%2A> a <xref:System.Web.HttpCacheVaryByHeaders.SetHeaders%2A>.

- 2 nové metody v <xref:System.Web.HttpCacheVaryByParams?displayProperty=nameWithType> třídy: <xref:System.Web.HttpCacheVaryByParams.GetParams%2A> a <xref:System.Web.HttpCacheVaryByParams.SetParams%2A>.

- V <xref:System.Web.Caching.AggregateCacheDependency?displayProperty=nameWithType> třídy, <xref:System.Web.Caching.AggregateCacheDependency.GetFileDependencies%2A> metody.

- V <xref:System.Web.Caching.CacheDependency>, <xref:System.Web.Caching.CacheDependency.GetFileDependencies%2A> metody.

<a name="Strings" />

### <a name="character-categories"></a>Kategoriích znaků
 Znaky v [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] jsou klasifikovány podle [Unicode Standard, verze 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/). V [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] a [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], znaky byly klasifikovány podle kategorií znaků Unicode 6.3.

 Podpora pro Unicode 8.0 je omezena na klasifikaci znaků, o <xref:System.Globalization.CharUnicodeInfo> třídy a typy a metody, které jsou na něm závislí. Patří mezi ně <xref:System.Globalization.StringInfo> třídy přetížené <xref:System.Char.GetUnicodeCategory%2A?displayProperty=nameWithType> metody a [znaku třídy](../../../docs/standard/base-types/character-classes-in-regular-expressions.md) rozpoznávaných modul regulárních výrazů rozhraní .NET Framework.  Znakové a řetězcové porovnání a řazení není touto změnou ovlivněna a Spolehněte se na příslušný operační systém, nebo v systémech Windows 7, v rozhraní .NET Framework poskytuje znaková data i nadále.

 Změny v kategoriích znaků Unicode 6.0 do kódování Unicode 7.0, naleznete v tématu [standardu Unicode, verze 7.0.0](https://www.unicode.org/versions/Unicode7.0.0/) na webu Unicode Consortium. Změny z kódování Unicode 7.0 Unicode 8.0, naleznete v tématu [standardu Unicode, verze 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/) na webu Unicode Consortium.

<a name="Crypto462" />

### <a name="cryptography"></a>Cryptography

 **Podpora pro X509 certifikáty obsahující DSA FIPS 186 3**

 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] Přidává podporu pro certifikáty DSA (algoritmu Digital Signature Algorithm) X509 klíči překročit FIPS limit 1024 bitů 186-2.

 Kromě podpory větší velikostí klíče FIPS 186-3 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] umožňuje computingu signatury s řady SHA-2 hashovacích algoritmů (SHA256, SHA384 a SHA512). FIPS 186 3 poskytuje podporu nové <xref:System.Security.Cryptography.DSACng?displayProperty=nameWithType> třídy.

 V souladu s nedávných změn <xref:System.Security.Cryptography.RSA> třídu v rozhraní .NET Framework 4.6 a <xref:System.Security.Cryptography.ECDsa> třídy v rozhraní .NET Framework 4.6.1, <xref:System.Security.Cryptography.DSA> abstraktní základní třída v [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] má další metody, které umožňují volajícím použít funkce bez přetypování. Můžete volat <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey%2A?displayProperty=nameWithType> metodu rozšíření k podepisování dat, jak ukazuje následující příklad.

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

A je možné volat <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey%2A?displayProperty=nameWithType> metodu rozšíření k ověření podepsaná data, jak ukazuje následující příklad.

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

 **Lepší čitelnosti vstupů ECDiffieHellman odvození klíče rutin**

 Rozhraní .NET Framework 3.5 přidali podporu pro Ellipic křivky Diffie-Hellman klíč dohody s tři různé rutiny funkce odvození klíče (KDF). Vstupy pro rutiny a rutiny sami, byly nakonfigurovány pomocí vlastností na <xref:System.Security.Cryptography.ECDiffieHellmanCng> objektu. Ale protože ne každá rutina umožňuje číst vlastnost každý vstupní, byl dostatek místa pro nejasnosti v minulosti vývojáře.

 K vyřešení tohoto v [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], byly přidány následující tři metody do <xref:System.Security.Cryptography.ECDiffieHellman> základní třída pro větší přehlednost reprezentaci těchto rutin KDF a jejich vstupech:

|ECDiffieHellman – metoda|Popis|
|----------------------------|-----------------|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHash%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Odvozuje materiál klíče pomocí vzorce<br /><br /> Hodnota HASH (secretPrepend &#124; &#124; *x* &#124; &#124; secretAppend)<br /><br /> Hodnota HASH (secretPrepend OrElse *x* OrElse secretAppend)<br /><br /> kde *x* je vypočítaný výsledek algoritmu Diffie-Hellman ES.|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHmac%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Odvozuje materiál klíče pomocí vzorce<br /><br /> Metoda HMAC (hmacKey secretPrepend &#124; &#124; *x* &#124; &#124; secretAppend)<br /><br /> Metoda HMAC (hmacKey secretPrepend OrElse *x* OrElse secretAppend)<br /><br /> kde *x* je vypočítaný výsledek algoritmu Diffie-Hellman ES.|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyTls%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Je odvozena pomocí algoritmu TLS pseudonáhodné – funkce (PRF) odvození klíče.|

 **Podpora pro symetrické šifrování trvalé klíč**

 Knihovna šifrování Windows (CNG) přidali jsme podporu pro ukládání trvalých symetrické klíče a pomocí symetrické klíče uložené hardwaru a [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] mades pro vývojáře, aby bylo možné tuto funkci používat.  Pojem názvy klíčů a klíč zprostředkovatele je specifický pro implementaci, použití této funkce vyžaduje použití konstruktoru konkrétní implementaci typů namísto přístup upřednostňované objekt pro vytváření (například voláním `Aes.Create`).

 Podpora šifrování se symetrickým trvalé klíč existuje pro AES (<xref:System.Security.Cryptography.AesCng>) a algoritmus 3DES (<xref:System.Security.Cryptography.TripleDESCng>) algoritmy. Příklad:

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

 **Podpora SignedXml pro vytvoření hodnoty hash SHA-2**

 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] Přidává podporu pro <xref:System.Security.Cryptography.Xml.SignedXml> třídy pro RSA-SHA256, RSA SHA384 a RSA SHA512 PKCS č. 1 podpisu metody a SHA256, SHA384 a SHA512 odkaz algoritmus digest.

 Identifikátor URI konstanty jsou zveřejněné na <xref:System.Security.Cryptography.Xml.SignedXml>:

|SignedXml pole|Konstanta|
|---------------------|--------------|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA256Url>|"http://www.w3.org/2001/04/xmlenc#sha256"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA256Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha256"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA384Url>|"http://www.w3.org/2001/04/xmldsig-more#sha384"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA384Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha384"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA512Url>|"http://www.w3.org/2001/04/xmlenc#sha512"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA512Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha512"|

 Všechny programy, které jste zaregistrovali vlastní <xref:System.Security.Cryptography.SignatureDescription> obslužné rutiny do <xref:System.Security.Cryptography.CryptoConfig> přidat podporu pro tyto algoritmy budou i nadále fungovat, jak tomu bylo v minulosti, ale protože je nyní výchozí platformu, <xref:System.Security.Cryptography.CryptoConfig> registrace je už nezbytné.

<a name="SQLClient" />

### <a name="sqlclient"></a>SqlClient

 Zprostředkovatel dat .NET framework pro SQL Server (<xref:System.Data.SqlClient?displayProperty=nameWithType>) obsahuje následující nové funkce v [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]:

 **Sdružování připojení a časových limitů s databází Azure SQL**

 Když povoleno sdružování připojení a dojde k vypršení časového limitu nebo jiná chyba přihlášení, výjimka se uloží do mezipaměti a uložená v mezipaměti se výjimka při pokusu o jakékoli další připojení pro další 5 sekund až 1 minuty.  Další podrobnosti najdete v tématu [SQL sdružování připojení serveru (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md).

 Toto chování není žádoucí, při připojování ke službě Azure SQL Database, protože pokusy o připojení může selhat s přechodným chybám, které jsou obvykle rychle obnovit. Pro lepší optimalizaci prostředí opakovat připojení, období blokování připojení fondu, chování je odebrána, když dojde k selhání připojení k databázím SQL Azure.

 Přidání nového `PoolBlockingPeriod` – klíčové slovo umožňuje vyberte období blokování pro vaši aplikaci nejvhodnější. Mezi hodnoty patří:

`Auto`

Fond připojení blokování období pro aplikaci, která se připojuje ke službě Azure SQL Database je zakázaná a fond připojení blokování období pro aplikaci, která se připojuje k jiné instanci serveru SQL Server je povolen. Jedná se o výchozí hodnotu. Pokud název koncového bodu serveru skončí s žádným z následujících akcí, jsou považovány za Azure SQL Database:

- .database.windows.net

- .database.chinacloudapi.cn

- .database.usgovcloudapi.net

- .database.cloudapi.de

`AlwaysBlock`

V období blokování fondu připojení je vždy povolena.

`NeverBlock`

V období blokování fondu připojení je vždy zakázaná.

 **Vylepšení pro Always Encrypted**

 SQLClient zavádí dvě vylepšení pro Always Encrypted:

- Ke zlepšení výkonu parametrizované dotazy proti šifrovaného databázového sloupce, metadata šifrování pro parametry dotazu je nyní v mezipaměti. S <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled%2A?displayProperty=nameWithType> nastavenou na `true` (což je výchozí hodnota), pokud stejný dotaz je volána více než jednou, klient získá parametr metadata ze serveru pouze jednou.

- Sloupec šifrování klíče položky v mezipaměti klíče jsou nyní vyloučení po konfigurovat časový interval, nastavit pomocí <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionKeyCacheTtl%2A?displayProperty=nameWithType> vlastnost.

<a name="WCF" />

### <a name="windows-communication-foundation"></a>Windows Communication Foundation
 V [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], Windows Communication Foundation je vylepšená v následujících oblastech:

 **Podpora zabezpečení přenosu WCF pro certifikáty uložené, pomocí CNG**

 Zabezpečení přenosu WCF podporuje certifikátů uložených pomocí knihovny šifrování Windows (CNG). V [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], tato podpora je omezena na použití certifikátů s veřejným klíčem, který má v délka exponentu více než 32 bitů. Když aplikace cílena [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], tato funkce je ve výchozím.

 Pro aplikace, které se zaměřují [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] a starší ale jsou spuštěny na [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], tuto funkci je možné povolit tak, že přidáte následující řádek, který [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) část app.config nebo web.config soubor.

```xml
<AppContextSwitchOverrides
    value="Switch.System.ServiceModel.DisableCngCertificates=false"
/>
```

To je možné provést prostřednictvím kódu programu s kódem, jako je následující:

```csharp
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificates";
AppContext.SetSwitch(disableCngCertificates, false);
```

```vb
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"
AppContext.SetSwitch(disableCngCertificates, False)
```

 **Pomocí třídy DataContractJsonSerializer, lepší podpora pro více pravidel úpravy letního času**

 Zákazníci mohou používat nastavení konfigurace aplikace k určení, zda <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> třída podporuje víc úpravy pravidel pro jednoho časové pásmo. Toto je přihlašovaná funkce. Ho Pokud chcete povolit, přidejte do souboru app.config následující nastavení:

```xml
<runtime>
     <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseTimeZoneInfo=false" />
</runtime>
```

Pokud je tato funkce povolena, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> objektu používá <xref:System.TimeZoneInfo> zadejte místo <xref:System.TimeZone> typ k deserializaci data a času. <xref:System.TimeZoneInfo> podporuje víc úpravy pravidel, které umožňuje pracovat s daty historické časové pásmo;   <xref:System.TimeZone> tak není.

Další informace o <xref:System.TimeZoneInfo> strukturu a úpravy časového pásma, naleznete v tématu [Přehled časových pásem](../../../docs/standard/datetime/time-zone-overview.md).

**Nejlepší shoda NetNamedPipeBinding**

 WCF obsahuje nové nastavení aplikace, které lze nastavit pro klientské aplikace k zajištění, že se že vždy připojí ke službě naslouchání na identifikátoru URI, který nejlépe odpovídá ten, který vyžadují. Pomocí tohoto nastavení aplikace nastavte na `false` (výchozí), je možné pro klienty, kteří používají <xref:System.ServiceModel.NetNamedPipeBinding> pokus o připojení ke službě naslouchá na identifikátor URI, který je podřetězec požadovaný identifikátor URI.

 Například se klient pokusí připojit k služba naslouchá na `net.pipe://localhost/Service1`, ale jiné služby na tomto počítači spuštěna s oprávněním správce naslouchá na `net.pipe://localhost`. Pomocí tohoto nastavení aplikace nastavte na `false`, klient se pokusil připojit ke službě nesprávné. Po nastavení na hodnotu nastavení aplikace, které `true`, klient se vždy připojí k nejlépe odpovídající služby.

> [!NOTE]
> Klienti, kteří používají <xref:System.ServiceModel.NetNamedPipeBinding> nalezení služeb na základě základní adresa služby (pokud existuje) místo adresy úplné koncového bodu. Aby toto nastavení vždy funguje služba používali jedinečné základní adresa.

 Chcete-li tuto změnu, přidejte následující nastavení aplikace do souboru App.config nebo Web.config klientské aplikace:

```xml
<configuration>
    <appSettings>
        <add key="wcf:useBestMatchNamedPipeUri" value="true" />
    </appSettings>
</configuration>
```

 **Protokol SSL 3.0 není výchozím protokolem**

 Pokud používáte NetTcp k zabezpečení přenosů a přihlašovacích údajů typu certifikátu, SSL 3.0 už nejsou výchozí protokol použitý pro vyjednávání zabezpečeného připojení. Ve většině případů by měl existovat žádný vliv na stávající aplikace, protože protokol TLS 1.0 je obsažena v seznamu protokolů pro NetTcp. Všichni existující klienti měli být schopni vyjednat připojení pomocí na nejnižší TLS 1.0. Ssl3 je potřeba, použijte jednu z následujících mechanismů konfigurace se přidá do seznamu vyjednávaný protokolů.

- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=nameWithType> Vlastnost

- <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> Vlastnost

- [ \<Přenosu >](../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md) část [ \<netTcpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) oddílu

- [ \<SslStreamSecurity >](../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) část [ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) oddílu

<a name="WPF462" />

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)
 V [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], Windows Presentation Foundation je vylepšená v následujících oblastech:

 **Řazení skupin**

 Aplikace, která se používá <xref:System.Windows.Data.CollectionView> objektu k seskupení dat můžete teď explicitně deklarovat způsob řazení skupin. Explicitní řazení adres problému neintuitivním řazení dochází Pokud aplikace dynamicky přidá nebo odebere skupiny nebo při změně hodnoty vlastnosti položek, které jsou součástí seskupení. Můžete také zvýšit výkon samotného procesu vytvoření skupiny přesunutím porovnávání vlastností seskupení z řazení na plné kolekci řazení skupin.

 Pro podporu třídění skupiny nové <xref:System.ComponentModel.GroupDescription.SortDescriptions%2A?displayProperty=nameWithType> a <xref:System.ComponentModel.GroupDescription.CustomSort%2A?displayProperty=nameWithType> vlastnosti popisují způsob řazení kolekce skupin vytvářených <xref:System.ComponentModel.GroupDescription> objektu. To je obdobou identicky pojmenovanou způsob <xref:System.Windows.Data.ListCollectionView> vlastnosti popisují způsob řazení datových položek.

 Dvě nové statické vlastnosti <xref:System.Windows.Data.PropertyGroupDescription> třídy <xref:System.Windows.Data.PropertyGroupDescription.CompareNameAscending%2A> a <xref:System.Windows.Data.PropertyGroupDescription.CompareNameDescending%2A>, lze použít pro nejběžnější případy.

 Například následující data skupiny XAML podle věku, věkové skupiny ve vzestupném pořadí řazení a seskupte položky v rámci každé kategorie age group podle příjmení.

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

 **Podpora softwarová klávesnice**

 Softwarová klávesnice podpory umožňuje fokus v aplikacích WPF sledování automaticky vyvoláním a zavření nové softwarová klávesnice ve Windows 10, při přijetí vstup pomocí dotyku, jež může převzít textového vstupu ovládacím prvkem.

 V předchozích verzích rozhraní .NET Framework nemůže aplikace WPF optimalizované fokus sledování bez zakázání podpora gesta dotykového pera a dotykového ovládání WPF.  Aplikace WPF v důsledku toho musíte vybrat mezi plnou podporu dotykového ovládání WPF nebo Spolehněte se na podporu myši Windows.

 **DPI podle monitoru**

 Pro podporu poslední růst počtu vysokých hodnot DPI a DPI hybridní prostředí pro aplikace WPF, WPF v [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] umožňuje sledování na sledování. Zobrazit [ukázky a příručka pro vývojáře](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI) na Githubu pro další informace o tom, jak povolit aplikaci WPF se nastavení DPI podle monitoru.

 V předchozích verzích rozhraní .NET Framework jsou aplikace WPF systému – rozpoznání nastavení DPI. Jinými slovy uživatelského rozhraní aplikace se škálovat podle operačního systému podle potřeby, v závislosti na DPI monitorování, na kterém je vykreslen aplikace. , 

 Pro aplikace běžící v rámci [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], DPI za monitorování změn v aplikacích WPF můžete zakázat přidáním konfiguraci příkazu [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) část konfigurace aplikací souboru následujícím způsobem:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Windows.DoNotScaleForDpiChanges=false"/>
</runtime>
```

<a name="WF462" />

### <a name="windows-workflow-foundation-wf"></a>Windows Workflow Foundation (WF)
 V [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], vylepšili jsme Windows Workflow Foundation v následující oblasti:

 **Podpora pro výrazy jazyka C# a technologie IntelliSense v Návrháři Re-hosted WF**

 Počínaje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], WF podporuje výrazy jazyka C# v obou Návrhář Visual Studio a v pracovních postupech kódu. Návrháři pracovních postupů Re-hosted je klíčovou funkcí služby pracovního postupu, který umožňuje pro návrháře postupu provádění v aplikaci mimo sadu Visual Studio (například v WPF).  Windows Workflow Foundation umožňuje podporu v Návrháři pracovních postupů Re-hosted výrazy jazyka C# a technologii IntelliSense. Další informace najdete v tématu [blogu Windows Workflow Foundation](https://go.microsoft.com/fwlink/?LinkID=809042&clcid=0x409).

 `Availability of IntelliSense when a customer rebuilds a workflow project from Visual Studio` Ve verzích rozhraní .NET Framework starších než [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], když zákazník znovu sestaví projekt pracovního postupu ze sady Visual Studio nefunguje technologie IntelliSense Návrháře pracovního postupu. Při sestavení projektu je úspěšné, typy pracovních postupů nebyly nalezeny v návrháři, a upozornění z technologie IntelliSense pro chybějící typy pracovních postupů ve **seznam chyb** okna. [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] Řeší tento problém a zpřístupňuje technologii IntelliSense.

 **Spustit pracovní postup aplikace V1 sledování pracovního postupu na chvíli v režimu FIPS**

 Počítače s režimu dodržování standardů FIPS povolené teď můžete úspěšně spustit pracovní postup aplikace verze 1 – vizuální styl s pracovním postupem sledování. Pokud chcete povolit tento scénář, musíte udělat následující změny do souboru app.config:

```xml
<add key="microsoft:WorkflowRuntime:FIPSRequired" value="true" />
```

 Pokud v tomto scénáři není povolené, spuštění aplikace i nadále k vyvolání výjimky se zprávou "Tato implementace není součástí Windows Platform FIPS ověřit kryptografické algoritmy."

 **Vylepšení pracovního postupu při použití dynamické aktualizace se Návrhář postupu provádění Visual Studio**

 Návrháře postupu provádění, Návrhář aktivity FlowChart a jiné návrháře aktivit pracovního postupu teď úspěšně načíst a zobrazit pracovní postupy, které byly uloženy po volání <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> metody. Ve verzích rozhraní .NET Framework před [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], načtením souboru XAML v sadě Visual Studio pro pracovní postup, který byl uložen po volání <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> může vést k následujícím problémům:

- Návrháře postupu provádění nelze správně načíst soubor XAML (když <xref:System.Activities.Presentation.ViewState.ViewStateData.Id%2A?displayProperty=nameWithType> je na konci řádku).

- Návrhář aktivity flowchart nebo jiné návrháře aktivit pracovního postupu se může zobrazit všechny objekty do výchozího umístění na rozdíl od hodnoty připojené vlastnosti.


### <a name="clickonce"></a>ClickOnce

Aktualizovali jsme ClickOnce pro podporu protokolu TLS 1.1 a TLS 1.2 kromě 1.0 protokolu, která již podporuje. ClickOnce automaticky rozpozná, protokol, který se vyžaduje; žádné další kroky v rámci aplikace ClickOnce jsou požadovány pro povolení TLS 1.1 a 1.2 podpory.

<a name="UWPConvert" />

### <a name="converting-windows-forms-and-wpf-apps-to--uwp-apps"></a>Převod Windows Forms a WPF aplikace na aplikacích pro UWP
 Windows teď nabízí funkce pro používání stávající aplikace klasické pracovní plochy Windows, včetně aplikací pro WPF a Windows Forms, pro univerzální platformu Windows (UPW). Tato technologie funguje jako most tím, že můžete migrovat postupně svém stávajícím základu kódu pro UPW, a tím uvedení vaší aplikace na všech zařízeních s Windows 10.

 Převedené aplikace klasické pracovní plochy získat identitu aplikace podobné identity aplikace v aplikacích pro UWP, který zpřístupňuje rozhraní API pro UPW zprostředkují funkce jako živé dlaždice a oznámení. Aplikace i nadále chovat stejně jako předtím a spouští jako aplikace s úplným vztahem důvěryhodnosti. Po převedení aplikace kontejneru proces aplikací lze přidat k existující proces úplný vztah důvěryhodnosti pro přidání adaptivní uživatelské rozhraní. Při všechny funkce je přesunuta do procesu kontejnerů aplikací, proces úplný vztah důvěryhodnosti mohou být odstraněny a nové aplikace pro UPW, být k dispozici na všech zařízeních s Windows 10.

<a name="Debug462" />

### <a name="debugging-improvements"></a>Vylepšení ladění
 *Nespravované ladění v rozhraní API* v bylo vylepšeno [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] k další analýze při <xref:System.NullReferenceException> je vyvolána výjimka, aby bylo možné určit, které proměnné na jednom řádku zdrojového kódu je `null`.   Pro podporu tohoto scénáře, byly přidány následující rozhraní API pro spravované ladění rozhraní API.

- [Icordebugcode4 –](../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md), [icordebugvariablehome –](../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md), a [icordebugvariablehomeenum –](../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) rozhraní, které zpřístupňují nativní domovů spravované proměnné. To umožňuje ladicí programy chtít provést i analýzy toku kódu při <xref:System.NullReferenceException> dojde k a práci zpět k určení spravované proměnné, která odpovídá nativní umístění, která byla `null`.

- [ICorDebugType2::GetTypeID](../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) metoda poskytuje mapování pro ICorDebugType k [cor_typeid –](../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), umožňuje ladicího programu k získání [cor_typeid –](../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) bez instance z ICorDebugType. Stávající rozhraní API na [cor_typeid –](../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) lze použít k určení rozložení třídy typu.

<a name="v461" />

## <a name="whats-new-in-the-net-framework-461"></a>Co je nového v rozhraní .NET Framework 4.6.1

[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] Obsahuje nové funkce v následujících oblastech:

- [Cryptography](#Crypto)

- [ADO.NET](#ADO.NET461)

- [Windows Presentation Foundation (WPF)](#WPF461)

- [Windows Workflow Foundation](#WWF461)

- [Profilace](#Profile461)

- [NGen](#NGEN461)

Další informace o [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], naleznete v následujících tématech:

- [Seznam změn v rozhraní .NET Framework 4.6.1](https://go.microsoft.com/fwlink/?LinkId=622964)

- [Kompatibilita aplikací ve verzi 4.6.1](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)

- [Rozdíly v rozhraních na rozhraní .NET Framework API](https://go.microsoft.com/fwlink/?LinkId=622989) (na Githubu)

<a name="Crypto" />

### <a name="cryptography-support-for-x509-certificates-containing-ecdsa"></a>Kryptografie: Podpora pro X509 certifikáty ECDSA obsahující
 Rozhraní .NET Framework 4.6 přidání podpory RSACng X509 certifikáty. [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] Přidává podporu pro ECDSA (Elliptic Curve algoritmu Digital Signature Algorithm) X509 certifikáty.

 ECDSA nabízí lepší výkon a je bezpečnější algoritmus šifrování než RSA, poskytuje skvělou volbou kde zabezpečení TLS (Transport Layer) výkon a škálovatelnost se netýká. Implementace rozhraní .NET Framework zabalí volání do stávajících funkcí Windows.

 Následující příklad kódu ukazuje, jak snadné je a generuje podpis pro datový proud bajtů pomocí novou podporu pro ECDSA certifikátů X 509 součástí [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].

 [!code-csharp[whatsnew.461.crypto#1](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#1)]
 [!code-vb[whatsnew.461.crypto#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code461.vb#1)]

 To nabízí označené kontrast pro kód potřebný k vygenerování podpisu v rozhraní .NET Framework 4.6.

 [!code-csharp[whatsnew.461.crypto#2](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#2)]
 [!code-vb[whatsnew.461.crypto#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code46.vb#2)]

<a name="ADO.NET461" />

### <a name="adonet"></a>ADO.NET
 Následující jsou přidané do ADO.NET:

**Always Encrypted podporu pro hardware chráněných klíčů**

 ADO.NET teď podporuje ukládání s funkcí Always Encrypted sloupec hlavního klíče nativně v modulech hardwarového zabezpečení (HSM). Díky této podpoře zákazníci můžou využívat asymetrických klíčů uložených v modulech hardwarového zabezpečení bez nutnosti psát vlastní sloupec hlavní klíč úložiště poskytovatele a zaregistrovat je v aplikacích.

 Zákazníkům musíte nainstalovat poskytovatele CSP poskytnutých dodavatelem modulu hardwarového zabezpečení nebo zprostředkovatelé úložiště klíčů CNG na serverech aplikace nebo klientské počítače za účelem přístupu k s funkcí Always Encrypted data chráněná pomocí hlavních klíčů sloupce uložené v modulu HSM.

 **Vylepšené <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> chování připojení AlwaysOn**

SqlClient teď automaticky poskytuje rychlejší připojení do dostupnosti skupiny (skupina dostupnosti AlwaysOn). Transparentně zjišťuje, zda vaše aplikace se připojuje ke skupině dostupnosti AlwaysOn (AG) v jiné podsíti a rychle zjistí aktuální aktivní server a poskytuje připojení k serveru. Před touto verzí musel nastavíme připojovací řetězec, který chcete zahrnout aplikace `"MultisubnetFailover=true"` k označení, že se připojuje ke skupině dostupnosti AlwaysOn. Bez nastavení připojení – klíčové slovo `true`, aplikace může dojít k vypršení časového limitu při připojování ke skupině dostupnosti AlwaysOn. V této vydané verzi, aplikace provede *není* potřeba nastavit <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> k `true` zobrazovat. Další informace o podpora klienta SqlClient pro skupiny dostupnosti Always On najdete v tématu [podpora klienta SqlClient pro vysokou dostupnost, zotavení po havárii](../../../docs/framework/data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md).

<a name="WPF461" />

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)
 Windows Presentation Foundation obsahuje několik vylepšení a změny.

 **Vylepšení výkonu**

 Zpoždění při aktivaci touch událostí chyba byla opravena v [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]. Kromě toho, že zadáte <xref:System.Windows.Controls.RichTextBox> ovládací prvek již blokuje rendrovacím vlákně během rychlý vstup.

 **Vylepšení kontroly pravopisu**

 Nástroj pro kontrolu pravopisu v subsystému WPF se aktualizovala na Windows 8.1 a novější verze operačního systému využívat podporu pro kontrolu pravopisu další jazyky.  Není žádná změna v funkce na verze Windows starší než Windows 8.1.

 Stejně jako v předchozích verzích rozhraní .NET Framework, jazyk <xref:System.Windows.Controls.TextBox> řídit ora <xref:System.Windows.Controls.RichTextBox> bloku se zjistil tím, že hledají informace v tomto pořadí:

- `xml:lang`, pokud je k dispozici.

- Aktuální jazyk.

- Aktuální jazyková verze vlákna.

 Další informace o podpoře jazyků v subsystému WPF naleznete v tématu [WPF blogový příspěvek o funkcích rozhraní .NET Framework 4.6.1](https://go.microsoft.com/fwlink/?LinkID=691819).

 **Další podporu pro vlastní slovníky jednotlivých uživatelů**

 V [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], WPF rozpozná vlastní slovníky, které jsou registrovány globálně. Tato možnost je k dispozici kromě možnost zaregistrovat na ovládací prvek.

 V předchozích verzích WPF vlastní slovníky nebyl rozpoznán vyloučené slova a automaticky opravovat seznamy. Jsou podporované ve Windows 8.1 a Windows 10 pomocí souborů, které mohou být umístěny pod `%AppData%\Microsoft\Spelling\<language tag>` adresáře.  K těmto souborům platí následující pravidla:

- Soubory by měly mít rozšíření DIC (pro přidání slov), .exc (pro vyloučení slov) nebo ACL (pro automatické opravy).

- Soubory musí být UTF-16 LE ve formátu prostého textu, který se spustí značky pořadí bajtů (BOM).

- Každý řádek by měl obsahovat slova (v seznamech přidání a vyloučených word), nebo dvojici automatických oprav se slovy oddělené symbolem svislá čára ("&#124;") (v seznamu automaticky opravovat slova).

- Tyto soubory jsou považovány za jen pro čtení a nezmění v systému.

> [!NOTE]
> Tyto nové formáty souborů nejsou přímo podporované rozhraní API pro kontrolu pravopisu WPF a vlastní slovníky zadaný pro WPF aplikace by měla dál používat .lex soubory.

**Ukázky**

 Existuje mnoho vzorků WPF na [/WPF – ukázky Microsoft](https://github.com/Microsoft/WPF-Samples) úložiště GitHub. Pomozte nám vylepšit naše ukázky odesláním žádosti o přijetí změn nebo otevírání [problém Githubu](https://github.com/Microsoft/WPF-Samples/issues).

 **Rozšíření rozhraní DirectX**

 Zahrnuje WPF [balíček NuGet](https://go.microsoft.com/fwlink/?LinkID=691342) , který poskytuje nové implementace <xref:System.Windows.Interop.D3DImage> to usnadní vám pro spolupráci s DX10 a Dx11 obsahu. Kód pro tento balíček byl open source a je k dispozici [na Githubu](https://github.com/Microsoft/WPFDXInterop).

<a name="WWF461" />

### <a name="windows-workflow-foundation-transactions"></a>Windows Workflow Foundation: Transakce
 <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> Metoda teď můžete použít Správce distribuovaných transakcí než MSDTC zvýšit úroveň transakce. To provedete tak, že zadáte identifikátor GUID transakce promoter k novému <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> přetížení. Pokud je tato operace úspěšná, existují omezení možnosti transakce. Jakmile je zapsán promoter transakce-služby MSDTC, následující metody vyvolání <xref:System.Transactions.TransactionPromotionException> protože povýšení MSDTC, požadují tyto metody:

- <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetDtcTransaction%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetExportCookie%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetTransmitterPropagationToken%2A?displayProperty=nameWithType>

 Jakmile promoter transakce – služba MSDTC je zapsán, se musí použít pro budoucí trvalý zařazení pomocí protokolů, které definuje. <xref:System.Guid> Transakce promoter můžete získat pomocí <xref:System.Transactions.Transaction.PromoterType%2A> vlastnost. Když transakce podporuje poskytuje promoter transakce <xref:System.Byte> pole, které představuje přesunutá token. Aplikaci můžete získat přesunutá token pro jiné MSDTC povýšen transakce s <xref:System.Transactions.Transaction.GetPromotedToken%2A> metody.

 Uživatelé nového <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> přetížení musí následovat volání konkrétní pořadí, v pořadí pro operaci povýšení úspěšné dokončení. Tato pravidla jsou popsaná v dokumentaci k metody.

<a name="Profile461" />

### <a name="profiling"></a>Profilace

Nespravované rozhraní API profilování bylo vylepšeno následujícím způsobem:

- Lepší podpora pro přístup k PDB v [icorprofilerinfo7 –](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md) rozhraní.

   V ASP.NET Core je stále mnohem běžnější pro sestavení zkompilované v paměti podle Roslyn. Pro vývojáře a nástroje pro profilaci to znamená, že soubory PDB, které byly v minulosti serializovat na disk nemusí být k dispozici. Profiler nástroje často používají soubory PDB pro mapování kódu zpět do zdrojové řádky pro úlohy, jako je například analýza výkonu pokrytí nebo řádek po řádku kódu. [Icorprofilerinfo7 –](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md) rozhraní teď obsahuje dvě nové metody, [ICorProfilerInfo7::GetInMemorySymbolsLength](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md) a [ICorProfilerInfo7::ReadInMemorySymbols](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md) , tyto nástroje profiler poskytnout přístup k datům PDB v paměti, s využitím nových rozhraní API, profiler může získat obsah souboru PDB v paměti jako bajtové pole a potom ji zpracovat nebo ho serializovat na disk.

- Lepší instrumentace ICorProfiler rozhraní.

   Profilovací programy, které používáte `ICorProfiler` ReJit funkce rozhraní API pro dynamické instrumentace nyní můžete upravit některá metadata. Dříve by mohl tyto nástroje instrumentace IL kdykoli, ale metadata můžou upravovat jenom v okamžiku načtení modulu. Protože IL odkazuje na metadata, to omezené druhy instrumentaci, která se nedala provést. Budeme mít některé z těchto omezení zrušeno tak, že přidáte [ICorProfilerInfo7::ApplyMetaData](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md) do podmnožinu úpravy metadat po tento modul se načte, konkrétně tak, že přidáte nové metody `AssemblyRef`, `TypeRef`, `TypeSpec`, `MemberRef`, `MemberSpec`, a `UserString` záznamy. Tato změna umožňuje mnohem širší rozsah o průběžné instrumentace.

<a name="NGEN461" />

### <a name="native-image-generator-ngen-pdbs"></a>Nativní bitové kopie (NGEN) generátor soubory PDB
 Trasování událostí mezi počítači umožňuje zákazníkům programu na počítači A profilu a pohled na data profilace se mapování řádku zdroje na počítači B. pomocí předchozí verze rozhraní .NET Framework, uživatel by kopírovat všech modulů a nativní bitové kopie profilovaných stroj analýzy počítači, který obsahuje IL souborem PDB můžete vytvářet zdrojový nativní mapování. Během tohoto procesu může fungovat dobře, když jsou relativně malé, například pro telefonní aplikace soubory, soubory můžou být hodně velké na desktopové systémy a nevyžadují spoustu času ke kopírování.

 U souborů PDB pro Ngen můžete vytvořit NGen souboru PDB, který obsahuje mapování IL na nativní bez závislosti na IL PDB. V tomto scénáři trasování událostí mezi počítači vše, co je potřeba je zkopírovat nativní bitové kopie souboru PDB, který je generován A počítač do počítači B a použití [ladění rozhraní API přístup](/visualstudio/debugger/debug-interface-access/debug-interface-access-sdk-reference) číst mapování zdroje IL IL PDB a nativní Image IL na nativní mapování pro PDB. Kombinace obou mapování poskytuje zdroj nativní mapování. Protože nativní bitové kopie souboru PDB je mnohem menší, než všechny moduly a nativní bitové kopie, proces kopírování z počítače A počítač b je mnohem rychlejší.

<a name="v46" />

## <a name="whats-new-in-net-2015"></a>Co je nového v .NET 2015
 Představuje .NET 2015 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] a .NET Core. Některé nové funkce, platit pro oboje, a další funkce jsou specifické pro [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] nebo [!INCLUDE[net_core](../../../includes/net-core-md.md)].

- **ASP.NET Core**

     .NET 2015 zahrnuje ASP.NET Core, která je Štíhlá implementace .NET pro vytváření moderních cloudových aplikací. ASP.NET Core je modulární, takže může obsahovat pouze funkce, které jsou potřeba ve vaší aplikaci. Může být hostovaná ve službě IIS nebo ve vlastním procesu v místním prostředí a na stejném serveru můžete spouštět aplikace s různými verzemi rozhraní .NET Framework. Zahrnuje nové prostředí konfigurace systému, který je určený pro nasazení v cloudu.

     Webové stránky, MVC a webového rozhraní API jsou sjednocené do jednoho rámec volá MVC 6. ASP.NET Core můžete vytvářet aplikace pomocí nástrojů v sadě Visual Studio 2015 nebo novější. Vaše stávající aplikace budou fungovat na nové rozhraní .NET Framework; ale sestavit aplikaci, která používá MVC 6 nebo SignalR 3, musíte použít systém projektu v sadě Visual Studio 2015 nebo novější.

     Informace najdete v tématu [ASP.NET Core](/aspnet/core/).

- **Aktualizace technologie ASP.NET**

    - **Asynchronní odpověď spotřeby založený na úlohách rozhraní API**

         Technologie ASP.NET nyní poskytuje jednoduché rozhraní API založené na úlohách pro vyčištění asynchronní odpověď <xref:System.Web.HttpResponse.FlushAsync%2A?displayProperty=nameWithType>, odpovědi asynchronně zapsány pomocí váš jazyk, který umožňuje `async/await` podporovat.

    - **Vazby modelu podporuje metody vracející úlohy**

         V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], ASP.NET přidali funkci vazby modelu, umožňující přístup operace s daty založených na přístupu CRUD v stránky webových formulářů a uživatelských ovládacích prvků, který rozšiřitelné, zaměřuje kódu. Vazby modelu systém nyní podporuje <xref:System.Threading.Tasks.Task>-vrácení metody vazby modelu. Tato funkce umožňuje vývojářům webových formulářů výhody škálovatelnosti asynchronní snadné datové vazby systému při použití novější verze ORMs, včetně rozhraní Entity Framework.

         Asynchronní vazby modelu je řízen `aspnet:EnableAsyncModelBinding` nastavení konfigurace.

        ```xml
        <appSettings>
           <add key=" aspnet:EnableAsyncModelBinding" value="true|false" />
        </appSettings>
        ```

         V aplikacích cíle [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], použije se výchozí `true`. Na aplikace běžící na [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] , který cílí na starší verzi rozhraní .NET Framework, je `false` ve výchozím nastavení. To se dá nastavit tak, že nastavíte konfigurační nastavení `true`.

    - **Podpora HTTP/2 (Windows 10)**

         [HTTP/2](https://www.wikipedia.org/wiki/HTTP/2) novou verzi protokolu HTTP, která poskytuje mnohem lepší využití připojení (méně doby odezvy mezi klientem a serverem), výsledkem nižší latencí na webové stránce načítání pro uživatele.  Webové stránky (na rozdíl od služby) využívat na maximum z HTTP/2, protože protokol optimalizuje pro více artefakty, které jsou požadovány v rámci prostředí s jednotným. Byla přidána podpora HTTP/2 technologie ASP.NET v rozhraní .NET Framework 4.6. Protože síťových funkcí existuje na více úrovních, nové funkce byly zapotřebí ve Windows, služby IIS a ASP.NET umožňuje HTTP/2. Musí běžet na Windows 10 pomocí protokolu HTTP/2 technologie ASP.NET.

         HTTP/2 je také podporováno a na ve výchozím nastavení pro Windows 10 Universal Windows Platform (UWP) aplikace, které používají <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> rozhraní API.

         Aby bylo možné poskytnout způsob, jak používat [PUSH_PROMISE](https://http2.github.io/http2-spec/#PUSH_PROMISE) funkce v aplikacích ASP.NET, novou metodu s dvě přetížení, <xref:System.Web.HttpResponse.PushPromise%28System.String%29> a <xref:System.Web.HttpResponse.PushPromise%28System.String%2CSystem.String%2CSystem.Collections.Specialized.NameValueCollection%29>, byl přidán do <xref:System.Web.HttpResponse> třídy.

        > [!NOTE]
        > I když ASP.NET Core podporuje HTTP/2, podpora pro funkce nabízené PROMISE ještě nejsou přidané.

         Všechnu práci udělat v prohlížeči a webový server (IIS na Windows). Nemusíte dělat žádné náročná na výkon nepoužily pro vaše uživatele.

         Většina [nejpoužívanějších prohlížečích podporuje HTTP/2](https://www.wikipedia.org/wiki/HTTP/2), takže je pravděpodobné, že vaši uživatelé budou těžit z podpora HTTP/2, pokud to server podporuje.

    - **Podpora pro protokol vazby tokenů**

         Microsoft a Google, se spolupráce, na nový přístup k ověřování, volá se, [tokenu vazby protokolu](https://github.com/TokenBinding/Internet-Drafts). Předpokládá se, že ověřovací tokeny (v mezipaměti prohlížeče) můžete vám ho někdo ukradne a používá zločinci do jinak zabezpečeného přístupu k prostředkům (třeba vaše bankovním účtu) bez nutnosti heslo nebo jiné privilegovaných znalostní báze. Cílem je nový protokol ke zmírnění tohoto problému.

         Token vazby protokolu se ve Windows 10 implementované jako funkce prohlížeči. Aplikace ASP.NET se bude podílet na protokol, tak, že ověřovací tokeny jsou ověřeny jako legitimní. Klient a server implementace navázat na začátku do konce ochranu zadaný protokol.

    - **Náhodná řetězec hashovacích algoritmů**

         Rozhraní .NET Framework 4.5 zavedené [náhodného řetězce hashovací algoritmus](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md). Ale není podporované technologií ASP.NET kvůli některé technologie ASP.NET funkce závisí na stabilní hodnotu hash. V [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], náhodného řetězce hashovací algoritmy jsou nyní podporovány. Chcete-li tuto funkci povolit, použijte `aspnet:UseRandomizedStringHashAlgorithm` nastavení konfigurace.

        ```xml
        <appSettings>
           <add key="aspnet:UseRandomizedStringHashAlgorithm" value="true|false" />
        </appSettings>
        ```

- **ADO.NET**

     ADO .NET teď podporuje funkci Always Encrypted dostupnou v SQL Server 2016 Community Technology Preview 2 (CTP2). S funkcí Always Encrypted systému SQL Server můžete provádět operace na šifrovaných dat a nejlepší šifrovacího klíče se nachází v důvěryhodném prostředí zákazníka a ne na serveru aplikace. Vždy šifrovaný zabezpečuje zákaznická data, kteří datoví analytici nebudou mít přístup k datům ve formátu prostého textu. Šifrování a dešifrování dat se transparentně odehrává na úrovni ovladač, minimalizace změny, které se mají provést, stávající aplikace. Podrobnosti najdete v tématu [(databázový stroj) s funkcí Always Encrypted](/sql/relational-databases/security/encryption/always-encrypted-database-engine) a [(vývoj pro klientské) s funkcí Always Encrypted](/sql/relational-databases/security/encryption/always-encrypted-client-development).

- **64bitový kompilátor JIT pro spravovaný kód**

     Rozhraní .NET Framework 4.6 obsahuje novou verzi 64bitového kompilátoru JIT (původně s dřívějším kódovým komponentách RyuJIT). Nový 64bitový kompilátor nabízí výrazné zlepšení výkonu v porovnání s starší 64bitovým kompilátorem JIT. Nový 64bitový kompilátor je povolený pro 64bitové procesy spuštěné na rozhraní .NET Framework 4.6. Vaše aplikace poběží v 64bitový proces, pokud je kompilován jako 64-bit nebo AnyCPU a běží na 64bitový operační systém. Zatímco k přechodu na nový kompilátor co nejtransparentnější se věnovat pozornost, jsou změny v chování je to možné. Rádi se dozvíme o problémech při používání nového kompilátoru JIT došlo k přímo. Kontaktujte nás prostřednictvím [Microsoft Connect](https://connect.microsoft.com/) Pokud narazíte na problém, který může souviset s nového 64bitového kompilátoru JIT.

     Nový 64bitový kompilátor JIT také zahrnuje SIMD funkce hardwarové akcelerace při spolu s podporou SIMD typy v <xref:System.Numerics> obor názvů, který může přinést vylepšení dobrého výkonu.

- **Vylepšení zavaděče sestavení**

     Zavaděč sestavení teď využívá efektivněji uvolňuje sestavení IL paměť, po zavedení odpovídající image NGEN. Tato změna snižuje využití virtuální paměti, což je obzvlášť přínosné pro velké 32bitové aplikace (jako je Visual Studio) a šetří taky fyzickou paměť.

- **Změny knihovny základních tříd**

     Mnoho nových rozhraní API se přidaly kolem k [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] umožňující klíčové scénáře. Patří mezi ně následující změny a přídavky:

    - **IReadOnlyCollection\<T > Implementace**

         Další kolekce implementovat <xref:System.Collections.Generic.IReadOnlyCollection%601> například <xref:System.Collections.Generic.Queue%601> a <xref:System.Collections.Generic.Stack%601>.

    - **CultureInfo.CurrentCulture a CultureInfo.CurrentUICulture**

         <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> a <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> vlastnosti jsou teď pro čtení i zápis, spíše než jen pro čtení. Pokud přiřadíte nové <xref:System.Globalization.CultureInfo> objekt má tyto vlastnosti aktuální jazykové verzi vlákna určené `Thread.CurrentThread.CurrentCulture` určené jazykové verze vlákna vlastnost a aktuálního uživatelského rozhraní `Thread.CurrentThread.CurrentUICulture` také změnit vlastnosti.

    - **Vylepšení uvolňování paměti (GC)**

         <xref:System.GC> Třída nyní zahrnuje <xref:System.GC.TryStartNoGCRegion%2A> a <xref:System.GC.EndNoGCRegion%2A> metody, které umožňují zakázat uvolňování paměti během provádění kritickou cestu.

         O nové přetížení <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%2CSystem.Boolean%29?displayProperty=nameWithType> metoda umožňuje řídit, jestli haldy malých objektů a haldy pro velké objekty, jež jsou a komprimovat nebo pouze, jež.

    - **Typy s podporou SIMD**

         <xref:System.Numerics> Obor názvů, jako teď zahrnuje celou řadu typů podporou SIMD <xref:System.Numerics.Matrix3x2>, <xref:System.Numerics.Matrix4x4>, <xref:System.Numerics.Plane>, <xref:System.Numerics.Quaternion>, <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, a <xref:System.Numerics.Vector4>.

         Nový 64bitový kompilátor JIT také zahrnuje funkce hardwarové akcelerace SIMD, a proto existují zejména výrazné zlepšení výkonu při použití typů podporou SIMD s nového 64bitového kompilátoru JIT.

    - **Aktualizace kryptografie**

         <xref:System.Security.Cryptography?displayProperty=nameWithType> Rozhraní API je právě aktualizována o podporu [kryptografie Windows CNG API](/windows/desktop/SecCNG/cng-reference). Předchozí verze rozhraní .NET Framework mají spoléhal na zcela [starší verzi rozhraní API pro šifrování Windows](/windows/desktop/SecCrypto/cryptography-portal) jako základ pro <xref:System.Security.Cryptography?displayProperty=nameWithType> implementace. Jsme měli žádosti o podporu rozhraní API CNG, protože ji podporuje [moderní kryptografické algoritmy](/windows/desktop/SecCNG/cng-features#suite-b-support), které jsou důležité pro určité kategorie aplikací.

         Rozhraní .NET Framework 4.6 obsahuje následující nová vylepšení pro podporu kryptografie Windows CNG rozhraní API:

        - Sadu rozšiřujících metod pro X509 certifikáty, `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` a `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)`, které vrací na základě CNG implementace spíše než na základě CAPI implementace, pokud je to možné. (Některé čipové karty atd., stále vyžadují CAPI a rozhraní API pro zpracování na náhradní řešení).

        - <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> Třídu, která poskytuje implementaci CNG algoritmus RSA.

        - Vylepšení rozhraní API RSA tak, aby běžné akce už nevyžadují přetypování. Například na šifrování dat pomocí <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> objektu vyžaduje kód následujícím postupem v předchozích verzích rozhraní .NET Framework.

             [!code-csharp[WhatsNew.Casting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#1)]
             [!code-vb[WhatsNew.Casting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#1)]

             Kód, který využívá šifrování nové rozhraní API v rozhraní .NET Framework 4.6 může být přepsán následujícím způsobem, aby se zabránilo přetypování.

             [!code-csharp[WhatsNew.Casting#2](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#2)]
             [!code-vb[WhatsNew.Casting#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#2)]

    - **Podpora pro převod data a časy na Unixový čas nebo z**

         Byly přidány následující nové metody pro <xref:System.DateTimeOffset> struktury, které podporují převod hodnoty data a času na Unixový čas nebo z:

        - <xref:System.DateTimeOffset.FromUnixTimeSeconds%2A?displayProperty=nameWithType>

        - <xref:System.DateTimeOffset.FromUnixTimeMilliseconds%2A?displayProperty=nameWithType>

        - <xref:System.DateTimeOffset.ToUnixTimeSeconds%2A?displayProperty=nameWithType>

        - <xref:System.DateTimeOffset.ToUnixTimeMilliseconds%2A?displayProperty=nameWithType>

    - **Přepínače kompatibility**

         Nové <xref:System.AppContext> třídy přidá nové funkce kompatibility, která umožňuje autorům knihovny poskytovat jednotné odhlášení mechanismus pro nové funkce pro své uživatele. Určuje kontrakt volně spárované mezi součástmi, chcete-li komunikovat požadavek výslovného nesouhlasu s. Tato funkce je obvykle důležité při změně stávajících funkcí. Naopak již existuje implicitní vyjádřit výslovný souhlas pro nové funkce.

         S <xref:System.AppContext>, definujete knihovny a zpřístupňují přepínače kompatibility, při kód, který závisí na nich můžete nastavit tyto přepínače ovlivnit chování knihovny. Ve výchozím nastavení, knihovny přinášejí nové funkce a upravují pouze (to znamená, poskytují funkce pro předchozí) Pokud přepínač nastavený.

         Aplikace (nebo knihovny) můžete deklarovat hodnotu přepínače (což je vždy <xref:System.Boolean> hodnota), který definuje závislé knihovny. Přepínač je vždy implicitně `false`. Nastavíte přepínač na `true` povolí ho. Explicitním nastavením přepínač na `false` poskytuje nové chování.

        ```csharp
        AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", true);
        ```

         Knihovny musí zjistí, jestli příjemce je deklarovaný hodnota přepínače a odpovídajícím způsobem reagovat na něj.

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
           else {
              // new code
           }
        }
        ```

         Je vhodné použít konzistentní formát pro přepínače, protože jsou formální smlouvu vystavené knihovny. Tady jsou dvě zřejmé formátů.

        - *Přepínač*. *obor názvů*.*switchName*

        - *Přepínač*. *Knihovna*.*switchName*

    - **Změny asynchronního zpracování (TAP) založené na úlohách**

         Pro aplikace, které cílí [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> objekty dědí jazykové verze a jazykové verze uživatelského rozhraní volajícího vlákna. Chování aplikací, které cílí na předchozí verze rozhraní .NET Framework nebo, který sdělení nebudete cílit na konkrétní verzi rozhraní .NET Framework, je to neovlivní. Další informace najdete v části "Jazyková verze a úkolově orientovanou asynchronní operace" <xref:System.Globalization.CultureInfo> třídě.

         <xref:System.Threading.AsyncLocal%601?displayProperty=nameWithType> Třída umožňuje znázornění okolí dat, jako je místní pro danou asynchronní řízení toku `async` metoda. Slouží k uchovávání dat napříč vlákny. Můžete také definovat metodu zpětného volání, která obdrží oznámení pokaždé, když se změní data okolí, buď protože <xref:System.Threading.AsyncLocal%601.Value%2A?displayProperty=nameWithType> explicitně byla změněna vlastnost, nebo protože vlákna došlo k přechodu kontextu.

         Tři metody pohodlí <xref:System.Threading.Tasks.Task.CompletedTask%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.FromCanceled%2A?displayProperty=nameWithType>, a <xref:System.Threading.Tasks.Task.FromException%2A?displayProperty=nameWithType>, byly přidány na základě úlohy asynchronního zpracování (TAP) k vrácení dokončených úloh v určitém stavu.

         <xref:System.IO.Pipes.NamedPipeClientStream> Třída nyní podporuje asynchronní komunikaci pomocí svého nového <xref:System.IO.Pipes.NamedPipeClientStream.ConnectAsync%2A>. Metoda.

    - **EventSource se teď podporuje zápis do protokolu událostí**

         Teď můžete použít <xref:System.Diagnostics.Tracing.EventSource> třídy do protokolu administrativních nebo provozních zpráv do protokolu událostí, kromě toho pro všechny existující relace trasování událostí pro Windows na počítači. V minulosti jste měli použít balíček Microsoft.Diagnostics.Tracing.EventSource NuGet pro tuto funkci. Tato funkce je teď integrovaná do rozhraní .NET Framework 4.6.

         Balíček NuGet a rozhraní .NET Framework 4.6 se aktualizovaly s následujícími funkcemi:

        - **Dynamické události**

             Umožňuje událostí, které jsou definovány "průběžně", bez vytváření metody událostí.

        - **Bohaté datové části**

             Umožňuje speciálně s atributy třídy a pole, stejně jako primitivní typy, které mají být předány jako datovou část

        - **Sledování aktivit**

             Způsobí, že spouštění a zastavování událostí k událostem značky mezi nimi s ID, který reprezentuje všechny aktuálně aktivní aktivity.

         Pro podporu tyto funkce, přetížené <xref:System.Diagnostics.Tracing.EventSource.Write%2A> metoda byl přidán do <xref:System.Diagnostics.Tracing.EventSource> třídy.

- **Windows Presentation Foundation (WPF)**

    - **HDPI vylepšení**

         Podpora HDPI ve WPF je teď lepší v [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]. Změny byly provedeny na rozložení zaokrouhluje se směrem snížit instance výstřižek v ovládacích prvcích s ohraničením. Ve výchozím nastavení, tato funkce je povolena pouze v případě vaší <xref:System.Runtime.Versioning.TargetFrameworkAttribute> je nastavena na rozhraní .NET 4.6.  Aplikace, které jsou cíleny na starší verze rozhraní Framework, ale jsou spuštěny na [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] můžete přejít k nové chování tak, že přidáte následující řádek, který [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) část souboru app.config:

        ```xml
        <AppContextSwitchOverrides
        value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false"
        />
        ```

         WPF windows tažných více monitorů s jiným nastavením DPI (Instalační program s více hodnot DPI) jsou nyní úplně vykreslit bez blacked mimo oblasti. Toto chování můžete zrušit tak, že přidáte následující řádek, který `<appSettings>` část souboru app.config pro toto chování zakázat:

        ```xml
        <add key="EnableMultiMonitorDisplayClipping" value="true"/>
        ```

         Podpora pro automatické načítání kurzor vpravo na základě nastavení DPI byl přidán do <xref:System.Windows.Input.Cursor?displayProperty=nameWithType>.

    - **Je lepší dotykové ovládání**

         Zprávy zákazníků o [připojit](https://connect.microsoft.com/VisualStudio/feedback/details/903760/) touch, který vytváří nepředvídatelné chování se mluví ve [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]. Dvojitým klepnutím prahová hodnota pro aplikace Windows Store a aplikace WPF je teď stejný ve Windows 8.1 a vyšší.

    - **Podpora transparentní podřízených oken**

         Použití rozhraní WPF v [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] podporuje transparentní podřízená okna ve Windows 8.1 a novější. To umožňuje vytvoření průhledných a neobdélníkových podřízených oken v systému windows. nejvyšší úrovně. Můžete povolit tuto funkci tak, že nastavíte <xref:System.Windows.Interop.HwndSourceParameters.UsesPerPixelTransparency%2A?displayProperty=nameWithType> vlastnost `true`.

- **Windows Communication Foundation (WCF)**

    - **Podpora protokolu SSL**

         WCF teď podporuje SSL verzi TLS 1.1 a TLS 1.2, kromě SSL 3.0 a TLS 1.0, když používáte NetTcp ověřování zabezpečení a klient přenosu. Nyní je možné vybrat protokol, který použití nebo zakažte staré protokoly nižší úrovně zabezpečení. To můžete udělat buď tak, že nastavíte <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A> vlastnost nebo přidáním následujícího kódu do konfiguračního souboru.

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

    - **Odesílání zpráv s použitím různých připojení prostřednictvím protokolu HTTP**

         WCF teď umožňuje uživatelům Ujistěte se, že jsou některé zprávy odesílané pomocí jiné základní připojení protokolu HTTP. Toto lze provést dvěma způsoby:

        - **Pomocí předpony názvu skupiny připojení**

             Uživatelé mohou zadat řetězec, který WCF se použije jako předpona pro název skupiny připojení. Dvě zprávy s různými předponami se posílají pomocí jiné základní připojení protokolu HTTP. Nastavte předponu přidáním dvojice klíč/hodnota do zprávy <xref:System.ServiceModel.Channels.Message.Properties%2A?displayProperty=nameWithType> vlastnost. Klíč je "HttpTransportConnectionGroupNamePrefix"; hodnota je požadovanou předponu.

        - **Použití objektů pro vytváření různých kanálů**

             Uživatele můžete také povolit funkci, která zajistí, že zprávy odesílané pomocí kanály vytvořené objekty pro vytváření jiný kanál použije různé základní připojení protokolu HTTP. Na tuto funkci povolit, musí uživatelé nastavit následující `appSetting` k `true`:

            ```xml
            <appSettings>
               <add key="wcf:httpTransportBinding:useUniqueConnectionPoolPerFactory" value="true" />
            </appSettings>
            ```

- **Windows Workflow Foundation (WWF)**

     Nyní můžete zadat počet sekund, po které služby pracovního postupu bude blokovat požadavek operation mimo pořadí po nevyřízené záložky "bez protokolu" před vypršením časového limitu požadavku. "Bez protokolu" Záložka je záložku, která nesouvisí se zbývající aktivity Receive. Některé aktivity vytváření záložek bez protokolu v rámci jejich implementace, proto nemusí být zřejmé, že existuje záložku bez protokolu. Patří mezi ně stavu a vybrat. Takže pokud máte služby pracovního postupu implementovaná pomocí stavového stroje nebo obsahující aktivitě Pick, budete pravděpodobně máte záložek bez protokolu. Zadejte interval, tak, že přidáte řádek podobný následujícího `appSettings` části souboru app.config:

    ```xml
    <add key="microsoft:WorkflowServices:FilterResumeTimeoutInSeconds" value="60"/>
    ```

     Výchozí hodnota je 60 sekund. Pokud `value` je nastavena na hodnotu 0, mimo pořadí požadavky byly zamítnuty okamžitě se chyba s textem, který vypadá takto:

    ```
    Operation 'Request3|{http://tempuri.org/}IService' on service instance with identifier '2b0667b6-09c8-4093-9d02-f6c67d534292' cannot be performed at this time. Please ensure that the operations are performed in the correct order and that the binding in use provides ordered delivery guarantees.
    ```

     Toto je stejná zpráva, která se zobrazí, pokud neobdrží zprávu mimo pořadí operace a neexistují žádné záložky bez protokolu.

     Pokud hodnota `FilterResumeTimeoutInSeconds` element je nenulová, existují záložek bez protokolu a časový limit vyprší, operace selže se zprávou časový limit.

- **Transakce**

     Teď může obsahovat identifikátor distribuované transakce pro transakce, která způsobila výjimku odvozenou od <xref:System.Transactions.TransactionException> vyvolání. To provedete tak, že přidáte následující klíč `appSettings` části souboru app.config:

    ```xml
    <add key="Transactions:IncludeDistributedTransactionIdInExceptionMessage" value="true"/>
    ```

     Výchozí hodnota je `false`.

- **Sítě**

    - **Opětovné použití soketů**

         Windows 10 obsahuje nový algoritmus vysokou škálovatelnost sítě, který umožňuje lepší využití prostředků počítače opětovným použitím místní porty pro odchozí připojení TCP. Rozhraní .NET Framework 4.6 podporuje nový algoritmus povolení aplikace .NET, abyste mohli využívat nové chování. V předchozích verzích Windows bylo umělé souběžných připojení limitu (obvykle 16384, výchozí velikost rozsah dynamických portů), který může omezit škálovatelnost služby způsobením vyčerpání portů při zátěži.

         V [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], dvě nová rozhraní API se přidaly do umožňují opakované použití portu, což účinně odstraní 64 kB omezení souběžných připojení:

        - <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> Hodnota výčtu.

        - <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> Vlastnost.

         Ve výchozím nastavení <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> vlastnost `false` není-li `HWRPortReuseOnSocketBind` hodnotu `HKLM\SOFTWARE\Microsoft\.NETFramework\v4.0.30319` klíč registru je nastavené na 0x1. Chcete-li povolit opakované použití místního portu na připojení prostřednictvím protokolu HTTP, nastavte <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> vlastnost `true`. To způsobí, že všechny odchozí připojení TCP soketu z <xref:System.Net.Http.HttpClient> a <xref:System.Net.HttpWebRequest> používat novou možnost soketu Windows 10, [SO_REUSE_UNICASTPORT](/windows/desktop/WinSock/sol-socket-socket-options), umožňující opětovné použití místní port.

         Můžete zadat vývojáře, kteří vytvářejí aplikace pouze pro sokety <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> při volání metody, jako možnost <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> odchozí sockets použít místní porty během vazby.

    - **Podpora mezinárodních názvů domén a kódování PunyCode**

         Nové vlastnosti <xref:System.Uri.IdnHost%2A>, byl přidán do <xref:System.Uri> třídy pro zajištění lepší podpory mezinárodních názvů domén a kódování PunyCode.

- **Změna velikosti v ovládacích prvcích Windows Forms.**

     Tato funkce rozbalen v [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] zahrnout <xref:System.Windows.Forms.DomainUpDown>, <xref:System.Windows.Forms.NumericUpDown>, <xref:System.Windows.Forms.DataGridViewComboBoxColumn>, <xref:System.Windows.Forms.DataGridViewColumn> a <xref:System.Windows.Forms.ToolStripSplitButton> typy a obdélník určené <xref:System.Drawing.Design.PaintValueEventArgs.Bounds%2A> vlastnost použitou při kreslení <xref:System.Drawing.Design.UITypeEditor> .

     Toto je přihlašovaná funkce. Ji Pokud chcete povolit, nastavte `EnableWindowsFormsHighDpiAutoResizing` elementu `true` v souboru konfigurace (app.config) aplikace:

    ```xml
    <appSettings>
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
    </appSettings>
    ```

- **Podpora kódování znakových stránek**

     [!INCLUDE[net_core](../../../includes/net-core-md.md)] primárně podporuje kódování Unicode a ve výchozím nastavení poskytuje omezenou podporu pro kódování znakových stránek. Můžete přidat podporu pro kódování znakových stránek v rozhraní .NET Framework, ale nepodporuje je k dispozici [!INCLUDE[net_core](../../../includes/net-core-md.md)] zaregistrováním kódování znakových stránek s <xref:System.Text.Encoding.RegisterProvider%2A?displayProperty=nameWithType> metody. Další informace naleznete v tématu <xref:System.Text.CodePagesEncodingProvider?displayProperty=nameWithType>.

- **.NET Native**

     Aplikace Windows pro Windows 10, které se zaměřují [!INCLUDE[net_core](../../../includes/net-core-md.md)] a jsou napsané v C# nebo Visual Basic můžete využívat nové technologie, která sestavuje aplikace do nativního kódu, nikoli IL. Vytvářejí charakteristické rychlejší spouštění a časy spuštění aplikace. Další informace najdete v tématu [kompilování aplikací pomocí .NET Native](../../../docs/framework/net-native/index.md). Přehled rozhraní .NET Native, který zkoumá, jak se liší od kompilace JIT a NGEN a tom, jak to znamená, že pro váš kód, naleznete v tématu [.NET Native a kompilace](../../../docs/framework/net-native/net-native-and-compilation.md).

     Vaše aplikace se kompilují do nativního kódu ve výchozím nastavení při jejich kompilaci pomocí sady Visual Studio 2015 nebo novější. Další informace najdete v tématu [Začínáme s .NET Native](../../../docs/framework/net-native/getting-started-with-net-native.md).

     Počet nových rozhraní a výčty byly přidány pro podporu ladění aplikací .NET Native, nespravované ladění rozhraní API. Další informace najdete v tématu [ladění (referenční dokumentace nespravovaného rozhraní API)](../../../docs/framework/unmanaged-api/debugging/index.md) tématu.

- **Open sourcové balíčky rozhraní .NET Framework**

     Balíčků .NET core, jako jsou neměnné kolekce [SIMD API](https://go.microsoft.com/fwlink/?LinkID=518639), a například síťové rozhraní API najdete v <xref:System.Net.Http> obor názvů jsou teď k dispozici jako opensourcových balíčků na [Githubu](https://github.com/). Chcete-li přistupovat ke kódu, přečtěte si téma [CoreFx na Githubu](https://github.com/dotnet/corefx). Další informace a jak přispívat na těchto balíčků naleznete v tématu [.NET Core a Open Source](../../../docs/framework/get-started/net-core-and-open-source.md), [.NET domovskou stránku na Githubu](https://github.com/dotnet/home).

 [Zpět na začátek](#introduction)

<a name="v452" />

## <a name="whats-new-in-the-net-framework-452"></a>Co je nového v .NET Frameworku 4.5.2

- **Nová rozhraní API pro aplikace ASP.NET.** Nové <xref:System.Web.HttpResponse.AddOnSendingHeaders%2A?displayProperty=nameWithType> a <xref:System.Web.HttpResponseBase.AddOnSendingHeaders%2A?displayProperty=nameWithType> metody umožňují kontrolovat a upravovat hlavičky odpovědi a stavový kód jako odpověď se vyprázdní do klientské aplikace. Zvažte použití těchto metod namísto <xref:System.Web.HttpApplication.PreSendRequestHeaders> a <xref:System.Web.HttpApplication.PreSendRequestContent> události jsou efektivní a spolehlivá.

     <xref:System.Web.Hosting.HostingEnvironment.QueueBackgroundWorkItem%2A?displayProperty=nameWithType> Metoda umožňuje naplánovat malé na pozadí pracovní položky. ASP.NET sleduje tyto položky a zabrání až do dokončení všech pracovních položek na pozadí bezodkladně ukončuje pracovní proces služby IIS. Tuto metodu nelze volat mimo doménu spravovanou aplikaci ASP.NET.

     Nové <xref:System.Web.HttpResponse.HeadersWritten?displayProperty=nameWithType> a <xref:System.Web.HttpResponseBase.HeadersWritten?displayProperty=nameWithType> vlastnosti vrací logické hodnoty označující, zda bylo zapsáno hlavičky odpovědi. Můžete použít tyto vlastnosti abyste měli jistotu, která volá rozhraní API, jako <xref:System.Web.HttpResponse.StatusCode%2A?displayProperty=nameWithType> (který vyvolat výjimky, pokud byla zapsána záhlaví) proběhne úspěšně.

- **Změna velikosti v ovládacích prvcích Windows Forms.** Tato funkce byla rozšířena. Nyní můžete nastavení DPI systému Změna velikosti součástí tyto doplňkové ovládací prvky (například šipku rozevíracího seznamu v polích se seznamem):

    - <xref:System.Windows.Forms.ComboBox>
    - <xref:System.Windows.Forms.ToolStripComboBox>
    - <xref:System.Windows.Forms.ToolStripMenuItem>
    - <xref:System.Windows.Forms.Cursor>
    - <xref:System.Windows.Forms.DataGridView>
    - <xref:System.Windows.Forms.DataGridViewComboBoxColumn>

     Toto je přihlašovaná funkce. Ji Pokud chcete povolit, nastavte `EnableWindowsFormsHighDpiAutoResizing` elementu `true` v souboru konfigurace (app.config) aplikace:

    ```xml
    <appSettings>
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
    </appSettings>
    ```

- **Nová funkce pracovního postupu.** Resource Manageru, která používá <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> – metoda (a tedy implementace <xref:System.Transactions.IPromotableSinglePhaseNotification> rozhraní) můžete použít novou <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> metoda požádat o následující:

    - Zvýšit úroveň transakce na transakci Microsoft distribuované transakce koordinátor (MSDTC).

    - Nahraďte <xref:System.Transactions.IPromotableSinglePhaseNotification> s <xref:System.Transactions.ISinglePhaseNotification>, což je trvalý zařazení, která podporuje jedna fáze potvrzení.

     To lze provést v rámci stejné aplikační doméně a nevyžaduje žádné další nespravovaného kódu pro interakci s MSDTC k provedení povýšení. Novou metodu lze volat pouze v případě, že je počet volání z <xref:System.Transactions?displayProperty=nameWithType> k <xref:System.Transactions.IPromotableSinglePhaseNotification> `Promote` metodu, která je implementována pomocí zařazení možné zařazení.

- **Vylepšení profilování.** Následující nové nespravované profilování rozhraní API poskytuje robustnější profilování:

    - [COR_PRF_ASSEMBLY_REFERENCE_INFO – struktura](../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)
    - [COR_PRF_HIGH_MONITOR – výčet](../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)
    - [GetAssemblyReferences – metoda](../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
    - [GetEventMask2 – metoda](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
    - [SetEventMask2 – metoda](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
    - [AddAssemblyReference – metoda](../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)

     Předchozí `ICorProfiler` implementace nepodporuje opožděné načtení závislých sestavení. Nová rozhraní API profilování vyžaduje závislá sestavení, které jsou vloženy možné načíst okamžitě, místo po kompletní inicializaci aplikace načítání profileru. Tato změna nemá vliv na stávající uživatelé `ICorProfiler` rozhraní API.

- **Vylepšení ladění.** Následující nové nespravované ladění rozhraní API poskytuje lepší integraci s profiler. Je možné teď přístup metadata tak, že profiler i lokálních proměnných a kódu vložen vytvářených kompilátoru ReJIT požadavky při vypsat ladění.

    - [SetWriteableMetadataUpdateMode – metoda](../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)
    - [EnumerateLocalVariablesEx – metoda](../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)
    - [GetLocalVariableEx – metoda](../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)
    - [GetCodeEx – metoda](../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)
    - [GetActiveReJitRequestILCode – metoda](../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)
    - [GetInstrumentedILMap – metoda](../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)

- **Událost sledování změn.** Rozhraní .NET Framework 4.5.2 umožňuje trasování mimo proces, na základě Event Tracing for Windows ETW aktivit pro větší plochu povrchu. To umožňuje dodavatelům rozšířené Power Management (APM) poskytuje jednoduché nástroje, které lépe sledovat náklady na jednotlivé požadavky a aktivity, které překračují vlákna.  Tyto události jsou vyvolány pouze v případě, že je; povolit řadiče trasování událostí pro Windows změny proto neovlivní doposud zapsán trasování událostí pro Windows kód nebo kód, který běží s trasování událostí pro Windows, které jsou zakázané.

- **Zvyšuje se úroveň transakce a jeho převodu do trvalý zařazení**

     <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> nové rozhraní API doplňuje rozhraní .NET Framework 4.5.2 a 4.6:

    ```csharp
    [System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]
    public Enlistment PromoteAndEnlistDurable(Guid resourceManagerIdentifier,
                                              IPromotableSinglePhaseNotification promotableNotification,
                                              ISinglePhaseNotification enlistmentNotification,
                                              EnlistmentOptions enlistmentOptions)
    ```

     Metoda může být používán zařazení, který byl dříve vytvořen <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> v reakci <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> metoda. Požádá `System.Transactions` zvýšit úroveň transakce na transakci MSDTC a "převést" zařazení možné zařazení trvalý zařazení. Po úspěšném dokončení této metody <xref:System.Transactions.IPromotableSinglePhaseNotification> rozhraní bude odkazovat už `System.Transactions`, a všechny budoucí oznámení budou doručeny v zadaných <xref:System.Transactions.ISinglePhaseNotification> rozhraní. Zařazení dotyčný musí fungovat jako trvalý zařazení, podporu protokolování transakce a obnovení. Odkazovat na <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType> podrobnosti. Kromě toho musí podporovat zařazení <xref:System.Transactions.ISinglePhaseNotification>.  Tato metoda může *pouze* volat během zpracování <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> volání. Pokud to není případ, <xref:System.Transactions.TransactionException> je vyvolána výjimka.

 [Zpět na začátek](#introduction)

<a name="v451" />

## <a name="whats-new-in-the-net-framework-451"></a>Co je nového v rozhraní .NET Framework 4.5.1
 **Duben 2014 aktualizuje**:

- [Visual Studio 2013 Update 2](https://go.microsoft.com/fwlink/p/?LinkId=393658) obsahuje aktualizace šablony přenosné knihovny tříd pro podporu těchto scénářů:

    - Můžete použít rozhraní API Windows Runtime v přenosných knihovnách, které se zaměřují na Windows 8.1, Windows Phone 8.1 a Windows Phone Silverlight 8.1.

    - Můžete zahrnout XAML (Windows.UI.XAML typy) v přenosných knihovnách při cílení na Windows 8.1 nebo Windows Phone 8.1. Podporují se následující šablony XAML:  Prázdná stránka, slovník prostředků, ovládací prvek bez vizuálního vzhledu a uživatelský ovládací prvek.

    - Přenosné součást prostředí Windows Runtime (soubor .winmd) můžete vytvořit pro použití v aplikacích pro Store, které se zaměřují na Windows 8.1 a Windows Phone 8.1.

    - Windows Store nebo Windows Phone Store knihovny tříd jako jsou přenosné knihovny tříd můžete změnit cíl.

     Další informace o těchto změnách najdete v tématu [přenosné knihovny tříd](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).

- Rozhraní .NET Framework obsahu, teď obsahuje dokumentaci pro [!INCLUDE[net_native](../../../includes/net-native-md.md)], což je technologie předkompilace pro sestavování a nasazování aplikací pro Windows. [!INCLUDE[net_native](../../../includes/net-native-md.md)] své aplikace přímo do nativního kódu namísto (IL intermediate language), zkompiluje pro vyšší výkon. Podrobnosti najdete v tématu [kompilování aplikací pomocí .NET Native](../../../docs/framework/net-native/index.md).

- [Referenční zdroje rozhraní .NET Framework](https://referencesource.microsoft.com/) poskytuje nové možnosti procházení a vylepšené funkce. Můžete nyní procházet zdrojový kód rozhraní .NET Framework online, [stáhnout odkaz](https://referencesource.microsoft.com/download.html) pro prohlížení v režimu offline a procházení zdroje (včetně oprav a aktualizací) během ladění. Další informace najdete v příspěvku na blogu [nový vzhled pro zdroj odkazu .NET](https://blogs.msdn.microsoft.com/dotnet/2014/02/24/a-new-look-for-net-reference-source/).

 Hlavní nové vlastnosti a vylepšení v rozhraní .NET Framework 4.5.1 zahrnují:

- Automatické přesměrování vazby pro sestavení. Od verze Visual Studio 2013, pokud kompilujete aplikace, která se zaměřuje [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], přesměrování vazby může být přidáno do konfiguračního souboru aplikace Pokud vaše aplikace nebo její součásti odkazují na více verzí stejného sestavení. Můžete také povolit tuto funkci pro projekty, které jsou cíleny na starší verze rozhraní .NET Framework. Další informace najdete v tématu [jak: Povolení a zákaz automatického přesměrování vazby](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md).

- Schopnost shromažďovat diagnostické informace umožňující vývojářům zvyšovat výkon serverových a cloudových aplikací. Další informace najdete v tématu <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityId%2A> a <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityIdCore%2A> metody v <xref:System.Diagnostics.Tracing.EventSource> třídy.

- Schopnost explicitně komprimovat haldy pro velké objekty (LOH) během uvolnění paměti. Další informace najdete v tématu <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> vlastnost.

- Další výkonnostní zlepšení, jako je například pozastavení aplikace technologie ASP.NET, vylepšení vícejádrové JIT a rychlejší spuštění aplikace po rozhraní .NET Framework aktualizovat. Podrobnosti najdete v tématu [oznámení .NET Framework 4.5.1](https://blogs.msdn.microsoft.com/dotnet/2013/06/26/announcing-the-net-framework-4-5-1-preview/) a [pozastavení aplikace technologie ASP.NET](https://blogs.msdn.microsoft.com/dotnet/2013/10/09/asp-net-app-suspend-responsive-shared-net-web-hosting/) blogový příspěvek.

 Vylepšení formuláře Windows zahrnují:

- Změna velikosti v ovládacích prvcích Windows Forms. Nastavení hodnoty DPI systému můžete použít ke změně velikosti součásti ovládacích prvků (například ikon, které se zobrazí v mřížce vlastností) že vyjádří svůj pomocí položky v konfiguračním souboru aplikace (app.config) pro vaši aplikaci. Tato funkce je aktuálně podporovaná v následujících ovládacích prvků Windows Forms:

    - <xref:System.Windows.Forms.PropertyGrid>
    - <xref:System.Windows.Forms.TreeView>
    - Některé aspekty <xref:System.Windows.Forms.DataGridView> (viz [nové funkce ve verzi 4.5.2](#v452) další ovládací prvky, které jsou podporovány)

     Chcete-li tuto funkci povolit, přidejte novou \<appSettings > element do konfiguračního souboru (app.config) a nastavte `EnableWindowsFormsHighDpiAutoResizing` elementu `true`:

    ```xml
    <appSettings>
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
    </appSettings>
    ```

 Vylepšení při ladění aplikací rozhraní .NET Framework v sadě Visual Studio 2013 zahrnují:

- Návratové hodnoty v ladicím programu sady Visual Studio. Při ladění spravované aplikace v sadě Visual Studio 2013, zobrazí okno Automatické hodnoty návratové typy a hodnoty pro metody. Tyto informace jsou k dispozici pro desktop, Windows Store a aplikací Windows Phone. Další informace najdete v tématu [Kontrola návratových hodnot volání metod](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/dn32325728%v=vs.120%29).

- Upravit a pokračovat pro 64bitové aplikace. Visual Studio 2013 podporuje funkce upravit a pokračovat pro 64bitové spravované aplikace pro desktop, Windows Store a Windows Phone. Stávající omezení zůstávají v platnosti pro 32bitové a 64bitové aplikace (viz poslední část [podporované změny kódu (C#)](/visualstudio/debugger/supported-code-changes-csharp) článku).

- Asynchronní ladění. Chcete-li snadněji ladit asynchronní aplikace v sadě Visual Studio 2013, zásobník volání skryje kód infrastruktury poskytovaný kompilátory, aby podporoval asynchronní programování a také zřetězený v logicky nadřízených snímcích, takže můžete postupovat podle logického program spuštění více jasně. Okno úlohy nahrazuje okno paralelní úkoly a zobrazuje úlohy, které se týkají konkrétní zarážky a také zobrazuje všechny úkoly, které jsou aktuálně aktivní nebo plánované v aplikaci. Může číst informace o této funkci v části "asynchronní ladění" [oznámení .NET Framework 4.5.1](https://blogs.msdn.microsoft.com/dotnet/2013/06/26/announcing-the-net-framework-4-5-1-preview/).

- Lepší podpora výjimek součásti prostředí Windows Runtime. V [!INCLUDE[win81](../../../includes/win81-md.md)], výjimky, které vznikají v aplikacích pro Windows Store, uchovávají informace o chybě, která způsobila výjimku, i přes jazykové hranice. Může číst informace o této funkci v části "Vývoj aplikací pro Windows Store" [oznámení .NET Framework 4.5.1](https://blogs.msdn.microsoft.com/dotnet/2013/06/26/announcing-the-net-framework-4-5-1-preview/).

 Od verze Visual Studio 2013, můžete použít [profilu nástroj Optimalizace řízený spravovanými (Mpgo.exe)](../../../docs/framework/tools/mpgo-exe-managed-profile-guided-optimization-tool.md) optimalizovat [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikací, jakož i aplikace klasické pracovní plochy.

 Nové funkce v technologii ASP.NET 4.5.1 naleznete v tématu [ASP.NET and Web Tools pro Visual Studio 2013 – poznámky k](/aspnet/visual-studio/overview/2013/release-notes).

 [Zpět na začátek](#introduction)

<a name="v45" />

## <a name="whats-new-in-the-net-framework-45"></a>Co je nového v rozhraní .NET Framework 4.5

### <a name="core-new-features-and-improvements"></a>Hlavní nové vlastnosti a vylepšení

- Schopnost systému pro redukci restartuje pomocí detekce a zavření aplikací rozhraní .NET Framework 4 během nasazení. Zobrazit [omezení restartů systému při instalaci rozhraní .NET Framework 4.5](../../../docs/framework/deployment/reducing-system-restarts.md).

- Podpora pro pole, které jsou větší než 2 gigabajty (GB) na 64bitových platformách. Tuto funkci je možné povolit v konfiguračním souboru aplikace. Naleznete v tématu [ \<gcAllowVeryLargeObjects > element](../../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md), které jsou uvedeny také další omezení velikosti objektu a velikost pole.

- Lepší výkon pomocí sběru plýtvání na pozadí pro servery. Při použití v uvolňování paměti serveru [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], uvolňování paměti na pozadí je automaticky povolen. Najdete v části uvolňování paměti serveru na pozadí [základy kolekce paměti](../../../docs/standard/garbage-collection/fundamentals.md) tématu.

- Kompilace just-in-time (JIT) na pozadí, která je volitelně k dispozici také u vícejádrových procesorů pro zvýšení výkonu aplikací. Viz <xref:System.Runtime.ProfileOptimization>.

- Možnost omezit jak dlouho modul regulárních výrazů se pokusí o překlad regulárního výrazu před uplynutím časového limitu. Zobrazit <xref:System.Text.RegularExpressions.Regex.MatchTimeout%2A?displayProperty=nameWithType> vlastnost.

- Možnost definovat výchozí kulturu pro doménu aplikace. Zobrazit <xref:System.Globalization.CultureInfo> třídy.

- Podpora konzoly pro kódování Unicode (UTF-16). Zobrazit <xref:System.Console> třídy.

- Podpora verzního objednávání kultury řetězce a porovnávání dat. Zobrazit <xref:System.Globalization.SortVersion> třídy.

- Lepšího výkonu při načítání prostředků. Zobrazit [zabalení a nasazení prostředků](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).

- Vylepšení komprese ZIP ke zmenšení velikosti komprimovaného souboru. Zobrazit <xref:System.IO.Compression?displayProperty=nameWithType> oboru názvů.

- Možnost přizpůsobit kontext odrazu, aby potlačil výchozí chování odrazu prostřednictvím <xref:System.Reflection.Context.CustomReflectionContext> třídy.

- Podpora mezinárodních názvů domén v aplikacích (IDNA) verze 2008 standard při <xref:System.Globalization.IdnMapping?displayProperty=nameWithType> třída se používá na [!INCLUDE[win8](../../../includes/win8-md.md)].

- Delegování porovnání řetězců pro operační systém, který implementuje znakovou sadu Unicode 6.0 při použití rozhraní .NET Framework na [!INCLUDE[win8](../../../includes/win8-md.md)]. Při spuštění na jiných platformách, rozhraní .NET Framework obsahuje vlastní řetězec porovnání dat, který implementuje Unicode 5.x. Najdete v článku <xref:System.String> třídy a části poznámky <xref:System.Globalization.SortVersion> třídy.

- Možnost spočítat hodnoty hash pro řetězce na základě domény aplikace. Zobrazit [ \<UseRandomizedStringHashAlgorithm > Element](../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).

- Podpora reflexe typů byla rozdělena mezi <xref:System.Type> a <xref:System.Reflection.TypeInfo> třídy. Zobrazit [reflexe v rozhraní .NET Framework pro aplikace Windows Store](../../../docs/framework/reflection-and-codedom/reflection-for-windows-store-apps.md).

### <a name="managed-extensibility-framework-mef"></a>Managed Extensibility Framework (MEF)
 V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], Managed Extensibility Framework (MEF) obsahuje následující nové funkce:

- Podpora pro obecné typy.

- Podle úmluvy programovací model, který umožňuje vytvořit části podle konvence pojmenování, nikoli atributů.

- Více rozsahů.

- Podmnožina MEF, který vám pomůže při vytváření [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace. Tato podmnožina je k dispozici jako [balíčku ke stažení](https://go.microsoft.com/fwlink/?LinkId=256238) v galerii NuGet. K instalaci balíčku, otevřete projekt v sadě Visual Studio, zvolte **spravovat balíčky NuGet** z **projektu** nabídky a Hledat online `Microsoft.Composition` balíčku.

 Další informace najdete v tématu [Managed Extensibility Framework (MEF)](../../../docs/framework/mef/index.md).

### <a name="asynchronous-file-operations"></a>Asynchronní operace se soubory
 V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], byly přidány nové asynchronní funkce k jazykům C# a Visual Basic. Tyto funkce přidají modelu provádění asynchronních operací založené na úlohách. Pokud chcete použít tento nový model, použijte asynchronní metody v vstupně-výstupních tříd. Zobrazit [vstupně-výstupní asynchronní](../../../docs/standard/io/asynchronous-file-i-o.md).

<a name="tools" />

### <a name="tools"></a>Nástroje
 V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], Resource File Generator (Resgen.exe) umožňuje vytvořit soubor .resw pro použití v [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] vložené aplikace ze souboru .resources v sestavení rozhraní .NET Framework. Další informace najdete v tématu [Resgen.exe (Generátor zdrojových souborů)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md).

 Optimalizace řízená spravovanými profily (Mpgo.exe) umožňuje zlepšit dobu spuštění aplikace, využití paměti (velikost pracovní sady) a propustnost optimalizací sestavení nativních bitových kopií. Nástroj příkazového řádku generuje data profilu pro sestavení aplikací nativních bitových kopií. Zobrazit [Mpgo.exe (nástroj pro optimalizaci na základě spravovaného profilu)](../../../docs/framework/tools/mpgo-exe-managed-profile-guided-optimization-tool.md). Od verze Visual Studio 2013, můžete použít Mpgo.exe k optimalizaci [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikací, jakož i aplikace klasické pracovní plochy.

<a name="parallel" />

### <a name="parallel-computing"></a>Paralelní výpočty
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Nabízí několik nových funkcí a vylepšení pro paralelní výpočty. Patří mezi ně lepší výkon, lepší kontrolu, vylepšenou podporu pro asynchronní programování, nové knihovny datového toku a vylepšenou podporu pro paralelní analýzy ladění a výkonu. Viz položka [co je nového u paralelismu v rozhraní .NET 4.5](https://go.microsoft.com/fwlink/?LinkId=235061) v paralelním programování v blogu .NET.

<a name="web" />

### <a name="web"></a>Web

ASP.NET 4.5 a 4.5.1 přidá vazby modelu webových formulářů, podporu WebSocket, asynchronní obslužné rutiny, vylepšení výkonu a mnoho dalších funkcí. Další informace naleznete v následujících materiálech:

- [ASP.NET 4.5 a Visual Studio 2012](https://docs.microsoft.com/previous-versions/aspnet/hh420390(v=vs.110))

- [ASP.NET a webové nástroje pro Visual Studio 2013 – poznámky k verzi](/aspnet/visual-studio/overview/2013/release-notes)

### <a name="networking-a-namenetworking-"></a>Sítě <a name="networking" />

[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Poskytuje nové programovací rozhraní pro aplikace HTTP. Další informace najdete v tématu nové <xref:System.Net.Http?displayProperty=nameWithType> a <xref:System.Net.Http.Headers?displayProperty=nameWithType> obory názvů.

Podpora je součástí nového programovacího rozhraní pro přijímání a interakci s připojením WebSocket pomocí stávající <xref:System.Net.HttpListener> a související třídy. Další informace najdete v tématu nové <xref:System.Net.WebSockets> obor názvů a <xref:System.Net.HttpListener> třídy.

Kromě toho [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] zahrnuje následující vylepšení sítě:

- RFC podpora standardu URI splňující. Další informace najdete v tématu <xref:System.Uri> a související třídy.

- Podpora pro analýzu mezinárodních názvů domén (IDN). Další informace najdete v tématu <xref:System.Uri> a související třídy.

- Podpora pro e-mailovou adresu internacionalizace (EAI). Další informace najdete v tématu <xref:System.Net.Mail> oboru názvů.

- Vylepšená podpora protokolu IPv6. Další informace najdete v tématu <xref:System.Net.NetworkInformation> oboru názvů.

- Podpora soketu v duálním režimu. Další informace najdete v tématu <xref:System.Net.Sockets.Socket> a <xref:System.Net.Sockets.TcpListener> třídy.

<a name="client" />

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)
 V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], obsahuje Windows Presentation Foundation (WPF) změny a vylepšení v následujících oblastech:

- Nové <xref:System.Windows.Controls.Ribbon.Ribbon> ovládací prvek, který umožňující provádět implementaci pás uživatelského rozhraní, který je hostitelem panelu nástrojů Rychlý přístup, nabídky aplikace a karet.

- Nové <xref:System.ComponentModel.INotifyDataErrorInfo> rozhraní, které podporuje synchronní a asynchronní ověření dat.

- Nové funkce pro <xref:System.Windows.Controls.VirtualizingPanel> a <xref:System.Windows.Threading.Dispatcher> třídy.

- Vylepšili jsme výkon při zobrazování velkých sad seskupených dat a to přístupem ke kolekcím na vláknech mimo uživatelské rozhraní.

- Datové vazby k statické vlastnosti, vázání dat na vlastní typy, které implementují <xref:System.Reflection.ICustomTypeProvider> rozhraní a načítání informací o vázání dat z vazbového výrazu.

- Přemístění dat jako změny hodnot (živé tvarování).

- Možnost zkontrolovat, zda je kontext dat pro kontejner položek odpojen.

- Možnost nastavit dobu, která má uplynout mezi změnami vlastností a aktualizacemi zdrojů dat.

- Vylepšená podpora pro implementaci vzorců slabých událostí. Také události mohou nyní přijímat rozšíření značek.

<a name="windows_communication_foundation" />

### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)
 V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], následující funkce byly přidány pro jednodušší zápis a udržování aplikací Windows Communication Foundation (WCF):

- Zjednodušení generovaných konfiguračních souborů.

- Podpora rozvoje prvního kontraktu.

- Schopnost snadno konfigurovat režim kompatibility ASP.NET.

- Změny ve výchozích hodnotách vlastností snížit pravděpodobnost, že budete muset nastavit jejich přenosu.

- Aktualizuje <xref:System.Xml.XmlDictionaryReaderQuotas> třídy snížit pravděpodobnost, že budete muset ručně konfigurovat kvóty pro čtenáře slovníku XML.

- Ověření konfiguračních souborů WCF aplikací Visual Studio jako součást procesu sestavení, takže můžete zjistit chyby konfigurace před spuštěním vaší aplikace.

- Nová podpora asynchronního streamování.

- Nový protokol HTTPS mapování pro usnadnění vystavení koncového bodu přes HTTPS pomocí Internetové informační služby (IIS).

- Možnost Generovat metadata v jednom dokumentu WSDL připojením `?singleWSDL` na adresu URL služby.

- Sockety umožňují skutečnou obousměrnou komunikaci přes porty 80 a 443 s charakteristikami výkonu, podobné přenosu protokolu TCP.

- Podpora konfigurace služeb v kódu.

- Popisy tlačítek editoru XML.

- <xref:System.ServiceModel.ChannelFactory> Podpora ukládání do mezipaměti.

- Podpora komprese binárního kodéru.

- Podpora pro přenos UDP, který umožňuje vývojářům zapisovat služby využívající "zprávy vypal a zapomeň" zasílání zpráv. Klient odešle zprávu službě a očekává, že žádná odpověď ze služby.

- Možnost podporovat více režimů ověřování v jednom koncovém bodu WCF při použití přenosového protokolu HTTP a zabezpečení přenosu.

- Podpora služeb WCF, které používají mezinárodní názvy domén (IDN).

 Další informace najdete v tématu [co je nového ve Windows Communication Foundation](https://go.microsoft.com/fwlink/?LinkId=228173).

<a name="windows_workflow_foundation" />

### <a name="windows-workflow-foundation-wf"></a>Windows Workflow Foundation (WF)
 V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], bylo přidáno několik nových funkcí pro Windows Workflow Foundation (WF), včetně:

- Pracovní postupy stroje, které byly poprvé představeny jako součást rozhraní .NET Framework 4.0.1 ([rozhraní .NET Framework 4 Platform Update 1](https://go.microsoft.com/fwlink/?LinkID=215092)). Tato aktualizace je zahrnuta několika nových třídách a činnostech, které vývojářům umožňují vytvářet pracovní postupy stavu počítače. Tyto třídy a činnosti byly aktualizovány [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] zahrnout:

    - Možnost nastavit zarážky na stavy.

    - Možnost kopírování a vkládání přechodů v Návrháři pracovních postupů.

    - Podpora návrhářů pro sdílené vytváření aktivačních přechodů.

    - Aktivity pro vytvoření pracovní postupy stavu počítače, včetně: <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State>, a <xref:System.Activities.Statements.Transition>.

- Rozšířené funkce návrháře postupu provádění, jako je následující:

    - Rozšířené možnosti hledání pracovního postupu v sadě Visual Studio, včetně **rychlé hledání** a **najít v souborech**.

    - Možnost automaticky vytvořit sekvenční aktivitu, pokud je druhá podřízená aktivita přidána do aktivity kontejneru a sekvenční aktivity zahrnout obě aktivity.

    - Podpora posouvání, což umožňuje viditelnou část pracovního postupu bez použití posuvníků změnit.

    - Nový **Osnova dokumentu** zobrazení, které obsahující komponenty pracovního postupu v zobrazení stromové osnovy a umožní vám vybrat komponenty v **Osnova dokumentu** zobrazení.

    - Možnost přidání poznámek k činnostem.

    - Možnost definovat a využívat delegáty aktivity pomocí návrháře postupu provádění.

    - Automatické připojení a automatické vložení činností a přechodů v pracovních postupech stavu počítače a vývojového diagramu.

- Úložiště zobrazí informace o pracovním postupu v jednom elementu souboru XAML, tak můžou snadno najít a upravit informace o stavu zobrazení stavu.

- Aktivita kontejneru NoPersistScope zabránit uchování podřízené aktivity.

- Podpora pro výrazy jazyka C#:

    - Projekty pracovního postupu, které používají jazyk Visual Basic budou používat výrazy jazyka Visual Basic a projekty pracovního postupu C# budou používat výrazy jazyka C#.

    - Projekty jazyka C# pracovního postupu, které byly vytvořeny v sadě Visual Studio 2010 a které mají výrazy jazyka Visual Basic jsou kompatibilní s projekty C# pracovního postupu, které používají výrazy jazyka C#.

- Vylepšení správy verzí:

    - Nové <xref:System.Activities.WorkflowIdentity> třídu, která zajišťuje mapování mezi trvalé instance práce a jejich definicí pracovního postupu.

    - Vedle sebe spuštění několika verzí pracovního postupu u stejného hostitele, včetně <xref:System.ServiceModel.Activities.WorkflowServiceHost>.

    - V režimu dynamické aktualizace, je možnost upravit definici trvalé instance práce.

- Kontraktem nasazení služby pracovního postupu, který poskytuje podporu pro automatické generování činností, které odpovídají existující smlouvě o službách.

 Další informace najdete v tématu [co je nového ve Windows Workflow Foundation](https://go.microsoft.com/fwlink/?LinkId=228176).

<a name="tailored" />

### [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]

[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace jsou určeny pro konkrétní provedení form factor a využívají výkon operačního systému Windows. Podmnožinu [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo 4.5.1 je k dispozici pro vytváření [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace pro Windows pomocí C# nebo Visual Basic. Tato Podsada se nazývá [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] a je podrobněji popsána [přehled](https://go.microsoft.com/fwlink/?LinkId=228491) Windows Dev Center.

### <a name="portable-class-libraries-a-nameportable-"></a>Přenosné knihovny tříd <a name="portable" />

Knihovny přenosných tříd projektu v sadě Visual Studio 2012 (a novějších verzích) umožňuje zapisovat a vytvářet spravovaná sestavení, které pracují na více platformách rozhraní .NET Framework. Používání knihovny přenosných tříd projektu zvolte platformy (jako jsou Windows Phone a [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]) do cíle. Dostupné typy a členy v projektu jsou automaticky omezeny na běžnými typy a členy v těchto platformách. Další informace najdete v tématu [přenosné knihovny tříd](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).

## <a name="see-also"></a>Viz také:

- [Rozhraní .NET Framework a nesvázaná vydání](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)
- [Co je nového v usnadnění přístupu v rozhraní .NET Framework](whats-new-in-accessibility.md)
- [Co je nového v sadě Visual Studio 2017](/visualstudio/ide/whats-new-in-visual-studio)
- [ASP.NET](/aspnet)
- [Co je nového v jazyce Visual C++](/cpp/what-s-new-for-visual-cpp-in-visual-studio)
