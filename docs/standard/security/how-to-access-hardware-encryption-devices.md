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
ms.openlocfilehash: d6ee22fd9fb0c11e22ac01ff83b3269e37e37763
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706172"
---
# <a name="how-to-access-hardware-encryption-devices"></a><span data-ttu-id="c8402-102">Postupy: Přístup k hardwarovým šifrovacím zařízením</span><span class="sxs-lookup"><span data-stu-id="c8402-102">How to: Access Hardware Encryption Devices</span></span>
<span data-ttu-id="c8402-103">Pro přístup k hardwarovým šifrovacím zařízením můžete použít třídu <xref:System.Security.Cryptography.CspParameters>.</span><span class="sxs-lookup"><span data-stu-id="c8402-103">You can use the <xref:System.Security.Cryptography.CspParameters> class to access hardware encryption devices.</span></span> <span data-ttu-id="c8402-104">Tuto třídu můžete například použít k integraci aplikace s čipovou kartou, generátor náhodných čísel hardwaru nebo implementaci hardwaru konkrétního šifrovacího algoritmu.</span><span class="sxs-lookup"><span data-stu-id="c8402-104">For example, you can use this class to integrate your application with a smart card, a hardware random number generator, or a hardware implementation of a particular cryptographic algorithm.</span></span>  
  
 <span data-ttu-id="c8402-105">Třída <xref:System.Security.Cryptography.CspParameters> vytvoří zprostředkovatele kryptografických služeb (CSP), který přistupuje k správně nainstalovanému hardwarovému šifrovacímu zařízení.</span><span class="sxs-lookup"><span data-stu-id="c8402-105">The <xref:System.Security.Cryptography.CspParameters> class creates a cryptographic service provider (CSP) that accesses a properly installed hardware encryption device.</span></span>  <span data-ttu-id="c8402-106">Dostupnost zprostředkovatele CSP můžete ověřit kontrolou následujícího klíče registru pomocí Editoru registru (Regedit. exe): HKEY_LOCAL_MACHINE \Software\Microsoft\Cryptography\Defaults\Provider.</span><span class="sxs-lookup"><span data-stu-id="c8402-106">You can verify the availability of a CSP by inspecting the following registry key using the Registry Editor (Regedit.exe):  HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider.</span></span>  
  
### <a name="to-sign-data-using-a-key-card"></a><span data-ttu-id="c8402-107">Podepisování dat pomocí karty klíčů</span><span class="sxs-lookup"><span data-stu-id="c8402-107">To sign data using a key card</span></span>  
  
1. <span data-ttu-id="c8402-108">Vytvořte novou instanci třídy <xref:System.Security.Cryptography.CspParameters>, předejte typ poskytovatele Integer a název poskytovatele do konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="c8402-108">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2. <span data-ttu-id="c8402-109">Předejte příslušné příznaky do vlastnosti <xref:System.Security.Cryptography.CspParameters.Flags%2A> nově vytvořeného objektu <xref:System.Security.Cryptography.CspParameters>.</span><span class="sxs-lookup"><span data-stu-id="c8402-109">Pass the appropriate flags to the <xref:System.Security.Cryptography.CspParameters.Flags%2A> property of the newly created <xref:System.Security.Cryptography.CspParameters> object.</span></span>  <span data-ttu-id="c8402-110">Například předejte příznak <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer>.</span><span class="sxs-lookup"><span data-stu-id="c8402-110">For example, pass the <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> flag.</span></span>  
  
3. <span data-ttu-id="c8402-111">Vytvořte novou instanci třídy <xref:System.Security.Cryptography.AsymmetricAlgorithm> (například třídu <xref:System.Security.Cryptography.RSACryptoServiceProvider>) a předejte objekt <xref:System.Security.Cryptography.CspParameters> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="c8402-111">Create a new instance of an <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (for example, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class), passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
4. <span data-ttu-id="c8402-112">Pomocí jedné z metod `Sign` podepište data a pomocí jedné z metod `Verify` Ověřte data.</span><span class="sxs-lookup"><span data-stu-id="c8402-112">Sign your data using one of the `Sign` methods and verify your data using one of the `Verify` methods.</span></span>  
  
