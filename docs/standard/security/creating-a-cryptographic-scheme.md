---
title: Vytváření šifrovacích schémat
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- encryption [.NET Framework], creating cryptographic schemes
- cryptography [.NET Framework], creating cryptographic schemes
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3ef3741ef5cec720c2fb285c9aa60d610acc0be9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59321650"
---
# <a name="creating-a-cryptographic-scheme"></a><span data-ttu-id="cf9e3-102">Vytváření šifrovacích schémat</span><span class="sxs-lookup"><span data-stu-id="cf9e3-102">Creating a Cryptographic Scheme</span></span>
<span data-ttu-id="cf9e3-103">Kryptografické součásti rozhraní .NET Framework mohou být kombinovány pro vytvoření různých schémat k šifrování a dešifrování dat.</span><span class="sxs-lookup"><span data-stu-id="cf9e3-103">The cryptographic components of the .NET Framework can be combined to create different schemes to encrypt and decrypt data.</span></span>  
  
 <span data-ttu-id="cf9e3-104">Jednoduché šifrovacích schémat pro šifrování a dešifrování dat například zadat následující kroky:</span><span class="sxs-lookup"><span data-stu-id="cf9e3-104">A simple cryptographic scheme for encrypting and decrypting data might specify the following steps:</span></span>  
  
1. <span data-ttu-id="cf9e3-105">Každá ze smluvních stran generuje pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="cf9e3-105">Each party generates a public/private key pair.</span></span>  
  
2. <span data-ttu-id="cf9e3-106">Smluvní strany vyměňují své veřejné klíče.</span><span class="sxs-lookup"><span data-stu-id="cf9e3-106">The parties exchange their public keys.</span></span>  
  
3. <span data-ttu-id="cf9e3-107">Každá ze smluvních stran vygeneruje tajný klíč pro šifrování TripleDES, například a nově vytvořený klíč zašifruje pomocí veřejného klíče druhé strany.</span><span class="sxs-lookup"><span data-stu-id="cf9e3-107">Each party generates a secret key for TripleDES encryption, for example, and encrypts the newly created key using the other's public key.</span></span>  
  
4. <span data-ttu-id="cf9e3-108">Každá ze smluvních stran odesílá data do jiné a zkombinuje tajný klíč druhé strany s vlastní, v určitém pořadí, chcete-li vytvořit nový tajný klíč.</span><span class="sxs-lookup"><span data-stu-id="cf9e3-108">Each party sends the data to the other and combines the other's secret key with its own, in a particular order, to create a new secret key.</span></span>  
  
5. <span data-ttu-id="cf9e3-109">Smluvní strany souhlasí potom zahájit konverzaci pomocí symetrického šifrování.</span><span class="sxs-lookup"><span data-stu-id="cf9e3-109">The parties then initiate a conversation using symmetric encryption.</span></span>  
  
 <span data-ttu-id="cf9e3-110">Vytváření šifrovacích schémat není jednoduchý úkol.</span><span class="sxs-lookup"><span data-stu-id="cf9e3-110">Creating a cryptographic scheme is not a trivial task.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="cf9e3-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cf9e3-111">See also</span></span>

- [<span data-ttu-id="cf9e3-112">Šifrovací služby</span><span class="sxs-lookup"><span data-stu-id="cf9e3-112">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
