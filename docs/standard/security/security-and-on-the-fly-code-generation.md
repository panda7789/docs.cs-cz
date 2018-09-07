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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ffb1081c80c31353ad38080ae16ef9f8a74b5481
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44046772"
---
# <a name="security-and-on-the-fly-code-generation"></a><span data-ttu-id="9a91f-102">Zabezpečení a průběžné vytváření kódu</span><span class="sxs-lookup"><span data-stu-id="9a91f-102">Security and On-the-Fly Code Generation</span></span>
<span data-ttu-id="9a91f-103">Některé knihovny fungují tak, že generování kódu a spouštěním provádět některé operace pro volajícího.</span><span class="sxs-lookup"><span data-stu-id="9a91f-103">Some libraries operate by generating code and running it to perform some operation for the caller.</span></span> <span data-ttu-id="9a91f-104">Základní problém je generování kódu jménem nižší úrovně důvěryhodnosti kódu a běží na vyšší vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="9a91f-104">The basic problem is generating code on behalf of lesser-trust code and running it at a higher trust.</span></span> <span data-ttu-id="9a91f-105">Problém se zhoršuje, když volající může ovlivnit generování kódu, proto musíte zajistit, že je vygenerována pouze kód, které považujete za bezpečný.</span><span class="sxs-lookup"><span data-stu-id="9a91f-105">The problem worsens when the caller can influence code generation, so you must ensure that only code you consider safe is generated.</span></span>  
  
 <span data-ttu-id="9a91f-106">Je potřeba vědět, přesně jaký kód generují po celou dobu.</span><span class="sxs-lookup"><span data-stu-id="9a91f-106">You need to know exactly what code you are generating at all times.</span></span> <span data-ttu-id="9a91f-107">To znamená, že musí mít přísné ovládacích prvků na všechny hodnoty, které jste získali od uživatele, mohou to být uzavřené v uvozovkách řetězce, (které by měl být uvozen řídicími znaky, takže nemůžou obsahovat prvky neočekávaný kód), identifikátory (které by měly být porovnány k ověření, že jsou platné identifikátory), nebo cokoli jiného.</span><span class="sxs-lookup"><span data-stu-id="9a91f-107">This means that you must have strict controls on any values that you get from a user, be they quote-enclosed strings (which should be escaped so they cannot include unexpected code elements), identifiers (which should be checked to verify that they are valid identifiers), or anything else.</span></span> <span data-ttu-id="9a91f-108">Identifikátory mohou být nebezpečné, protože zkompilovaného sestavení lze upravit tak, aby jeho identifikátory obsahují zvláštní znaky, které budou pravděpodobně ho rozdělit (i když je zřídka ohrožení zabezpečení).</span><span class="sxs-lookup"><span data-stu-id="9a91f-108">Identifiers can be dangerous because a compiled assembly can be modified so that its identifiers contain strange characters, which will probably break it (although this is rarely a security vulnerability).</span></span>  
  
 <span data-ttu-id="9a91f-109">Doporučuje se, že generování kódu pomocí reflexe generování, které často umožňuje vyhnout se mnohé z těchto problémů.</span><span class="sxs-lookup"><span data-stu-id="9a91f-109">It is recommended that you generate code with reflection emit, which often helps you avoid many of these problems.</span></span>  
  
 <span data-ttu-id="9a91f-110">Při kompilaci kódu, zvažte, zda je nějakým způsobem ho změnit škodlivý program.</span><span class="sxs-lookup"><span data-stu-id="9a91f-110">When you compile the code, consider whether there is some way a malicious program could modify it.</span></span> <span data-ttu-id="9a91f-111">Existuje krátké období, během které škodlivý kód může změnit zdrojový kód na disku před kompilátor přečte nebo před kódu načte soubor .dll?</span><span class="sxs-lookup"><span data-stu-id="9a91f-111">Is there a small window of time during which malicious code can change source code on disk before the compiler reads it or before your code loads the .dll file?</span></span> <span data-ttu-id="9a91f-112">Pokud ano, je nutné chránit adresáře, který obsahuje tyto soubory použít seznam řízení přístupu v systému souborů, podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="9a91f-112">If so, you must protect the directory containing these files, using an Access Control List in the file system, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a91f-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9a91f-113">See also</span></span>

- [<span data-ttu-id="9a91f-114">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="9a91f-114">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
