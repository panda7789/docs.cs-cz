---
title: Přerušující změny knihovny základních tříd
description: Obsahuje seznam nejnovějších změn v základních knihovnách .NET.
ms.date: 09/20/2019
ms.openlocfilehash: 45de0f0d418437cf1677c9a8c7cfc9b6c33a24ef
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144474"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="6f70d-103">Základní knihovny .NET – přerušující změny</span><span class="sxs-lookup"><span data-stu-id="6f70d-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="6f70d-104">Základní knihovny .NET poskytují primitivní a další obecné typy používané .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6f70d-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="6f70d-105">Na této stránce jsou popsány následující přerušující se změny:</span><span class="sxs-lookup"><span data-stu-id="6f70d-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="6f70d-106">Zásadní změna</span><span class="sxs-lookup"><span data-stu-id="6f70d-106">Breaking change</span></span> | <span data-ttu-id="6f70d-107">Představená verze</span><span class="sxs-lookup"><span data-stu-id="6f70d-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="6f70d-108">Metody SSE a SSE2 CompareGreaterThan správně zpracovávají vstupy NaN.</span><span class="sxs-lookup"><span data-stu-id="6f70d-108">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="6f70d-109">5.0</span><span class="sxs-lookup"><span data-stu-id="6f70d-109">5.0</span></span> |
| [<span data-ttu-id="6f70d-110">Sada CounterSet. provedení operace CreateCounterSetInstance nyní vyvolá chybu InvalidOperationException, pokud již instance existuje.</span><span class="sxs-lookup"><span data-stu-id="6f70d-110">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exist</span></span>](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | <span data-ttu-id="6f70d-111">5.0</span><span class="sxs-lookup"><span data-stu-id="6f70d-111">5.0</span></span> |
| [<span data-ttu-id="6f70d-112">Rozhraní API, která verze sestav nyní hlásí produkt a nikoli verzi souboru</span><span class="sxs-lookup"><span data-stu-id="6f70d-112">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="6f70d-113">3.0</span><span class="sxs-lookup"><span data-stu-id="6f70d-113">3.0</span></span> |
| [<span data-ttu-id="6f70d-114">Vlastní instance EncoderFallbackBuffer se nemůžou vrátit rekurzivně.</span><span class="sxs-lookup"><span data-stu-id="6f70d-114">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="6f70d-115">3.0</span><span class="sxs-lookup"><span data-stu-id="6f70d-115">3.0</span></span> |
| [<span data-ttu-id="6f70d-116">Změny chování při formátování a analýze plovoucí desetinné čárky</span><span class="sxs-lookup"><span data-stu-id="6f70d-116">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="6f70d-117">3.0</span><span class="sxs-lookup"><span data-stu-id="6f70d-117">3.0</span></span> |
| [<span data-ttu-id="6f70d-118">Operace analýzy s plovoucí desetinnou čárkou již nejsou úspěšné nebo vyvolávají výjimku OverflowException</span><span class="sxs-lookup"><span data-stu-id="6f70d-118">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="6f70d-119">3.0</span><span class="sxs-lookup"><span data-stu-id="6f70d-119">3.0</span></span> |
| [<span data-ttu-id="6f70d-120">InvalidAsynchronousStateException – přesunuté do jiného sestavení</span><span class="sxs-lookup"><span data-stu-id="6f70d-120">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="6f70d-121">3.0</span><span class="sxs-lookup"><span data-stu-id="6f70d-121">3.0</span></span> |
| [<span data-ttu-id="6f70d-122">Výměna chybně formátovaných sekvencí UTF-8 se řídí pokyny pro kódování Unicode</span><span class="sxs-lookup"><span data-stu-id="6f70d-122">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="6f70d-123">3.0</span><span class="sxs-lookup"><span data-stu-id="6f70d-123">3.0</span></span> |
| [<span data-ttu-id="6f70d-124">TypeDescriptionProviderAttribute přesunuté do jiného sestavení</span><span class="sxs-lookup"><span data-stu-id="6f70d-124">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="6f70d-125">3.0</span><span class="sxs-lookup"><span data-stu-id="6f70d-125">3.0</span></span> |
| [<span data-ttu-id="6f70d-126">ZipArchiveEntry už nezpracovává archivy s nekonzistentními velikostmi záznamů.</span><span class="sxs-lookup"><span data-stu-id="6f70d-126">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="6f70d-127">3.0</span><span class="sxs-lookup"><span data-stu-id="6f70d-127">3.0</span></span> |
| [<span data-ttu-id="6f70d-128">Typ výjimky serializátoru JSON se změnil z JsonException na NotSupportedException.</span><span class="sxs-lookup"><span data-stu-id="6f70d-128">JSON serializer exception type changed from JsonException to NotSupportedException</span></span>](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | <span data-ttu-id="6f70d-129">3.0</span><span class="sxs-lookup"><span data-stu-id="6f70d-129">3.0</span></span> |
| [<span data-ttu-id="6f70d-130">Změna v sémantikě (String) null v Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="6f70d-130">Change in semantics of (string)null in Utf8JsonWriter</span></span>](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | <span data-ttu-id="6f70d-131">3.0</span><span class="sxs-lookup"><span data-stu-id="6f70d-131">3.0</span></span> |
| [<span data-ttu-id="6f70d-132">Metody JsonEncodedText. Encode mají další argument JavaScriptEncoder.</span><span class="sxs-lookup"><span data-stu-id="6f70d-132">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | <span data-ttu-id="6f70d-133">3.0</span><span class="sxs-lookup"><span data-stu-id="6f70d-133">3.0</span></span> |
| [<span data-ttu-id="6f70d-134">Změnil se podpis JsonFactoryConverter. CreateConverter.</span><span class="sxs-lookup"><span data-stu-id="6f70d-134">JsonFactoryConverter.CreateConverter signature changed</span></span>](#jsonfactoryconvertercreateconverter-signature-changed) | <span data-ttu-id="6f70d-135">3.0</span><span class="sxs-lookup"><span data-stu-id="6f70d-135">3.0</span></span> |
| [<span data-ttu-id="6f70d-136">Změny rozhraní API JsonElement</span><span class="sxs-lookup"><span data-stu-id="6f70d-136">JsonElement API changes</span></span>](#jsonelement-api-changes) | <span data-ttu-id="6f70d-137">3.0</span><span class="sxs-lookup"><span data-stu-id="6f70d-137">3.0</span></span> |
| [<span data-ttu-id="6f70d-138">Parametr FieldInfo. SetValue vyvolá výjimku pro statická pole pouze pro init.</span><span class="sxs-lookup"><span data-stu-id="6f70d-138">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="6f70d-139">3.0</span><span class="sxs-lookup"><span data-stu-id="6f70d-139">3.0</span></span> |
| [<span data-ttu-id="6f70d-140">Soukromá pole přidaná k předdefinovaným typům struktury</span><span class="sxs-lookup"><span data-stu-id="6f70d-140">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="6f70d-141">2.1</span><span class="sxs-lookup"><span data-stu-id="6f70d-141">2.1</span></span> |
| [<span data-ttu-id="6f70d-142">Změna výchozí hodnoty UseShellExecute objektu Process</span><span class="sxs-lookup"><span data-stu-id="6f70d-142">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="6f70d-143">2.1</span><span class="sxs-lookup"><span data-stu-id="6f70d-143">2.1</span></span> |
| [<span data-ttu-id="6f70d-144">Verze OpenSSL v macOS</span><span class="sxs-lookup"><span data-stu-id="6f70d-144">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="6f70d-145">2.1</span><span class="sxs-lookup"><span data-stu-id="6f70d-145">2.1</span></span> |
| [<span data-ttu-id="6f70d-146">UnauthorizedAccessException vyvolaná atributy SystemInfo.</span><span class="sxs-lookup"><span data-stu-id="6f70d-146">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="6f70d-147">1.0</span><span class="sxs-lookup"><span data-stu-id="6f70d-147">1.0</span></span> |
| [<span data-ttu-id="6f70d-148">Manipulace s poškozenými výjimkami stavu procesu není podporována.</span><span class="sxs-lookup"><span data-stu-id="6f70d-148">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="6f70d-149">1.0</span><span class="sxs-lookup"><span data-stu-id="6f70d-149">1.0</span></span> |
| [<span data-ttu-id="6f70d-150">Vlastnosti objekt UriBuilder protokolu už neobsahují úvodní znaky.</span><span class="sxs-lookup"><span data-stu-id="6f70d-150">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="6f70d-151">1.0</span><span class="sxs-lookup"><span data-stu-id="6f70d-151">1.0</span></span> |
| [<span data-ttu-id="6f70d-152">Process. StartInfo vyvolá InvalidOperationException pro procesy, které jste nespustili.</span><span class="sxs-lookup"><span data-stu-id="6f70d-152">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="6f70d-153">1.0</span><span class="sxs-lookup"><span data-stu-id="6f70d-153">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="6f70d-154">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="6f70d-154">.NET 5.0</span></span>

[!INCLUDE [sse-comparegreaterthan-intrinsics](../../../includes/core-changes/corefx/5.0/sse-comparegreaterthan-intrinsics.md)]

***

[!INCLUDE [createcountersetinstance-throws-invalidoperation](../../../includes/core-changes/corefx/5.0/createcountersetinstance-throws-invalidoperation.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="6f70d-155">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="6f70d-155">.NET Core 3.0</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="6f70d-156">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="6f70d-156">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="6f70d-157">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="6f70d-157">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***
