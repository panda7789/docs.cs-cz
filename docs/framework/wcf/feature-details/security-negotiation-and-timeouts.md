---
title: Vyjednávání a časové limity zabezpečení
ms.date: 03/30/2017
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
ms.openlocfilehash: 1b5fb15b4ea00ba33b741c96bcb423aefe9890fa
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600994"
---
# <a name="security-negotiation-and-timeouts"></a>Vyjednávání a časové limity zabezpečení
Když klienti a služby ověřují, Windows Communication Foundation (WCF) podporuje režim, ve kterém je pověření služby vyjednáno jako součást ověřování. V takových scénářích dojde k nenáročnému Exchangi mezi klientem a službou, aby bylo možné rozšířit pověření služby na klienta. <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A>Vlastnost určuje dobu, po kterou může trvat vícenásobné výměny ramen. Tento časový limit se však vztahuje pouze v případě, že výměna ve skutečnosti trvá více, než jedna odpověď na požadavek. V případech, kdy se vyjednávání dokončí v jedné operaci odezvy, se nepoužije časový limit.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [Postupy: Nastavení hodnoty vlastnosti MaxClockSkew](how-to-set-a-max-clock-skew.md)
