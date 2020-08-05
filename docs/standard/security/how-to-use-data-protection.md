---
title: 'Postupy: Použití ochrany dat'
description: Naučte se používat ochranu dat pomocí přístupu k rozhraní data Protection API (DPAPI) v rozhraní .NET.
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DPAPI
- encryption [.NET], data protection API
- data [.NET], decryption
- ProtectedMemory class, about ProtectedMemory class
- ProtectedData class, about ProtectedData class
- cryptography [.NET], data protection API
- data protection API [.NET]
- decryption
- data [.NET], encryption
ms.assetid: 606698b0-cb1a-42ca-beeb-0bea34205d20
ms.openlocfilehash: 263a07ddf357734e819fffdd41cdff60657adf15
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557057"
---
# <a name="how-to-use-data-protection"></a><span data-ttu-id="bbdcf-103">Postupy: Použití ochrany dat</span><span class="sxs-lookup"><span data-stu-id="bbdcf-103">How to: Use Data Protection</span></span>

> [!NOTE]
> <span data-ttu-id="bbdcf-104">Tento článek se týká systému Windows.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-104">This article applies to Windows.</span></span>
>
> <span data-ttu-id="bbdcf-105">Informace o ASP.NET Core najdete v tématu [ASP.NET Core Data Protection](/aspnet/core/security/data-protection/introduction).</span><span class="sxs-lookup"><span data-stu-id="bbdcf-105">For information about ASP.NET Core, see [ASP.NET Core Data Protection](/aspnet/core/security/data-protection/introduction).</span></span>

<span data-ttu-id="bbdcf-106">Rozhraní .NET poskytuje přístup k rozhraní data Protection API (DPAPI), které umožňuje šifrovat data pomocí informací z aktuálního uživatelského účtu nebo počítače.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-106">.NET provides access to the data protection API (DPAPI), which allows you to encrypt data using information from the current user account or computer.</span></span>  <span data-ttu-id="bbdcf-107">Při použití rozhraní DPAPI je obtížné vyřešit obtížně generovaný a uložený kryptografický klíč.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-107">When you use the DPAPI, you alleviate the difficult problem of explicitly generating and storing a cryptographic key.</span></span>  
  
<span data-ttu-id="bbdcf-108">Použijte <xref:System.Security.Cryptography.ProtectedData> třídu k zašifrování kopie pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-108">Use the <xref:System.Security.Cryptography.ProtectedData> class to encrypt a copy of an array of bytes.</span></span> <span data-ttu-id="bbdcf-109">Tato funkce je k dispozici v .NET Framework, .NET Core a .NET 5.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-109">This functionality is available in .NET Framework, .NET Core, and .NET 5.</span></span>  <span data-ttu-id="bbdcf-110">Můžete určit, že data zašifrovaná pomocí aktuálního uživatelského účtu je možné dešifrovat jenom stejným uživatelským účtem, nebo můžete zadat, aby se data zašifrovaná aktuálním uživatelským účtem mohla dešifrovat jakýmkoli účtem v počítači.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-110">You can specify that data encrypted by the current user account can be decrypted only by the same user account, or you can specify that data encrypted by the current user account can be decrypted by any account on the computer.</span></span>  <span data-ttu-id="bbdcf-111"><xref:System.Security.Cryptography.DataProtectionScope>Podrobný popis možností najdete v části výčet <xref:System.Security.Cryptography.ProtectedData> .</span><span class="sxs-lookup"><span data-stu-id="bbdcf-111">See the <xref:System.Security.Cryptography.DataProtectionScope> enumeration for a detailed description of <xref:System.Security.Cryptography.ProtectedData> options.</span></span>  
  
### <a name="to-encrypt-data-to-a-file-or-stream-using-data-protection"></a><span data-ttu-id="bbdcf-112">Šifrování dat do souboru nebo datového proudu pomocí ochrany dat</span><span class="sxs-lookup"><span data-stu-id="bbdcf-112">To encrypt data to a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="bbdcf-113">Vytvořte náhodnou entropii.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-113">Create random entropy.</span></span>  
  
