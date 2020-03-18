---
title: Publikování balíčku NuGet
description: Doporučení osvědčených postupů pro publikování knihoven .NET na NuGet.
ms.date: 10/02/2018
ms.openlocfilehash: 089c660bc51252c6295858b1462ae59bde968564
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "76744553"
---
# <a name="publishing-a-nuget-package"></a><span data-ttu-id="4e1d0-103">Publikování balíčku NuGet</span><span class="sxs-lookup"><span data-stu-id="4e1d0-103">Publishing a NuGet package</span></span>

<span data-ttu-id="4e1d0-104">Balíčky NuGet jsou publikovány a spotřebovávány z úložišť balíčků.</span><span class="sxs-lookup"><span data-stu-id="4e1d0-104">NuGet packages are published and consumed from package repositories.</span></span> <span data-ttu-id="4e1d0-105">Zatímco NuGet.org je nejznámější a nejpoužívanější úložiště, existuje mnoho míst k publikování balíčků NuGet:</span><span class="sxs-lookup"><span data-stu-id="4e1d0-105">While NuGet.org is the most widely known and used repository, there are many places to publish NuGet packages:</span></span>

* <span data-ttu-id="4e1d0-106">**[NuGet.org](https://www.nuget.org/)** je primární online úložiště pro balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="4e1d0-106">**[NuGet.org](https://www.nuget.org/)** is the primary online repository for NuGet packages.</span></span> <span data-ttu-id="4e1d0-107">Všechny balíčky na NuGet.org jsou veřejně dostupné všem.</span><span class="sxs-lookup"><span data-stu-id="4e1d0-107">All packages on NuGet.org are publicly available to everyone.</span></span> <span data-ttu-id="4e1d0-108">Ve výchozím nastavení visual studio NuGet.org jako zdroj balíčku a pro mnoho vývojářů NuGet.org je pouze úložiště balíčků, které budou pracovat.</span><span class="sxs-lookup"><span data-stu-id="4e1d0-108">By default, Visual Studio has NuGet.org as a package source and for many developers NuGet.org is the only package repository they'll interact with.</span></span> <span data-ttu-id="4e1d0-109">NuGet.org je nejlepší místo pro publikování stabilních balíčků a předběžných verzí balíčků, na které chcete získat zpětnou vazbu komunity.</span><span class="sxs-lookup"><span data-stu-id="4e1d0-109">NuGet.org is the best place to publish stable packages and pre-release packages that you want community feedback on.</span></span>

* <span data-ttu-id="4e1d0-110">**[MyGet](https://myget.org/)** je služba úložiště, která podporuje vlastní kanály balíčků pro open source projekty.</span><span class="sxs-lookup"><span data-stu-id="4e1d0-110">**[MyGet](https://myget.org/)** is a repository service that supports custom package feeds for open-source projects.</span></span> <span data-ttu-id="4e1d0-111">Veřejný vlastní zdroj MyGet je ideálním místem pro publikování předběžných balíčků vytvořených vaší službou CI.</span><span class="sxs-lookup"><span data-stu-id="4e1d0-111">A MyGet public custom feed is an ideal place to publish pre-release packages created by your CI service.</span></span> <span data-ttu-id="4e1d0-112">MyGet také poskytuje soukromé kanály komerčně.</span><span class="sxs-lookup"><span data-stu-id="4e1d0-112">MyGet also provides private feeds commercially.</span></span>

* <span data-ttu-id="4e1d0-113">**[Místní informační kanál](/nuget/hosting-packages/local-feeds)** umožňuje zacházet se složkou jako `*.nupkg` úložiště balíčků a zpřístupňuje soubory ve složce nuget.</span><span class="sxs-lookup"><span data-stu-id="4e1d0-113">A **[local feed](/nuget/hosting-packages/local-feeds)** allows you to treat a folder like a package repository and makes the `*.nupkg` files in the folder accessible by NuGet.</span></span> <span data-ttu-id="4e1d0-114">Místní zdroj je užitečné pro testování balíčku NuGet před publikováním na NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="4e1d0-114">A local feed is useful for testing a NuGet package before publishing it to NuGet.org.</span></span>

> [!NOTE]
> <span data-ttu-id="4e1d0-115">NuGet.org [neumožňuje odstranění balíčku](/nuget/policies/deleting-packages) po jeho odeslání.</span><span class="sxs-lookup"><span data-stu-id="4e1d0-115">NuGet.org [does not allow a package to be deleted](/nuget/policies/deleting-packages) once it is uploaded.</span></span> <span data-ttu-id="4e1d0-116">Balíček může být neuveden, takže není veřejně viditelný v `*.nupkg` ui, ale lze jej stále stáhnout při obnovení.</span><span class="sxs-lookup"><span data-stu-id="4e1d0-116">A package can be unlisted so that it is not publicly visible in the UI but the `*.nupkg` can still be downloaded on restore.</span></span> <span data-ttu-id="4e1d0-117">nuget.org také neumožňuje duplicitní verze balíčků.</span><span class="sxs-lookup"><span data-stu-id="4e1d0-117">Also, nuget.org does not allow duplicate package versions.</span></span> <span data-ttu-id="4e1d0-118">Chcete-li opravit balíček NuGet s chybou, musíte zrušit seznam nesprávného balíčku, vzrůst číslo verze a publikovat novou verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="4e1d0-118">To correct a NuGet package with an error you have to unlist the incorrect package, increment the version number and publish a new version of the package.</span></span>

<span data-ttu-id="4e1d0-119">✔️ DO [publikovat stabilní balíčky a předběžné verze balíčků,](/nuget/create-packages/publish-a-package) které chcete, aby komunita zpětná vazba na NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="4e1d0-119">✔️ DO [publish stable packages and pre-release packages](/nuget/create-packages/publish-a-package) you want community feedback on to NuGet.org.</span></span>

<span data-ttu-id="4e1d0-120">✔️ ZVAŽTe publikování předběžných balíčků do informačního kanálu MyGet z průběžné integrace sestavení.</span><span class="sxs-lookup"><span data-stu-id="4e1d0-120">✔️ CONSIDER publishing pre-release packages to a MyGet feed from a continuous integration build.</span></span>

<span data-ttu-id="4e1d0-121">✔️ zvážit testování balíčků ve vývojovém prostředí pomocí místního kanálu nebo MyGet.</span><span class="sxs-lookup"><span data-stu-id="4e1d0-121">✔️ CONSIDER testing packages in your development environment using a local feed or MyGet.</span></span> <span data-ttu-id="4e1d0-122">Zkontrolujte, zda balíček funguje a pak publikovat do NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="4e1d0-122">Check the package works then publish it to NuGet.org.</span></span>

## <a name="nugetorg-security"></a><span data-ttu-id="4e1d0-123">NuGet.org zabezpečení</span><span class="sxs-lookup"><span data-stu-id="4e1d0-123">NuGet.org security</span></span>

<span data-ttu-id="4e1d0-124">Je důležité, aby chybní herci nemohli získat přístup k vašemu účtu NuGet a nahrát škodlivou verzi knihovny.</span><span class="sxs-lookup"><span data-stu-id="4e1d0-124">It's important that bad actors can't access your NuGet account and upload a malicious version of your library.</span></span> <span data-ttu-id="4e1d0-125">NuGet.org nabízí dvoufaktorové ověřování a e-mailová oznámení při publikování balíčku.</span><span class="sxs-lookup"><span data-stu-id="4e1d0-125">NuGet.org offers two-factor authentication and email notifications when a package is published.</span></span> <span data-ttu-id="4e1d0-126">Po přihlášení k NuGet.org na stránce **Nastavení účtu** povolte tyto funkce.</span><span class="sxs-lookup"><span data-stu-id="4e1d0-126">Enable these features after logging into NuGet.org on the **Account settings** page.</span></span>

<span data-ttu-id="4e1d0-127">![alternativní text](./media/publish-nuget-package/nuget-2fa.png "Zabezpečení účtu NuGet")</span><span class="sxs-lookup"><span data-stu-id="4e1d0-127">![alt text](./media/publish-nuget-package/nuget-2fa.png "NuGet Account Security")</span></span>

<span data-ttu-id="4e1d0-128">✔️ do použít účet Microsoft pro přihlášení k NuGet.</span><span class="sxs-lookup"><span data-stu-id="4e1d0-128">✔️ DO use a Microsoft account to sign in to NuGet.</span></span>

<span data-ttu-id="4e1d0-129">✔️ DO povolit dvoufaktorové ověřování pro přístup k NuGet.</span><span class="sxs-lookup"><span data-stu-id="4e1d0-129">✔️ DO enable two-factor authentication for accessing NuGet.</span></span>

<span data-ttu-id="4e1d0-130">✔️ do povolit e-mailové oznámení při publikování balíčku.</span><span class="sxs-lookup"><span data-stu-id="4e1d0-130">✔️ DO enable email notification when a package is published.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="4e1d0-131">[Předchozí](sourcelink.md)
>[další](versioning.md)</span><span class="sxs-lookup"><span data-stu-id="4e1d0-131">[Previous](sourcelink.md)
[Next](versioning.md)</span></span>
