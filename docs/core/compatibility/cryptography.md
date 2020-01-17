---
title: Kryptografie – průlomové změny – .NET Core
description: Vypíše zásadní změny týkající se kryptografie v .NET Core.
ms.date: 09/20/2019
ms.openlocfilehash: 4b13985a12ee0530edd3a0960923aafef1696d90
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116465"
---
# <a name="cryptography-breaking-changes"></a><span data-ttu-id="28ec0-103">Kryptografie – průlomové změny</span><span class="sxs-lookup"><span data-stu-id="28ec0-103">Cryptography breaking changes</span></span>

<span data-ttu-id="28ec0-104">Na této stránce jsou popsány následující přerušující se změny:</span><span class="sxs-lookup"><span data-stu-id="28ec0-104">The following breaking changes are documented on this page:</span></span>

- [<span data-ttu-id="28ec0-105">EnvelopedCms ve výchozím nastavení šifrování AES-256</span><span class="sxs-lookup"><span data-stu-id="28ec0-105">EnvelopedCms defaults to AES-256 encryption</span></span>](#envelopedcms-defaults-to-aes-256-encryption)
- [<span data-ttu-id="28ec0-106">Minimální velikost pro generování klíče RSAOpenSsl se zvýšila.</span><span class="sxs-lookup"><span data-stu-id="28ec0-106">Minimum size for RSAOpenSsl key generation has increased</span></span>](#minimum-size-for-rsaopenssl-key-generation-has-increased)
- [<span data-ttu-id="28ec0-107">.NET Core 3,0 upřednostňuje OpenSSL 1.1. x až OpenSSL 1.0. x</span><span class="sxs-lookup"><span data-stu-id="28ec0-107">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>](#net-core-30-prefers-openssl-11x-to-openssl-10x)
- [<span data-ttu-id="28ec0-108">Lepší ověřování argumentu v konstruktoru Pkcs8PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="28ec0-108">Better argument validation in the Pkcs8PrivateKeyInfo constructor</span></span>](#better-argument-validation-in-the-pkcs8privatekeyinfo-constructor)

## <a name="net-core-30"></a><span data-ttu-id="28ec0-109">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="28ec0-109">.NET Core 3.0</span></span>

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

***

## <a name="net-core-30-preview-9"></a><span data-ttu-id="28ec0-110">.NET Core 3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="28ec0-110">.NET Core 3.0 Preview 9</span></span>

[!INCLUDE[Better argument validation in the Pkcs8PrivateKeyInfo constructor](~/includes/core-changes/cryptography/3.0/better-argument-validation-in-pkcs8privatekeyinfo-ctor.md)]

***
