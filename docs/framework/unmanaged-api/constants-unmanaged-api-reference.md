---
title: Konstanty (referenční dokumentace nespravovaného rozhraní API)
ms.date: 03/30/2017
helpviewer_keywords:
- constants for unmanaged API [.NET Framework]
- native API reference [.NET Framework], constants
- unmanaged API reference [.NET Framework], constants
ms.assetid: 77526f65-b71c-4483-9d19-3a3751fd8a45
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c537e4967c284df899a131b44d96dbdb6e1af29
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587671"
---
# <a name="constants-unmanaged-api-reference"></a><span data-ttu-id="0140b-102">Konstanty (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="0140b-102">Constants (Unmanaged API Reference)</span></span>
<span data-ttu-id="0140b-103">Toto téma popisuje typ jazyka, jazyk dodavatele a konstanty typu dokumentu, které jsou definovány v CorSym.idl.</span><span class="sxs-lookup"><span data-stu-id="0140b-103">This topic describes the language type, language vendor, and document type constants that are defined in CorSym.idl.</span></span>  
  
## <a name="language-type-constants"></a><span data-ttu-id="0140b-104">Konstanty jazyka zadejte</span><span class="sxs-lookup"><span data-stu-id="0140b-104">Language Type Constants</span></span>  
 <span data-ttu-id="0140b-105">Následující tabulka uvádí jazykové konstanty typů, které představují identifikátory GUID, které identifikují programovacích jazyků.</span><span class="sxs-lookup"><span data-stu-id="0140b-105">The following table shows language type constants, which represent GUIDs that identify programming languages.</span></span>  
  
|<span data-ttu-id="0140b-106">Symbol</span><span class="sxs-lookup"><span data-stu-id="0140b-106">Symbol</span></span>|<span data-ttu-id="0140b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="0140b-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="0140b-108">CorSym_LanguageType_C</span><span class="sxs-lookup"><span data-stu-id="0140b-108">CorSym_LanguageType_C</span></span>|<span data-ttu-id="0140b-109">Určuje jazyk C.</span><span class="sxs-lookup"><span data-stu-id="0140b-109">Indicates the C language.</span></span>|  
|<span data-ttu-id="0140b-110">CorSym_LanguageType_CPlusPlus</span><span class="sxs-lookup"><span data-stu-id="0140b-110">CorSym_LanguageType_CPlusPlus</span></span>|<span data-ttu-id="0140b-111">Určuje jazyk C++.</span><span class="sxs-lookup"><span data-stu-id="0140b-111">Indicates the C++ language.</span></span>|  
|<span data-ttu-id="0140b-112">CorSym_LanguageType_CSharp</span><span class="sxs-lookup"><span data-stu-id="0140b-112">CorSym_LanguageType_CSharp</span></span>|<span data-ttu-id="0140b-113">Označuje, C# jazyka.</span><span class="sxs-lookup"><span data-stu-id="0140b-113">Indicates the C# language.</span></span>|  
|<span data-ttu-id="0140b-114">CorSym_LanguageType_Basic</span><span class="sxs-lookup"><span data-stu-id="0140b-114">CorSym_LanguageType_Basic</span></span>|<span data-ttu-id="0140b-115">Určuje základní jazyk.</span><span class="sxs-lookup"><span data-stu-id="0140b-115">Indicates the Basic language.</span></span>|  
|<span data-ttu-id="0140b-116">CorSym_LanguageType_Java</span><span class="sxs-lookup"><span data-stu-id="0140b-116">CorSym_LanguageType_Java</span></span>|<span data-ttu-id="0140b-117">Určuje jazyk Java.</span><span class="sxs-lookup"><span data-stu-id="0140b-117">Indicates the Java language.</span></span>|  
|<span data-ttu-id="0140b-118">CorSym_LanguageType_Cobol</span><span class="sxs-lookup"><span data-stu-id="0140b-118">CorSym_LanguageType_Cobol</span></span>|<span data-ttu-id="0140b-119">Určuje jazyk, COBOL.</span><span class="sxs-lookup"><span data-stu-id="0140b-119">Indicates the COBOL language.</span></span>|  
|<span data-ttu-id="0140b-120">CorSym_LanguageType_Pascal</span><span class="sxs-lookup"><span data-stu-id="0140b-120">CorSym_LanguageType_Pascal</span></span>|<span data-ttu-id="0140b-121">Určuje jazyk, Pascal.</span><span class="sxs-lookup"><span data-stu-id="0140b-121">Indicates the Pascal language.</span></span>|  
|<span data-ttu-id="0140b-122">CorSym_LanguageType_ILAssembly</span><span class="sxs-lookup"><span data-stu-id="0140b-122">CorSym_LanguageType_ILAssembly</span></span>|<span data-ttu-id="0140b-123">Určuje kód sestavení Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="0140b-123">Indicates the Microsoft intermediate language (MSIL) assembly code.</span></span>|  
|<span data-ttu-id="0140b-124">CorSym_LanguageType_JScript</span><span class="sxs-lookup"><span data-stu-id="0140b-124">CorSym_LanguageType_JScript</span></span>|<span data-ttu-id="0140b-125">Určuje jazyk JScript.</span><span class="sxs-lookup"><span data-stu-id="0140b-125">Indicates the JScript language.</span></span>|  
|<span data-ttu-id="0140b-126">CorSym_LanguageType_SMC</span><span class="sxs-lookup"><span data-stu-id="0140b-126">CorSym_LanguageType_SMC</span></span>|<span data-ttu-id="0140b-127">Určuje jazyk, SMC.</span><span class="sxs-lookup"><span data-stu-id="0140b-127">Indicates the SMC language.</span></span>|  
|<span data-ttu-id="0140b-128">CorSym_LanguageType_MCPlusPlus</span><span class="sxs-lookup"><span data-stu-id="0140b-128">CorSym_LanguageType_MCPlusPlus</span></span>|<span data-ttu-id="0140b-129">Určuje jazyk C++ povoleny pro rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0140b-129">Indicates the C++ language enabled for the .NET Framework.</span></span>|  
  
