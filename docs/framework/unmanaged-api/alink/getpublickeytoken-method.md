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
ms.openlocfilehash: 94a473d00110c07615ccdfc98bb8944e40dc30e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405470"
---
# <a name="getpublickeytoken-method"></a><span data-ttu-id="d3dbf-102">GetPublicKeyToken – metoda</span><span class="sxs-lookup"><span data-stu-id="d3dbf-102">GetPublicKeyToken Method</span></span>
<span data-ttu-id="d3dbf-103">Načte token veřejného klíče pro danou keyfile nebo kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="d3dbf-103">Retrieves the public key token for a given keyfile or key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3dbf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3dbf-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d3dbf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d3dbf-105">Parameters</span></span>  
 `pszKeyFile`  
 <span data-ttu-id="d3dbf-106">Název souboru klíče.</span><span class="sxs-lookup"><span data-stu-id="d3dbf-106">Filename of the key.</span></span>  
  
 `pszKeyContainer`  
 <span data-ttu-id="d3dbf-107">Název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="d3dbf-107">Name of the key container.</span></span>  
  
 `pvPublicKeyToken`  
 <span data-ttu-id="d3dbf-108">Adresa, kde má být uložena token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="d3dbf-108">Address where key token is to be stored.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="d3dbf-109">Určuje velikost v bajtech vyrovnávací paměti indikován `pvPublicKeyToken`.</span><span class="sxs-lookup"><span data-stu-id="d3dbf-109">Specifies the size, in bytes, of the buffer indicated by `pvPublicKeyToken`.</span></span> <span data-ttu-id="d3dbf-110">Po návratu obsahuje skutečný počet bajtů použitých.</span><span class="sxs-lookup"><span data-stu-id="d3dbf-110">Upon return, contains actual number of bytes used.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d3dbf-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d3dbf-111">Return Value</span></span>  
 <span data-ttu-id="d3dbf-112">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="d3dbf-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3dbf-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d3dbf-113">Requirements</span></span>  
 <span data-ttu-id="d3dbf-114">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="d3dbf-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3dbf-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="d3dbf-115">See Also</span></span>  
 [<span data-ttu-id="d3dbf-116">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d3dbf-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="d3dbf-117">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d3dbf-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="d3dbf-118">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="d3dbf-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
