---
title: Změny rozdělení knihovny základních tříd
description: Uvádí nejnovější změny v .NET CoreFx, knihovně základních tříd.
ms.date: 09/20/2019
ms.openlocfilehash: 56a3cf4f4c00a79752d5a98bb086bb9f8c0614b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147572"
---
# <a name="corefx-breaking-changes"></a><span data-ttu-id="161a6-103">CoreFx láme změny</span><span class="sxs-lookup"><span data-stu-id="161a6-103">CoreFx breaking changes</span></span>

<span data-ttu-id="161a6-104">CoreFx poskytuje primitiva a další obecné typy používané .NET Core.</span><span class="sxs-lookup"><span data-stu-id="161a6-104">CoreFx provides the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="161a6-105">Na této stránce jsou popsány následující změny:</span><span class="sxs-lookup"><span data-stu-id="161a6-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="161a6-106">Narušující změny</span><span class="sxs-lookup"><span data-stu-id="161a6-106">Breaking change</span></span> | <span data-ttu-id="161a6-107">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="161a6-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="161a6-108">Api, která sestavy verze nyní sestavy produktu a není verze souboru</span><span class="sxs-lookup"><span data-stu-id="161a6-108">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="161a6-109">3.0</span><span class="sxs-lookup"><span data-stu-id="161a6-109">3.0</span></span> |
| [<span data-ttu-id="161a6-110">Vlastní instance EncoderFallbackBuffer nemohou rekurzivně ustoupit</span><span class="sxs-lookup"><span data-stu-id="161a6-110">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="161a6-111">3.0</span><span class="sxs-lookup"><span data-stu-id="161a6-111">3.0</span></span> |
| [<span data-ttu-id="161a6-112">Změny chování formátování s plovoucí desetinnou táhou a analýza</span><span class="sxs-lookup"><span data-stu-id="161a6-112">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="161a6-113">3.0</span><span class="sxs-lookup"><span data-stu-id="161a6-113">3.0</span></span> |
| [<span data-ttu-id="161a6-114">Operace analýzy s plovoucí desetinnou táhou již neselžou nebo nevyvolá vyzvučují výjimku Přetečení</span><span class="sxs-lookup"><span data-stu-id="161a6-114">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="161a6-115">3.0</span><span class="sxs-lookup"><span data-stu-id="161a6-115">3.0</span></span> |
| [<span data-ttu-id="161a6-116">InvalidAsynchronousStateException přesunuta do jiného sestavení</span><span class="sxs-lookup"><span data-stu-id="161a6-116">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="161a6-117">3.0</span><span class="sxs-lookup"><span data-stu-id="161a6-117">3.0</span></span> |
| [<span data-ttu-id="161a6-118">NET Core 3.0 se řídí osvědčenými postupy Unicode při výměně špatně vytvořených bajtových sekvencí UTF-8</span><span class="sxs-lookup"><span data-stu-id="161a6-118">NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences</span></span>](#net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences) | <span data-ttu-id="161a6-119">3.0</span><span class="sxs-lookup"><span data-stu-id="161a6-119">3.0</span></span> |
| [<span data-ttu-id="161a6-120">TypeDescriptionProviderAttribute přesunutdo jiného sestavení</span><span class="sxs-lookup"><span data-stu-id="161a6-120">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="161a6-121">3.0</span><span class="sxs-lookup"><span data-stu-id="161a6-121">3.0</span></span> |
| [<span data-ttu-id="161a6-122">ZipArchiveEntry již zpracovává archivy s nekonzistentními velikostmi položek</span><span class="sxs-lookup"><span data-stu-id="161a6-122">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="161a6-123">3.0</span><span class="sxs-lookup"><span data-stu-id="161a6-123">3.0</span></span> |
| [<span data-ttu-id="161a6-124">Typ výjimky serializátoru JSON byl změněn z JsonException na NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="161a6-124">JSON serializer exception type changed from JsonException to NotSupportedException</span></span>](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | <span data-ttu-id="161a6-125">3.0</span><span class="sxs-lookup"><span data-stu-id="161a6-125">3.0</span></span> |
| [<span data-ttu-id="161a6-126">Změna sémantiky (string)null v Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="161a6-126">Change in semantics of (string)null in Utf8JsonWriter</span></span>](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | <span data-ttu-id="161a6-127">3.0</span><span class="sxs-lookup"><span data-stu-id="161a6-127">3.0</span></span> |
| [<span data-ttu-id="161a6-128">Metody JsonEncodedText.Encode mají další argument JavaScriptEncoder</span><span class="sxs-lookup"><span data-stu-id="161a6-128">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | <span data-ttu-id="161a6-129">3.0</span><span class="sxs-lookup"><span data-stu-id="161a6-129">3.0</span></span> |
| [<span data-ttu-id="161a6-130">JsonFactoryConverter.CreateConverter podpis změněn</span><span class="sxs-lookup"><span data-stu-id="161a6-130">JsonFactoryConverter.CreateConverter signature changed</span></span>](#jsonfactoryconvertercreateconverter-signature-changed) | <span data-ttu-id="161a6-131">3.0</span><span class="sxs-lookup"><span data-stu-id="161a6-131">3.0</span></span> |
| [<span data-ttu-id="161a6-132">Změny rozhraní API Prvku JsonElement</span><span class="sxs-lookup"><span data-stu-id="161a6-132">JsonElement API changes</span></span>](#jsonelement-api-changes) | <span data-ttu-id="161a6-133">3.0</span><span class="sxs-lookup"><span data-stu-id="161a6-133">3.0</span></span> |
| [<span data-ttu-id="161a6-134">FieldInfo.SetValue vyvolá výjimku pro statická pole pouze init.</span><span class="sxs-lookup"><span data-stu-id="161a6-134">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="161a6-135">3.0</span><span class="sxs-lookup"><span data-stu-id="161a6-135">3.0</span></span> |
| [<span data-ttu-id="161a6-136">Soukromá pole přidaná k předdefinovaným typům struktury</span><span class="sxs-lookup"><span data-stu-id="161a6-136">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="161a6-137">2.1</span><span class="sxs-lookup"><span data-stu-id="161a6-137">2.1</span></span> |
| [<span data-ttu-id="161a6-138">Změna výchozí hodnoty useShellExecute</span><span class="sxs-lookup"><span data-stu-id="161a6-138">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="161a6-139">2.1</span><span class="sxs-lookup"><span data-stu-id="161a6-139">2.1</span></span> |
| [<span data-ttu-id="161a6-140">Verze OpenSSL v macOS</span><span class="sxs-lookup"><span data-stu-id="161a6-140">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="161a6-141">2.1</span><span class="sxs-lookup"><span data-stu-id="161a6-141">2.1</span></span> |
| [<span data-ttu-id="161a6-142">UnauthorizedAccessException vyvoláno souborem FileSystemInfo.Attributes</span><span class="sxs-lookup"><span data-stu-id="161a6-142">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="161a6-143">1.0</span><span class="sxs-lookup"><span data-stu-id="161a6-143">1.0</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="161a6-144">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="161a6-144">.NET Core 3.0</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="161a6-145">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="161a6-145">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="161a6-146">.NET Jádro 1.0</span><span class="sxs-lookup"><span data-stu-id="161a6-146">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***
