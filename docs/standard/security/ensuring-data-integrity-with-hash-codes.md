---
title: Zajištění integrity dat pomocí hodnot hash
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16770ea938973372d1d94c628c42d5d5bf10c695
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43874989"
---
# <a name="ensuring-data-integrity-with-hash-codes"></a><span data-ttu-id="7da34-102">Zajištění integrity dat pomocí hodnot hash</span><span class="sxs-lookup"><span data-stu-id="7da34-102">Ensuring Data Integrity with Hash Codes</span></span>
<span data-ttu-id="7da34-103">Hodnota hash je číselná hodnota pevnou délku, která jednoznačně identifikuje data.</span><span class="sxs-lookup"><span data-stu-id="7da34-103">A hash value is a numeric value of a fixed length that uniquely identifies data.</span></span> <span data-ttu-id="7da34-104">Hodnoty hash znázornění velkých objemů dat jako mnohem menší číselných hodnot, tak se používají v digitální podpisy.</span><span class="sxs-lookup"><span data-stu-id="7da34-104">Hash values represent large amounts of data as much smaller numeric values, so they are used with digital signatures.</span></span> <span data-ttu-id="7da34-105">Hodnota hash se můžete přihlásit efektivnější než podepisování větší hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7da34-105">You can sign a hash value more efficiently than signing the larger value.</span></span> <span data-ttu-id="7da34-106">Hodnoty hash jsou také užitečná pro ověření integrity dat posílaných prostřednictvím nezabezpečených kanálů.</span><span class="sxs-lookup"><span data-stu-id="7da34-106">Hash values are also useful for verifying the integrity of data sent through insecure channels.</span></span> <span data-ttu-id="7da34-107">Hodnota hash přijatá data je možné porovnat s hodnoty hash dat, protože byla odeslána k určení, zda byla data změněna.</span><span class="sxs-lookup"><span data-stu-id="7da34-107">The hash value of received data can be compared to the hash value of data as it was sent to determine whether the data was altered.</span></span>  
  
 <span data-ttu-id="7da34-108">Toto téma popisuje, jak vytvořit a ověřit hash kódy s využitím tříd v <xref:System.Security.Cryptography?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7da34-108">This topic describes how to generate and verify hash codes by using the classes in the <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="generating-a-hash"></a><span data-ttu-id="7da34-109">Generování hodnoty Hash</span><span class="sxs-lookup"><span data-stu-id="7da34-109">Generating a Hash</span></span>  
 <span data-ttu-id="7da34-110">Třídy spravované hash může hash pole bajtů nebo objekt spravovaný datový proud.</span><span class="sxs-lookup"><span data-stu-id="7da34-110">The managed hash classes can hash either an array of bytes or a managed stream object.</span></span> <span data-ttu-id="7da34-111">Následující příklad používá algoritmus hash SHA1 vytvořit hodnotu hash pro řetězce.</span><span class="sxs-lookup"><span data-stu-id="7da34-111">The following example uses the SHA1 hash algorithm to create a hash value for a string.</span></span> <span data-ttu-id="7da34-112">V příkladu se používá <xref:System.Text.UnicodeEncoding> pro převod řetězce na pole bajtů, které jsou hashována pomocí <xref:System.Security.Cryptography.SHA1Managed> třídy.</span><span class="sxs-lookup"><span data-stu-id="7da34-112">The example uses the <xref:System.Text.UnicodeEncoding> class to convert the string into an array of bytes that are hashed by using the <xref:System.Security.Cryptography.SHA1Managed> class.</span></span> <span data-ttu-id="7da34-113">Hodnota hash se pak zobrazí v konzole.</span><span class="sxs-lookup"><span data-stu-id="7da34-113">The hash value is then displayed to the console.</span></span>  
  
 [!code-csharp[GeneratingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/generatingahash/cs/program.cs#1)]
 [!code-vb[GeneratingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/generatingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="7da34-114">Tento kód se zobrazí následující řetězec do konzoly:</span><span class="sxs-lookup"><span data-stu-id="7da34-114">This code will display the following string to the console:</span></span>  
  
 `59 4 248 102 77 97 142 201 210 12 224 93 25 41 100 197 213 134 130 135`  
  
## <a name="verifying-a-hash"></a><span data-ttu-id="7da34-115">Ověření hodnoty Hash</span><span class="sxs-lookup"><span data-stu-id="7da34-115">Verifying a Hash</span></span>  
 <span data-ttu-id="7da34-116">Data je možné porovnat s hodnotou hash k určení jeho integritu.</span><span class="sxs-lookup"><span data-stu-id="7da34-116">Data can be compared to a hash value to determine its integrity.</span></span> <span data-ttu-id="7da34-117">Obvykle data se po zahašování použije v určitém čase a hodnota hash je chráněn nějakým způsobem.</span><span class="sxs-lookup"><span data-stu-id="7da34-117">Usually, data is hashed at a certain time and the hash value is protected in some way.</span></span> <span data-ttu-id="7da34-118">Data můžete kdykoli později, znovu vytvořit otisk a ve srovnání s chráněná hodnota.</span><span class="sxs-lookup"><span data-stu-id="7da34-118">At a later time, the data can be hashed again and compared to the protected value.</span></span> <span data-ttu-id="7da34-119">Pokud se hodnoty hash shodují, data nikdo nezměnil.</span><span class="sxs-lookup"><span data-stu-id="7da34-119">If the hash values match, the data has not been altered.</span></span> <span data-ttu-id="7da34-120">Pokud hodnoty nejsou shodné, data byla poškozena.</span><span class="sxs-lookup"><span data-stu-id="7da34-120">If the values do not match, the data has been corrupted.</span></span> <span data-ttu-id="7da34-121">Pro tento systém fungovat musí být šifrované nebo udržen v tajnosti před všechny nedůvěryhodní chráněné hash.</span><span class="sxs-lookup"><span data-stu-id="7da34-121">For this system to work, the protected hash must be encrypted or kept secret from all untrusted parties.</span></span>  
  
 <span data-ttu-id="7da34-122">Následující příklad porovnává předchozí hodnotu hash řetězce na novou hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="7da34-122">The following example compares the previous hash value of a string to a new hash value.</span></span> <span data-ttu-id="7da34-123">V tomto příkladu prochází každý bajt hodnoty hash a provádí porovnání.</span><span class="sxs-lookup"><span data-stu-id="7da34-123">This example loops through each byte of the hash values and makes a comparison.</span></span>  
  
 [!code-csharp[VerifyingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/verifyingahash/cs/program.cs#1)]
 [!code-vb[VerifyingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/verifyingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="7da34-124">Pokud tyto hodnoty hash shodují, zobrazí tento kód do konzoly následující:</span><span class="sxs-lookup"><span data-stu-id="7da34-124">If the two hash values match, this code displays the following to the console:</span></span>  
  
```  
The hash codes match.  
```  
  
 <span data-ttu-id="7da34-125">Pokud shodné nejsou, zobrazí následující kód:</span><span class="sxs-lookup"><span data-stu-id="7da34-125">If they do not match, the code displays the following:</span></span>  
  
```  
The hash codes do not match.  
```  
  
## <a name="see-also"></a><span data-ttu-id="7da34-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7da34-126">See also</span></span>

- [<span data-ttu-id="7da34-127">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="7da34-127">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
