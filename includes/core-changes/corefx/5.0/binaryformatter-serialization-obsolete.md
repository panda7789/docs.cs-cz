---
ms.openlocfilehash: 7cb146d19486618a4cee9976abe2220ea4b72790
ms.sourcegitcommit: d337df55f83325918cbbd095eb573400bea49064
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2020
ms.locfileid: "88203971"
---
### <a name="binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps"></a><span data-ttu-id="009e2-101">Metody serializace BinaryFormatter jsou zastaralé a zakázané v aplikacích ASP.NET</span><span class="sxs-lookup"><span data-stu-id="009e2-101">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>

<span data-ttu-id="009e2-102">`Serialize` a `Deserialize` metody <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> , a <xref:System.Runtime.Serialization.Formatter> <xref:System.Runtime.Serialization.IFormatter> jsou nyní zastaralé.</span><span class="sxs-lookup"><span data-stu-id="009e2-102">`Serialize` and `Deserialize` methods on <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, <xref:System.Runtime.Serialization.Formatter>, and <xref:System.Runtime.Serialization.IFormatter> are now obsolete.</span></span> <span data-ttu-id="009e2-103">Kromě toho <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> je serializace ve výchozím nastavení zakázána pro aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="009e2-103">Additionally, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> serialization is prohibited by default for ASP.NET apps.</span></span>

#### <a name="change-description"></a><span data-ttu-id="009e2-104">Popis změny</span><span class="sxs-lookup"><span data-stu-id="009e2-104">Change description</span></span>

<span data-ttu-id="009e2-105">V důsledku [chyb zabezpečení](../../../../docs/standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities) v nástroji <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> jsou nyní zastaralé následující metody.</span><span class="sxs-lookup"><span data-stu-id="009e2-105">Due to [security vulnerabilities](../../../../docs/standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities) in <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, the following methods are now obsolete.</span></span> <span data-ttu-id="009e2-106">Kromě toho se v ASP.NET Core 5,0 a novějších aplikacích vyvolá <xref:System.NotSupportedException> , pokud webová aplikace nemá opětovné povolení <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> funkcí.</span><span class="sxs-lookup"><span data-stu-id="009e2-106">Additionally, in ASP.NET Core 5.0 and later apps, they will throw a <xref:System.NotSupportedException>, unless the web app has re-enabled <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> functionality.</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>

<span data-ttu-id="009e2-107">Tyto metody jsou označeny jako zastaralé jako součást snahy o použití <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> v rámci ekosystému .NET.</span><span class="sxs-lookup"><span data-stu-id="009e2-107">These methods are marked obsolete as part of an effort to wind down usage of <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> within the .NET ecosystem.</span></span>

<span data-ttu-id="009e2-108">Následující metody serializace jsou také zastaralé, ale nemají žádné změny v chování:</span><span class="sxs-lookup"><span data-stu-id="009e2-108">The following serialization methods are also now obsolete, but have no behavioral changes:</span></span>

- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

#### <a name="version-introduced"></a><span data-ttu-id="009e2-109">Představená verze</span><span class="sxs-lookup"><span data-stu-id="009e2-109">Version introduced</span></span>

<span data-ttu-id="009e2-110">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="009e2-110">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="009e2-111">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="009e2-111">Recommended action</span></span>

- <span data-ttu-id="009e2-112">Přestat používat <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ve svém kódu.</span><span class="sxs-lookup"><span data-stu-id="009e2-112">Stop using <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> in your code.</span></span> <span data-ttu-id="009e2-113">Místo toho zvažte použití <xref:System.Text.Json.JsonSerializer> nebo <xref:System.Xml.Serialization.XmlSerializer> .</span><span class="sxs-lookup"><span data-stu-id="009e2-113">Instead, consider using <xref:System.Text.Json.JsonSerializer> or <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="009e2-114">Další informace najdete v tématu [BinaryFormatter Security Guide](../../../../docs/standard/serialization/binaryformatter-security-guide.md).</span><span class="sxs-lookup"><span data-stu-id="009e2-114">For more information, see [BinaryFormatter security guide](../../../../docs/standard/serialization/binaryformatter-security-guide.md).</span></span>

