---
title: IDENTITY_ATTRIBUTE_BLOB – struktura
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- IDENTITY_ATTRIBUTE_BLOB
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDENTITY_ATTRIBUTE_BLOB
helpviewer_keywords:
- IDENTITY_ATTRIBUTE_BLOB structure [.NET Framework fusion]
ms.assetid: af14ae5f-d226-47dd-ba90-8fc6e6605d4d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58ee2764d2e2c4c4e21effa3e0c3551a2e145f40
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796500"
---
# <a name="identity_attribute_blob-structure"></a><span data-ttu-id="a5038-102">IDENTITY_ATTRIBUTE_BLOB – struktura</span><span class="sxs-lookup"><span data-stu-id="a5038-102">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>
<span data-ttu-id="a5038-103">Obsahuje informace o jednom atributu v sestavení a skládá se ze tří `DWORD`s.</span><span class="sxs-lookup"><span data-stu-id="a5038-103">Contains information about a single attribute in an assembly, and consists of three `DWORD`s.</span></span> <span data-ttu-id="a5038-104">Každé `DWORD` je posun do vyrovnávací paměti znaků vytvářený `CurrentIntoBuffer` metodou rozhraní [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a5038-104">Each `DWORD` is an offset into a character buffer produced by the `CurrentIntoBuffer` method of the [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) interface</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5038-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5038-105">Syntax</span></span>  
  
```cpp  
typedef struct _IDENTITY_ATTRIBUTE_BLOB {  
    DWORD  ofsNamespace;  
    DWORD  ofsName;  
    DWORD  ofsValue;  
}   IDENTITY_ATTRIBUTE_BLOB;  
```  
  
## <a name="members"></a><span data-ttu-id="a5038-106">Členové</span><span class="sxs-lookup"><span data-stu-id="a5038-106">Members</span></span>  
  
|<span data-ttu-id="a5038-107">Člen</span><span class="sxs-lookup"><span data-stu-id="a5038-107">Member</span></span>|<span data-ttu-id="a5038-108">Popis</span><span class="sxs-lookup"><span data-stu-id="a5038-108">Description</span></span>|  
|------------|-----------------|  
|`ofsNamespace`|<span data-ttu-id="a5038-109">První posun do vyrovnávací paměti znaků.</span><span class="sxs-lookup"><span data-stu-id="a5038-109">The first offset into the character buffer.</span></span> <span data-ttu-id="a5038-110">Na tento posun nenásleduje obor názvů atributu, ale řada znaků null.</span><span class="sxs-lookup"><span data-stu-id="a5038-110">This offset is not followed by the attribute's namespace, but by a series of null characters.</span></span> <span data-ttu-id="a5038-111">Proto se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="a5038-111">Therefore, it is not used.</span></span>|  
|`ofsName`|<span data-ttu-id="a5038-112">Druhý posun do vyrovnávací paměti znaků.</span><span class="sxs-lookup"><span data-stu-id="a5038-112">The second offset into the character buffer.</span></span> <span data-ttu-id="a5038-113">Toto umístění označuje začátek názvu atributu.</span><span class="sxs-lookup"><span data-stu-id="a5038-113">This location marks the start of the attribute's name.</span></span>|  
|`ofsValue`|<span data-ttu-id="a5038-114">Třetí posun do vyrovnávací paměti znaků.</span><span class="sxs-lookup"><span data-stu-id="a5038-114">The third offset into the character buffer.</span></span> <span data-ttu-id="a5038-115">Toto umístění označuje začátek hodnoty atributu.</span><span class="sxs-lookup"><span data-stu-id="a5038-115">This location marks the start of the attribute's value.</span></span>|  
  
## <a name="sample"></a><span data-ttu-id="a5038-116">Ukázka</span><span class="sxs-lookup"><span data-stu-id="a5038-116">Sample</span></span>  
 <span data-ttu-id="a5038-117">Následující příklad znázorňuje několik základních kroků, které nakonec mají za následek vyplněnou `IDENTITY_ATTRIBUTE_BLOB` strukturu:</span><span class="sxs-lookup"><span data-stu-id="a5038-117">The following example illustrates several basic steps, which eventually result in a populated `IDENTITY_ATTRIBUTE_BLOB` structure:</span></span>  
  
1. <span data-ttu-id="a5038-118">Získejte [IReferenceIdentity –](ireferenceidentity-interface.md) pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="a5038-118">Obtain an [IReferenceIdentity](ireferenceidentity-interface.md) for the assembly.</span></span>  
  
2. <span data-ttu-id="a5038-119">Zavolejte metodu a získejte [IEnumIDENTITY_ATTRIBUTE.](ienumidentity-attribute-interface.md) `IReferenceIdentity::EnumAttributes`</span><span class="sxs-lookup"><span data-stu-id="a5038-119">Call the `IReferenceIdentity::EnumAttributes` method, and obtain an [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md).</span></span>  
  
3. <span data-ttu-id="a5038-120">Vytvořte vyrovnávací paměť znaků a přetypujte ji jako `IDENTITY_ATTRIBUTE_BLOB` strukturu.</span><span class="sxs-lookup"><span data-stu-id="a5038-120">Create a character buffer, and cast it as an `IDENTITY_ATTRIBUTE_BLOB` structure.</span></span>  
  
4. <span data-ttu-id="a5038-121">`CurrentIntoBuffer` Zavolejte metodu`IEnumIDENTITY_ATTRIBUTE` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a5038-121">Call the `CurrentIntoBuffer` method of the `IEnumIDENTITY_ATTRIBUTE` interface.</span></span> <span data-ttu-id="a5038-122">Tato metoda zkopíruje atributy `Namespace`, `Name`a `Value` do vyrovnávací paměti znaků.</span><span class="sxs-lookup"><span data-stu-id="a5038-122">This method copies the attributes `Namespace`, `Name`, and `Value` into the character buffer.</span></span> <span data-ttu-id="a5038-123">Tři posuny k těmto řetězcům budou k dispozici ve `IDENTITY_ATTRIBUTE_BLOB` struktuře.</span><span class="sxs-lookup"><span data-stu-id="a5038-123">The three offsets to those strings will become available in the `IDENTITY_ATTRIBUTE_BLOB` structure.</span></span>  
  
```cpp  
// EnumAssemblyAttributes.cpp : main project file.  
  
#include "stdafx.h"  
  
#include "fusion.h"  
#include "windows.h"  
#include "stdio.h"  
#include "mscoree.h"  
#include "isolation.h"  
  
typedef HRESULT (__stdcall *PFNGETREF)(LPCWSTR pwzFile, REFIID riid, IUnknown **ppUnk);  
typedef HRESULT (__stdcall *PFNGETAUTH)(IIdentityAuthority **ppIIdentityAuthority);  
  
PFNGETREF                   g_pfnGetAssemblyIdentityFromFile = NULL;  
PFNGETAUTH                  g_pfnGetIdentityAuthority = NULL;  
IUnknown                    *g_pUnk = NULL;  
  
bool Init()  
{  
    HRESULT     hr = S_OK;  
    DWORD       dwSize = 0;  
    bool        bRC = false;  
  
    hr = CorBindToRuntimeEx(NULL, L"wks", 0, CLSID_CorRuntimeHost,  
                           IID_ICorRuntimeHost, (void **)&g_pUnk);  
    if(FAILED(hr)) {  
        printf("Error: Failed to initialize CLR runtime! hr = 0x%0x\n",  
                hr);  
        goto Exit;  
    }  
  
    if (SUCCEEDED(hr)) {  
        hr = GetRealProcAddress("GetAssemblyIdentityFromFile",  
                         (VOID **)&g_pfnGetAssemblyIdentityFromFile);  
    }  
  
    if (SUCCEEDED(hr)) {  
        hr = GetRealProcAddress("GetIdentityAuthority",  
                                (VOID **)&g_pfnGetIdentityAuthority);  
    }  
  
    if (!g_pfnGetAssemblyIdentityFromFile ||   
        !g_pfnGetIdentityAuthority)  
    {  
        printf("Error: Cannot get required APIs from fusion.dll!\n");  
        goto Exit;  
    }  
  
    bRC = true;  
  
Exit:  
    return bRC;  
}  
  
void Shutdown()  
{  
    if(g_pUnk) {  
        g_pUnk->Release();  
        g_pUnk = NULL;  
    }  
}  
  
void Usage()  
{  
    printf("EnumAssemblyAttributes: A tool to enumerate the identity   
            attributes of a given assembly.\n\n");  
    printf("Usage: EnumAssemblyAttributes AssemblyFilePath\n");  
    printf("\n");  
}  
  
int _cdecl wmain(int argc, LPCWSTR argv[])  
{  
    int     iResult = 1;  
    IUnknown                    *pUnk  = NULL;  
    IReferenceIdentity          *pRef  = NULL;  
    HRESULT                     hr     = S_OK;     
    IEnumIDENTITY_ATTRIBUTE     *pEnum = NULL;  
    BYTE                        abData[1024];  
    DWORD                       cbAvailable;  
    DWORD                       cbUsed;  
    IDENTITY_ATTRIBUTE_BLOB     *pBlob;  
  
    if(argc != 2) {  
        Usage();  
        goto Exit;  
    }  
  
    if(!Init()) {  
        printf("Failure initializing EnumIdAttr.\n");  
        goto Exit;  
    }  
  
    hr = g_pfnGetAssemblyIdentityFromFile(argv[1],   
                            __uuidof(IReferenceIdentity), &pUnk);  
  
    if (FAILED(hr)) {  
        printf("GetAssemblyIdentityFromFile failed with hr = 0x%x",   
                hr);  
        goto Exit;  
    }  
  
    hr = pUnk->QueryInterface(__uuidof(IReferenceIdentity),   
                              (void**)&pRef);  
    if (FAILED(hr)) {  
        goto Exit;  
    }  
  
    hr = pRef->EnumAttributes(&pEnum);  
    if (FAILED(hr)) {  
        printf("IReferenceIdentity::EnumAttributes failed with hr =   
                0x%x", hr);  
        goto Exit;  
    }  
  
    pBlob = (IDENTITY_ATTRIBUTE_BLOB *)(abData);  
    while (1) {  
        cbAvailable = sizeof(abData);  
        hr = pEnum->CurrentIntoBuffer(cbAvailable, abData, &cbUsed);  
        if (FAILED(hr)) {  
            printf("IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer failed   
                    with hr = 0x%x", hr);  
            goto Exit;  
        }  
  
        if (! cbUsed) {  
            break;  
        }  
  
        LPWSTR pwzNameSpace = (LPWSTR)(abData + pBlob->ofsNamespace);  
        LPWSTR pwzName      = (LPWSTR)(abData + pBlob->ofsName);  
        LPWSTR pwzValue     = (LPWSTR)(abData + pBlob->ofsValue);  
        printf("%ws: %ws = %ws\n", pwzNameSpace, pwzName, pwzValue);  
  
        hr = pEnum->Skip(1);  
        if (FAILED(hr)) {  
            printf("IEnumIDENTITY_ATTRIBUTE::Skip failed with hr =   
                    0x%x", hr);  
            goto Exit;  
        }  
    }  
  
    iResult = 0;  
  
Exit:  
  
    Shutdown();  
  
    if (pUnk) {  
        pUnk->Release();  
    }  
  
    if (pRef) {  
        pRef->Release();  
    }  
  
    if (pEnum) {  
        pEnum->Release();  
    }  
  
    return iResult;  
}  
```  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="a5038-124">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="a5038-124">To run the sample</span></span>  
 <span data-ttu-id="a5038-125">C:\\> EnumAssemblyAttributes.exe C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\System.dll</span><span class="sxs-lookup"><span data-stu-id="a5038-125">C:\\> EnumAssemblyAttributes.exe C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\System.dll</span></span>  
  
### <a name="sample-output"></a><span data-ttu-id="a5038-126">Ukázkový výstup</span><span class="sxs-lookup"><span data-stu-id="a5038-126">Sample output</span></span>  
 <span data-ttu-id="a5038-127">Culture = neutrální</span><span class="sxs-lookup"><span data-stu-id="a5038-127">Culture = neutral</span></span>  
  
 <span data-ttu-id="a5038-128">název = systém</span><span class="sxs-lookup"><span data-stu-id="a5038-128">name = System</span></span>  
  
 <span data-ttu-id="a5038-129">processorArchitecture = MSIL</span><span class="sxs-lookup"><span data-stu-id="a5038-129">processorArchitecture = MSIL</span></span>  
  
 <span data-ttu-id="a5038-130">PublicKeyToken = b77a5c561934e089</span><span class="sxs-lookup"><span data-stu-id="a5038-130">PublicKeyToken = b77a5c561934e089</span></span>  
  
 <span data-ttu-id="a5038-131">Verze = 2.0.0.0</span><span class="sxs-lookup"><span data-stu-id="a5038-131">Version = 2.0.0.0</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5038-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a5038-132">Requirements</span></span>  
 <span data-ttu-id="a5038-133">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5038-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5038-134">**Hlaviček** Izolace. h</span><span class="sxs-lookup"><span data-stu-id="a5038-134">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="a5038-135">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5038-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5038-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a5038-136">See also</span></span>

- [<span data-ttu-id="a5038-137">IReferenceIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a5038-137">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)
- [<span data-ttu-id="a5038-138">IEnumIDENTITY_ATTRIBUTE – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a5038-138">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](ienumidentity-attribute-interface.md)
- [<span data-ttu-id="a5038-139">IDENTITY_ATTRIBUTE – struktura</span><span class="sxs-lookup"><span data-stu-id="a5038-139">IDENTITY_ATTRIBUTE Structure</span></span>](identity-attribute-structure.md)
- [<span data-ttu-id="a5038-140">Struktury pro fúze</span><span class="sxs-lookup"><span data-stu-id="a5038-140">Fusion Structures</span></span>](fusion-structures.md)
