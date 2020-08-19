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
# <a name="networking-breaking-changes"></a><span data-ttu-id="017fe-103">Síťové přerušující změny</span><span class="sxs-lookup"><span data-stu-id="017fe-103">Networking breaking changes</span></span>

<span data-ttu-id="017fe-104">Na této stránce jsou popsány následující přerušující se změny:</span><span class="sxs-lookup"><span data-stu-id="017fe-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="017fe-105">Zásadní změna</span><span class="sxs-lookup"><span data-stu-id="017fe-105">Breaking change</span></span> | <span data-ttu-id="017fe-106">Představená verze</span><span class="sxs-lookup"><span data-stu-id="017fe-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="017fe-107">MulticastOption. Group nepřijímá hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="017fe-107">MulticastOption.Group doesn't accept a null value</span></span>](#multicastoptiongroup-doesnt-accept-a-null-value) | <span data-ttu-id="017fe-108">5.0</span><span class="sxs-lookup"><span data-stu-id="017fe-108">5.0</span></span> |
| [<span data-ttu-id="017fe-109">Výchozí hodnota zprávy HttpRequestMessage. Version se změnila na 1,1.</span><span class="sxs-lookup"><span data-stu-id="017fe-109">Default value of HttpRequestMessage.Version changed to 1.1</span></span>](#default-value-of-httprequestmessageversion-changed-to-11) | <span data-ttu-id="017fe-110">3.0</span><span class="sxs-lookup"><span data-stu-id="017fe-110">3.0</span></span> |
| [<span data-ttu-id="017fe-111">WebClient. CancelAsync nevždycky zruší hned</span><span class="sxs-lookup"><span data-stu-id="017fe-111">WebClient.CancelAsync doesn't always cancel immediately</span></span>](#webclientcancelasync-doesnt-always-cancel-immediately) | <span data-ttu-id="017fe-112">2.0</span><span class="sxs-lookup"><span data-stu-id="017fe-112">2.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="017fe-113">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="017fe-113">.NET 5.0</span></span>

[!INCLUDE [multicastoption-group-doesnt-accept-null](../../../includes/core-changes/networking/5.0/multicastoption-group-doesnt-accept-null.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="017fe-114">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="017fe-114">.NET Core 3.0</span></span>

[!INCLUDE[Default value of HttpRequestMessage.Version changed to 1.1](~/includes/core-changes/networking/3.0/httprequestmessage-version-change.md)]

***

## <a name="net-core-20"></a><span data-ttu-id="017fe-115">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="017fe-115">.NET Core 2.0</span></span>

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***
