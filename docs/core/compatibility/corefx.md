---
title: Přerušující změny knihovny základních tříd
description: Obsahuje seznam nejnovějších změn v základních knihovnách .NET.
ms.date: 09/20/2019
ms.openlocfilehash: 841003fdb114042466cc15b4846e133cf37de85c
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135643"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="13ad8-103">Základní knihovny .NET – přerušující změny</span><span class="sxs-lookup"><span data-stu-id="13ad8-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="13ad8-104">Základní knihovny .NET poskytují primitivní a další obecné typy používané .NET Core.</span><span class="sxs-lookup"><span data-stu-id="13ad8-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="13ad8-105">Na této stránce jsou popsány následující přerušující se změny:</span><span class="sxs-lookup"><span data-stu-id="13ad8-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="13ad8-106">Zásadní změna</span><span class="sxs-lookup"><span data-stu-id="13ad8-106">Breaking change</span></span> | <span data-ttu-id="13ad8-107">Představená verze</span><span class="sxs-lookup"><span data-stu-id="13ad8-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="13ad8-108">Rozhraní API, která verze sestav nyní hlásí produkt a nikoli verzi souboru</span><span class="sxs-lookup"><span data-stu-id="13ad8-108">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="13ad8-109">3.0</span><span class="sxs-lookup"><span data-stu-id="13ad8-109">3.0</span></span> |
| [<span data-ttu-id="13ad8-110">Vlastní instance EncoderFallbackBuffer se nemůžou vrátit rekurzivně.</span><span class="sxs-lookup"><span data-stu-id="13ad8-110">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="13ad8-111">3.0</span><span class="sxs-lookup"><span data-stu-id="13ad8-111">3.0</span></span> |
| [<span data-ttu-id="13ad8-112">Změny chování při formátování a analýze plovoucí desetinné čárky</span><span class="sxs-lookup"><span data-stu-id="13ad8-112">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="13ad8-113">3.0</span><span class="sxs-lookup"><span data-stu-id="13ad8-113">3.0</span></span> |
| [<span data-ttu-id="13ad8-114">Operace analýzy s plovoucí desetinnou čárkou již nejsou úspěšné nebo vyvolávají výjimku OverflowException</span><span class="sxs-lookup"><span data-stu-id="13ad8-114">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="13ad8-115">3.0</span><span class="sxs-lookup"><span data-stu-id="13ad8-115">3.0</span></span> |
| [<span data-ttu-id="13ad8-116">InvalidAsynchronousStateException – přesunuté do jiného sestavení</span><span class="sxs-lookup"><span data-stu-id="13ad8-116">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="13ad8-117">3.0</span><span class="sxs-lookup"><span data-stu-id="13ad8-117">3.0</span></span> |
| [<span data-ttu-id="13ad8-118">.NET Core 3,0 se řídí osvědčenými postupy Unicode při nahrazování nesprávně naformátovaných sekvencí bajtů UTF-8.</span><span class="sxs-lookup"><span data-stu-id="13ad8-118">NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences</span></span>](#net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences) | <span data-ttu-id="13ad8-119">3.0</span><span class="sxs-lookup"><span data-stu-id="13ad8-119">3.0</span></span> |
| [<span data-ttu-id="13ad8-120">TypeDescriptionProviderAttribute přesunuté do jiného sestavení</span><span class="sxs-lookup"><span data-stu-id="13ad8-120">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="13ad8-121">3.0</span><span class="sxs-lookup"><span data-stu-id="13ad8-121">3.0</span></span> |
| [<span data-ttu-id="13ad8-122">ZipArchiveEntry už nezpracovává archivy s nekonzistentními velikostmi záznamů.</span><span class="sxs-lookup"><span data-stu-id="13ad8-122">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="13ad8-123">3.0</span><span class="sxs-lookup"><span data-stu-id="13ad8-123">3.0</span></span> |
| [<span data-ttu-id="13ad8-124">Typ výjimky serializátoru JSON se změnil z JsonException na NotSupportedException.</span><span class="sxs-lookup"><span data-stu-id="13ad8-124">JSON serializer exception type changed from JsonException to NotSupportedException</span></span>](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | <span data-ttu-id="13ad8-125">3.0</span><span class="sxs-lookup"><span data-stu-id="13ad8-125">3.0</span></span> |
| [<span data-ttu-id="13ad8-126">Změna v sémantikě (String) null v Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="13ad8-126">Change in semantics of (string)null in Utf8JsonWriter</span></span>](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | <span data-ttu-id="13ad8-127">3.0</span><span class="sxs-lookup"><span data-stu-id="13ad8-127">3.0</span></span> |
| [<span data-ttu-id="13ad8-128">Metody JsonEncodedText. Encode mají další argument JavaScriptEncoder.</span><span class="sxs-lookup"><span data-stu-id="13ad8-128">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | <span data-ttu-id="13ad8-129">3.0</span><span class="sxs-lookup"><span data-stu-id="13ad8-129">3.0</span></span> |
| [<span data-ttu-id="13ad8-130">Změnil se podpis JsonFactoryConverter. CreateConverter.</span><span class="sxs-lookup"><span data-stu-id="13ad8-130">JsonFactoryConverter.CreateConverter signature changed</span></span>](#jsonfactoryconvertercreateconverter-signature-changed) | <span data-ttu-id="13ad8-131">3.0</span><span class="sxs-lookup"><span data-stu-id="13ad8-131">3.0</span></span> |
| [<span data-ttu-id="13ad8-132">Změny rozhraní API JsonElement</span><span class="sxs-lookup"><span data-stu-id="13ad8-132">JsonElement API changes</span></span>](#jsonelement-api-changes) | <span data-ttu-id="13ad8-133">3.0</span><span class="sxs-lookup"><span data-stu-id="13ad8-133">3.0</span></span> |
| [<span data-ttu-id="13ad8-134">Parametr FieldInfo. SetValue vyvolá výjimku pro statická pole pouze pro init.</span><span class="sxs-lookup"><span data-stu-id="13ad8-134">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="13ad8-135">3.0</span><span class="sxs-lookup"><span data-stu-id="13ad8-135">3.0</span></span> |
| [<span data-ttu-id="13ad8-136">Soukromá pole přidaná k předdefinovaným typům struktury</span><span class="sxs-lookup"><span data-stu-id="13ad8-136">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="13ad8-137">2.1</span><span class="sxs-lookup"><span data-stu-id="13ad8-137">2.1</span></span> |
| [<span data-ttu-id="13ad8-138">Změna výchozí hodnoty UseShellExecute objektu Process</span><span class="sxs-lookup"><span data-stu-id="13ad8-138">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="13ad8-139">2.1</span><span class="sxs-lookup"><span data-stu-id="13ad8-139">2.1</span></span> |
| [<span data-ttu-id="13ad8-140">Verze OpenSSL v macOS</span><span class="sxs-lookup"><span data-stu-id="13ad8-140">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="13ad8-141">2.1</span><span class="sxs-lookup"><span data-stu-id="13ad8-141">2.1</span></span> |
| [<span data-ttu-id="13ad8-142">UnauthorizedAccessException vyvolaná atributy SystemInfo.</span><span class="sxs-lookup"><span data-stu-id="13ad8-142">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="13ad8-143">1.0</span><span class="sxs-lookup"><span data-stu-id="13ad8-143">1.0</span></span> |
| [<span data-ttu-id="13ad8-144">Manipulace s poškozenými výjimkami stavu procesu není podporována.</span><span class="sxs-lookup"><span data-stu-id="13ad8-144">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="13ad8-145">1.0</span><span class="sxs-lookup"><span data-stu-id="13ad8-145">1.0</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="13ad8-146">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="13ad8-146">.NET Core 3.0</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="13ad8-147">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="13ad8-147">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="13ad8-148">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="13ad8-148">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***
