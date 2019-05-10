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
ms.openlocfilehash: 9c16c994e3976fb3ee569799461db1d1789a6186
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64654384"
---
# <a name="how-to-access-hardware-encryption-devices"></a><span data-ttu-id="da7ce-102">Postupy: Přístup k hardwarovým šifrovacím zařízením</span><span class="sxs-lookup"><span data-stu-id="da7ce-102">How to: Access Hardware Encryption Devices</span></span>
<span data-ttu-id="da7ce-103">Můžete použít <xref:System.Security.Cryptography.CspParameters> třídy pro přístup k hardwarovým šifrovacím zařízením.</span><span class="sxs-lookup"><span data-stu-id="da7ce-103">You can use the <xref:System.Security.Cryptography.CspParameters> class to access hardware encryption devices.</span></span> <span data-ttu-id="da7ce-104">Tato třída můžete například použít k integraci vaší aplikace pomocí čipové karty, generátor náhodných čísel hardware nebo hardware provádění konkrétní kryptografický algoritmus.</span><span class="sxs-lookup"><span data-stu-id="da7ce-104">For example, you can use this class to integrate your application with a smart card, a hardware random number generator, or a hardware implementation of a particular cryptographic algorithm.</span></span>  
  
 <span data-ttu-id="da7ce-105"><xref:System.Security.Cryptography.CspParameters> Třída vytvoří zprostředkovatele kryptografických služeb (CSP), který přistupuje k správně nainstalována hardwarové šifrování zařízení.</span><span class="sxs-lookup"><span data-stu-id="da7ce-105">The <xref:System.Security.Cryptography.CspParameters> class creates a cryptographic service provider (CSP) that accesses a properly installed hardware encryption device.</span></span>  <span data-ttu-id="da7ce-106">Dostupnost služby Zprostředkovatel kryptografických služeb můžete ověřit kontrolou následující klíč registru, pomocí Editoru registru (Regedit.exe):  HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider.</span><span class="sxs-lookup"><span data-stu-id="da7ce-106">You can verify the availability of a CSP by inspecting the following registry key using the Registry Editor (Regedit.exe):  HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider.</span></span>  
  
### <a name="to-sign-data-using-a-key-card"></a><span data-ttu-id="da7ce-107">Podepsat data pomocí klíčů karty</span><span class="sxs-lookup"><span data-stu-id="da7ce-107">To sign data using a key card</span></span>  
  
1. <span data-ttu-id="da7ce-108">Vytvořit novou instanci třídy <xref:System.Security.Cryptography.CspParameters> třídy, prochází zprostředkovatele typu celé číslo a název poskytovatele pro konstruktor.</span><span class="sxs-lookup"><span data-stu-id="da7ce-108">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2. <span data-ttu-id="da7ce-109">Předat vhodné příznaky <xref:System.Security.Cryptography.CspParameters.Flags%2A> vlastnosti nově vytvořeného <xref:System.Security.Cryptography.CspParameters> objektu.</span><span class="sxs-lookup"><span data-stu-id="da7ce-109">Pass the appropriate flags to the <xref:System.Security.Cryptography.CspParameters.Flags%2A> property of the newly created <xref:System.Security.Cryptography.CspParameters> object.</span></span>  <span data-ttu-id="da7ce-110">Například předání <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> příznak.</span><span class="sxs-lookup"><span data-stu-id="da7ce-110">For example, pass the <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> flag.</span></span>  
  
3. <span data-ttu-id="da7ce-111">Vytvořit novou instanci třídy <xref:System.Security.Cryptography.AsymmetricAlgorithm> třídy (například <xref:System.Security.Cryptography.RSACryptoServiceProvider> třídy), předejte <xref:System.Security.Cryptography.CspParameters> objekt konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="da7ce-111">Create a new instance of an <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (for example, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class), passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
4. <span data-ttu-id="da7ce-112">Podepište data pomocí jedné z `Sign` metody a ověření pomocí jedné z dat `Verify` metody.</span><span class="sxs-lookup"><span data-stu-id="da7ce-112">Sign your data using one of the `Sign` methods and verify your data using one of the `Verify` methods.</span></span>  
  
