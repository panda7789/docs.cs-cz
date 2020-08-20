---
ms.openlocfilehash: 1cb6e953aa57c72ee6a2665c521bada10e0786cf
ms.sourcegitcommit: 7499bdb428d63ed0e19e97f54d3d576c41598659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/31/2020
ms.locfileid: "87455769"
---
### <a name="utf-7-code-paths-are-obsolete"></a><span data-ttu-id="e13f7-101">Cesty kódu UTF-7 jsou zastaralé.</span><span class="sxs-lookup"><span data-stu-id="e13f7-101">UTF-7 code paths are obsolete</span></span>

<span data-ttu-id="e13f7-102">Kódování UTF-7 se už mezi aplikacemi nepoužívá a mnoho specifikací teď [zakazuje použití](https://security.stackexchange.com/a/68609/3573) při výměně.</span><span class="sxs-lookup"><span data-stu-id="e13f7-102">The UTF-7 encoding is no longer in wide use among applications, and many specs now [forbid its use](https://security.stackexchange.com/a/68609/3573) in interchange.</span></span> <span data-ttu-id="e13f7-103">V aplikacích, které nepředpokládá nahlašování dat kódovaných v kódování UTF-7, se někdy [používá také jako vektor útoku](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7) .</span><span class="sxs-lookup"><span data-stu-id="e13f7-103">It's also occasionally [used as an attack vector](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7) in applications that don't anticipate encountering UTF-7-encoded data.</span></span> <span data-ttu-id="e13f7-104">Microsoft upozorňuje na použití, <xref:System.Text.UTF7Encoding?displayProperty=nameWithType> protože neposkytuje detekci chyb.</span><span class="sxs-lookup"><span data-stu-id="e13f7-104">Microsoft warns against use of <xref:System.Text.UTF7Encoding?displayProperty=nameWithType> because it doesn't provide error detection.</span></span>

<span data-ttu-id="e13f7-105">V důsledku toho <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> <xref:System.Text.UTF7Encoding.%23ctor%2A> jsou nyní zastaraly vlastnosti a konstruktory.</span><span class="sxs-lookup"><span data-stu-id="e13f7-105">Consequently, the <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> property and <xref:System.Text.UTF7Encoding.%23ctor%2A> constructors are now obsolete.</span></span> <span data-ttu-id="e13f7-106">Navíc <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> a <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType> již neumožňuje zadat `UTF-7` .</span><span class="sxs-lookup"><span data-stu-id="e13f7-106">Additionally, <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> and <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType> no longer allow you to specify `UTF-7`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e13f7-107">Popis změny</span><span class="sxs-lookup"><span data-stu-id="e13f7-107">Change description</span></span>

<span data-ttu-id="e13f7-108">Dřív jste mohli vytvořit instanci kódování UTF-7 pomocí <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="e13f7-108">Previously, you could create an instance of the UTF-7 encoding by using the <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> APIs.</span></span> <span data-ttu-id="e13f7-109">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e13f7-109">For example:</span></span>

```csharp
Encoding enc1 = Encoding.GetEncoding("utf-7"); // By name.
Encoding enc2 = Encoding.GetEncoding(65000); // By code page.
```

<span data-ttu-id="e13f7-110">Kromě toho instance, která představuje kódování UTF-7, byla vytvořena pomocí <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> metody, která vytvoří výčet všech <xref:System.Text.Encoding> instancí zaregistrovaných v systému.</span><span class="sxs-lookup"><span data-stu-id="e13f7-110">Additionally, an instance that represents the UTF-7 encoding was enumerated by the <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> method, which enumerates all the <xref:System.Text.Encoding> instances registered on the system.</span></span>

<span data-ttu-id="e13f7-111">Počínaje rozhraním .NET 5,0 <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> jsou vlastnosti a <xref:System.Text.UTF7Encoding.%23ctor%2A> konstruktory zastaralé a jsou vyprodukovány upozornění `SYSLIB0001` (nebo `MSLIB0001` ve verzi Preview).</span><span class="sxs-lookup"><span data-stu-id="e13f7-111">Starting in .NET 5.0, the <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> property and <xref:System.Text.UTF7Encoding.%23ctor%2A> constructors are obsolete and produce warning `SYSLIB0001` (or `MSLIB0001` in preview versions).</span></span> <span data-ttu-id="e13f7-112">Chcete-li však omezit počet upozornění, která volající obdrží při použití <xref:System.Text.UTF7Encoding> třídy, <xref:System.Text.UTF7Encoding> samotný typ není označen jako zastaralý.</span><span class="sxs-lookup"><span data-stu-id="e13f7-112">However, to reduce the number of warnings that callers receive when using the <xref:System.Text.UTF7Encoding> class, the <xref:System.Text.UTF7Encoding> type itself is not marked obsolete.</span></span>

```csharp
// The next line generates warning SYSLIB0001.
UTF7Encoding enc = new UTF7Encoding();
// The next line does not generate a warning.
byte[] bytes = enc.GetBytes("Hello world!");
```

<span data-ttu-id="e13f7-113">Kromě toho <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> metody zacházejí s názvem kódování `utf-7` a znakovou stránkou `65000` jako `unknown` .</span><span class="sxs-lookup"><span data-stu-id="e13f7-113">Additionally, the <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> methods treat the encoding name `utf-7` and the code page `65000` as `unknown`.</span></span> <span data-ttu-id="e13f7-114">Ošetření kódování jako `unknown` způsobí, že metoda vyvolá výjimku <xref:System.ArgumentException> .</span><span class="sxs-lookup"><span data-stu-id="e13f7-114">Treating the encoding as `unknown` causes the method to throw an <xref:System.ArgumentException>.</span></span>

```csharp
// Throws ArgumentException, same as calling Encoding.GetEncoding("unknown").
Encoding enc = Encoding.GetEncoding("utf-7");
```

<span data-ttu-id="e13f7-115">Nakonec <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> Metoda nezahrnuje kódování UTF-7 v poli <xref:System.Text.EncodingInfo> , které vrací.</span><span class="sxs-lookup"><span data-stu-id="e13f7-115">Finally, the <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> method doesn't include the UTF-7 encoding in the <xref:System.Text.EncodingInfo> array that it returns.</span></span> <span data-ttu-id="e13f7-116">Kódování je vyloučeno, protože nemůže být vytvořena instance.</span><span class="sxs-lookup"><span data-stu-id="e13f7-116">The encoding is excluded because it cannot be instantiated.</span></span>

```csharp
foreach (EncodingInfo encInfo in Encoding.GetEncodings())
{
    // The next line would throw if GetEncodings included UTF-7.
    Encoding enc = Encoding.GetEncoding(encInfo.Name);
}
```

#### <a name="reason-for-change"></a><span data-ttu-id="e13f7-117">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="e13f7-117">Reason for change</span></span>

<span data-ttu-id="e13f7-118">Mnoho aplikací volá `Encoding.GetEncoding("encoding-name")` s hodnotou názvu kódování, která je poskytnuta nedůvěryhodným zdrojem.</span><span class="sxs-lookup"><span data-stu-id="e13f7-118">Many applications call `Encoding.GetEncoding("encoding-name")` with an encoding name value that's provided by an untrusted source.</span></span> <span data-ttu-id="e13f7-119">Například webový klient nebo server může převzít `charset` část `Content-Type` hlavičky a předat hodnotu přímo do `Encoding.GetEncoding` bez ověření.</span><span class="sxs-lookup"><span data-stu-id="e13f7-119">For example, a web client or server might take the `charset` portion of the `Content-Type` header and pass the value directly to `Encoding.GetEncoding` without validating it.</span></span> <span data-ttu-id="e13f7-120">To by mohlo umožňovat zadat škodlivý koncový bod `Content-Type: ...; charset=utf-7` , což by mohlo způsobit nesprávné chování přijímající aplikace.</span><span class="sxs-lookup"><span data-stu-id="e13f7-120">This could allow a malicious endpoint to specify `Content-Type: ...; charset=utf-7`, which could cause the receiving application to misbehave.</span></span>

<span data-ttu-id="e13f7-121">Kromě toho zakázání cest kódu ve formátu UTF-7 umožňuje optimalizace kompilátorů, jako jsou ty, které používá Blazor, k odebrání těchto cest kódu zcela ze výsledné aplikace.</span><span class="sxs-lookup"><span data-stu-id="e13f7-121">Additionally, disabling UTF-7 code paths allows optimizing compilers, such as those used by Blazor, to remove these code paths entirely from the resulting application.</span></span> <span data-ttu-id="e13f7-122">V důsledku toho zkompilované aplikace pracují efektivněji a zabírají méně místa na disku.</span><span class="sxs-lookup"><span data-stu-id="e13f7-122">As a result, the compiled applications run more efficiently and take less disk space.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e13f7-123">Představená verze</span><span class="sxs-lookup"><span data-stu-id="e13f7-123">Version introduced</span></span>

<span data-ttu-id="e13f7-124">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="e13f7-124">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e13f7-125">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="e13f7-125">Recommended action</span></span>

<span data-ttu-id="e13f7-126">Ve většině případů není nutné provádět žádnou akci.</span><span class="sxs-lookup"><span data-stu-id="e13f7-126">In most cases, you don't need to take any action.</span></span> <span data-ttu-id="e13f7-127">Pro aplikace, které dříve aktivovaly cesty kódu související s kódováním UTF-7, je však vhodné postupovat podle pokynů.</span><span class="sxs-lookup"><span data-stu-id="e13f7-127">However, for apps that have previously activated UTF-7-related code paths, consider the guidance that follows.</span></span>

- <span data-ttu-id="e13f7-128">Pokud vaše aplikace volá <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> s neznámými názvy kódování poskytnutými nedůvěryhodným zdrojem:</span><span class="sxs-lookup"><span data-stu-id="e13f7-128">If your app calls <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> with unknown encoding names provided by an untrusted source:</span></span>

  <span data-ttu-id="e13f7-129">Místo toho Porovnejte názvy kódování s konfigurovatelným seznamem povolených.</span><span class="sxs-lookup"><span data-stu-id="e13f7-129">Instead, compare the encoding names against a configurable allow list.</span></span> <span data-ttu-id="e13f7-130">Seznam konfigurovatelných povolených možností by měl obsahovat minimální standardní kódování UTF-8.</span><span class="sxs-lookup"><span data-stu-id="e13f7-130">The configurable allow list should at minimum include the industry-standard "utf-8".</span></span> <span data-ttu-id="e13f7-131">V závislosti na vašich klientech a zákonných požadavcích možná budete muset také zapnout kódování pro konkrétní oblast, například "GB18030".</span><span class="sxs-lookup"><span data-stu-id="e13f7-131">Depending on your clients and regulatory requirements, you may also need to allow region-specific encodings, such as "GB18030".</span></span>

  <span data-ttu-id="e13f7-132">Pokud neimplementujete seznam povolených, <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> vrátí všechny <xref:System.Text.Encoding> , které jsou součástí systému nebo které jsou zaregistrovány prostřednictvím vlastního <xref:System.Text.EncodingProvider> .</span><span class="sxs-lookup"><span data-stu-id="e13f7-132">If you don't implement an allow list, <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> will return any <xref:System.Text.Encoding> that's built into the system or that's registered via a custom <xref:System.Text.EncodingProvider>.</span></span> <span data-ttu-id="e13f7-133">Auditujte požadavky služby a ověřte, zda se jedná o požadované chování.</span><span class="sxs-lookup"><span data-stu-id="e13f7-133">Audit your service's requirements to validate that this is the desired behavior.</span></span> <span data-ttu-id="e13f7-134">Kódování UTF-7 bude ve výchozím nastavení nadále zakázáno, pokud vaše aplikace znovu nepovolí přepínač kompatibility, který je uveden dále v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="e13f7-134">UTF-7 continues to be disabled by default unless your application re-enables the compatibility switch mentioned later in this article.</span></span>

- <span data-ttu-id="e13f7-135">Pokud používáte <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> nebo <xref:System.Text.UTF7Encoding> máte ve svém vlastním protokolu nebo formátu souboru:</span><span class="sxs-lookup"><span data-stu-id="e13f7-135">If you're using <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> or <xref:System.Text.UTF7Encoding> within your own protocol or file format:</span></span>

  <span data-ttu-id="e13f7-136">Přepněte na použití <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> nebo <xref:System.Text.UTF8Encoding> .</span><span class="sxs-lookup"><span data-stu-id="e13f7-136">Switch to using <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> or <xref:System.Text.UTF8Encoding>.</span></span> <span data-ttu-id="e13f7-137">UTF-8 je oborová Standard a je široce podporovaná napříč jazyky, operačními systémy a moduly runtime.</span><span class="sxs-lookup"><span data-stu-id="e13f7-137">UTF-8 is an industry standard and is widely supported across languages, operating systems, and runtimes.</span></span> <span data-ttu-id="e13f7-138">Použití UTF-8 usnadňuje budoucí údržbu kódu a usnadňuje spolupráci se zbytkem ekosystému.</span><span class="sxs-lookup"><span data-stu-id="e13f7-138">Using UTF-8 eases future maintenance of your code and makes it more interoperable with the rest of the ecosystem.</span></span>

- <span data-ttu-id="e13f7-139">Pokud porovnáváte <xref:System.Text.Encoding> instanci proti <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="e13f7-139">If you're comparing an <xref:System.Text.Encoding> instance against <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType>:</span></span>

  <span data-ttu-id="e13f7-140">Místo toho zvažte možnost provést kontrolu na dobře známé znakové stránce UTF-7, což je `65000` .</span><span class="sxs-lookup"><span data-stu-id="e13f7-140">Instead, consider performing a check against the well-known UTF-7 code page, which is `65000`.</span></span> <span data-ttu-id="e13f7-141">Porovnáním s znakovou stránkou se vyhnete varování a také zpracovává některé hraniční případy, například pokud někdo volal `new UTF7Encoding()` nebo podtřídí typ.</span><span class="sxs-lookup"><span data-stu-id="e13f7-141">By comparing against the code page, you avoid the warning and also handle some edge cases, such as if somebody called `new UTF7Encoding()` or subclassed the type.</span></span>

  ```csharp
  void DoSomething(Encoding enc)
  {
      // Don't perform the check this way.
      // It produces a warning and misses some edge cases.
      if (enc == Encoding.UTF7)
      {
          // Encoding is UTF-7.
      }

      // Instead, perform the check this way.
      if (enc != null && enc.CodePage == 65000)
      {
          // Encoding is UTF-7.
      }
  }
  ```

- <span data-ttu-id="e13f7-142">Pokud musíte použít <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> nebo <xref:System.Text.UTF7Encoding> :</span><span class="sxs-lookup"><span data-stu-id="e13f7-142">If you must use <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> or <xref:System.Text.UTF7Encoding>:</span></span>

  <span data-ttu-id="e13f7-143">Můžete potlačit `SYSLIB0001` upozornění v kódu nebo v souboru *. csproj* projektu.</span><span class="sxs-lookup"><span data-stu-id="e13f7-143">You can suppress the `SYSLIB0001` warning in code or within your project's *.csproj* file.</span></span>

  ```csharp
  #pragma warning disable SYSLIB0001 // Disable the warning.
  Encoding enc = Encoding.UTF7;
  #pragma warning restore SYSLIB0001 // Re-enable the warning.
  ```

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below suppresses SYSLIB0001 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0001</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  > [!NOTE]
  > <span data-ttu-id="e13f7-144">Potlačení `SYSLIB0001` zakáže jenom <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> Upozornění a <xref:System.Text.UTF7Encoding> obsoletion.</span><span class="sxs-lookup"><span data-stu-id="e13f7-144">Suppressing `SYSLIB0001` only disables the <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> and <xref:System.Text.UTF7Encoding> obsoletion warnings.</span></span> <span data-ttu-id="e13f7-145">Nevypne žádná další upozornění ani nemění chování rozhraní API, jako je <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e13f7-145">It doesn't disable any other warnings or change the behavior of APIs like <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="e13f7-146">Pokud potřebujete podporu `Encoding.GetEncoding("utf-7", ...)` :</span><span class="sxs-lookup"><span data-stu-id="e13f7-146">If you must support `Encoding.GetEncoding("utf-7", ...)`:</span></span>

  <span data-ttu-id="e13f7-147">Podporu této služby můžete znovu povolit prostřednictvím přepínače kompatibility.</span><span class="sxs-lookup"><span data-stu-id="e13f7-147">You can re-enable support for this via a compatibility switch.</span></span> <span data-ttu-id="e13f7-148">Tento přepínač kompatibility lze zadat v souboru *. csproj* aplikace nebo v [konfiguračním souboru run-time](../../../../docs/core/run-time-config/index.md), jak je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="e13f7-148">This compatibility switch can be specified in the application's *.csproj* file or in a [run-time configuration file](../../../../docs/core/run-time-config/index.md), as shown in the following examples.</span></span>

  <span data-ttu-id="e13f7-149">V souboru *. csproj* aplikace:</span><span class="sxs-lookup"><span data-stu-id="e13f7-149">In the application's *.csproj* file:</span></span>

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- Re-enable support for UTF-7 -->
     <EnableUnsafeUTF7Encoding>true</EnableUnsafeUTF7Encoding>
    </PropertyGroup>
  </Project>
  ```

  <span data-ttu-id="e13f7-150">V *runtimeconfig.template.jsaplikace v* souboru:</span><span class="sxs-lookup"><span data-stu-id="e13f7-150">In the application's *runtimeconfig.template.json* file:</span></span>

  ```json
  {
    "configProperties": {
      "System.Text.Encoding.EnableUnsafeUTF7Encoding": true
    }
  }
  ```

  > [!TIP]
  > <span data-ttu-id="e13f7-151">Pokud znovu povolíte podporu UTF-7, měli byste provést kontrolu zabezpečení kódu, který volá <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e13f7-151">If you re-enable support for UTF-7, you should perform a security review of code that calls <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="e13f7-152">Kategorie</span><span class="sxs-lookup"><span data-stu-id="e13f7-152">Category</span></span>

- <span data-ttu-id="e13f7-153">Knihovny Core .NET</span><span class="sxs-lookup"><span data-stu-id="e13f7-153">Core .NET libraries</span></span>
- <span data-ttu-id="e13f7-154">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e13f7-154">Security</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e13f7-155">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="e13f7-155">Affected APIs</span></span>

- <xref:System.Text.Encoding.UTF7?displayProperty=fullName>
- <xref:System.Text.UTF7Encoding.%23ctor>
- <xref:System.Text.UTF7Encoding.%23ctor(System.Boolean)>
- <xref:System.Text.Encoding.GetEncoding(System.Int32)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.String)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncodings?displayProperty=fullName>

<!--

#### Affected APIs

- `System.Text.Encoding.UTF7`
- `System.Text.UTF7Encoding.#ctor`
- `System.Text.UTF7Encoding.#ctor(System.Boolean)`
- `System.Text.Encoding.GetEncoding(System.Int32)`
- `System.Text.Encoding.GetEncoding(System.String)`
- `System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)`
- `System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)`
- `System.Text.Encoding.GetEncodings`

-->
