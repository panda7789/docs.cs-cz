---
title: Zajištění integrity dat pomocí hodnot hash
description: Naučte se, jak zajistit integritu dat pomocí kódů hash v .NET. Hodnota hash je číselná hodnota s pevnou délkou, která jednoznačně identifikuje data.
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- generating hash
- verifying hash codes
- cryptography [.NET], hash
- data integrity
- checking hash codes
- encryption [.NET], hash
- hash
ms.assetid: 33660f33-b70f-4dca-8c87-ab35cfc2961a
ms.openlocfilehash: 3205e37f283cb205f5edfc5948a9cb9f7256f752
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556953"
---
# <a name="ensuring-data-integrity-with-hash-codes"></a><span data-ttu-id="d7ce7-104">Zajištění integrity dat pomocí hodnot hash</span><span class="sxs-lookup"><span data-stu-id="d7ce7-104">Ensuring Data Integrity with Hash Codes</span></span>
<span data-ttu-id="d7ce7-105">Hodnota hash je číselná hodnota s pevnou délkou, která jednoznačně identifikuje data.</span><span class="sxs-lookup"><span data-stu-id="d7ce7-105">A hash value is a numeric value of a fixed length that uniquely identifies data.</span></span> <span data-ttu-id="d7ce7-106">Hodnoty hash představují velké objemy dat s mnohem menšími číselnými hodnotami, takže se používají s digitálními podpisy.</span><span class="sxs-lookup"><span data-stu-id="d7ce7-106">Hash values represent large amounts of data as much smaller numeric values, so they are used with digital signatures.</span></span> <span data-ttu-id="d7ce7-107">Hodnotu hash můžete efektivně podepsat, než je třeba podepsat větší hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d7ce7-107">You can sign a hash value more efficiently than signing the larger value.</span></span> <span data-ttu-id="d7ce7-108">Hodnoty hash jsou také užitečné pro ověření integrity dat odesílaných prostřednictvím nezabezpečených kanálů.</span><span class="sxs-lookup"><span data-stu-id="d7ce7-108">Hash values are also useful for verifying the integrity of data sent through insecure channels.</span></span> <span data-ttu-id="d7ce7-109">Hodnota hash přijatých dat se dá porovnat s hodnotou hash dat, protože byla odeslána, aby se zjistilo, jestli se data změnila.</span><span class="sxs-lookup"><span data-stu-id="d7ce7-109">The hash value of received data can be compared to the hash value of data as it was sent to determine whether the data was altered.</span></span>  
  
<span data-ttu-id="d7ce7-110">Toto téma popisuje, jak generovat a ověřit kódy hash pomocí tříd v <xref:System.Security.Cryptography> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d7ce7-110">This topic describes how to generate and verify hash codes by using the classes in the <xref:System.Security.Cryptography> namespace.</span></span>  
  
