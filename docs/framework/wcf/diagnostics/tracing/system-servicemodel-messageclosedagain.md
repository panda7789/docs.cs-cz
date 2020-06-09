---
title: System.ServiceModel.MessageClosedAgain
ms.date: 03/30/2017
ms.assetid: 24c274d4-65cd-4c91-9869-bc6eb34ef979
ms.openlocfilehash: d341953b8e12b14e6a3fe8a477c16a1b3a4454ae
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84580434"
---
# <a name="systemservicemodelmessageclosedagain"></a><span data-ttu-id="4e379-102">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="4e379-102">System.ServiceModel.MessageClosedAgain</span></span>
<span data-ttu-id="4e379-103">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="4e379-103">System.ServiceModel.MessageClosedAgain</span></span>  
  
## <a name="description"></a><span data-ttu-id="4e379-104">Popis</span><span class="sxs-lookup"><span data-stu-id="4e379-104">Description</span></span>  
 <span data-ttu-id="4e379-105">Zpráva byla znovu zavřena.</span><span class="sxs-lookup"><span data-stu-id="4e379-105">A message was closed again.</span></span>  
  
 <span data-ttu-id="4e379-106">Zpráva by měla být zavřena pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="4e379-106">A message should be closed only once.</span></span> <span data-ttu-id="4e379-107">Pokud je toto trasování generováno v uživatelském rozšíření kódu, znamená to, že kód rozšíření uživatele zavírá zprávu, která již byla zavřena.</span><span class="sxs-lookup"><span data-stu-id="4e379-107">If this trace is being emitted in user extension code, it indicates that the user extension code is closing a message that has already been closed.</span></span> <span data-ttu-id="4e379-108">Pokud se toto trasování generuje prostřednictvím kódu produktu, znamená to, že kód rozšíření uživatele může potenciálně zavřít zprávu příliš brzy.</span><span class="sxs-lookup"><span data-stu-id="4e379-108">If this trace is being emitted through product code, it indicates that the user extension code could potentially be closing a message too early.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e379-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="4e379-109">See also</span></span>

- [<span data-ttu-id="4e379-110">Trasování</span><span class="sxs-lookup"><span data-stu-id="4e379-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="4e379-111">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="4e379-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="4e379-112">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="4e379-112">Administration and Diagnostics</span></span>](../index.md)
