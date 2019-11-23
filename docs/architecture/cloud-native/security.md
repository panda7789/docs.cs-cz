---
title: Zabezpečení
description: Architekt cloudových nativních aplikací .NET pro Azure | Bezpečnost
ms.date: 06/30/2019
ms.openlocfilehash: 848255de70038798417a558543d0b1ea8cff1e37
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184769"
---
# <a name="security"></a><span data-ttu-id="e0610-103">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e0610-103">Security</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="e0610-104">Nejedná se o den, kdy zprávy neobsahují nějaký příběh o napadené společnosti, nebo nějakým způsobem ztrácí data zákazníků.</span><span class="sxs-lookup"><span data-stu-id="e0610-104">Not a day goes by where the news doesn't contain some story about a company being hacked or somehow losing their customers' data.</span></span> <span data-ttu-id="e0610-105">Dokonce i země nejsou odolné vůči problémům vytvořeným v zabezpečení jako dodatečně.</span><span class="sxs-lookup"><span data-stu-id="e0610-105">Even countries aren't immune to the problems created by treating security as an afterthought.</span></span> <span data-ttu-id="e0610-106">V letech byly společnosti ošetřené zabezpečení zákaznických dat a ve skutečnosti i jejich celé sítě jako "Skvělé".</span><span class="sxs-lookup"><span data-stu-id="e0610-106">For years, companies have treated the security of customer data and, in fact, their entire networks as something of a "nice to have".</span></span> <span data-ttu-id="e0610-107">Windows servery zůstaly neopravené, Ancient verze PHP zůstaly spuštěné a MongoDB databáze zůstanou otevřené na světě.</span><span class="sxs-lookup"><span data-stu-id="e0610-107">Windows servers were left unpatched, ancient versions of PHP kept running and MongoDB databases left wide open to the world.</span></span>

<span data-ttu-id="e0610-108">Existují však reálné důsledky, které neudržují místo zabezpečení při sestavování a nasazování aplikací.</span><span class="sxs-lookup"><span data-stu-id="e0610-108">However, there are starting to be real-world consequences for not maintaining a security mindset when building and deploying applications.</span></span> <span data-ttu-id="e0610-109">Řada společností se dozvěděla o tvrdých způsobech, které se mohou vyskytnout, když servery a desktopy nejsou opraveny během 2017 [NotPetya](https://www.wired.com/story/notpetya-cyberattack-ukraine-russia-code-crashed-the-world/).</span><span class="sxs-lookup"><span data-stu-id="e0610-109">Many companies learned the hard way what can happen when servers and desktops aren't patched during the 2017 outbreak of [NotPetya](https://www.wired.com/story/notpetya-cyberattack-ukraine-russia-code-crashed-the-world/).</span></span> <span data-ttu-id="e0610-110">Náklady na tyto útoky byly snadno dostupné v miliardách, přičemž některé odhady obsahují ztráty z tohoto jednoho útoku v 10 000 000 000 amerických dolarech.</span><span class="sxs-lookup"><span data-stu-id="e0610-110">The cost of these attacks has easily reached into the billions, with some estimates putting the losses from this single attack at 10 billion US dollars.</span></span>

<span data-ttu-id="e0610-111">I vlády nejsou odolné vůči incidentům hackerů.</span><span class="sxs-lookup"><span data-stu-id="e0610-111">Even governments aren't immune to hacking incidents.</span></span> <span data-ttu-id="e0610-112">Město Baltimore bylo držitelem Ransom [, což znemožňuje, aby občané](https://www.vox.com/recode/2019/5/21/18634505/baltimore-ransom-robbinhood-mayor-jack-young-hackers) zaplatili své účty nebo používaly služby měst.</span><span class="sxs-lookup"><span data-stu-id="e0610-112">The city of Baltimore was held ransom by [criminals](https://www.vox.com/recode/2019/5/21/18634505/baltimore-ransom-robbinhood-mayor-jack-young-hackers) making it impossible for citizens to pay their bills or use city services.</span></span>

<span data-ttu-id="e0610-113">Došlo také ke zvýšení právních předpisů, které zmocňuje určitá ochrana dat pro osobní údaje.</span><span class="sxs-lookup"><span data-stu-id="e0610-113">There has also been an increase in legislation that mandates certain data protections for personal data.</span></span> <span data-ttu-id="e0610-114">V Evropě byl GDPR v platnost po dobu delší než 1 rok a v poslední době v Kalifornii prošla vlastní verzí nazvanou CCDA, která vstoupí v platnost 1. ledna 2020.</span><span class="sxs-lookup"><span data-stu-id="e0610-114">In Europe, GDPR has been in effect for more than a year and, more recently, California passed their own version called CCDA, which comes into effect January 1, 2020.</span></span> <span data-ttu-id="e0610-115">Tato pokuta v rámci GDPR můžou být tak, aby se z nich mohla podávat společnosti za firmy.</span><span class="sxs-lookup"><span data-stu-id="e0610-115">The fines under GDPR can be so punishing as to put companies out of business.</span></span> <span data-ttu-id="e0610-116">Google už bylo pro porušení 50 000 000 EUR. to je v porovnání s potenciálními pokutami jenom v intervalu.</span><span class="sxs-lookup"><span data-stu-id="e0610-116">Google has already been fined 50 million Euros for violations, but that's just a drop in the bucket compared with the potential fines.</span></span>

<span data-ttu-id="e0610-117">V krátkém případě je zabezpečení vážným podnikáním.</span><span class="sxs-lookup"><span data-stu-id="e0610-117">In short, security is serious business.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e0610-118">[Předchozí](identity-server.md)
>[Další](azure-security.md)</span><span class="sxs-lookup"><span data-stu-id="e0610-118">[Previous](identity-server.md)
[Next](azure-security.md)</span></span>
