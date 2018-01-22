---
title: "Protokol událostí systému nelze odstranit."
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 26ca8819-4ce5-49c6-98f3-27fe9e2e8e3d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e07c6514d8ef3dd4f1cad40cbab1ff1c54c65796
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="system-event-log-cannot-be-deleted"></a><span data-ttu-id="1384e-102">Protokol událostí systému nelze odstranit.</span><span class="sxs-lookup"><span data-stu-id="1384e-102">System event log cannot be deleted</span></span>
<span data-ttu-id="1384e-103">Byl proveden pokus o odstranění protokolu událostí systému, kterou nejde odstranit.</span><span class="sxs-lookup"><span data-stu-id="1384e-103">An attempt has been made to delete the system event log, which cannot be deleted.</span></span> <span data-ttu-id="1384e-104">Protokol systému sleduje systémové události, jako je například selhání spuštění a hardwaru systému.</span><span class="sxs-lookup"><span data-stu-id="1384e-104">The system log tracks system events such as system startup and hardware failures.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1384e-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="1384e-105">To correct this error</span></span>  
  
-   <span data-ttu-id="1384e-106">Uvažujte aplikace zapisovat do aplikace nebo vlastního protokolu, nikoli protokol událostí systému.</span><span class="sxs-lookup"><span data-stu-id="1384e-106">Consider having your application write to an application or custom log, rather than the system event log.</span></span>  
  
-   <span data-ttu-id="1384e-107">Nepokoušejte se odstranit protokol událostí systému.</span><span class="sxs-lookup"><span data-stu-id="1384e-107">Do not attempt to delete the system event log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1384e-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="1384e-108">See Also</span></span>  
 [<span data-ttu-id="1384e-109">Správa protokolů událostí</span><span class="sxs-lookup"><span data-stu-id="1384e-109">Administering Event Logs</span></span>](http://msdn.microsoft.com/library/35f53238-bdd2-417b-acd8-2fd9f7397f18)  
 [<span data-ttu-id="1384e-110">Postupy: vytváření a odebrání vlastní protokoly událostí</span><span class="sxs-lookup"><span data-stu-id="1384e-110">How to: Create and Remove Custom Event Logs</span></span>](http://msdn.microsoft.com/library/af9b7da0-80c7-46ac-b7f7-897063ddd503)
