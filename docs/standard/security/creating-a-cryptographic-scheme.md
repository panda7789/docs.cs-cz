---
title: "Vytváření šifrovacích schémat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- encryption [.NET Framework], creating cryptographic schemes
- cryptography [.NET Framework], creating cryptographic schemes
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b0aabdc9150aea73ad9078b0e9ee92b2abd03e17
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="creating-a-cryptographic-scheme"></a><span data-ttu-id="3a5bc-102">Vytváření šifrovacích schémat</span><span class="sxs-lookup"><span data-stu-id="3a5bc-102">Creating a Cryptographic Scheme</span></span>
<span data-ttu-id="3a5bc-103">K vytvoření různých schémat k šifrování a dešifrování dat mohou být kombinovány kryptografické součásti rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3a5bc-103">The cryptographic components of the .NET Framework can be combined to create different schemes to encrypt and decrypt data.</span></span>  
  
 <span data-ttu-id="3a5bc-104">Jednoduchý kryptografických sloužící k šifrování a dešifrování dat může určit následující kroky:</span><span class="sxs-lookup"><span data-stu-id="3a5bc-104">A simple cryptographic scheme for encrypting and decrypting data might specify the following steps:</span></span>  
  
1.  <span data-ttu-id="3a5bc-105">Každá strana vygeneruje pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="3a5bc-105">Each party generates a public/private key pair.</span></span>  
  
2.  <span data-ttu-id="3a5bc-106">Strany vyměňují své veřejné klíče.</span><span class="sxs-lookup"><span data-stu-id="3a5bc-106">The parties exchange their public keys.</span></span>  
  
3.  <span data-ttu-id="3a5bc-107">Každá strana vygeneruje tajný klíč pro šifrování TripleDES, například a nově vytvořený klíč zašifruje pomocí veřejného klíče druhé strany.</span><span class="sxs-lookup"><span data-stu-id="3a5bc-107">Each party generates a secret key for TripleDES encryption, for example, and encrypts the newly created key using the other's public key.</span></span>  
  
4.  <span data-ttu-id="3a5bc-108">Každá strana odesílá data na druhý a kombinují jiný tajný klíč s vlastní, v konkrétní pořadí, chcete-li vytvořit nový tajný klíč.</span><span class="sxs-lookup"><span data-stu-id="3a5bc-108">Each party sends the data to the other and combines the other's secret key with its own, in a particular order, to create a new secret key.</span></span>  
  
5.  <span data-ttu-id="3a5bc-109">Strany poté zahájit konverzaci pomocí symetrického šifrování.</span><span class="sxs-lookup"><span data-stu-id="3a5bc-109">The parties then initiate a conversation using symmetric encryption.</span></span>  
  
 <span data-ttu-id="3a5bc-110">Vytvoření kryptografických schémat není jednoduchý úkol.</span><span class="sxs-lookup"><span data-stu-id="3a5bc-110">Creating a cryptographic scheme is not a trivial task.</span></span> <span data-ttu-id="3a5bc-111">Další informace o používání šifrování najdete v tématu Kryptografie v dokumentaci platformy sady SDK na http://msdn.microsoft.com/library.</span><span class="sxs-lookup"><span data-stu-id="3a5bc-111">For more information on using cryptography, see the Cryptography topic in the Platform SDK documentation at http://msdn.microsoft.com/library.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a5bc-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="3a5bc-112">See Also</span></span>  
 [<span data-ttu-id="3a5bc-113">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="3a5bc-113">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
