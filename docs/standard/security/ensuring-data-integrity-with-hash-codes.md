---
title: "Zajištění integrity dat pomocí hodnot hash"
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
- generating hash
- verifying hash codes
- cryptography [.NET Framework], hash
- data integrity
- checking hash codes
- encryption [.NET Framework], hash
- hash
ms.assetid: 33660f33-b70f-4dca-8c87-ab35cfc2961a
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b5d54a608ae87a1b453b4fa2b4b351ac5fc9f068
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ensuring-data-integrity-with-hash-codes"></a><span data-ttu-id="b9f85-102">Zajištění integrity dat pomocí hodnot hash</span><span class="sxs-lookup"><span data-stu-id="b9f85-102">Ensuring Data Integrity with Hash Codes</span></span>
<span data-ttu-id="b9f85-103">Hodnota hash je číselná hodnota pevnou délku, která jednoznačně identifikuje data.</span><span class="sxs-lookup"><span data-stu-id="b9f85-103">A hash value is a numeric value of a fixed length that uniquely identifies data.</span></span> <span data-ttu-id="b9f85-104">Hodnoty hash představují velké objemy dat jako mnohem menší číselné hodnoty, takže se používají s digitálními podpisy.</span><span class="sxs-lookup"><span data-stu-id="b9f85-104">Hash values represent large amounts of data as much smaller numeric values, so they are used with digital signatures.</span></span> <span data-ttu-id="b9f85-105">Hodnota hash je možné podepsat efektivnější než velkou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b9f85-105">You can sign a hash value more efficiently than signing the larger value.</span></span> <span data-ttu-id="b9f85-106">Hodnoty hash jsou taky užitečné pro ověření integrity dat odeslaných v nezabezpečené kanály.</span><span class="sxs-lookup"><span data-stu-id="b9f85-106">Hash values are also useful for verifying the integrity of data sent through insecure channels.</span></span> <span data-ttu-id="b9f85-107">Hodnota hash přijatých dat. lze porovnat hodnotu hash dat, jako byl odeslán k určení, zda byla změněna data.</span><span class="sxs-lookup"><span data-stu-id="b9f85-107">The hash value of received data can be compared to the hash value of data as it was sent to determine whether the data was altered.</span></span>  
  
 <span data-ttu-id="b9f85-108">Toto téma popisuje, jak vytvořit a ověřit kódů hash pomocí třídy v <xref:System.Security.Cryptography?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b9f85-108">This topic describes how to generate and verify hash codes by using the classes in the <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="generating-a-hash"></a><span data-ttu-id="b9f85-109">Generování hodnoty Hash</span><span class="sxs-lookup"><span data-stu-id="b9f85-109">Generating a Hash</span></span>  
 <span data-ttu-id="b9f85-110">Spravované hash třídy můžete hash pole bajtů nebo objekt spravovaného streamu.</span><span class="sxs-lookup"><span data-stu-id="b9f85-110">The managed hash classes can hash either an array of bytes or a managed stream object.</span></span> <span data-ttu-id="b9f85-111">Následující příklad používá algoritmus hash SHA1 vytvořit hodnotu hash pro řetězec.</span><span class="sxs-lookup"><span data-stu-id="b9f85-111">The following example uses the SHA1 hash algorithm to create a hash value for a string.</span></span> <span data-ttu-id="b9f85-112">V příkladu se používá <xref:System.Text.UnicodeEncoding> třída převést řetězec na pole bajtů, které jsou hashována pomocí <xref:System.Security.Cryptography.SHA1Managed> třídy.</span><span class="sxs-lookup"><span data-stu-id="b9f85-112">The example uses the <xref:System.Text.UnicodeEncoding> class to convert the string into an array of bytes that are hashed by using the <xref:System.Security.Cryptography.SHA1Managed> class.</span></span> <span data-ttu-id="b9f85-113">Hodnota hash se následně zobrazí ke konzole.</span><span class="sxs-lookup"><span data-stu-id="b9f85-113">The hash value is then displayed to the console.</span></span>  
  
 [!code-csharp[GeneratingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/generatingahash/cs/program.cs#1)]
 [!code-vb[GeneratingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/generatingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="b9f85-114">Tento kód se zobrazí následující řetězec do konzoly:</span><span class="sxs-lookup"><span data-stu-id="b9f85-114">This code will display the following string to the console:</span></span>  
  
 `59 4 248 102 77 97 142 201 210 12 224 93 25 41 100 197 213 134 130 135`  
  
## <a name="verifying-a-hash"></a><span data-ttu-id="b9f85-115">Ověření hodnoty Hash</span><span class="sxs-lookup"><span data-stu-id="b9f85-115">Verifying a Hash</span></span>  
 <span data-ttu-id="b9f85-116">Data lze porovnat s hodnotou hash určit jeho integritu.</span><span class="sxs-lookup"><span data-stu-id="b9f85-116">Data can be compared to a hash value to determine its integrity.</span></span> <span data-ttu-id="b9f85-117">Obvykle se rozdělí data v určitém čase a hodnota hash je chráněný nějakým způsobem.</span><span class="sxs-lookup"><span data-stu-id="b9f85-117">Usually, data is hashed at a certain time and the hash value is protected in some way.</span></span> <span data-ttu-id="b9f85-118">Data můžete později, znovu rozdělí a porovnání s chráněná hodnota.</span><span class="sxs-lookup"><span data-stu-id="b9f85-118">At a later time, the data can be hashed again and compared to the protected value.</span></span> <span data-ttu-id="b9f85-119">Pokud se hodnoty hash shodují, data nikdo nezměnil.</span><span class="sxs-lookup"><span data-stu-id="b9f85-119">If the hash values match, the data has not been altered.</span></span> <span data-ttu-id="b9f85-120">Pokud se hodnoty neshodují, je poškozená data.</span><span class="sxs-lookup"><span data-stu-id="b9f85-120">If the values do not match, the data has been corrupted.</span></span> <span data-ttu-id="b9f85-121">Pro tento systém fungovat musí být chráněný hash šifrované nebo náskoku před všechny nedůvěryhodní.</span><span class="sxs-lookup"><span data-stu-id="b9f85-121">For this system to work, the protected hash must be encrypted or kept secret from all untrusted parties.</span></span>  
  
 <span data-ttu-id="b9f85-122">Následující příklad porovnává předchozí hodnotu hash řetězce na novou hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="b9f85-122">The following example compares the previous hash value of a string to a new hash value.</span></span> <span data-ttu-id="b9f85-123">V tomto příkladu prochází každým bajtem hodnoty hash a provádí porovnání.</span><span class="sxs-lookup"><span data-stu-id="b9f85-123">This example loops through each byte of the hash values and makes a comparison.</span></span>  
  
 [!code-csharp[VerifyingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/verifyingahash/cs/program.cs#1)]
 [!code-vb[VerifyingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/verifyingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="b9f85-124">Pokud tyto hodnoty hash shodují, tento kód zobrazí následující do konzoly:</span><span class="sxs-lookup"><span data-stu-id="b9f85-124">If the two hash values match, this code displays the following to the console:</span></span>  
  
```  
The hash codes match.  
```  
  
 <span data-ttu-id="b9f85-125">Pokud se neshodují, zobrazí se následující kód:</span><span class="sxs-lookup"><span data-stu-id="b9f85-125">If they do not match, the code displays the following:</span></span>  
  
```  
The hash codes do not match.  
```  
  
## <a name="see-also"></a><span data-ttu-id="b9f85-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="b9f85-126">See Also</span></span>  
 [<span data-ttu-id="b9f85-127">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="b9f85-127">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
