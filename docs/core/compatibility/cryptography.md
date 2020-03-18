---
title: Kryptografie láme změny
description: Zobrazí seznam změn změny související s kryptografií v množení .NET Core.
ms.date: 02/10/2020
ms.openlocfilehash: c25eefa8e3ee01ed7a1df4ec4aa9225f2c347a4d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449210"
---
# <a name="cryptography-breaking-changes"></a><span data-ttu-id="3165a-103">Kryptografie láme změny</span><span class="sxs-lookup"><span data-stu-id="3165a-103">Cryptography breaking changes</span></span>

<span data-ttu-id="3165a-104">Na této stránce jsou popsány následující změny:</span><span class="sxs-lookup"><span data-stu-id="3165a-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="3165a-105">Narušující změny</span><span class="sxs-lookup"><span data-stu-id="3165a-105">Breaking change</span></span> | <span data-ttu-id="3165a-106">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="3165a-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="3165a-107">Standardy EnvelopedCms jsou výchozí pro šifrování AES-256</span><span class="sxs-lookup"><span data-stu-id="3165a-107">EnvelopedCms defaults to AES-256 encryption</span></span>](#envelopedcms-defaults-to-aes-256-encryption) | <span data-ttu-id="3165a-108">3.0</span><span class="sxs-lookup"><span data-stu-id="3165a-108">3.0</span></span> |
| [<span data-ttu-id="3165a-109">Minimální velikost pro generování klíčů RSAOpenSsl se zvýšila</span><span class="sxs-lookup"><span data-stu-id="3165a-109">Minimum size for RSAOpenSsl key generation has increased</span></span>](#minimum-size-for-rsaopenssl-key-generation-has-increased) | <span data-ttu-id="3165a-110">3.0</span><span class="sxs-lookup"><span data-stu-id="3165a-110">3.0</span></span> |
| [<span data-ttu-id="3165a-111">.NET Core 3.0 preferuje OpenSSL 1.1.x na OpenSSL 1.0.x</span><span class="sxs-lookup"><span data-stu-id="3165a-111">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>](#net-core-30-prefers-openssl-11x-to-openssl-10x) | <span data-ttu-id="3165a-112">3.0</span><span class="sxs-lookup"><span data-stu-id="3165a-112">3.0</span></span> |
| [<span data-ttu-id="3165a-113">Lepší ověření argumentu v konstruktoru Pkcs8PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="3165a-113">Better argument validation in the Pkcs8PrivateKeyInfo constructor</span></span>](#better-argument-validation-in-the-pkcs8privatekeyinfo-constructor) | <span data-ttu-id="3165a-114">3.0</span><span class="sxs-lookup"><span data-stu-id="3165a-114">3.0</span></span> |
| [<span data-ttu-id="3165a-115">Logický parametr SignedCms.ComputeSignature je respektován</span><span class="sxs-lookup"><span data-stu-id="3165a-115">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected) | <span data-ttu-id="3165a-116">2.1</span><span class="sxs-lookup"><span data-stu-id="3165a-116">2.1</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="3165a-117">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="3165a-117">.NET Core 3.0</span></span>

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

***

[!INCLUDE[Better argument validation in the Pkcs8PrivateKeyInfo constructor](~/includes/core-changes/cryptography/3.0/better-argument-validation-in-pkcs8privatekeyinfo-ctor.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="3165a-118">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="3165a-118">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***