### <a name="to-generate-a-random-number-using-a-hardware-random-number-generator"></a><span data-ttu-id="c8402-113">Vygenerování náhodného čísla pomocí generátoru náhodných čísel hardwaru</span><span class="sxs-lookup"><span data-stu-id="c8402-113">To generate a random number using a hardware random number generator</span></span>  
  
1. <span data-ttu-id="c8402-114">Vytvořte novou instanci třídy <xref:System.Security.Cryptography.CspParameters>, předejte typ poskytovatele Integer a název poskytovatele do konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="c8402-114">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2. <span data-ttu-id="c8402-115">Vytvořte novou instanci <xref:System.Security.Cryptography.RNGCryptoServiceProvider>a předejte objekt <xref:System.Security.Cryptography.CspParameters> do konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="c8402-115">Create a new instance of the <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
3. <span data-ttu-id="c8402-116">Pomocí metody <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> nebo <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> Vytvořte náhodnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c8402-116">Create a random value using the <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> or <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8402-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="c8402-117">Example</span></span>  
 <span data-ttu-id="c8402-118">Následující příklad kódu ukazuje, jak podepisovat data pomocí čipové karty.</span><span class="sxs-lookup"><span data-stu-id="c8402-118">The following code example demonstrates how to sign data using a smart card.</span></span>  <span data-ttu-id="c8402-119">Příklad kódu vytvoří objekt <xref:System.Security.Cryptography.CspParameters>, který zpřístupňuje čipovou kartu, a poté inicializuje <xref:System.Security.Cryptography.RSACryptoServiceProvider> objekt pomocí zprostředkovatele CSP.</span><span class="sxs-lookup"><span data-stu-id="c8402-119">The code example creates a <xref:System.Security.Cryptography.CspParameters> object that exposes a smart card, and then initializes an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object using the CSP.</span></span>  <span data-ttu-id="c8402-120">Příklad kódu pak podepisuje a ověřuje data.</span><span class="sxs-lookup"><span data-stu-id="c8402-120">The code example then signs and verifies some data.</span></span>  
  
 [!code-cpp[Cryptography.SmartCardCSP#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CPP/Cryptography.SmartCardCSP.cpp#1)]
 [!code-csharp[Cryptography.SmartCardCSP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CS/example.cs#1)]
 [!code-vb[Cryptography.SmartCardCSP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Cryptography.SmartCardCSP/VB/example.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c8402-121">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="c8402-121">Compiling the Code</span></span>  
  
- <span data-ttu-id="c8402-122">Zahrňte <xref:System> a <xref:System.Security.Cryptography> obory názvů.</span><span class="sxs-lookup"><span data-stu-id="c8402-122">Include the <xref:System> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
- <span data-ttu-id="c8402-123">Musíte mít nainstalovanou čtečku čipových karet a ovladače nainstalované v počítači.</span><span class="sxs-lookup"><span data-stu-id="c8402-123">You must have a smart card reader and drivers installed on your computer.</span></span>  
  
- <span data-ttu-id="c8402-124">Objekt <xref:System.Security.Cryptography.CspParameters> musíte inicializovat pomocí informací, které jsou specifické pro vaše čtecí zařízení karet.</span><span class="sxs-lookup"><span data-stu-id="c8402-124">You must initialize the <xref:System.Security.Cryptography.CspParameters> object using information specific to your card reader.</span></span>  <span data-ttu-id="c8402-125">Další informace najdete v dokumentaci ke čtečce karet.</span><span class="sxs-lookup"><span data-stu-id="c8402-125">For more information, see the documentation of your card reader.</span></span>
