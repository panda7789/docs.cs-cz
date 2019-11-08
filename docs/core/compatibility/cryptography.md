---
title: Kryptografie – průlomové změny – .NET Core
description: Vypíše zásadní změny týkající se kryptografie v .NET Core.
ms.date: 09/20/2019
ms.openlocfilehash: 628162eb391c27b810e9db0a869896eb8443a06f
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739733"
---
# <a name="cryptography-breaking-changes"></a>Kryptografie – průlomové změny

Následující seznam uvádí zásadní změny týkající se kryptografie podle verze .NET Core.

## <a name="net-core-30-preview-9"></a>.NET Core 3,0 Preview 9

[!INCLUDE[Better argument validation in the Pkcs8PrivateKeyInfo constructor](~/includes/core-changes/cryptography/better-argument-validation-in-pkcs8privatekeyinfo-ctor.md)]

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/net-core-3-0-prefers-openssl-1-1-x.md)]