### <a name="to-generate-a-random-number-using-a-hardware-random-number-generator"></a><span data-ttu-id="da7ce-113">Generovat náhodné číslo pomocí hardwaru generátor náhodných čísel</span><span class="sxs-lookup"><span data-stu-id="da7ce-113">To generate a random number using a hardware random number generator</span></span>  
  
1. <span data-ttu-id="da7ce-114">Vytvořit novou instanci třídy <xref:System.Security.Cryptography.CspParameters> třídy, prochází zprostředkovatele typu celé číslo a název poskytovatele pro konstruktor.</span><span class="sxs-lookup"><span data-stu-id="da7ce-114">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2. <span data-ttu-id="da7ce-115">Vytvořit novou instanci třídy <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, předejte <xref:System.Security.Cryptography.CspParameters> objekt konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="da7ce-115">Create a new instance of the <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
3. <span data-ttu-id="da7ce-116">Vytvořit náhodnou hodnotu pomocí <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> nebo <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="da7ce-116">Create a random value using the <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> or <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da7ce-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="da7ce-117">Example</span></span>  
 <span data-ttu-id="da7ce-118">Následující příklad kódu ukazuje, jak podepsat data pomocí čipové karty.</span><span class="sxs-lookup"><span data-stu-id="da7ce-118">The following code example demonstrates how to sign data using a smart card.</span></span>  <span data-ttu-id="da7ce-119">Příklad kódu vytvoří <xref:System.Security.Cryptography.CspParameters> objekt, který zpřístupňuje čipových karet a poté inicializuje <xref:System.Security.Cryptography.RSACryptoServiceProvider> pomocí CSP.</span><span class="sxs-lookup"><span data-stu-id="da7ce-119">The code example creates a <xref:System.Security.Cryptography.CspParameters> object that exposes a smart card, and then initializes an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object using the CSP.</span></span>  <span data-ttu-id="da7ce-120">Příklad kódu a podepíše a ověří nějaká data.</span><span class="sxs-lookup"><span data-stu-id="da7ce-120">The code example then signs and verifies some data.</span></span>  
  
 [!code-cpp[Cryptography.SmartCardCSP#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CPP/Cryptography.SmartCardCSP.cpp#1)]
 [!code-csharp[Cryptography.SmartCardCSP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CS/example.cs#1)]
 [!code-vb[Cryptography.SmartCardCSP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Cryptography.SmartCardCSP/VB/example.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="da7ce-121">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="da7ce-121">Compiling the Code</span></span>  
  
- <span data-ttu-id="da7ce-122">Zahrnout <xref:System> a <xref:System.Security.Cryptography> obory názvů.</span><span class="sxs-lookup"><span data-stu-id="da7ce-122">Include the <xref:System> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
- <span data-ttu-id="da7ce-123">Musíte mít čtečku čipových karet a ovladače v počítači nainstalována.</span><span class="sxs-lookup"><span data-stu-id="da7ce-123">You must have a smart card reader and drivers installed on your computer.</span></span>  
  
- <span data-ttu-id="da7ce-124">Je třeba inicializovat <xref:System.Security.Cryptography.CspParameters> pomocí informací specifických pro vaši čtečku.</span><span class="sxs-lookup"><span data-stu-id="da7ce-124">You must initialize the <xref:System.Security.Cryptography.CspParameters> object using information specific to your card reader.</span></span>  <span data-ttu-id="da7ce-125">Další informace naleznete v dokumentaci vaši čtečku.</span><span class="sxs-lookup"><span data-stu-id="da7ce-125">For more information, see the documentation of your card reader.</span></span>
