---
title: Zabezpečení a průběžné vytváření kódu
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- code security, on-the-fly code generation
- on-the-fly code generation
- security [.NET Framework], on-the-fly code generation
- secure coding, on-the-fly code generation
ms.assetid: 6d221724-bb21-4d76-90c3-0ee2a2e69be2
ms.openlocfilehash: 64ddcc6a379e5719eb734eede13e576a707696fe
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705883"
---
# <a name="security-and-on-the-fly-code-generation"></a><span data-ttu-id="c2f6d-102">Zabezpečení a průběžné vytváření kódu</span><span class="sxs-lookup"><span data-stu-id="c2f6d-102">Security and On-the-Fly Code Generation</span></span>
<span data-ttu-id="c2f6d-103">Některé knihovny fungují tak, že generují kód a spouštějí ho k provedení určité operace pro volajícího.</span><span class="sxs-lookup"><span data-stu-id="c2f6d-103">Some libraries operate by generating code and running it to perform some operation for the caller.</span></span> <span data-ttu-id="c2f6d-104">Základní problém je generování kódu jménem méně důvěryhodného kódu a jeho spuštění s vyšší důvěryhodností.</span><span class="sxs-lookup"><span data-stu-id="c2f6d-104">The basic problem is generating code on behalf of lesser-trust code and running it at a higher trust.</span></span> <span data-ttu-id="c2f6d-105">Problém se zhorší, když volající může ovlivnit generování kódu, takže je nutné zajistit, aby byl vygenerován pouze kód, který považujete za bezpečný.</span><span class="sxs-lookup"><span data-stu-id="c2f6d-105">The problem worsens when the caller can influence code generation, so you must ensure that only code you consider safe is generated.</span></span>  
  
 <span data-ttu-id="c2f6d-106">Je potřeba přesně zjistit, co kód vygenerujete za všech okolností.</span><span class="sxs-lookup"><span data-stu-id="c2f6d-106">You need to know exactly what code you are generating at all times.</span></span> <span data-ttu-id="c2f6d-107">To znamená, že musíte mít přísné ovládací prvky pro všechny hodnoty, které obdržíte od uživatele, jako řetězce v uvozovkách (které by měly být uvozeny řídicími znaky), identifikátory (které by měly být zkontrolovány, abyste ověřili, že jsou platné. identifikátory) nebo cokoli jiného.</span><span class="sxs-lookup"><span data-stu-id="c2f6d-107">This means that you must have strict controls on any values that you get from a user, be they quote-enclosed strings (which should be escaped so they cannot include unexpected code elements), identifiers (which should be checked to verify that they are valid identifiers), or anything else.</span></span> <span data-ttu-id="c2f6d-108">Identifikátory mohou být nebezpečné, protože zkompilované sestavení lze upravit tak, aby jeho identifikátory obsahovaly nezvyklé znaky, což bude pravděpodobně přerušeno (i když se jedná o vzácnou chybu zabezpečení).</span><span class="sxs-lookup"><span data-stu-id="c2f6d-108">Identifiers can be dangerous because a compiled assembly can be modified so that its identifiers contain strange characters, which will probably break it (although this is rarely a security vulnerability).</span></span>  
  
 <span data-ttu-id="c2f6d-109">Doporučujeme, abyste vygenerovali kód s vygenerováním reflexe, což často pomáhá vyhnout se mnohé z těchto problémů.</span><span class="sxs-lookup"><span data-stu-id="c2f6d-109">It is recommended that you generate code with reflection emit, which often helps you avoid many of these problems.</span></span>  
  
 <span data-ttu-id="c2f6d-110">Při kompilování kódu zvažte, zda existuje nějaký způsob, jak škodlivý program upravit.</span><span class="sxs-lookup"><span data-stu-id="c2f6d-110">When you compile the code, consider whether there is some way a malicious program could modify it.</span></span> <span data-ttu-id="c2f6d-111">Existuje malé okno času, během kterého škodlivý kód může změnit zdrojový kód na disku před tím, než ho kompilátor přečte nebo před tím, než kód načte soubor. dll?</span><span class="sxs-lookup"><span data-stu-id="c2f6d-111">Is there a small window of time during which malicious code can change source code on disk before the compiler reads it or before your code loads the .dll file?</span></span> <span data-ttu-id="c2f6d-112">V takovém případě je nutné chránit adresář obsahující tyto soubory pomocí seznamu Access Control v systému souborů podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="c2f6d-112">If so, you must protect the directory containing these files, using an Access Control List in the file system, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2f6d-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2f6d-113">See also</span></span>

- [<span data-ttu-id="c2f6d-114">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="c2f6d-114">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
