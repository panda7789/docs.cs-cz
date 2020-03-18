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
# <a name="corefx-breaking-changes"></a>CoreFx láme změny

CoreFx poskytuje primitiva a další obecné typy používané .NET Core.

Na této stránce jsou popsány následující změny:

| Narušující změny | Zavedená verze |
| - | :-: |
| [Api, která sestavy verze nyní sestavy produktu a není verze souboru](#apis-that-report-version-now-report-product-and-not-file-version) | 3.0 |
| [Vlastní instance EncoderFallbackBuffer nemohou rekurzivně ustoupit](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | 3.0 |
| [Změny chování formátování s plovoucí desetinnou táhou a analýza](#floating-point-formatting-and-parsing-behavior-changed) | 3.0 |
| [Operace analýzy s plovoucí desetinnou táhou již neselžou nebo nevyvolá vyzvučují výjimku Přetečení](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | 3.0 |
| [InvalidAsynchronousStateException přesunuta do jiného sestavení](#invalidasynchronousstateexception-moved-to-another-assembly) | 3.0 |
| [NET Core 3.0 se řídí osvědčenými postupy Unicode při výměně špatně vytvořených bajtových sekvencí UTF-8](#net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences) | 3.0 |
| [TypeDescriptionProviderAttribute přesunutdo jiného sestavení](#typedescriptionproviderattribute-moved-to-another-assembly) | 3.0 |
| [ZipArchiveEntry již zpracovává archivy s nekonzistentními velikostmi položek](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | 3.0 |
| [Typ výjimky serializátoru JSON byl změněn z JsonException na NotSupportedException](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | 3.0 |
| [Změna sémantiky (string)null v Utf8JsonWriter](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | 3.0 |
| [Metody JsonEncodedText.Encode mají další argument JavaScriptEncoder](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | 3.0 |
| [JsonFactoryConverter.CreateConverter podpis změněn](#jsonfactoryconvertercreateconverter-signature-changed) | 3.0 |
| [Změny rozhraní API Prvku JsonElement](#jsonelement-api-changes) | 3.0 |
| [FieldInfo.SetValue vyvolá výjimku pro statická pole pouze init.](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | 3.0 |
| [Soukromá pole přidaná k předdefinovaným typům struktury](#private-fields-added-to-built-in-struct-types) | 2.1 |
| [Změna výchozí hodnoty useShellExecute](#change-in-default-value-of-useshellexecute) | 2.1 |
| [Verze OpenSSL v macOS](#openssl-versions-on-macos) | 2.1 |
| [UnauthorizedAccessException vyvoláno souborem FileSystemInfo.Attributes](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | 1.0 |

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

## <a name="net-core-10"></a>.NET Jádro 1.0

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***
