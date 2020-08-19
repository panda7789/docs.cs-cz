---
title: Síťové přerušující změny
description: Obsahuje seznam nejnovějších změn v sítích .NET Core.
ms.date: 05/05/2020
ms.openlocfilehash: 5d27f9663a2c1b79610ab002a03beeafa8b2818e
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557958"
---
# <a name="networking-breaking-changes"></a>Síťové přerušující změny

Na této stránce jsou popsány následující přerušující se změny:

| Zásadní změna | Představená verze |
| - | - |
| [MulticastOption. Group nepřijímá hodnotu null.](#multicastoptiongroup-doesnt-accept-a-null-value) | 5.0 |
| [Výchozí hodnota zprávy HttpRequestMessage. Version se změnila na 1,1.](#default-value-of-httprequestmessageversion-changed-to-11) | 3.0 |
| [WebClient. CancelAsync nevždycky zruší hned](#webclientcancelasync-doesnt-always-cancel-immediately) | 2.0 |

## <a name="net-50"></a>.NET 5,0

[!INCLUDE [multicastoption-group-doesnt-accept-null](../../../includes/core-changes/networking/5.0/multicastoption-group-doesnt-accept-null.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[Default value of HttpRequestMessage.Version changed to 1.1](~/includes/core-changes/networking/3.0/httprequestmessage-version-change.md)]

***

## <a name="net-core-20"></a>.NET Core 2.0

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***
