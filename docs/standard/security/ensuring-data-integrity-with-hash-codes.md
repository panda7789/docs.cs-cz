---
title: Zajištění integrity dat pomocí hodnot hash
description: Naučte se, jak zajistit integritu dat pomocí kódů hash v .NET. Hodnota hash je číselná hodnota s pevnou délkou, která jednoznačně identifikuje data.
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
ms.openlocfilehash: ffc5e78228f4e7c56febdc0872a0bc0fc581f162
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769051"
---
# <a name="ensuring-data-integrity-with-hash-codes"></a><span data-ttu-id="0f58f-104">Zajištění integrity dat pomocí hodnot hash</span><span class="sxs-lookup"><span data-stu-id="0f58f-104">Ensuring Data Integrity with Hash Codes</span></span>
<span data-ttu-id="0f58f-105">Hodnota hash je číselná hodnota s pevnou délkou, která jednoznačně identifikuje data.</span><span class="sxs-lookup"><span data-stu-id="0f58f-105">A hash value is a numeric value of a fixed length that uniquely identifies data.</span></span> <span data-ttu-id="0f58f-106">Hodnoty hash představují velké objemy dat s mnohem menšími číselnými hodnotami, takže se používají s digitálními podpisy.</span><span class="sxs-lookup"><span data-stu-id="0f58f-106">Hash values represent large amounts of data as much smaller numeric values, so they are used with digital signatures.</span></span> <span data-ttu-id="0f58f-107">Hodnotu hash můžete efektivně podepsat, než je třeba podepsat větší hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0f58f-107">You can sign a hash value more efficiently than signing the larger value.</span></span> <span data-ttu-id="0f58f-108">Hodnoty hash jsou také užitečné pro ověření integrity dat odesílaných prostřednictvím nezabezpečených kanálů.</span><span class="sxs-lookup"><span data-stu-id="0f58f-108">Hash values are also useful for verifying the integrity of data sent through insecure channels.</span></span> <span data-ttu-id="0f58f-109">Hodnota hash přijatých dat se dá porovnat s hodnotou hash dat, protože byla odeslána, aby se zjistilo, jestli se data změnila.</span><span class="sxs-lookup"><span data-stu-id="0f58f-109">The hash value of received data can be compared to the hash value of data as it was sent to determine whether the data was altered.</span></span>  
  
 <span data-ttu-id="0f58f-110">Toto téma popisuje, jak generovat a ověřit kódy hash pomocí tříd v <xref:System.Security.Cryptography?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0f58f-110">This topic describes how to generate and verify hash codes by using the classes in the <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="generating-a-hash"></a><span data-ttu-id="0f58f-111">Generování hodnoty hash</span><span class="sxs-lookup"><span data-stu-id="0f58f-111">Generating a Hash</span></span>  
 <span data-ttu-id="0f58f-112">Spravované třídy hash mohou vytvořit hodnotu hash pole bajtů nebo objektu spravovaného datového proudu.</span><span class="sxs-lookup"><span data-stu-id="0f58f-112">The managed hash classes can hash either an array of bytes or a managed stream object.</span></span> <span data-ttu-id="0f58f-113">Následující příklad používá algoritmus hash SHA1 k vytvoření hodnoty hash pro řetězec.</span><span class="sxs-lookup"><span data-stu-id="0f58f-113">The following example uses the SHA1 hash algorithm to create a hash value for a string.</span></span> <span data-ttu-id="0f58f-114">V příkladu se používá <xref:System.Text.UnicodeEncoding> třída pro převod řetězce na pole bajtů, které jsou hashy pomocí <xref:System.Security.Cryptography.SHA1Managed> třídy.</span><span class="sxs-lookup"><span data-stu-id="0f58f-114">The example uses the <xref:System.Text.UnicodeEncoding> class to convert the string into an array of bytes that are hashed by using the <xref:System.Security.Cryptography.SHA1Managed> class.</span></span> <span data-ttu-id="0f58f-115">Hodnota hash se pak zobrazí v konzole nástroje.</span><span class="sxs-lookup"><span data-stu-id="0f58f-115">The hash value is then displayed to the console.</span></span>  

 <span data-ttu-id="0f58f-116">Microsoft doporučuje SHA256 nebo lepší kvůli kolizi problémů se SHA1.</span><span class="sxs-lookup"><span data-stu-id="0f58f-116">Due to collision problems with SHA1, Microsoft recommends SHA256 or better.</span></span>
  
 [!code-csharp[GeneratingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/generatingahash/cs/program.cs#1)]
 [!code-vb[GeneratingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/generatingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="0f58f-117">Tento kód zobrazí následující řetězec pro konzolu:</span><span class="sxs-lookup"><span data-stu-id="0f58f-117">This code will display the following string to the console:</span></span>  
  
 `59 4 248 102 77 97 142 201 210 12 224 93 25 41 100 197 213 134 130 135`  
  
## <a name="verifying-a-hash"></a><span data-ttu-id="0f58f-118">Ověření hodnoty hash</span><span class="sxs-lookup"><span data-stu-id="0f58f-118">Verifying a Hash</span></span>  
 <span data-ttu-id="0f58f-119">Data je možné porovnat s hodnotou hash k určení její integrity.</span><span class="sxs-lookup"><span data-stu-id="0f58f-119">Data can be compared to a hash value to determine its integrity.</span></span> <span data-ttu-id="0f58f-120">Data jsou obvykle Hashovaná v určitou dobu a hodnota hash je chráněna nějakým způsobem.</span><span class="sxs-lookup"><span data-stu-id="0f58f-120">Usually, data is hashed at a certain time and the hash value is protected in some way.</span></span> <span data-ttu-id="0f58f-121">Později můžete data znovu hash a porovnat s chráněnou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="0f58f-121">At a later time, the data can be hashed again and compared to the protected value.</span></span> <span data-ttu-id="0f58f-122">Pokud se hodnoty hash shodují, data se nezmění.</span><span class="sxs-lookup"><span data-stu-id="0f58f-122">If the hash values match, the data has not been altered.</span></span> <span data-ttu-id="0f58f-123">Pokud se hodnoty neshodují, data jsou poškozena.</span><span class="sxs-lookup"><span data-stu-id="0f58f-123">If the values do not match, the data has been corrupted.</span></span> <span data-ttu-id="0f58f-124">Aby tento systém fungoval, musí být chráněný algoritmus hash zašifrovaný nebo musí uchovávat tajné klíče ze všech nedůvěryhodných stran.</span><span class="sxs-lookup"><span data-stu-id="0f58f-124">For this system to work, the protected hash must be encrypted or kept secret from all untrusted parties.</span></span>  
  
 <span data-ttu-id="0f58f-125">Následující příklad porovnává předchozí hodnotu hash řetězce s novou hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="0f58f-125">The following example compares the previous hash value of a string to a new hash value.</span></span> <span data-ttu-id="0f58f-126">Tento příklad projde každým bajtem hodnot hash a provede porovnání.</span><span class="sxs-lookup"><span data-stu-id="0f58f-126">This example loops through each byte of the hash values and makes a comparison.</span></span>  
  
 [!code-csharp[VerifyingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/verifyingahash/cs/program.cs#1)]
 [!code-vb[VerifyingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/verifyingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="0f58f-127">Pokud se dvě hodnoty hash shodují, tento kód zobrazí následující kód konzole:</span><span class="sxs-lookup"><span data-stu-id="0f58f-127">If the two hash values match, this code displays the following to the console:</span></span>  
  
```console  
The hash codes match.  
```  
  
 <span data-ttu-id="0f58f-128">Pokud se neshodují, kód zobrazí následující:</span><span class="sxs-lookup"><span data-stu-id="0f58f-128">If they do not match, the code displays the following:</span></span>  
  
```console  
The hash codes do not match.  
```  
  
## <a name="see-also"></a><span data-ttu-id="0f58f-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="0f58f-129">See also</span></span>

- [<span data-ttu-id="0f58f-130">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="0f58f-130">Cryptographic Services</span></span>](cryptographic-services.md)
