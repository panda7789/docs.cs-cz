---
title: Zabezpečení a průběžné vytváření kódu
description: Generování kódu jménem méně důvěryhodného kódu, který běží s vyšším vztahem důvěryhodnosti, je problém se zabezpečením, zejména pokud volající může ovlivnit generování kódu.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- code security, on-the-fly code generation
- on-the-fly code generation
- security [.NET Framework], on-the-fly code generation
- secure coding, on-the-fly code generation
ms.assetid: 6d221724-bb21-4d76-90c3-0ee2a2e69be2
ms.openlocfilehash: 34ebda27a81ca29ebb27a721b77b735a12be882e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186790"
---
# <a name="security-and-on-the-fly-code-generation"></a><span data-ttu-id="d66eb-103">Zabezpečení a průběžné vytváření kódu</span><span class="sxs-lookup"><span data-stu-id="d66eb-103">Security and On-the-Fly Code Generation</span></span>
<span data-ttu-id="d66eb-104">Některé knihovny pracují generováním kódu a jeho spuštěním k provedení některé operace pro volajícího.</span><span class="sxs-lookup"><span data-stu-id="d66eb-104">Some libraries operate by generating code and running it to perform some operation for the caller.</span></span> <span data-ttu-id="d66eb-105">Základním problémem je generování kódu jménem méně důvěryhodného kódu a jeho spuštění s vyšším vztahem důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="d66eb-105">The basic problem is generating code on behalf of lesser-trust code and running it at a higher trust.</span></span> <span data-ttu-id="d66eb-106">Problém se zhoršuje, když volající může ovlivnit generování kódu, takže je nutné zajistit, že je generován pouze kód, který považujete za bezpečný.</span><span class="sxs-lookup"><span data-stu-id="d66eb-106">The problem worsens when the caller can influence code generation, so you must ensure that only code you consider safe is generated.</span></span>  
  
 <span data-ttu-id="d66eb-107">Musíte přesně vědět, jaký kód generujete za všech okolností.</span><span class="sxs-lookup"><span data-stu-id="d66eb-107">You need to know exactly what code you are generating at all times.</span></span> <span data-ttu-id="d66eb-108">To znamená, že musíte mít přísné kontroly všech hodnot, které získáte od uživatele, ať už se jedná o řetězce uzavřené v uvozovkách (které by měly být uvozeny, aby nemohly obsahovat neočekávané prvky kódu), identifikátory (které by měly být zkontrolovány, aby se ověřilo, že jsou platné identifikátory) nebo cokoli jiného.</span><span class="sxs-lookup"><span data-stu-id="d66eb-108">This means that you must have strict controls on any values that you get from a user, be they quote-enclosed strings (which should be escaped so they cannot include unexpected code elements), identifiers (which should be checked to verify that they are valid identifiers), or anything else.</span></span> <span data-ttu-id="d66eb-109">Identifikátory mohou být nebezpečné, protože zkompilované sestavení lze upravit tak, aby jeho identifikátory obsahovaly podivné znaky, které je pravděpodobně přeruší (i když se zřídka jedná o chybu zabezpečení).</span><span class="sxs-lookup"><span data-stu-id="d66eb-109">Identifiers can be dangerous because a compiled assembly can be modified so that its identifiers contain strange characters, which will probably break it (although this is rarely a security vulnerability).</span></span>  
  
 <span data-ttu-id="d66eb-110">Doporučujese generovat kód s odrazem vyzařovat, což často pomáhá vyhnout se mnoho z těchto problémů.</span><span class="sxs-lookup"><span data-stu-id="d66eb-110">It is recommended that you generate code with reflection emit, which often helps you avoid many of these problems.</span></span>  
  
 <span data-ttu-id="d66eb-111">Při kompilaci kódu zvažte, zda existuje nějaký způsob, jak škodlivý program může změnit.</span><span class="sxs-lookup"><span data-stu-id="d66eb-111">When you compile the code, consider whether there is some way a malicious program could modify it.</span></span> <span data-ttu-id="d66eb-112">Existuje malé časové okno, během kterého škodlivý kód může změnit zdrojový kód na disku před překladač přečte nebo před kód načte soubor DLL?</span><span class="sxs-lookup"><span data-stu-id="d66eb-112">Is there a small window of time during which malicious code can change source code on disk before the compiler reads it or before your code loads the .dll file?</span></span> <span data-ttu-id="d66eb-113">Pokud ano, je nutné chránit adresář obsahující tyto soubory pomocí seznamu řízení přístupu v systému souborů podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="d66eb-113">If so, you must protect the directory containing these files, using an Access Control List in the file system, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d66eb-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="d66eb-114">See also</span></span>

- [<span data-ttu-id="d66eb-115">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="d66eb-115">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
