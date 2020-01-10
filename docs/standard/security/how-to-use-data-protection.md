---
title: 'Postupy: Použití ochrany dat'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DPAPI
- encryption [.NET Framework], data protection API
- data [.NET Framework], decryption
- ProtectedMemory class, about ProtectedMemory class
- ProtectedData class, about ProtectedData class
- cryptography [.NET Framework], data protection API
- data protection API [.NET Framework]
- decryption
- data [.NET Framework], encryption
ms.assetid: 606698b0-cb1a-42ca-beeb-0bea34205d20
ms.openlocfilehash: 0efd677f11189b28b8efc184c04b30a047ab942b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706029"
---
# <a name="how-to-use-data-protection"></a><span data-ttu-id="fc834-102">Postupy: Použití ochrany dat</span><span class="sxs-lookup"><span data-stu-id="fc834-102">How to: Use Data Protection</span></span>
<span data-ttu-id="fc834-103">.NET Framework poskytuje přístup k rozhraní data Protection API (DPAPI), které umožňuje šifrovat data pomocí informací z aktuálního uživatelského účtu nebo počítače.</span><span class="sxs-lookup"><span data-stu-id="fc834-103">The .NET Framework provides access to the data protection API (DPAPI), which allows you to encrypt data using information from the current user account or computer.</span></span>  <span data-ttu-id="fc834-104">Při použití rozhraní DPAPI je obtížné vyřešit obtížně generovaný a uložený kryptografický klíč.</span><span class="sxs-lookup"><span data-stu-id="fc834-104">When you use the DPAPI, you alleviate the difficult problem of explicitly generating and storing a cryptographic key.</span></span>  
  
 <span data-ttu-id="fc834-105">Použijte třídu <xref:System.Security.Cryptography.ProtectedMemory> k zašifrování pole bajtů v paměti.</span><span class="sxs-lookup"><span data-stu-id="fc834-105">Use the <xref:System.Security.Cryptography.ProtectedMemory> class to encrypt an array of in-memory bytes.</span></span>  <span data-ttu-id="fc834-106">Tato funkce je k dispozici v systému Microsoft Windows XP a novějších operačních systémech.</span><span class="sxs-lookup"><span data-stu-id="fc834-106">This functionality is available in Microsoft Windows XP and later operating systems.</span></span>  <span data-ttu-id="fc834-107">Můžete určit, že paměť zašifrovaná pomocí aktuálního procesu může být dešifrována pouze aktuálním procesem, všemi procesy nebo ze stejného kontextu uživatele.</span><span class="sxs-lookup"><span data-stu-id="fc834-107">You can specify that memory encrypted by the current process can be decrypted by the current process only, by all processes, or from the same user context.</span></span>  <span data-ttu-id="fc834-108">Podrobný popis možností <xref:System.Security.Cryptography.ProtectedMemory> naleznete v <xref:System.Security.Cryptography.MemoryProtectionScope> výčtu.</span><span class="sxs-lookup"><span data-stu-id="fc834-108">See the <xref:System.Security.Cryptography.MemoryProtectionScope> enumeration for a detailed description of <xref:System.Security.Cryptography.ProtectedMemory> options.</span></span>  
  
 <span data-ttu-id="fc834-109">Použijte třídu <xref:System.Security.Cryptography.ProtectedData> k zašifrování kopie pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="fc834-109">Use the <xref:System.Security.Cryptography.ProtectedData> class to encrypt a copy of an array of bytes.</span></span> <span data-ttu-id="fc834-110">Tato funkce je k dispozici v systému Microsoft Windows 2000 a novějších operačních systémech.</span><span class="sxs-lookup"><span data-stu-id="fc834-110">This functionality is available in Microsoft Windows 2000 and later operating systems.</span></span>  <span data-ttu-id="fc834-111">Můžete určit, že data zašifrovaná pomocí aktuálního uživatelského účtu je možné dešifrovat jenom stejným uživatelským účtem, nebo můžete zadat, aby se data zašifrovaná aktuálním uživatelským účtem mohla dešifrovat jakýmkoli účtem v počítači.</span><span class="sxs-lookup"><span data-stu-id="fc834-111">You can specify that data encrypted by the current user account can be decrypted only by the same user account, or you can specify that data encrypted by the current user account can be decrypted by any account on the computer.</span></span>  <span data-ttu-id="fc834-112">Podrobný popis možností <xref:System.Security.Cryptography.ProtectedData> naleznete v <xref:System.Security.Cryptography.DataProtectionScope> výčtu.</span><span class="sxs-lookup"><span data-stu-id="fc834-112">See the <xref:System.Security.Cryptography.DataProtectionScope> enumeration for a detailed description of <xref:System.Security.Cryptography.ProtectedData> options.</span></span>  
  
### <a name="to-encrypt-in-memory-data-using-data-protection"></a><span data-ttu-id="fc834-113">Šifrování dat v paměti pomocí ochrany dat</span><span class="sxs-lookup"><span data-stu-id="fc834-113">To encrypt in-memory data using data protection</span></span>  
  