## <a name="generating-a-hash"></a><span data-ttu-id="d7ce7-111">Generování hodnoty hash</span><span class="sxs-lookup"><span data-stu-id="d7ce7-111">Generating a Hash</span></span>

 <span data-ttu-id="d7ce7-112">Spravované třídy hash mohou vytvořit hodnotu hash pole bajtů nebo objektu spravovaného datového proudu.</span><span class="sxs-lookup"><span data-stu-id="d7ce7-112">The managed hash classes can hash either an array of bytes or a managed stream object.</span></span> <span data-ttu-id="d7ce7-113">Následující příklad používá algoritmus hash SHA1 k vytvoření hodnoty hash pro řetězec.</span><span class="sxs-lookup"><span data-stu-id="d7ce7-113">The following example uses the SHA1 hash algorithm to create a hash value for a string.</span></span> <span data-ttu-id="d7ce7-114">V příkladu se používá <xref:System.Text.UnicodeEncoding> třída pro převod řetězce na pole bajtů, které jsou hashy pomocí <xref:System.Security.Cryptography.SHA256> třídy.</span><span class="sxs-lookup"><span data-stu-id="d7ce7-114">The example uses the <xref:System.Text.UnicodeEncoding> class to convert the string into an array of bytes that are hashed by using the <xref:System.Security.Cryptography.SHA256> class.</span></span> <span data-ttu-id="d7ce7-115">Hodnota hash se pak zobrazí v konzole nástroje.</span><span class="sxs-lookup"><span data-stu-id="d7ce7-115">The hash value is then displayed to the console.</span></span>  

 [!code-csharp[GeneratingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/generatingahash/cs/program.cs#1)]
 [!code-vb[GeneratingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/generatingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="d7ce7-116">Tento kód zobrazí následující řetězec pro konzolu:</span><span class="sxs-lookup"><span data-stu-id="d7ce7-116">This code will display the following string to the console:</span></span>  
  
 `185 203 236 22 3 228 27 130 87 23 244 15 87 88 14 43 37 61 106 224 81 172 224 211 104 85 194 197 194 25 120 217`  
  
## <a name="verifying-a-hash"></a><span data-ttu-id="d7ce7-117">Ověření hodnoty hash</span><span class="sxs-lookup"><span data-stu-id="d7ce7-117">Verifying a Hash</span></span>

 <span data-ttu-id="d7ce7-118">Data je možné porovnat s hodnotou hash k určení její integrity.</span><span class="sxs-lookup"><span data-stu-id="d7ce7-118">Data can be compared to a hash value to determine its integrity.</span></span> <span data-ttu-id="d7ce7-119">Data jsou obvykle Hashovaná v určitou dobu a hodnota hash je chráněna nějakým způsobem.</span><span class="sxs-lookup"><span data-stu-id="d7ce7-119">Usually, data is hashed at a certain time and the hash value is protected in some way.</span></span> <span data-ttu-id="d7ce7-120">Později můžete data znovu hash a porovnat s chráněnou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="d7ce7-120">At a later time, the data can be hashed again and compared to the protected value.</span></span> <span data-ttu-id="d7ce7-121">Pokud se hodnoty hash shodují, data se nezmění.</span><span class="sxs-lookup"><span data-stu-id="d7ce7-121">If the hash values match, the data has not been altered.</span></span> <span data-ttu-id="d7ce7-122">Pokud se hodnoty neshodují, data jsou poškozena.</span><span class="sxs-lookup"><span data-stu-id="d7ce7-122">If the values do not match, the data has been corrupted.</span></span> <span data-ttu-id="d7ce7-123">Aby tento systém fungoval, musí být chráněný algoritmus hash zašifrovaný nebo musí uchovávat tajné klíče ze všech nedůvěryhodných stran.</span><span class="sxs-lookup"><span data-stu-id="d7ce7-123">For this system to work, the protected hash must be encrypted or kept secret from all untrusted parties.</span></span>  
  
 <span data-ttu-id="d7ce7-124">Následující příklad porovnává předchozí hodnotu hash řetězce s novou hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="d7ce7-124">The following example compares the previous hash value of a string to a new hash value.</span></span> <span data-ttu-id="d7ce7-125">Tento příklad projde každým bajtem hodnot hash a provede porovnání.</span><span class="sxs-lookup"><span data-stu-id="d7ce7-125">This example loops through each byte of the hash values and makes a comparison.</span></span>  
  
 [!code-csharp[VerifyingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/verifyingahash/cs/program.cs#1)]
 [!code-vb[VerifyingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/verifyingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="d7ce7-126">Pokud se dvě hodnoty hash shodují, tento kód zobrazí následující kód konzole:</span><span class="sxs-lookup"><span data-stu-id="d7ce7-126">If the two hash values match, this code displays the following to the console:</span></span>  
  
```console  
The hash codes match.  
```  
  
 <span data-ttu-id="d7ce7-127">Pokud se neshodují, kód zobrazí následující:</span><span class="sxs-lookup"><span data-stu-id="d7ce7-127">If they do not match, the code displays the following:</span></span>  
  
```console  
The hash codes do not match.  
```  
  
## <a name="see-also"></a><span data-ttu-id="d7ce7-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="d7ce7-128">See also</span></span>

- [<span data-ttu-id="d7ce7-129">Kryptografický model</span><span class="sxs-lookup"><span data-stu-id="d7ce7-129">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="d7ce7-130">Šifrovací služby</span><span class="sxs-lookup"><span data-stu-id="d7ce7-130">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="d7ce7-131">Kryptografie pro různé platformy</span><span class="sxs-lookup"><span data-stu-id="d7ce7-131">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="d7ce7-132">Ochrana dat ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d7ce7-132">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
