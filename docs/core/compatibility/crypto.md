---
title: Kryptografie – průlomové změny, verze 2,2 až 3,0 – .NET Core
description: Uvádí přerušující změny z verze 2,2 na verzi 3,0 rozhraní .NET Core, ASP.NET Core a EF Core.
ms.date: 09/10/2019
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 44caf042404d44ec4c5cb7b7e25883d8460efeb5
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71217064"
---
# <a name="breaking-changes-for-migration-from-version-22-to-30"></a>Narušení změn migrace z verze 2,2 na 3,0

> [!IMPORTANT]
> Tento článek je v rámci konstrukce. Nejedná se o úplný seznam nejnovějších změn .NET Core. Další informace o nejnovějších změnách .NET Core můžete v úložišti dotnet/Docs na GitHubu kontrolovat jednotlivé [problémy se změnami](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Abreaking-change) . 

Pokud migrujete z verze 2,2 na verzi 3,0 rozhraní .NET Core, ASP.NET Core nebo EF Core, přečtěte si následující témata, kde najdete zásadní změny, které by mohly mít vliv na vaši aplikaci:

## <a name="corefx"></a>CoreFx

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/version-information-changes.md)]

***

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

***

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/floating-point-changes.md)]

***

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/move-invalidasynchronousstateexception.md)]

***

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/net-core-3-0-follows-unicode-utf8-best-practices.md)]

***

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/move-typedescriptionproviderattribute.md)]

***

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/ziparchiveentry-and-inconsistent-entry-sizes.md)]

## <a name="cryptography"></a>Kryptografick

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/net-core-3-0-prefers-openssl-1-1-x.md)]

## <a name="globalization"></a>Globalizace

[!INCLUDE["C" locale maps to the invariant locale](~/includes/core-changes/globalization/c-locale-maps-to-invariant-locale.md)]

## <a name="visual-basic"></a>Visual Basic

[!INCLUDE[vbNewLine is obsolete](~/includes/core-changes/visualbasic/vbnewline-is-obsolete.md)]

## <a name="entity-framework-core"></a>Entity Framework Core

[Entity Framework Core přerušující změny](/ef/core/what-is-new/ef-core-3.0/breaking-changes)