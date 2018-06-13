---
title: 'Postupy: Přístup k hardwarovým šifrovacím zařízením'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- encryption
- key card
- cryptography
- hardware encryption
- CspParameters
ms.assetid: b0e734df-6eb4-4b16-b48c-6f0fe82d5f17
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c0d5b72e9067a5a6304d88d1e09716088637cbfd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581713"
---
# <a name="how-to-access-hardware-encryption-devices"></a><span data-ttu-id="40070-102">Postupy: Přístup k hardwarovým šifrovacím zařízením</span><span class="sxs-lookup"><span data-stu-id="40070-102">How to: Access Hardware Encryption Devices</span></span>
<span data-ttu-id="40070-103">Můžete použít <xref:System.Security.Cryptography.CspParameters> třída pro přístup k hardwarovým šifrovacím zařízením.</span><span class="sxs-lookup"><span data-stu-id="40070-103">You can use the <xref:System.Security.Cryptography.CspParameters> class to access hardware encryption devices.</span></span> <span data-ttu-id="40070-104">Tuto třídu můžete použít například k integraci vaší aplikace pomocí čipové karty, hardwaru generátoru náhodných čísel nebo hardwarové implementaci konkrétního šifrovacího algoritmu.</span><span class="sxs-lookup"><span data-stu-id="40070-104">For example, you can use this class to integrate your application with a smart card, a hardware random number generator, or a hardware implementation of a particular cryptographic algorithm.</span></span>  
  
 <span data-ttu-id="40070-105"><xref:System.Security.Cryptography.CspParameters> Třída vytvoří zprostředkovatele kryptografických služeb (CSP), který přistupuje k šifrování zařízení správně nainstalovaný hardware.</span><span class="sxs-lookup"><span data-stu-id="40070-105">The <xref:System.Security.Cryptography.CspParameters> class creates a cryptographic service provider (CSP) that accesses a properly installed hardware encryption device.</span></span>  <span data-ttu-id="40070-106">Dostupnost zprostředkovatele kryptografických služeb můžete ověřit zkontrolováním následující klíč registru pomocí Editoru registru (Regedit.exe): HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider.</span><span class="sxs-lookup"><span data-stu-id="40070-106">You can verify the availability of a CSP by inspecting the following registry key using the Registry Editor (Regedit.exe):  HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider.</span></span>  
  
### <a name="to-sign-data-using-a-key-card"></a><span data-ttu-id="40070-107">Podepsat data pomocí klíče karty</span><span class="sxs-lookup"><span data-stu-id="40070-107">To sign data using a key card</span></span>  
  
1.  <span data-ttu-id="40070-108">Vytvořit novou instanci třídy <xref:System.Security.Cryptography.CspParameters> třídy a předejte typ integer poskytovatele a název zprostředkovatele pro konstruktor.</span><span class="sxs-lookup"><span data-stu-id="40070-108">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2.  <span data-ttu-id="40070-109">Předat příslušné příznaky tak, aby <xref:System.Security.Cryptography.CspParameters.Flags%2A> vlastnost nově vytvořený <xref:System.Security.Cryptography.CspParameters> objektu.</span><span class="sxs-lookup"><span data-stu-id="40070-109">Pass the appropriate flags to the <xref:System.Security.Cryptography.CspParameters.Flags%2A> property of the newly created <xref:System.Security.Cryptography.CspParameters> object.</span></span>  <span data-ttu-id="40070-110">Například předat <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> příznak.</span><span class="sxs-lookup"><span data-stu-id="40070-110">For example, pass the <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> flag.</span></span>  
  
