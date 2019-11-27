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
# <a name="net-core-federal-information-processing-standard-fips-compliance"></a>Kompatibilita standardu FIPS (Federal Information Processing Standard) .NET Core

Publikace standardu FIPS (Federal Information Processing Standard) 140-2 je standard pro státní správu USA, který definuje minimální požadavky na zabezpečení pro kryptografické moduly v produktech informačních technologií, jak je definováno v části 5131 těchto informací. Reforma správy technologických aktů 1996.

.NET Core:

* Předá kryptografická primitiva volání ke standardním modulům, které poskytuje základní operační systém.
* Nevynutil **použití** algoritmů SCHVÁLENÉho standardem FIPS ani velikostí klíčů v aplikacích .NET Core.

Správce systému zodpovídá za konfiguraci dodržování standardů FIPS pro operační systém.

Pokud je kód napsán pro prostředí kompatibilní se standardem FIPS, vývojář zodpovídá za to, že nepoužívají nekompatibilní algoritmy FIPS.

Další informace o dodržování standardu FIPS najdete v následujících článcích:

* [Dodržování předpisů FIPS Windows](/windows/security/threat-protection/fips-140-validation)
* [Konfigurace Windows pro dodržování standardu FIPS](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)
* [10,2. STANDARD FIPS (FEDERAL INFORMATION PROCESSING STANDARD)](https://access.redhat.com/documentation/red_hat_enterprise_linux/6/html/security_guide/sect-security_guide-federal_standards_and_regulations-federal_information_processing_standard)
