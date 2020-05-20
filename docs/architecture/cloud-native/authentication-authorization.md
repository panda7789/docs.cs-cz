---
title: Ověřování a autorizace v cloudových nativních aplikacích
description: Architekt cloudových nativních aplikací .NET pro Azure | Ověřování a autorizace v cloudových nativních aplikacích
ms.date: 05/13/2020
ms.openlocfilehash: e5254560ac82662e5e3ea6a25997516cd2b478b0
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614302"
---
# <a name="authentication-and-authorization-in-cloud-native-apps"></a><span data-ttu-id="eb2eb-103">Ověřování a autorizace v aplikacích nativních pro cloud</span><span class="sxs-lookup"><span data-stu-id="eb2eb-103">Authentication and authorization in cloud-native apps</span></span>

<span data-ttu-id="eb2eb-104">*Ověřování* je proces určování identity objektu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="eb2eb-104">*Authentication* is the process of determining the identity of a security principal.</span></span> <span data-ttu-id="eb2eb-105">*Autorizace* je úkonem udělení ověřeného oprávnění zabezpečení k provedení akce nebo přístupu k prostředku.</span><span class="sxs-lookup"><span data-stu-id="eb2eb-105">*Authorization* is the act of granting an authenticated principal permission to perform an action or access a resource.</span></span> <span data-ttu-id="eb2eb-106">Někdy se ověřování zkracuje na `AuthN` a na se zkracuje autorizace `AuthZ` .</span><span class="sxs-lookup"><span data-stu-id="eb2eb-106">Sometimes authentication is shortened to `AuthN` and authorization is shortened to `AuthZ`.</span></span> <span data-ttu-id="eb2eb-107">Cloudové nativní aplikace musí při ověřování objektů zabezpečení spoléhat na otevřené protokoly založené na protokolu HTTP, protože klienti i aplikace můžou běžet kdekoli na světě na libovolné platformě nebo zařízení.</span><span class="sxs-lookup"><span data-stu-id="eb2eb-107">Cloud-native applications need to rely on open HTTP-based protocols to authenticate security principals since both clients and applications could be running anywhere in the world on any platform or device.</span></span> <span data-ttu-id="eb2eb-108">Jediným běžným faktorem je HTTP.</span><span class="sxs-lookup"><span data-stu-id="eb2eb-108">The only common factor is HTTP.</span></span>

<span data-ttu-id="eb2eb-109">Mnoho organizací stále spoléhá na místní ověřovací služby, jako je Active Directory Federation Services (AD FS) (ADFS).</span><span class="sxs-lookup"><span data-stu-id="eb2eb-109">Many organizations still rely on local authentication services like Active Directory Federation Services (ADFS).</span></span> <span data-ttu-id="eb2eb-110">I když tento přístup tradičně sloužil organizacím v místní potřebě ověřování, cloudové aplikace v nativním prostředí můžou využívat systémy navržené speciálně pro Cloud.</span><span class="sxs-lookup"><span data-stu-id="eb2eb-110">While this approach has traditionally served organizations well for on premises authentication needs, cloud-native applications benefit from systems designed specifically for the cloud.</span></span> <span data-ttu-id="eb2eb-111">V 2019 nedávném zpravodaji NCSC (National Internetal Security Center) se v porovnání se službou AD FS ve skutečnosti sníží riziko, že "organizace využívající Azure AD jako primární zdroj ověřování."</span><span class="sxs-lookup"><span data-stu-id="eb2eb-111">A recent 2019 United Kingdom National Cyber Security Centre (NCSC) advisory states that "organizations using Azure AD as their primary authentication source will actually lower their risk compared to ADFS."</span></span> <span data-ttu-id="eb2eb-112">Mezi důvody [uvedené v této analýze](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/) patří:</span><span class="sxs-lookup"><span data-stu-id="eb2eb-112">Some reasons outlined in [this analysis](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/) include:</span></span>

- <span data-ttu-id="eb2eb-113">Přístup k úplné sadě technologií ochrany přihlašovacích údajů společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="eb2eb-113">Access to full set of Microsoft credential protection technologies.</span></span>
- <span data-ttu-id="eb2eb-114">Většina organizací se už v některém rozsahu spoléhá na Azure AD.</span><span class="sxs-lookup"><span data-stu-id="eb2eb-114">Most organizations are already relying on Azure AD to some extent.</span></span>
- <span data-ttu-id="eb2eb-115">Dvojitá hodnota hash algoritmu hash protokolu NTLM zajišťuje ohrožení nepovoluje přihlašovací údaje, které fungují v místní službě Active Directory.</span><span class="sxs-lookup"><span data-stu-id="eb2eb-115">Double hashing of NTLM hashes ensures compromise won't allow credentials that work in local Active Directory.</span></span>

## <a name="references"></a><span data-ttu-id="eb2eb-116">Odkazy</span><span class="sxs-lookup"><span data-stu-id="eb2eb-116">References</span></span>

- [<span data-ttu-id="eb2eb-117">Základy ověřování</span><span class="sxs-lookup"><span data-stu-id="eb2eb-117">Authentication basics</span></span>](https://docs.microsoft.com/azure/active-directory/develop/authentication-scenarios)
- [<span data-ttu-id="eb2eb-118">Přístupové tokeny a deklarace identity</span><span class="sxs-lookup"><span data-stu-id="eb2eb-118">Access tokens and claims</span></span>](https://docs.microsoft.com/azure/active-directory/develop/access-tokens)
- [<span data-ttu-id="eb2eb-119">Může být čas na Ditch místních ověřovacích služeb.</span><span class="sxs-lookup"><span data-stu-id="eb2eb-119">It may be time to ditch your on premises authentication services</span></span>](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/)

>[!div class="step-by-step"]
><span data-ttu-id="eb2eb-120">[Předchozí](identity.md) 
> [Další](azure-active-directory.md)</span><span class="sxs-lookup"><span data-stu-id="eb2eb-120">[Previous](identity.md)
[Next](azure-active-directory.md)</span></span>
