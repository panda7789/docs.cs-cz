---
title: Přerušující změny knihovny základních tříd
description: Obsahuje seznam nejnovějších změn v rozhraní .NET CoreFx, knihovny základních tříd.
ms.date: 09/20/2019
ms.openlocfilehash: 9e8a00abfae8bf8f5301a4879cb5274492a2b6fd
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093081"
---
# <a name="corefx-breaking-changes"></a>CoreFx průlomové změny

CoreFx poskytuje primitivní a další obecné typy používané .NET Core.

Na této stránce jsou popsány následující přerušující se změny:

- [Rozhraní API, která verze sestav nyní hlásí produkt a nikoli verzi souboru](#apis-that-report-version-now-report-product-and-not-file-version)
- [Vlastní instance EncoderFallbackBuffer se nemůžou vrátit rekurzivně.](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively)
- [Změny chování při formátování a analýze plovoucí desetinné čárky](#floating-point-formatting-and-parsing-behavior-changed)
- [Operace analýzy s plovoucí desetinnou čárkou již nejsou úspěšné nebo vyvolávají výjimku OverflowException](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception)
- [InvalidAsynchronousStateException – přesunuté do jiného sestavení](#invalidasynchronousstateexception-moved-to-another-assembly)
- [.NET Core 3,0 se řídí osvědčenými postupy Unicode při nahrazování nesprávně naformátovaných sekvencí bajtů UTF-8.](#net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences)
- [TypeDescriptionProviderAttribute přesunuté do jiného sestavení](#typedescriptionproviderattribute-moved-to-another-assembly)
- [ZipArchiveEntry už nezpracovává archivy s nekonzistentními velikostmi záznamů.](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes)
- [Typ výjimky serializátoru JSON se změnil z JsonException na NotSupportedException.](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception)
- [Změna v sémantikě (String) null v Utf8JsonWriter](#change-in-semantics-of-stringnull-in-utf8jsonwriter)
- [Metody JsonEncodedText. Encode mají další argument JavaScriptEncoder.](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument)
- [Změnil se podpis JsonFactoryConverter. CreateConverter.](#jsonfactoryconvertercreateconverter-signature-changed)
- [Změny rozhraní API JsonElement](#jsonelement-api-changes)
- [Soukromá pole přidaná k předdefinovaným typům struktury](#private-fields-added-to-built-in-struct-types)
- [Změna výchozí hodnoty UseShellExecute objektu Process](#change-in-default-value-of-useshellexecute)

## <a name="net-core-30"></a>.NET Core 3.0

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

## <a name="net-core-30-preview-9"></a>.NET Core 3,0 Preview 9

[!INCLUDE[JSON serializer exception type changed from JsonException to NotSupportedException](~/includes/core-changes/corefx/3.0/serializer-throws-notsupportedexception.md)]

***

## <a name="net-core-30-preview-8"></a>.NET Core 3,0 Preview 8

[!INCLUDE[Change in semantics of (string)null in Utf8JsonWriter](~/includes/core-changes/corefx/3.0/change-in-null-in-utf8jsonwriter.md)]

***

[!INCLUDE[JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument](~/includes/core-changes/corefx/3.0/jsonencodedtext-encode-has-additional-argument.md)]

***

[!INCLUDE[JsonFactoryConverter.CreateConverter signature changed](~/includes/core-changes/corefx/3.0/jsonfactoryconverter-createconverter.md)]

***

## <a name="net-core-30-preview-7"></a>.NET Core 3,0 Preview 7

[!INCLUDE[JsonElement API changes](~/includes/core-changes/corefx/3.0/jsonelement-api-changes.md)]

***

## <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***
