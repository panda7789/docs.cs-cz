---
title: "Zabezpečení a průběžné vytváření kódu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code security, on-the-fly code generation
- on-the-fly code generation
- security [.NET Framework], on-the-fly code generation
- secure coding, on-the-fly code generation
ms.assetid: 6d221724-bb21-4d76-90c3-0ee2a2e69be2
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c00c66be812f2a1cdfdf761f681d2a0561a284bf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="security-and-on-the-fly-code-generation"></a><span data-ttu-id="d5062-102">Zabezpečení a průběžné vytváření kódu</span><span class="sxs-lookup"><span data-stu-id="d5062-102">Security and On-the-Fly Code Generation</span></span>
<span data-ttu-id="d5062-103">Některé knihovny fungují pomocí generování kódu a spustit a provést nějaké operace pro volajícího.</span><span class="sxs-lookup"><span data-stu-id="d5062-103">Some libraries operate by generating code and running it to perform some operation for the caller.</span></span> <span data-ttu-id="d5062-104">Základní problém generování kódu jménem kódu nižší úrovně důvěryhodnosti a spuštěná na vyšší vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="d5062-104">The basic problem is generating code on behalf of lesser-trust code and running it at a higher trust.</span></span> <span data-ttu-id="d5062-105">Problém se zhoršuje, když volající může ovlivnit generování kódu, proto musíte zajistit, že je vygenerováno, pouze kód, které považujete za bezpečná.</span><span class="sxs-lookup"><span data-stu-id="d5062-105">The problem worsens when the caller can influence code generation, so you must ensure that only code you consider safe is generated.</span></span>  
  
 <span data-ttu-id="d5062-106">Je třeba vědět, přesně jaký kód generují za všech okolností.</span><span class="sxs-lookup"><span data-stu-id="d5062-106">You need to know exactly what code you are generating at all times.</span></span> <span data-ttu-id="d5062-107">To znamená, že je nutné mít přísné ovládacích prvků na všechny hodnoty, které jste získali od uživatele, mohou to být řetězce uzavřené v uvozovkách, (které by měly být ukončeny, takže nemůžou zahrnovat neočekávané prvky kódu), identifikátory (které by měly být zkontrolovány ověřte, zda jsou platná identifikátorů), nebo cokoliv jiného.</span><span class="sxs-lookup"><span data-stu-id="d5062-107">This means that you must have strict controls on any values that you get from a user, be they quote-enclosed strings (which should be escaped so they cannot include unexpected code elements), identifiers (which should be checked to verify that they are valid identifiers), or anything else.</span></span> <span data-ttu-id="d5062-108">Identifikátory může být nebezpečné, protože kompilované sestavení můžete upravit tak, aby jeho identifikátory obsahovat neobvyklé znaky, které bude pravděpodobně ho rozdělit (i když je zřídka chybu zabezpečení).</span><span class="sxs-lookup"><span data-stu-id="d5062-108">Identifiers can be dangerous because a compiled assembly can be modified so that its identifiers contain strange characters, which will probably break it (although this is rarely a security vulnerability).</span></span>  
  
 <span data-ttu-id="d5062-109">Doporučujeme, abyste generovali kód pomocí reflexe emitování, což často umožňuje vyhnout se mnoho z těchto problémů.</span><span class="sxs-lookup"><span data-stu-id="d5062-109">It is recommended that you generate code with reflection emit, which often helps you avoid many of these problems.</span></span>  
  
 <span data-ttu-id="d5062-110">Při kompilaci kódu zvažte, zda je nějakým způsobem škodlivý program se může změnit.</span><span class="sxs-lookup"><span data-stu-id="d5062-110">When you compile the code, consider whether there is some way a malicious program could modify it.</span></span> <span data-ttu-id="d5062-111">Je k dispozici krátké době, během které škodlivý kód změnit zdrojový kód na disku, než ho kompilátor přečte nebo před kódu souboru .dll?</span><span class="sxs-lookup"><span data-stu-id="d5062-111">Is there a small window of time during which malicious code can change source code on disk before the compiler reads it or before your code loads the .dll file?</span></span> <span data-ttu-id="d5062-112">Pokud ano, je nutné chránit adresář obsahující tyto soubory použít seznam řízení přístupu v systému souborů, podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="d5062-112">If so, you must protect the directory containing these files, using an Access Control List in the file system, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5062-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5062-113">See Also</span></span>  
 [<span data-ttu-id="d5062-114">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="d5062-114">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
