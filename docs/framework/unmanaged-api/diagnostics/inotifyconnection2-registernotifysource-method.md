---
title: "INotifyConnection2::RegisterNotifySource – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: INotifyConnection2.RegisterNotifySource
api_location: diasymreader.dll
api_type: COM
f1_keywords: INotifyConnection2::RegisterNotifySource
helpviewer_keywords:
- INotifyConnection2::RegisterNotifySource method [.NET Framework debugging]
- RegisterNotifySource method [.NET Framework debugging]
ms.assetid: 2632da80-6e4b-4429-8dee-b382745a5f81
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a141872dc5699e5b317b21f03672fe0d76096392
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="inotifyconnection2registernotifysource-method"></a><span data-ttu-id="a4bb1-102">INotifyConnection2::RegisterNotifySource – metoda</span><span class="sxs-lookup"><span data-stu-id="a4bb1-102">INotifyConnection2::RegisterNotifySource Method</span></span>
<span data-ttu-id="a4bb1-103">Nainstaluje zadaný oznámení zdroj.</span><span class="sxs-lookup"><span data-stu-id="a4bb1-103">Installs a specified notification source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4bb1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4bb1-104">Syntax</span></span>  
  
```  
HRESULT RegisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource,  
    [out] INotifySink2**   out_ppNotifySink  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a4bb1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a4bb1-105">Parameters</span></span>  
 `in_pNotifySource`  
 <span data-ttu-id="a4bb1-106">[v] Určuje objekt, který se má použít jako zdroj pro oznámení.</span><span class="sxs-lookup"><span data-stu-id="a4bb1-106">[in] Specifies the object to be used as the notification source.</span></span>  
  
 `out_ppNotifySink`  
 <span data-ttu-id="a4bb1-107">[out] Získá objekt, který má být použit jako jímku oznámení.</span><span class="sxs-lookup"><span data-stu-id="a4bb1-107">[out] Receives the object to be used as the notification sink.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4bb1-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a4bb1-108">Return Value</span></span>  
 <span data-ttu-id="a4bb1-109">S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="a4bb1-109">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4bb1-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a4bb1-110">Requirements</span></span>  
 <span data-ttu-id="a4bb1-111">**Záhlaví:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="a4bb1-111">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4bb1-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4bb1-112">See Also</span></span>  
 [<span data-ttu-id="a4bb1-113">INotifyConnection2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a4bb1-113">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 [<span data-ttu-id="a4bb1-114">INotifySource2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a4bb1-114">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [<span data-ttu-id="a4bb1-115">INotifySink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a4bb1-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="a4bb1-116">UnregisterNotifySource – metoda</span><span class="sxs-lookup"><span data-stu-id="a4bb1-116">UnregisterNotifySource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-unregisternotifysource-method.md)
