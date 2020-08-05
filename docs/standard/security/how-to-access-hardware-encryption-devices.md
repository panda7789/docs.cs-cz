---
title: 'Postupy: Přístup k hardwarovým šifrovacím zařízením'
ms.date: 07/14/2020
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
ms.openlocfilehash: 7cd3aab80a8388c1d4ce08e4ae94aae84cfff239
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557135"
---
# <a name="how-to-access-hardware-encryption-devices"></a><span data-ttu-id="cca36-102">Postupy: Přístup k hardwarovým šifrovacím zařízením</span><span class="sxs-lookup"><span data-stu-id="cca36-102">How to: Access Hardware Encryption Devices</span></span>

> [!NOTE]
> <span data-ttu-id="cca36-103">Tento článek se týká systému Windows.</span><span class="sxs-lookup"><span data-stu-id="cca36-103">This article applies to Windows.</span></span>

<span data-ttu-id="cca36-104"><xref:System.Security.Cryptography.CspParameters>Pro přístup k hardwarovým šifrovacím zařízením můžete použít třídu.</span><span class="sxs-lookup"><span data-stu-id="cca36-104">You can use the <xref:System.Security.Cryptography.CspParameters> class to access hardware encryption devices.</span></span> <span data-ttu-id="cca36-105">Tuto třídu můžete například použít k integraci aplikace s čipovou kartou, generátor náhodných čísel hardwaru nebo implementaci hardwaru konkrétního šifrovacího algoritmu.</span><span class="sxs-lookup"><span data-stu-id="cca36-105">For example, you can use this class to integrate your application with a smart card, a hardware random number generator, or a hardware implementation of a particular cryptographic algorithm.</span></span>  

<span data-ttu-id="cca36-106"><xref:System.Security.Cryptography.CspParameters>Třída vytvoří zprostředkovatele kryptografických služeb (CSP), který přistupuje k správně nainstalovanému hardwarovému šifrovacímu zařízení.</span><span class="sxs-lookup"><span data-stu-id="cca36-106">The <xref:System.Security.Cryptography.CspParameters> class creates a cryptographic service provider (CSP) that accesses a properly installed hardware encryption device.</span></span>  <span data-ttu-id="cca36-107">Dostupnost zprostředkovatele CSP můžete ověřit kontrolou následujícího klíče registru pomocí Editoru registru (Regedit.exe): HKEY_LOCAL_MACHINE \Software\Microsoft\Cryptography\Defaults\Provider.</span><span class="sxs-lookup"><span data-stu-id="cca36-107">You can verify the availability of a CSP by inspecting the following registry key using the Registry Editor (Regedit.exe):  HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider.</span></span>  
  
### <a name="to-sign-data-using-a-key-card"></a><span data-ttu-id="cca36-108">Podepisování dat pomocí karty klíčů</span><span class="sxs-lookup"><span data-stu-id="cca36-108">To sign data using a key card</span></span>  
  
1. <span data-ttu-id="cca36-109">Vytvořte novou instanci <xref:System.Security.Cryptography.CspParameters> třídy, předejte typ poskytovatele Integer a název poskytovatele do konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="cca36-109">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2. <span data-ttu-id="cca36-110">Předejte příslušné příznaky do <xref:System.Security.Cryptography.CspParameters.Flags%2A> vlastnosti nově vytvořeného <xref:System.Security.Cryptography.CspParameters> objektu.</span><span class="sxs-lookup"><span data-stu-id="cca36-110">Pass the appropriate flags to the <xref:System.Security.Cryptography.CspParameters.Flags%2A> property of the newly created <xref:System.Security.Cryptography.CspParameters> object.</span></span>  <span data-ttu-id="cca36-111">Například předejte <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> příznak.</span><span class="sxs-lookup"><span data-stu-id="cca36-111">For example, pass the <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> flag.</span></span>  
  
3. <span data-ttu-id="cca36-112">Vytvořte novou instanci <xref:System.Security.Cryptography.AsymmetricAlgorithm> třídy (například <xref:System.Security.Cryptography.RSACryptoServiceProvider> třídy) a předejte <xref:System.Security.Cryptography.CspParameters> objekt konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="cca36-112">Create a new instance of an <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (for example, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class), passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
4. <span data-ttu-id="cca36-113">Podepište data pomocí jedné z `Sign` metod a ověřte data pomocí jedné z `Verify` metod.</span><span class="sxs-lookup"><span data-stu-id="cca36-113">Sign your data using one of the `Sign` methods and verify your data using one of the `Verify` methods.</span></span>  
  
