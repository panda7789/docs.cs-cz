---
title: Ověřování zabezpečení a počet selhání ověření za sekundu
ms.date: 03/30/2017
ms.assetid: 266c3bd3-2ffc-4471-94b7-3675443be1ac
ms.openlocfilehash: 546d81b73e912915d265fb194de4ad9e45d55cea
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163914"
---
# <a name="security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="8963e-102">Ověřování zabezpečení a počet selhání ověření za sekundu</span><span class="sxs-lookup"><span data-stu-id="8963e-102">Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="8963e-103">Název čítače: ověření zabezpečení a počet selhání ověření za sekundu.</span><span class="sxs-lookup"><span data-stu-id="8963e-103">Counter name: Security Validation and Authentication Failures Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8963e-104">Popis</span><span class="sxs-lookup"><span data-stu-id="8963e-104">Description</span></span>  
 <span data-ttu-id="8963e-105">Tento čítač se zvyšuje vždy, když je zpráva odmítnuta z důvodu problému se zabezpečením, na který nepokrývá čítač "počet neautorizovaných volání zabezpečení".</span><span class="sxs-lookup"><span data-stu-id="8963e-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="8963e-106">Mezi takové problémy patří:</span><span class="sxs-lookup"><span data-stu-id="8963e-106">Such problems include:</span></span>  
  
- <span data-ttu-id="8963e-107">Z zprávy nelze číst token klienta.</span><span class="sxs-lookup"><span data-stu-id="8963e-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="8963e-108">Token klienta se nezdařil při ověřování (například chybné heslo).</span><span class="sxs-lookup"><span data-stu-id="8963e-108">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="8963e-109">Ověření podpisu se nezdařilo (například zpráva byla zfalšována).</span><span class="sxs-lookup"><span data-stu-id="8963e-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="8963e-110">Zpráva je duplicitní z předchozí verze, ke které může dojít během útoku prostřednictvím opakovaného přehrání.</span><span class="sxs-lookup"><span data-stu-id="8963e-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="8963e-111">Došlo k chybě dešifrování.</span><span class="sxs-lookup"><span data-stu-id="8963e-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="8963e-112">Ve zprávě chybí některé povinné prvky (například chybějící časové razítko nebo šifrovaný blok dat).</span><span class="sxs-lookup"><span data-stu-id="8963e-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="8963e-113">Během TLSNEGO/SPNEGO handshake došlo k chybám.</span><span class="sxs-lookup"><span data-stu-id="8963e-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="8963e-114">Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), jehož hodnota se počítá pomocí následujícího vzorce:</span><span class="sxs-lookup"><span data-stu-id="8963e-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula:</span></span>  
  
 <span data-ttu-id="8963e-115">(N1-N0)/((D1-D0)/F)</span><span class="sxs-lookup"><span data-stu-id="8963e-115">(N1-N0)/((D1-D0)/F)</span></span>
