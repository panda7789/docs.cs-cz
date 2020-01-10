---
title: Publikování balíčku NuGet
description: Doporučení osvědčených postupů pro publikování knihoven .NET do NuGet.
ms.date: 10/02/2018
ms.openlocfilehash: e567fe3f7e00bf322cdd50786e50128961107469
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706462"
---
# <a name="publishing-a-nuget-package"></a><span data-ttu-id="37263-103">Publikování balíčku NuGet</span><span class="sxs-lookup"><span data-stu-id="37263-103">Publishing a NuGet package</span></span>

<span data-ttu-id="37263-104">Balíčky NuGet se zveřejňují a spotřebovávají z úložišť balíčků.</span><span class="sxs-lookup"><span data-stu-id="37263-104">NuGet packages are published and consumed from package repositories.</span></span> <span data-ttu-id="37263-105">I když je NuGet.org nejčastěji známé a používané úložiště, je k dispozici mnoho míst pro publikování balíčků NuGet:</span><span class="sxs-lookup"><span data-stu-id="37263-105">While NuGet.org is the most widely known and used repository, there are many places to publish NuGet packages:</span></span>

* <span data-ttu-id="37263-106">**[NuGet.org](https://www.nuget.org/)** je primární online úložiště pro balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="37263-106">**[NuGet.org](https://www.nuget.org/)** is the primary online repository for NuGet packages.</span></span> <span data-ttu-id="37263-107">Všechny balíčky v NuGet.org jsou veřejně dostupné všem uživatelům.</span><span class="sxs-lookup"><span data-stu-id="37263-107">All packages on NuGet.org are publicly available to everyone.</span></span> <span data-ttu-id="37263-108">Ve výchozím nastavení sada Visual Studio NuGet.org jako zdroj balíčku a pro mnoho vývojářů NuGet.org je jediným úložištěm balíčků, se kterým budou pracovat.</span><span class="sxs-lookup"><span data-stu-id="37263-108">By default, Visual Studio has NuGet.org as a package source and for many developers NuGet.org is the only package repository they'll interact with.</span></span> <span data-ttu-id="37263-109">NuGet.org je to nejlepší místo pro publikování stabilních balíčků a předběžných vydaných balíčků, na které chcete komunitu poskytovat názory.</span><span class="sxs-lookup"><span data-stu-id="37263-109">NuGet.org is the best place to publish stable packages and pre-release packages that you want community feedback on.</span></span>

* <span data-ttu-id="37263-110">**[MyGet](https://myget.org/)** je služba úložiště, která podporuje vlastní kanály balíčků pro open source projekty.</span><span class="sxs-lookup"><span data-stu-id="37263-110">**[MyGet](https://myget.org/)** is a repository service that supports custom package feeds for open-source projects.</span></span> <span data-ttu-id="37263-111">Vlastní informační kanál MyGet je ideálním místem pro publikování předběžných verzí balíčků vytvořených službou CI.</span><span class="sxs-lookup"><span data-stu-id="37263-111">A MyGet public custom feed is an ideal place to publish pre-release packages created by your CI service.</span></span> <span data-ttu-id="37263-112">MyGet také poskytuje soukromé informační kanály komerčně.</span><span class="sxs-lookup"><span data-stu-id="37263-112">MyGet also provides private feeds commercially.</span></span>

* <span data-ttu-id="37263-113">**[Místní kanál](/nuget/hosting-packages/local-feeds)** umožňuje považovat složku jako úložiště balíčků a zpřístupňuje soubory `*.nupkg` ve složce přístupné pomocí NuGet.</span><span class="sxs-lookup"><span data-stu-id="37263-113">A **[local feed](/nuget/hosting-packages/local-feeds)** allows you to treat a folder like a package repository and makes the `*.nupkg` files in the folder accessible by NuGet.</span></span> <span data-ttu-id="37263-114">Místní kanál je vhodný pro otestování balíčku NuGet před jeho publikováním na NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="37263-114">A local feed is useful for testing a NuGet package before publishing it to NuGet.org.</span></span>

> [!NOTE]
> <span data-ttu-id="37263-115">NuGet.org [neumožňuje odstranění balíčku](/nuget/policies/deleting-packages) po jeho nahrání.</span><span class="sxs-lookup"><span data-stu-id="37263-115">NuGet.org [does not allow a package to be deleted](/nuget/policies/deleting-packages) once it is uploaded.</span></span> <span data-ttu-id="37263-116">Balíček může být nezobrazený, aby nebyl veřejně viditelný v uživatelském rozhraní, ale `*.nupkg` se pořád dá stáhnout při obnovení.</span><span class="sxs-lookup"><span data-stu-id="37263-116">A package can be unlisted so that it is not publicly visible in the UI but the `*.nupkg` can still be downloaded on restore.</span></span> <span data-ttu-id="37263-117">Nuget.org také nepovoluje duplicitní verze balíčků.</span><span class="sxs-lookup"><span data-stu-id="37263-117">Also, nuget.org does not allow duplicate package versions.</span></span> <span data-ttu-id="37263-118">Chcete-li opravit balíček NuGet s chybou, je třeba zrušit seznam nesprávného balíčku, zvýšit číslo verze a publikovat novou verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="37263-118">To correct a NuGet package with an error you have to unlist the incorrect package, increment the version number and publish a new version of the package.</span></span>

<span data-ttu-id="37263-119">**✔️** [publikovat stabilní balíčky a předběžné verze balíčků](/nuget/create-packages/publish-a-package) , ve kterých chcete, aby se komunitní názory na NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="37263-119">**✔️ DO** [publish stable packages and pre-release packages](/nuget/create-packages/publish-a-package) you want community feedback on to NuGet.org.</span></span>

<span data-ttu-id="37263-120">**✔️ zvažte** publikování předběžných verzí balíčků do MyGet kanálu ze sestavení průběžné integrace.</span><span class="sxs-lookup"><span data-stu-id="37263-120">**✔️ CONSIDER** publishing pre-release packages to a MyGet feed from a continuous integration build.</span></span>

<span data-ttu-id="37263-121">**✔️ zvažte** testování balíčků ve vývojovém prostředí pomocí místního informačního kanálu nebo MyGet.</span><span class="sxs-lookup"><span data-stu-id="37263-121">**✔️ CONSIDER** testing packages in your development environment using a local feed or MyGet.</span></span> <span data-ttu-id="37263-122">Zkontrolujte, jestli balíček funguje, a pak ho publikujte na NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="37263-122">Check the package works then publish it to NuGet.org.</span></span>

## <a name="nugetorg-security"></a><span data-ttu-id="37263-123">Zabezpečení NuGet.org</span><span class="sxs-lookup"><span data-stu-id="37263-123">NuGet.org security</span></span>

<span data-ttu-id="37263-124">Je důležité, aby chybné objekty actor měly přístup k vašemu účtu NuGet a nahráli škodlivou verzi vaší knihovny.</span><span class="sxs-lookup"><span data-stu-id="37263-124">It's important that bad actors can't access your NuGet account and upload a malicious version of your library.</span></span> <span data-ttu-id="37263-125">NuGet.org nabízí dvojúrovňové ověřování a e-mailová oznámení při publikování balíčku.</span><span class="sxs-lookup"><span data-stu-id="37263-125">NuGet.org offers two-factor authentication and email notifications when a package is published.</span></span> <span data-ttu-id="37263-126">Tyto funkce povolte po přihlášení k NuGet.org na stránce **Nastavení účtu** .</span><span class="sxs-lookup"><span data-stu-id="37263-126">Enable these features after logging into NuGet.org on the **Account settings** page.</span></span>

<span data-ttu-id="37263-127">![alternativní text](./media/publish-nuget-package/nuget-2fa.png "Zabezpečení účtu NuGet")</span><span class="sxs-lookup"><span data-stu-id="37263-127">![alt text](./media/publish-nuget-package/nuget-2fa.png "NuGet Account Security")</span></span>

<span data-ttu-id="37263-128">k přihlášení do NuGet se **✔️** použít účet Microsoft.</span><span class="sxs-lookup"><span data-stu-id="37263-128">**✔️ DO** use a Microsoft account to sign in to NuGet.</span></span>

<span data-ttu-id="37263-129">**✔️** povolit dvojúrovňové ověřování pro přístup k nugetu.</span><span class="sxs-lookup"><span data-stu-id="37263-129">**✔️ DO** enable two-factor authentication for accessing NuGet.</span></span>

<span data-ttu-id="37263-130">Při publikování balíčku **✔️** povolit e-mailová oznámení.</span><span class="sxs-lookup"><span data-stu-id="37263-130">**✔️ DO** enable email notification when a package is published.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="37263-131">[Předchozí](sourcelink.md)
>[Další](versioning.md)</span><span class="sxs-lookup"><span data-stu-id="37263-131">[Previous](sourcelink.md)
[Next](versioning.md)</span></span>
