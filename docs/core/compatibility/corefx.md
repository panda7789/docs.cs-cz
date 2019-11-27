---
title: Zásadní změny v knihovně základních tříd – .NET Core
description: Obsahuje seznam nejnovějších změn v rozhraní .NET CoreFx, knihovny základních tříd.
ms.date: 09/20/2019
ms.openlocfilehash: 859eb30b8f6fa48350f81ee1822247e72698fead
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429192"
---
# <a name="corefx-breaking-changes"></a><span data-ttu-id="c1a92-103">CoreFx průlomové změny</span><span class="sxs-lookup"><span data-stu-id="c1a92-103">CoreFx breaking changes</span></span>

<span data-ttu-id="c1a92-104">Následující seznam uvádí CoreFx zásadní změny ve verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c1a92-104">The following is a list of CoreFx breaking changes by .NET Core version.</span></span> <span data-ttu-id="c1a92-105">CoreFx poskytuje primitivní a další obecné typy používané .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c1a92-105">CoreFx provides the primitives and other general types used by .NET Core.</span></span>

## <a name="net-core-30-preview-7"></a><span data-ttu-id="c1a92-106">.NET Core 3,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="c1a92-106">.NET Core 3.0 Preview 7</span></span>

[!INCLUDE[JsonElement API changes](~/includes/core-changes/corefx/jsonelement-api-changes.md)]

## <a name="net-core-30-preview-8"></a><span data-ttu-id="c1a92-107">.NET Core 3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="c1a92-107">.NET Core 3.0 Preview 8</span></span>

[!INCLUDE[Change in semantics of (string)null in Utf8JsonWriter](~/includes/core-changes/corefx/change-in-null-in-utf8jsonwriter.md)]

***

[!INCLUDE[JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument](~/includes/core-changes/corefx/jsonencodedtext-encode-has-additional-argument.md)]

***

[!INCLUDE[JsonFactoryConverter.CreateConverter signature changed](~/includes/core-changes/corefx/jsonfactoryconverter-createconverter.md)]

## <a name="net-core-30-preview-9"></a><span data-ttu-id="c1a92-108">.NET Core 3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="c1a92-108">.NET Core 3.0 Preview 9</span></span>

[!INCLUDE[Json serializer exception type changed from JsonException to NotSupportedException](~/includes/core-changes/corefx/serializer-throws-notsupportedexception.md)]

## <a name="net-core-30"></a><span data-ttu-id="c1a92-109">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c1a92-109">.NET Core 3.0</span></span>

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/version-information-changes.md)]

***

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

***

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/floating-point-changes.md)]

***

[!INCLUDE[Floating-point parsing operations no longer fail or throw an OverflowException](~/includes/core-changes/corefx/floating-point-parsing-does-not-overflow.md)]

***

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/move-invalidasynchronousstateexception.md)]

***

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/net-core-3-0-follows-unicode-utf8-best-practices.md)]

***

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/move-typedescriptionproviderattribute.md)]

***

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/ziparchiveentry-and-inconsistent-entry-sizes.md)]
