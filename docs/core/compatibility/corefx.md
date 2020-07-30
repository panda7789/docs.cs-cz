---
title: Přerušující změny knihovny základních tříd
description: Obsahuje seznam nejnovějších změn v základních knihovnách .NET.
ms.date: 07/27/2020
ms.openlocfilehash: d34cd2e7ba1122b11921eefaee2ed55ba0c8df8d
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302994"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="da6ae-103">Základní knihovny .NET – přerušující změny</span><span class="sxs-lookup"><span data-stu-id="da6ae-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="da6ae-104">Základní knihovny .NET poskytují primitivní a další obecné typy používané .NET Core.</span><span class="sxs-lookup"><span data-stu-id="da6ae-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="da6ae-105">Na této stránce jsou popsány následující přerušující se změny:</span><span class="sxs-lookup"><span data-stu-id="da6ae-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="da6ae-106">Zásadní změna</span><span class="sxs-lookup"><span data-stu-id="da6ae-106">Breaking change</span></span> | <span data-ttu-id="da6ae-107">Představená verze</span><span class="sxs-lookup"><span data-stu-id="da6ae-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="da6ae-108">Vector \<T> vždy vyvolá NotSupportedException pro nepodporované typy</span><span class="sxs-lookup"><span data-stu-id="da6ae-108">Vector\<T> always throws NotSupportedException for unsupported types</span></span>](#vectort-always-throws-notsupportedexception-for-unsupported-types) | <span data-ttu-id="da6ae-109">5.0</span><span class="sxs-lookup"><span data-stu-id="da6ae-109">5.0</span></span> |
| [<span data-ttu-id="da6ae-110">Výchozí ActivityIdFormat je W3C.</span><span class="sxs-lookup"><span data-stu-id="da6ae-110">Default ActivityIdFormat is W3C</span></span>](#default-activityidformat-is-w3c) | <span data-ttu-id="da6ae-111">5.0</span><span class="sxs-lookup"><span data-stu-id="da6ae-111">5.0</span></span> |
| [<span data-ttu-id="da6ae-112">Změna chování pro Vector2. lerp a Vector4. lerp</span><span class="sxs-lookup"><span data-stu-id="da6ae-112">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>](#behavior-change-for-vector2lerp-and-vector4lerp) | <span data-ttu-id="da6ae-113">5.0</span><span class="sxs-lookup"><span data-stu-id="da6ae-113">5.0</span></span> |
| [<span data-ttu-id="da6ae-114">Metody SSE a SSE2 CompareGreaterThan správně zpracovávají vstupy NaN.</span><span class="sxs-lookup"><span data-stu-id="da6ae-114">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="da6ae-115">5.0</span><span class="sxs-lookup"><span data-stu-id="da6ae-115">5.0</span></span> |
| [<span data-ttu-id="da6ae-116">Sada CounterSet. provedení operace CreateCounterSetInstance nyní vyvolá chybu InvalidOperationException, pokud již instance existuje.</span><span class="sxs-lookup"><span data-stu-id="da6ae-116">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exist</span></span>](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | <span data-ttu-id="da6ae-117">5.0</span><span class="sxs-lookup"><span data-stu-id="da6ae-117">5.0</span></span> |
| [<span data-ttu-id="da6ae-118">Balíček Microsoft. DotNet. PlatformAbstractions se odebral.</span><span class="sxs-lookup"><span data-stu-id="da6ae-118">Microsoft.DotNet.PlatformAbstractions package removed</span></span>](#microsoftdotnetplatformabstractions-package-removed) | <span data-ttu-id="da6ae-119">5.0</span><span class="sxs-lookup"><span data-stu-id="da6ae-119">5.0</span></span> |
| [<span data-ttu-id="da6ae-120">Rozhraní API, která verze sestav nyní hlásí produkt a nikoli verzi souboru</span><span class="sxs-lookup"><span data-stu-id="da6ae-120">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="da6ae-121">3.0</span><span class="sxs-lookup"><span data-stu-id="da6ae-121">3.0</span></span> |
| [<span data-ttu-id="da6ae-122">Vlastní instance EncoderFallbackBuffer se nemůžou vrátit rekurzivně.</span><span class="sxs-lookup"><span data-stu-id="da6ae-122">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="da6ae-123">3.0</span><span class="sxs-lookup"><span data-stu-id="da6ae-123">3.0</span></span> |
| [<span data-ttu-id="da6ae-124">Změny chování při formátování a analýze plovoucí desetinné čárky</span><span class="sxs-lookup"><span data-stu-id="da6ae-124">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="da6ae-125">3.0</span><span class="sxs-lookup"><span data-stu-id="da6ae-125">3.0</span></span> |
| [<span data-ttu-id="da6ae-126">Operace analýzy s plovoucí desetinnou čárkou již nejsou úspěšné nebo vyvolávají výjimku OverflowException</span><span class="sxs-lookup"><span data-stu-id="da6ae-126">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="da6ae-127">3.0</span><span class="sxs-lookup"><span data-stu-id="da6ae-127">3.0</span></span> |
| [<span data-ttu-id="da6ae-128">InvalidAsynchronousStateException – přesunuté do jiného sestavení</span><span class="sxs-lookup"><span data-stu-id="da6ae-128">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="da6ae-129">3.0</span><span class="sxs-lookup"><span data-stu-id="da6ae-129">3.0</span></span> |
| [<span data-ttu-id="da6ae-130">Výměna chybně formátovaných sekvencí UTF-8 se řídí pokyny pro kódování Unicode</span><span class="sxs-lookup"><span data-stu-id="da6ae-130">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="da6ae-131">3.0</span><span class="sxs-lookup"><span data-stu-id="da6ae-131">3.0</span></span> |
| [<span data-ttu-id="da6ae-132">TypeDescriptionProviderAttribute přesunuté do jiného sestavení</span><span class="sxs-lookup"><span data-stu-id="da6ae-132">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="da6ae-133">3.0</span><span class="sxs-lookup"><span data-stu-id="da6ae-133">3.0</span></span> |
| [<span data-ttu-id="da6ae-134">ZipArchiveEntry už nezpracovává archivy s nekonzistentními velikostmi záznamů.</span><span class="sxs-lookup"><span data-stu-id="da6ae-134">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="da6ae-135">3.0</span><span class="sxs-lookup"><span data-stu-id="da6ae-135">3.0</span></span> |
| [<span data-ttu-id="da6ae-136">Typ výjimky serializátoru JSON se změnil z JsonException na NotSupportedException.</span><span class="sxs-lookup"><span data-stu-id="da6ae-136">JSON serializer exception type changed from JsonException to NotSupportedException</span></span>](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | <span data-ttu-id="da6ae-137">3.0</span><span class="sxs-lookup"><span data-stu-id="da6ae-137">3.0</span></span> |
| [<span data-ttu-id="da6ae-138">Změna v sémantikě (String) null v Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="da6ae-138">Change in semantics of (string)null in Utf8JsonWriter</span></span>](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | <span data-ttu-id="da6ae-139">3.0</span><span class="sxs-lookup"><span data-stu-id="da6ae-139">3.0</span></span> |
| [<span data-ttu-id="da6ae-140">Metody JsonEncodedText. Encode mají další argument JavaScriptEncoder.</span><span class="sxs-lookup"><span data-stu-id="da6ae-140">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | <span data-ttu-id="da6ae-141">3.0</span><span class="sxs-lookup"><span data-stu-id="da6ae-141">3.0</span></span> |
| [<span data-ttu-id="da6ae-142">Změnil se podpis JsonFactoryConverter. CreateConverter.</span><span class="sxs-lookup"><span data-stu-id="da6ae-142">JsonFactoryConverter.CreateConverter signature changed</span></span>](#jsonfactoryconvertercreateconverter-signature-changed) | <span data-ttu-id="da6ae-143">3.0</span><span class="sxs-lookup"><span data-stu-id="da6ae-143">3.0</span></span> |
| [<span data-ttu-id="da6ae-144">Změny rozhraní API JsonElement</span><span class="sxs-lookup"><span data-stu-id="da6ae-144">JsonElement API changes</span></span>](#jsonelement-api-changes) | <span data-ttu-id="da6ae-145">3.0</span><span class="sxs-lookup"><span data-stu-id="da6ae-145">3.0</span></span> |
| [<span data-ttu-id="da6ae-146">Parametr FieldInfo. SetValue vyvolá výjimku pro statická pole pouze pro init.</span><span class="sxs-lookup"><span data-stu-id="da6ae-146">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="da6ae-147">3.0</span><span class="sxs-lookup"><span data-stu-id="da6ae-147">3.0</span></span> |
| [<span data-ttu-id="da6ae-148">Soukromá pole přidaná k předdefinovaným typům struktury</span><span class="sxs-lookup"><span data-stu-id="da6ae-148">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="da6ae-149">2.1</span><span class="sxs-lookup"><span data-stu-id="da6ae-149">2.1</span></span> |
| [<span data-ttu-id="da6ae-150">Změna výchozí hodnoty UseShellExecute objektu Process</span><span class="sxs-lookup"><span data-stu-id="da6ae-150">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="da6ae-151">2.1</span><span class="sxs-lookup"><span data-stu-id="da6ae-151">2.1</span></span> |
| [<span data-ttu-id="da6ae-152">Verze OpenSSL v macOS</span><span class="sxs-lookup"><span data-stu-id="da6ae-152">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="da6ae-153">2.1</span><span class="sxs-lookup"><span data-stu-id="da6ae-153">2.1</span></span> |
| [<span data-ttu-id="da6ae-154">UnauthorizedAccessException vyvolaná atributy SystemInfo.</span><span class="sxs-lookup"><span data-stu-id="da6ae-154">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="da6ae-155">1.0</span><span class="sxs-lookup"><span data-stu-id="da6ae-155">1.0</span></span> |
| [<span data-ttu-id="da6ae-156">Manipulace s poškozenými výjimkami stavu procesu není podporována.</span><span class="sxs-lookup"><span data-stu-id="da6ae-156">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="da6ae-157">1.0</span><span class="sxs-lookup"><span data-stu-id="da6ae-157">1.0</span></span> |
| [<span data-ttu-id="da6ae-158">Vlastnosti objekt UriBuilder protokolu už neobsahují úvodní znaky.</span><span class="sxs-lookup"><span data-stu-id="da6ae-158">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="da6ae-159">1.0</span><span class="sxs-lookup"><span data-stu-id="da6ae-159">1.0</span></span> |
| [<span data-ttu-id="da6ae-160">Process. StartInfo vyvolá InvalidOperationException pro procesy, které jste nespustili.</span><span class="sxs-lookup"><span data-stu-id="da6ae-160">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="da6ae-161">1.0</span><span class="sxs-lookup"><span data-stu-id="da6ae-161">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="da6ae-162">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="da6ae-162">.NET 5.0</span></span>

[!INCLUDE [vectort-throws-notsupportedexception](../../../includes/core-changes/corefx/5.0/vectort-throws-notsupportedexception.md)]

***

[!INCLUDE [default-activityidformat-changed](../../../includes/core-changes/corefx/5.0/default-activityidformat-changed.md)]

***

[!INCLUDE [vector-lerp-behavior-change](../../../includes/core-changes/corefx/5.0/vector-lerp-behavior-change.md)]

***

[!INCLUDE [sse-comparegreaterthan-intrinsics](../../../includes/core-changes/corefx/5.0/sse-comparegreaterthan-intrinsics.md)]

***

[!INCLUDE [createcountersetinstance-throws-invalidoperation](../../../includes/core-changes/corefx/5.0/createcountersetinstance-throws-invalidoperation.md)]

***

[!INCLUDE [platformabstractions-package-removed](../../../includes/core-changes/corefx/5.0/platformabstractions-package-removed.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="da6ae-163">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="da6ae-163">.NET Core 3.0</span></span>

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

***

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/3.0/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

***

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/3.0/floating-point-changes.md)]

***

[!INCLUDE[Floating-point parsing operations no longer fail or throw an OverflowException](~/includes/core-changes/corefx/3.0/floating-point-parsing-does-not-overflow.md)]

***

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/3.0/move-invalidasynchronousstateexception.md)]

***

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/3.0/net-core-3-0-follows-unicode-utf8-best-practices.md)]

***

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/3.0/move-typedescriptionproviderattribute.md)]

***

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/3.0/ziparchiveentry-and-inconsistent-entry-sizes.md)]

***

[!INCLUDE[JSON serializer exception type changed from JsonException to NotSupportedException](~/includes/core-changes/corefx/3.0/serializer-throws-notsupportedexception.md)]

***

[!INCLUDE[Change in semantics of (string)null in Utf8JsonWriter](~/includes/core-changes/corefx/3.0/change-in-null-in-utf8jsonwriter.md)]

***

[!INCLUDE[JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument](~/includes/core-changes/corefx/3.0/jsonencodedtext-encode-has-additional-argument.md)]

***

[!INCLUDE[JsonFactoryConverter.CreateConverter signature changed](~/includes/core-changes/corefx/3.0/jsonfactoryconverter-createconverter.md)]

***

[!INCLUDE[JsonElement API changes](~/includes/core-changes/corefx/3.0/jsonelement-api-changes.md)]

***

[!INCLUDE [FieldInfo.SetValue throws exception for static, init-only fields](~/includes/core-changes/corefx/3.0/fieldinfo-setvalue-exception.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="da6ae-164">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="da6ae-164">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="da6ae-165">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="da6ae-165">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***