### <a name="to-generate-a-random-number-using-a-hardware-random-number-generator"></a><span data-ttu-id="cca36-114">Vygenerování náhodného čísla pomocí generátoru náhodných čísel hardwaru</span><span class="sxs-lookup"><span data-stu-id="cca36-114">To generate a random number using a hardware random number generator</span></span>  
  
1. <span data-ttu-id="cca36-115">Vytvořte novou instanci <xref:System.Security.Cryptography.CspParameters> třídy, předejte typ poskytovatele Integer a název poskytovatele do konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="cca36-115">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2. <span data-ttu-id="cca36-116">Vytvořte novou instanci <xref:System.Security.Cryptography.RNGCryptoServiceProvider> objektu a předejte <xref:System.Security.Cryptography.CspParameters> objekt konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="cca36-116">Create a new instance of the <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
3. <span data-ttu-id="cca36-117">Vytvořte náhodnou hodnotu pomocí <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> metody nebo <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> .</span><span class="sxs-lookup"><span data-stu-id="cca36-117">Create a random value using the <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> or <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cca36-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="cca36-118">Example</span></span>

<span data-ttu-id="cca36-119">Následující příklad kódu ukazuje, jak podepisovat data pomocí čipové karty.</span><span class="sxs-lookup"><span data-stu-id="cca36-119">The following code example demonstrates how to sign data using a smart card.</span></span>  <span data-ttu-id="cca36-120">Příklad kódu vytvoří <xref:System.Security.Cryptography.CspParameters> objekt, který zpřístupňuje čipovou kartu, a poté inicializuje <xref:System.Security.Cryptography.RSACryptoServiceProvider> objekt pomocí CSP.</span><span class="sxs-lookup"><span data-stu-id="cca36-120">The code example creates a <xref:System.Security.Cryptography.CspParameters> object that exposes a smart card, and then initializes an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object using the CSP.</span></span>  <span data-ttu-id="cca36-121">Příklad kódu pak podepisuje a ověřuje data.</span><span class="sxs-lookup"><span data-stu-id="cca36-121">The code example then signs and verifies some data.</span></span>  

<span data-ttu-id="cca36-122">Z důvodu kolizí problémů se SHA1 doporučujeme SHA256 nebo lepší.</span><span class="sxs-lookup"><span data-stu-id="cca36-122">Due to collision problems with SHA1, we recommend SHA256 or better.</span></span>
  
[!code-cpp[Cryptography.SmartCardCSP#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CPP/Cryptography.SmartCardCSP.cpp#1)]
[!code-csharp[Cryptography.SmartCardCSP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CS/example.cs#1)]
[!code-vb[Cryptography.SmartCardCSP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Cryptography.SmartCardCSP/VB/example.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cca36-123">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="cca36-123">Compiling the Code</span></span>  
  
- <span data-ttu-id="cca36-124">Přidejte <xref:System> <xref:System.Security.Cryptography> obory názvů a.</span><span class="sxs-lookup"><span data-stu-id="cca36-124">Include the <xref:System> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
- <span data-ttu-id="cca36-125">Musíte mít nainstalovanou čtečku čipových karet a ovladače nainstalované v počítači.</span><span class="sxs-lookup"><span data-stu-id="cca36-125">You must have a smart card reader and drivers installed on your computer.</span></span>  
  
- <span data-ttu-id="cca36-126">Je nutné inicializovat <xref:System.Security.Cryptography.CspParameters> objekt s použitím informací, které jsou specifické pro vaše čtecí zařízení karet.</span><span class="sxs-lookup"><span data-stu-id="cca36-126">You must initialize the <xref:System.Security.Cryptography.CspParameters> object using information specific to your card reader.</span></span>  <span data-ttu-id="cca36-127">Další informace najdete v dokumentaci ke čtečce karet.</span><span class="sxs-lookup"><span data-stu-id="cca36-127">For more information, see the documentation of your card reader.</span></span>

## <a name="see-also"></a><span data-ttu-id="cca36-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="cca36-128">See also</span></span>

- [<span data-ttu-id="cca36-129">Kryptografický model</span><span class="sxs-lookup"><span data-stu-id="cca36-129">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="cca36-130">Šifrovací služby</span><span class="sxs-lookup"><span data-stu-id="cca36-130">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="cca36-131">Kryptografie pro různé platformy</span><span class="sxs-lookup"><span data-stu-id="cca36-131">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="cca36-132">Ochrana dat ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="cca36-132">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
