---
title: "Postupy: Použití ochrany dat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 99608c991d79d204085f190c00e347aae15eb2cb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-data-protection"></a><span data-ttu-id="4ba0f-102">Postupy: Použití ochrany dat</span><span class="sxs-lookup"><span data-stu-id="4ba0f-102">How to: Use Data Protection</span></span>
<span data-ttu-id="4ba0f-103">Rozhraní .NET Framework poskytuje přístup k data protection API (DPAPI), které umožňuje šifrování dat pomocí informací z aktuální uživatelský účet nebo počítači.</span><span class="sxs-lookup"><span data-stu-id="4ba0f-103">The .NET Framework provides access to the data protection API (DPAPI), which allows you to encrypt data using information from the current user account or computer.</span></span>  <span data-ttu-id="4ba0f-104">Pokud použijete rozhraní DPAPI, tím se obtížně problém explicitně generování a ukládání kryptografického klíče.</span><span class="sxs-lookup"><span data-stu-id="4ba0f-104">When you use the DPAPI, you alleviate the difficult problem of explicitly generating and storing a cryptographic key.</span></span>  
  
 <span data-ttu-id="4ba0f-105">Použití <xref:System.Security.Cryptography.ProtectedMemory> třída k zašifrování pole bajtů v paměti.</span><span class="sxs-lookup"><span data-stu-id="4ba0f-105">Use the <xref:System.Security.Cryptography.ProtectedMemory> class to encrypt an array of in-memory bytes.</span></span>  <span data-ttu-id="4ba0f-106">Tato funkce je k dispozici v systému Microsoft Windows XP a novějších operačních systémech.</span><span class="sxs-lookup"><span data-stu-id="4ba0f-106">This functionality is available in Microsoft Windows XP and later operating systems.</span></span>  <span data-ttu-id="4ba0f-107">Můžete určit, že paměť šifrována pomocí aktuálního procesu mohou ho dešifrovat aktuální proces pouze všechny procesy, nebo ze stejného uživatelského kontextu.</span><span class="sxs-lookup"><span data-stu-id="4ba0f-107">You can specify that memory encrypted by the current process can be decrypted by the current process only, by all processes, or from the same user context.</span></span>  <span data-ttu-id="4ba0f-108">Najdete v článku <xref:System.Security.Cryptography.MemoryProtectionScope> výčet podrobný popis <xref:System.Security.Cryptography.ProtectedMemory> možnosti.</span><span class="sxs-lookup"><span data-stu-id="4ba0f-108">See the <xref:System.Security.Cryptography.MemoryProtectionScope> enumeration for a detailed description of <xref:System.Security.Cryptography.ProtectedMemory> options.</span></span>  
  
 <span data-ttu-id="4ba0f-109">Použití <xref:System.Security.Cryptography.ProtectedData> třída k zašifrování kopie pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="4ba0f-109">Use the <xref:System.Security.Cryptography.ProtectedData> class to encrypt a copy of an array of bytes.</span></span> <span data-ttu-id="4ba0f-110">Tato funkce je k dispozici v systému Microsoft Windows 2000 a novějších operačních systémech.</span><span class="sxs-lookup"><span data-stu-id="4ba0f-110">This functionality is available in Microsoft Windows 2000 and later operating systems.</span></span>  <span data-ttu-id="4ba0f-111">Můžete zadat data zašifrovaná pomocí aktuální uživatelský účet je pak možné dešifrovat jenom pomocí stejného uživatelského účtu, nebo můžete zadat, že všechny účet v počítači, mohou ho dešifrovat data zašifrovaná pomocí aktuálního uživatelského účtu.</span><span class="sxs-lookup"><span data-stu-id="4ba0f-111">You can specify that data encrypted by the current user account can be decrypted only by the same user account, or you can specify that data encrypted by the current user account can be decrypted by any account on the computer.</span></span>  <span data-ttu-id="4ba0f-112">Najdete v článku <xref:System.Security.Cryptography.DataProtectionScope> výčet podrobný popis <xref:System.Security.Cryptography.ProtectedData> možnosti.</span><span class="sxs-lookup"><span data-stu-id="4ba0f-112">See the <xref:System.Security.Cryptography.DataProtectionScope> enumeration for a detailed description of <xref:System.Security.Cryptography.ProtectedData> options.</span></span>  
  
### <a name="to-encrypt-in-memory-data-using-data-protection"></a><span data-ttu-id="4ba0f-113">K šifrování dat v paměti pomocí funkce Ochrana dat</span><span class="sxs-lookup"><span data-stu-id="4ba0f-113">To encrypt in-memory data using data protection</span></span>  
  
1.  <span data-ttu-id="4ba0f-114">Zavolejte statickou <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> metoda při předávání pole bajtů k šifrování, entropie a rozsahu ochrany paměti.</span><span class="sxs-lookup"><span data-stu-id="4ba0f-114">Call the static <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> method while passing an array of bytes to encrypt, the entropy, and the memory protection scope.</span></span>  
  
