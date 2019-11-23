---
title: Identita
description: Architekt cloudových nativních aplikací .NET pro Azure | Odcizen
ms.date: 09/23/2019
ms.openlocfilehash: 4cc7c04bf323d2589777df466321f6801f511b6f
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183047"
---
# <a name="identity"></a>Identita

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Většina softwarových aplikací musí mít znalosti uživatele nebo procesu, který je volá. Uživatel nebo proces, který interakci s aplikací, je známý jako objekt zabezpečení a proces ověřování a autorizace těchto objektů zabezpečení se označuje jako Správa identit, nebo jen *Identita*. Jednoduché aplikace můžou zahrnovat veškerou správu identit v rámci aplikace, ale tento přístup se nedokáže dobře škálovat u mnoha aplikací a mnoha druhů objektů zabezpečení. Systém Windows podporuje používání služby Active Directory k zajištění centralizovaného ověřování a autorizace.

<!-- (insert figure showing Windows AD auth model) -->

I když toto řešení platí v rámci podnikových sítí, není navržené pro uživatele nebo aplikace, které jsou mimo doménu služby AD. S růstem internetových aplikací a rostoucím počtem aplikací pro Cloud Native se vyvinuly modely zabezpečení.

V dnešním cloudově nativním modelu identity se předpokládá, že je architektura distribuována. Aplikace se dají nasadit kdekoli a můžou komunikovat s jinými aplikacemi odkudkoli. Klienti můžou s těmito aplikacemi komunikovat odkudkoli a ve skutečnosti se klienti mohou skládat z jakékoli kombinace platforem a zařízení. Řešení identity nativní pro Cloud využívají otevřené standardy k zajištění zabezpečeného přístupu k aplikacím od klientů. Tito klienti jsou v rozsahu od lidských uživatelů na počítačích nebo na telefonech k dalším aplikacím hostovaným kdekoli online, k nastavením horních polí a zařízení IOT, na kterých běží jakákoli softwarová platforma kdekoli na světě.

Moderní cloudová řešení identit obvykle využívají přístupové tokeny, které jsou vydány službou Secure token Service nebo serverem (STS) k objektu zabezpečení, jakmile je jejich identita určena. Přístupový token, typicky JSON Web Token (JWT), zahrnuje *deklarace identity* objektu zabezpečení. Tyto deklarace budou minimálně zahrnovat identitu uživatele, ale můžou zahrnovat i další deklarace identity, které můžou aplikace použít k určení úrovně přístupu k udělení objektu zabezpečení.

<!-- (insert figure showing basic handshake involving a principal, an STS, and an app) -->

Služba STS obvykle zodpovídá jenom za ověřování objektu zabezpečení. Určení jejich úrovně přístupu k prostředkům je ponecháno i v ostatních částech aplikace.

## <a name="references"></a>Reference

- [Platforma Microsoft identity](https://docs.microsoft.com/azure/active-directory/develop/)

>[!div class="step-by-step"]
>[Předchozí](azure-monitor.md)
>[Další](authentication-authorization.md)
