---
title: Vytváření šifrovacích schémat
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- encryption [.NET Framework], creating cryptographic schemes
- cryptography [.NET Framework], creating cryptographic schemes
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
ms.openlocfilehash: 1478873c1c2dc73ca31c9078e39a3902966bf674
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288417"
---
# <a name="creating-a-cryptographic-scheme"></a><span data-ttu-id="c828b-102">Vytváření šifrovacích schémat</span><span class="sxs-lookup"><span data-stu-id="c828b-102">Creating a Cryptographic Scheme</span></span>
<span data-ttu-id="c828b-103">Kryptografické komponenty .NET Framework mohou být kombinovány pro vytváření různých schémat pro šifrování a dešifrování dat.</span><span class="sxs-lookup"><span data-stu-id="c828b-103">The cryptographic components of the .NET Framework can be combined to create different schemes to encrypt and decrypt data.</span></span>  
  
 <span data-ttu-id="c828b-104">Jednoduché kryptografické schéma pro šifrování a dešifrování dat může určovat následující kroky:</span><span class="sxs-lookup"><span data-stu-id="c828b-104">A simple cryptographic scheme for encrypting and decrypting data might specify the following steps:</span></span>  
  
1. <span data-ttu-id="c828b-105">Každá strana vygeneruje pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="c828b-105">Each party generates a public/private key pair.</span></span>  
  
2. <span data-ttu-id="c828b-106">Smluvní strany si vyměňují jejich veřejné klíče.</span><span class="sxs-lookup"><span data-stu-id="c828b-106">The parties exchange their public keys.</span></span>  
  
3. <span data-ttu-id="c828b-107">Každá ze smluvních stran generuje tajný klíč pro šifrování TripleDES, například a zašifruje nově vytvořený klíč pomocí veřejného klíče druhého.</span><span class="sxs-lookup"><span data-stu-id="c828b-107">Each party generates a secret key for TripleDES encryption, for example, and encrypts the newly created key using the other's public key.</span></span>  
  
4. <span data-ttu-id="c828b-108">Každá ze smluvních stran odesílá data do druhé a kombinuje tajný klíč druhé s vlastním tajným klíčem, a to v konkrétním pořadí pro vytvoření nového tajného klíče.</span><span class="sxs-lookup"><span data-stu-id="c828b-108">Each party sends the data to the other and combines the other's secret key with its own, in a particular order, to create a new secret key.</span></span>  
  
5. <span data-ttu-id="c828b-109">Strany pak iniciují konverzaci pomocí symetrického šifrování.</span><span class="sxs-lookup"><span data-stu-id="c828b-109">The parties then initiate a conversation using symmetric encryption.</span></span>  
  
 <span data-ttu-id="c828b-110">Vytváření šifrovacího schématu není triviální úloha.</span><span class="sxs-lookup"><span data-stu-id="c828b-110">Creating a cryptographic scheme is not a trivial task.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c828b-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="c828b-111">See also</span></span>

- [<span data-ttu-id="c828b-112">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="c828b-112">Cryptographic Services</span></span>](cryptographic-services.md)
