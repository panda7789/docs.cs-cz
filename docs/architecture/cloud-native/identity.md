---
title: Identita
description: Architekt cloudových nativních aplikací .NET pro Azure | Odcizen
ms.date: 05/13/2020
ms.openlocfilehash: 9fa48977e58e2ca5a5f3e231372a4791640a85fd
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614016"
---
# <a name="identity"></a>Identita

Většina softwarových aplikací musí mít znalosti uživatele nebo procesu, který je volá. Uživatel nebo proces, který interakci s aplikací, je známý jako objekt zabezpečení a proces ověřování a autorizace těchto objektů zabezpečení se označuje jako Správa identit, nebo jen *Identita*. Jednoduché aplikace můžou zahrnovat veškerou správu identit v rámci aplikace, ale tento přístup se nedokáže dobře škálovat u mnoha aplikací a mnoha druhů objektů zabezpečení. Systém Windows podporuje používání služby Active Directory k zajištění centralizovaného ověřování a autorizace.

<!-- (insert figure showing Windows AD auth model) -->

I když toto řešení platí v rámci podnikových sítí, není navržené pro uživatele nebo aplikace, které jsou mimo doménu služby AD. S růstem internetových aplikací a rostoucím počtem aplikací pro Cloud Native se vyvinuly modely zabezpečení.

V dnešním cloudově nativním modelu identity se předpokládá, že je architektura distribuována. Aplikace se dají nasadit kdekoli a můžou komunikovat s jinými aplikacemi odkudkoli. Klienti můžou s těmito aplikacemi komunikovat odkudkoli a ve skutečnosti se klienti mohou skládat z jakékoli kombinace platforem a zařízení. Řešení identity nativní pro Cloud využívají otevřené standardy k zajištění zabezpečeného přístupu k aplikacím od klientů. Tito klienti jsou v rozsahu od lidských uživatelů na počítačích nebo na telefonech k dalším aplikacím hostovaným kdekoli online, k nastavením horních polí a zařízení IOT, na kterých běží jakákoli softwarová platforma kdekoli na světě.

Moderní cloudová řešení identit obvykle využívají přístupové tokeny, které jsou vydány službou Secure token Service nebo serverem (STS) k objektu zabezpečení, jakmile je jejich identita určena. Přístupový token, typicky JSON Web Token (JWT), zahrnuje *deklarace identity* objektu zabezpečení. Tyto deklarace budou minimálně zahrnovat identitu uživatele, ale můžou zahrnovat i další deklarace identity, které můžou aplikace použít k určení úrovně přístupu k udělení objektu zabezpečení.

<!-- (insert figure showing basic handshake involving a principal, an STS, and an app) -->

Služba STS obvykle zodpovídá jenom za ověřování objektu zabezpečení. Určení jejich úrovně přístupu k prostředkům je ponecháno i v ostatních částech aplikace.

## <a name="references"></a>Odkazy

- [Microsoft identity platform](https://docs.microsoft.com/azure/active-directory/develop/)

>[!div class="step-by-step"]
>[Předchozí](azure-monitor.md) 
> [Další](authentication-authorization.md)
