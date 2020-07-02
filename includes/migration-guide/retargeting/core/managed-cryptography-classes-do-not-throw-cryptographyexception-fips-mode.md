---
ms.openlocfilehash: 0b62eff8d70873293aafa539f40bf032672df57a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617801"
---
### <a name="managed-cryptography-classes-do-not-throw-a-cryptographyexception-in-fips-mode"></a><span data-ttu-id="da925-101">Spravované kryptografické třídy nevyvolávají výjimku CryptographyException v režimu FIPS.</span><span class="sxs-lookup"><span data-stu-id="da925-101">Managed cryptography classes do not throw a CryptographyException in FIPS mode</span></span>

#### <a name="details"></a><span data-ttu-id="da925-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="da925-102">Details</span></span>

<span data-ttu-id="da925-103">V .NET Framework 4.7.2 a starších verzích spravované třídy zprostředkovatele kryptografických služeb, jako je například <xref:System.Security.Cryptography.SHA256Managed> vyvolat a v <xref:System.Security.Cryptography.CryptographicException> případě, že systémové šifrovací knihovny jsou konfigurovány v režimu FIPS.</span><span class="sxs-lookup"><span data-stu-id="da925-103">In .NET Framework 4.7.2 and earlier versions, managed cryptographic provider classes such as <xref:System.Security.Cryptography.SHA256Managed> throw a <xref:System.Security.Cryptography.CryptographicException> when the system cryptographic libraries are configured in FIPS mode.</span></span> <span data-ttu-id="da925-104">Tyto výjimky jsou vyvolány, protože spravované verze neprošly certifikací FIPS (Federal Information Processing Standards) 140-2 a také k blokování kryptografických algoritmů, které nebyly považovány za schválené na základě pravidel FIPS.</span><span class="sxs-lookup"><span data-stu-id="da925-104">These exceptions are thrown because the managed versions have not undergone FIPS (Federal Information Processing Standards) 140-2 certification, as well as to block cryptographic algorithms that were not considered to be approved based on the FIPS rules.</span></span>  <span data-ttu-id="da925-105">Vzhledem k tomu, že někteří vývojáři mají své vývojové počítače v režimu FIPS, jsou tyto výjimky často vyvolány pouze v produkčních systémech. Aplikace, které cílí na .NET Framework 4,8 a novější verze, automaticky přepnou na novější, uvolněnou zásadu, takže <xref:System.Security.Cryptography.CryptographicException> v takových případech již není vyvoláno ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="da925-105">Because few developers have their development machines in FIPS mode, these exceptions are frequently thrown only on production systems.Applications that target .NET Framework 4.8 and later versions automatically switch to the newer, relaxed policy, so that a <xref:System.Security.Cryptography.CryptographicException> is no longer thrown by default in such cases.</span></span> <span data-ttu-id="da925-106">Místo toho spravované kryptografické třídy přesměrují kryptografické operace do systémové knihovny kryptografie.</span><span class="sxs-lookup"><span data-stu-id="da925-106">Instead, the managed cryptography classes redirect cryptographic operations to a system cryptography library.</span></span> <span data-ttu-id="da925-107">Tato změna zásad efektivně odstraňuje potenciálně matoucí rozdíl mezi vývojářskými prostředími a provozními prostředími a zpřístupňuje nativní komponenty a spravované komponenty v rámci stejných kryptografických zásad.</span><span class="sxs-lookup"><span data-stu-id="da925-107">This policy change effectively removes a potentially confusing difference between developer environments and the production environments and makes native components and managed components operate under the same cryptographic policy.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="da925-108">Návrh</span><span class="sxs-lookup"><span data-stu-id="da925-108">Suggestion</span></span>

<span data-ttu-id="da925-109">Pokud je toto chování nežádoucí, můžete si ho odhlásit a obnovit předchozí chování tak, aby <xref:System.Security.Cryptography.CryptographicException> byl v režimu FIPS vyvolán přidáním následujícího nastavení konfigurace [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="da925-109">If this behavior is undesirable, you can opt out of it and restore the previous behavior so that a <xref:System.Security.Cryptography.CryptographicException> is thrown in FIPS mode by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) configuration setting to the [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.UseLegacyFipsThrow=true" />
</runtime>
```

<span data-ttu-id="da925-110">Pokud je vaše aplikace cílena .NET Framework 4.7.2 nebo starší, můžete k této změně také vyjádřit přidáním následujícího nastavení konfigurace [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="da925-110">If your application targets .NET Framework 4.7.2 or earlier, you can also opt in to this change by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) configuration setting to the [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.UseLegacyFipsThrow=false" />
</runtime>
```

| <span data-ttu-id="da925-111">Name</span><span class="sxs-lookup"><span data-stu-id="da925-111">Name</span></span>    | <span data-ttu-id="da925-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="da925-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="da925-113">Rozsah</span><span class="sxs-lookup"><span data-stu-id="da925-113">Scope</span></span>   | <span data-ttu-id="da925-114">Edge</span><span class="sxs-lookup"><span data-stu-id="da925-114">Edge</span></span>        |
| <span data-ttu-id="da925-115">Verze</span><span class="sxs-lookup"><span data-stu-id="da925-115">Version</span></span> | <span data-ttu-id="da925-116">4,8</span><span class="sxs-lookup"><span data-stu-id="da925-116">4.8</span></span>         |
| <span data-ttu-id="da925-117">Typ</span><span class="sxs-lookup"><span data-stu-id="da925-117">Type</span></span>    | <span data-ttu-id="da925-118">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="da925-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="da925-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="da925-119">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AesManaged?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.MD5Cng?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.MD5CryptoServiceProvider?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RC2CryptoServiceProvider?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RijndaelManaged?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RIPEMD160Managed?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.SHA1Managed?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.SHA256Managed?displayProperty=nameWithType>
