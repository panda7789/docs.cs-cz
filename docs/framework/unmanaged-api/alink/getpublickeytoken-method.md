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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ec2c357cd56670f4f2deed8023bed7842a7f4ed7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741883"
---
# <a name="getpublickeytoken-method"></a><span data-ttu-id="8bc17-102">GetPublicKeyToken – metoda</span><span class="sxs-lookup"><span data-stu-id="8bc17-102">GetPublicKeyToken Method</span></span>
<span data-ttu-id="8bc17-103">Načte token veřejného klíče pro daný parametr keyfile nebo kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="8bc17-103">Retrieves the public key token for a given keyfile or key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bc17-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8bc17-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="8bc17-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bc17-105">Parameters</span></span>  
 `pszKeyFile`  
 <span data-ttu-id="8bc17-106">Název souboru klíče.</span><span class="sxs-lookup"><span data-stu-id="8bc17-106">Filename of the key.</span></span>  
  
 `pszKeyContainer`  
 <span data-ttu-id="8bc17-107">Název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="8bc17-107">Name of the key container.</span></span>  
  
 `pvPublicKeyToken`  
 <span data-ttu-id="8bc17-108">Adresa, kde má být uložen token klíče.</span><span class="sxs-lookup"><span data-stu-id="8bc17-108">Address where key token is to be stored.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="8bc17-109">Určuje velikost v bajtech, vyrovnávací paměti indikován `pvPublicKeyToken`.</span><span class="sxs-lookup"><span data-stu-id="8bc17-109">Specifies the size, in bytes, of the buffer indicated by `pvPublicKeyToken`.</span></span> <span data-ttu-id="8bc17-110">Po návratu obsahuje skutečný počet bajtů.</span><span class="sxs-lookup"><span data-stu-id="8bc17-110">Upon return, contains actual number of bytes used.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8bc17-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8bc17-111">Return Value</span></span>  
 <span data-ttu-id="8bc17-112">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="8bc17-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bc17-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8bc17-113">Requirements</span></span>  
 <span data-ttu-id="8bc17-114">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="8bc17-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bc17-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8bc17-115">See also</span></span>

- [<span data-ttu-id="8bc17-116">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8bc17-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="8bc17-117">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8bc17-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="8bc17-118">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="8bc17-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
