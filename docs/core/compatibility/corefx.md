---
title: Přerušující změny knihovny základních tříd
description: Obsahuje seznam nejnovějších změn v základních knihovnách .NET.
ms.date: 09/20/2019
ms.openlocfilehash: bc80f27a8a98890a93ad3b99e09ea7ea380d506c
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158468"
---
# <a name="core-net-libraries-breaking-changes"></a>Základní knihovny .NET – přerušující změny

Základní knihovny .NET poskytují primitivní a další obecné typy používané .NET Core.

Na této stránce jsou popsány následující přerušující se změny:

| Zásadní změna | Představená verze |
| - | :-: |
| [Rozhraní API, která verze sestav nyní hlásí produkt a nikoli verzi souboru](#apis-that-report-version-now-report-product-and-not-file-version) | 3.0 |
| [Vlastní instance EncoderFallbackBuffer se nemůžou vrátit rekurzivně.](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | 3.0 |
| [Změny chování při formátování a analýze plovoucí desetinné čárky](#floating-point-formatting-and-parsing-behavior-changed) | 3.0 |
| [Operace analýzy s plovoucí desetinnou čárkou již nejsou úspěšné nebo vyvolávají výjimku OverflowException](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | 3.0 |
| [InvalidAsynchronousStateException – přesunuté do jiného sestavení](#invalidasynchronousstateexception-moved-to-another-assembly) | 3.0 |
| [Výměna chybně formátovaných sekvencí UTF-8 se řídí pokyny pro kódování Unicode](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | 3.0 |
| [TypeDescriptionProviderAttribute přesunuté do jiného sestavení](#typedescriptionproviderattribute-moved-to-another-assembly) | 3.0 |
| [ZipArchiveEntry už nezpracovává archivy s nekonzistentními velikostmi záznamů.](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | 3.0 |
| [Typ výjimky serializátoru JSON se změnil z JsonException na NotSupportedException.](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | 3.0 |
| [Změna v sémantikě (String) null v Utf8JsonWriter](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | 3.0 |
| [Metody JsonEncodedText. Encode mají další argument JavaScriptEncoder.](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | 3.0 |
| [Změnil se podpis JsonFactoryConverter. CreateConverter.](#jsonfactoryconvertercreateconverter-signature-changed) | 3.0 |
| [Změny rozhraní API JsonElement](#jsonelement-api-changes) | 3.0 |
| [Parametr FieldInfo. SetValue vyvolá výjimku pro statická pole pouze pro init.](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | 3.0 |
| [Soukromá pole přidaná k předdefinovaným typům struktury](#private-fields-added-to-built-in-struct-types) | 2.1 |
| [Změna výchozí hodnoty UseShellExecute objektu Process](#change-in-default-value-of-useshellexecute) | 2.1 |
| [Verze OpenSSL v macOS](#openssl-versions-on-macos) | 2.1 |
| [UnauthorizedAccessException vyvolaná atributy SystemInfo.](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | 1.0 |
| [Manipulace s poškozenými výjimkami stavu procesu není podporována.](#handling-corrupted-state-exceptions-is-not-supported) | 1.0 |

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

## <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a>.NET Core 1,0

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***
