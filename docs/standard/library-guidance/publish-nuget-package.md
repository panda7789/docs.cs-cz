---
title: Publikování balíčku NuGet
description: Doporučení osvědčených postupů pro publikování knihovny .NET NuGet
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 9c8442b52ed2c54d2fb3368a2e886c5fc2b19148
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65640774"
---
# <a name="publishing-a-nuget-package"></a><span data-ttu-id="01492-103">Publikování balíčku NuGet</span><span class="sxs-lookup"><span data-stu-id="01492-103">Publishing a NuGet package</span></span>

<span data-ttu-id="01492-104">Balíčky NuGet se publikovat a použít z úložišť balíčků.</span><span class="sxs-lookup"><span data-stu-id="01492-104">NuGet packages are published and consumed from package repositories.</span></span> <span data-ttu-id="01492-105">I když NuGet.org nejčastěji známé a využité úložiště, publikovat balíčky NuGet mnoho místech:</span><span class="sxs-lookup"><span data-stu-id="01492-105">While NuGet.org is the most widely known and used repository, there are many places to publish NuGet packages:</span></span>

* <span data-ttu-id="01492-106">**[NuGet.org](https://www.nuget.org/)**  slouží jako primární online úložiště balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="01492-106">**[NuGet.org](https://www.nuget.org/)** is the primary online repository for NuGet packages.</span></span> <span data-ttu-id="01492-107">Všech balíčků na NuGet.org jsou veřejně dostupné pro všechny uživatele.</span><span class="sxs-lookup"><span data-stu-id="01492-107">All packages on NuGet.org are publicly available to everyone.</span></span> <span data-ttu-id="01492-108">Ve výchozím nastavení Visual Studio má NuGet.org jako zdroj balíčků a řada vývojářů NuGet.org je pouze úložiště balíčků, kterou budete pracovat.</span><span class="sxs-lookup"><span data-stu-id="01492-108">By default, Visual Studio has NuGet.org as a package source and for many developers NuGet.org is the only package repository they'll interact with.</span></span> <span data-ttu-id="01492-109">NuGet.org je nejlepším místem, kde můžete publikovat stabilní balíčky a balíčky v předběžné verzi, které chcete zpětná vazba komunity na.</span><span class="sxs-lookup"><span data-stu-id="01492-109">NuGet.org is the best place to publish stable packages and pre-release packages that you want community feedback on.</span></span>

* <span data-ttu-id="01492-110">**[MyGet](https://myget.org/)**  je služba úložiště, která podporuje informační kanály vlastních balíčků pro open source projektů.</span><span class="sxs-lookup"><span data-stu-id="01492-110">**[MyGet](https://myget.org/)** is a repository service that supports custom package feeds for open-source projects.</span></span> <span data-ttu-id="01492-111">MyGet veřejné vlastního kanálu je ideálním místem pro publikovat balíčky v předběžné verzi vytvořené služby CI.</span><span class="sxs-lookup"><span data-stu-id="01492-111">A MyGet public custom feed is an ideal place to publish pre-release packages created by your CI service.</span></span> <span data-ttu-id="01492-112">MyGet také poskytuje privátní kanály komerčně.</span><span class="sxs-lookup"><span data-stu-id="01492-112">MyGet also provides private feeds commercially.</span></span>

* <span data-ttu-id="01492-113">A **[místní informační kanál](/nuget/hosting-packages/local-feeds)** umožňuje přistupovat ke všem složku jako úložiště balíčků a zpřístupňuje `*.nupkg` soubory ve složce přístupný balíčkem NuGet.</span><span class="sxs-lookup"><span data-stu-id="01492-113">A **[local feed](/nuget/hosting-packages/local-feeds)** allows you to treat a folder like a package repository and makes the `*.nupkg` files in the folder accessible by NuGet.</span></span> <span data-ttu-id="01492-114">Místní informační kanál je užitečné pro testování před publikováním na NuGet.org balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="01492-114">A local feed is useful for testing a NuGet package before publishing it to NuGet.org.</span></span>

> [!NOTE]
> <span data-ttu-id="01492-115">NuGet.org [neumožňuje balíček odstranit](/nuget/policies/deleting-packages) po nahrání.</span><span class="sxs-lookup"><span data-stu-id="01492-115">NuGet.org [does not allow a package to be deleted](/nuget/policies/deleting-packages) once it is uploaded.</span></span> <span data-ttu-id="01492-116">Balíček může neuvedené tak, že není veřejně viditelné v uživatelském rozhraní ale `*.nupkg` stále je možné stáhnout na obnovení.</span><span class="sxs-lookup"><span data-stu-id="01492-116">A package can be unlisted so that it is not publicly visible in the UI but the `*.nupkg` can still be downloaded on restore.</span></span> <span data-ttu-id="01492-117">Navíc nuget.org nepovoluje duplicitní balíčku verze.</span><span class="sxs-lookup"><span data-stu-id="01492-117">Also, nuget.org does not allow duplicate package versions.</span></span> <span data-ttu-id="01492-118">Chcete-li opravit balíček NuGet s chybou budete muset vyjmutí ze seznamu nesprávné balíčku, zvýší číslo verze a publikujte novou verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="01492-118">To correct a NuGet package with an error you have to unlist the incorrect package, increment the version number and publish a new version of the package.</span></span>

<span data-ttu-id="01492-119">**PROVEĎTE ✔️** [publikovat stabilní balíčky a balíčky v předběžné verzi](/nuget/create-packages/publish-a-package) chcete zpětná vazba komunity na NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="01492-119">**✔️ DO** [publish stable packages and pre-release packages](/nuget/create-packages/publish-a-package) you want community feedback on to NuGet.org.</span></span>

<span data-ttu-id="01492-120">**✔️ ZVAŽTE** publikování balíčky v předběžné verzi MyGet informačního kanálu ze sestavení kontinuální integrace.</span><span class="sxs-lookup"><span data-stu-id="01492-120">**✔️ CONSIDER** publishing pre-release packages to a MyGet feed from a continuous integration build.</span></span>

<span data-ttu-id="01492-121">**✔️ ZVAŽTE** testování balíčků ve vašem vývojovém prostředí pomocí místního kanálu či MyGet.</span><span class="sxs-lookup"><span data-stu-id="01492-121">**✔️ CONSIDER** testing packages in your development environment using a local feed or MyGet.</span></span> <span data-ttu-id="01492-122">Zkontrolujte balíček funguje potom ji publikovat na NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="01492-122">Check the package works then publish it to NuGet.org.</span></span>

## <a name="nugetorg-security"></a><span data-ttu-id="01492-123">NuGet.org security</span><span class="sxs-lookup"><span data-stu-id="01492-123">NuGet.org security</span></span>

<span data-ttu-id="01492-124">Je důležité, že nelze přístup k vašemu účtu NuGet a odeslat škodlivý verzi knihovny.</span><span class="sxs-lookup"><span data-stu-id="01492-124">It's important that bad actors can't access your NuGet account and upload a malicious version of your library.</span></span> <span data-ttu-id="01492-125">NuGet.org nabízí dvojúrovňového ověřování a e-mailové oznámení, když se publikuje balíček.</span><span class="sxs-lookup"><span data-stu-id="01492-125">NuGet.org offers two-factor authentication and email notifications when a package is published.</span></span> <span data-ttu-id="01492-126">Tyto funkce povolit po přihlášení na NuGet.org na **nastavení účtu** stránky.</span><span class="sxs-lookup"><span data-stu-id="01492-126">Enable these features after logging into NuGet.org on the **Account settings** page.</span></span>

<span data-ttu-id="01492-127">![alternativní text](./media/publish-nuget-package/nuget-2fa.png "zabezpečení účtu NuGet")</span><span class="sxs-lookup"><span data-stu-id="01492-127">![alt text](./media/publish-nuget-package/nuget-2fa.png "NuGet Account Security")</span></span>

<span data-ttu-id="01492-128">**PROVEĎTE ✔️** použít účet Microsoft pro přihlášení k NuGet.</span><span class="sxs-lookup"><span data-stu-id="01492-128">**✔️ DO** use a Microsoft account to sign in to NuGet.</span></span>

<span data-ttu-id="01492-129">**PROVEĎTE ✔️** povolení dvoufaktorového ověřování pro přístup k NuGet.</span><span class="sxs-lookup"><span data-stu-id="01492-129">**✔️ DO** enable two-factor authentication for accessing NuGet.</span></span>

<span data-ttu-id="01492-130">**PROVEĎTE ✔️** povolit e-mailové oznámení, když se publikuje balíček.</span><span class="sxs-lookup"><span data-stu-id="01492-130">**✔️ DO** enable email notification when a package is published.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="01492-131">[Předchozí](sourcelink.md)
>[další](versioning.md)</span><span class="sxs-lookup"><span data-stu-id="01492-131">[Previous](sourcelink.md)
[Next](versioning.md)</span></span>