1. <span data-ttu-id="fc834-114">Při předávání pole bajtů k zašifrování, entropie a rozsahu ochrany paměti volejte metodu static <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A>.</span><span class="sxs-lookup"><span data-stu-id="fc834-114">Call the static <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> method while passing an array of bytes to encrypt, the entropy, and the memory protection scope.</span></span>  
  
### <a name="to-decrypt-in-memory-data-using-data-protection"></a><span data-ttu-id="fc834-115">Dešifrování dat v paměti pomocí ochrany dat</span><span class="sxs-lookup"><span data-stu-id="fc834-115">To decrypt in-memory data using data protection</span></span>  
  
1. <span data-ttu-id="fc834-116">Při předávání pole bajtů k dešifrování a rozsahu ochrany paměti volejte metodu static <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A>.</span><span class="sxs-lookup"><span data-stu-id="fc834-116">Call the static <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> method while passing an array of bytes to decrypt and the memory protection scope.</span></span>  
  
### <a name="to-encrypt-data-to-a-file-or-stream-using-data-protection"></a><span data-ttu-id="fc834-117">Šifrování dat do souboru nebo datového proudu pomocí ochrany dat</span><span class="sxs-lookup"><span data-stu-id="fc834-117">To encrypt data to a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="fc834-118">Vytvořte náhodnou entropii.</span><span class="sxs-lookup"><span data-stu-id="fc834-118">Create random entropy.</span></span>  
  
2. <span data-ttu-id="fc834-119">Při předávání pole bajtů k zašifrování, entropie a rozsahu ochrany dat volejte statickou <xref:System.Security.Cryptography.ProtectedData.Protect%2A>ovou metodu.</span><span class="sxs-lookup"><span data-stu-id="fc834-119">Call the static <xref:System.Security.Cryptography.ProtectedData.Protect%2A> method while passing an array of bytes to encrypt, the entropy, and the data protection scope.</span></span>  
  
3. <span data-ttu-id="fc834-120">Zapište zašifrovaná data do souboru nebo datového proudu.</span><span class="sxs-lookup"><span data-stu-id="fc834-120">Write the encrypted data to a file or stream.</span></span>  
  
### <a name="to-decrypt-data-from-a-file-or-stream-using-data-protection"></a><span data-ttu-id="fc834-121">Dešifrování dat ze souboru nebo datového proudu pomocí ochrany dat</span><span class="sxs-lookup"><span data-stu-id="fc834-121">To decrypt data from a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="fc834-122">Přečtěte si šifrovaná data ze souboru nebo datového proudu.</span><span class="sxs-lookup"><span data-stu-id="fc834-122">Read the encrypted data from a file or stream.</span></span>  
  
2. <span data-ttu-id="fc834-123">Při předávání pole bajtů k dešifrování a rozsahu ochrany dat volejte statickou <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A>ovou metodu.</span><span class="sxs-lookup"><span data-stu-id="fc834-123">Call the static <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> method while passing an array of bytes to decrypt and the data protection scope.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc834-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="fc834-124">Example</span></span>  
 <span data-ttu-id="fc834-125">Následující příklad kódu ukazuje dvě formy šifrování a dešifrování.</span><span class="sxs-lookup"><span data-stu-id="fc834-125">The following code example demonstrates two forms of encryption and decryption.</span></span>  <span data-ttu-id="fc834-126">Nejprve příklad kódu šifruje a pak dešifruje pole bajtů v paměti.</span><span class="sxs-lookup"><span data-stu-id="fc834-126">First, the code example encrypts and then decrypts an in-memory array of bytes.</span></span>  <span data-ttu-id="fc834-127">V dalším příkladu kód zašifruje kopii pole bajtů, uloží ho do souboru, načte data zpátky ze souboru a pak data dešifruje.</span><span class="sxs-lookup"><span data-stu-id="fc834-127">Next, the code example encrypts a copy of a byte array, saves it to a file, loads the data back from the file, and then decrypts the data.</span></span>  <span data-ttu-id="fc834-128">V příkladu se zobrazí původní data, šifrovaná data a dešifrovaná data.</span><span class="sxs-lookup"><span data-stu-id="fc834-128">The example displays the original data, the encrypted data, and the decrypted data.</span></span>  
  
 [!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
 [!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fc834-129">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="fc834-129">Compiling the Code</span></span>  
  
- <span data-ttu-id="fc834-130">Zahrňte odkaz na `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="fc834-130">Include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="fc834-131">Zadejte obor názvů <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography>a <xref:System.Text>.</span><span class="sxs-lookup"><span data-stu-id="fc834-131">Include the <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography>, and <xref:System.Text> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc834-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fc834-132">See also</span></span>

- <xref:System.Security.Cryptography.ProtectedMemory>
- <xref:System.Security.Cryptography.ProtectedData>
