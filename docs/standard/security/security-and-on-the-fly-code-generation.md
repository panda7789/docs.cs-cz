---
title: Zabezpečení a průběžné vytváření kódu
description: Generování kódu jménem méně důvěryhodného kódu, který běží ve vyšším vztahu důvěryhodnosti, je bezpečnostním problémem, zejména v případě, že volající může ovlivnit generování kódu.
ms.date: 07/15/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- code security, on-the-fly code generation
- on-the-fly code generation
- security [.NET], on-the-fly code generation
- secure coding, on-the-fly code generation
ms.assetid: 6d221724-bb21-4d76-90c3-0ee2a2e69be2
ms.openlocfilehash: a3fc51c346feffa85537d95ccdbd23d943827edf
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555692"
---
# <a name="security-and-on-the-fly-code-generation"></a><span data-ttu-id="b1a77-103">Zabezpečení a průběžné vytváření kódu</span><span class="sxs-lookup"><span data-stu-id="b1a77-103">Security and On-the-Fly Code Generation</span></span>

<span data-ttu-id="b1a77-104">Některé knihovny fungují tak, že generují kód a spouštějí ho k provedení určité operace pro volajícího.</span><span class="sxs-lookup"><span data-stu-id="b1a77-104">Some libraries operate by generating code and running it to perform some operation for the caller.</span></span> <span data-ttu-id="b1a77-105">Základní problém je generování kódu jménem méně důvěryhodného kódu a jeho spuštění s vyšší důvěryhodností.</span><span class="sxs-lookup"><span data-stu-id="b1a77-105">The basic problem is generating code on behalf of lesser-trust code and running it at a higher trust.</span></span> <span data-ttu-id="b1a77-106">Problém se zhorší, když volající může ovlivnit generování kódu, takže je nutné zajistit, aby byl vygenerován pouze kód, který považujete za bezpečný.</span><span class="sxs-lookup"><span data-stu-id="b1a77-106">The problem worsens when the caller can influence code generation, so you must ensure that only code you consider safe is generated.</span></span>  
  
<span data-ttu-id="b1a77-107">Je potřeba přesně zjistit, co kód vygenerujete za všech okolností.</span><span class="sxs-lookup"><span data-stu-id="b1a77-107">You need to know exactly what code you are generating at all times.</span></span> <span data-ttu-id="b1a77-108">To znamená, že musíte mít přísné ovládací prvky pro všechny hodnoty, které obdržíte od uživatele, jako řetězce v uvozovkách (které by měly být uvozeny řídicími znaky), identifikátory (které by měly být zkontrolovány, zda jsou platné identifikátory) nebo cokoli jiného.</span><span class="sxs-lookup"><span data-stu-id="b1a77-108">This means that you must have strict controls on any values that you get from a user, be they quote-enclosed strings (which should be escaped so they cannot include unexpected code elements), identifiers (which should be checked to verify that they are valid identifiers), or anything else.</span></span> <span data-ttu-id="b1a77-109">Identifikátory mohou být nebezpečné, protože zkompilované sestavení lze upravit tak, aby jeho identifikátory obsahovaly nezvyklé znaky, což bude pravděpodobně přerušeno (i když se jedná o vzácnou chybu zabezpečení).</span><span class="sxs-lookup"><span data-stu-id="b1a77-109">Identifiers can be dangerous because a compiled assembly can be modified so that its identifiers contain strange characters, which will probably break it (although this is rarely a security vulnerability).</span></span>  
  
<span data-ttu-id="b1a77-110">Doporučujeme, abyste vygenerovali kód s vygenerováním reflexe, což často pomáhá vyhnout se mnohé z těchto problémů.</span><span class="sxs-lookup"><span data-stu-id="b1a77-110">It is recommended that you generate code with reflection emit, which often helps you avoid many of these problems.</span></span>  
  
<span data-ttu-id="b1a77-111">Při kompilování kódu zvažte, zda existuje nějaký způsob, jak škodlivý program upravit.</span><span class="sxs-lookup"><span data-stu-id="b1a77-111">When you compile the code, consider whether there is some way a malicious program could modify it.</span></span> <span data-ttu-id="b1a77-112">Existuje malé okno času, během kterého škodlivý kód může změnit zdrojový kód na disku před tím, než ho kompilátor přečte nebo před tím, než kód načte soubor. dll?</span><span class="sxs-lookup"><span data-stu-id="b1a77-112">Is there a small window of time during which malicious code can change source code on disk before the compiler reads it or before your code loads the .dll file?</span></span> <span data-ttu-id="b1a77-113">V takovém případě je nutné chránit adresář obsahující tyto soubory pomocí seznamu Access Control v systému souborů podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="b1a77-113">If so, you must protect the directory containing these files, using an Access Control List in the file system, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1a77-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1a77-114">See also</span></span>

- [<span data-ttu-id="b1a77-115">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="b1a77-115">Secure Coding Guidelines</span></span>](secure-coding-guidelines.md)
- [<span data-ttu-id="b1a77-116">ASP.NET Core zabezpečení</span><span class="sxs-lookup"><span data-stu-id="b1a77-116">ASP.NET Core Security</span></span>](/aspnet/core/security/)
