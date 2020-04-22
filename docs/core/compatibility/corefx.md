---
title: Změny rozdělení knihovny základních tříd
description: Uvádí nejnovější změny v základních knihovnách .NET.
ms.date: 09/20/2019
ms.openlocfilehash: 8cf90ca2bc8736101c1cb8d327a93d100148937b
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021825"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="b3bb5-103">Základní knihovny .NET narušují změny</span><span class="sxs-lookup"><span data-stu-id="b3bb5-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="b3bb5-104">Základní knihovny .NET poskytují primitiva a další obecné typy používané jádrem .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b3bb5-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="b3bb5-105">Na této stránce jsou popsány následující změny:</span><span class="sxs-lookup"><span data-stu-id="b3bb5-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="b3bb5-106">Narušující změny</span><span class="sxs-lookup"><span data-stu-id="b3bb5-106">Breaking change</span></span> | <span data-ttu-id="b3bb5-107">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="b3bb5-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="b3bb5-108">Api, která sestavy verze nyní sestavy produktu a není verze souboru</span><span class="sxs-lookup"><span data-stu-id="b3bb5-108">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="b3bb5-109">3.0</span><span class="sxs-lookup"><span data-stu-id="b3bb5-109">3.0</span></span> |
| [<span data-ttu-id="b3bb5-110">Vlastní instance EncoderFallbackBuffer nemohou rekurzivně ustoupit</span><span class="sxs-lookup"><span data-stu-id="b3bb5-110">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="b3bb5-111">3.0</span><span class="sxs-lookup"><span data-stu-id="b3bb5-111">3.0</span></span> |
| [<span data-ttu-id="b3bb5-112">Změny chování formátování s plovoucí desetinnou táhou a analýza</span><span class="sxs-lookup"><span data-stu-id="b3bb5-112">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="b3bb5-113">3.0</span><span class="sxs-lookup"><span data-stu-id="b3bb5-113">3.0</span></span> |
| [<span data-ttu-id="b3bb5-114">Operace analýzy s plovoucí desetinnou táhou již neselžou nebo nevyvolá vyzvučují výjimku Přetečení</span><span class="sxs-lookup"><span data-stu-id="b3bb5-114">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="b3bb5-115">3.0</span><span class="sxs-lookup"><span data-stu-id="b3bb5-115">3.0</span></span> |
| [<span data-ttu-id="b3bb5-116">InvalidAsynchronousStateException přesunuta do jiného sestavení</span><span class="sxs-lookup"><span data-stu-id="b3bb5-116">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="b3bb5-117">3.0</span><span class="sxs-lookup"><span data-stu-id="b3bb5-117">3.0</span></span> |
| [<span data-ttu-id="b3bb5-118">NET Core 3.0 se řídí osvědčenými postupy Unicode při výměně špatně vytvořených bajtových sekvencí UTF-8</span><span class="sxs-lookup"><span data-stu-id="b3bb5-118">NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences</span></span>](#net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences) | <span data-ttu-id="b3bb5-119">3.0</span><span class="sxs-lookup"><span data-stu-id="b3bb5-119">3.0</span></span> |
| [<span data-ttu-id="b3bb5-120">TypeDescriptionProviderAttribute přesunutdo jiného sestavení</span><span class="sxs-lookup"><span data-stu-id="b3bb5-120">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="b3bb5-121">3.0</span><span class="sxs-lookup"><span data-stu-id="b3bb5-121">3.0</span></span> |
| [<span data-ttu-id="b3bb5-122">ZipArchiveEntry již zpracovává archivy s nekonzistentními velikostmi položek</span><span class="sxs-lookup"><span data-stu-id="b3bb5-122">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="b3bb5-123">3.0</span><span class="sxs-lookup"><span data-stu-id="b3bb5-123">3.0</span></span> |
| [<span data-ttu-id="b3bb5-124">Typ výjimky serializátoru JSON byl změněn z JsonException na NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="b3bb5-124">JSON serializer exception type changed from JsonException to NotSupportedException</span></span>](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | <span data-ttu-id="b3bb5-125">3.0</span><span class="sxs-lookup"><span data-stu-id="b3bb5-125">3.0</span></span> |
| [<span data-ttu-id="b3bb5-126">Změna sémantiky (string)null v Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="b3bb5-126">Change in semantics of (string)null in Utf8JsonWriter</span></span>](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | <span data-ttu-id="b3bb5-127">3.0</span><span class="sxs-lookup"><span data-stu-id="b3bb5-127">3.0</span></span> |
| [<span data-ttu-id="b3bb5-128">Metody JsonEncodedText.Encode mají další argument JavaScriptEncoder</span><span class="sxs-lookup"><span data-stu-id="b3bb5-128">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | <span data-ttu-id="b3bb5-129">3.0</span><span class="sxs-lookup"><span data-stu-id="b3bb5-129">3.0</span></span> |
| [<span data-ttu-id="b3bb5-130">JsonFactoryConverter.CreateConverter podpis změněn</span><span class="sxs-lookup"><span data-stu-id="b3bb5-130">JsonFactoryConverter.CreateConverter signature changed</span></span>](#jsonfactoryconvertercreateconverter-signature-changed) | <span data-ttu-id="b3bb5-131">3.0</span><span class="sxs-lookup"><span data-stu-id="b3bb5-131">3.0</span></span> |
| [<span data-ttu-id="b3bb5-132">Změny rozhraní API Prvku JsonElement</span><span class="sxs-lookup"><span data-stu-id="b3bb5-132">JsonElement API changes</span></span>](#jsonelement-api-changes) | <span data-ttu-id="b3bb5-133">3.0</span><span class="sxs-lookup"><span data-stu-id="b3bb5-133">3.0</span></span> |
| [<span data-ttu-id="b3bb5-134">FieldInfo.SetValue vyvolá výjimku pro statická pole pouze init.</span><span class="sxs-lookup"><span data-stu-id="b3bb5-134">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="b3bb5-135">3.0</span><span class="sxs-lookup"><span data-stu-id="b3bb5-135">3.0</span></span> |
| [<span data-ttu-id="b3bb5-136">Soukromá pole přidaná k předdefinovaným typům struktury</span><span class="sxs-lookup"><span data-stu-id="b3bb5-136">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="b3bb5-137">2.1</span><span class="sxs-lookup"><span data-stu-id="b3bb5-137">2.1</span></span> |
| [<span data-ttu-id="b3bb5-138">Změna výchozí hodnoty useShellExecute</span><span class="sxs-lookup"><span data-stu-id="b3bb5-138">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="b3bb5-139">2.1</span><span class="sxs-lookup"><span data-stu-id="b3bb5-139">2.1</span></span> |
| [<span data-ttu-id="b3bb5-140">Verze OpenSSL v macOS</span><span class="sxs-lookup"><span data-stu-id="b3bb5-140">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="b3bb5-141">2.1</span><span class="sxs-lookup"><span data-stu-id="b3bb5-141">2.1</span></span> |
| [<span data-ttu-id="b3bb5-142">UnauthorizedAccessException vyvoláno souborem FileSystemInfo.Attributes</span><span class="sxs-lookup"><span data-stu-id="b3bb5-142">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="b3bb5-143">1.0</span><span class="sxs-lookup"><span data-stu-id="b3bb5-143">1.0</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="b3bb5-144">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b3bb5-144">.NET Core 3.0</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="b3bb5-145">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="b3bb5-145">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="b3bb5-146">.NET Jádro 1.0</span><span class="sxs-lookup"><span data-stu-id="b3bb5-146">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***
