---
title: Návrh aplikací Dockeru
description: Tady najít odkaz na podrobné příručce k architektuře mikroslužeb, protože se na téma, který není podrobně popsané v této příručce.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 858147883b3b4a5a5f487856028fdbfa84f6cca9
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675183"
---
# <a name="design-docker-applications"></a>Návrh aplikací Dockeru

Kapitoly 1 jsme zavedli základní koncepty týkající se kontejnerů a Dockeru. Tyto informace je základní úroveň informací, které potřebujete, abyste mohli začít. Ale podnikových aplikací mohou být složité a skládá z několika služeb namísto jedné služby nebo kontejneru. Pro tyto případy použití volitelné je potřeba vědět další přístupy k návrhu, jako je architektura Service-Oriented (SOA) a pokročilejší koncepty mikroslužeb a kontejnerů koncepty Orchestrace. Rámec tohoto dokumentu se neomezuje na mikroslužby ale do jakékoli Docker aplikace životního cyklu, proto ho není prozkoumat architektury mikroslužeb do hloubky protože také můžete použít kontejnerům a Dockeru s regulární SOA, úlohy na pozadí nebo úlohy, nebo dokonce i s monolitickými aplikacemi způsoby nasazení.

**Další informace o** Další informace o podnikové aplikace a architekturu mikroslužeb do hloubky, přečtěte si příručku [NET Mikroslužeb: Architektura pro Kontejnerizovaných aplikací .NET](https://docs.microsoft.com/dotnet/standard/microservices-architecture) , který si můžete stáhnout také z <https://aka.ms/MicroservicesEbook>.

Ale předtím, než se dostaneme k životního cyklu aplikace a DevOps, je důležité vědět, jak budete k návrhu a sestavování vaší aplikace a jaké jsou vaše volby při návrhu.

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](common-container-design-principles.md)
