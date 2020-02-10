---
title: Kryptografie – průlomové změny
description: Vypíše zásadní změny týkající se kryptografie v .NET Core.
ms.date: 09/20/2019
ms.openlocfilehash: fcef4b65245a5dd9219cbdbb548ca575a823a949
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093029"
---
# <a name="cryptography-breaking-changes"></a>Kryptografie – průlomové změny

Na této stránce jsou popsány následující přerušující se změny:

- [EnvelopedCms ve výchozím nastavení šifrování AES-256](#envelopedcms-defaults-to-aes-256-encryption)
- [Minimální velikost pro generování klíče RSAOpenSsl se zvýšila.](#minimum-size-for-rsaopenssl-key-generation-has-increased)
- [.NET Core 3,0 upřednostňuje OpenSSL 1.1. x až OpenSSL 1.0. x](#net-core-30-prefers-openssl-11x-to-openssl-10x)
- [Lepší ověřování argumentu v konstruktoru Pkcs8PrivateKeyInfo](#better-argument-validation-in-the-pkcs8privatekeyinfo-constructor)

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

***

## <a name="net-core-30-preview-9"></a>.NET Core 3,0 Preview 9

[!INCLUDE[Better argument validation in the Pkcs8PrivateKeyInfo constructor](~/includes/core-changes/cryptography/3.0/better-argument-validation-in-pkcs8privatekeyinfo-ctor.md)]

***
