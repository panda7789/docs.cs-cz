---
title: Přerušující změny knihovny základních tříd
description: Obsahuje seznam nejnovějších změn v základních knihovnách .NET.
ms.date: 09/20/2019
ms.openlocfilehash: a2eb4be89d78f50d201272f3449374bc27d8c785
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859925"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="d2270-103">Základní knihovny .NET – přerušující změny</span><span class="sxs-lookup"><span data-stu-id="d2270-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="d2270-104">Základní knihovny .NET poskytují primitivní a další obecné typy používané .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d2270-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="d2270-105">Na této stránce jsou popsány následující přerušující se změny:</span><span class="sxs-lookup"><span data-stu-id="d2270-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="d2270-106">Zásadní změna</span><span class="sxs-lookup"><span data-stu-id="d2270-106">Breaking change</span></span> | <span data-ttu-id="d2270-107">Představená verze</span><span class="sxs-lookup"><span data-stu-id="d2270-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="d2270-108">Metody SSE a SSE2 CompareGreaterThan správně zpracovávají vstupy NaN.</span><span class="sxs-lookup"><span data-stu-id="d2270-108">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="d2270-109">5.0</span><span class="sxs-lookup"><span data-stu-id="d2270-109">5.0</span></span> |
| [<span data-ttu-id="d2270-110">Rozhraní API, která verze sestav nyní hlásí produkt a nikoli verzi souboru</span><span class="sxs-lookup"><span data-stu-id="d2270-110">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="d2270-111">3.0</span><span class="sxs-lookup"><span data-stu-id="d2270-111">3.0</span></span> |
| [<span data-ttu-id="d2270-112">Vlastní instance EncoderFallbackBuffer se nemůžou vrátit rekurzivně.</span><span class="sxs-lookup"><span data-stu-id="d2270-112">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="d2270-113">3.0</span><span class="sxs-lookup"><span data-stu-id="d2270-113">3.0</span></span> |
| [<span data-ttu-id="d2270-114">Změny chování při formátování a analýze plovoucí desetinné čárky</span><span class="sxs-lookup"><span data-stu-id="d2270-114">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="d2270-115">3.0</span><span class="sxs-lookup"><span data-stu-id="d2270-115">3.0</span></span> |
| [<span data-ttu-id="d2270-116">Operace analýzy s plovoucí desetinnou čárkou již nejsou úspěšné nebo vyvolávají výjimku OverflowException</span><span class="sxs-lookup"><span data-stu-id="d2270-116">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="d2270-117">3.0</span><span class="sxs-lookup"><span data-stu-id="d2270-117">3.0</span></span> |
| [<span data-ttu-id="d2270-118">InvalidAsynchronousStateException – přesunuté do jiného sestavení</span><span class="sxs-lookup"><span data-stu-id="d2270-118">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="d2270-119">3.0</span><span class="sxs-lookup"><span data-stu-id="d2270-119">3.0</span></span> |
| [<span data-ttu-id="d2270-120">Výměna chybně formátovaných sekvencí UTF-8 se řídí pokyny pro kódování Unicode</span><span class="sxs-lookup"><span data-stu-id="d2270-120">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="d2270-121">3.0</span><span class="sxs-lookup"><span data-stu-id="d2270-121">3.0</span></span> |
| [<span data-ttu-id="d2270-122">TypeDescriptionProviderAttribute přesunuté do jiného sestavení</span><span class="sxs-lookup"><span data-stu-id="d2270-122">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="d2270-123">3.0</span><span class="sxs-lookup"><span data-stu-id="d2270-123">3.0</span></span> |
| [<span data-ttu-id="d2270-124">ZipArchiveEntry už nezpracovává archivy s nekonzistentními velikostmi záznamů.</span><span class="sxs-lookup"><span data-stu-id="d2270-124">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="d2270-125">3.0</span><span class="sxs-lookup"><span data-stu-id="d2270-125">3.0</span></span> |
| [<span data-ttu-id="d2270-126">Typ výjimky serializátoru JSON se změnil z JsonException na NotSupportedException.</span><span class="sxs-lookup"><span data-stu-id="d2270-126">JSON serializer exception type changed from JsonException to NotSupportedException</span></span>](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | <span data-ttu-id="d2270-127">3.0</span><span class="sxs-lookup"><span data-stu-id="d2270-127">3.0</span></span> |
| [<span data-ttu-id="d2270-128">Změna v sémantikě (String) null v Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="d2270-128">Change in semantics of (string)null in Utf8JsonWriter</span></span>](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | <span data-ttu-id="d2270-129">3.0</span><span class="sxs-lookup"><span data-stu-id="d2270-129">3.0</span></span> |
| [<span data-ttu-id="d2270-130">Metody JsonEncodedText. Encode mají další argument JavaScriptEncoder.</span><span class="sxs-lookup"><span data-stu-id="d2270-130">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | <span data-ttu-id="d2270-131">3.0</span><span class="sxs-lookup"><span data-stu-id="d2270-131">3.0</span></span> |
| [<span data-ttu-id="d2270-132">Změnil se podpis JsonFactoryConverter. CreateConverter.</span><span class="sxs-lookup"><span data-stu-id="d2270-132">JsonFactoryConverter.CreateConverter signature changed</span></span>](#jsonfactoryconvertercreateconverter-signature-changed) | <span data-ttu-id="d2270-133">3.0</span><span class="sxs-lookup"><span data-stu-id="d2270-133">3.0</span></span> |
| [<span data-ttu-id="d2270-134">Změny rozhraní API JsonElement</span><span class="sxs-lookup"><span data-stu-id="d2270-134">JsonElement API changes</span></span>](#jsonelement-api-changes) | <span data-ttu-id="d2270-135">3.0</span><span class="sxs-lookup"><span data-stu-id="d2270-135">3.0</span></span> |
| [<span data-ttu-id="d2270-136">Parametr FieldInfo. SetValue vyvolá výjimku pro statická pole pouze pro init.</span><span class="sxs-lookup"><span data-stu-id="d2270-136">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="d2270-137">3.0</span><span class="sxs-lookup"><span data-stu-id="d2270-137">3.0</span></span> |
| [<span data-ttu-id="d2270-138">Soukromá pole přidaná k předdefinovaným typům struktury</span><span class="sxs-lookup"><span data-stu-id="d2270-138">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="d2270-139">2.1</span><span class="sxs-lookup"><span data-stu-id="d2270-139">2.1</span></span> |
| [<span data-ttu-id="d2270-140">Změna výchozí hodnoty UseShellExecute objektu Process</span><span class="sxs-lookup"><span data-stu-id="d2270-140">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="d2270-141">2.1</span><span class="sxs-lookup"><span data-stu-id="d2270-141">2.1</span></span> |
| [<span data-ttu-id="d2270-142">Verze OpenSSL v macOS</span><span class="sxs-lookup"><span data-stu-id="d2270-142">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="d2270-143">2.1</span><span class="sxs-lookup"><span data-stu-id="d2270-143">2.1</span></span> |
| [<span data-ttu-id="d2270-144">UnauthorizedAccessException vyvolaná atributy SystemInfo.</span><span class="sxs-lookup"><span data-stu-id="d2270-144">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="d2270-145">1.0</span><span class="sxs-lookup"><span data-stu-id="d2270-145">1.0</span></span> |
| [<span data-ttu-id="d2270-146">Manipulace s poškozenými výjimkami stavu procesu není podporována.</span><span class="sxs-lookup"><span data-stu-id="d2270-146">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="d2270-147">1.0</span><span class="sxs-lookup"><span data-stu-id="d2270-147">1.0</span></span> |
| [<span data-ttu-id="d2270-148">Vlastnosti objekt UriBuilder protokolu už neobsahují úvodní znaky.</span><span class="sxs-lookup"><span data-stu-id="d2270-148">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="d2270-149">1.0</span><span class="sxs-lookup"><span data-stu-id="d2270-149">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="d2270-150">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="d2270-150">.NET 5.0</span></span>

[!INCLUDE [sse-comparegreaterthan-intrinsics](../../../includes/core-changes/corefx/5.0/sse-comparegreaterthan-intrinsics.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="d2270-151">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="d2270-151">.NET Core 3.0</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="d2270-152">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="d2270-152">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="d2270-153">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="d2270-153">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***
