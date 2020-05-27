---
title: IMetaDataAssemblyEmit::SetAssemblyProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyProps method [.NET Framework metadata]
ms.assetid: 91b633d7-9e75-43c3-a8d2-2144984e5f9e
topic_type:
- apiref
ms.openlocfilehash: 7c6adcbcfe64f63048078b4ccba6727a58531033
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008102"
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a><span data-ttu-id="310ef-102">IMetaDataAssemblyEmit::SetAssemblyProps – metoda</span><span class="sxs-lookup"><span data-stu-id="310ef-102">IMetaDataAssemblyEmit::SetAssemblyProps Method</span></span>
<span data-ttu-id="310ef-103">Upraví zadanou `Assembly` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="310ef-103">Modifies the specified `Assembly` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="310ef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="310ef-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyProps (  
    [in] mdAssembly               pma,  
    [in] const void               *pbPublicKey,  
    [in] ULONG                    cbPublicKey,  
    [in] ULONG                    ulHashAlgId,  
    [in] LPCWSTR                  szName,  
    [in] const ASSEMBLYMETADATA   *pMetaData,  
    [in] DWORD                    dwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="310ef-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="310ef-105">Parameters</span></span>  
 `pma`  
 <span data-ttu-id="310ef-106">pro Token metadat, který určuje `Assembly` strukturu metadat, která má být upravena.</span><span class="sxs-lookup"><span data-stu-id="310ef-106">[in] The metadata token that specifies the `Assembly` metadata structure to be modified.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="310ef-107">pro Ukazatel na veřejný klíč vydavatele sestavení.</span><span class="sxs-lookup"><span data-stu-id="310ef-107">[in] A pointer to the public key of the publisher of the assembly.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="310ef-108">pro Velikost v bajtech `pbPublicKey` .</span><span class="sxs-lookup"><span data-stu-id="310ef-108">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `ulHashAlgId`  
 <span data-ttu-id="310ef-109">pro Identifikátor algoritmu hash, který slouží k hashování souborů sestavení.</span><span class="sxs-lookup"><span data-stu-id="310ef-109">[in] The identifier for the hash algorithm used to hash the assembly files.</span></span>  
  
 `szName`  
 <span data-ttu-id="310ef-110">pro Textový název sestavení čitelný lidmi</span><span class="sxs-lookup"><span data-stu-id="310ef-110">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="310ef-111">pro Ukazatel na AssemblyMetadata –, který obsahuje informace o verzi, platformě a národním prostředí pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="310ef-111">[in] A pointer to the ASSEMBLYMETADATA that contains version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="310ef-112">pro Bitová kombinace hodnot [AssemblyFlags –](assemblyflags-enumeration.md) , které určují různé atributy sestavení.</span><span class="sxs-lookup"><span data-stu-id="310ef-112">[in] A bitwise combination of [AssemblyFlags](assemblyflags-enumeration.md) values that specify various attributes of the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="310ef-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="310ef-113">Remarks</span></span>  
 <span data-ttu-id="310ef-114">Chcete-li vytvořit `Assembly` strukturu metadat, použijte metodu [IMetaDataAssemblyEmit::D efineassembly](imetadataassemblyemit-defineassembly-method.md) .</span><span class="sxs-lookup"><span data-stu-id="310ef-114">To create an `Assembly` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssembly](imetadataassemblyemit-defineassembly-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="310ef-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="310ef-115">Requirements</span></span>  
 <span data-ttu-id="310ef-116">**Platforma:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="310ef-116">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="310ef-117">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="310ef-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="310ef-118">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="310ef-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="310ef-119">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="310ef-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="310ef-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="310ef-120">See also</span></span>

- [<span data-ttu-id="310ef-121">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="310ef-121">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