### <a name="to-decrypt-in-memory-data-using-data-protection"></a><span data-ttu-id="4ba0f-115">K dešifrování dat v paměti pomocí funkce Ochrana dat</span><span class="sxs-lookup"><span data-stu-id="4ba0f-115">To decrypt in-memory data using data protection</span></span>  
  
1.  <span data-ttu-id="4ba0f-116">Zavolejte statickou <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> metoda při předávání pole bajtů k dešifrování a rozsahu ochrany paměti.</span><span class="sxs-lookup"><span data-stu-id="4ba0f-116">Call the static <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> method while passing an array of bytes to decrypt and the memory protection scope.</span></span>  
  
### <a name="to-encrypt-data-to-a-file-or-stream-using-data-protection"></a><span data-ttu-id="4ba0f-117">Šifrování dat do souboru nebo datového proudu s použitím ochrany dat</span><span class="sxs-lookup"><span data-stu-id="4ba0f-117">To encrypt data to a file or stream using data protection</span></span>  
  
1.  <span data-ttu-id="4ba0f-118">Vytvořte náhodné šifrování.</span><span class="sxs-lookup"><span data-stu-id="4ba0f-118">Create random entropy.</span></span>  
  
2.  <span data-ttu-id="4ba0f-119">Zavolejte statickou <xref:System.Security.Cryptography.ProtectedData.Protect%2A> metoda při předávání pole bajtů k šifrování, entropie a rozsahu ochrany dat.</span><span class="sxs-lookup"><span data-stu-id="4ba0f-119">Call the static <xref:System.Security.Cryptography.ProtectedData.Protect%2A> method while passing an array of bytes to encrypt, the entropy, and the data protection scope.</span></span>  
  
3.  <span data-ttu-id="4ba0f-120">Šifrovaná data zapište do souboru nebo datový proud.</span><span class="sxs-lookup"><span data-stu-id="4ba0f-120">Write the encrypted data to a file or stream.</span></span>  
  
### <a name="to-decrypt-data-from-a-file-or-stream-using-data-protection"></a><span data-ttu-id="4ba0f-121">Dešifrování dat ze souboru nebo datového proudu s použitím ochrany dat</span><span class="sxs-lookup"><span data-stu-id="4ba0f-121">To decrypt data from a file or stream using data protection</span></span>  
  
1.  <span data-ttu-id="4ba0f-122">Čtení ze souboru nebo datový proud šifrovaná data.</span><span class="sxs-lookup"><span data-stu-id="4ba0f-122">Read the encrypted data from a file or stream.</span></span>  
  
2.  <span data-ttu-id="4ba0f-123">Zavolejte statickou <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> metoda při předávání pole bajtů k dešifrování a rozsahu ochrany dat.</span><span class="sxs-lookup"><span data-stu-id="4ba0f-123">Call the static <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> method while passing an array of bytes to decrypt and the data protection scope.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ba0f-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="4ba0f-124">Example</span></span>  
 <span data-ttu-id="4ba0f-125">Následující příklad kódu ukazuje dvě formy šifrování a dešifrování.</span><span class="sxs-lookup"><span data-stu-id="4ba0f-125">The following code example demonstrates two forms of encryption and decryption.</span></span>  <span data-ttu-id="4ba0f-126">Příklad kódu nejprve šifruje a poté dešifruje pole bajtů v paměti.</span><span class="sxs-lookup"><span data-stu-id="4ba0f-126">First, the code example encrypts and then decrypts an in-memory array of bytes.</span></span>  <span data-ttu-id="4ba0f-127">V dalším kroku příkladu kódu šifruje kopii bajtové pole, uloží do souboru, načte data zpět ze souboru a poté dešifruje data.</span><span class="sxs-lookup"><span data-stu-id="4ba0f-127">Next, the code example encrypts a copy of a byte array, saves it to a file, loads the data back from the file, and then decrypts the data.</span></span>  <span data-ttu-id="4ba0f-128">Příklad zobrazí původní data, šifrovaná data a dešifrovaná data.</span><span class="sxs-lookup"><span data-stu-id="4ba0f-128">The example displays the original data, the encrypted data, and the decrypted data.</span></span>  
  
 [!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
 [!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4ba0f-129">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="4ba0f-129">Compiling the Code</span></span>  
  
-   <span data-ttu-id="4ba0f-130">Zahrnout odkaz na `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="4ba0f-130">Include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="4ba0f-131">Zahrnout <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography>, a <xref:System.Text> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4ba0f-131">Include the <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography>, and <xref:System.Text> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ba0f-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="4ba0f-132">See Also</span></span>  
 <xref:System.Security.Cryptography.ProtectedMemory>  
 <xref:System.Security.Cryptography.ProtectedData>