2. <span data-ttu-id="bbdcf-114">Volejte statickou <xref:System.Security.Cryptography.ProtectedData.Protect%2A> metodu při předávání pole bajtů k zašifrování, entropii a rozsahu ochrany dat.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-114">Call the static <xref:System.Security.Cryptography.ProtectedData.Protect%2A> method while passing an array of bytes to encrypt, the entropy, and the data protection scope.</span></span>  
  
3. <span data-ttu-id="bbdcf-115">Zapište zašifrovaná data do souboru nebo datového proudu.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-115">Write the encrypted data to a file or stream.</span></span>  
  
### <a name="to-decrypt-data-from-a-file-or-stream-using-data-protection"></a><span data-ttu-id="bbdcf-116">Dešifrování dat ze souboru nebo datového proudu pomocí ochrany dat</span><span class="sxs-lookup"><span data-stu-id="bbdcf-116">To decrypt data from a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="bbdcf-117">Přečtěte si šifrovaná data ze souboru nebo datového proudu.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-117">Read the encrypted data from a file or stream.</span></span>  
  
2. <span data-ttu-id="bbdcf-118">Volejte statickou <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> metodu při předávání pole bajtů k dešifrování a rozsahu ochrany dat.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-118">Call the static <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> method while passing an array of bytes to decrypt and the data protection scope.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbdcf-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="bbdcf-119">Example</span></span>

<span data-ttu-id="bbdcf-120">Následující příklad kódu ukazuje dvě formy šifrování a dešifrování.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-120">The following code example demonstrates two forms of encryption and decryption.</span></span>  <span data-ttu-id="bbdcf-121">Nejprve příklad kódu šifruje a pak dešifruje pole bajtů v paměti.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-121">First, the code example encrypts and then decrypts an in-memory array of bytes.</span></span>  <span data-ttu-id="bbdcf-122">V dalším příkladu kód zašifruje kopii pole bajtů, uloží ho do souboru, načte data zpátky ze souboru a pak data dešifruje.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-122">Next, the code example encrypts a copy of a byte array, saves it to a file, loads the data back from the file, and then decrypts the data.</span></span>  <span data-ttu-id="bbdcf-123">V příkladu se zobrazí původní data, šifrovaná data a dešifrovaná data.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-123">The example displays the original data, the encrypted data, and the decrypted data.</span></span>

[!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
[!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bbdcf-124">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="bbdcf-124">Compiling the Code</span></span>  

<span data-ttu-id="bbdcf-125">Tento příklad se zkompiluje a spustí pouze v případě, že cílíte .NET Framework a běží v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-125">This example compiles and runs only when targeting .NET Framework and running on Windows.</span></span>

- <span data-ttu-id="bbdcf-126">Přidejte odkaz na `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="bbdcf-126">Include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="bbdcf-127">Přidejte <xref:System> <xref:System.IO> obor názvů,, <xref:System.Security.Cryptography> a <xref:System.Text> .</span><span class="sxs-lookup"><span data-stu-id="bbdcf-127">Include the <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography>, and <xref:System.Text> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbdcf-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="bbdcf-128">See also</span></span>

- [<span data-ttu-id="bbdcf-129">Kryptografický model</span><span class="sxs-lookup"><span data-stu-id="bbdcf-129">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="bbdcf-130">Šifrovací služby</span><span class="sxs-lookup"><span data-stu-id="bbdcf-130">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="bbdcf-131">Kryptografie pro různé platformy</span><span class="sxs-lookup"><span data-stu-id="bbdcf-131">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.ProtectedMemory>
- <xref:System.Security.Cryptography.ProtectedData>
- [<span data-ttu-id="bbdcf-132">Ochrana dat ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="bbdcf-132">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