## <a name="language-vendor-constants"></a><span data-ttu-id="0140b-130">Konstanty jazyka dodavatele</span><span class="sxs-lookup"><span data-stu-id="0140b-130">Language Vendor Constants</span></span>  
 <span data-ttu-id="0140b-131">Následující tabulka uvádí jazykové dodavatele konstanty, které představují identifikátory GUID, které identifikují programovací jazyk dodavatelů.</span><span class="sxs-lookup"><span data-stu-id="0140b-131">The following table shows language vendor constants, which represent GUIDs that identify programming language vendors.</span></span>  
  
|<span data-ttu-id="0140b-132">Symbol</span><span class="sxs-lookup"><span data-stu-id="0140b-132">Symbol</span></span>|<span data-ttu-id="0140b-133">Popis</span><span class="sxs-lookup"><span data-stu-id="0140b-133">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="0140b-134">CorSym_LanguageVendor_Microsoft</span><span class="sxs-lookup"><span data-stu-id="0140b-134">CorSym_LanguageVendor_Microsoft</span></span>|<span data-ttu-id="0140b-135">Označuje společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0140b-135">Indicates Microsoft.</span></span>|  
  
## <a name="document-type-constants"></a><span data-ttu-id="0140b-136">Konstanty typu dokumentu</span><span class="sxs-lookup"><span data-stu-id="0140b-136">Document Type Constants</span></span>  
 <span data-ttu-id="0140b-137">Následující tabulka uvádí dokument, typ konstanty, které představují identifikátory GUID, které identifikují typů dokumentů.</span><span class="sxs-lookup"><span data-stu-id="0140b-137">The following table shows document type constants, which represent GUIDs that identify document types.</span></span>  
  
|<span data-ttu-id="0140b-138">Symbol</span><span class="sxs-lookup"><span data-stu-id="0140b-138">Symbol</span></span>|<span data-ttu-id="0140b-139">Popis</span><span class="sxs-lookup"><span data-stu-id="0140b-139">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="0140b-140">CorSym_DocumentType_Text</span><span class="sxs-lookup"><span data-stu-id="0140b-140">CorSym_DocumentType_Text</span></span>|<span data-ttu-id="0140b-141">Určuje textový dokument.</span><span class="sxs-lookup"><span data-stu-id="0140b-141">Indicates a text document.</span></span>|  
|<span data-ttu-id="0140b-142">CorSym_DocumentType_MC</span><span class="sxs-lookup"><span data-stu-id="0140b-142">CorSym_DocumentType_MC</span></span>|<span data-ttu-id="0140b-143">Označuje než textovém dokumentu.</span><span class="sxs-lookup"><span data-stu-id="0140b-143">Indicates a non-text document.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0140b-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0140b-144">See also</span></span>
- [<span data-ttu-id="0140b-145">Referenční informace o nespravovaném rozhraní API</span><span class="sxs-lookup"><span data-stu-id="0140b-145">Unmanaged API Reference</span></span>](../../../docs/framework/unmanaged-api/index.md)
