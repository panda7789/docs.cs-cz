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
# <a name="networking-breaking-changes"></a><span data-ttu-id="44979-103">Síťové přerušující změny</span><span class="sxs-lookup"><span data-stu-id="44979-103">Networking breaking changes</span></span>

<span data-ttu-id="44979-104">Na této stránce jsou popsány následující přerušující se změny:</span><span class="sxs-lookup"><span data-stu-id="44979-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="44979-105">Zásadní změna</span><span class="sxs-lookup"><span data-stu-id="44979-105">Breaking change</span></span> | <span data-ttu-id="44979-106">Představená verze</span><span class="sxs-lookup"><span data-stu-id="44979-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="44979-107">WinHttpHandler odebrané z modulu runtime .NET</span><span class="sxs-lookup"><span data-stu-id="44979-107">WinHttpHandler removed from .NET runtime</span></span>](#winhttphandler-removed-from-net-runtime) | <span data-ttu-id="44979-108">5.0</span><span class="sxs-lookup"><span data-stu-id="44979-108">5.0</span></span> |
| [<span data-ttu-id="44979-109">MulticastOption. Group nepřijímá hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="44979-109">MulticastOption.Group doesn't accept a null value</span></span>](#multicastoptiongroup-doesnt-accept-a-null-value) | <span data-ttu-id="44979-110">5.0</span><span class="sxs-lookup"><span data-stu-id="44979-110">5.0</span></span> |
| [<span data-ttu-id="44979-111">Výchozí hodnota zprávy HttpRequestMessage. Version se změnila na 1,1.</span><span class="sxs-lookup"><span data-stu-id="44979-111">Default value of HttpRequestMessage.Version changed to 1.1</span></span>](#default-value-of-httprequestmessageversion-changed-to-11) | <span data-ttu-id="44979-112">3.0</span><span class="sxs-lookup"><span data-stu-id="44979-112">3.0</span></span> |
| [<span data-ttu-id="44979-113">WebClient. CancelAsync nevždycky zruší hned</span><span class="sxs-lookup"><span data-stu-id="44979-113">WebClient.CancelAsync doesn't always cancel immediately</span></span>](#webclientcancelasync-doesnt-always-cancel-immediately) | <span data-ttu-id="44979-114">2.0</span><span class="sxs-lookup"><span data-stu-id="44979-114">2.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="44979-115">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="44979-115">.NET 5.0</span></span>

[!INCLUDE [winhttphandler-removed-from-runtime](../../../includes/core-changes/networking/5.0/winhttphandler-removed-from-runtime.md)]

***

[!INCLUDE [multicastoption-group-doesnt-accept-null](../../../includes/core-changes/networking/5.0/multicastoption-group-doesnt-accept-null.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="44979-116">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="44979-116">.NET Core 3.0</span></span>

[!INCLUDE[Default value of HttpRequestMessage.Version changed to 1.1](~/includes/core-changes/networking/3.0/httprequestmessage-version-change.md)]

***

## <a name="net-core-20"></a><span data-ttu-id="44979-117">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="44979-117">.NET Core 2.0</span></span>

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***
