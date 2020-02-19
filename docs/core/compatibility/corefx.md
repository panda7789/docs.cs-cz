---
title: Přerušující změny knihovny základních tříd
description: Obsahuje seznam nejnovějších změn v rozhraní .NET CoreFx, knihovny základních tříd.
ms.date: 09/20/2019
ms.openlocfilehash: 7c59f2a96545e74e4099b6078ff52009740699c6
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449546"
---
# <a name="corefx-breaking-changes"></a><span data-ttu-id="9acf7-103">CoreFx průlomové změny</span><span class="sxs-lookup"><span data-stu-id="9acf7-103">CoreFx breaking changes</span></span>

<span data-ttu-id="9acf7-104">CoreFx poskytuje primitivní a další obecné typy používané .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9acf7-104">CoreFx provides the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="9acf7-105">Na této stránce jsou popsány následující přerušující se změny:</span><span class="sxs-lookup"><span data-stu-id="9acf7-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="9acf7-106">Zásadní změna</span><span class="sxs-lookup"><span data-stu-id="9acf7-106">Breaking change</span></span> | <span data-ttu-id="9acf7-107">Představená verze</span><span class="sxs-lookup"><span data-stu-id="9acf7-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="9acf7-108">Rozhraní API, která verze sestav nyní hlásí produkt a nikoli verzi souboru</span><span class="sxs-lookup"><span data-stu-id="9acf7-108">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="9acf7-109">3.0</span><span class="sxs-lookup"><span data-stu-id="9acf7-109">3.0</span></span> |
| [<span data-ttu-id="9acf7-110">Vlastní instance EncoderFallbackBuffer se nemůžou vrátit rekurzivně.</span><span class="sxs-lookup"><span data-stu-id="9acf7-110">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="9acf7-111">3.0</span><span class="sxs-lookup"><span data-stu-id="9acf7-111">3.0</span></span> |
| [<span data-ttu-id="9acf7-112">Změny chování při formátování a analýze plovoucí desetinné čárky</span><span class="sxs-lookup"><span data-stu-id="9acf7-112">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="9acf7-113">3.0</span><span class="sxs-lookup"><span data-stu-id="9acf7-113">3.0</span></span> |
| [<span data-ttu-id="9acf7-114">Operace analýzy s plovoucí desetinnou čárkou již nejsou úspěšné nebo vyvolávají výjimku OverflowException</span><span class="sxs-lookup"><span data-stu-id="9acf7-114">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="9acf7-115">3.0</span><span class="sxs-lookup"><span data-stu-id="9acf7-115">3.0</span></span> |
| [<span data-ttu-id="9acf7-116">InvalidAsynchronousStateException – přesunuté do jiného sestavení</span><span class="sxs-lookup"><span data-stu-id="9acf7-116">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="9acf7-117">3.0</span><span class="sxs-lookup"><span data-stu-id="9acf7-117">3.0</span></span> |
| [<span data-ttu-id="9acf7-118">.NET Core 3,0 se řídí osvědčenými postupy Unicode při nahrazování nesprávně naformátovaných sekvencí bajtů UTF-8.</span><span class="sxs-lookup"><span data-stu-id="9acf7-118">NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences</span></span>](#net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences) | <span data-ttu-id="9acf7-119">3.0</span><span class="sxs-lookup"><span data-stu-id="9acf7-119">3.0</span></span> |
| [<span data-ttu-id="9acf7-120">TypeDescriptionProviderAttribute přesunuté do jiného sestavení</span><span class="sxs-lookup"><span data-stu-id="9acf7-120">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="9acf7-121">3.0</span><span class="sxs-lookup"><span data-stu-id="9acf7-121">3.0</span></span> |
| [<span data-ttu-id="9acf7-122">ZipArchiveEntry už nezpracovává archivy s nekonzistentními velikostmi záznamů.</span><span class="sxs-lookup"><span data-stu-id="9acf7-122">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="9acf7-123">3.0</span><span class="sxs-lookup"><span data-stu-id="9acf7-123">3.0</span></span> |
| [<span data-ttu-id="9acf7-124">Typ výjimky serializátoru JSON se změnil z JsonException na NotSupportedException.</span><span class="sxs-lookup"><span data-stu-id="9acf7-124">JSON serializer exception type changed from JsonException to NotSupportedException</span></span>](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | <span data-ttu-id="9acf7-125">3.0</span><span class="sxs-lookup"><span data-stu-id="9acf7-125">3.0</span></span> |
| [<span data-ttu-id="9acf7-126">Změna v sémantikě (String) null v Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="9acf7-126">Change in semantics of (string)null in Utf8JsonWriter</span></span>](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | <span data-ttu-id="9acf7-127">3.0</span><span class="sxs-lookup"><span data-stu-id="9acf7-127">3.0</span></span> |
| [<span data-ttu-id="9acf7-128">Metody JsonEncodedText. Encode mají další argument JavaScriptEncoder.</span><span class="sxs-lookup"><span data-stu-id="9acf7-128">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | <span data-ttu-id="9acf7-129">3.0</span><span class="sxs-lookup"><span data-stu-id="9acf7-129">3.0</span></span> |
| [<span data-ttu-id="9acf7-130">Změnil se podpis JsonFactoryConverter. CreateConverter.</span><span class="sxs-lookup"><span data-stu-id="9acf7-130">JsonFactoryConverter.CreateConverter signature changed</span></span>](#jsonfactoryconvertercreateconverter-signature-changed) | <span data-ttu-id="9acf7-131">3.0</span><span class="sxs-lookup"><span data-stu-id="9acf7-131">3.0</span></span> |
| [<span data-ttu-id="9acf7-132">Změny rozhraní API JsonElement</span><span class="sxs-lookup"><span data-stu-id="9acf7-132">JsonElement API changes</span></span>](#jsonelement-api-changes) | <span data-ttu-id="9acf7-133">3.0</span><span class="sxs-lookup"><span data-stu-id="9acf7-133">3.0</span></span> |
| [<span data-ttu-id="9acf7-134">Parametr FieldInfo. SetValue vyvolá výjimku pro statická pole pouze pro init.</span><span class="sxs-lookup"><span data-stu-id="9acf7-134">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="9acf7-135">3.0</span><span class="sxs-lookup"><span data-stu-id="9acf7-135">3.0</span></span> |
| [<span data-ttu-id="9acf7-136">Soukromá pole přidaná k předdefinovaným typům struktury</span><span class="sxs-lookup"><span data-stu-id="9acf7-136">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="9acf7-137">2.1</span><span class="sxs-lookup"><span data-stu-id="9acf7-137">2.1</span></span> |
| [<span data-ttu-id="9acf7-138">Změna výchozí hodnoty UseShellExecute objektu Process</span><span class="sxs-lookup"><span data-stu-id="9acf7-138">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="9acf7-139">2.1</span><span class="sxs-lookup"><span data-stu-id="9acf7-139">2.1</span></span> |
| [<span data-ttu-id="9acf7-140">UnauthorizedAccessException vyvolaná atributy SystemInfo.</span><span class="sxs-lookup"><span data-stu-id="9acf7-140">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="9acf7-141">1.0</span><span class="sxs-lookup"><span data-stu-id="9acf7-141">1.0</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="9acf7-142">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="9acf7-142">.NET Core 3.0</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="9acf7-143">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="9acf7-143">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="9acf7-144">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="9acf7-144">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***
