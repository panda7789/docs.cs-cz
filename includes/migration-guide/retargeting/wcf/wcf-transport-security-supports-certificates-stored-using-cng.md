---
ms.openlocfilehash: 5c09bee92f679cd7e7a95cd23d5ce0ca9b57170c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614500"
---
### <a name="wcf-transport-security-supports-certificates-stored-using-cng"></a><span data-ttu-id="66e69-101">Zabezpečení přenosu WCF podporuje certifikáty uložené pomocí CNG</span><span class="sxs-lookup"><span data-stu-id="66e69-101">WCF transport security supports certificates stored using CNG</span></span>

#### <a name="details"></a><span data-ttu-id="66e69-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="66e69-102">Details</span></span>

<span data-ttu-id="66e69-103">Počínaje aplikacemi, které cílí na .NET Framework 4.6.2, podporuje zabezpečení přenosu WCF certifikáty uložené pomocí knihovny kryptografických služeb systému Windows (CNG).</span><span class="sxs-lookup"><span data-stu-id="66e69-103">Starting with apps that target the .NET Framework 4.6.2, WCF transport security supports certificates stored using the Windows Cryptography Library (CNG).</span></span> <span data-ttu-id="66e69-104">Tato podpora je omezená na certifikáty s veřejným klíčem, který má exponent větší než 32 bitů.</span><span class="sxs-lookup"><span data-stu-id="66e69-104">This support is limited to certificates with a public key that has an exponent no more than 32 bits in length.</span></span> <span data-ttu-id="66e69-105">Když je aplikace cílena na .NET Framework 4.6.2, je tato funkce ve výchozím nastavení zapnutá. V dřívějších verzích .NET Framework se pokus o použití certifikátů x509 s poskytovatelem úložiště klíčů CSG vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="66e69-105">When an application targets the .NET Framework 4.6.2, this feature is on by default.In earlier versions of the .NET Framework, the attempt to use X509 certificates with a CSG key storage provider throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="66e69-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="66e69-106">Suggestion</span></span>

<span data-ttu-id="66e69-107">Aplikace, které cílí na .NET Framework 4.6.1 a starší, ale běží na .NET Framework 4.6.2, můžou povolit podporu pro certifikáty CNG přidáním následujícího řádku do `<runtime>` oddílu souboru app.config nebo web.config:</span><span class="sxs-lookup"><span data-stu-id="66e69-107">Apps that target the .NET Framework 4.6.1 and earlier but are running on the .NET Framework 4.6.2 can enable support for CNG certificates by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableCngCertificates=false" />
</runtime>
```

<span data-ttu-id="66e69-108">To lze provést také programově pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="66e69-108">This can also be done programmatically with the following code:</span></span>

```csharp
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificate";

AppContext.SetSwitch(disableCngCertificates, false);
```

```vb
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"
AppContext.SetSwitch(disableCngCertificates, False)
```

<span data-ttu-id="66e69-109">Všimněte si, že vzhledem k tomu, že v důsledku této změny, nebude již spuštěn žádný kód pro zpracování výjimek, který závisí na pokusu o zahájení zabezpečené komunikace s certifikátem CNG na selhání.</span><span class="sxs-lookup"><span data-stu-id="66e69-109">Note that, because of this change, any exception handling code that depends on the attempt to initiate secure communication with a CNG certificate to fail will no longer execute.</span></span>

| <span data-ttu-id="66e69-110">Name</span><span class="sxs-lookup"><span data-stu-id="66e69-110">Name</span></span>    | <span data-ttu-id="66e69-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="66e69-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="66e69-112">Rozsah</span><span class="sxs-lookup"><span data-stu-id="66e69-112">Scope</span></span>   | <span data-ttu-id="66e69-113">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="66e69-113">Minor</span></span>       |
| <span data-ttu-id="66e69-114">Verze</span><span class="sxs-lookup"><span data-stu-id="66e69-114">Version</span></span> | <span data-ttu-id="66e69-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="66e69-115">4.6.2</span></span>       |
| <span data-ttu-id="66e69-116">Typ</span><span class="sxs-lookup"><span data-stu-id="66e69-116">Type</span></span>    | <span data-ttu-id="66e69-117">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="66e69-117">Retargeting</span></span> |
