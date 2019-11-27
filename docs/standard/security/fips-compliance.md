---
title: Dodržování standardu FIPS – .NET Core
description: Vysvětluje dodržování předpisů standardu FIPS (Federal Information Processing Standard) .NET Core.
ms.date: 11/20/2019
author: Rick-Anderson
ms.author: riande
ms.openlocfilehash: cf640c857e79ae811dd38d57a0e5301b7bc96572
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74205064"
---
# <a name="net-core-federal-information-processing-standard-fips-compliance"></a><span data-ttu-id="9b291-103">Kompatibilita standardu FIPS (Federal Information Processing Standard) .NET Core</span><span class="sxs-lookup"><span data-stu-id="9b291-103">.NET Core Federal Information Processing Standard (FIPS) compliance</span></span>

<span data-ttu-id="9b291-104">Publikace standardu FIPS (Federal Information Processing Standard) 140-2 je standard pro státní správu USA, který definuje minimální požadavky na zabezpečení pro kryptografické moduly v produktech informačních technologií, jak je definováno v části 5131 těchto informací. Reforma správy technologických aktů 1996.</span><span class="sxs-lookup"><span data-stu-id="9b291-104">The Federal Information Processing Standard (FIPS) Publication 140-2 is a U.S. government standard that defines minimum security requirements for cryptographic modules in information technology products, as defined in Section 5131 of the Information Technology Management Reform Act of 1996.</span></span>

<span data-ttu-id="9b291-105">.NET Core:</span><span class="sxs-lookup"><span data-stu-id="9b291-105">.NET Core:</span></span>

* <span data-ttu-id="9b291-106">Předá kryptografická primitiva volání ke standardním modulům, které poskytuje základní operační systém.</span><span class="sxs-lookup"><span data-stu-id="9b291-106">Passes cryptographic primitives calls through to the standard modules the underlying operating system provides.</span></span>
* <span data-ttu-id="9b291-107">Nevynutil **použití** algoritmů SCHVÁLENÉho standardem FIPS ani velikostí klíčů v aplikacích .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9b291-107">Does **not** enforce the use of FIPS Approved algorithms or key sizes in .NET Core apps.</span></span>

<span data-ttu-id="9b291-108">Správce systému zodpovídá za konfiguraci dodržování standardů FIPS pro operační systém.</span><span class="sxs-lookup"><span data-stu-id="9b291-108">The system administrator is responsible for configuring the FIPS compliance for an operating system.</span></span>

<span data-ttu-id="9b291-109">Pokud je kód napsán pro prostředí kompatibilní se standardem FIPS, vývojář zodpovídá za to, že nepoužívají nekompatibilní algoritmy FIPS.</span><span class="sxs-lookup"><span data-stu-id="9b291-109">If code is written for a FIPS-compliant environment, the developer is responsible for ensuring that non-compliant FIPS algorithms aren't used.</span></span>

<span data-ttu-id="9b291-110">Další informace o dodržování standardu FIPS najdete v následujících článcích:</span><span class="sxs-lookup"><span data-stu-id="9b291-110">For more information on FIPS compliance, see the following articles:</span></span>

* [<span data-ttu-id="9b291-111">Dodržování předpisů FIPS Windows</span><span class="sxs-lookup"><span data-stu-id="9b291-111">Windows FIPS Compliance</span></span>](/windows/security/threat-protection/fips-140-validation)
* [<span data-ttu-id="9b291-112">Konfigurace Windows pro dodržování standardu FIPS</span><span class="sxs-lookup"><span data-stu-id="9b291-112">Configuring Windows for FIPS Compliance</span></span>](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)
* [<span data-ttu-id="9b291-113">10,2. STANDARD FIPS (FEDERAL INFORMATION PROCESSING STANDARD)</span><span class="sxs-lookup"><span data-stu-id="9b291-113">10.2. FEDERAL INFORMATION PROCESSING STANDARD (FIPS)</span></span>](https://access.redhat.com/documentation/red_hat_enterprise_linux/6/html/security_guide/sect-security_guide-federal_standards_and_regulations-federal_information_processing_standard)
