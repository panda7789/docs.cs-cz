---
title: Omezení Xamarin
ms.date: 12/13/2019
description: Popisuje některá omezení, která se objeví při použití Xamarin.
ms.openlocfilehash: 192f25954726919dc66d706e755e0853404b4d85
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447165"
---
# <a name="xamarin-limitations"></a><span data-ttu-id="694bc-103">Omezení Xamarin</span><span class="sxs-lookup"><span data-stu-id="694bc-103">Xamarin limitations</span></span>

<span data-ttu-id="694bc-104">Microsoft. data. sqlite cílí .NET Standard 2,0 a jsou podporovány v Xamarin.</span><span class="sxs-lookup"><span data-stu-id="694bc-104">Microsoft.Data.Sqlite targets .NET Standard 2.0 and is supported on Xamarin.</span></span> <span data-ttu-id="694bc-105">Následující tabulka ukazuje, které platformy výchozí sada SQLitePCLRaw poskytuje nativní binární soubory SQLite pro.</span><span class="sxs-lookup"><span data-stu-id="694bc-105">The following table shows which platforms the default SQLitePCLRaw bundle provides native SQLite binaries for.</span></span> <span data-ttu-id="694bc-106">Podrobnosti o používání jiné sady prostředků nebo poskytování vlastních nativních binárních souborů SQLite najdete v tématu [vlastní verze SQLite](custom-versions.md) .</span><span class="sxs-lookup"><span data-stu-id="694bc-106">See [Custom SQLite versions](custom-versions.md) for details on using a different bundle or providing your own native SQLite binaries.</span></span>

| <span data-ttu-id="694bc-107">Platforma</span><span class="sxs-lookup"><span data-stu-id="694bc-107">Platform</span></span> | <span data-ttu-id="694bc-108">Binární soubory SQLite</span><span class="sxs-lookup"><span data-stu-id="694bc-108">SQLite binaries</span></span> |
| --- | --- |
| <span data-ttu-id="694bc-109">**Xamarin.Android**</span><span class="sxs-lookup"><span data-stu-id="694bc-109">**Xamarin.Android**</span></span> | <span data-ttu-id="694bc-110">—</span><span class="sxs-lookup"><span data-stu-id="694bc-110">—</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm64-v8a` | <span data-ttu-id="694bc-111">✔</span><span class="sxs-lookup"><span data-stu-id="694bc-111">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`armeabi-v7a` | <span data-ttu-id="694bc-112">✔</span><span class="sxs-lookup"><span data-stu-id="694bc-112">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86` | <span data-ttu-id="694bc-113">✔</span><span class="sxs-lookup"><span data-stu-id="694bc-113">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86_64` | <span data-ttu-id="694bc-114">✔</span><span class="sxs-lookup"><span data-stu-id="694bc-114">✔</span></span> |
| <span data-ttu-id="694bc-115">**Xamarin.iOS**</span><span class="sxs-lookup"><span data-stu-id="694bc-115">**Xamarin.iOS**</span></span> | <span data-ttu-id="694bc-116">✔</span><span class="sxs-lookup"><span data-stu-id="694bc-116">✔</span></span> |
| <span data-ttu-id="694bc-117">**Xamarin.Mac**</span><span class="sxs-lookup"><span data-stu-id="694bc-117">**Xamarin.Mac**</span></span> | <span data-ttu-id="694bc-118">✔</span><span class="sxs-lookup"><span data-stu-id="694bc-118">✔</span></span> |
| <span data-ttu-id="694bc-119">**Xamarin. TVOS**</span><span class="sxs-lookup"><span data-stu-id="694bc-119">**Xamarin.TVOS**</span></span> | <span data-ttu-id="694bc-120">✔</span><span class="sxs-lookup"><span data-stu-id="694bc-120">✔</span></span> |
| <span data-ttu-id="694bc-121">**UPW**</span><span class="sxs-lookup"><span data-stu-id="694bc-121">**UWP**</span></span> | <span data-ttu-id="694bc-122">—</span><span class="sxs-lookup"><span data-stu-id="694bc-122">—</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm` | <span data-ttu-id="694bc-123">✔</span><span class="sxs-lookup"><span data-stu-id="694bc-123">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm64` | <span data-ttu-id="694bc-124">✔</span><span class="sxs-lookup"><span data-stu-id="694bc-124">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`x64` | <span data-ttu-id="694bc-125">✔</span><span class="sxs-lookup"><span data-stu-id="694bc-125">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86` | <span data-ttu-id="694bc-126">✔</span><span class="sxs-lookup"><span data-stu-id="694bc-126">✔</span></span> |

## <a name="ios"></a><span data-ttu-id="694bc-127">iOS</span><span class="sxs-lookup"><span data-stu-id="694bc-127">iOS</span></span>

<span data-ttu-id="694bc-128">Microsoft. data. sqlite se pokusí automaticky inicializovat sady SQLitePCLRaw.</span><span class="sxs-lookup"><span data-stu-id="694bc-128">Microsoft.Data.Sqlite tries to automatically initialize SQLitePCLRaw bundles.</span></span> <span data-ttu-id="694bc-129">Vzhledem k tomu, že došlo k omezení kompilace v předstihu (AOT) pro Xamarin. iOS, pokus se nezdaří a zobrazí se následující chyba.</span><span class="sxs-lookup"><span data-stu-id="694bc-129">Unfortunately, because of limitations in the ahead-of-time (AOT) compilation for Xamarin.iOS, the attempt fails and you get the following error.</span></span>

> <span data-ttu-id="694bc-130">Musíte volat `SQLitePCL.raw.SetProvider()`.</span><span class="sxs-lookup"><span data-stu-id="694bc-130">You need to call `SQLitePCL.raw.SetProvider()`.</span></span> <span data-ttu-id="694bc-131">Pokud používáte balíček sady prostředků, je to provedeno voláním `SQLitePCL.Batteries.Init()`.</span><span class="sxs-lookup"><span data-stu-id="694bc-131">If you're using a bundle package, this is done by calling `SQLitePCL.Batteries.Init()`.</span></span>

<span data-ttu-id="694bc-132">Pro inicializaci sady přidejte do aplikace následující řádek kódu před použitím Microsoft. data. sqlite.</span><span class="sxs-lookup"><span data-stu-id="694bc-132">To initialize the bundle, add the following line of code to your app before using Microsoft.Data.Sqlite.</span></span>

```csharp
SQLitePCL.Batteries_V2.Init();
```

## <a name="see-also"></a><span data-ttu-id="694bc-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="694bc-133">See also</span></span>

* [<span data-ttu-id="694bc-134">Asynchronní omezení</span><span class="sxs-lookup"><span data-stu-id="694bc-134">Async limitations</span></span>](async.md)
* [<span data-ttu-id="694bc-135">Vlastní verze SQLite</span><span class="sxs-lookup"><span data-stu-id="694bc-135">Custom SQLite versions</span></span>](custom-versions.md)
