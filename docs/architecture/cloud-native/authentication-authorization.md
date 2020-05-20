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
# <a name="authentication-and-authorization-in-cloud-native-apps"></a>Ověřování a autorizace v aplikacích nativních pro cloud

*Ověřování* je proces určování identity objektu zabezpečení. *Autorizace* je úkonem udělení ověřeného oprávnění zabezpečení k provedení akce nebo přístupu k prostředku. Někdy se ověřování zkracuje na `AuthN` a na se zkracuje autorizace `AuthZ` . Cloudové nativní aplikace musí při ověřování objektů zabezpečení spoléhat na otevřené protokoly založené na protokolu HTTP, protože klienti i aplikace můžou běžet kdekoli na světě na libovolné platformě nebo zařízení. Jediným běžným faktorem je HTTP.

Mnoho organizací stále spoléhá na místní ověřovací služby, jako je Active Directory Federation Services (AD FS) (ADFS). I když tento přístup tradičně sloužil organizacím v místní potřebě ověřování, cloudové aplikace v nativním prostředí můžou využívat systémy navržené speciálně pro Cloud. V 2019 nedávném zpravodaji NCSC (National Internetal Security Center) se v porovnání se službou AD FS ve skutečnosti sníží riziko, že "organizace využívající Azure AD jako primární zdroj ověřování." Mezi důvody [uvedené v této analýze](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/) patří:

- Přístup k úplné sadě technologií ochrany přihlašovacích údajů společnosti Microsoft.
- Většina organizací se už v některém rozsahu spoléhá na Azure AD.
- Dvojitá hodnota hash algoritmu hash protokolu NTLM zajišťuje ohrožení nepovoluje přihlašovací údaje, které fungují v místní službě Active Directory.

## <a name="references"></a>Odkazy

- [Základy ověřování](https://docs.microsoft.com/azure/active-directory/develop/authentication-scenarios)
- [Přístupové tokeny a deklarace identity](https://docs.microsoft.com/azure/active-directory/develop/access-tokens)
- [Může být čas na Ditch místních ověřovacích služeb.](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/)

>[!div class="step-by-step"]
>[Předchozí](identity.md) 
> [Další](azure-active-directory.md)
