---
title: Síťové přerušující změny
description: Obsahuje seznam nejnovějších změn v sítích .NET Core.
ms.date: 05/05/2020
ms.openlocfilehash: 568d26bde43ccd6e19fbe2d947f576ef5f99450a
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608463"
---
# <a name="networking-breaking-changes"></a>Síťové přerušující změny

Na této stránce jsou popsány následující přerušující se změny:

| Zásadní změna | Představená verze |
| - | - |
| [WinHttpHandler odebrané z modulu runtime .NET](#winhttphandler-removed-from-net-runtime) | 5.0 |
| [MulticastOption. Group nepřijímá hodnotu null.](#multicastoptiongroup-doesnt-accept-a-null-value) | 5.0 |
| [Výchozí hodnota zprávy HttpRequestMessage. Version se změnila na 1,1.](#default-value-of-httprequestmessageversion-changed-to-11) | 3.0 |
| [WebClient. CancelAsync nevždycky zruší hned](#webclientcancelasync-doesnt-always-cancel-immediately) | 2.0 |

## <a name="net-50"></a>.NET 5,0

[!INCLUDE [winhttphandler-removed-from-runtime](../../../includes/core-changes/networking/5.0/winhttphandler-removed-from-runtime.md)]

***

[!INCLUDE [multicastoption-group-doesnt-accept-null](../../../includes/core-changes/networking/5.0/multicastoption-group-doesnt-accept-null.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[Default value of HttpRequestMessage.Version changed to 1.1](~/includes/core-changes/networking/3.0/httprequestmessage-version-change.md)]

***

## <a name="net-core-20"></a>.NET Core 2.0

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***
