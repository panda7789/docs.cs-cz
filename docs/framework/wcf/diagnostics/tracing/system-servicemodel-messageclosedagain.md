---
title: System.ServiceModel.MessageClosedAgain
ms.date: 03/30/2017
ms.assetid: 24c274d4-65cd-4c91-9869-bc6eb34ef979
ms.openlocfilehash: a18355d55359df665d0e936ce95da34bf07aec6a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181330"
---
# <a name="systemservicemodelmessageclosedagain"></a><span data-ttu-id="eb5fa-102">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="eb5fa-102">System.ServiceModel.MessageClosedAgain</span></span>
<span data-ttu-id="eb5fa-103">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="eb5fa-103">System.ServiceModel.MessageClosedAgain</span></span>  
  
## <a name="description"></a><span data-ttu-id="eb5fa-104">Popis</span><span class="sxs-lookup"><span data-stu-id="eb5fa-104">Description</span></span>  
 <span data-ttu-id="eb5fa-105">Zpráva byla znovu zavřena.</span><span class="sxs-lookup"><span data-stu-id="eb5fa-105">A message was closed again.</span></span>  
  
 <span data-ttu-id="eb5fa-106">Zprávu je třeba zavřít pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="eb5fa-106">A message should be closed only once.</span></span> <span data-ttu-id="eb5fa-107">Pokud toto trasování se právě emituje do kódu rozšíření uživatele, znamená to, že uživatelský kód rozšíření se zavírá zprávu, která již byla uzavřena.</span><span class="sxs-lookup"><span data-stu-id="eb5fa-107">If this trace is being emitted in user extension code, it indicates that the user extension code is closing a message that has already been closed.</span></span> <span data-ttu-id="eb5fa-108">Pokud toto trasování se právě emituje prostřednictvím kódu produktu, znamená to, že uživatelský kód rozšíření může potenciálně být zavření zprávy příliš brzy.</span><span class="sxs-lookup"><span data-stu-id="eb5fa-108">If this trace is being emitted through product code, it indicates that the user extension code could potentially be closing a message too early.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb5fa-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eb5fa-109">See also</span></span>

- [<span data-ttu-id="eb5fa-110">Trasování</span><span class="sxs-lookup"><span data-stu-id="eb5fa-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="eb5fa-111">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="eb5fa-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="eb5fa-112">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="eb5fa-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
