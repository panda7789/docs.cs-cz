---
title: Silné názvy a knihovny .NET
description: Doporučení osvědčených postupů pro silné pojmenovávání knihoven .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/16/2018
ms.openlocfilehash: 3e7cc9a3a1be05d8fcb02b34f7027126697d15d0
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73196968"
---
# <a name="strong-naming"></a><span data-ttu-id="c21df-103">Vytváření silných názvů</span><span class="sxs-lookup"><span data-stu-id="c21df-103">Strong naming</span></span>

<span data-ttu-id="c21df-104">Silné pojmenování odkazuje na podepsání sestavení klíčem a vytváření [sestavení se silným názvem](../assembly/strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="c21df-104">Strong naming refers to signing an assembly with a key, producing a [strong-named assembly](../assembly/strong-named.md).</span></span> <span data-ttu-id="c21df-105">Je-li sestavení se silným názvem, vytvoří jedinečnou identitu na základě názvu a čísla verze sestavení a může přispět k prevenci konfliktů sestavení.</span><span class="sxs-lookup"><span data-stu-id="c21df-105">When an assembly is strong-named, it creates a unique identity based on the name and assembly version number, and it can help prevent assembly conflicts.</span></span>

<span data-ttu-id="c21df-106">Nevýhodou na silné názvy je, že .NET Framework ve Windows umožňuje striktní načítání sestavení, jakmile je sestavení silným názvem.</span><span class="sxs-lookup"><span data-stu-id="c21df-106">The downside to strong naming is that the .NET Framework on Windows enables strict loading of assemblies once an assembly is strong named.</span></span> <span data-ttu-id="c21df-107">Odkaz na sestavení se silným názvem se musí přesně shodovat s verzí, na kterou odkazuje sestavení. při použití sestavení vynutí vývojáři [nakonfigurovat přesměrování vazby](../../framework/configure-apps/redirect-assembly-versions.md) .</span><span class="sxs-lookup"><span data-stu-id="c21df-107">A strong-named assembly reference must exactly match the version referenced by an assembly, forcing developers to [configure binding redirects](../../framework/configure-apps/redirect-assembly-versions.md) when using the assembly:</span></span>

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
         <dependentAssembly>
            <assemblyIdentity name="myAssembly" publicKeyToken="32ab4ba45e0a69a1" culture="neutral" />
            <bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0"/>
         </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

<span data-ttu-id="c21df-108">Když vývojáři rozhraní .NET nakladou stížnost na silné pojmenování, k čemu obvykle dochází, je striktní načítání sestavení.</span><span class="sxs-lookup"><span data-stu-id="c21df-108">When .NET developers complain about strong naming, what they're usually complaining about is strict assembly loading.</span></span> <span data-ttu-id="c21df-109">Naštěstí je tento problém izolovaný od .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c21df-109">Fortunately, this issue is isolated to the .NET Framework.</span></span> <span data-ttu-id="c21df-110">.NET Core, Xamarin, UWP a většina dalších implementací .NET nemají striktní načítání sestavení a odstraňují Hlavní nevýhodou silných názvů.</span><span class="sxs-lookup"><span data-stu-id="c21df-110">.NET Core, Xamarin, UWP, and most other .NET implementations don't have strict assembly loading and removes the main downside of strong naming.</span></span>

<span data-ttu-id="c21df-111">Jedním z důležitých aspektů silného pojmenování je to, že je to virové: silné pojmenované sestavení může odkazovat jenom na další silná pojmenovaná sestavení.</span><span class="sxs-lookup"><span data-stu-id="c21df-111">One important aspect of strong naming is that it's viral: a strong named assembly can only reference other strong named assemblies.</span></span> <span data-ttu-id="c21df-112">Pokud vaše knihovna nemá silný název, měli byste vyloučit vývojáře, kteří sestavují aplikaci nebo knihovnu, která potřebuje silné názvy jejich použití.</span><span class="sxs-lookup"><span data-stu-id="c21df-112">If your library isn't strong named, then you have excluded developers who are building an application or library that needs strong naming from using it.</span></span>

<span data-ttu-id="c21df-113">Výhody silného pojmenování:</span><span class="sxs-lookup"><span data-stu-id="c21df-113">The benefits of strong naming are:</span></span>

1. <span data-ttu-id="c21df-114">Sestavení lze odkazovat a používat v jiných sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="c21df-114">The assembly can be referenced and used by other strong-named assemblies.</span></span>
2. <span data-ttu-id="c21df-115">Sestavení může být uloženo v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="c21df-115">The assembly can be stored in the Global Assembly Cache (GAC).</span></span>
3. <span data-ttu-id="c21df-116">Sestavení lze načítat souběžně s jinými verzemi sestavení.</span><span class="sxs-lookup"><span data-stu-id="c21df-116">The assembly can be loaded side by side with other versions of the assembly.</span></span> <span data-ttu-id="c21df-117">Souběžné načítání sestavení je běžně vyžadováno aplikacemi s architekturami modulů plug-in.</span><span class="sxs-lookup"><span data-stu-id="c21df-117">Side-by-side assembly loading is commonly required by applications with plug-in architectures.</span></span>

## <a name="create-strong-named-net-libraries"></a><span data-ttu-id="c21df-118">Vytvořit silně pojmenované knihovny .NET</span><span class="sxs-lookup"><span data-stu-id="c21df-118">Create strong named .NET libraries</span></span>

<span data-ttu-id="c21df-119">Měli byste silně pojmenovat open source knihovny .NET.</span><span class="sxs-lookup"><span data-stu-id="c21df-119">You should strong name your open-source .NET libraries.</span></span> <span data-ttu-id="c21df-120">Silné pojmenování sestavení zajišťuje, aby ho nejvíc uživatelé mohl použít a striktní načítání sestavení ovlivňuje jenom .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c21df-120">Strong naming an assembly ensures the most people can use it, and strict assembly loading only affects the .NET Framework.</span></span>

> [!NOTE]
> <span data-ttu-id="c21df-121">Tyto doprovodné materiály jsou specifické pro veřejně distribuované knihovny .NET, jako jsou knihovny .NET publikované v NuGet.org. Pro většinu aplikací .NET není vyžadováno silné pojmenování a ve výchozím nastavení by se nemělo provádět.</span><span class="sxs-lookup"><span data-stu-id="c21df-121">This guidance is specific to publicly distributed .NET libraries, such as .NET libraries published on NuGet.org. Strong naming is not required by most .NET applications and should not be done by default.</span></span>

<span data-ttu-id="c21df-122">**✔️ zvažte** silné pojmenovávání sestavení vaší knihovny.</span><span class="sxs-lookup"><span data-stu-id="c21df-122">**✔️ CONSIDER** strong naming your library's assemblies.</span></span>

<span data-ttu-id="c21df-123">**✔️ zvažte** přidání klíče silného pojmenování do systému správy zdrojů.</span><span class="sxs-lookup"><span data-stu-id="c21df-123">**✔️ CONSIDER** adding the strong naming key to your source control system.</span></span>

> <span data-ttu-id="c21df-124">Veřejně dostupný klíč umožňuje vývojářům změnit a znovu zkompilovat zdrojový kód knihovny se stejným klíčem.</span><span class="sxs-lookup"><span data-stu-id="c21df-124">A publicly available key lets developers modify and recompile your library source code with the same key.</span></span>
> 
> <span data-ttu-id="c21df-125">Silný klíč pro pojmenovávání by neměl být veřejný, pokud byl v minulosti použit k udělení zvláštních oprávnění ve [scénářích s částečnou důvěryhodností](../../framework/misc/using-libraries-from-partially-trusted-code.md).</span><span class="sxs-lookup"><span data-stu-id="c21df-125">You shouldn't make the strong naming key public if it has been used in the past to give special permissions in [partial-trust scenarios](../../framework/misc/using-libraries-from-partially-trusted-code.md).</span></span> <span data-ttu-id="c21df-126">V opačném případě může dojít k ohrožení stávajících prostředí.</span><span class="sxs-lookup"><span data-stu-id="c21df-126">Otherwise, you might compromise existing environments.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c21df-127">Pokud je požadována identita vydavatele kódu, doporučujeme podepisování prostřednictvím [technologie Authenticode](/windows-hardware/drivers/install/authenticode) a [balíčku NuGet](/nuget/create-packages/sign-a-package) .</span><span class="sxs-lookup"><span data-stu-id="c21df-127">When the identity of the publisher of the code is desired, [Authenticode](/windows-hardware/drivers/install/authenticode) and [NuGet Package Signing](/nuget/create-packages/sign-a-package) are recommended.</span></span> <span data-ttu-id="c21df-128">Zabezpečení přístupu kódu (CAS) by nemělo být použito jako zmírnění zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c21df-128">Code Access Security (CAS) should not be used as a security mitigation.</span></span>

<span data-ttu-id="c21df-129">**✔️ zvažte** zvýšení verze sestavení pouze při změnách hlavní verze, které uživatelům pomůžou snížit přesměrování vazby a jak často se aktualizují.</span><span class="sxs-lookup"><span data-stu-id="c21df-129">**✔️ CONSIDER** incrementing the assembly version on only major version changes to help users reduce binding redirects, and how often they're updated.</span></span>

> <span data-ttu-id="c21df-130">Přečtěte si další informace o způsobu [správy verzí a verzi sestavení](./versioning.md#assembly-version).</span><span class="sxs-lookup"><span data-stu-id="c21df-130">Read more about [versioning and the assembly version](./versioning.md#assembly-version).</span></span>

<span data-ttu-id="c21df-131">**❌** Nepřidávat, odebírat ani měnit silný názvový klíč.</span><span class="sxs-lookup"><span data-stu-id="c21df-131">**❌ DO NOT** add, remove, or change the strong naming key.</span></span>

> <span data-ttu-id="c21df-132">Úprava silného klíče pro pojmenování sestavení změní identitu sestavení a přeruší zkompilovaný kód, který ho používá.</span><span class="sxs-lookup"><span data-stu-id="c21df-132">Modifying an assembly's strong naming key changes the assembly's identity and breaks compiled code that uses it.</span></span> <span data-ttu-id="c21df-133">Další informace najdete v tématu [binární změny v binárním souboru](./breaking-changes.md#binary-breaking-change).</span><span class="sxs-lookup"><span data-stu-id="c21df-133">For more information, see [binary breaking changes](./breaking-changes.md#binary-breaking-change).</span></span>

<span data-ttu-id="c21df-134">**❌** nepublikujte v knihovně silně pojmenované a nedostatečně pojmenované verze vaší knihovny.</span><span class="sxs-lookup"><span data-stu-id="c21df-134">**❌ DO NOT** publish strong-named and non-strong-named versions of your library.</span></span> <span data-ttu-id="c21df-135">Například `Contoso.Api` a `Contoso.Api.StrongNamed`.</span><span class="sxs-lookup"><span data-stu-id="c21df-135">For example, `Contoso.Api` and `Contoso.Api.StrongNamed`.</span></span>

> <span data-ttu-id="c21df-136">Publikování dvou balíčků rozvětvení ekosystém pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="c21df-136">Publishing two packages forks your developer eco-system.</span></span> <span data-ttu-id="c21df-137">Také Pokud aplikace skončí v závislosti na obou balíčcích, může vývojář zaznamenat konflikty názvů typů.</span><span class="sxs-lookup"><span data-stu-id="c21df-137">Also, if an application ends up depending on both packages the developer can encounter type name conflicts.</span></span> <span data-ttu-id="c21df-138">V případě, že se týká .NET, jsou různými typy v různých sestaveních.</span><span class="sxs-lookup"><span data-stu-id="c21df-138">As far as .NET is concerned they are different types in different assemblies.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c21df-139">[Předchozí](cross-platform-targeting.md)
>[Další](nuget.md)</span><span class="sxs-lookup"><span data-stu-id="c21df-139">[Previous](cross-platform-targeting.md)
[Next](nuget.md)</span></span>
