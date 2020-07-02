---
ms.openlocfilehash: 36a9db601f7637185bf48dfcbe2233b4489fcdcf
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614444"
---
### <a name="aescryptoserviceprovider-decryptor-provides-a-reusable-transform"></a><span data-ttu-id="40d97-101">Dešifrovací modul AesCryptoServiceProvider poskytuje opakovaně použitelnou transformaci.</span><span class="sxs-lookup"><span data-stu-id="40d97-101">AesCryptoServiceProvider decryptor provides a reusable transform</span></span>

#### <a name="details"></a><span data-ttu-id="40d97-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="40d97-102">Details</span></span>

<span data-ttu-id="40d97-103">Od aplikací, které cílí na .NET Framework 4.6.2, <xref:System.Security.Cryptography.AesCryptoServiceProvider> dešifrovací modul poskytuje opakovaně použitelnou transformaci.</span><span class="sxs-lookup"><span data-stu-id="40d97-103">Starting with apps that target the .NET Framework 4.6.2, the <xref:System.Security.Cryptography.AesCryptoServiceProvider> decryptor provides a reusable transform.</span></span> <span data-ttu-id="40d97-104">Po volání <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName> je transformace znovu inicializována a lze ji znovu použít.</span><span class="sxs-lookup"><span data-stu-id="40d97-104">After a call to <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>, the transform is reinitialized and can be reused.</span></span> <span data-ttu-id="40d97-105">Pro aplikace, které cílí na starší verze .NET Framework, se pokusí znovu použít dešifrovací modul voláním <xref:System.Security.Cryptography.CryptoAPITransform.TransformBlock(System.Byte[],System.Int32,System.Int32,System.Byte[],System.Int32)?displayProperty=fullName> po volání metody <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName> vyvolá <xref:System.Security.Cryptography.CryptographicException> nebo vytvoří poškozená data.</span><span class="sxs-lookup"><span data-stu-id="40d97-105">For apps that target earlier versions of the .NET Framework, attempting to reuse the decryptor by calling <xref:System.Security.Cryptography.CryptoAPITransform.TransformBlock(System.Byte[],System.Int32,System.Int32,System.Byte[],System.Int32)?displayProperty=fullName> after a call to <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName> throws a <xref:System.Security.Cryptography.CryptographicException> or produces corrupted data.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="40d97-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="40d97-106">Suggestion</span></span>

<span data-ttu-id="40d97-107">Dopad této změny by měl být minimální, protože se jedná o očekávané chování. Aplikace, které závisí na předchozím chování, se můžou z něj odhlásit tím, že do `<runtime>` části konfiguračního souboru aplikace přidají následující nastavení konfigurace:</span><span class="sxs-lookup"><span data-stu-id="40d97-107">The impact of this change should be minimal, since this is the expected behavior.Applications that depend on the previous behavior can opt out of it using it by adding the following configuration setting to the `<runtime>` section of the application's configuration file:</span></span>

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=true"/>
</runtime>
```

<span data-ttu-id="40d97-108">Kromě toho aplikace, které cílí na předchozí verzi .NET Framework, ale jsou spuštěné v rámci verze .NET Framework počínaje .NET Framework 4.6.2, můžou se k ní přihlásit přidáním následujícího nastavení konfigurace do `<runtime>` oddílu konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="40d97-108">In addition, applications that target a previous version of the .NET Framework but are running under a version of the .NET Framework starting with .NET Framework 4.6.2 can opt in to it by adding the following configuration setting to the `<runtime>` section of the application's configuration file:</span></span>

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=false"/>
</runtime>
```

| <span data-ttu-id="40d97-109">Name</span><span class="sxs-lookup"><span data-stu-id="40d97-109">Name</span></span>    | <span data-ttu-id="40d97-110">Hodnota</span><span class="sxs-lookup"><span data-stu-id="40d97-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="40d97-111">Rozsah</span><span class="sxs-lookup"><span data-stu-id="40d97-111">Scope</span></span>   | <span data-ttu-id="40d97-112">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="40d97-112">Minor</span></span>       |
| <span data-ttu-id="40d97-113">Verze</span><span class="sxs-lookup"><span data-stu-id="40d97-113">Version</span></span> | <span data-ttu-id="40d97-114">4.6.2</span><span class="sxs-lookup"><span data-stu-id="40d97-114">4.6.2</span></span>       |
| <span data-ttu-id="40d97-115">Typ</span><span class="sxs-lookup"><span data-stu-id="40d97-115">Type</span></span>    | <span data-ttu-id="40d97-116">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="40d97-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="40d97-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="40d97-117">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AesCryptoServiceProvider.CreateDecryptor?displayProperty=nameWithType>
