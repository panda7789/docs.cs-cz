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
ms.openlocfilehash: 297931db9d0bbced79a009575abc52a5676ac72a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="system-event-log-cannot-be-deleted"></a><span data-ttu-id="71a34-102">Protokol událostí systému nelze odstranit.</span><span class="sxs-lookup"><span data-stu-id="71a34-102">System event log cannot be deleted</span></span>
<span data-ttu-id="71a34-103">Byl proveden pokus o odstranění protokolu událostí systému, kterou nejde odstranit.</span><span class="sxs-lookup"><span data-stu-id="71a34-103">An attempt has been made to delete the system event log, which cannot be deleted.</span></span> <span data-ttu-id="71a34-104">Protokol systému sleduje systémové události, jako je například selhání spuštění a hardwaru systému.</span><span class="sxs-lookup"><span data-stu-id="71a34-104">The system log tracks system events such as system startup and hardware failures.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="71a34-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="71a34-105">To correct this error</span></span>  
  
-   <span data-ttu-id="71a34-106">Uvažujte aplikace zapisovat do aplikace nebo vlastního protokolu, nikoli protokol událostí systému.</span><span class="sxs-lookup"><span data-stu-id="71a34-106">Consider having your application write to an application or custom log, rather than the system event log.</span></span>  
  
-   <span data-ttu-id="71a34-107">Nepokoušejte se odstranit protokol událostí systému.</span><span class="sxs-lookup"><span data-stu-id="71a34-107">Do not attempt to delete the system event log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71a34-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="71a34-108">See Also</span></span>  
 [<span data-ttu-id="71a34-109">Správa protokolů událostí</span><span class="sxs-lookup"><span data-stu-id="71a34-109">Administering Event Logs</span></span>](http://msdn.microsoft.com/en-us/35f53238-bdd2-417b-acd8-2fd9f7397f18)  
 [<span data-ttu-id="71a34-110">Postupy: vytváření a odebrání vlastní protokoly událostí</span><span class="sxs-lookup"><span data-stu-id="71a34-110">How to: Create and Remove Custom Event Logs</span></span>](http://msdn.microsoft.com/en-us/af9b7da0-80c7-46ac-b7f7-897063ddd503)
