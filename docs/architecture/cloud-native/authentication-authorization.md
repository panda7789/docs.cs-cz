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
# <a name="authentication-and-authorization-in-cloud-native-apps"></a>Ověřování a autorizace v aplikacích nativních pro cloud

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

*Ověřování* je proces určení identity objektu zabezpečení. *Autorizace* je akt udělení ověřeného hlavního uživatele oprávnění k provedení akce nebo přístupu k prostředku. Někdy je ověřování `AuthN` zkráceno na a `AuthZ`autorizace se zkrátí na . Cloudové nativní aplikace se musí spoléhat na otevřené protokoly založené na protokolu HTTP k ověření objektů zabezpečení, protože klienti i aplikace mohou být spuštěny kdekoli na světě na libovolné platformě nebo zařízení. Jediným společným faktorem je HTTP.

Mnoho organizací stále spoléhá na místní ověřovací služby, jako je služba ADFS (Active Directory Federation Services). Zatímco tento přístup tradičně sloužil organizacím dobře pro místní potřeby ověřování, aplikace nativní pro cloud těží ze systémů navržených speciálně pro cloud. Nedávný 2019 United Kingdom National Security Centre (NCSC) poradní uvádí, že "organizace, které používají Azure AD jako jejich primární zdroj ověřování bude ve skutečnosti snížit své riziko ve srovnání s ADFS." Některé důvody uvedené v [této analýze](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/) patří:

- Přístup k úplné sadě technologií ochrany přihlašovacích údajů společnosti Microsoft.
- Většina organizací se už do jisté míry spoléhá na Azure AD.
- Dvojité zahashování hash NTLM zajišťuje ohrožení zabezpečení nepovolí pověření, která fungují v místní službě Active Directory.

## <a name="references"></a>Odkazy

- [Základy ověřování](https://docs.microsoft.com/azure/active-directory/develop/authentication-scenarios)
- [Přístupové tokeny a deklarace identity](https://docs.microsoft.com/azure/active-directory/develop/access-tokens)
- [Možná je čas zbavit se místních ověřovacích služeb.](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/)

>[!div class="step-by-step"]
>[Předchozí](identity.md)
>[další](azure-active-directory.md)
