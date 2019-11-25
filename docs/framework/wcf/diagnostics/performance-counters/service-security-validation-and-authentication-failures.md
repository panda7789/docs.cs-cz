---
title: 'Služba: Počet chyb ověření zabezpečení'
ms.date: 03/30/2017
ms.assetid: 55c98268-b1ad-459d-851b-25ef52248187
ms.openlocfilehash: 399249926bcb1383fd33f60510c2c212c6f4261c
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204584"
---
# <a name="service-security-validation-and-authentication-failures"></a><span data-ttu-id="ce730-102">Služba: Počet chyb ověření zabezpečení</span><span class="sxs-lookup"><span data-stu-id="ce730-102">Service: Security Validation and Authentication Failures</span></span>
<span data-ttu-id="ce730-103">Counter name: Security Validation and Authentication Failures</span><span class="sxs-lookup"><span data-stu-id="ce730-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="ce730-104">Popis</span><span class="sxs-lookup"><span data-stu-id="ce730-104">Description</span></span>  
 <span data-ttu-id="ce730-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span><span class="sxs-lookup"><span data-stu-id="ce730-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="ce730-106">Such problems include:</span><span class="sxs-lookup"><span data-stu-id="ce730-106">Such problems include:</span></span>  
  
- <span data-ttu-id="ce730-107">Client token cannot be read from the message.</span><span class="sxs-lookup"><span data-stu-id="ce730-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="ce730-108">Client token has failed authentication (for example, bad password).</span><span class="sxs-lookup"><span data-stu-id="ce730-108">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="ce730-109">Signature verification has failed (for example, the message has been tampered).</span><span class="sxs-lookup"><span data-stu-id="ce730-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="ce730-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span><span class="sxs-lookup"><span data-stu-id="ce730-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="ce730-111">A decryption failure has occurred.</span><span class="sxs-lookup"><span data-stu-id="ce730-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="ce730-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span><span class="sxs-lookup"><span data-stu-id="ce730-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="ce730-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span><span class="sxs-lookup"><span data-stu-id="ce730-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
