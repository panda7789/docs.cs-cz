---
title: InitDbgTransportManager – funkce
ms.date: 03/30/2017
api_name:
- InitDbgTransportManager
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- InitDbgTransportManager
helpviewer_keywords:
- remote debugging API [Silverlight]
- InitDbgTransportManager function
- Silverlight, remote debugging
ms.assetid: a30102ff-c52e-48c9-b3a9-aa14286a42b2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74cb2c7d1f79d23e1331cc7192ba2d6acfd9835c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761647"
---
# <a name="initdbgtransportmanager-function"></a><span data-ttu-id="f7d92-102">InitDbgTransportManager – funkce</span><span class="sxs-lookup"><span data-stu-id="f7d92-102">InitDbgTransportManager Function</span></span>
<span data-ttu-id="f7d92-103">Inicializuje správce přenosu pro připojení k vzdálené cílové pro výčet procesu a modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="f7d92-103">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7d92-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7d92-104">Syntax</span></span>  
  
```  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f7d92-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f7d92-105">Return Value</span></span>  
 <span data-ttu-id="f7d92-106">S_OK</span><span class="sxs-lookup"><span data-stu-id="f7d92-106">S_OK</span></span>  
 <span data-ttu-id="f7d92-107">Úspěch.</span><span class="sxs-lookup"><span data-stu-id="f7d92-107">Success.</span></span>  
  
 <span data-ttu-id="f7d92-108">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="f7d92-108">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="f7d92-109">Funkce se nepodařilo přidělit paměť pro správce přenosu.</span><span class="sxs-lookup"><span data-stu-id="f7d92-109">The function was unable to allocate memory for a transport manager.</span></span>  
  
 <span data-ttu-id="f7d92-110">E_FAIL (nebo jiné E_ návratové kódy)</span><span class="sxs-lookup"><span data-stu-id="f7d92-110">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="f7d92-111">Jiné chyby.</span><span class="sxs-lookup"><span data-stu-id="f7d92-111">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7d92-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f7d92-112">Requirements</span></span>  
 <span data-ttu-id="f7d92-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7d92-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7d92-114">**Záhlaví:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="f7d92-114">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="f7d92-115">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="f7d92-115">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="f7d92-116">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="f7d92-116">**.NET Framework Versions:** 3.5 SP1</span></span>