3.  <span data-ttu-id="40070-111">Vytvořit novou instanci třídy <xref:System.Security.Cryptography.AsymmetricAlgorithm> – třída (například <xref:System.Security.Cryptography.RSACryptoServiceProvider> třída), předejte <xref:System.Security.Cryptography.CspParameters> objekt konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="40070-111">Create a new instance of an <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (for example, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class), passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
4.  <span data-ttu-id="40070-112">Podepište data pomocí jedné z `Sign` metody a ověřte vaše data pomocí jedné z `Verify` metody.</span><span class="sxs-lookup"><span data-stu-id="40070-112">Sign your data using one of the `Sign` methods and verify your data using one of the `Verify` methods.</span></span>  
  
### <a name="to-generate-a-random-number-using-a-hardware-random-number-generator"></a><span data-ttu-id="40070-113">Generovat náhodné číslo pomocí generátoru náhodných čísel hardwaru</span><span class="sxs-lookup"><span data-stu-id="40070-113">To generate a random number using a hardware random number generator</span></span>  
  
1.  <span data-ttu-id="40070-114">Vytvořit novou instanci třídy <xref:System.Security.Cryptography.CspParameters> třídy a předejte typ integer poskytovatele a název zprostředkovatele pro konstruktor.</span><span class="sxs-lookup"><span data-stu-id="40070-114">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2.  <span data-ttu-id="40070-115">Vytvořit novou instanci třídy <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, předejte <xref:System.Security.Cryptography.CspParameters> objekt konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="40070-115">Create a new instance of the <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
3.  <span data-ttu-id="40070-116">Vytvoření náhodná hodnota pomocí <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> nebo <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="40070-116">Create a random value using the <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> or <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40070-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="40070-117">Example</span></span>  
 <span data-ttu-id="40070-118">Následující příklad kódu ukazuje, jak podepsat data pomocí čipové karty.</span><span class="sxs-lookup"><span data-stu-id="40070-118">The following code example demonstrates how to sign data using a smart card.</span></span>  <span data-ttu-id="40070-119">Příklad kódu vytvoří <xref:System.Security.Cryptography.CspParameters> objekt, který zpřístupňuje čipových karet a poté inicializuje <xref:System.Security.Cryptography.RSACryptoServiceProvider> pomocí CSP.</span><span class="sxs-lookup"><span data-stu-id="40070-119">The code example creates a <xref:System.Security.Cryptography.CspParameters> object that exposes a smart card, and then initializes an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object using the CSP.</span></span>  <span data-ttu-id="40070-120">Příklad kódu a podepíše a ověří některá data.</span><span class="sxs-lookup"><span data-stu-id="40070-120">The code example then signs and verifies some data.</span></span>  
  
 [!code-cpp[Cryptography.SmartCardCSP#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CPP/Cryptography.SmartCardCSP.cpp#1)]
 [!code-csharp[Cryptography.SmartCardCSP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CS/example.cs#1)]
 [!code-vb[Cryptography.SmartCardCSP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Cryptography.SmartCardCSP/VB/example.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="40070-121">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="40070-121">Compiling the Code</span></span>  
  
-   <span data-ttu-id="40070-122">Zahrnout <xref:System> a <xref:System.Security.Cryptography> obory názvů.</span><span class="sxs-lookup"><span data-stu-id="40070-122">Include the <xref:System> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
-   <span data-ttu-id="40070-123">Musíte mít čtečka čipových karet a ovladače, které jsou v počítači nainstalována.</span><span class="sxs-lookup"><span data-stu-id="40070-123">You must have a smart card reader and drivers installed on your computer.</span></span>  
  
-   <span data-ttu-id="40070-124">Je třeba inicializovat <xref:System.Security.Cryptography.CspParameters> pomocí informace specifické pro vaši čtečku.</span><span class="sxs-lookup"><span data-stu-id="40070-124">You must initialize the <xref:System.Security.Cryptography.CspParameters> object using information specific to your card reader.</span></span>  <span data-ttu-id="40070-125">Další informace najdete v dokumentaci vaši čtečku.</span><span class="sxs-lookup"><span data-stu-id="40070-125">For more information, see the documentation of your card reader.</span></span>
