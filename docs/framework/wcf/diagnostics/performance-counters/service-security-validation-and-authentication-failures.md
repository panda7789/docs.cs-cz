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
# <a name="service-security-validation-and-authentication-failures"></a><span data-ttu-id="999ac-102">Služba: Počet chyb ověření zabezpečení</span><span class="sxs-lookup"><span data-stu-id="999ac-102">Service: Security Validation and Authentication Failures</span></span>
<span data-ttu-id="999ac-103">Název čítače: ověření zabezpečení a selhání ověřování</span><span class="sxs-lookup"><span data-stu-id="999ac-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="999ac-104">Popis</span><span class="sxs-lookup"><span data-stu-id="999ac-104">Description</span></span>  
 <span data-ttu-id="999ac-105">Tento čítač se zvyšuje vždy, když je zpráva odmítnuta z důvodu problému se zabezpečením, na který nepokrývá čítač "počet neautorizovaných volání zabezpečení".</span><span class="sxs-lookup"><span data-stu-id="999ac-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="999ac-106">Mezi takové problémy patří:</span><span class="sxs-lookup"><span data-stu-id="999ac-106">Such problems include:</span></span>  
  
- <span data-ttu-id="999ac-107">Z zprávy nelze číst token klienta.</span><span class="sxs-lookup"><span data-stu-id="999ac-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="999ac-108">Token klienta se nezdařil při ověřování (například chybné heslo).</span><span class="sxs-lookup"><span data-stu-id="999ac-108">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="999ac-109">Ověření podpisu se nezdařilo (například zpráva byla zfalšována).</span><span class="sxs-lookup"><span data-stu-id="999ac-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="999ac-110">Zpráva je duplicitní z předchozí verze, ke které může dojít během útoku prostřednictvím opakovaného přehrání.</span><span class="sxs-lookup"><span data-stu-id="999ac-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="999ac-111">Došlo k chybě dešifrování.</span><span class="sxs-lookup"><span data-stu-id="999ac-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="999ac-112">Ve zprávě chybí některé povinné prvky (například chybějící časové razítko nebo šifrovaný blok dat).</span><span class="sxs-lookup"><span data-stu-id="999ac-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="999ac-113">Během TLSNEGO/SPNEGO handshake došlo k chybám.</span><span class="sxs-lookup"><span data-stu-id="999ac-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
