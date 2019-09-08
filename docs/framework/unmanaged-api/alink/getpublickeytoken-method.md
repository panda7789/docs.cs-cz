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
ms.openlocfilehash: 158ecc036d56e2ad9a3fa650677c04ebcbfd7696
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777225"
---
# <a name="getpublickeytoken-method"></a><span data-ttu-id="17d75-102">GetPublicKeyToken – metoda</span><span class="sxs-lookup"><span data-stu-id="17d75-102">GetPublicKeyToken Method</span></span>
<span data-ttu-id="17d75-103">Načte token veřejného klíče pro daný soubor klíče nebo kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="17d75-103">Retrieves the public key token for a given keyfile or key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17d75-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17d75-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="17d75-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="17d75-105">Parameters</span></span>  
 `pszKeyFile`  
 <span data-ttu-id="17d75-106">Název souboru klíče</span><span class="sxs-lookup"><span data-stu-id="17d75-106">Filename of the key.</span></span>  
  
 `pszKeyContainer`  
 <span data-ttu-id="17d75-107">Název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="17d75-107">Name of the key container.</span></span>  
  
 `pvPublicKeyToken`  
 <span data-ttu-id="17d75-108">Adresa, kam se má uložit klíč tokenu</span><span class="sxs-lookup"><span data-stu-id="17d75-108">Address where key token is to be stored.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="17d75-109">Určuje velikost vyrovnávací paměti (v bajtech), kterou vyznačuje `pvPublicKeyToken`.</span><span class="sxs-lookup"><span data-stu-id="17d75-109">Specifies the size, in bytes, of the buffer indicated by `pvPublicKeyToken`.</span></span> <span data-ttu-id="17d75-110">Při návratu obsahuje skutečný počet použitých bajtů.</span><span class="sxs-lookup"><span data-stu-id="17d75-110">Upon return, contains actual number of bytes used.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="17d75-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="17d75-111">Return Value</span></span>  
 <span data-ttu-id="17d75-112">Vrací S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="17d75-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17d75-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="17d75-113">Requirements</span></span>  
 <span data-ttu-id="17d75-114">Vyžaduje ALink. h.</span><span class="sxs-lookup"><span data-stu-id="17d75-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17d75-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="17d75-115">See also</span></span>

- [<span data-ttu-id="17d75-116">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="17d75-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="17d75-117">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="17d75-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="17d75-118">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="17d75-118">ALink API</span></span>](index.md)
