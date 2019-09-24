---
title: CoreFx zásadní změny – .NET Core
description: Obsahuje seznam nejnovějších změn v rozhraní .NET CoreFx, knihovny základních tříd.
ms.date: 09/20/2019
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7940da342bae6a745b6729ad00c42dbde27a96c8
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71217134"
---
# <a name="corefx-breaking-changes"></a><span data-ttu-id="f24d1-103">CoreFx průlomové změny</span><span class="sxs-lookup"><span data-stu-id="f24d1-103">CoreFx breaking changes</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f24d1-104">Tento článek je v rámci konstrukce.</span><span class="sxs-lookup"><span data-stu-id="f24d1-104">This article is under construction.</span></span> <span data-ttu-id="f24d1-105">Nejedná se o úplný seznam nejnovějších změn .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f24d1-105">This is not a complete list of .NET Core breaking changes.</span></span> <span data-ttu-id="f24d1-106">Další informace o nejnovějších změnách .NET Core můžete v úložišti dotnet/Docs na GitHubu kontrolovat jednotlivé [problémy se změnami](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Abreaking-change) .</span><span class="sxs-lookup"><span data-stu-id="f24d1-106">For more information on .NET Core breaking changes, you can examine individual [breaking changes issues](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Abreaking-change) in the dotnet/docs repository on GitHub.</span></span> 

<span data-ttu-id="f24d1-107">Následující seznam uvádí CoreFx zásadní změny ve verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f24d1-107">The following is a list of CoreFx breaking changes by .NET Core version.</span></span> <span data-ttu-id="f24d1-108">CoreFx poskytuje primitivní a další obecné typy používané .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f24d1-108">CoreFx provides the primitives and other general types used by .NET Core.</span></span>

## <a name="net-core-30-preview-7"></a><span data-ttu-id="f24d1-109">.NET Core 3,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="f24d1-109">.NET Core 3.0 Preview 7</span></span>

[!INCLUDE[JsonElement API changes](~/includes/core-changes/corefx/jsonelement-api-changes.md)]

## <a name="net-core-30-preview-8"></a><span data-ttu-id="f24d1-110">.NET Core 3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="f24d1-110">.NET Core 3.0 Preview 8</span></span>

[!INCLUDE[Change in semantics of (string)null in Utf8JsonWriter](~/includes/core-changes/corefx/change-in-null-in-utf8jsonwriter.md)]

***

[!INCLUDE[JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument](~/includes/core-changes/corefx/jsonencodedtext-encode-has-additional-argument.md)]

***

[!INCLUDE[JsonFactoryConverter.CreateConverter signature changed](~/includes/core-changes/corefx/jsonfactoryconverter-createconverter.md)]

## <a name="net-core-30-preview-9"></a><span data-ttu-id="f24d1-111">.NET Core 3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="f24d1-111">.NET Core 3.0 Preview 9</span></span>

[!INCLUDE[Json serializer exception type changed from JsonException to NotSupportedException](~/includes/core-changes/corefx/serializer-throws-notsupportedexception.md)]

## <a name="net-core-30"></a><span data-ttu-id="f24d1-112">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f24d1-112">.NET Core 3.0</span></span>

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/version-information-changes.md)]

***

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

***

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/floating-point-changes.md)]

***

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/move-invalidasynchronousstateexception.md)]

***

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/net-core-3-0-follows-unicode-utf8-best-practices.md)]

***

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/move-typedescriptionproviderattribute.md)]

***

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/ziparchiveentry-and-inconsistent-entry-sizes.md)]

