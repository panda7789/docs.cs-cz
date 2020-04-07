---
title: Ověřování a autorizace v aplikacích nativních pro cloud
description: Navrhování cloudových nativních aplikací .NET pro Azure | Ověřování a autorizace v nativních aplikacích cloudu
ms.date: 03/02/2020
ms.openlocfilehash: 6261a0a72405bc1c984a04a7851aea4dd6664ddf
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805553"
---
# <a name="authentication-and-authorization-in-cloud-native-apps"></a><span data-ttu-id="e96c2-103">Ověřování a autorizace v aplikacích nativních pro cloud</span><span class="sxs-lookup"><span data-stu-id="e96c2-103">Authentication and authorization in cloud-native apps</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="e96c2-104">*Ověřování* je proces určení identity objektu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e96c2-104">*Authentication* is the process of determining the identity of a security principal.</span></span> <span data-ttu-id="e96c2-105">*Autorizace* je akt udělení ověřeného hlavního uživatele oprávnění k provedení akce nebo přístupu k prostředku.</span><span class="sxs-lookup"><span data-stu-id="e96c2-105">*Authorization* is the act of granting an authenticated principal permission to perform an action or access a resource.</span></span> <span data-ttu-id="e96c2-106">Někdy je ověřování `AuthN` zkráceno na a `AuthZ`autorizace se zkrátí na .</span><span class="sxs-lookup"><span data-stu-id="e96c2-106">Sometimes authentication is shortened to `AuthN` and authorization is shortened to `AuthZ`.</span></span> <span data-ttu-id="e96c2-107">Cloudové nativní aplikace se musí spoléhat na otevřené protokoly založené na protokolu HTTP k ověření objektů zabezpečení, protože klienti i aplikace mohou být spuštěny kdekoli na světě na libovolné platformě nebo zařízení.</span><span class="sxs-lookup"><span data-stu-id="e96c2-107">Cloud-native applications need to rely on open HTTP-based protocols to authenticate security principals since both clients and applications could be running anywhere in the world on any platform or device.</span></span> <span data-ttu-id="e96c2-108">Jediným společným faktorem je HTTP.</span><span class="sxs-lookup"><span data-stu-id="e96c2-108">The only common factor is HTTP.</span></span>

<span data-ttu-id="e96c2-109">Mnoho organizací stále spoléhá na místní ověřovací služby, jako je služba ADFS (Active Directory Federation Services).</span><span class="sxs-lookup"><span data-stu-id="e96c2-109">Many organizations still rely on local authentication services like Active Directory Federation Services (ADFS).</span></span> <span data-ttu-id="e96c2-110">Zatímco tento přístup tradičně sloužil organizacím dobře pro místní potřeby ověřování, aplikace nativní pro cloud těží ze systémů navržených speciálně pro cloud.</span><span class="sxs-lookup"><span data-stu-id="e96c2-110">While this approach has traditionally served organizations well for on premises authentication needs, cloud-native applications benefit from systems designed specifically for the cloud.</span></span> <span data-ttu-id="e96c2-111">Nedávný 2019 United Kingdom National Security Centre (NCSC) poradní uvádí, že "organizace, které používají Azure AD jako jejich primární zdroj ověřování bude ve skutečnosti snížit své riziko ve srovnání s ADFS."</span><span class="sxs-lookup"><span data-stu-id="e96c2-111">A recent 2019 United Kingdom National Cyber Security Centre (NCSC) advisory states that "organizations using Azure AD as their primary authentication source will actually lower their risk compared to ADFS."</span></span> <span data-ttu-id="e96c2-112">Některé důvody uvedené v [této analýze](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/) patří:</span><span class="sxs-lookup"><span data-stu-id="e96c2-112">Some reasons outlined in [this analysis](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/) include:</span></span>

- <span data-ttu-id="e96c2-113">Přístup k úplné sadě technologií ochrany přihlašovacích údajů společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e96c2-113">Access to full set of Microsoft credential protection technologies.</span></span>
- <span data-ttu-id="e96c2-114">Většina organizací se už do jisté míry spoléhá na Azure AD.</span><span class="sxs-lookup"><span data-stu-id="e96c2-114">Most organizations are already relying on Azure AD to some extent.</span></span>
- <span data-ttu-id="e96c2-115">Dvojité zahashování hash NTLM zajišťuje ohrožení zabezpečení nepovolí pověření, která fungují v místní službě Active Directory.</span><span class="sxs-lookup"><span data-stu-id="e96c2-115">Double hashing of NTLM hashes ensures compromise won't allow credentials that work in local Active Directory.</span></span>

## <a name="references"></a><span data-ttu-id="e96c2-116">Odkazy</span><span class="sxs-lookup"><span data-stu-id="e96c2-116">References</span></span>

- [<span data-ttu-id="e96c2-117">Základy ověřování</span><span class="sxs-lookup"><span data-stu-id="e96c2-117">Authentication basics</span></span>](https://docs.microsoft.com/azure/active-directory/develop/authentication-scenarios)
- [<span data-ttu-id="e96c2-118">Přístupové tokeny a deklarace identity</span><span class="sxs-lookup"><span data-stu-id="e96c2-118">Access tokens and claims</span></span>](https://docs.microsoft.com/azure/active-directory/develop/access-tokens)
- [<span data-ttu-id="e96c2-119">Možná je čas zbavit se místních ověřovacích služeb.</span><span class="sxs-lookup"><span data-stu-id="e96c2-119">It may be time to ditch your on premises authentication services</span></span>](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/)

>[!div class="step-by-step"]
><span data-ttu-id="e96c2-120">[Předchozí](identity.md)
>[další](azure-active-directory.md)</span><span class="sxs-lookup"><span data-stu-id="e96c2-120">[Previous](identity.md)
[Next](azure-active-directory.md)</span></span>