- <span data-ttu-id="009e2-115">Můžete dočasně potlačit <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> upozornění v době kompilace, což je `SYSLIB0011` .</span><span class="sxs-lookup"><span data-stu-id="009e2-115">You can temporarily suppress the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> compile-time warning, which is `SYSLIB0011`.</span></span> <span data-ttu-id="009e2-116">Doporučujeme, abyste před výběrem této možnosti důkladně vyhodnotili kód pro rizika.</span><span class="sxs-lookup"><span data-stu-id="009e2-116">We recommend that you thoroughly assess your code for risks before choosing this option.</span></span> <span data-ttu-id="009e2-117">Nejjednodušší způsob, jak potlačit upozornění, je obklopit jednotlivé weby volání `#pragma` direktiv.</span><span class="sxs-lookup"><span data-stu-id="009e2-117">The easiest way to suppress the warnings is to surround the individual call site with `#pragma` directives.</span></span>

  ```csharp
  // Now read the purchase order back from disk
  using (var readStream = new FileStream("myfile.bin", FileMode.Open))
  {
      var formatter = new BinaryFormatter();
  #pragma warning disable SYSLIB0011
      return (PurchaseOrder)formatter.Deserialize(readStream);
  #pragma warning restore SYSLIB0011
  }
  ```

  <span data-ttu-id="009e2-118">Můžete také potlačit upozornění v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="009e2-118">You can also suppress the warning in the project file.</span></span>

  ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Disable "BinaryFormatter is obsolete" warnings for entire project -->
    <NoWarn>$(NoWarn);SYSLIB0011</NoWarn>
  </PropertyGroup>
  ```

  <span data-ttu-id="009e2-119">Potlačíte-li upozornění v souboru projektu, je upozornění potlačeno pro všechny soubory kódu v projektu.</span><span class="sxs-lookup"><span data-stu-id="009e2-119">If you suppress the warning in the project file, the warning is suppressed for all code files in the project.</span></span> <span data-ttu-id="009e2-120">Potlačení SYSLIB0011 potlačí upozornění způsobené použitím jiných zastaralých rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="009e2-120">Suppressing SYSLIB0011 does not suppress warnings caused by using other obsolete APIs.</span></span>

- <span data-ttu-id="009e2-121">Chcete-li pokračovat <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> v používání aplikace ASP.NET, můžete je znovu povolit v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="009e2-121">To continue using <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> in ASP.NET apps, you can re-enable it in the project file.</span></span> <span data-ttu-id="009e2-122">Důrazně to však nedoporučujeme.</span><span class="sxs-lookup"><span data-stu-id="009e2-122">However, it's strongly recommended not to do this.</span></span> <span data-ttu-id="009e2-123">Další informace najdete v tématu [BinaryFormatter Security Guide](../../../../docs/standard/serialization/binaryformatter-security-guide.md).</span><span class="sxs-lookup"><span data-stu-id="009e2-123">For more information, see [BinaryFormatter security guide](../../../../docs/standard/serialization/binaryformatter-security-guide.md).</span></span>

  ```xml
  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Warning: Setting the following switch is *NOT* recommended in web apps. -->
    <EnableUnsafeBinaryFormatterSerialization>true</EnableUnsafeBinaryFormatterSerialization>
  </PropertyGroup>
  ```

<span data-ttu-id="009e2-124">Další informace o doporučených akcích najdete v tématu [řešení chyb BinaryFormatter obsoletion a deaktivace](https://aka.ms/binaryformatter).</span><span class="sxs-lookup"><span data-stu-id="009e2-124">For more information about recommended actions, see [Resolving BinaryFormatter obsoletion and disablement errors](https://aka.ms/binaryformatter).</span></span>

#### <a name="category"></a><span data-ttu-id="009e2-125">Kategorie</span><span class="sxs-lookup"><span data-stu-id="009e2-125">Category</span></span>

- <span data-ttu-id="009e2-126">Knihovny Core .NET</span><span class="sxs-lookup"><span data-stu-id="009e2-126">Core .NET libraries</span></span>
- <span data-ttu-id="009e2-127">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="009e2-127">ASP.NET</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="009e2-128">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="009e2-128">Affected APIs</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize`
- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize`
- `M:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)`
- `M:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)`
- `M:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)`
- `M:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)`

-->
