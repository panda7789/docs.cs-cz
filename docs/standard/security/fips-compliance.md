---
title: Dodržování standardu FIPS – .NET Core
description: Vysvětluje dodržování předpisů standardu FIPS (Federal Information Processing Standard) .NET Core.
ms.date: 11/20/2019
author: Rick-Anderson
ms.author: riande
ms.openlocfilehash: 84d6edc6975af0484bb67999ad5891eaf4db057d
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626955"
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
* [Kapitola 8. Federální normy a předpisy Red Hat Enterprise Linux 7](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/security_guide/chap-federal_standards_and_regulations)
