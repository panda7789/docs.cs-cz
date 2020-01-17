---
title: Zásadní změny v knihovně základních tříd – .NET Core
description: Obsahuje seznam nejnovějších změn v rozhraní .NET CoreFx, knihovny základních tříd.
ms.date: 09/20/2019
ms.openlocfilehash: eb416a0b061bfe50db330627c0ea68e0ba0c9079
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116503"
---
# <a name="corefx-breaking-changes"></a><span data-ttu-id="23d0b-103">CoreFx průlomové změny</span><span class="sxs-lookup"><span data-stu-id="23d0b-103">CoreFx breaking changes</span></span>

<span data-ttu-id="23d0b-104">CoreFx poskytuje primitivní a další obecné typy používané .NET Core.</span><span class="sxs-lookup"><span data-stu-id="23d0b-104">CoreFx provides the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="23d0b-105">Na této stránce jsou popsány následující přerušující se změny:</span><span class="sxs-lookup"><span data-stu-id="23d0b-105">The following breaking changes are documented on this page:</span></span>

- [<span data-ttu-id="23d0b-106">Rozhraní API, která verze sestav nyní hlásí produkt a nikoli verzi souboru</span><span class="sxs-lookup"><span data-stu-id="23d0b-106">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version)
- [<span data-ttu-id="23d0b-107">Vlastní instance EncoderFallbackBuffer se nemůžou vrátit rekurzivně.</span><span class="sxs-lookup"><span data-stu-id="23d0b-107">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively)
- [<span data-ttu-id="23d0b-108">Změny chování při formátování a analýze plovoucí desetinné čárky</span><span class="sxs-lookup"><span data-stu-id="23d0b-108">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed)
- [<span data-ttu-id="23d0b-109">Operace analýzy s plovoucí desetinnou čárkou již nejsou úspěšné nebo vyvolávají výjimku OverflowException</span><span class="sxs-lookup"><span data-stu-id="23d0b-109">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception)
- [<span data-ttu-id="23d0b-110">InvalidAsynchronousStateException – přesunuté do jiného sestavení</span><span class="sxs-lookup"><span data-stu-id="23d0b-110">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly)
- [<span data-ttu-id="23d0b-111">.NET Core 3,0 se řídí osvědčenými postupy Unicode při nahrazování nesprávně naformátovaných sekvencí bajtů UTF-8.</span><span class="sxs-lookup"><span data-stu-id="23d0b-111">NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences</span></span>](#net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences)
- [<span data-ttu-id="23d0b-112">TypeDescriptionProviderAttribute přesunuté do jiného sestavení</span><span class="sxs-lookup"><span data-stu-id="23d0b-112">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly)
- [<span data-ttu-id="23d0b-113">ZipArchiveEntry už nezpracovává archivy s nekonzistentními velikostmi záznamů.</span><span class="sxs-lookup"><span data-stu-id="23d0b-113">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes)
- [<span data-ttu-id="23d0b-114">Typ výjimky serializátoru JSON se změnil z JsonException na NotSupportedException.</span><span class="sxs-lookup"><span data-stu-id="23d0b-114">JSON serializer exception type changed from JsonException to NotSupportedException</span></span>](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception)
- [<span data-ttu-id="23d0b-115">Změna v sémantikě (String) null v Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="23d0b-115">Change in semantics of (string)null in Utf8JsonWriter</span></span>](#change-in-semantics-of-stringnull-in-utf8jsonwriter)
- [<span data-ttu-id="23d0b-116">Metody JsonEncodedText. Encode mají další argument JavaScriptEncoder.</span><span class="sxs-lookup"><span data-stu-id="23d0b-116">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument)
- [<span data-ttu-id="23d0b-117">Změnil se podpis JsonFactoryConverter. CreateConverter.</span><span class="sxs-lookup"><span data-stu-id="23d0b-117">JsonFactoryConverter.CreateConverter signature changed</span></span>](#jsonfactoryconvertercreateconverter-signature-changed)
- [<span data-ttu-id="23d0b-118">Změny rozhraní API JsonElement</span><span class="sxs-lookup"><span data-stu-id="23d0b-118">JsonElement API changes</span></span>](#jsonelement-api-changes)
- [<span data-ttu-id="23d0b-119">Soukromá pole přidaná k předdefinovaným typům struktury</span><span class="sxs-lookup"><span data-stu-id="23d0b-119">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types)
- [<span data-ttu-id="23d0b-120">Změna výchozí hodnoty UseShellExecute objektu Process</span><span class="sxs-lookup"><span data-stu-id="23d0b-120">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute)

## <a name="net-core-30"></a><span data-ttu-id="23d0b-121">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="23d0b-121">.NET Core 3.0</span></span>

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

## <a name="net-core-30-preview-9"></a><span data-ttu-id="23d0b-122">.NET Core 3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="23d0b-122">.NET Core 3.0 Preview 9</span></span>

[!INCLUDE[JSON serializer exception type changed from JsonException to NotSupportedException](~/includes/core-changes/corefx/3.0/serializer-throws-notsupportedexception.md)]

***

## <a name="net-core-30-preview-8"></a><span data-ttu-id="23d0b-123">.NET Core 3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="23d0b-123">.NET Core 3.0 Preview 8</span></span>

[!INCLUDE[Change in semantics of (string)null in Utf8JsonWriter](~/includes/core-changes/corefx/3.0/change-in-null-in-utf8jsonwriter.md)]

***

[!INCLUDE[JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument](~/includes/core-changes/corefx/3.0/jsonencodedtext-encode-has-additional-argument.md)]

***

[!INCLUDE[JsonFactoryConverter.CreateConverter signature changed](~/includes/core-changes/corefx/3.0/jsonfactoryconverter-createconverter.md)]

***

## <a name="net-core-30-preview-7"></a><span data-ttu-id="23d0b-124">.NET Core 3,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="23d0b-124">.NET Core 3.0 Preview 7</span></span>

[!INCLUDE[JsonElement API changes](~/includes/core-changes/corefx/3.0/jsonelement-api-changes.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="23d0b-125">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="23d0b-125">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***
