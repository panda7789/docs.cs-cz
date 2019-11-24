---
title: GetPublicKeyToken – metoda
ms.date: 03/30/2017
api_name:
- IALink2.GetPublicKeyToken
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetPublicKeyToken
helpviewer_keywords:
- GetPublicKeyToken method
ms.assetid: 4a16374c-94b0-47b0-9fed-88c2b0cdccd4
topic_type:
- apiref
ms.openlocfilehash: 2e7ed4e1529104db30b0b06665f74342d9ca9a01
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447239"
---
# <a name="getpublickeytoken-method"></a><span data-ttu-id="b938f-102">GetPublicKeyToken – metoda</span><span class="sxs-lookup"><span data-stu-id="b938f-102">GetPublicKeyToken Method</span></span>
<span data-ttu-id="b938f-103">Retrieves the public key token for a given keyfile or key container.</span><span class="sxs-lookup"><span data-stu-id="b938f-103">Retrieves the public key token for a given keyfile or key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b938f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b938f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="b938f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b938f-105">Parameters</span></span>  
 `pszKeyFile`  
 <span data-ttu-id="b938f-106">Filename of the key.</span><span class="sxs-lookup"><span data-stu-id="b938f-106">Filename of the key.</span></span>  
  
 `pszKeyContainer`  
 <span data-ttu-id="b938f-107">Name of the key container.</span><span class="sxs-lookup"><span data-stu-id="b938f-107">Name of the key container.</span></span>  
  
 `pvPublicKeyToken`  
 <span data-ttu-id="b938f-108">Address where key token is to be stored.</span><span class="sxs-lookup"><span data-stu-id="b938f-108">Address where key token is to be stored.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="b938f-109">Specifies the size, in bytes, of the buffer indicated by `pvPublicKeyToken`.</span><span class="sxs-lookup"><span data-stu-id="b938f-109">Specifies the size, in bytes, of the buffer indicated by `pvPublicKeyToken`.</span></span> <span data-ttu-id="b938f-110">Upon return, contains actual number of bytes used.</span><span class="sxs-lookup"><span data-stu-id="b938f-110">Upon return, contains actual number of bytes used.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b938f-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b938f-111">Return Value</span></span>  
 <span data-ttu-id="b938f-112">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="b938f-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b938f-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b938f-113">Requirements</span></span>  
 <span data-ttu-id="b938f-114">Requires alink.h.</span><span class="sxs-lookup"><span data-stu-id="b938f-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b938f-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b938f-115">See also</span></span>

- [<span data-ttu-id="b938f-116">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b938f-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="b938f-117">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b938f-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="b938f-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="b938f-118">ALink API</span></span>](index.md)
