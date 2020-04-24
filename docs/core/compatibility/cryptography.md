---
title: Kryptografie – průlomové změny
description: Uvádí zásadní změny týkající se kryptografie v .NET Core.
ms.date: 04/22/2020
ms.openlocfilehash: 66049473083d87b4c84408f35a04193a4563c2b3
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135595"
---
# <a name="cryptography-breaking-changes"></a><span data-ttu-id="62e58-103">Kryptografie – průlomové změny</span><span class="sxs-lookup"><span data-stu-id="62e58-103">Cryptography breaking changes</span></span>

<span data-ttu-id="62e58-104">Na této stránce jsou popsány následující přerušující se změny:</span><span class="sxs-lookup"><span data-stu-id="62e58-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="62e58-105">Zásadní změna</span><span class="sxs-lookup"><span data-stu-id="62e58-105">Breaking change</span></span> | <span data-ttu-id="62e58-106">Představená verze</span><span class="sxs-lookup"><span data-stu-id="62e58-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="62e58-107">SPUSTIT syntaxi DŮVĚRYHODNÉho certifikátu, který už není podporovaný na Linux</span><span class="sxs-lookup"><span data-stu-id="62e58-107">BEGIN TRUSTED CERTIFICATE syntax no longer supported on Linux</span></span>](#begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux) | <span data-ttu-id="62e58-108">3.0</span><span class="sxs-lookup"><span data-stu-id="62e58-108">3.0</span></span> |
| [<span data-ttu-id="62e58-109">EnvelopedCms ve výchozím nastavení šifrování AES-256</span><span class="sxs-lookup"><span data-stu-id="62e58-109">EnvelopedCms defaults to AES-256 encryption</span></span>](#envelopedcms-defaults-to-aes-256-encryption) | <span data-ttu-id="62e58-110">3.0</span><span class="sxs-lookup"><span data-stu-id="62e58-110">3.0</span></span> |
| [<span data-ttu-id="62e58-111">Minimální velikost pro generování klíče RSAOpenSsl se zvýšila.</span><span class="sxs-lookup"><span data-stu-id="62e58-111">Minimum size for RSAOpenSsl key generation has increased</span></span>](#minimum-size-for-rsaopenssl-key-generation-has-increased) | <span data-ttu-id="62e58-112">3.0</span><span class="sxs-lookup"><span data-stu-id="62e58-112">3.0</span></span> |
| [<span data-ttu-id="62e58-113">.NET Core 3,0 upřednostňuje OpenSSL 1.1. x až OpenSSL 1.0. x</span><span class="sxs-lookup"><span data-stu-id="62e58-113">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>](#net-core-30-prefers-openssl-11x-to-openssl-10x) | <span data-ttu-id="62e58-114">3.0</span><span class="sxs-lookup"><span data-stu-id="62e58-114">3.0</span></span> |
| [<span data-ttu-id="62e58-115">Lepší ověřování argumentu v konstruktoru Pkcs8PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="62e58-115">Better argument validation in the Pkcs8PrivateKeyInfo constructor</span></span>](#better-argument-validation-in-the-pkcs8privatekeyinfo-constructor) | <span data-ttu-id="62e58-116">3.0</span><span class="sxs-lookup"><span data-stu-id="62e58-116">3.0</span></span> |
| [<span data-ttu-id="62e58-117">Je respektován logický parametr SignedCms. ComputeSignature.</span><span class="sxs-lookup"><span data-stu-id="62e58-117">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected) | <span data-ttu-id="62e58-118">2.1</span><span class="sxs-lookup"><span data-stu-id="62e58-118">2.1</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="62e58-119">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="62e58-119">.NET Core 3.0</span></span>

[!INCLUDE [begin-trusted-cert-linux](~/includes/core-changes/cryptography/3.0/begin-trusted-cert-linux.md)]

***

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

***

[!INCLUDE[Better argument validation in the Pkcs8PrivateKeyInfo constructor](~/includes/core-changes/cryptography/3.0/better-argument-validation-in-pkcs8privatekeyinfo-ctor.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="62e58-120">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="62e58-120">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***
